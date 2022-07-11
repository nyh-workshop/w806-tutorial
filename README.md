# w806-tutorial

References for SDK deployment: https://github.com/IOsetting/wm-sdk-w806

Basically, this microcontroller is neither ARM, MIPS nor RISC-V. It is based on the C-Sky architecture ([source](https://www.cnx-software.com/2021/11/08/winnermicro-w806-240-mhz-mcu-2-development-board/)).

![image](https://user-images.githubusercontent.com/20377029/178199745-8980a67e-2441-4df3-8985-98a411e09533.png)

## Here is what is tried from the [SDK deployment tutorial](https://github.com/IOsetting/wm-sdk-w806) for **Windows** users:
1. Download MSYS2 and install packages. Then launch the MSYS2.
2. Once you get these C-Sky toolchains, extract the <code>csky-elfabiv2-tools-mingw-minilibc-yyyymmdd.tar.gz</code> into a folder, for example: <code>c:\csky-elfabiv2-tools-mingw-minilibc-yyyymmdd</code>
3. Next, git clone the https://github.com/IOsetting/wm-sdk-w806 into another folder.
4. Make sure you are inside the MSYS2. Switch directory to <code>x:/wm-sdk-w806</code>, then <code>make menuconfig</code>.
5. Inside the menuconfig, go to <code>Toolchain Configuration</code> and insert <code>/c/csky-elfabiv2-tools-mingw-minilibc-yyyymmdd/bin/</code> into the empty box (be sure you need to have the '/' after the bin!).
6. Press "Save", and "Exit" to the main menu.
7. At the <code>Download Configuration</code> select your download port and rename it to <code>COMX</code> where X is your serial port number. (Connect the W806 module to the PC and go to Device Manager to see the number!)
8. Press "Save", and "Exit" to main menu. Again, press "Exit".
9. Afterwards, enter <code>make</code> to compile, or <code>make flash</code> to compile and flash.
10. For <code>make flash</code>, when you are shown "Wait Serial Sync...", briefly press the reset button on the W806 module.
> connecting serial...
>
> serial connected.
>
> wait serial sync.......
>
> serial sync sucess.
>
> mac CC-CC-CC-CC-CC-CC.
>
> start download.
>
> 0% [#####] 100%
>
> download completed.
>
> reset command has been sent.
11. Enjoy the new program written into your W806 module!

## If you ever need your own project folder ([reference](https://github.com/IOsetting/wm-sdk-w806/issues/22)):
1. Create a new folder, example <code>X:/MyW806_Project</code>
2. In the folder, git clone https://github.com/IOsetting/wm-sdk-w806.
3. After cloning, go to the <code>wm-sdk-w806</code> folder, and <code>make menuconfig</code>
4. In <code>Toolchain Configuration</code> -> insert the location of installed C-Sky toolchain binaries.
5. In <code>Download Configuration</code> -> select download port, rename to <code>COMX</code> where X is the serial port number.
6. All your own project is in the <code>wm-sdk-w806/app/</code> folder. You can write your own code within the folder.
7. <code>make</code> to compile, <code>make flash</code> to compile and flash into W806.

## Issues:
- If the flashed app does not work properly in the W806, try <code>make distclean</code> and recompile and reflash again.
