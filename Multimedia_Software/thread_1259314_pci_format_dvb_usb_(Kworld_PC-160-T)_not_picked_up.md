---
title: "pci format dvb_usb (Kworld PC-160-T) not picked up..."
date: 2009-09-06
forum: Multimedia Software
---

### Post by atcrank on 2009-09-06
Hi all,

Just starting out with Ubuntu Jaunty and am liking it so far... but, I want to set up a Kworld DVB-T PC-160-T.  This is a DVB card sold in Australia.  It looks like it started out life as a Kworld DVB-T PC-160-2T, but without the AF9013 tuner fitted.  I found out a little about this card here, and in the downstream links:  [http://www.mythtv.org/wiki/Kworld_DVB-T_PC160-2T](http://www.mythtv.org/wiki/Kworld_DVB-T_PC160-2T)

The card is PCI format mounting a VIA VT6210L USB host controller, which hosts one AF9015A tuner chip as a USB device (I surmise).  It was not working under my plain vanilla install of Ubuntu and updated with kernel 2.6.28-15-generic.

I followed the instructions here [http://linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers) to get up to date V4L2 drivers - this went pretty smoothly.  I am working through the checks at the end, with no success.

I have used modprobe dvb_usb_af9015 to ensure the module is loaded.

I have tried two different firmware files: 
[http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw]("http://www.otit.fi/%7Ecrope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw")
and the one supplied with the kernel.


Below are lshw (-short), lspci, lsusb. lsmod outputs.  I'm not sure the VT6210 Host is currently id'd.  The module af9015 is loading in the kernel, but nothing uses it, and nothing appears in /dev/dvb or /dev/video

Basic Hardware info:

me@Myth-desktop:~$ sudo lshw -short
H/W path          Device      Class       Description
=====================================================
                              system      PROD00000000
/0                            bus         GA-7S748
/0/0                          memory      128KiB BIOS
/0/4                          processor   AMD Athlon(tm) XP 2500+
/0/4/9                        memory      128KiB L1 cache
/0/4/a                        memory      512KiB L2 cache
/0/1b                         memory      512MiB System Memory
/0/1b/0                       memory      512MiB DIMM 200 MHz (5.0 ns)
/0/1b/1                       memory      DIMM 200 MHz (5.0 ns) [empty]
/0/1b/2                       memory      DIMM 200 MHz (5.0 ns) [empty]
/0/100                        bridge      746 Host
/0/100/1                      bridge      SG86C202
/0/100/1/0                    display     NV18 [GeForce4 MX 440 AGP 8x]
/0/100/2                      bridge      SiS963 [MuTIOL Media IO]
/0/100/2.1                    bus         SiS961/2 SMBus Controller
/0/100/2.5        scsi0       storage     5513 [IDE]
/0/100/2.5/0      /dev/sda    disk        250GB WDC WD2500JB-00R
/0/100/2.5/0/1    /dev/sda1   volume      9538MiB EXT3 volume
/0/100/2.5/0/2    /dev/sda2   volume      223GiB Extended partition
/0/100/2.5/0/2/5  /dev/sda5   volume      1906MiB Linux swap / Solaris partition
/0/100/2.5/0/2/6  /dev/sda6   volume      4769MiB Linux filesystem partition
/0/100/2.5/0/2/7  /dev/sda7   volume      217GiB Linux filesystem partition
/0/100/2.5/1      /dev/cdrom  disk        DVD reader
/0/100/2.7                    multimedia  AC'97 Sound Controller
/0/100/3                      bus         USB 1.1 Controller
/0/100/3.1                    bus         USB 1.1 Controller
/0/100/3.3                    bus         USB 2.0 Controller
/0/100/b                      bus         VT82xxxxx UHCI USB 1.1 Controller
/0/100/b.2                    bus         USB 2.0
/1                pan0        network     Ethernet interface


me@Myth-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)

me@Myth-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1b80:c161  


If anyone has made it to the end of all that, and can suggest lines of attack, please please help!


AT

---

### Post by atcrank on 2009-09-25
Solved!
 
The af9015 driver module maintained by Antti Palossari works for this chipset, but didn't work on my card.
 
I thought the problem might be a USBID recognition problem and eventually got up the courage to email Antti (being fairly newb I could have been doing all sorts of things wrong and didn't want to waste his time) before going to bed.
 
When I got up, he had developed a solution and emailed me with it!
 
The problem was that Kworld had removed the first tuner - USBID 1b80:c160, and left ab80:c161.  Since the c161 misbehaves on the dual tuner version at present, it is disabled by default.
 
I think the patch has gone into the mainstream v4l-dvb build now, so it should be as simple as downloading and installing the main tree in future.

---

### Post by deivis on 2010-01-15
Can you post solution that Antti prduced? 

I have same situation than you did. I also have KWolrd PC160-T (lable printed to PCB) and $ lsusb also gave me only ID 1b80:c161. I used latest v4l-dvb source (13.10.2010) so I think solution that solved your broblem is not submited into v4l-dvb jet.

---

### Post by atcrank on 2010-01-16
Antti gave me this link: [http://linuxtv.org/hg/~anttip/af9015](http://linuxtv.org/hg/~anttip/af9015)

It is a few months since then, so I'm not certain that it is going to work. Download the .gz, unpack, make and install.  He also cced me when he asked Mauro Carvalho Chehab to pull updated material.  Since Mauro is the maintainer of V4L-DVB, I assumed it was mainstreamed now - perhaps wrongly.

I have given the machine with this card to a friend, so I'm posting this from a non-Linux machine and it will be tricky to get at the mercurial package I had from antti then if the patches were reverted for some reason.

---

### Post by deivis on 2010-01-19
Thanks, this solution almost helped me to solve problem. But also I had to update af9015 firmware to 4.95.0 what I found from [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/]("http://www.otit.fi/%7Ecrope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/")
Before firmware update I had strange errors what presented by dmesg command. After updating and hard reboot everything worked as expected.

---

