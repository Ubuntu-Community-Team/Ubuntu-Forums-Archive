---
title: "hauppauge 950 problem installing!?!?"
date: 2009-01-22
forum: Multimedia Software
---

### Post by rusted88 on 2009-01-22
I know that there is a lot of how to on this forums, but now I think that I tried to many of them and that it messed up my files . Because now I can't see the dvb folder that's suppose to be in dev. I was wondering if there was some way to reset everything back to normal without having to reinstall Ubuntu again or at least get my dvb folder back with the files in it.

And if someone know wich is the best method to install that 950 tuner please tell me I have been trying to solves this for over a month the closest I got was having only image with linuxtv.

Thx for the help.

---

### Post by rusted88 on 2009-01-22
I also wanted to know if it would be possible to use this tuner with vlc?

---

### Post by wolfen69 on 2009-01-22
first we need to know which chipset it is using. post the output of
```
lspci
``` or ```
lsusb
``` if it is a usb tuner.

---

### Post by rusted88 on 2009-01-22
lspci gave me this


00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)

and  lsusb gave this
Bus 008 Device 004: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 008 Device 002: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 2040:6513 Hauppauge 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 03f0:6204 Hewlett-Packard DeskJet 5150c
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by slick666 on 2009-01-22
I don't know about the hauppage 950 but the lsusb shows that it's at least connecting and can be seen as a usb device.

check out this linux tv wiki about it

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950")

---

### Post by rusted88 on 2009-01-22
> **slick666 said:**
> I don't know about the hauppage 950 but the lsusb shows that it's at least connecting and can be seen as a usb device.

check out this linux tv wiki about it

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950")

i tried the lsusb -v command and I can't see my tuner so I can't continue with the rest of the steps

---

### Post by rusted88 on 2009-01-22
> **rusted88 said:**
> i tried the lsusb -v command and I can't see my tuner so I can't continue with the rest of the steps

Never mind that the list was to long so I just coudn't see it.

---

### Post by rusted88 on 2009-01-24
The only thing that I know that is working is generating the firmware like it'S said on this page [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950")

after that i always get errors and I still don't have de dvb folder in dev

---

### Post by slick666 on 2009-02-11
I actually bought one of my own (950Q actually) and am working on the issue. I wanted to see if rusted88 made out ok?

I think I have everything setup properly. Here is what dmesg says
```
[ 1884.468579] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 1884.468585] tveeprom 0-0050: audio processor is AU8522 (idx 44)
[ 1884.468591] tveeprom 0-0050: decoder processor is AU8522 (idx 42)
[ 1884.468596] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[ 1884.468602] hauppauge_eeprom: hauppauge eeprom: model=72001
[ 1884.478674] xc5000: Successfully identified at address 0x61
[ 1884.478684] xc5000: Firmware has not been loaded previously
[ 1884.478691] DVB: registering new adapter (au0828)
[ 1884.478697] DVB: registering frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[ 1884.479422] Registered device AU0828 [Hauppauge HVR950Q]

```

Is this what you were getting? I'm working on trying to connect using vlc. I'll let you all now how it works.

---

### Post by engle.aj on 2009-02-12
Hey all,

I too am having problems with this card in Ubuntu 8.10.

I can extract the firmware just fine.  However, when I go to compile the driver (em28xx-new), I get the following:

```
:~/HVR950/em28xx-new$ make

running ./build.sh build

make[1]: Entering directory `/home/adam/HVR950/em28xx-new'
rm -rf Module.symvers; 
make -C /lib/modules/`if [ -d /lib/modules/2.6.21.4-eeepc ]; then echo 2.6.21.4-eeepc; else uname -r; fi`/build SUBDIRS=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
make[2]: Makefile: No such file or directory
make[2]: *** No rule to make target `Makefile'.  Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/adam/HVR950/em28xx-new'

```

This is getting to be quite frustrating.  The device doesn't show up as a video device (/dev/video).  Looking for help if you have it.

Thanks.

---

### Post by slick666 on 2009-02-14
The one thing I want to clarify is the difference between 950 and 950Q

**950 NOT EQUAL 950Q**

After looking up the products I found that my 950q has some significant internal changes and my results may not be equated to a 950.

If your using a 950Q the default em28xx seems to work fine for me. All I had to do was download the firmware and copy it to the /lib/firmware

Here they are
> 
!!!!For 950Q ONLY!!!!
sudo su
cd /tmp
wget -q [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)
wget -q [http://www.steventoth.net/linux/xc5000/extract.sh](http://www.steventoth.net/linux/xc5000/extract.sh)
sh extract.sh
cp dvb-fe-xc5000-1.1.fw /lib/firmware


I hope this helps :)

---

### Post by buntunub on 2009-12-29
> **slick666 said:**
> The one thing I want to clarify is the difference between 950 and 950Q

**950 NOT EQUAL 950Q**

After looking up the products I found that my 950q has some significant internal changes and my results may not be equated to a 950.

If your using a 950Q the default em28xx seems to work fine for me. All I had to do was download the firmware and copy it to the /lib/firmware

Here they are


I hope this helps :)

cp: cannot stat `dvb-fe-xc5000-1.1.fw': No such file or directory

Also, does this fix the no sound issue?

---

