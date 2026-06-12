---
title: "Dell inspiron 1545 wireless drivers?"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by GutsyGIbboned on 2009-02-06
I installed linux on my laptop when windows screwed up and my disk to install it stopped working.

I don't have my service tag with me (at college) but can anyone point me in the direction of wireless drivers for it as my ethernet port doesn't work and I need net access..?

I have an openSUSE cd aswell so if these drivers work on both even better.

Thanks..

---

### Post by Ayuthia on 2009-02-06
You need to identify your wireless card in Linux first.  If you can go into Ubuntu, please open up a Terminal and type:
```
lspci -nn
```
It will return a list of pci devices.  Look for the ones that contain Network Controller or Ethernet Controller.  They will be your network devices.  One of them should be listed with wireless in it or 802.11.  That is your wireless card.  If you can report back the make, model, and chipset, we can try to help you find what you need.  For example, mine returns:
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
```
The information that we need to know is that it is a Broadcom (make) BCM4311 (model) 14e4:4311 (chipset).

Also let us know which version of Ubuntu you are using (Gutsy 7.10, Hardy 8.04/8.04.1/8.04.2, Intrepid 8.10).  There have been a few new wireless modules that have been added during the last couple of releases.

---

### Post by superprash2003 on 2009-02-06
have you tried system->admin->hardware drivers?

---

### Post by OwenHell on 2009-09-12
new guy, same problem, I have a dell inspiron 1545 running 9.04 that has a Broadcom BCM 412 14e4:4315 is there a package  that can solve all my WiFi problem.     I do have a request/question Linux mint is a sibling of ubuntu and i LOVE both version what I love in in Linux mint is that just make it work back end model, In ubuntu it is the GUI. Linux mint just &quot;looks&quot; to much like 95/XP.   if you know of a ubuntu theme that could put on mint or is there instruction that i can get mint repository  on ubuntu  I do think you for any help, so thank you.

---

### Post by Pepe Lebuntu on 2009-10-20
> **Ayuthia said:**
> You need to identify your wireless card in Linux first.  If you can go into Ubuntu, please open up a Terminal and type:
```
lspci -nn
```It will return a list of pci devices.  Look for the ones that contain Network Controller or Ethernet Controller.  They will be your network devices.  One of them should be listed with wireless in it or 802.11.  That is your wireless card.  If you can report back the make, model, and chipset, we can try to help you find what you need.  For example, mine returns:
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
```The information that we need to know is that it is a Broadcom (make) BCM4311 (model) 14e4:4311 (chipset).

Also let us know which version of Ubuntu you are using (Gutsy 7.10, Hardy 8.04/8.04.1/8.04.2, Intrepid 8.10).  There have been a few new wireless modules that have been added during the last couple of releases.

Hi there,

Just bought a Dell Inspiron 1545 for my wife, and everything is working fine, except the wireless. It won't even recognise that there are any wireless signals, even though there are. When I go to System>Admin>Hardware Drivers, it says that it's using a Broadcom one.

I checked for the code you requested, and got this:

> 09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

Any help would be much appreciated.

---

### Post by Pepe Lebuntu on 2009-10-24
bump. Any help?

---

### Post by f4k1r on 2009-10-24
Even I have the same problem. Plz help!!!

---

### Post by f4k1r on 2009-10-24
try this link...
i followed it and now its working
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by Pepe Lebuntu on 2009-10-25
> **f4k1r said:**
> try this link...
i followed it and now its working
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Thanks f4k1r. So, I've downloaded the 32 bit driver (I assume that's the right one), but from there what do I do with it? (forgive the newbie question!) Where should I extract it to? Install it to? Would you mind giving me an idea of what to do from here? 

Thanks for your patience and help - really, really appreciate it.

---

### Post by f4k1r on 2009-10-25
I followed all the instructions in the Readme file one by one and it worked, you also give it a try and post if you face any problem.

once you follow all the instructions then go to hardware drivers and activate the driver to use and restart once.

---

### Post by dnoob on 2009-11-23
New guy with the same problem.  I have followed the directions and I have downloaded the file but I have not been able to get the file to run.  I can't find the ReadMe file.  I feel like I am so close to getting it, lol.




I am retarded, followed the link and found it.

---

### Post by steven1664 on 2009-11-23
When you install if you can plug into your wireless router with an Ethernet cable you can activate your driver for your wireless card through system>administration>hardware drivers

---

### Post by dnoob on 2009-11-23
I followed the directions but it said that I did not have the permissions to remove the files.

I tried the Admin and hardware drivers thing as well, it said no.

---

### Post by steven1664 on 2009-11-25
Ok what happened when you went to hardware drivers?  Not to be rude but it wont just tell you no.  

Try this open up a terminal and type

sudo apt-get update

Then let that run then when connected with an ethernet cable to your router go to 

system>administration>hardware drivers

It will say searching for hardware drivers.  Then when it comes up click on your wireless driver which I am assuming it is the Broadcom STA wireless driver.

Click on it and on the bottom right of the box there will be a button that says activate.  It is very important that you are connected to your router with an ethernet cable so that you can download the driver and it will activate it once it is downloaded and you will be able to use your wireless.

Let me know if you have any other issues with it and I will try and help you out

---

### Post by poison.designs on 2009-12-16
I've got the same computer and I'm still having issues.

:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

(That's the first time ALL that has come up, usually it just lists my wireless and eth)

As I followed the instructions on Broadcom's site, I ran into another problem:

$ dir
Desktop    Downloads         hybrid_wl    Pictures  Templates
Documents  examples.desktop  Music    Public      Videos
$ cd hybrid_wl
$ dir
built-in.o  Module.markers  README.txt            wl.ko     wl.o
lib        modules.order   src                wl.mod.c
Makefile    Module.symvers  wireless-driver.tar.gz  wl.mod.o

$ lsmod | grep "b43\|ssb\|wl"
b43                   136552  0 
mac80211              210104  1 b43
cfg80211              109144  2 b43,mac80211
led_class               5256  1 b43
ssb                    40944  1 b43
$ rmmod b43
ERROR: Removing 'b43': Operation not permitted
$ rmmod ssb
 ERROR: Module ssb is in use by b43
 $ rmmod wl
 ERROR: Module wl does not exist in /proc/modules

$ modprobe lib80211
FATAL: Error inserting lib80211 (/lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211.ko): Operation not permitted

I also tried plugging my computer directly into my router. At first, it didn't work, but I guess it's decided to start playing nice. But for some reason I'm not seeing anything listed in hardware drivers. Last night, there were two listing for broadcom (I think it was) and only one would let me activate. Where'd they go?

I'm at a loss. Any suggestions?

---

### Post by reve99 on 2009-12-18
thanks, i'll try it too

---

### Post by Some Penguin on 2009-12-18
> **poison.designs said:**
> I've got the same computer and I'm still having issues.
$ rmmod b43
ERROR: Removing 'b43': Operation not permitted
$ rmmod ssb
 ERROR: Module ssb is in use by b43
 $ rmmod wl
 ERROR: Module wl does not exist in /proc/modules

$ modprobe lib80211
FATAL: Error inserting lib80211 (/lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211.ko): Operation not permitted


Were you not operating as root?

---

### Post by Sniffer on 2009-12-18
I have one as well and to solve my problem i have installed by synaptic bcmwl-kernelsource package, restart and everything working.

---

### Post by reve99 on 2009-12-18
running ,running

---

### Post by jeremy1701 on 2010-02-04
I have this same computer and also had the wireless problem when I installed Ubuntu 9.10. I found that the bcmwl package that came with the install disk was corrupt and not installing properly. I downloaded and installed an updated package and it's now working perfectly.

---

### Post by Pepe Lebuntu on 2010-02-04
For anybody else who might be scouting around for whether this kinda computer is suitable, I'll just tell our story.

I bought the Dell 1525 for my wife. We weren't aware of jeremy's solution at the time (as you can probably see from page 1 of this thread), and it drove us crazy. We eventually got it fixed with a linux-guru friend of ours. But APART from that, it's an awesome computer and runs very nicely on ubuntu. In fact, we were so happy with it, we actually gave my wife's computer away to her parents for Christmas, and bought another one!

BUT, here's the tip - this is the lesson we learned the second time we ordered one: if you buy off the Dell website (and if you're buying Dell, you really should!), you can customise the wireless as part of the ordering process. For like $30 more or something, you can get the exact same wireless card as a Dell Mini 10, which ubuntu picks up immediately. It's also got stronger range and download ability (from what I understand). It seems like Dell have chucked some cheap-and-nasty Broadcom wireless card into their standard config for the 1545 - I don't know, maybe they're tired of them lying around the factory. If you avoid these and go for the upgrade, this is BY FAR the easiest solution.

---

### Post by bobdeveaux on 2010-03-03
> **f4k1r said:**
> I followed all the instructions in the Readme file one by one and it worked, you also give it a try and post if you face any problem.

once you follow all the instructions then go to hardware drivers and activate the driver to use and restart once.

Thank you. I registered just to say this worked :-)

Downloaded:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Followed the instructions in readme.

Connected to wireless within 5 seconds of installing driver.

Thank you! :-)

---

### Post by lawentzel on 2010-05-08
I found another site that suggested going into Synaptic Package Manager and searching for "broadcom". After reinstalling those drivers, I rebooted, and the system found the wireless drivers with no problem.

I did need to hook my laptop up via a wired connection to get the drivers reinstalled.

---

### Post by kashifmehmood on 2010-05-09
Dear friends,

Thx for the useful info on this thread. My problem is slightly unique in the sense that the Broadcom STA drivers on my 1545  are working fine (about 70% of the time) but the remaining 30% of the time, I have to suffer dropped internet connections (Ubuntu gives the message "xxx Disconnected). I have to restart the laptop or try again after 10-15 mins.

Any help would be highly appreciated.

---

### Post by Frozen North on 2010-09-16
Owen, Gutsy, Pepe

Don't know if this is solved yet but this is how I solved it (on Mint 9 which is Ubuntu-based):

Follow the link that F4k1r gave and do what it says.  I could get the internet working during the current login session but try as I might I could not get it to work after a re-start.  However!  After a couple of gos at this without success I discovered that once the laptop had gone on-line, the correct Broadcomm driver was offered in the 'hardware' icon (sorry, not that familiar with Ubuntu;))

I installed the driver whilst on-line and had no problems since - in fact I now get better wireless reception than on any other machine

I hope this helps

Cheers!

---

### Post by OooBuntuRox on 2010-09-24
Has anyone had any success with any WiFi-N cards in the 1545? If yes, please contribute at this thread:

[http://ubuntuforums.org/showthread.php?p=9882723#post9882723](http://ubuntuforums.org/showthread.php?p=9882723#post9882723)

Thanks, OooBuntuRox, :guitar:

---

### Post by atul.ctray on 2011-02-21
Hi.. thnx 4 the solution mate... just reinstalled the drivers from the package manager and restarted... Found my laptop to be connected to the wi-fi network when the desktop loaded..

---

### Post by aperomsik on 2011-05-04
I too have a Dell 1545. In Lucid it worked fine, I think I was using ndiswrapper back then though. In Maverick I think I switched to STA. Over the life span of Maverick I found that with some kernel updates the wireless would only work on every other reboot. The latest kernels for Maverick actually seem to be working pretty well. So of course it's time to switch to Natty. With Natty I find that if I uninstall and reinstall STA, then it works on the next boot, or perhaps the boot after that. Once it is working, it remains working when I hibernate and resume -- a process that seems more reliable than under Maverick, mostly. However when I shut down and reboot I couldn't figure out how to get the wireless to work again, with several more reboots it didn't come back until I uninstalled and reinstalled STA again (using jockey-gtk). 

Any ideas?

lshw excerpt:

```
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth4
                version: 01
                serial: 70:1a:04:13:fc:60
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.247.4 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:f69fc000-f69fffff


```

---

### Post by aperomsik on 2011-05-10
I *think* I have it working more reliably now... I added a file /etc/modprobe.d/blacklist-ndiswrapper.conf containing the single line "blacklist ndiswrapper" without the quotes, and the next reboot was OK.

---

### Post by Akusa on 2011-08-01
Hopefully this does not count as thread necromancy.
My sister has a Dell Inspiron 1545 that has the 10.04 version of Ubuntu on it.  I was following the readme on [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and ran into a few problems.  I tried to reinstall what looked like a pre-installed version of Broadband driver, but could not and thus removed it.  When I tried untarring the tarball I also ran into a few problems...did the syntax change at all or are there requirements for a "path"?  I'm sorry, this is my first time touching a version of Linux :???:

---

### Post by wildmanne39 on 2011-08-01
Hi, run these commands in a terminal please
```
sudo lshw -C network
```
```
lsmod
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Akusa on 2011-08-02
Thanks for the quick reply.  I think that Ubuntu is working a bit funky on my laptop since I cannot perform a lot of the code on the online tutorials for installing tar.gz files (fail @sudo commands, apt-get commands, cannot find the build-essential package, and internet plugins fail)
==========================================
```
sudo lshw -C network
```If I ever try to input a sudo command, I am asked for a password, but  cannot input anything unless I hit enter, and after repeating 3 times it  quits.

Using a sudo su code and logging on to root I get:
```
*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:09:af:35
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2  driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.7 latency=0  link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:35:43:f2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```==========================================
```
lsmod
```Gives:
```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      52042  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   163556  0 
dell_wmi                1793  0 
i915                  288611  3 
drm_kms_helper         29329  1 i915
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57374  0 
mac80211              205402  1 b43
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
dell_laptop             6888  0 
dcdbas                  5422  1 dell_laptop
cfg80211              126144  2 b43,mac80211
led_class               2864  1 b43
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
psmouse                63677  0 
serio_raw               3978  0 
drm                   162377  4 i915,drm_kms_helper
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
usb_storage            39841  0 
sky2                   40807  0 
ssb                    38934  1 b43
ahci                   32360  2 

```==========================================
```
lspci -nn | grep 0280
```Gives:
```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```==========================================
```
iwconfig
```Gives:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```==========================================
```
rfkill list all
```Gives:
```
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```==========================================

---

### Post by wildmanne39 on 2011-08-02
Hi, it looks like the driver or firmware is not installed correctly, open synaptic and type bcm into the search box and you will see everything that is installed for your broadcom card.

Uninstall everything that has a green square next to it, then restart your computer.

Open the terminal and copy and paste this into it then hit enter.
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-installer
``` 
then disconnect your wired connection and restart your computer and it should work.

Also when you type your password into the terminal it does not show it on the screen, after you finished typing it hit enter and if the password is correct it should perform the command you told it too.


A lot of commands that are ran in the terminal do not show the outcome of the command in the terminal.

Thank you

---

### Post by Akusa on 2011-08-02
Mmm, I'd just like to verify:

On Synaptic Searching BCM (Name) gives:
libcman-dev
libscman3
(both do not have a green square)

Searching BCM (Name and Description) gives:
libapache2-mod-php5
libapache2-mod-php5filter
libcman-dev
libscman3
php5-cgi
php5-cli
(No green square)
and libklibc (green square)

Since quick search doesn't offer any packages with green square

The description for libklibc:
klibc is intended to be a minimalistic libc subset for use with
initramfs.  It is deliberately written for small size, minimal
entanglement, and portability, not speed.  It is definitely a work in
progress, and a lot of things are still missing.

Wasn't strikingly Broadband related, I'd just like to check :D thanks a bunch though!

---

### Post by wildmanne39 on 2011-08-02
Hi, take a screenshot of that window in synaptic and post it here by clicking on the paper clip in the reply window.

The only things you need to worry about is the b43 cutter,the ones that begin with broadcom, and anything with bcm or b43 in it.

The reason the drivers are not showing up in synaptic is because you installed them from the terminal right?
Thank you

---

### Post by wildmanne39 on 2011-08-02
Hi, post the results of these commands please:
```
dmesg | grep wlan0
```
```
dmesg | grep firmware
```
```
lsmod | grep b43
```
Thank you

---

### Post by witeshark17 on 2011-08-02
> **wildmanne39 said:**
> Hi, it looks like the driver or firmware is not installed correctly, open synaptic and type bcm into the search box and you will see everything that is installed for your broadcom card.

Uninstall everything that has a green square next to it, then restart your computer.

Open the terminal and copy and paste this into it then hit enter.
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-installer
```then disconnect your wired connection and restart your computer and it should work.

Also when you type your password into the terminal it does not show it on the screen, after you finished typing it hit enter and if the password is correct it should perform the command you told it too.


A lot of commands that are ran in the terminal do not show the outcome of the command in the terminal.

Thank you Suppose what we find in synaptic package manager are not marked green; wouldn't work to simply mark and install them?

---

### Post by wildmanne39 on 2011-08-02
Hi, you can but it is easier to just install from the terminal with the command I gave you that way you make sure you install the right ones.

Also there is still a chance we will have to blacklist some drivers after you install the correct driver and firmware.
Thank you

---

### Post by Akusa on 2011-08-02
Trying to upload a screenshot of synaptic using the paperclip (something like invalid file error).
I'm going to trust this image hosting site that I've never used before:
[IMG]http://i51.tinypic.com/whxweq.png[/IMG]

Q: "The reason the drivers are not showing up in synaptic is because you installed them from the terminal right?"

A: While going through the readme file, I noticed that there was a b43 file similar to Broadband Tar.gz file that was mentioned in the link earlier.  However when I tried to follow the steps of: How To Install a Pre-Compiled Driver, there were no results so I decided on attempting a fresh install.

When doing the fresh install I couldn't get past the build steps: "Untarring the Proper Tarball" and "Building the Driver as a Linux Loadable Kernal Module (LKM)"... I'm suspecting that it is because I was incapable of downloading the dev  "the proper tools,packages, header files and libraries to build a standard a kernel module" mentioned since the steps of 
```

# apt-get install build-essential linux-headers-generic
# apt-get build-dep linux

```
always gave an error of:
```

Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

```

Right now I think that I removed a similar driver but did not correctly fresh install the one in the link...

---

### Post by nm_geo on 2011-08-02
You need sudo to do apt-get

Please do these before anything else

```
sudo apt-get update && sudo apt-get upgrade
```

Just copy and paste in the terminal >>> hit enter

---

### Post by Akusa on 2011-08-02
> **wildmanne39 said:**
> Hi, post the results of these commands please: 
```
dmesg | grep wlan0
```

Gives:
empty space...


```
dmesg | grep firmware
```

Gives:
```

[   10.256247] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   10.306022] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   10.308284] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   10.345245] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   10.348035] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   10.355169] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   47.180276] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   47.182054] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   47.183907] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

```
lsmod | grep b43
```

Gives:
```

b43                   163556  0 
mac80211              205402  1 b43
cfg80211              126144  2 b43,mac80211
led_class               2864  1 b43
ssb                    38934  1 b43

```

---

### Post by nm_geo on 2011-08-02
Akusa read the message just before yours ...
You really need to update & upgrade and you are running 10.04 correct?

---

### Post by Akusa on 2011-08-02
> **nm_geo said:**
> You need sudo to do apt-get

Please do these before anything else

```
sudo apt-get update && sudo apt-get upgrade
```Just copy and paste in the terminal >>> hit enter

I'm surprised, that actually worked. :-o
I guess I'll try to install the driver then.

---

### Post by nm_geo on 2011-08-02
> **akusa said:**
> i'm surprised, that actually worked. :-o
i guess i'll try to install the driver then.


wait..

You have a driver B43 installed already..

Try 

```
sudo modprobe b43
```

Did the updates and upgrade finish already?

---

### Post by wildmanne39 on 2011-08-02
Hi, do not try the way I told you too, I did not realize you needed to do it a different way in 10.04. 

I am sorry about that let's do what nm_geo says.
Thank you

---

### Post by nm_geo on 2011-08-02
You were doing fine wildmanne we need to get Joseph to fix that sticky..

---

### Post by Akusa on 2011-08-02
Mmm I've followed the update for apt-get and tried to get build-essential (but ran into the same problem of 

```

Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

```Typing 
```

sudo modprobe b43

```Doesn't appear to do anything and just starts a new line...

-Well I guess I'll need to frequently refresh this page, haha.  And thanks for the help, it's a really overwhelmingly supportive online community, really great!

Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid

is what pops up

---

### Post by nm_geo on 2011-08-02
Check Synaptic for that build-essential 

Let us know what you see...

---

### Post by nm_geo on 2011-08-02
Question you do have ethernet cable connection correct?

I saw you had an assigned IP in the earlier post and made an assumption.  Those get me in trouble all the time.. Cable in computer right?

---

### Post by Akusa on 2011-08-02
Searching Build-Essential yields no results
Searching Build Essential yields: libagg-dev

I'm not too sure if the b43 driver was installed since I followed these steps:
(Although I could only find some b43 variant and could not reinstall in through synaptic, the only choice was to remove package).
Fresh installation:
------------------
1: Remove any other drivers for the Broadcom wireless device.

There are several open source drivers that are used to drive Broadcom 802.11
chips such as b43 and ssb. They will conflict with this driver and need
to be uninstalled before this driver can be installed.  Any previous 
revisions of the wl driver also need to be removed.

Note: On some systems such as Ubuntu 9.10, the ssb module may load during
boot even though it is blacklisted (see note under Common Issues on how to
resolve this). Nevertheless, ssb still must be removed
(by hand or script) before wl is loaded. The wl driver will not function 
properly if ssb the module is loaded.

# lsmod  | grep "b43\|ssb\|wl"

If any of these are installed, remove them:
# rmmod b43
# rmmod ssb
# rmmod wl

To blacklist these drivers and prevent them from loading in the future:
# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
-------------------------------------------------------------------------------------------
Since I don't have any personal files on here would you recommend that I reinstall the 10.04 OS completely and get back the preinstalled version of the Broadcom driver?

---

### Post by witeshark17 on 2011-08-02
Finding the packages in synaptic and mark + install worked for me - happily on wireless now  thanks everyone! :KS:popcorn:

---

### Post by nm_geo on 2011-08-02
Well you could do that but I think if you have the ethernet cable attached we can fix it...

When you go to Synaptic and do a search in the box like _build_  then hit enter you should see it.. 

That is why I am wondering  what we have here right now..

try this in terminal

```
nm-tool
```

Just copy and paste the command then results..

---

### Post by wildmanne39 on 2011-08-02
Hi, I am glad you got it working. 
Thank you nm_geo.

---

### Post by Akusa on 2011-08-02
Ah actually I realized that there was a history function on Synaptic. 

The B43-related package I removed was: bcmwl-modaliases

---

### Post by nm_geo on 2011-08-02
Ok np DO YOU HAVE ethernet cable attached ?? ... Please answer that one for me..

```
nm-tool
```

Please

---

### Post by nm_geo on 2011-08-02
> **witeshark17 said:**
> Finding the packages in synaptic and mark + install worked for me - happily on wireless now  thanks everyone! :KS:popcorn:

Cool witeshark17..

---

### Post by Akusa on 2011-08-02
Yes I do have ethernet attached -wince- it's the only way that I can achieve access to this forum :(.  On a bit of a side note:

Going through:
```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
``` 

Allowed me to update Synaptic and now I can find build-essential, banzai!  I guess I can try reinstalling the driver if I need to.  Um yes I shall input that bit of code now...

---

### Post by Akusa on 2011-08-02
```

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:22:5F:35:43:F2

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:23:AE:09:AF:35

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             71.242.0.12


```

---

### Post by nm_geo on 2011-08-02
Just install from Synaptic.. b43-fwcutter
Read what it says.. in10.04 the b43-fwcutter does the firmware install.
If it shows to be installed mark it for re-install.. apply

---

### Post by Akusa on 2011-08-02
Yes I was looking at the B43_fwcutter since it was mentioned earlier and I saw it there...currently installing it :).  I am seeing the light at the end of the tunnel...ah~~and it is installed.  So should I restart the labby and pull out the ethernet cord as well?

Banzai Flash Player is working!

---

### Post by nm_geo on 2011-08-02
> **Akusa said:**
> Yes I was looking at the B43_fwcutter since it was mentioned earlier and I saw it there...currently installing it :).  I am seeing the light at the end of the tunnel...ah~~and it is installed.  So should I restart the labby and pull out the ethernet cord as well?

That would be correct..
when you return run a few commands for me please.. I want to hear good things... LOL

What is a labby?

---

### Post by wildmanne39 on 2011-08-02
Hi, yes take out the wired connection then restart your computer.

---

### Post by Akusa on 2011-08-02
Well let me just tell you that I'm not using an ethernet cable :guitar:, but I really want to say thank you to everyone who offered their input and time into solving this problem.  I'm just a little surprised about the "GPG Ubuntu Jaunty Archive Error" in a new install of the LTS.  It seemed simple enough to fix though...

On a bit of a sidenote, are there good antiviral programs or do security updates take care of that?

---

### Post by wildmanne39 on 2011-08-02
Hi, I am glad you got it working.

the only time you really need antivirus it when you are running a mail server.

---

### Post by nm_geo on 2011-08-02
> **Akusa said:**
> Well let me just tell you that I'm not using an ethernet cable :guitar:, but I really want to say thank you to everyone who offered their input and time into solving this problem.  I'm just a little surprised about the "GPG Ubuntu Jaunty Archive Error" in a new install of the LTS.  It seemed simple enough to fix though...

On a bit of a sidenote, are there good antiviral programs or do security updates take care of that?

You will be glad to know you do not need antiviral programs.. Not at all..

please run

```
sudo lshw -C network 
```

Just be smart and you are safe stay updated..

---

### Post by EkuquoL on 2011-08-02
I am unsure why... But Ubuntu doesn't like to use RPM archivers.

RPM is a really neat multi-tool  that can autoinstall for you and resolve dependencies as well.

If you are going to attempt using OpenSuse packages -- They might / might not work. 
Just first before watching error after error... 

Get a RPM archiver... Then try to use the packages. You might even find a rpm archive that is for linux and that will even work for your little laptop.

---

### Post by mortchase on 2011-12-16
Hi I'm mort with dell insp 1545 laptop with a controller as follows: 0c:00.0 network controller[0280] Broadcom corp BCM4312 802.11 b/g LP-PHY [14e4:4315] on ubuntu 10.04.3 LTS. Simply cannot make an internet connection Help!!! Thanks for any info

---

### Post by TBABill on 2011-12-16
Hi Mort, if you have ethernet access, just plug in to ethernet, do a ```
sudo apt-get update
``` Then go to hardware drivers or something similar to that (can't recall exactly) and when the driver applet comes up, select the STA driver, click activate and then restart once completed. Should be up and running on restart.

If you cannot get online, you'll need your Ubuntu CD. Go to software sources and add the CD as a source...there's an option to do so in there. Once that's done, do a ```
sudo apt-get update
```Then go through the step above to activate the STA driver.

If neither works and you're ok with reinstalling Ubuntu, here's a trick that works nicely with your card. Fire up the LiveCD (boot from it). Once you get to the desktop, go to that hardware drivers app and enable the STA driver, but DO NOT RESTART when it tells you to!!!! That's critical here. 

Next, just close that app once it says you need to restart the machine to complete the install. Open a terminal and type in ```
sudo modprobe wl
```Wait a few moments, then connect to your network. 

NEXT, select install Ubuntu. Do not restart or shut down before doing this or you'll have to do it all over again. Once Ubuntu finishes installing you should have a working wireless connection when you restart to complete the Ubuntu install.

---

### Post by mortchase on 2011-12-21
This is mort: thanks for a reply re;ubuntu/wireless. will try your  suggestions.

---

### Post by mortchase on 2011-12-21
[QUOTE=TBABill;11543233] hi TBABill: will try your suggestions, thanks so much for your reply   mort

---

### Post by mortchase on 2011-12-21
hi TBABill: Thanks for the quick reply concerning ubuntu/inspiron 1545/wirelee connection. i may reinstall ubuntu and follow your suggestions Thanks again;  mort

---

### Post by mortchase on 2011-12-21
hi TBABill; this is mort; read your suggestions. have nothing important on this machine so will reinstall ubuntu and follow your re's   Thanks again; mort

---

### Post by witeshark17 on 2011-12-21
Best of luck, please keep us posted...

---

### Post by mortchase on 2011-12-31
hi TBABILL;11543233 Your recommendations solved my connect-to-internet just as you predicted.I'm grateful and appreciative. How in the world did you acquire the "tricks" that solved my problem. Thanks again!! I'm mort.

---

