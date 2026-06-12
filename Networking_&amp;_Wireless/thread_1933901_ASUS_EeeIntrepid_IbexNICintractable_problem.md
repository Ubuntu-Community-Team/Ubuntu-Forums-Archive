---
title: "ASUS Eee/Intrepid Ibex/NIC/intractable problem"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by Santillana on 2012-03-01
I have a problem that may be intractable because of the combination of factors that it entails, but I thought that if the competence to help solve this problem could be found anywhere, it would be on this forum with its board of world-beating experts.
 
 
I have a double installation of Ubuntu Intrepid Ibex and Windows 7 (sorry to use that kind of word in decent company). One problem is that I need Windows until I am independently capable of finding my way around the Internet. I cannot get Ibex to do this for me. Ibex will, as yet, not recognize that there is any Internet connection. Experimentation with Ibex' Network Manager (has a different appearance from other versions' Network Managers) and the terminal has led to nothing.
 
 
The double installation, too, with Gparted and GRUB, was much like a double bypass surgery that I would love not having to repeat. (I know Ibex is out of date, but Ibex was on my installation CD, came with C. Negus' book).
 
 
I have a wired NIC, Atheros AR8132, and a wireless one, Atheros AR2427. Windows connects perfectly to the Internet through either one.
 
 
**$ sudo lshw**
 
 
tells me that both cards are UNCLAIMED, meaning that no driver is in association with the NIC in question. This seems to be like the core of the problem, but I have no clear idea where the solution might be found. Wandering aimlessly on this forum and elsewhere has led to nothing. You know when you are making progress and when you have to rethink and I have to rethink right now.
 
 
I would be more than grateful for information to point me in the direction of a solution. I am in a learning process as far as Linux/Ubuntu/open source/networking, so any constructive response would be more than welcome.

---

### Post by chili555 on 2012-03-01
First of all, I'd like to congratulate you for being Interpid enough (ha! ha!) to try Ubuntu Linux. It is a lot of fun and I know you will enjoy it.

Let's start on the easiest task first: wireless. Your device is supposed to work with the module ath9k. The trouble is, I am not sure if Intrepid Ibex, also known as 8.10, includes ath9k. Let's check. Please open a terminal and run:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Please post the pci.id that you find. It will be something like 168c:002c.

Now let's see if ath9k exists on your ancient Ibex. Please run:```
modinfo ath9k
```Does it say that ath9k is not found or does it return lots of mysterious-looking data? If the latter, then ath9k exists.

Now let's see if your device is claimed by ath9k:```
modinfo ath9k | grep 002C
```Here, substitute the last four digits of the pci.id you found, if not 002c. Caplitalize any letters. 

Does ath9k both exist and claim your device? If so, let's load it and see what happens:```
sudo modprobe ath9k
iwconfig
```Was a wireless interface wlan0 created?

Depending on what you find will determine how we proceed.

---

### Post by Santillana on 2012-03-02
Thanks a million, chili555. Even if my problem IS intractable, this is competence expansion like nothing else. I found your commands/utilities in Mark Sobell's book and read up on them before I actually tried them. Reading the book from cover to cover as I am now doing, I would have come across them in about a month's time. Invaluable with somebody like you who can see things like that in context. Anyway, here's what happened:
 
```
$ lspci -nn | grep 0280
```
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:002c] (rev 01)
```
$ modinfo ath9k
```
ssfilename: /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko
license: Dual BSD/GPL
description: Support for Atheros 802.11n wireless cards.
Author: Atheros Communications
srcversion: 5307204F68EC6FC867B1E91
alias: pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias: pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias: pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends: mac80211
vermagic: 2.6.27-7-generic SMP mod unload modversions 586
```
$ modinfo ath9k | grep 002C
```
*The ”C” capitalized, but no result. Of course, there is no string ”002C”in the modinfo output to detect.*
```
$ sudo modprobe ath9k
```
*Password requested, but no visible result.*
```
$ iwconfig
```
lo no wireless extensions
pan0 no wireless extensions

---

### Post by chili555 on 2012-03-02
Well, let's try to trick ath9k to recognize your device. Even if this works, it may or may not drive the device effectively. It's certainly worth a try before I play the 'upgrade to Oneiric and all your troubles will be over' card. Please do:```

sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```

ACTION=="add", SUBSYSTEM=="pci", ATTR{idVendor}=="168c", ATTR{idProduct}=="002c", RUN+="/sbin/modprobe -qba ath9k"
```Caps, brackets, punctuation, etc. are crucial. Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long single line:```

install ath9k /sbin/modprobe --ignore-install ath9k $CMDLINE_OPTS; /bin/echo "168c 002c" > /sys/bus/pci/drivers/ath9k/new_id
```
Proofread twice, save and close gedit. Reboot and let us have your report.

We are on the bleeding edge of experimentation. I am sort of interested in how this works myself! There is nothing harmful here; it just either works or doesn't. If not, I have other cards ...ahem... up my sleeve.

Thanks for your kind comments.

---

### Post by chili555 on 2012-03-02
FYI, here is my modinfo:```
chili@LAPTOP60:~$ modinfo ath9k 
filename:       /lib/modules/[COLOR="Red"]3.0.0-16[/COLOR]-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     82D62ECA4C6A2273AD5EDE6
alias:          platform:ar934x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="Red"]168C[/COLOR]d0000[COLOR="Red"]002C[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,cfg80211,ath9k_common,ath
vermagic:       3.0.0-16-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
```

---

### Post by Santillana on 2012-03-02
I will pick up on your excellent suggestions on Monday, if that's alright. Your answers bounce back so fast I can't keep up. Private messages isn't working, so that's why this. All the best!

---

### Post by Santillana on 2012-03-05
Hi chili555, still no luck after having written the two text lines into the respective file (both files were initially empty, by the way) . Network Manager says "no connection".
 
Of course, the fault also lies with me for not being able to maneuver Ibex' Network Manager right. Right now, I have one connection in the list of connections and that is called ifupdown. I have been trying to remove all connections on the list in order to have a fresh start working from the command line but ifupdown will not go away.
 
The point to which I am trying to get is that your excellent ideas have not been seriously tried yet. I still have command line work to do, centering around commands like **ifconfig**, **ifup** and **ifupdown **- files like **etc/network/interfaces** and **/etc/resolv.conf** will also need to be worked with - all in order to actually create a connection on the right basis (more than likely the binding NIC/driver is now working). C. Negus' book on Linux says nothing meaningful about this, and neither does M. Sobell's or the college course book on Linux that I possess.
 
If you would further earn my gratitude, would you possibly advise me on this - on actually creating a connection from the command line, so the connection is turned on and Firefox can start working - or point me in the direction of some Internet resource where I could read up on all this? If by any means it can be avoided, I would like to avoid using the Ibex Network Manager because that seems to be one big failure from beginning to end. Many thanks in advance.

---

### Post by chili555 on 2012-03-05
Network Manager is so completely in control of networking that it is difficult to impossible to take back control with manual methods. If you really want to run on your own and not depend on NM, as I do on several of my computers, the best and perhaps only option is to remove NM entirely.

The other files are relatively easy. Here is a sample /etc/network/interfaces for a 40-bit WEP network named *yournetwork*:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid yournetwork
wireless-key 0123456789
```For /etc/reolv.conf, you may safely use the IP address of the gateway and let the router do the work:```
nameserver 192.168.1.1
```Normally, using DHCP, the appropriate nameservers will be supplied by the router and written into resolv.

Assuming these two files are written correctly, you should get a connection with:```
sudo ifdown wlan0 && sudo ifup wlan0
```These processes are described in eye-glazing details in their manual pages:```
man interfaces
man resolv.conf
```After writing the files I suggested, did a wireless interface get created?```
iwconfig
```Do you see networks in Network Manager? If you do, click on yours and see if you are challenged for any encryption details and connect. Does the card scan for networks?```
sudo iwlist wlan0 scan
```

---

### Post by Santillana on 2012-03-05
The man pages have a lot of information and I will get down to that right now - thanks.
 
Just for the record, I seem to have nothing concrete to work on just yet:
 
```
iwconfig
```
 
gave
 
lo no wireless extensions
 
pan0 no wireless extensions
 
 
 
Nothing like eth0, eth1 ocr wlan0 crops up.
 
```
sudo iwlist wlan0 scan
```
 
gave
 
wlan0 Interface doesn't support scanning.
 
 
I am aware that my problem statements are very fuzzy and wide. I will read up on the man pages and try to circle the problems more closely. Get down to the wire, like.

---

### Post by chili555 on 2012-03-05
> I am aware that my problem statements are very fuzzy and wide.They are fairly clear to an old-timer who went through much of the same a few years back. As well, working with new Ubuntians on elemental networking gives me some insight on what you may be experiencing.

Until we get the driver to recognize the wireless card and pick up the reins and drive, we have the cart before the horse. The finest, most elegant .conf files in the world won't revive a dead horse. 

Our report card is iwconfig. If there is nothing like this, all futher efforts are vain:> lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0      IEEE 802.11abg  ESSID:"mynetwork"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:13:10:62:88:77   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/100  Signal level=-51 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:483  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:2We need to see an interface with details. So far, that we do not see. The best place for diagnostics is in the kernel messages file, called *dmesg*. Let's see if there are any errors or warnings about ath9k:```
dmesg | grep -i ath
```Once we get the interface working, the rest is easy.

---

### Post by Santillana on 2012-03-05
I am getting down to this right now. Out of band question maybe: is the response
 
pan0    no wireless extensions
 
useless for our purposes?

---

### Post by chili555 on 2012-03-05
> **Santillana said:**
> I am getting down to this right now. Out of band question maybe: is the response
 
pan0    no wireless extensions
 
useless for our purposes?Correct. Personal Area Networking Profile (PAN) allows Bluetooth devices to form an ad-hoc network, access a remote network through a network access point.

We want the Atheros card to fall in love with and marry the ath9k driver and give birth to a wireless interface probably of the form wlan0. We'll accept eth1 and maybe ath0.

Did you proofread the files? Are they in place as expected?

---

### Post by Santillana on 2012-03-05
Yes indeed, both files are in the right place and containing exactly the text lines. Some reflections, though:
 
Curiosity 1: the text lines are so long that they cannot be fitted on one single editor line. When I backstep with the left-arrow key through the line to check, the cursor seems to skip the "/" after "sys" in one of the files and the "/" after "sbin" in the other. I wrote the lines exactly verbatim as you gave them to me.
 
Curiosity 2: there is a file copy with a ~ immediately after the file name in both places.
 
```
 
dmesg | grep -i ath

```
 
did not produce an error message but no other response either.

---

### Post by chili555 on 2012-03-05
Do you mean like this in example #1? If you maximize the text editor, does it expand like in example #2? Both files should only consist of *one* long line.> did not produce an error message but no other response either. How about this:```
sudo modprobe ath9k
dmesg | grep -i ath
```Or this:```
sudo su
modprobe ath9k
echo "168c 002c" > /sys/bus/pci/drivers/ath9k/new_id
iwconfig
exit
```If the latter stanza works, it suggests that the two files we wrote are, in some way, faulty and that we need to go about this in another way.

---

### Post by Santillana on 2012-03-05
Massive response to the first two-line command body:
 
[8837.37615] ath9k: 0.1
[8837.384785] ath9k 0000:02:00.0: PCI INT A > GSI 17 (level, low) -> IRQ 17
[8837.384827] ath9k 0000:02:00.0: setting latency timer to 64
...
...
+ 15 lines more of text. Can I have until tomorrow to write it all down, or is there even a way of isolating the more pertinent sections?

---

### Post by chili555 on 2012-03-05
> Can I have until tomorrow to write it all downOf course. This is for your support, not mine.

You can copy and paste from the terminal window to the text editor and save it to a USB key and transfer it to the computer you are answering on, if that helps.

---

### Post by Santillana on 2012-03-05
Very good. I'll look into a way of copy/paste. I am very grateful for your help, I just don't want you to be logged in just for my sake. If it seems all right, I'll send you a snap Private Message tomorrow when I've got the problem solved. Thank you! :)

---

### Post by Santillana on 2012-03-05
Massive response to be sure:
 
root@martin-laptop:/home/martin# sudo modprobe ath9k
root@martin-laptop:/home/martin# dmesg | grep -i ath
[ 8837.376515] ath9k: 0.1
[ 8837.384785] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 8837.384827] ath9k 0000:02:00.0: setting latency timer to 64
[ 8837.384973] IP: [<f9658bd0>] :ath9k:ath9k_hw_attach+0x20/0x80
[ 8837.385062] Modules linked in: ath9k mac80211 cfg80211 usblp usbhid hid ipv6 binfmt_misc sco bridge stp rfcomm bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_conservative cpufreq_ondemand cpufreq_userspace cpufreq_stats freq_table pci_slot sbs sbshc container af_packet iptable_filter ip_tables x_tables parport_pc lp parport joydev uvcvideo snd_hda_intel compat_ioctl32 videodev v4l1_compat evdev snd_pcm_oss snd_mixer_oss snd_pcm video output battery ac psmouse snd_seq_dummy serio_raw wmi snd_seq_oss button snd_seq_midi eeepc_laptop snd_rawmidi pcspkr snd_seq_midi_event snd_seq snd_timer snd_seq_device snd shpchp pci_hotplug soundcore snd_page_alloc ext3 jbd mbcache sd_mod crc_t10dif sg ahci libata scsi_mod dock ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 8837.385453] EIP is at ath9k_hw_attach+0x20/0x80 [ath9k]
[ 8837.385640] [<f966c46c>] ? ath_init+0x8c/0x5d0 [ath9k]
[ 8837.385740] [<f9662adc>] ? ath_attach+0x2c/0x230 [ath9k]
[ 8837.385861] [<f9662e05>] ? ath_pci_probe+0x125/0x2b0 [ath9k]
[ 8837.386764] EIP: [<f9658bd0>] ath9k_hw_attach+0x20/0x80 [ath9k] SS:ESP 0068:eb193da4
 
Thanks for the tip of copy/paste. Didn't believe that a common file format existed, but you were right as usual, so there did.
 
Look, no rush with this. Any time you feel like looking into this is welcome, so I don't have to feel like a sponger who adds insult to injury by trying to rush you on top of everything. All the best.

---

### Post by chili555 on 2012-03-05
> [ 8837.385453] EIP is at ath9k_hw_attach+0x20/0x80 [ath9k]
[ 8837.385640] [<f966c46c>] ? ath_init+0x8c/0x5d0 [ath9k]
[ 8837.385740] [<f9662adc>] ? ath_attach+0x2c/0x230 [ath9k]
[ 8837.385861] [<f9662e05>] ? ath_pci_probe+0x125/0x2b0 [ath9k]
[ 8837.386764] EIP: [<f9658bd0>] ath9k_hw_attach+0x20/0x80 [ath9k] SS:ESP 0068:eb193da4I think the human-readable version is something like, "I don't like your hardware, I don't like your driver, I think I'm gonna be sick." I don't think there is any realistic chance that the native ath9k driver is going to work even with all the dirty tricks at my disposal. I think you have a few options.> 'upgrade to Oneiric and all your troubles will be over'Or try ndiswrapper. Here is a reference: [http://ubuntuforums.org/showthread.php?t=1369304](http://ubuntuforums.org/showthread.php?t=1369304) Several posts describe the correct .inf file.

We could also look at compat-wireless. When you open Synaptic Package Manager, is there a linux-backports-modules-somesuch that deals with updated drivers?

I will be pleased to assist in any event.

---

### Post by Santillana on 2012-03-05
> **chili555 said:**
> I think the human-readable version is something like, "I don't like your hardware, I don't like your driver, I think I'm gonna be sick." I don't think there is any realistic chance that the native ath9k driver is going to work even with all the dirty tricks at my disposal. I think you have a few options.Or try ndiswrapper. Here is a reference: [http://ubuntuforums.org/showthread.php?t=1369304](http://ubuntuforums.org/showthread.php?t=1369304) Several posts describe the correct .inf file.
 
We could also look at compat-wireless. When you open Synaptic Package Manager, is there a linux-backports-modules-somesuch that deals with updated drivers?
 
I will be pleased to assist in any event.
 
The radical solution, of course, is to upgrade to Oneiric. Is there any way of doing that from within Intrepid? You know that I like my double installation and I would like to use it until I can send Windows 7 flying with my bootprint in the lower part of its back. Talk about "reboot Windows". :)
 
How about this: you point me to GOOD information about the upgrade process here on this forum or elsewhere, I read up on that, get started and then start putting INTELLIGENT questions to you whenever I first run into trouble. In the meantime, I will look at the NdisWrapper information in the thread above.

---

### Post by chili555 on 2012-03-05
Here is a good link: [http://www.webupd8.org/2011/03/ubuntu-live-cd-will-let-you-upgrade-to.html](http://www.webupd8.org/2011/03/ubuntu-live-cd-will-let-you-upgrade-to.html)

Download and burn the live CD. Boot from the live CD and select *Install*. Several options will be presented, including upgrade Ibex to Oneiric (maybe, if the gap is not too big), and the foolproof step which is to install Oneiric over Ibex, leaving Windows alone. Ordinarily, I'd caution to read and select carefully, but you seem to do all these things with care.

Of course, the big thing will be to be able to check the operation of the Atheros wireless before you upgrade. It ought to sing!

---

### Post by Santillana on 2012-03-05
> **chili555 said:**
> Here is a good link: [http://www.webupd8.org/2011/03/ubuntu-live-cd-will-let-you-upgrade-to.html](http://www.webupd8.org/2011/03/ubuntu-live-cd-will-let-you-upgrade-to.html)
 
Download and burn the live CD. Boot from the live CD and select *Install*. Several options will be presented, including upgrade Ibex to Oneiric (maybe, if the gap is not too big), and the foolproof step which is to install Oneiric over Ibex, leaving Windows alone. Ordinarily, I'd caution to read and select carefully, but you seem to do all these things with care.
 
Of course, the big thing will be to be able to check the operation of the Atheros wireless before you upgrade. It ought to sing!
 
Great. Action time. Be getting back to you.

---

### Post by chili555 on 2012-03-05
Before you check out the wireless running the live CD before you install permanently. If you get stuck, stop and ask. We're all here for you!

---

### Post by Santillana on 2012-03-06
> **chili555 said:**
> Before you check out the wireless running the live CD before you install permanently. If you get stuck, stop and ask. We're all here for you!
 
Oh, now I see. Bit slow on the uptake here. What you mean to say is that I've got to check that Atheros &.c is found and accepted on the LIVE CD before I install onto the hard disk. Point taken.

---

### Post by Santillana on 2012-03-06
One more question before I have a go, out of curiosity and for competence expansion: we talk about live CD's, we install from live CD's and we can do most everything running Linux from a live CD.
 
One thing has struck me, though - isn't it equally possible to install &c. from a "live USB" ? It ought to be memory or other memory, plus it would be slightly easier to operate since I already bought a sizable USB stick memory after your wise suggestion that I should copy and paste the error message of a few days ago. Just thinking out loud.

---

### Post by Santillana on 2012-03-06
Sorry, disregard post above. Just learned better. Ubuntu must be burned into an .ISO image, not just copied. CD is the thing.

---

### Post by chili555 on 2012-03-06
You seem to be gaining knowledge in leaps and bounds today! Wonerful stuff! Sorry I haven't responded until now; it's still early here.

I'm anxious to hear your progress.

---

### Post by Santillana on 2012-03-07
Embarrassing to be running up against problems from second 1. :( I have burned an .ISO-file containing Oneiric, and CD with it on is in a CD/DVD-reader connected to the computer I am trying to commit to Ubuntu. But at boot time GRUB only brings up Ibex, one ordinary version, one for recovery and one memory test version, along with Windows 7.
 
Key F2 at boot time lets me tinker with boot sources etc. but my feeling is I don't have a grip on what I am doing. A command line function within GRUB is also available with key 'c' but again plodding around without a grip seems counterproductive.
 
These problems, booting/GRUB/bootloader/BIOS... aren't really in any course syllabus of Computer science. Is there any book or other resource that sort of approaches these problems from Genesis and on? All you learn in Computer science &. turns to junk in sunlight, recursion, strings, objects, parameter transport...all useless in the real world. The real world has real problems like these boot-up problems but the real world doesn't have any dean that you can consult for the right source of information. 
 
The right information is only in the heads of a few brilliant people and you better be one of those people :( or have their ear on a forum like this one. :)

---

### Post by chili555 on 2012-03-07
As I've said, you remind me of me a few years back! The problems seem baffling and yet are fairly easy.

First, when you boot all the way into Ibex and drop the CD in the tray and browse the contents, do you see Oneiric.whatever.iso or do you see something more like the attached? If you see the .iso, then you need to go back and *burn as an image*, not just copy the .iso. Burning an .iso as an image expands the .iso to the underlying files as I show attached.

Second, you may need to set the computer's BIOS to make the first boot device as the CDROM instead of the harddrive. Then the computer will see a bootable drive and boot to the CDROM and Oneiric disk instead of GRUB on the harddrive.

When you start the computer and get that satisfying beep, there is an option to go into the setup menu pages; i.e. the BIOS settings. Look for bootup and use the arrow keys to move the harddrive down and the CDROM to the top in the boot process. Save, exit and enjoy.

Post back if you get stuck. I'm here.> The right information is only in the heads of a few brilliant peopleIn this case, 'brilliant' means been there, done that, made the mistakes, learned a little bit and have the gray hairs to show for it.

---

### Post by Santillana on 2012-03-08
Thanks another million,chili555. I'm gonna have to do this according to Hoyle. A long, thorny way of insight lies before me to Enlightenment.

---

### Post by chili555 on 2012-03-08
Your sensei and sherpa are here to serve.

---

### Post by Santillana on 2012-03-08
OK, one more thing then before I throw myself against the wall next time: is there available,easy to use freeware that lets me "burn as image" if I have an .ISO-file? Got kind of despondent after having ruined 4 CD-ROM's permanently - if you go the wrong way about it, the CD-ROM becomes write-protected and useless with just a useless lump of .ISO-data on it that is not a genuine image file. Windows 7 did this, semi-commercial Roxio did this, then I sort of stalled.

---

### Post by chili555 on 2012-03-09
Roxio appears to do what you want: [http://forums.support.roxio.com/topic/9877-how-can-i-burn-aniso-file/](http://forums.support.roxio.com/topic/9877-how-can-i-burn-aniso-file/)

[http://www.roxio.com/enu/products/dla/features.html](http://www.roxio.com/enu/products/dla/features.html)> .iso Image Burning - Roxio Burn will burn an .iso image. Just drop the .iso file onto the desktop icon. This allows all types of discs to be burned, including bootable, audio, video and other special disc types.Of course, it's easy within Ubuntu, if that's an option.

---

### Post by Santillana on 2012-03-09
OK, now at least I have a file configuration on disk (CD-ROM) that looks like the one in your .png picture. (Tried for 2½ hours to create a picture like yours of what it looks like). 
 
On the disk is now not one monster .ISO file, but a collection of files like yours;  .disk, boot, dists, doc, install... My conclusion is that "burn as image" has worked (whatever it was that happened).
 
Now, of course, what I do is that I interrupt normal booting with key F2 (normal booting would have given me a choice of booting either Windows 7 or Linux).
 
This gets me to a screen picture with five choices at the top:
 
Main   Advanced   Security    Boot    Exit
 
Only Boot is relevant. From Boot, I get a list of:
 
Boot Device Priority
 
Boot Settings Configuration
 
The Boot Device Priority gives me another list:
 
1st Boot  Device [Removable Dev.]
2nd Boot Device [HDD PM WDC1600B]
3rd Boot Device [USB: TSSTcorp CDDVD]
 
The item order in the list can be shifted with the "+" key. I have tried having both [Removable... and [USB:... first. The other, of course, is the hard disk itself and irrelevant unless for normal booting through GRUB.
 
The only result, irrespective of my choice of a boot source, is that the USB connected CD/DVD-reader/writer hums a little, then normal booting resumes. I am perfectly ready to overwrite Ibex with Ozelot, by the way, without even experimenting with whether Ozelot finds any Atheros cards or drivers, it's just that I am stuck at this point.

---

### Post by chili555 on 2012-03-09
We are getting close!!!> The only result, irrespective of my choice of a boot source, is that **the USB connected CD/DVD-reader**/writer hums a little, then normal booting resumes.Look under 'Advanced' and see if there isn't a setting to allow or disallow booting from USB. > 1st Boot Device [Removable Dev.]What for example? A floppy you can't use?> On the disk is now not one monster .ISO file, but a collection of files like yours; .disk, boot, dists, doc, install... My conclusion is that "burn as image" has worked Yes, indeed! Perfect!> Tried for 2½ hours to create a picture like yours of what it looks likeYikes!! Under Applicatiobs > Accessories > Screenshot. I select 'Select an Area to Grab' and draw a box around what I want to show. It takes the shot and so I can find it easily, I save it with a descriptive name to Desktop. Later, it gets dragged into a folder on my desktop called 'Forum.'

PS - Off to breakfast with Mrs. Chili. I hope I come back to a good report!

---

### Post by Santillana on 2012-03-10
CD-ROM had a segment fault. :( What's more, two other CD-ROM's failed for similar reasons. At least now I have a CD-ROM with the right content (13 correct files as in earlier post) in the CD/DVD-reader/writer. I have enabled booting from USB (critically important, thanks), booting priority 1 is from the USB which is connected to the CD device in question, so whenever the CD device is connected through USB, booting takes place from there. So far so good.
 
Now, what I remember that you told me to do was to boot from the CD with the disk image and try to install by choosing Install. I'd be overjoyed for some moral support before I take the plunge, not to mention possibly a pointer or two as to procedure.
 
(I got this process, with choosing Install, some way under way with the segment faulty CD disk image before that failed because of the segment fault, so I am in the right neighborhood).

---

### Post by chili555 on 2012-03-10
> Now, what I remember that you told me to do was to boot from the CD with the disk image and try to install by choosing Install. Correct. When it gets there, it will (in a more sophisticated way than this) ask if you want to install along side everything you have now; in place of Ubuntu Ibex *ONLY* or in place of everything, including Windows. Read carefully and select carefully. If in doubt, stop and ask.

Does it segfault *every* time you try to install? You might download and try the alternate install disk. [http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

---

### Post by Santillana on 2012-03-10
The installation is under way - sort of. Of course, it wouldn't be me involved if everything were running smoothly. I chose "replace 8.10 with 11.10" - very good.
 
But one problem which I would have thought would be trivial is holding up completion. Minutes and minutes pass as the stage **Keyboard layout **seems to be impossible to pass. In fact, I interrupted the last installation attempt after 25 minutes of standstill at **Keyboard layout** and recommenced.
 
What is asked of me seems completely trivial: **Choose your keyboard layout:. **I chose a Swedish keyboard layout out of the left hand column and then the Continue button. And there it is, now into 15 minutes of standstill (reading from disk resumes on and off) Is there some subtlety with simultaneously choosing from the right hand column? How long a waiting time is a reasonable waiting time? Can this stage be completed in some standard sure-fire way? The keyboard should be alterable at some later stage, when the OS is well in place.

---

### Post by chili555 on 2012-03-10
> The keyboard should be alterable at some later stage, when the OS is well in place.It certainly is.

You might try typing a few characters so the little box can see that you recognize and have responded to a request for input. I am a bit surprised, because in the 12,000 times I've installed, I select US keyboard, skip the typing part and continue...and it continues.

After you have typed a few characters, will it continue or is it still stuck?

---

### Post by Santillana on 2012-03-10
SUCCESS!! :) Ubuntu 11.10 is in place and working! US English keyboard did it.
 
Thank you so much, chili555! I am forever indebted to you.
 
Ubuntu 11.10 looks strangish just now, though. Just a couple of icons in a column to the left, nothing like **Applications   System   Places **as in 8.10. I am going to have to read up on recreating GNOME out of all this.

---

### Post by Santillana on 2012-03-10
Aha.
 
```
$ sudo apt-get install gnome-shell
```
 
on the command line. But how do I even start up a terminal from strangish "everything jammed to the left"?

---

### Post by chili555 on 2012-03-10
Awesome!

Start by clicking that black ball lookin' thing in the extreme upper left. A text box will open; type in any application, such as Solitaire. Selections will appear and click one and it opens!

It's called Unity. Some people love it and some hate it and go to Gnome. You might just try it for a bit before you decide.

So...how's the wireless???

---

### Post by chili555 on 2012-03-10
> Start by clicking that black ball lookin' thing in the extreme upper left. A text box will open; type in any application, such as Solitaire. Selections will appear and click one and it opens!...or terminal...or Synaptic...or gedit...or what have you.

---

### Post by Santillana on 2012-03-10
> **chili555 said:**
> Awesome!
 
 
So...how's the wireless???
 
I'll be looking into that with your recommended methods/commands from this thread. But 11.10 greeted the wireless NIC with its name even during the installation. It recognizes. :)
 
I have got to celebrate just a wink, then I'll try to connect to the wireless, if you think that is wise.

---

### Post by chili555 on 2012-03-10
> I'll try to connect to the wireless, if you think that is wise.Sure! Whenever you can is fine. Mrs. Chili and I are leaving in a couple of hours, so I'll look forward to your report whenever it is convenient for you.

---

### Post by Santillana on 2012-03-10
> **chili555 said:**
> Sure! Whenever you can is fine. Mrs. Chili and I are leaving in a couple of hours, so I'll look forward to your report whenever it is convenient for you.
 
As you know, I am more than grateful for your help and nothing would be further from my mind than rushing you. If you happen to have a moment, at some suitable point in time, you know that I will always be grateful and attentive.
 
The truth is that I have been pessimistic about the whole project and now I am a little shaken that pessimism has been crushed to smithereens. Got to rethink now! :)

---

### Post by chili555 on 2012-03-10
That's my new motto: Pessimism Crushed in 46 Posts or Less.

---

### Post by chili555 on 2012-03-10
So did you try to connect? Did you click the Network Manager icon, see you network, click it and connect?

---

### Post by Santillana on 2012-03-11
My ISP has been holding up on my wireless network passcode! :(

Now that I finally got a hold of the passcode, Lo and Behold! :D:D:D Just Connect, then activate Firefox, then the Pearly Gate swings open!

I am writing this to you 
on Ubuntu 11.10
on a functioning wireless connection
on Firefox

I am ever so grateful to you, chili555. How can I make it up to you?

---

### Post by chili555 on 2012-03-11
> Just Connect, then activate Firefox, then the Pearly Gate swings open!Awesome! Great news.> I am ever so grateful to you, chili555. How can I make it up to you? Thank you. I just got my payday when I read that big, beautiful SOLVED up there on a thread titled, in part, 'intractable.'.

I hope you will continue to learn Ubuntu Linux and become both proficient and confident. Have fun and post back if any of us can help you again.

---

