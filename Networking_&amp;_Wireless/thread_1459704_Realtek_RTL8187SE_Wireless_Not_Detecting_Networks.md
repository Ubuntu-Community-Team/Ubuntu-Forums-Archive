---
title: "Realtek RTL8187SE Wireless Not Detecting Networks"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by BrianIsNew on 2010-04-21
Hey guys and gals,

I would hope that the title gives my problem away, but my wireless card is not detecting networks. 

I'm a total new guy to the Linux world, so please be patient with me. 8-[

Please bear with me as I proceed to spit out anything I think you may need to assist me.
[B]
_____________________________________________________________________[/B]

I currently have Ubuntu 9.10 installed on a stock Toshiba Satellite L505D-S5965.

zeus@olympia:~$** lsb_release -d**
Description:    Ubuntu 9.10
zeus@olympia:~$** uname -mr**
2.6.31-20-generic i686

zeus@olympia:~$[B] lspci -nn | grep -i wireless
[/B]02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)

zeus@olympia:~$** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.422 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry: on   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

zeus@olympia:~$** lsmod**
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  4 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd                    59204  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0 
serio_raw               5280  0 
rtl8187se             200472  0 
i2c_piix4               9932  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
video                  19380  0 
output                  2780  1 video
radeon                636000  1 
ttm                    36212  1 radeon
drm                   160032  3 radeon,ttm
agpgart                34988  2 ttm,drm
i2c_algo_bit            5760  1 radeon
r8169                  32064  0 
mii                     5212  1 r8169

zeus@olympia:~$** sudo lshw -C network**
  *-network               
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 00:24:d2:b6:76:2b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8180 latency=0 multicast=yes wireless=802.11b/g
       resources: irq:16 ioport:5000(size=256) memory:d5100000-d5103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:d6:f4:0a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.111 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:3000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d103ffff(prefetchable)

zeus@olympia:~$** iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
**_____________________________________________________________________**

The kernel boot message output (dmesg) is a little lengthy, but I have no problem posting it if it'll help.

Please let me know if this has been answered anywhere else in the forum, and I apologize if it is. Perhaps I overlooked a solid solution. :neutral:

Thanks in advance for any help!

---

### Post by chalex on 2010-04-21
This thread: [http://ubuntuforums.org/showthread.php?t=1416682](http://ubuntuforums.org/showthread.php?t=1416682)

The person says it started working after upgrading to the latest packages (Ubuntu 9.10)

Are you able to get on the network with a cable?

---

### Post by BrianIsNew on 2010-04-21
Thanks for the speedy reply, chalex.

My computer is currently up to date has no more available packages to upgrade to.

zeus@olympia:~$ **sudo apt-get update**
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done
zeus@olympia:~$ **sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And I am currently using a physical cable to attach to the switch for my network.

---

### Post by BrianIsNew on 2010-04-22
Still no clues to this one?

---

### Post by KaosKnight on 2010-04-23
What network program are you using? I recently went from 8.10 to 9.04 and couldn't get online using Wicd Manager. In the preferences, I had to switch my wireless interface from ath0 to wlan0 (or whatever logical name your card has). Once I did that and hit refresh, it found my network; before it wouldn't find anything.

---

### Post by BrianIsNew on 2010-04-26
I'm pretty positive that I don't have any network program other than the standard manager Ubuntu uses managing my connections. System>Preferences>Network Connections

---

### Post by BrianIsNew on 2010-04-28
Is everyone still blank? :-k

---

### Post by BrianIsNew on 2010-04-29
Bump?

---

### Post by BrianIsNew on 2010-04-30
I'd be happy with a point in a general direction? Anyone?[-o<

---

### Post by Chrisco66 on 2010-05-04
Im having the same problem.  mine will see wireless networks, even my own.  it will not connect to any of them however.  Same realtek RTL8187SE card shows up when I run lspci in terminal.  The same thing happened when i upgraded last time.  I wish i remember how I fixed it then.  I know it didnt take too long.  I just cant find the thread now.  I might have to go back to opensuse if I cant fix it pretty quick..

---

### Post by BrianIsNew on 2010-05-04
I browsed my way to [Realtek's site]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=40&PFid=40&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8187SE"), and it turns out that they don't list a driver for RTL8187se compatible with Linux. :sad:

If you find something, please let me know.

---

### Post by Fatman_UK on 2010-05-07
> **BrianIsNew said:**
> I browsed my way to [Realtek's site]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=40&PFid=40&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8187SE"), and it turns out that they don't list a driver for RTL8187se compatible with Linux. :sad:

If you find something, please let me know.

You already have the driver you need. Don't worry about the Realtek website. The driver is built into the Linux kernel. Check your lsmod output for the line with "rtl8187se" - that shows your hardware is recognised and the driver is being loaded.

I'm guessing a recent release of the driver has broken it somehow. I just upgraded my Advent G10 (netbook) from Karmic to Lucid and suddenly my wifi has conked out. It's been perfectly stable for at least 6 months. I'm going to have to investigate. I'll post again when I have news.

---

### Post by Chrisco66 on 2010-05-09
Anything?  There was talk about using a different kernel.  

I am almost ready to start buying mini wireless cards till I find one with Ubuntu support.  I looked at pricewatch.com, there are many cheap mini pci cards out there.  The question is how do I know which will be supported?  I really don't need to buy another non functioning card.  

The other choice was to go back to Opensuse for this machine.  I tried that too, no help.

I ran into this problem when I upgraded to 9.04, but I don't think I had problems when I upgraded to 9.10.  Now, Its happening again, and I don't know how to fix it.  Very annoying..

P.S.  I tried to install the windows driver using the GUI version of NDIS.  It seemed to install correctly, but it still wont connect.

---

### Post by pdc on 2010-05-10
from opensuse, lwfinger suggests the command

> lsmod | grep 87se

post #14

[http://forums.opensuse.org/get-help-here/pre-release-beta/425161-realtek-8187-wireless-pci-support-2.html](http://forums.opensuse.org/get-help-here/pre-release-beta/425161-realtek-8187-wireless-pci-support-2.html)

> Forget about ndiswrapper and compiling your own driver as the 11.2
kernel (2.6.32 ) includes a version of the vendor driver that works.

Is the driver loaded? Does 'lsmod | grep 87se' return anything? If so,
the driver is loaded.

and the command

> sudo /usr/sbin/iwlist scan

---

### Post by Chrisco66 on 2010-05-10
Ok, here it is.  Can you check that second command?  It didnt like it..

us@us:~$ lsmod | grep 87se
rtl8187se             159435  0 
us@us:~$ sudo /usr/sbin/iwlist scan
[sudo] password for us: 
sudo: /usr/sbin/iwlist: command not found
us@us:~$ 


Thanks in advance..

---

### Post by Chrisco66 on 2010-05-20
Anyone?

---

### Post by Chrisco66 on 2010-05-26
pdc has disappeared.  Im shopping for a new card.  Realtek is at the top of my @#$% list..

---

### Post by Leijonberg on 2010-05-27
I have a similar problem, running Ubuntu 10.04.

uname -mr:
2.6.32-22-generic x86_64

lspci -nn -s 8:
08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)

lsmod |grep rtl:
rtl8187se             178567  0 


I currently have the wireless card deactivated in BIOS, but should I enable it, I get a kernel panic when it tries to load the driver, something like "not syncing".
Anybody know anything about a driver bug being looked at?

---

### Post by Chrisco66 on 2010-05-27
I dont know if the developers are looking into it.  I know that I have 2 different computers, with 2 different cards, and neither one is working correctly after upgrade.  Im so disappointed in 10.04.

I was going back to Opensuse.  The strange thing is that it will no longer support the realtek card either.  I guess the new kernel didnt come with wireless support?  Or maybe it only supports brand new hardware?  In other words, this is not just an Ubuntu thing, the kernel is going to cause problems regardless of the distro.  

Who is driving this boat?

---

### Post by Chrisco66 on 2010-06-03
I give up.  Im going back to 9.10 for the laptops/netbooks.  I will find a replacement for Ubuntu that I dont have to "fix" after upgrade.

I have had wireless problems on two computers, and video problems on another.  

Its almost like the developers are trying prevent using Ubuntu on portables.  

I am seeking a replacement for Ubuntu, at least for the portables. Any suggestions would be appreciated..

---

### Post by Leijonberg on 2010-06-30
bump

---

### Post by thayerw on 2010-07-05
Arch Linux provides flawless support for the r8187se module in all the of past kernels I've used since purchasing my MSI Wind U120.  I'm really surprised this hasn't been addressed sooner here.  For giggles, I tested the 2.6.33 and 2.6.34 Ubuntu kernels as well and neither of them work either.

---

### Post by cetacean on 2010-07-05
I am not good enough to tell you the step-by-step, but I went through an enormous amount of heartache and then solved this quickly by downloading a Windows XP driver for the card and running ndiswrapper.

Apparently there is a whole range of wireless cards that simply have no 10.04 solutions but work perfectly under ndiswrapper using the older Windows drivers.

I spent dozens of hours over a period of weeks and then found out about this and had a perfectly working card (fast!) in minutes. It isn't the card, it's the driver.

Check out the "Starbucks" threads in wireless from a month ago.

---

