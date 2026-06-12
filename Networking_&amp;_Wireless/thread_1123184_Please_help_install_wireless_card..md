---
title: "Please help install wireless card."
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by slwtx2003 on 2009-04-11
I just downloaded and installed ubuntu 8.10 on my computer today.  I honestly had no idea what I was getting myself into, but now that I've started I can't stop!

I am trying to get my netgear wpn111 usb wireless internet card installed on my computer, and though I have found many forums about how to do this, I have no idea what they are saying when talking about codes, or where I put these in...  I don't know anything about linux, and I cannot even seem to find documentation on the basics online.

I tried to install build-essential on the computer so that I could follow some instructions online to get this thing installed, but I get an error;  Error: Dependency is not satisfiable: g++

help please!!

---

### Post by RedSingularity on 2009-04-11
Start off by posting the output of typing "lspci" in the terminal.

---

### Post by slwtx2003 on 2009-04-11
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:09.0 Communication controller: Agere Systems LT WinModem (rev 02)



this what you are looking for?

---

### Post by iponeverything on 2009-04-11
Where are the instructions that you were trying to follow?

---

### Post by slwtx2003 on 2009-04-11
[http://ubuntuforums.org/showthread.php?t=414023](http://ubuntuforums.org/showthread.php?t=414023)

Install newest ndiswrapper + build-essential

is the first instruction that I am trying to follow.  I am trying to install the build-essential program and that is where i am getting the g++ error

---

### Post by iponeverything on 2009-04-11
```
sudo apt-get install build-essential ndiswrapper

```

Try the above command to install build-essential and ndiswrapper
packages and post the output if it fails.

---

### Post by slwtx2003 on 2009-04-11
do i type that code into terminal?

---

### Post by iponeverything on 2009-04-11
yes :)

---

### Post by slwtx2003 on 2009-04-11
cool.  that is where i was lost.

I got an error

e: Couldn't find package build-essential

---

### Post by iponeverything on 2009-04-12
I guess that its hard to download the packages when you don't have an working wireless card!  Can you plug it into a wired connection to get the packages?

---

### Post by RedSingularity on 2009-04-12
If you cant get a wired connection you can get the required packages from another computer, save them to a flash drive and put them on the ubuntu computer.

---

### Post by slwtx2003 on 2009-04-12
where do i get the packages from?  I am not sure what I need!  I downloaded the build-essential_11.4_i386.deb and the 11.3 packages but i get that g++ error

---

### Post by RedSingularity on 2009-04-12
[[url=http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.3/g++-4.3_4.3.2-1ubuntu11_i386.deb]Here]("http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.3/g++-4.3_4.3.2-1ubuntu11_i386.deb%20is%20the%20g++%20package.") is the g++
[/URL]

---

### Post by slwtx2003 on 2009-04-12
now i get another error.

Error: Dependency is not satisfiable: libstdc++6-4.3-dev

when trying to install the g++ 4.3

---

### Post by iponeverything on 2009-04-12
> **slwtx2003 said:**
> now i get another error.

Error: Dependency is not satisfiable: libstdc++6-4.3-dev

when trying to install the g++ 4.3

Things will be much easier for you if you could get box connected to ethernet directly then do the apt-get -- is that not an option?

---

### Post by slwtx2003 on 2009-04-12
now keep in mind that this is a fresh install of ubuntu, so i dont mind messing it up a bit and needing to reinstall..

but i tried to install the libstdc and ti told me to install a gcc base.  when i installed the gcc base it told me to run 

sudo alt-get install -f

i am running it right now and it looks like its uninstalling the ubuntu.  what is this command doing?  if it is messing everything up then i will just reinstall tomorrow and connect directly to internet!

---

### Post by iponeverything on 2009-04-12
```
http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.3/libstdc++6-4.3-dev_4.3.2-1ubuntu11_amd64.deb
```

---

### Post by iponeverything on 2009-04-12
apt-get install -f 

can do some bad things. I would not be surprised if it removed gnome-desktop.. 

If you need to reinstall, we can try to work through this again.

---

### Post by slwtx2003 on 2009-04-12
weird...  it only takes about 10 minutes to reinstall it, so I am not concerned.  what does alt-get install -f do?

I will reinstall right now, and when i wake up in the morning i will hook up directly to the internet and run...

"sudo alt-get update"?

and this will allow me to install the build-essential? or do i need to run the

"sudo alt-get install build-essential ndiswrapper" 

command while connected to the internet!?

---

### Post by iponeverything on 2009-04-12
apt-get install -f tries to fix dependency issues for you. In most cases it best to ignore the system when it tells you to run it. -- look at summary before you hit "y" -- If it wants to remove packages this is almost always bad.

after you reinstall:

sudo apt-get update
sudo apt-get install build-essential ndiswrapper

---

### Post by RedSingularity on 2009-04-12
Thats better.....it will be MUCH easier and faster with a temporary wired connection.

---

### Post by slwtx2003 on 2009-04-12
ok!  Thank you very much for helping out!

I got myself plugged directly into my router, and am on the internet.  I ran the update command and was able to run the

sudo apt-get install build-essential

but when i run the command

sudo apt-get install build-essential ndiswrapper

i get an error that says couldn't find package ndiswrapper.  I have the latest copy of ndiswrapper, but i am not sure how to install it.  I downloaded v1.54(stable) from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) and am assuming it is the latest.

---

### Post by iponeverything on 2009-04-12
sorry try:

```
sudo apt-get install ndiswrapper-utils-1.9
```

I don't think that you have to build it from souce..

(which was reason one would pull down the build stuff)

If you do need to build from source.. its not really a big deal.

post the output of: "find ~|grep ndiswrapper" and I give you a quick howto.

---

### Post by slwtx2003 on 2009-04-12
ok.  I managed to get the drivers installed, but now the intructions are telling me to run this command: 

sudo ndiswrapper load_fw_ar5523 /etc/ndiswrapper/netwpn111/ar5523.bin

but this command is not working.  apparently the load_fw command was removed in previous versions of ndiswrapper?

basically, I cannot get the light on my usb device to come on at all.

he is an output from ndiswrapper -l
athwpn : driver installed
autorun : invalid driver!
netwpn111 : driver installed

...there was an autorun file in the folder where i installed the other 2 inf files!

here is the output of the find ~|grep ndiswrapper:

:~$ find ~|grep ndiswrapper

/home/sonny/Desktop/ndiswrapper-1.54
/home/sonny/Desktop/ndiswrapper-1.54/Makefile
/home/sonny/Desktop/ndiswrapper-1.54/ChangeLog
/home/sonny/Desktop/ndiswrapper-1.54/utils
/home/sonny/Desktop/ndiswrapper-1.54/utils/Makefile
/home/sonny/Desktop/ndiswrapper-1.54/utils/loadndisdriver.c
/home/sonny/Desktop/ndiswrapper-1.54/utils/loadndisdriver
/home/sonny/Desktop/ndiswrapper-1.54/utils/ndiswrapper
/home/sonny/Desktop/ndiswrapper-1.54/utils/ndiswrapper-buginfo
/home/sonny/Desktop/ndiswrapper-1.54/ndiswrapper.8
/home/sonny/Desktop/ndiswrapper-1.54/INSTALL
/home/sonny/Desktop/ndiswrapper-1.54/driver
/home/sonny/Desktop/ndiswrapper-1.54/driver/built-in.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/pnp.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/.hal_exports.h.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/.ndiswrapper.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/rtl.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/ndiswrapper.ko
/home/sonny/Desktop/ndiswrapper-1.54/driver/ntoskernel.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/usb.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/Module.symvers
/home/sonny/Desktop/ndiswrapper-1.54/driver/winnt_types.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/Makefile
/home/sonny/Desktop/ndiswrapper-1.54/driver/.ndiswrapper.ko.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/mkexport.sh
/home/sonny/Desktop/ndiswrapper-1.54/driver/hal_exports.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/crt_exports.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/.iw_ndis.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/ndis.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/ntoskernel_io_exports.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/modules.order
/home/sonny/Desktop/ndiswrapper-1.54/driver/ntoskernel_exports.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/ntoskernel_io.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/crt.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/wrapper.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/usb_exports.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/win2lin_stubs.S
/home/sonny/Desktop/ndiswrapper-1.54/driver/pe_linker.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/wrapmem.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/ndis.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/wrapper.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/ntoskernel.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/workqueue.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/.ndis_exports.h.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/.tmp_versions
/home/sonny/Desktop/ndiswrapper-1.54/driver/.tmp_versions/ndiswrapper.mod
/home/sonny/Desktop/ndiswrapper-1.54/driver/.ndiswrapper.mod.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/.usb.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/.pe_linker.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/pe_linker.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/ndiswrapper.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/.ntoskernel.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/ndiswrapper.mod.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/pe_linker.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/.wrapmem.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/divdi3.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/.rtl.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/.ntoskernel_io_exports.h.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/divdi3.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/pnp.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/.ndis.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/.hal.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/usb.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/loader.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/.crt.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/ntoskernel_io.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/hal.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/ndis.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/ndiswrapper.mod.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/.wrapndis.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/loader.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/wrapper.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/iw_ndis.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/hal.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/wrapndis.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/.divdi3.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/ndiswrapper.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/proc.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/rtl.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/Module.markers
/home/sonny/Desktop/ndiswrapper-1.54/driver/.proc.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/.loader.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/crt.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/.usb_exports.h.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/.pnp.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/loader.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/pnp.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/.wrapper.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/wrapmem.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/iw_ndis.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/.built-in.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/usb.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/proc.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/iw_ndis.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/mkstubs.sh
/home/sonny/Desktop/ndiswrapper-1.54/driver/.rtl_exports.h.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/.ntoskernel_io.o.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/rtl_exports.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/longlong.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/wrapndis.o
/home/sonny/Desktop/ndiswrapper-1.54/driver/.ntoskernel_exports.h.cmd
/home/sonny/Desktop/ndiswrapper-1.54/driver/ndis_exports.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/ntoskernel.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/wrapndis.c
/home/sonny/Desktop/ndiswrapper-1.54/driver/wrapmem.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/lin2win.h
/home/sonny/Desktop/ndiswrapper-1.54/driver/.crt_exports.h.cmd
/home/sonny/Desktop/ndiswrapper-1.54/ndiswrapper.spec
/home/sonny/Desktop/ndiswrapper-1.54/AUTHORS
/home/sonny/Desktop/ndiswrapper-1.54/loadndisdriver.8
/home/sonny/Desktop/ndiswrapper-1.54/README
/home/sonny/Desktop/ndiswrapper-1.51
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/Makefile
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/ChangeLog
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/utils
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/utils/Makefile
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/utils/loadndisdriver.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/utils/ndiswrapper
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/utils/ndiswrapper-buginfo
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/ndiswrapper.8
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/INSTALL
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/rtl.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/usb.h
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/winnt_types.h
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/Makefile
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/ndis.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/ntoskernel_io.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/wrapper.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/win2lin_stubs.S
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/pe_linker.h
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/ndis.h
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/ntoskernel.h
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/workqueue.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/pe_linker.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/ndiswrapper.h
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/divdi3.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/pnp.h
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/usb.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/loader.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/hal.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/loader.h
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/iw_ndis.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/wrapndis.h
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/proc.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/crt.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/pnp.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/wrapmem.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/iw_ndis.h
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/longlong.h
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/ntoskernel.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/wrapndis.c
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/wrapmem.h
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/driver/lin2win.h
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/ndiswrapper.spec
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/AUTHORS
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/loadndisdriver.8
/home/sonny/Desktop/ndiswrapper-1.51/ndiswrapper-1.51/README
/home/sonny/Desktop/ndiswrapper-1.54.tar.gz
/home/sonny/.local/share/Trash/info/ndiswrapper-1.54.trashinfo
/home/sonny/.local/share/Trash/info/ndiswrapper-1.2.54.trashinfo
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/Makefile
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/ChangeLog
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/utils
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/utils/Makefile
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/utils/loadndisdriver.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/utils/ndiswrapper
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/utils/ndiswrapper-buginfo
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/ndiswrapper.8
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/INSTALL
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/rtl.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/usb.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/winnt_types.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/Makefile
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/mkexport.sh
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/ndis.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/ntoskernel_io.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/wrapper.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/win2lin_stubs.S
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/pe_linker.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/ndis.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/ntoskernel.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/workqueue.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/pe_linker.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/ndiswrapper.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/divdi3.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/pnp.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/usb.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/loader.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/hal.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/loader.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/wrapper.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/iw_ndis.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/wrapndis.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/proc.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/crt.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/pnp.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/wrapmem.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/iw_ndis.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/mkstubs.sh
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/longlong.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/ntoskernel.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/wrapndis.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/wrapmem.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/driver/lin2win.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/ndiswrapper.spec
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/AUTHORS
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/loadndisdriver.8
/home/sonny/.local/share/Trash/files/ndiswrapper-1.54/README
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/Makefile
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/ChangeLog
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/utils
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/utils/Makefile
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/utils/loadndisdriver.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/utils/ndiswrapper
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/utils/ndiswrapper-buginfo
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/ndiswrapper.8
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/INSTALL
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/rtl.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/usb.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/winnt_types.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/Makefile
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/mkexport.sh
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/ndis.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/ntoskernel_io.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/wrapper.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/win2lin_stubs.S
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/pe_linker.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/ndis.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/ntoskernel.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/workqueue.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/pe_linker.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/ndiswrapper.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/divdi3.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/pnp.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/usb.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/loader.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/hal.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/loader.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/wrapper.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/iw_ndis.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/wrapndis.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/proc.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/crt.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/pnp.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/wrapmem.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/iw_ndis.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/mkstubs.sh
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/longlong.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/ntoskernel.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/wrapndis.c
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/wrapmem.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/driver/lin2win.h
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/ndiswrapper.spec
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/AUTHORS
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/loadndisdriver.8
/home/sonny/.local/share/Trash/files/ndiswrapper-1.2.54/README

---

### Post by iponeverything on 2009-04-13
phase two -- drop ndiswrapper and go with madwifi.

remove the driver from ndiswrapper.

```
sudo -i
cd /usr/src
wget http://nchc.dl.sourceforge.net/sourceforge/madwifi/madwifi-0.9.4.tar.gz
tar -zxvf madwifi-0.9.4.tar.gz
cd madwifi-0.9.4
make
make install

```

Then reboot.  Every time your kernel gets updated via update, you will have to do the following:

```

su -i
cd /usr/src/madwifi-0.9.4
make clean
make
make install

```

---

### Post by slwtx2003 on 2009-04-13
ok, the only information i could find online about what to do after i get madwifi installed...stated that madwifi does not support usb wireless adapters!  now if that's old information and it does support it then what do i do now?  I have it installed and my wpn111 still has no light.  I can plug it into a windows machine and the light comes right on.

oh, and why do i have to type in the sudo command in front of almost everything i do?  did i not make myself an admin or something?

---

### Post by Tr10 on 2009-04-13
> **slwtx2003 said:**
> ok, the only information i could find online about what to do after i get madwifi installed...stated that madwifi does not support usb wireless adapters!  now if that's old information and it does support it then what do i do now?  I have it installed and my wpn111 still has no light.  I can plug it into a windows machine and the light comes right on.

oh, and why do i have to type in the sudo command in front of almost everything i do?  did i not make myself an admin or something?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

:)

---

### Post by iponeverything on 2009-04-13
> **slwtx2003 said:**
> ok, the only information i could find online about what to do after i get madwifi installed...stated that madwifi does not support usb wireless adapters!  now if that's old information and it does support it then what do i do now?  I have it installed and my wpn111 still has no light.  I can plug it into a windows machine and the light comes right on.

oh, and why do i have to type in the sudo command in front of almost everything i do?  did i not make myself an admin or something?

Sorry about that, somehow or another I thought that was an internal device.. Not sure how I got that idea.. Maybe I got your issue mixed up with someone elses..   Following the instructions from the previous link that you provided regarding ndiswrapper.. did you make progress?  I know that ndiswrapper allows for various windows drivers to be used.. Maybe you could try different versions..

---

### Post by slwtx2003 on 2009-04-13
i think i am tired of fiddling with it!  I know that these usb guys act real weird sometimes, and I can't even get my blue light to come on.  I'd rather get a super long ethernet cable, cause this is frustrating!  :)  it would help if I knew what I was doing in the o/s, but with my ignorance in Linux, and my device not doing what it's supposed to......  yeah!

Though, I am not giving up on ubuntu!  I like it, just need to figure it out, and your guys help has been priceless.  i just needed that little bit of help to get in the door.

---

### Post by iponeverything on 2009-04-14
Here is great lecture that can get you up to speed very quickly with regard to following and understanding most of what is being suggested in these forums -- When you see someone post a bunch of commands to help you solve a problem, it will help you understand "what" as well as the "why".. 

 [http://www.doc.ic.ac.uk/~wjk/UnixIntro/](http://www.doc.ic.ac.uk/~wjk/UnixIntro/)

---

### Post by slwtx2003 on 2009-04-14
Thank you very much for that.  I will definitely get some use out of that page.

---

