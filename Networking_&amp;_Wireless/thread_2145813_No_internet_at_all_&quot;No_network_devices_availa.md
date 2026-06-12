---
title: "No internet at all &quot;No network devices available&quot;."
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by xp15 on 2013-05-16
Hello every guy and girl, I have a problem, curse from hell.
I use the leptop "Toshiba satellite C6660" with Ubuntu 12.04, this weird problem didn't happend before.

In livecd the wifi worked as needed, also the mouse/touchpad (for this another thread will be created).
After installation, no mouse on screen, thought to update, but no wifi or wired connection is seen.

It's really weird, that when I connected it wired, I have no message, the system denied.
How to make it work? How to fix? I need your help, teach me some tricks.

information:
```

Shay@OneiricOcelot:~$ sudo lshw
.
.
.
*-network UNCLAIMED
        description: Ethernet controller
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:01:00.0
        version: 05
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list
        configuration: latency=0
resources:  ioport:4000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
.
.
.
*-network UNCLAIMED
        description: Network controller
        product: RTL8188CE 802.11b/g/n WiFi Adapter
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:06:00.0
        version: 01
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list
        configuration: latency=0
resources:  ioport:2000(size=256) memory:d1500000-d0404fff memory:d0400000-d1503fff
.
.
.

```

```

Shay@OneiricOcelot:~$ lspci -v
.
.
.
01:00.0 Ethernet controller: Realtek Semiconducter Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
            subsystem: Toshiba America Info Systems Device fd3c
            Flags: bus master, fast devsel, latency 0, IRQ 11
            I/O ports at 4000 [size=256]
            Memory at d0404000 (64-bit, prefetchable) [size=4k]
            Memory at d0400000 (64-bit, prefetchable) [size=16k]
            Capabilities: <Access denied>

06:00.0 Network controller: Realtek Semiconducter Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
            subsystem: Realtek Semiconducter Co., Ltd. Device 8184
            Flags: bus master, fast devsel, latency 0, IRQ 11
            I/O ports at 2000 [size=256]
            Memory at d1500000 (64-bit, non-prefetchable) [size=16k]
            Capabilities: <Access denied>
.
.
.

```

Thanks! :grin:

---

### Post by papibe on 2013-05-16
Hi xp15.

I have a Toshiba A665 with the same ethernet card (different wireless adapter though). It works fine both on 12.04 and 13.04. The driver for the card is called: r8169.

Let's see if we can get more details out the logs. Could you post the output of these commands?
```
dmesg | grep -iE '8169|eth'

grep -iE '8169|eth' /var/log/syslog
```
When you get that, I'd like to try to load the module manually:
```
sudo modprobe r8169
```
What happens after that? If you still don't have network, please post the result of this immediately after:
```
dmesg | tail -n 20
```
Regards.

---

### Post by xp15 on 2013-05-16
Thanks for the answer, I will run this command and will give you the output.
The only problem is that I have to copy the output manually, bacause i have no mouse/touchpad (also a connected mouse not working).
I will do it as fast as a I can (:

OK:
```

shay@OneiricOcelot:~$ dmesg | grep -iE '8169|eth'
[            0.287478] ACPI Error: M[COLOR=#ff0000]eth[/COLOR]od parse/execution failed [\_SB_.PCI0.LPCB.ECO_._REG] (node f3829e10), AE_NOT_EXIST (20110523/psparse-536)
[            0.458650] i2c-core: driver [aat2870] using legacy suspend m[COLOR=#ff0000]eth[/COLOR]od
[            0.458651] i2c-core: driver [aat2870] using legacy resume m[COLOR=#ff0000]eth[/COLOR]od

```

this is for the first command.
doing the second now (:

---

### Post by papibe on 2013-05-16
Ohh.. that's a big job.

If you have a USB stick, you could redirect the output into a file and then copy the files into the USB:
```
dmesg | grep -iE '8169|eth'  > log1.txt

grep -iE '8169|eth' /var/log/syslog > log2.txt

dmesg | tail -n 20 > log3.txt
```
Regards.

---

### Post by xp15 on 2013-05-16
Oh, Thanks. but for my bad luck, also usb isnt working. I have no idea why, and in livecd everything worked.
I managed to picture the outputs and burn ao a CD-ROM. this is the only texhnology which is still working (: .

Here is the output for the second command:

for the third command:

and for the last one:

Thanks for the CD-ROM I made it! ^^
Do you have a way to make logs burn to a cd? like the offer you gave me for a disk-on-key, so I may use in the future.

Thank again for your help (:

---

### Post by papibe on 2013-05-16
> **xp15 said:**
> I managed to picture the outputs and burn ao a CD-ROM. this is the only texhnology which is still working (: .
Very resourceful ;)

The 'FATAL' error is the most important message.

My guess this is a problem with the 3.2.0-36 kernel. This could be because  either a botched upgrade or a bug with that particular kernel.

This is what I would do: boot into a previous kernel and check if you have access to your network.

To do that, you need to stop at the grub menu (text mode boot menu), and select a previous version of the kernel to boot from (skip the recovery ones).

If you can get your network back on one of the previous version, fully upgrade your system to get the newest kernel (3.2.0-43).

Let us know if that helps.
Regards.

---

### Post by varunendra on 2013-05-16
> **papibe said:**
> My guess this is a problem with the 3.2.0-36 kernel. This could be because  either a botched upgrade or a bug with that particular kernel.
Not sure about the pae version, but I am using the "3.2.0-36-generic" on my 12.04, 64-bit, and there is no problem with it. Especially, any such problem with the r8169 driver would be big one and will be immediately addresses since it is a very common and important driver. So I second the opinion that it may be a broken upgrade.

[s]Also, if not a problem, why not upgrade to 12.04? Oneiric has already reached its EOL : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)[/s]
**EDIT: **Oops! Sorry, missed the very second line of the first post (ran far away from the hell..;)). Terminal prompt confused me..

---

### Post by matt_symes on 2013-05-16
Thread moved to [B]Networking and Wireless.

[/B]...with a redirect from the old forum

---

### Post by xp15 on 2013-05-17
> **papibe said:**
> Very resourceful :wink:

The 'FATAL' error is the most important message.

My guess this is a problem with the 3.2.0-36 kernel. This could be  because  either a botched upgrade or a bug with that particular kernel.

This is what I would do: boot into a previous kernel and check if you have access to your network.

To do that, you need to stop at the grub menu (text mode boot menu), and  select a previous version of the kernel to boot from (skip the recovery  ones).

If you can get your network back on one of the previous version, fully upgrade your system to get the newest kernel (3.2.0-43).

Let us know if that helps.
Regards.

Oh, sounds right. the problem is that this is a freash install, so I dont have other kernel versions (:
But, your solution is good. I'm pretty suer that my inmstallation is 12.04.1, while the livecd iteslf is upgraded to 12.04.2 (or just upgraded, from other computer I used with the DOK-DiskOnKey).
I will download and create a new installation now.

Thanks a lot, I will upadte you (:

Yesterday it was late at night, and I have had to go to sleep, and now i'm after school. soory for the time till I responsed



> **varunendra said:**
> Not sure about the pae version, but I am using the "3.2.0-36-generic" on my 12.04, 64-bit, and there is no problem with it. Especially, any such problem with the r8169 driver would be big one and will be immediately addresses since it is a very common and important driver. So I second the opinion that it may be a broken upgrade.

[s]Also, if not a problem, why not upgrade to 12.04? Oneiric has already reached its EOL : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)[/s]
**EDIT: **Oops! Sorry, missed the very second line of the first post (ran far away from the hell..;)). Terminal prompt confused me..

^^. yea. I liked the name of this version, and used it as a "Memorial". what does "ran far away from the hell" mean? (:


Thanks everyone :D

---

### Post by LocoMotor101 on 2013-05-17
Hello:  I am having exactly the same problem, and I was beggining to think that it might be a problem of the kernel.  I just installed 12.04.02 yesterday but I have not been able to get any networking at all: both ethernet and wifi.  I did not work yesterday just trying all kind of things recommended here at this forum, without success.  Should we just download an older version and forget about 12.04.02?  Thanks.

---

### Post by Bucky Ball on 2013-05-17
> **LocoMotor101 said:**
> Should we just download an older version and forget about 12.04.02?  Thanks.

No. 11.10 was before 12.04 and is no longer supported. 12.04 LTS an LTS and most stable. The problem lies elsewhere.

Is your mouse and touchpad working and do you have the same model Toshiba as OP? If not then I will move your post to a thread of its own.

---

### Post by xp15 on 2013-05-17
yes, are you able to use the touchpad?

what about:
connected mouse?
usb?
wired network/internet connection?
CD-ROM?

I started to think that no output method except screen and keyboard (include mouse-keys), is working. Only CD-Rom, the only way to get a data out of the laptop (exept a camra (: oh, and manually ^^)

---

### Post by varunendra on 2013-05-17
> **xp15 said:**
> ..what does "ran far away from the hell" mean?
It was supposed to be a joke :P (I got scared from the word "hell" in your first line, and immediately skipped a couple of lines to keep distance from it!)

By the way, yours almost certainly sounds like a bad installation. You may check the integrity of the downloaded ISO by matching its md5sum : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that matches, boot the live cd, press any key during the purple boot screen to bring up advance menu, and select "Check the disc for defects". Sometimes the iso may be ok, the cd burn may be not.

If you happen to download the ISO again, I'd strongly recommend to download via torrent, as it ensures integrity of the downloaded data : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

However, if the md5sum of your already downloaded image matches and the 'cd test' is also ok, you may wish to do a 'Memory Test' (from the same menu as "check disc for defects") to test any possible memory leakage issues.

Although there can be many reasons for a broken installation/upgrade, but these two (bad source, bad memory) are most common.

> **LocoMotor101 said:**
> Should we just download an older version and forget about 12.04.02?  Thanks.
LocoMotor101,

I found your original thread : [http://ubuntuforums.org/showthread.php?t=2145799](http://ubuntuforums.org/showthread.php?t=2145799)
As per outputs of your last post (#19), your wireless is already all set. It is just 'Disabled' now which I'm sure Hadaka, who is helping you on that thread, will be able to fix easily. He is a dedicated member and you can trust him for solutions to such issues.

As for your wired connection, it should work out-of-box with 13.04, since the required driver is included in it (but not in earlier versions). However, it is highly recommended to 'Test' a version using live cd before installing it. Only install if everything works, or can be made to work as expected.

You may also choose to install the required 'alx' driver by manually downloading and compiling it, but I'd suggest to wait for what Hadaka is willing to try.

---

### Post by xp15 on 2013-05-17
> **papibe said:**
> Very resourceful ;)

The 'FATAL' error is the most important message.

My guess this is a problem with the 3.2.0-36 kernel. This could be because  either a botched upgrade or a bug with that particular kernel.

This is what I would do: boot into a previous kernel and check if you have access to your network.

To do that, you need to stop at the grub menu (text mode boot menu), and select a previous version of the kernel to boot from (skip the recovery ones).

If you can get your network back on one of the previous version, fully upgrade your system to get the newest kernel (3.2.0-43).

Let us know if that helps.
Regards.



YAY! I'm so glad you found me! So happy for your answer and help! You were right! I made a new installation with a new downloaded ISO (also a 64 bit this time-I'm used to 32 bit ^^)
Thank! TNX! and Thanks you very much! You made my laptop work! Network, Internet, USB, Mouse! Touchpad!

Thanks again and I wish you an Happy-Year!

> **varunendra said:**
> It was supposed to be a joke :razz: (I got scared from the word "hell" in your first line, and immediately skipped a couple of lines to keep distance from it!)


I'm soory about that ^^ Just waned to make my post with rhymes ^^ .
And I succeeded! papibe was right about trying another kernel version (:


Thanks everyone for giving answers and solutions! this thread will help many Linux users! :D

and LocoMotor101, try also making a new installation Disk or USB with a new ISO, download from Ubuntu site the 12.04.2 (don't forget the right bit version ^^).



Thanks you all! I wish you all a success in everything!

---

### Post by Bucky Ball on 2013-05-17
Good news. Please mark thread as solved to help others as follows:

Edit first post>Go Advanced>change prefix [all variants] to [SOLVED]. Thanks and good luck. ;)

PS: I have also attached your large image in the last post and removed it from the body of your post. Please refrain from putting large images in the body of your post.

---

### Post by xp15 on 2013-05-17
Done! And I just like big pictures (:

---

### Post by papibe on 2013-05-17
> **xp15 said:**
> YAY!
Yay :D

Glad you have your computer back.

---

### Post by Bucky Ball on 2013-05-17
> **xp15 said:**
> And I just like big pictures (:

Lol. Me too, but those with slow connections (and vision issues) can, unfortunately, find them a laggy, sluggish nightmare or a blurry mess. ;)

---

### Post by xp15 on 2013-05-18
> **Bucky Ball said:**
> Lol. Me too, but those with slow connections (and vision issues) can, unfortunately, find them a laggy, sluggish nightmare or a blurry mess. ;)

Got it ^^ . Some people has a slow connection, and some not a lot of RAM, like me :D (Hint: 1GB ^^)

---

