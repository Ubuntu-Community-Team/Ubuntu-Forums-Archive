---
title: "Wireless not working oh hp laptop"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by bigrthanu on 2011-09-19
Hello,
I am fairly new to ubuntu and i have an hp pavilion zd7000
and the wireless doesnt work. It hasnt worked since i installled 
ubuntu but im just now deciding to get it fixed.
under the tab in the right top corner where the internet stuff is it says

Wireless Networks:
Device not ready (Firmware missing)

Please help! Try to explain it as simple as possible because im new to using this OS.

Thank you.

---

### Post by wildmanne39 on 2011-09-19
Hi, welcome to the forum! please open a terminal by hitting ctrl+alt+t then paste these commands into it, then post the results here from each command:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by bigrthanu on 2011-09-19
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntu 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux





  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:2d:dc:d9
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too  driverversion=0.9.28 duplex=full ip=192.168.2.2 latency=32 link=yes  maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 ioport:3000(size=256) memory:d2007800-d20078ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:21 memory:d2004000-d2005fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:46:f8:8c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43legacy  driverversion=2.6.38-11-generic firmware=N/A link=no multicast=yes  wireless=IEEE 802.11bg



lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off



0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
usb_storage            43946  0 
uas                    17676  0 
binfmt_misc            13213  1 
nvidia               7098106  26 
rtl8180                35687  0 
snd_intel8x0           33213  2 
arc4                   12473  2 
snd_ac97_codec        105614  1 snd_intel8x0
eeprom_93cx6           12653  1 rtl8180
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
b43legacy             127415  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
mac80211              257001  2 rtl8180,b43legacy
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  3 rtl8180,b43legacy,mac80211
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
irda                  185091  0 
psmouse                73312  0 
soundcore              12600  1 snd
ppdev                  12849  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
serio_raw              12990  0 
lp                     13349  0 
video                  18951  0 
parport_pc             32111  1 
crc_ccitt              12595  1 irda
parport                36746  3 ppdev,lp,parport_pc
cb710_mmc              13380  0 
firewire_ohci          31504  0 
8139too                23208  0 
ssb                    45942  1 b43legacy
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
crc_itu_t              12627  1 firewire_core
cb710                  13734  1 cb710_mmc

---

### Post by wildmanne39 on 2011-09-20
Hi, I need to ask some questions. The card you want to get working is the internal broadcom card correct? 

You are also using an usb wireless adapter correct? what brand is it?

After we install the correct driver and firmware you will need to unplug the usb and restart your computer.

---

### Post by bigrthanu on 2011-09-20
I want the built in wireless to work, and i do not have a usb adapter plugged in. Im using the internet
using the Ethernet cord.

---

### Post by wildmanne39 on 2011-09-20
Hi, that is strange it is showing another wireless driver installed, let's black list it 
```
sudo su
echo "blacklist rtl8180" >> /etc/modprobe.d/blacklist.conf
exit

```
then unplug your wired connection and run this command please:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
then restart your computer.
Thank you

---

### Post by wildmanne39 on 2011-09-20
Hi, if that does not work i need to see the output from this command it is the most important of the commands I need to see.
```
lspci -nn | grep -e 0280 -e 0200 
```
I am very tired so if is is listed I have missed it.
Thank you

---

### Post by bigrthanu on 2011-09-20
The blacklist thing and the other code in that post arent really giving me anything. i try to post the blacklist code and it only pastes the first line.
and the other code does the same.
ill reply in a new reply for the other code youve just asked for, the "main one you needed"
thanks.

---

### Post by bigrthanu on 2011-09-20
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

---

### Post by wildmanne39 on 2011-09-20
Hi, you run each of those commands all at once by coping and pasting into the terminal and they will not show any output back.
Thank you

---

### Post by bigrthanu on 2011-09-20
You dont understand. It wont let me paste all of the code.
When i highlight the code and press copy and paste it into the terminal
it only pastes the 
sudo su And then ask's me for the password. Then i enter the password and it says wrong password. then i re enter it and it says

root@ubuntu:/home/administrator#

---

### Post by wildmanne39 on 2011-09-20
Hi, it looks like the correct driver and firmware is installed.

Ok, copy and paste all three lines of the first command into the terminal the suso su and all other lines at the same time into the terminal when it asks for your password type your user password that you set up when you installed ubuntu, it will be the same one you use to log in, unless you have automatic log in. 

The terminal will not show the password when you are typing it, if the password is correct it will just run the command.

Let's do some trouble shooting post the results of these commands please:
```
sudo iwlist scan
```
```
dmesg | egrep 'b43|firm'
```
```
lsmod | grep b43
```
I am going to bed for tonight, I can not think right I have been on for fifteen hours now, I will finish helping you tomorrow unless someone else does first.
Thank you

---

### Post by bigrthanu on 2011-09-20
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down




[    1.311864] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   12.317407] b43legacy-phy0: Broadcom 4306 WLAN found
[   12.340037] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   12.340059] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   12.364274] b43legacy-phy0 debug: Radio initialized
[   28.461625] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[   28.461631] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[   30.013949] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[   30.013955] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[  113.216040] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  113.216047] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[772166.106825] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[772166.106832] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[772166.712970] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[772166.712977] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[772169.415318] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[772169.415325] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[772169.682884] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[772169.682891] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[809314.262722] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[809314.262729] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[809314.643903] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[809314.643910] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[809314.914343] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[809314.914350] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[809315.842389] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[809315.842396] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[809321.356660] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[809321.356668] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[809321.640438] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[809321.640445] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[892436.309700] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[892436.309707] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[892446.535292] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[892446.535299] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[892447.181665] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[892447.181672] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[892455.466637] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[892455.466644] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[892481.385723] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[892481.385729] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[892482.395005] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[892482.395012] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).





b43legacy             127415  0 
mac80211              257001  2 rtl8180,b43legacy
cfg80211              156212  3 rtl8180,b43legacy,mac80211
ssb                    45942  1 b43legacy

---

### Post by wildmanne39 on 2011-09-20
Hi, alright we are going to approach this from a different angle.

Down load the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here, then unplug your wired connection. Open a terminal and do:
```
cd Desktop
sudo mv b43/* /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
the other commands that you were having trouble with post a screen shot of them pasted into the terminal so I can see how you are doing it, you can take the shot by hitting alt+print screen button.
Thank you

---

### Post by bigrthanu on 2011-09-20
I cant do any of this. It is extremely difficult for me.
Is there a way to do some kind of remote access ?
Id well appreciate it. I love the way ubuntu works i just wish the damn wireless would work.
Thanks

---

### Post by wildmanne39 on 2011-09-20
Hi, I think there is but I am not setup for it, I am not sure it is even allowed.

I will look into it.
Thank you

---

### Post by bigrthanu on 2011-09-20
Okay, thanks.

---

### Post by wildmanne39 on 2011-09-20
Hi, I am reading this link right now to set up what you ask about, please also use this link to do the same.
[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1723-how-to-use-remote-desktop-in-ubuntu-](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1723-how-to-use-remote-desktop-in-ubuntu-)
Thank you

---

### Post by bigrthanu on 2011-09-21
Okay i have set up the remote desktop

---

### Post by AnotherPenguin on 2011-09-21
Hi,
I've been using Linux for about a week and have been trying to get the wireless drivers the entire time. The problem is the Broadcom drivers which are very hard to get. I really wanted to ask, though, if i have b43 cards, will the codes you gave him work for me since he has b43legacy drivers.

---

### Post by wildmanne39 on 2011-09-21
Hi AnotherPenguin, welcome to the forum! most likely no, please post the results of this command here:
```
cat /etc/lsb-release; uname -a
```
```
lspci -nn | grep 0280
```
Thank you

---

### Post by wildmanne39 on 2011-09-21
Hi bigrthanu, PM me when you are ready to try with the information needed.
Thank you

---

### Post by AnotherPenguin on 2011-09-21
The first code gave me this:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux Ubuntu 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 i686 i386 GNU/Linux

The second code gave me this:
08:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

P.S. i really appreciate the help.

---

### Post by garvinrick4 on 2011-09-21
open synaptics and install the one checked marked and remove any other bcm if you
tried others. Take wired cable out and reboot. (link for you to save
Notice I typed bcm in search box to find. (read your link to understand your card bcm4322) you will need to load again some day. Step 1, step 2.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by wildmanne39 on 2011-09-21
Hi, you will also need to install > broadcom-sta-source + broadcom-sta-common if I am not mistaken.
Thank you

---

### Post by garvinrick4 on 2011-09-21
> **wildmanne39 said:**
> Hi, you will also need to install  if I am not mistaken.
Thank you Did not mean to jump in wildmanne39 thought you were off line.
take care. 
Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **STA** drivers can be activated for use.

---

### Post by AnotherPenguin on 2011-09-21
> **garvinrick4 said:**
> 
Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **STA** drivers can be activated for use.

Thank you both so much, I had activated the STA yesterday but since it was missing a few things it hadn't worked. I'm rebooting now and will post again to tell you if it did/ didn't work.

---

### Post by wildmanne39 on 2011-09-21
Ok, we will be here, when we get it working would you consider showing your support for me becoming an ubuntu member by clicking on the red link in my signature? if not that is ok too, and garvinrick4 could use your support as well, but I do not believe he as a link to his application for membership in his signature.
Thank you

---

### Post by AnotherPenguin on 2011-09-21
The wireless drivers worked perfectly. I would like to know what becoming an Ubuntu member does.

---

### Post by garvinrick4 on 2011-09-21
I guess OP is up and running but passed on posting wildmanne39, my other thread has
not posted back must of got X running. Got to go out and clean the pool, see you in a bit
there wildmanne39. Hot as Hell out there, darn. Got rid of Pool man in a fit of inspiration
that I will do that no problem, must have been crazy that day. Got no one left here to swim, just a bit of water to throw money into anymore.

---

### Post by wildmanne39 on 2011-09-21
Hi, it is just a process where it gives us a little more benefits for helping people, like a title under our name that says ubuntu member, and we can print ubuntu business cards,have an ubuntu email address and being an ubuntu member is a requirement before one can be selected as staff member, all positions are volunteer positions no one gets paid.
Thank you

---

### Post by garvinrick4 on 2011-09-21
> The wireless drivers worked perfectly
Thanks for posting there AnotherPenguin, very considerate.

---

### Post by AnotherPenguin on 2011-09-21
I know this is the wrong thread but if your running Ubuntu side by side with windows(i really didn't want to get rid of windows though i like Linux much much more) and you set the Root size to 10GB is that permanent?

---

### Post by wildmanne39 on 2011-09-21
Yes it is, you can manually change it with gparted from a livecd but you have to be very careful, are you wanting to change it?
Thank you

---

### Post by AnotherPenguin on 2011-09-21
Well I don't need to change it right now I have barely used up any space out of the 10GB but I really didn't know I would like Linux this much and if i will be using it more often I want to know if I will have enough space because I tend to eat up hard drive space.

---

### Post by wildmanne39 on 2011-09-21
Hi, did you do a normal dual install? or did you use wubi? and 10 gigs that is just the root partition size correct? and you have a separate partition for home or data?
Thank you

---

### Post by AnotherPenguin on 2011-09-21
I used Wubi and one of the boxes gives you choices on how large you want it to be. In the Disk Utility it says not partitioned. I think there's a separate file for home but I'm not sure.

---

### Post by AnotherPenguin on 2011-09-21
If it helps it falls under Peripheral Devices.

---

### Post by wildmanne39 on 2011-09-21
Hi, wubi is a whole different animal, you should start a new thread on it in absolute beginners, Rubi1200 is good with wubi, he wrote a guide for it, here are some links.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

Also I can tell you that you can use an usb drive and save your data to it and you do not need to worry about partition size, but a wubi install is meant just to be used to see if you like ubuntu then you should do a normal install.

If something happens to windows like a virus or the partition get corrupted you will have ubuntu to fall back on, but using it with wubi ubuntu will be down also. 

I have stayed with ubuntu for easy of use and the forums are the best you will see.
Thank you

---

### Post by AnotherPenguin on 2011-09-21
As far as viruses I was always very paranoid on Windows and have a very good virus protection software from Symantec called Endpoint but they are more famous for Norton. Also for recovery I have Puppy Linux on a USB. Thank you for the links though I'll make sure to check it out and I will also try to become an Ubuntu member when i have the chance.

---

### Post by wildmanne39 on 2011-09-21
Hi, your welcome! enjoy ubuntu and thank you.

---

