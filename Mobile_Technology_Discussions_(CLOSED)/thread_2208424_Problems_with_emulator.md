---
title: "Problems with emulator"
date: 2014-02-28
forum: Mobile Technology Discussions (CLOSED)
---

### Post by suoko on 2014-02-28
I'm trying the ubuntu touch emulator using the ubuntu-sdk interface.
I noticed that the ~/.local/share/ubuntu-emulator owner was root so I was not able to run it at all.
After I changed permissions the emulator is not running yet and here is the log: 


Checking installed emulator package.
ii ubuntu-emulator 0.2+14.04.20140227.1-0ubuntu1
Search configured emulator instances.
Utouch	ubuntu=20140228.1,device=20140115.1,version=212
Detecting device..
* there is no device connected.
Starting the selected emulator.
emulator: autoconfig: -ramdisk /home/gabriele/.local/share/ubuntu-emulator/Utouch/ramdisk.img
emulator: autoconfig: -datadir /home/gabriele/.local/share/ubuntu-emulator/Utouch
emulator: Could not open file: /home/gabriele/.local/share/ubuntu-emulator/Utouch/system/build.prop: No such file or directory
emulator: Coult not find CPU ABI in build properties!
emulator: Default target architecture=arm
emulator: Could not open file: /home/gabriele/.local/share/ubuntu-emulator/Utouch/system/build.prop: No such file or directory
emulator: Could not find target API level / SDK version in build properties!
emulator: Default target API level: 1000
emulator: using core hw config path: /home/gabriele/.local/share/ubuntu-emulator/Utouch/hardware-qemu.ini
emulator: keyset loaded from: /home/gabriele/.android/default.keyset
emulator: trying to load skin file '/usr/share/ubuntu-emulator/skins/EDGE/layout'
emulator: skin network speed: 'full'
emulator: skin network delay: 'none'
emulator: Using initial system image: /home/gabriele/.local/share/ubuntu-emulator/Utouch/system.img
emulator: autoconfig: -initdata /home/gabriele/.local/share/ubuntu-emulator/Utouch/userdata.img
emulator: Physical RAM size: 512MB

emulator: Could not open file: /home/gabriele/.local/share/ubuntu-emulator/Utouch/system/build.prop: No such file or directory
emulator: Coult not find CPU ABI in build properties!
emulator: Default target ABI: armeabi
Content of hardware configuration file:
  hw.cpu.arch = arm
  hw.ramSize = 512
  hw.screen = touch
  hw.mainKeys = yes
  hw.trackBall = yes
  hw.keyboard = no
  hw.keyboard.lid = no
  hw.keyboard.charmap = qwerty2
  hw.dPad = yes
  hw.gsmModem = yes
  hw.gps = yes
  hw.battery = yes
  hw.accelerometer = yes
  hw.audioInput = yes
  hw.audioOutput = yes
  hw.sdCard = yes
  hw.sdCard.path = /home/gabriele/.local/share/ubuntu-emulator/Utouch/sdcard.img
  disk.cachePartition = yes
  disk.cachePartition.path = /home/gabriele/.local/share/ubuntu-emulator/Utouch/cache.img
  disk.cachePartition.size = 66m
  hw.lcd.width = 480
  hw.lcd.height = 800
  hw.lcd.depth = 16
  hw.lcd.density = 160
  hw.lcd.backlight = yes
  hw.gpu.enabled = yes
  hw.camera.back = emulated
  hw.camera.front = none
  vm.heapSize = 48
  hw.sensors.proximity = yes
  hw.sensors.magnetic_field = yes
  hw.sensors.orientation = yes
  hw.sensors.temperature = yes
  hw.useext4 = yes
  kernel.path = /home/gabriele/.local/share/ubuntu-emulator/Utouch/ubuntu-kernel
  kernel.parameters =  androidboot.console=ttyS2
  disk.ramdisk.path = /home/gabriele/.local/share/ubuntu-emulator/Utouch/ramdisk.img
  disk.systemPartition.initPath = /home/gabriele/.local/share/ubuntu-emulator/Utouch/system.img
  disk.systemPartition.size = 200m
  disk.dataPartition.path = /home/gabriele/.local/share/ubuntu-emulator/Utouch/userdata.img
  disk.dataPartition.size = 200m
  avd.name = <build>
.
QEMU options list:
emulator: argv[00] = "/usr/share/android/emulator/out/host/linux-x86/bin/emulator-arm"
emulator: argv[01] = "-show-kernel"
emulator: argv[02] = "-serial"
emulator: argv[03] = "stdio"
emulator: argv[04] = "-cpu"
emulator: argv[05] = "cortex-a9"
emulator: argv[06] = "-append"
emulator: argv[07] = ""
emulator: argv[08] = "-android-hw"
emulator: argv[09] = "/home/gabriele/.local/share/ubuntu-emulator/Utouch/hardware-qemu.ini"
Concatenated QEMU options:
 /usr/share/android/emulator/out/host/linux-x86/bin/emulator-arm -show-kernel -serial stdio -cpu cortex-a9 -append  -android-hw /home/gabriele/.local/share/ubuntu-emulator/Utouch/hardware-qemu.ini
emulator: registered 'boot-properties' qemud service
emulator: nand_add_dev: system,size=0xc800000,initfile=/home/gabriele/.local/share/ubuntu-emulator/Utouch/system.img,pagesize=512,extrasize=0
emulator: mapping 'system' NAND image to /tmp/android-gabriele/emulator-1ja5X5
emulator: nand_add_dev: userdata,size=0xc800000,file=/home/gabriele/.local/share/ubuntu-emulator/Utouch/userdata.img,pagesize=512,extrasize=0
emulator: registered 'boot-properties' qemud service
emulator: Adding boot property: 'dalvik.vm.heapsize' = '48m'
emulator: Adding boot p
libGL error: Couldn't dlopen libudev.so.1 or libudev.so.0, driver detection may be broken.
emulator-arm: ../../../../src/loader/loader.c:129: asserted_dlsym: Assertion `result' failed.
roperty: 'qemu.sf.lcd_density' = '160'
emulator: Adding boot property: 'qemu.hw.mainkeys' = '1'
emulator: Adding boot property: 'qemu.sf.fake_camera' = 'back'
emulator: nand_add_dev: cache,size=0x4200000,file=/home/gabriele/.local/share/ubuntu-emulator/Utouch/cache.img,pagesize=512,extrasize=0
emulator: Initializing hardware OpenGLES emulation support
signal: aborted

---

### Post by anywnztj on 2014-03-01
Amost the same problem with you.My log:
------------------------------------------------------------------------------------
[COLOR=#888888]Checking installed emulator package.[/COLOR]
ii ubuntu-emulator 0.2+14.04.20140227.1-0ubuntu1
[COLOR=#888888]Search configured emulator instances.[/COLOR]
ubuntu-emulator	ubuntu=20140228.1,device=20140115.1,version=212
ubuntu-touch	ubuntu=20140301.1,device=20140115.1,version=215
[COLOR=#888888]Detecting device..[/COLOR]
[COLOR=#888888]* there is no device connected.[/COLOR]
[COLOR=#888888]Starting the selected emulator.[/COLOR]
emulator: autoconfig: -ramdisk /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/ramdisk.img
emulator: autoconfig: -datadir /home/ming/.local/share/ubuntu-emulator/ubuntu-touch
emulator: Could not open file: /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/system/build.prop: No such file or directory
emulator: Coult not find CPU ABI in build properties!
emulator: Default target architecture=arm
emulator: Could not open file: /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/system/build.prop: No such file or directory
emulator: Could not find target API level / SDK version in build properties!
emulator: Default target API level: 1000
emulator: using core hw config path: /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/hardware-qemu.ini
emulator: keyset loaded from: /home/ming/.android/default.keyset
emulator: trying to load skin file '/usr/share/ubuntu-emulator/skins/EDGE/layout'
emulator: skin network speed: 'full'
emulator: skin network delay: 'none'
emulator: Using initial system image: /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/system.img
emulator: autoconfig: -initdata /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/userdata.img
emulator: Physical RAM size: 512MB


emulator: Could not open file: /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/system/build.prop: No such file or directory
emulator: Coult not find CPU ABI in build properties!
emulator: Default target ABI: armeabi
Content of hardware configuration file:
  hw.cpu.arch = arm
  hw.ramSize = 512
  hw.screen = touch
  hw.mainKeys = yes
  hw.trackBall = yes
  hw.keyboard = no
  hw.keyboard.lid = no
  hw.keyboard.charmap = qwerty2
  hw.dPad = yes
  hw.gsmModem = yes
  hw.gps = yes
  hw.battery = yes
  hw.accelerometer = yes
  hw.audioInput = yes
  hw.audioOutput = yes
  hw.sdCard = yes
  hw.sdCard.path = /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/sdcard.img
  disk.cachePartition = yes
  disk.cachePartition.path = /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/cache.img
  disk.cachePartition.size = 66m
  hw.lcd.width = 480
  hw.lcd.height = 800
  hw.lcd.depth = 16
  hw.lcd.density = 160
  hw.lcd.backlight = yes
  hw.gpu.enabled = yes
  hw.camera.back = emulated
  hw.camera.front = none
  vm.heapSize = 48
  hw.sensors.proximity = yes
  hw.sensors.magnetic_field = yes
  hw.sensors.orientation = yes
  hw.sensors.temperature = yes
  hw.useext4 = yes
  kernel.path = /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/ubuntu-kernel
  kernel.parameters =  androidboot.console=ttyS2
  disk.ramdisk.path = /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/ramdisk.img
  disk.systemPartition.initPath = /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/system.img
  disk.systemPartition.size = 200m
  disk.dataPartition.path = /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/userdata.img
  disk.dataPartition.size = 200m
  avd.name = <build>
.
QEMU options list:
emulator: argv[00] = "/usr/share/android/emulator/out/host/linux-x86/bin/emulator-arm"
emulator: argv[01] = "-show-kernel"
emulator: argv[02] = "-serial"
emulator: argv[03] = "stdio"
emulator: argv[04] = "-cpu"
emulator: argv[05] = "cortex-a9"
emulator: argv[06] = "-append"
emulator: argv[07] = ""
emulator: argv[08] = "-android-hw"
emulator: argv[09] = "/home/ming/.local/share/ubuntu-emulator/ubuntu-touch/hardware-qemu.ini"
Concatenated QEMU options:
 /usr/share/android/emulator/out/host/linux-x86/bin/emulator-arm -show-kernel -serial stdio -cpu cortex-a9 -append  -android-hw /home/ming/.local/share/ubuntu-emulator/ubuntu-touch/hardware-qemu.ini
emulator: registered 'boot-properties' qemud service
emulator: nand_add_dev: system,size=0xc800000,initfile=/home/ming/.local/share/ubuntu-emulator/ubuntu-touch/system.img,pagesize=512,extrasize=0
emulator: mapping 'system' NAND image to /tmp/android-ming/emulator-QzWtdh
emulator: nand_add_dev: userdata,size=0xc800000,file=/home/ming/.local/share/ubuntu-emulator/ubuntu-touch/userdata.img,pagesize=512,extrasize=0
emulator: registered 'boot-properties' qemud service
emulator: Adding boot property: 'dalvik.vm.heapsize' = '
libGL error: Couldn't dlopen libudev.so.1 or libudev.so.0, driver detection may be broken.
emulator-arm: ../../../../src/loader/loader.c:129: asserted_dlsym: Assertion `result' failed.
48m'
emulator: Adding boot property: 'qemu.sf.lcd_density' = '160'
emulator: Adding boot property: 'qemu.hw.mainkeys' = '1'
emulator: Adding boot property: 'qemu.sf.fake_camera' = 'back'
emulator: nand_add_dev: cache,size=0x4200000,file=/home/ming/.local/share/ubuntu-emulator/ubuntu-touch/cache.img,pagesize=512,extrasize=0
emulator: Initializing hardware OpenGLES emulation support
signal: aborted (core dumped)
------------------------------------------------------------------------------------
Waiting for someone to help us.

---

### Post by anywnztj on 2014-03-01
I fix this issue now while get another issue.By doing this:
> sudo apt-get install libudev1:i386
You can have a try!

---

### Post by anywnztj on 2014-03-01
Ok.I reboot the emulator several times and wait for a long time and then it works!!

---

### Post by bagustris on 2014-03-02
Thanks! it works for me.

---

### Post by suoko on 2014-03-02
Thanks, that works for me too.
I'm now facing a minor problem with the b2g desktop emulator version b2g-30.0a1.multi.linux-x86_64.tar.bz2 (see video attachment)

---

### Post by vgerris on 2014-03-09
> **anywnztj said:**
> I fix this issue now while get another issue.By doing this:

You can have a try!

Thanks a lot, that made it working on my ubuntu 14.04 64 bit install

---

### Post by wangji on 2014-03-29
May this interest you to try :  

                                     [http://sourceforge.net/projects/toysbox/files/Android-CyanogenMod/](http://sourceforge.net/projects/toysbox/files/Android-CyanogenMod/)

it's quite fast and smooth ;either with live_iso or live_usb or installed on ubuntu x32/x64  both ok

---

### Post by uliraich on 2014-10-22
Hi,
I get the ubuntu-emulator running but see multicolored vertical stripes instead of the Ubuntu violet background.
Any clue where this could come from?
I am using an Intel Mobile 4 Chipset.
When trying to compile the emulator I get:

host C++: libicui18n-host <= external/icu4c/i18n/digitlst.cpp
In file included from external/icu4c/i18n/digitlst.cpp:41:0:
/usr/include/c++/4.8/limits:1407:35: error: template argument 1 is invalid
     struct numeric_limits<__int128>
                                   ^
/usr/include/c++/4.8/limits:1481:44: error: template argument 1 is invalid
     struct numeric_limits<unsigned __int128>
                                            ^

Uli

---

