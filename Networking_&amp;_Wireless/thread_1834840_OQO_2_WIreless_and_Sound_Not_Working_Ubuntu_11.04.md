---
title: "OQO 2 WIreless and Sound Not Working Ubuntu 11.04"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by DrRebar on 2011-08-28
Wow!
I finally decided to join the forum. As a former Apple devotee I can happily say I have made the switch to Ubuntu for some serious computing needs. 11.04 works well on the 3 year old Asus Eee PC 1000H, and triple boots nicely with Windows and the fruit based OS.
So, for my work in the hospital I have picked up an OQO model 2. It does what the iPad can not....run Windows. Also, unlike the iPad 2, it runs Ubuntu really well!
Windows 7 works well for x-rays and networking. However, Ubuntu 11.04 remarkably does well on the OQO. Installing with CLI command "xforcevesa" took care of the video part. Now onto the wireless and sound. I have tried the ndiswrapper thing and loaded the proper driver. Not working. 
In the forums I found a post about building the driver from a stable compat build ([http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)), but really would like some help. As I use this device for work I really do not want to mess up my installs. With some ingenuity with GRUB2 and Windows bootloader, I can default load Windows. Eventually will be able to switch that to Ubuntu default loading once I get the wireless and sound working.
Sound is another issue. For now really need to try to get wireless working on the OQO model 2. Some specs: 1.5 GHz CPU with 1 GB RAM. Wireless chipset I think is Atheros.
Say what you will about the OQO. Dead company, little to no support. Yes, it is a cool device. It works well in the hospital because it is truly portable. Nothing else like it on the market (forget Sony). Hopefully some company will make the fabled OQO 3. Either way I can solder, know how to use a torx #6 screwdriver, and have already made mods to the OQO the manufacturer could have refined. eBay has plenty of parts. Not cheap, but available.

---

### Post by fdrake on 2011-08-28
> **DrRebar said:**
> Wow!
I finally decided to join the forum. As a former Apple devotee I can happily say I have made the switch to Ubuntu for some serious computing needs. 11.04 works well on the 3 year old Asus Eee PC 1000H, and triple boots nicely with Windows and the fruit based OS.
So, for my work in the hospital I have picked up an OQO model 2. It does what the iPad can not....run Windows. Also, unlike the iPad 2, it runs Ubuntu really well!
Windows 7 works well for x-rays and networking. However, Ubuntu 11.04 remarkably does well on the OQO. Installing with CLI command "xforcevesa" took care of the video part. Now onto the wireless and sound. I have tried the ndiswrapper thing and loaded the proper driver. Not working. 
In the forums I found a post about building the driver from a stable compat build ([http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)), but really would like some help. As I use this device for work I really do not want to mess up my installs. With some ingenuity with GRUB2 and Windows bootloader, I can default load Windows. Eventually will be able to switch that to Ubuntu default loading once I get the wireless and sound working.
Sound is another issue. For now really need to try to get wireless working on the OQO model 2. Some specs: 1.5 GHz CPU with 1 GB RAM. Wireless chipset I think is Atheros.
Say what you will about the OQO. Dead company, little to no support. Yes, it is a cool device. It works well in the hospital because it is truly portable. Nothing else like it on the market (forget Sony). Hopefully some company will make the fabled OQO 3. Either way I can solder, know how to use a torx #6 screwdriver, and have already made mods to the OQO the manufacturer could have refined. eBay has plenty of parts. Not cheap, but available.

Click on my signature (NetWorking) below, and follow the steps. Post here the results please .

---

### Post by DrRebar on 2011-08-29
Despite wanting wifi and sound to work on the Ubuntu install on the OQO model 2, there is nothing I can do. 
When I installed Mac OS X (10.5.2) there was a patch set of files that I installed. One for wifi and another for sound. Works well (most of the time). Just like in the previous web posts on the matter in 2008-9, this does indeed make the OQO an outstanding device to use on the road when you need to have a "mac attack". If anyone is interested in compiling a version that works with Ubuntu 11.04 that would be great! The link to the file I would reference has been taken down. Wow! I think someone up there likes me as I just downloaded it a few weeks ago after it being up for almost two years!
So, for me, I will count my blessings! I still want to get Ubuntu fully working on the OQO. I have tried MadWifi and compat releases. All no go! I have tried backtrace files and even resorted to trying compiling drivers on my own. Wow, what a pain in the butt!
Anyway, if someone with some spare time has an interest in hacking a driver for wifi and sound for an OQO model 2 (1.5 GHz) I would not mind to pay a small fee for your time. I think Ubuntu will eventually be my main OS on this device as it boots fast, plays well with Windows and lets me get onto the hospital network with a wired connection. Once it goes wireless I will use it more at the bedside.
Thanks!

---

### Post by wildmanne39 on 2011-08-29
Hi, please post the results of these commands:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
lsusb
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

### Post by DrRebar on 2011-09-01
Output for (sudo lshw -C network)

 *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:03:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=28 mingnt=10
       resources: memory:c2100000-c210ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:03:05.0
       logical name: eth0
       version: 10
       serial: 00:0c:96:40:48:a9
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:bc00(size=256) memory:c2110000-c21100ff


Output for (lspci -nn | grep 0280)
NOTHING

Output for (lsusb)
Bus 003 Device 004: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 003 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 003 Device 002: ID 1410:2100 Novatel Wireless 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1557:0004 OQO 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Output for (iwconfig)
lo        no wireless extensions.

eth0      no wireless extensions.


Output for (rfkill list all)
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


Output for (lsmod)
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
rfcomm                 38125  8 
binfmt_misc            13213  1 
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
option                 21045  0 
ndiswrapper           192828  0 
btusb                  18160  2 
usb_wwan               19711  1 option
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
usbserial              37116  2 option,usb_wwan
soundcore              12600  0 
psmouse                73312  0 
snd_page_alloc         14036  0 
shpchp                 32345  0 
i2c_viapro             12969  0 
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
8139too                23208  0 
uas                    17676  0 
8139cp                 22497  0 
pata_via               13368  2

---

### Post by fdrake on 2011-09-01
> **DrRebar said:**
> Output for (sudo lshw -C network)

 *-network:0 [COLOR="Red"]UNCLAIMED  [/COLOR] 
       description: Ethernet controller
       product: [COLOR="Red"]AR5413 802.11abg NIC[/COLOR]
       vendor: Atheros Communications Inc.
  
You card uses ath5k driver, which is included in the kernels module by default since version 2.6.25, and should work fine in Ubuntu.
> 
ndiswrapper 192828 0 

You have installed ndiswrapper, so we need to get rid off that first,due to conflict issues.

try this commands and past here the outputs please:

```

sudo modprobe -r ndiswrapper
sudo modprobe -r madwifi 
sudo cat >> /etc/modprobe.d/blacklist
#disable ndiswrapper, it creates conflicts with ath5k <press-enter>
blacklist ndiswrapper <press-enter>
#disable madwifi, it creates conflicts with ath5k <press-enter>
blacklist ndiswrapper <press-enter>
<ctrl+D>
sudo rm /etc/modprobe.d/madwifi*
sudo apt-get install --reinstall linux-headers-$(uname -r)
sudo apt-get install --reinstall linux-backports-modules-wireless-$(less /etc/lsb-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f 2)-$(uname -r | cut -d "-" -f 3)
sudo aptitude update
sudo aptitude upgrade
sudo modprobe ath5k
reboot
sudo ip link set wlan%d up

```

if the problem persists, please see my previous post, post #2 and paste here the outputs.

---

### Post by cjcardinal on 2011-09-10
I'm curious if the OP ever managed to get this issue resolved.  I can say for certain that I had no issues out of the box with the WIFI, but that was using [this]("http://www.oqotalk.com/index.php?topic=3287.0") one-off installation of Ubuntu 8.10 that i found on the OQO Forums.  I am also curious if the OP could open a new thread, or point me in the direction of where I could get a little help installing a more modern version of Ubuntu, or xubuntu like 10.04+ because I am currently faced with all the normal live disk issues when trying to install

---

### Post by wildmanne39 on 2011-09-10
Hi, he never posted back we do not know if it is resolved or not.

You would be better off starting a thread in installations or general to get help on installing ubuntu.
Thank you

---

### Post by cjcardinal on 2011-09-10
> **wildmanne39 said:**
> Hi, he never posted back we do not know if it is resolved or not.

You would be better off starting a thread in installations or general to get help on installing ubuntu.
Thank you

Yeah i noticed that, so i did start a new thread.  this little device is quite a pain to get anything on it other than windows.  Ive tried crunchbang, ubuntu 9.04, 9.10, 10.04, 10.10, and 11.04 as well as Backtrack and Peppermint Two.  going to keep trying!

Thanks for the reply

---

### Post by wildmanne39 on 2011-09-10
Hi, your welcome! and welcome to the forum.

---

### Post by cjcardinal on 2011-09-11
I am really interested in the exact CLI command done to bring 11.04 to life on this device.  I am currently working on getting Peppermint Two on this thing and can get as far as formatting my drive, but then met with an installer crash

---

### Post by cjcardinal on 2011-09-11
as per the instructions in this thread, here are the outputs you asked for as I am facing the same issue now with Peppermint Two

```
carmen@minimax ~ $ sudo lshw -C network
[sudo] password for carmen: 
PCI (sysfs)  

  *-network:0             
       description: Ethernet controller
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:03:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=ath5k latency=168 maxlatency=28 mingnt=10
       resources: irq:17 memory:c2100000-c210ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:03:05.0
       logical name: eth0
       version: 10
       serial: 00:0c:96:40:44:f9
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.24 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:bc00(size=256) memory:c2110000-c21100ff
```

```
carmen@minimax ~ $ lspci -nn | grep 0280
carmen@minimax ~ $ lsusb
Bus 003 Device 003: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 003 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1557:0004 OQO 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
carmen@minimax ~ $ ^C
carmen@minimax ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

carmen@minimax ~ $ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

```
carmen@minimax ~ $ lsmod
Module                  Size  Used by
parport_pc             32111  0 
dm_crypt               22463  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_intel          24113  0 
snd_hda_codec          90901  1 snd_hda_intel
rfcomm                 38125  8 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
ath5k                 144534  0 
ath                    19141  1 ath5k
snd_seq_midi           13132  0 
mac80211              257001  1 ath5k
sco                    17827  2 
snd_rawmidi            25269  1 snd_seq_midi
bnep                   17785  2 
snd_seq_midi_event     14475  1 snd_seq_midi
l2cap                  48656  16 rfcomm,bnep
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  3 ath5k,ath,mac80211
btusb                  18160  2 
snd                    55295  8 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
psmouse                73312  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
i2c_viapro             12969  0 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
8139too                23208  0 
usb_storage            43946  0 
8139cp                 22497  0 
uas                    17676  0 
pata_via               13368  3 
carmen@minimax ~ $
```

---

### Post by wildmanne39 on 2011-09-11
Hi, please post the results of this command as well.
```
lspci -nn | grep -e 0280 -e 0200
```

Did you actually get ubuntu or some debian version of linux installed or are you running it from a livecd?
Thank you

---

### Post by cjcardinal on 2011-09-11
> **wildmanne39 said:**
> Hi, please post the results of this command as well.
```
lspci -nn | grep -e 0280 -e 0200
```

Did you actually get ubuntu or some debian version of linux installed or are you running it from a livecd?
Thank you


Here is the output

```
carmen@minimax ~ $ lspci -nn | grep -e 0280 -e 0200
03:04.0 Ethernet controller [0200]: Atheros Communications Inc. AR5413 802.11abg NIC [168c:001b] (rev 01)
03:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
```

I have [Peppermint Two]("http://peppermintos.com/") installed

---

### Post by wildmanne39 on 2011-09-11
Hi, let's see if we can install backports it should install the firmware for your card.
```
sudo apt-get install linux-backports-modules-wireless-natty-generic
```
you will have to change the last part to whatever your kernel name is.

This command will tell you your kernel name.
```
uname -a
```
Thank you

---

### Post by fdrake on 2011-09-11
@wildmanne39
just a tip.
uname -a > prints the kernel's information(name and version of kernel)
you are looking for the ubuntu distro release name
less /etc/lsb-release
see post #6

i also ,like you,think that by installing backports he should be all set, let's see

---

### Post by wildmanne39 on 2011-09-11
Hi fdrake, I see it, a lot of times I use this command but I am not felling good so I am not at my best.
```
cat /etc/lsb-release; uname -a
```
Thank you

---

### Post by fdrake on 2011-09-11
> **wildmanne39 said:**
> Hi fdrake, I see it, a lot of times I use this command but I am not felling good so I am not at my best.
 what do you expect after Saturday night?!:p:p:p

---

### Post by cjcardinal on 2011-09-12
ok so even with the proper repo in my sources.list, i "could not find package"  thoughts?  i have the backports enabled in my sources.

---

### Post by wildmanne39 on 2011-09-12
Hi, I do not know exactly how to do it since you are not using ubuntu, and the person I would normally ask is out of town.

If you post the information in post 17 here from that command it might help to figure it out.
Thank you

---

### Post by fdrake on 2011-09-12
> **cjcardinal said:**
> ok so even with the proper repo in my sources.list, i "could not find package"  thoughts?  i have the backports enabled in my sources.

you must have entered the wrong release name. please post the results of post #17

---

### Post by cjcardinal on 2011-09-12
sorry for the late response...

```
DISTRIB_ID=Peppermint
DISTRIB_RELEASE=2
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Peppermint Two"
Linux minimax 2.6.38-11-generic #48=Ubuntu SMP Fri July 29 19:05:14 UTC i68 6 i686 i386 GNU/Linux
```

---

### Post by cjcardinal on 2011-09-12
just to eliminate any potential issues based on the fact that I have Peppermint installed, I am downloading a fresh 10.04 Lucid right now and will re-do this thing and go from there.

I'll report back when everything is re loaded...thanks for all the help

---

### Post by wildmanne39 on 2011-09-12
Hi, your welcome! when you install if you choose to update and to install third party software a lot of times that helps.
Thank you

---

### Post by cjcardinal on 2011-09-12
> **wildmanne39 said:**
> Hi, your welcome! when you install if you choose to update and to install third party software a lot of times that helps.
Thank you

well now I am a little lost on doing CLI via a Unetbootin install, as per my new [thread]("http://ubuntuforums.org/showthread.php?t=1842892")

still working on it hahaha

---

### Post by cjcardinal on 2011-09-12
I would prefer to keep peppermint two because of how light it is...so i may continue to work on the wifi issue.





sound is next

---

### Post by wildmanne39 on 2011-09-12
Hi, does peppermint two have a support forum?
Thank you

---

### Post by cjcardinal on 2011-09-12
> **wildmanne39 said:**
> Hi, does peppermint two have a support forum?
Thank you

yeah, they do.  I'll post on there.  Thanks for your help wildmanne

---

### Post by wildmanne39 on 2011-09-12
Hi, your welcome! I hope they can help.

---

### Post by DrRebar on 2011-09-14
Hi There!
I did try to get back to this forum to let someone know that all of the solutions I have tried did NOT work. 
As I posted if someone has developed a simple way to get the OQO wireless and sound working, please let me know! A small fee would be coming your way!
For now I am awaiting shipment of a never opened OQO 1.6 GHz. I plan to take the HD out of the present OQO and transplant to the new one. On that SSD Windows 7, Mac OS 10.5.2 and Ubuntu 11.04 all have a separate partition. Sound and wifi work on the Windows and Mac side, but ubuntu does not. I have tried compiling drivers, kernels (from source files [takes about 12 hours on the OQO], and multiple system updates. For wireless I have also tried the madwifi driver. All my mojo on this Ubuntu install has cost me some days. I do enjoy Ubuntu and hope someday to get it working. The OQO otherwise will remain a triple boot wonder.

---

### Post by borborbor on 2012-01-03
Hi Oqo User :)
Please try to blacklist via-agp module (or rename it).
After that sound should work well.
My laptop is now connectet with Oqo 02 over wifi,
and on the Oqo there is madwifi-ng 0.9.4.4165.20110816 installed (gentoo).

When via-agp.ko is loaded I can use openchrome driver (dri and agp enabled),
but sound, wifi and usb is not working;
without via-agp module openchrome  is working (agp disabled) but also usb, sound and wifi are working very well.

Now I am using gentoo, kernel 3.1.5 but always were problems with via-agp -
also for ubuntu or debian. Kernel compilation time on Oqo 02 is about 90 min.

---

### Post by maestrobwh1 on 2012-01-06
I did the upgrade method mentioned here:

[http://ubuntuforums.org/showthread.php?t=1847296](http://ubuntuforums.org/showthread.php?t=1847296)

It gets you to Lucid with all working hardware.  I suppose I could do release upgrades to get to Ocelot but I don't see the point for what I need. 

and see my post #13 for further tweaks.  I booted a pen version of Ocelot to convert the resulting Lucid to ext4 (don't forget to change fstab to ext4 and set proper options)

Then also, upgrade to a backported Maverick kernel if you are using a SSD so that you can use the discard option to enable trim.

My Lucid OQO 02 used to take over a minute to boot from the traditional drive.  I am at a working desktop in 11 seconds with the SSD (mydigitaldiscount).

I even have the cou dialed back to 600 MHz and it does leaps and bounds over XP running at full cpu.  The OQO sounds like a vacuum cleaner.

---

### Post by borborbor on 2012-01-08
wifi:
I am now in living room, oqo is in my kitchen (about 10m and two solid concrete walls).
Ssh connection in ad-hoc mode is excellent. 
On my oqo(taken from my loptop screen in living room):
ath0      IEEE 802.11g  ESSID:"aaa"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 02:0C:96:40:84:0D
          ..............
         Link Quality=20/70  Signal level=-74 dBm  Noise level=-94 dBm
          
Ap mode also can be set.
On the other side now I am using: Bus 004 Device 003: ID 07d1:3c0a D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT2870].

hibernation:
It is possible to configure very well, following tuxonice guides
([http://en.wikipedia.org/wiki/TuxOnIce](http://en.wikipedia.org/wiki/TuxOnIce))

---

### Post by maestrobwh1 on 2012-03-01
@ borborbor

So you are running a gentoo kernel on ubuntu or peppermint two?  I tried peppermint two and liked how light it was but with pen drive from iso, no sound or wifi even with running a casper-rw persistence file where I could blacklist via_agp.  I already had Lucid working so I didn't try to install and tweak it. I also tried this as a boot option via_agp.blacklist=yes and this works for puppy linux slacko (latest).  With that as a boot option sound and wifi come right up in that version along with USB. Puppy beyond 4.2 was unusable but I found this reference on some place on the net.  Suspend doesn't work so puppy slacko is my fallback boot in case I need to work on Lucid.

Seems the via_agp module is really causing issues with later kernels on the OQO 02.

I have the via_agp.blacklist=yes boot option added into my /etc/default/grub to (hel) prevent a kernel upgrade from sabotaging me.

EDIT: I cloned my install and upgraded Lucid to Maverick, then Natty then Oneric.  The sound and wifi stopped working after Maverick so I am running 11.10 with Maverick's 2.6.35-32 kernel.  No perceived issues doing this.  Trim for ssd was supported starting with this kernel so I am not too badly affected.  Something happened with kernels later than 2.6.35 regarding the hardware on this machine.  If booting an install from usb (oddly boots fine as usb image created by USB creator with xforcevesa boot option, just not as fully installed os), it stalls and can't find the disk at some point and I am dropped into busybox: usb is shut down or being blocked during boot.  Also wifi and sound is blocked so something (suspect some configuration regarding via) is not loading properly with later kernels. The WIFI is supposed to be supported with ath5k even with 3.0.0  I transferred the setup to my HD and 3.0.0-16 boots but no wifi or sound. Annoying.

---

### Post by goatcow on 2013-02-11
Throwing a bump to this thread - hoping someone is still active that could maybe help - my issues are listed here with oqo model 02:  [http://ubuntuforums.org/showthread.php?t=2113143](http://ubuntuforums.org/showthread.php?t=2113143)

---

### Post by |{urse on 2013-02-11
Well, I've only seen everything working on the oqo2 with the iso I found here:

[http://www.oqotalk.com/index.php?topic=3287.0](http://www.oqotalk.com/index.php?topic=3287.0)

I've tried all kinds of crazy things to get a newer version of Ubuntu working but there's always issues with (surprise) networking!

Maybe you can bust that .iso open and figure out how they got it working.

---

### Post by goatcow on 2013-02-12
I installed using that image and it looks like they were using the madwifi (ath_pci) kernel modules....which when i tried compiling under 3.2 gave me the similar errors about HW revision not supported.

Time for more digging i suppose.

---

### Post by wildmanne39 on 2013-02-18
Old thread closed! Please do not bump old threads!

---

