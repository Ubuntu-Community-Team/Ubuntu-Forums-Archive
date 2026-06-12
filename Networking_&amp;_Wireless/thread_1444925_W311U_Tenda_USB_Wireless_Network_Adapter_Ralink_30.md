---
title: "W311U Tenda USB Wireless Network Adapter_Ralink 3070_148f:307Ubuntu8.04 LTS_2.6.24-27"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by :Chemist on 2010-04-01
Note to Moderator: I posted a similar thread ([http://ubuntuforums.org/showthread.php?t=1440653&highlight=%3BChemist](http://ubuntuforums.org/showthread.php?t=1440653&highlight=%3BChemist)) that may need to be deleted.  I actually followed the posting guidelines and posted here as new thread.

Quick overview:

Tenda W311U Wireless Network Adapter not working with Ubuntu 8.04 LTS.  I'm pretty new to Ubuntu, so if it's an easy fix let me know.  If it's not, I only spent $15, so I can buy a new one with better support if necessary.  I tried to use ndiswrapper, but W311U isn't listed on their support list...No luck.  Here's the basic info, so if anyone has any suggestions.....let me know.

Desktop, 2.8 Pentium 4 desktop, 2gb DDR400, 7300GT AGP

lsusb
Bus 005 Device 003: ID 148f:3070 Ralink Technology, Corp.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:5b:53:d1:0b  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:fe53:d10b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28303138 (26.9 MB)  TX bytes:4542684 (4.3 MB)
          Interrupt:18 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69200 (67.5 KB)  TX bytes:69200 (67.5 KB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lsmod
Module                  Size  Used by
af_packet              23812  2 
ipv6                  268036  8 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
container               5632  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
dock                   11280  0 
sbshc                   7680  1 sbs
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
it87                   20876  0 
hwmon_vid               4352  1 it87
lp                     12324  0 
usbhid                 32128  0 
evdev                  13056  5 
snd_ca0106             36192  2 
hid                    38784  1 usbhid
snd_ac97_codec        101028  1 snd_ca0106
ndiswrapper           192920  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
nvidia               7106084  34 
snd_pcm                78724  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
serio_raw               7940  0 
snd_rawmidi            25760  2 snd_ca0106,snd_seq_midi
psmouse                40336  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
snd                    56996  15 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
ac97_bus                3072  1 snd_ac97_codec
i2c_viapro              9876  0 
via_agp                11136  1 
snd_page_alloc         11400  2 snd_ca0106,snd_pcm
agpgart                34760  2 nvidia,via_agp
i2c_core               24832  2 nvidia,i2c_viapro
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
pcspkr                  4224  0 
ext3                  136968  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  4 
ata_generic             8324  0 
floppy                 59588  0 
via_rhine              26632  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
sata_via               12420  0 
pata_via               13316  3 
pata_acpi               8320  0 
mii                     6400  1 via_rhine
usbcore               146412  5 usbhid,ndiswrapper,ehci_hcd,uhci_hcd
libata                159728  4 ata_generic,sata_via,pata_via,pata_acpi
scsi_mod              151692  4 sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36616  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3584  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  5 

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:11:5b:53:d1:0b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.11 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lsb_release -d
Description:    Ubuntu 8.04.4 LTS

uname -mr
2.6.24-27-generic i686

---

### Post by ctbarker32 on 2010-04-02
W311U not working in 10.04 Beta 1 as well for what it's worth.

-CB

---

### Post by :Chemist on 2010-04-03
Thanks for the input.  I was debating on waiting for the 10.04 release to find out, but there are other $15-20 adapters available....just need to find a compatible one.  Can be PCI or USB.  I can go off of the lists, but they don't look very updated (in the fast-paced technology sense).  Suggestions appreciated  :)

---

### Post by chili555 on 2010-04-03
> Bus 005 Device 003: ID [COLOR="Red"]148f:3070[/COLOR] Ralink Technology, Corp.This device is claimed by *both* rt2870sta and rt2800usb; since they conflict, they won't drive the device. Unfortunately, it appears that you have installed *another* driver, ndiswrapper, which also doesn't work. Before you buy a new device, are you ready to try to properly drive the device you have? If so, please post:```
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/blacklist.conf
cat /etc/modules
```I'll grab a tranquilizer and an adult beverage.

---

### Post by eeBus on 2010-04-05
I have the Tenda W311U working under Ubuntu 10.04 Beta 1 on my netbook (Lenovo s10-2).

All I did was add rt2870sta to the end of the /etc/modules file.

It works but only shows a connection speed of 54Mbs, so I don't know if it is wireless N. (The router certainly is wireless N!) 

Hope this helps

---

### Post by :Chemist on 2010-04-12
thanks Chili, I'd love to try.  Here's the info:

$ cat /etc/modprobe.d/blacklist

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
------------------------------------------------------------------------------
$ cat /etc/modprobe.d/blacklist.conf

cat: /etc/modprobe.d/blacklist.conf: No such file or directory
------------------------------------------------------------------------------
$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

# Generated by sensors-detect on Sun Mar 14 13:24:44 2010
# Chip drivers
it87
-------------------------------------------------------------------------------
:Chemist

---

### Post by chili555 on 2010-04-12
I just noticed this:> uname -mr
**2.6.24-27**-generic i686 That kernel, in fact has no modules that support your device. Compare to 9.10 and 10.04 that have two and one needs to be blacklisted. Therefor, it appears we have three choices; first, update to a later version of Ubuntu. Second, we could look for an old .tar.gz version of the rt2870sta driver that we can compile and build from source, or, last, you can shop for a different device.

Version 10.04 is right around the corner.

What is your choice?

---

### Post by :Chemist on 2010-04-13
I'm not at all opposed to updating to 10.04.  I was actually planning on it once the full version is released (April 29th?).  I'm probably too new to Ubuntu to do anything too complicated (I don't have much of a programming background....I always used Windows.  I do understand hardware pretty well and have built 3-4 desktops with Windows, though).  

It looks like I will be able to upgrade to 10.04 without having to reinstall from scratch.  So when I upgrade, should this work out of the box or will I have to install or blacklist a driver?  BTW, thanks for replying and helping - I really appreciate it.

:Chemist

---

### Post by chili555 on 2010-04-13
You will probably have to blacklist rt2800usb, rt2x00lib and rt2x00usb. A reboot should put you in business.

Good luck and post back if you get stuck.

---

### Post by :Chemist on 2010-04-14
So knowing that I wanted to upgrade to 10.04 to get W311U to work, I got adventurous and upgraded 8.04-->8.10-->9.04-->9.10.  CHILI, if you're still out there, what do I need to repost about my system?  I'm still struggling with the outputs I get from lsusb, ifconfig, iwconfig, lsmod, sudo lshw -C network, etc., so bear with me.  It's all foreign to me.  I reeaaally don't understand linux drivers :(  Lemme know

:Chemist

---

### Post by chili555 on 2010-04-15
Just remove your little Tenda and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Now do:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Reboot and reinsert your device. It should be working.

---

### Post by :Chemist on 2010-04-15
Chili555, you are AWESOME!  It works. Using it now.  Ran speedtest @ [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/) and got 18MBPS down & 2.1MBPS up.  That matches my result with wired connection.  Thanks for all of your help.   I spent way too long on this.

---

### Post by TheStreetSpirit on 2010-05-01
followed chili's steps, but how exactly can I tell if it is working? internet seems a bit faster but theres no icon or indicator.

---

### Post by congminh1709 on 2010-05-15
Hello every one, searching ubuntuforums and I found this topic.

I want everyone to confirm if W311U Tenda USB Wireless Network Adapter can be compatible with Ubuntu 10.04 LTS and aircrack-ng 1.1 with full speed (150 Mbps)?

Thanks.

---

### Post by chengxt_0 on 2010-05-18
thanks very much&#12290; because you i use ubuntu again.

---

### Post by barrydrink on 2010-05-28
I'm also trying to get the W311U to work. I have followed the instructions below, and after reboot I get connected to my WLAN. However, browsing is painfully slow - it takes about a minute to open a page like [www.bbc.co.uk]("http://bbc.co.uk"). I am on a 8Mb broadband connection, so this clearly wrong.

When looking at the W311U when plugged in, the green light goes out every few seconds, for a few seconds at a time which I don't think is correct. It's as though it is not working during these periods.

Please help... I am using 10.04 64 bit.

Best reagrds,
Barry

> **chili555 said:**
> Just remove your little Tenda and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Now do:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Reboot and reinsert your device. It should be working.

---

### Post by chili555 on 2010-05-28
How about letting me see:```
lsmod | grep rt2
dmesg | grep -i RT2
iwconfig
```Thanks.

---

### Post by barrydrink on 2010-05-28
```
lsmod | grep rt2
rt2870sta             525366  1 
``````

dmesg | grep -i RT2
[    8.767805] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    8.857884] usbcore: registered new interface driver rt2870
[    9.362768] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"dynamode home"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.442 GHz  Access Point: 00:08:5C:98:17:25   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-59 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```Thanks for your assistance,
Barry

---

### Post by argongold10 on 2010-06-13
Hi Barry, 

I am also using Ubuntu 10.04 on 64-bit processor and currently trying to fix Tenda W311U usb wireless connection but no success so far. Previously it was working fine with Ubuntu 9.10 after blacklisting rt2870sta .

How about you?  If you got it fixed  then let us know the exact steps.

Regards,
Argon

---

### Post by barrydrink on 2010-06-19
> **argongold10 said:**
> Hi Barry, 

I am also using Ubuntu 10.04 on 64-bit processor and currently trying to fix Tenda W311U usb wireless connection but no success so far. Previously it was working fine with Ubuntu 9.10 after blacklisting rt2870sta .

How about you?  If you got it fixed  then let us know the exact steps.

Regards,
Argon

I did the blacklisting, but found that browsing was still extremely slow, with 'resolving host' displayed by the browser whenever I clicked a link. I found a cure [here]("http://code.google.com/p/chromium/issues/detail?id=12754#c37"). This is aimed at the Chrome browser, but I think the fix applies to any.

Barry

---

### Post by Philip Farrugia on 2010-06-25
Finally got my ralink 3070 usb working by simply adding the rt2870sta to the modules file as above.
 Thanks Everyone!

However it only works with WEP and not WPA2 which all my other devices are using.
Anyone got any ideas how I can use wpa2?

---

### Post by Oiorpata on 2010-07-02
I'd love to hear from anyone who has managed to get Tenda W311U to connect to a WPA2 protected network too. I'm having the exact same problem as Philip Farrugia and several other 64 bit Ubuntu 10.04 users. After blacklisting the conflicting drivers the adapter now finds the network but keeps asking for the WPA2 password and timing out.

---

### Post by timlev on 2010-07-12
I am running into the same problems. Would those who got it working let us know what kind of wireless security they are using? (i.e. WEP, WPA, WPA2, etc.) Thanks!

---

### Post by bornbyforce on 2010-08-10
> **chili555 said:**
> Just remove your little Tenda and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Now do:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Reboot and reinsert your device. It should be working.

OK I have just bought the Tenda w311U and these instructions worked for me on 32bit Lucid.
A little added detail that might save others some time...
When I installed it on windows the driver files where actually rt2780 (without the sta, usb bits)
ignore that please! if you get in trouble about the third set of commands just sudo gedit the /etc/modules file and on a new line add the magic word rt2780sta all what is left to do is save and restart. oh and may be post here and thank chili555 for the help!

Also in my case I am using a laptop with a broken wireless button which means my computer was looking at the internal wifi and was considering it off so having tenda working was a bit confusing. There might be other solutions but I prefer surgical procedure. (opened the laptop and took the wireless card off). And with Chili555's instructions I am back online again... without wires.

---

### Post by Oiorpata on 2010-11-08
I never did manage to get the Tenda W3111U working with anything better than WEP on 64bit ubuntu 10.04, it would time out trying to connect using WPA. 
The good news is that after upgrading to version 10.10 the problem has vanished.

---

### Post by Flickster on 2010-12-25
Hey everyone, 

I did everything Chili and bornbyforce said to do, but still not luck with my tenda. I'm running a 64bit 10.10 btw. Is anyone out there who can help me figure this out? It doesn't even recognize the USB adapter when I do iwconfig. 

Help?

---

### Post by Randymanme on 2011-08-22
Thank you very much, Chili555.  I just happened to find your directions while Googling my similar problem.

---

### Post by handyosprey on 2012-02-22
> **chili555 said:**
> Just remove your little Tenda and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Now do:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Reboot and reinsert your device. It should be working.Thanks chili555

Worked perfectly for me .

---

### Post by handyosprey on 2012-02-22
Forgot to add , my usb stick is a dynamode wl-700n-m .But it showed as a ralink 3070 on ubuntu 10.4

---

### Post by S2UIRR3L on 2012-07-05
Did everything listed above and for some reason, it's not connecting. It shows my wireless router in the list, I click on it, enter my password. It "tries" to connect, but keeps coming back to ask me for my password again... Here's what I have:

COMPUTER: Dell Inspiron 1000 (laptop)
LINUX OS: Ubuntu Lucid Lynx 10.04
ROUTER: Netgear Wireless N (with WPA/WPA2)
USB: Tenda W311U 802.11 B/G/N (with WPA/WPA2)

When instructed to add the tree blacklist lines... I just added them to the very bottom of the page... Was I supposed to add them to a different location? I'm kinda new to doing everything on Ubuntu as well lol. Thanks a million for everything!!!

-Leo in Massachusetts (us)

---

### Post by chili555 on 2012-07-05
Please change your router to WPA2 only and then run and post:```
rfkill list all
lsmod | grep rt2
```> I just added them to the very bottom of the pagePerfect!

---

### Post by S2UIRR3L on 2012-07-05
> **chili555 said:**
> Please change your router to WPA2 only and then run and post:```
rfkill list all
lsmod | grep rt2
```Perfect!



Do I add that "rfkill" stuff to the bottom of the same page that I added the 3 blacklist things? I apologize for my ignorance, I'm just starting to do things in terminal.

-Leo in Massachusetts (us)

---

### Post by chili555 on 2012-07-05
No. Just run those commands in a terminal and post the result here. The results will help us diagnose why your wireless isn't working. In the second command, the pipe symbol | is on the right side of my US keyboard on the same key with \.

Here is a sample from my computer attached. You could simply copy and paste the entire output from you computer and post it here.

---

### Post by S2UIRR3L on 2012-07-05
I hope this helps...?

---

### Post by chili555 on 2012-07-05
Your device ought to spring to life. You have the right driver in place and the conflicting drivers blacklisted. Do you indeed have the same device? Please run:```
lsusb
```Make note of the usb.id for your device; is it the same as the title of this thread148f:3070? I don't need a screenshot, just confirmation that it is the same or, if not, what it is.

Also please run and post:```
dmesg | grep rt2
```You can copy and paste from the terminal and post it here. It's probably easier than a screenshot.

---

### Post by S2UIRR3L on 2012-07-05
I just bought the thing on eBay (won the bid for .99 cents / free shipping lol)
I've tried it in my neighbor's Windows 7 computer and it worked flawless.



_Here's the output for "lsusb"_
squirrel@inspiron1000-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
squirrel@inspiron1000-laptop:~$ 



_Here's the output for "dmesg | grep rt2"_
squirrel@inspiron1000-laptop:~$ dmesg | grep rt2
[   30.430892] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   30.856767] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   30.941273] usbcore: registered new interface driver rt2870
squirrel@inspiron1000-laptop:~$ 



(I've rebooted and left the blacklisted items alone before copying these outputs)



At one time, it was working on this Inspiron 1000 laptop. Weird part is, Debian Squeeze didn't need to download the drivers, they were already in the OS, but the ethernet cable didn't work (couldn't care less)... That was all on another hard drive that was about to die.

I put a freshly formatted 20-Gig IBM hard drive and tried to install Debian Squeeze again, but it just wouldn't happen... I tried a few other LXDE distros (because I only have 512-Mb of RAM and LXDE was suggested by everyone because they're light weight)... They didn't like the laptop either...

But Lucid Lynx 32-bit, they get along fantastic and I've downloaded all the Ubuntu restricted extras so I can listen to The Tom Leykis Show via PLS file on Rhythmbox and I've even downloaded a really cool looking SlicknesS Black theme and everything is so nice and fluid... The wireless is the only thing that's killing me lol. I'm using the ethernet right now to talk with you.

By the way, Chili... Thank you for everything you're doing for all of us here on the forums... I wish I could hug you!!!

-Leo in Massachusetts (us)

---

### Post by chili555 on 2012-07-06
My favorite kind of problem here: everything looks perfect except it doesn't work!

I assume you have a wireless interface wlan0. Please check:```
iwconfig
```Does it scan?```
sudo iwlist wlan0 scan
```I don't need the entire result here, just tell me if it scans and sees your network. If not, what is the message or error? Do you see networks when you click the Network Manager icon?

---

### Post by S2UIRR3L on 2012-07-06
I can tell you before running those commands...
It scans for all signals, regardless if they're B/G/N or WPA/WPA2. This little thing even picks up my neighbor from the other side of the forest that separates our two back yards (aprox. half an acre away lol) and shows the signal strengths.

My other wireless USB is about to be delivered (won two auctions on eBay by accident lol). At least they didn't cost me much, both cost me 99-cents each and both were free shipping. The second is a Netgear N-150 (i think). I had a Netgear before and all I had to do with that was enable some sort of "B43" something.

I'll keep trying with this Tenda because I'm curious to find out what it is... so I'll learn how to "fix" it in future, if I need to for some one else, the way you're trying to help me (smiles).

Thanks again, Chili!

---

### Post by S2UIRR3L on 2012-07-06
This is the output from those two commands:
(My network's name is RabidSquirrelNetwork)

iwconfig
```
squirrel@inspiron1000-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-89 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```



sudo iwlist wlan0 scan
```
squirrel@inspiron1000-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for squirrel: 
wlan0     Scan completed :
          Cell 01 - Address: 00:24:B2:E0:E7:67
                    Protocol:802.11g/n
                    ESSID:"RabidSquirrelNetwork"
                    Mode:Managed
                    Channel:2
                    Quality:100/100  Signal level:-47 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: C4:3D:C7:AB:0B:98
                    Protocol:802.11g/n
                    ESSID:"robertwillisredsox31"
                    Mode:Managed
                    Channel:3
                    Quality:18/100  Signal level:-83 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1F:90:F1:3B:95
                    Protocol:802.11b/g
                    ESSID:"Bat Signal"
                    Mode:Managed
                    Channel:11
                    Quality:13/100  Signal level:-85 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
```

---

### Post by chili555 on 2012-07-06
> wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Ole Chili doesn't like the look of that one bit. Is this the built-in rt2870sta that comes in Ubuntu 10.04 or did you download and compile something?

---

### Post by S2UIRR3L on 2012-07-06
The only thing that I downloaded was the Ubuntu Restricted Extras from the Software Center, so I can listen to the stream from [http://www.BlowMeUpTom.com](http://www.BlowMeUpTom.com) using Rhythmbox.

I may have also did the thing to watch a movie, I can't remember if I've already done it or not, but this is the thread that I always use for a fresh install, if I need to do it to watch a dvd. The thread is located [HERE]("http://ubuntuforums.org/showthread.php?t=1410675").

Other than that, I didn't do much of anything to this fresh install. Just only what was mentioned on this thread with the black listing the three lines, followed by the other commands that ended with "EXIT"

---

### Post by chili555 on 2012-07-06
> followed by the other commands that ended with "EXIT"Let's take a look at that. Please post:```
cat /etc/rc.local
modinfo rt2870sta | grep filename
```

---

### Post by S2UIRR3L on 2012-07-06
```
squirrel@inspiron1000-laptop:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
squirrel@inspiron1000-laptop:~$ modinfo rt2870sta | grep filename
filename:       /lib/modules/2.6.32-41-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
squirrel@inspiron1000-laptop:~$ 
```
The other stuff I did to listen to Tom Leykis and watch a movie didn't affect anything, did it? I can't see how it would, it's for something totally different.

By the way, I'll check again when I get home at around 10 PM Eastern (boston / usa time).

---

### Post by chili555 on 2012-07-07
> The other stuff I did to listen to Tom Leykis and watch a movie didn't affect anything, did it?I highly doubt it. Let's do a full diagnostic work-up. We are going to create a big text file and zip it and, so we don't flood the forum, attach the zip as an attachment to your reply. 

Detach any ethernet cables. Please reboot so we have a clean slate. Open a terminal and do:```
dmesg > squ.txt
lsmod >> squ.txt
iwconfig >> squ.txt
sudo cat /var/log/syslog | grep etwork | tail -n25 >> squ.txt
ls /etc/Wireless >> squ.txt
cat /etc/Wireless/RT2870STA/RT2870STA.dat >> squ.txt
zip squ.zip squ.txt
```Find the zip file squ.zip in your user directory and attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by S2UIRR3L on 2012-07-07
I appreciate all the help you've been giving me... but if it looks as if nothing will work and this combo is just incompatible, I don't want to bother you... I wish there was a way that I can compensate you for everything, Chili... Thanks a million!!!

I hope this is the file that you've asked for. I copied the commands to a blank text and saved it. I unplugged the CAT-5 cable, rebooted and entered the commands that you gave me. I left the wireless USB thing in tho, I never took that out.

Here's the output (in .zip attachment)

---

### Post by chili555 on 2012-07-07
First of all, thank you for your kind comments. Let's see if we can fix this little problem:> [   26.357079] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.datPlease do:```
sudo su
mkdir /etc/Wireless
mkdir /etc/Wireless/RT3070STA
```If, in either case, it says the directory already exists, please continue:```
echo Default > /etc/Wireless/RT3070STA/RT3070STA.dat
```Now we unload and reload the driver:```
modprobe -r rt2870sta
modprobe rt2870sta
exit
```Is there any improvement?

---

### Post by S2UIRR3L on 2012-07-08
Okay... I've entered the codes, copied and saved them, unplugged the CAT-5, rebooted and tried to connect with the Tenda W311U... Same story, it sees my network, I enter my password, it tries to connect but fails and asks me for the password to no end.

Here's what the codes returned:

```
squirrel@inspiron1000-laptop:~$ sudo su
[sudo] password for squirrel: 
root@inspiron1000-laptop:/home/squirrel# mkdir /etc/Wireless
root@inspiron1000-laptop:/home/squirrel# mkdir /etc/Wireless/RT3070STA
root@inspiron1000-laptop:/home/squirrel# echo Default > /etc/Wireless/RT3070STA/RT3070STA.dat
root@inspiron1000-laptop:/home/squirrel# modprobe -r rt2870sta
FATAL: Module rt2870sta is in use.
root@inspiron1000-laptop:/home/squirrel# modprobe rt2870sta
root@inspiron1000-laptop:/home/squirrel# exit
exit
squirrel@inspiron1000-laptop:~$ 
```

---

### Post by chili555 on 2012-07-08
> root@inspiron1000-laptop:/home/squirrel# modprobe -r rt2870sta
FATAL: Module rt2870sta is in use.Not sure I like that...

Is there any change if you reboot?

Please make me a new squ.zip as in post #44 after a reboot. Thanks.

---

### Post by S2UIRR3L on 2012-07-08
Here ya go... Reboot with both the Tenda and the CAT-5 plugged in. The Tenda tried to connect first, asked for my password and I canceled. That's when the CAT-5 took over. I made the squ.zip and here it is:

---

### Post by chili555 on 2012-07-08
I am ready to ditch the driver. There are a few ways we could proceed. I am fairly confident that an upgrade to Ubuntu 12.04 would solve your issue. You could test the theory by downloading and running the live CD. If it works, install.

We could look for a native driver to compile and install it. It might be a bit of a challenge for kernel version 2.6.32. I may have a few things lying around on my computer. We might find some help here: [https://launchpad.net/~logari81/+archive/ppa/+sourcepub/1136891/+listing-archive-extra](https://launchpad.net/~logari81/+archive/ppa/+sourcepub/1136891/+listing-archive-extra) 

We could locate the Windows XP driver and try ndiswrapper. In any case, I'll be very happy to assist you. What is your preference?

---

### Post by S2UIRR3L on 2012-07-08
You're going to reach through the computer screen and choke me for this one...

My mom just handed me something... Said she didn't know if it was important or not... She handed me the CD rom that came with the wireless stick... I popped it in and there's a .tar.bz2 thing labled LINUX DRIVER!!!!!!!!!!

I've attached the file here, please tell me how to install it... I don't know how to do anything with a .tar.bz2 and I'm thinking I'll have to do it with terminal? This will be our last attempt and I wouldn't blame you for strangling me :(

This may be useful for anyone else in the same situation... I hope it helps everyone, the same way you've been helping me... Chili555, you're a saint!!!

[B][SIZE=4]Here are the drivers (if I've uploaded them correctly):
 
 
[/SIZE][/B]

---

### Post by chili555 on 2012-07-08
I'd never choke a good newbie who's willing to learn. No worries. I think that's the less good way to proceed. I suggest you open a terminal and do:```
wget https://launchpad.net/~logari81/+archive/ppa/+files/rt3070_2.3.0.2-0ubuntu1%7Eppa1%7Elucid2_all.deb
sudo su
dpkg -i rt3070*.deb
echo "blacklist rt2870sta" >> /etc/modprobe.d/blacklist.conf
ifconfig wlan0 down
modprobe -r rt2870sta
modprobe rt3070sta
exit
```You will need a working ethernet connection to download the package and any dependencies. Post any errors and, especially, if you get stuck.

---

### Post by S2UIRR3L on 2012-07-08
Chili... I think it was my hard drive that was corrupted and THAT'S why it wasn't working... Before I got the chance to try what you suggested (in post #52, above this one), the hard drive started buzzing and it died...

I doubt it had anything to do with with any commands that I've entered because I knew the hard drive was "whiney" to begin with... But it started actually "buzzing" when I turned on the computer tonight and it started slowing down until it stopped spinning.

I think the bearings in the drive finally dried up and ceased.

Does this sound like a possible cause, as to why we couldn't get the Tenda W311U to work, with all the drivers and commands and tweaking that didn't seem to work?

Again, I really doubt that my hard drive died because of all we did... The hard drive is about 10 years old and I thought I could get another 2 or 3 years out of it.

But if you suspect that it's something I did, maybe we should ask the mods to delete a few posts, as well as that .tar.bz2 that I've uploaded as a precaution.

What do you think?

-Leo in Massachusetts (us)

---

### Post by chili555 on 2012-07-09
I highly doubt any commands you issued had any significant effect on your harddrive. Had we compiled a kernel or done a similar process that uses the drive more or less continuously, then I might agree. All we did is request diagnostics. Even so, any harddrive ought to be capable of occasional kernel compiles!

Compiling your own custom fine-tuned kernel: now there's an interesting task for another day!

I also wouldn't delete any posts, which you can do be editing the post and replacing all the text with 'Deleted.' I think the eventual outcome ought to stand for itself. The searchers ought to have the good sense to read to the end and look for those magic words, 'It's working!' before they unleash a proposed but unproven fix.  

I suggest you replace the harddrive and proceed. If you have the live CD from which you installed, you may be able to boot into it and rescue any crucial items from your user directory by copying them to a USB key. It sometimes works.

---

### Post by S2UIRR3L on 2012-07-09
I'm with you on this one... I don't feel that anything we did would cause the hard drive to crash. It was just a really old hard drive. I didn't have much to save, since it was a fresh install. Even if I had anything on it, I wouldn't be able to save anything, since it doesn't spin anymore. I'll drill a hole through it before I recycle it.

I know I have another hard drive some where, and once I format it, I'll probably try installing Ubuntu first, and if that doesn't work, others have told me that Xubuntu is a light weight that would work better with the half gig of ram that I have in the laptop. I guess it's a great opportunity to start learning XFCE?

Once again, Chili... You are one of the most valuable people that I've ever had the privilege of speaking with on these forums. You're kind, you're understanding, you're strait to the point and you go out of your way to help a total stranger like my self... THANK YOU

-Leo in Massachusetts (us)

---

### Post by chili555 on 2012-07-09
Thank you so much for your very kind comments. I look forward to your further report. I suspect it will be that it works perfectly and you are a happy penguin!

---

### Post by S2UIRR3L on 2012-07-09
Happy penguin... err squirrel?

Just installed Xubuntu 12.04 on a freshly formatted Fujitsu 60-Gig on this little Dell Inspiron-1000 laptop and I didn't have to search for anything what so ever. I installed with a hard wired CAT-5 (to be sure everything worked) and then tried the Tenda W311U. I'm actually using the laptop, with the wireless, to post this.

To my surprise, Xubuntu 12.04 is actually a little slower than Ubuntu 10.04, but it's very stable and EVERYTHING works out of box! I'm a happy penguin! I now have no doubt that it was the other IBM 20-Gig hard drive that was corrupted, not to mention that it stopped spinning all together (old age) lol. Thanks a million for everything, Chili!!!

-Leo in Massachusetts

---

### Post by chili555 on 2012-07-09
Happy to have helped and I'm glad it's working. Have fun!

---

