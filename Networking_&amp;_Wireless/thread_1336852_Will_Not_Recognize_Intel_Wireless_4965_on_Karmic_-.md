---
title: "Will Not Recognize Intel Wireless 4965 on Karmic -Please Help"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by mercerudy on 2009-11-24
Hello all,

I just changed out the Broadcom wireless card in my Dell Mini 9 for the Intel 4965.  I expected it to go smoothly because I was under the impression that this card worked with Ubuntu 9.10 out-of-the-box, and I'm still not quite sure if that impression was correct.  I uninstalled the Broadcom drivers after booting up with the Intel card and after noticing that my Intel card wasn't being picked up, I reinstalled network manager.  I also tried
```
sudo modprobe iwl4965
```which returned nothing and didn't change the problem.  I decided to try booting from my live stick, and it worked!  The card was recognized and performed beautifully.  So, I decided to just go ahead and reinstall Ubuntu (just my "/" partition), and again, the card worked.  After rebooting, the card was not seen again...I went ahead and did a full os reinstall and it still isn't seen...I've searched high and low but haven't found anything yet that has worked for me.  I'm pretty new to Linux, so please bear with me.  I hope someone can help me figure this out soon!  Thanks!  Other info:

```
lspci
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 57)

``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

``````
sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 57
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f0200000-f0201fff

``````
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
``````
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                          Ignoring unknown interface eth0=eth0.

```

So I suppose the problem lies within the fact that the Network is Unclaimed...

---

### Post by mercerudy on 2009-11-29
No suggestions at all?  Please help me if you can...

---

### Post by mercerudy on 2009-11-30
Added details... bump

---

### Post by mercerudy on 2009-11-30
Please Help!  :confused:  ](*,)
Tried
```
rmmod iwlagn
sudo modprobe iwlagn
```

Also...
```
dmesg | grep -ie radio -e iwl -e wlan
[    5.857455] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    5.857466] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    5.857675] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.857724] iwlagn 0000:03:00.0: setting latency timer to 64
[    5.857849] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[    5.861065] iwlagn 0000:03:00.0: EEPROM not found, EEPROM_GP=0x90000000
[    5.861078] iwlagn 0000:03:00.0: EEPROM not found, EEPROM_GP=0x90000000
[    5.861086] iwlagn 0000:03:00.0: Unable to init EEPROM
[    5.861127] iwlagn 0000:03:00.0: PCI INT A disabled
[    5.861158] iwlagn: probe of 0000:03:00.0 failed with error -2

```

---

### Post by mercerudy on 2009-11-30
So everything I've read tells me that the necessary drivers have been present since kernel 2.6.24.  I am using the latest kernel and tried loading the modules myself...

What am I missing?

Any help would be appreciated.  Thank you...

---

### Post by reinier on 2009-12-01
I have the same problem since I switched from 9.04 to 9.10 about 1 month ago. I have tried all the suggestions I could find on the web, but without any result. I hope someone will come up with a solution soon. Sorry, but I cannot help you.

---

### Post by chili555 on 2009-12-01
> [    5.861078] iwlagn 0000:03:00.0: EEPROM not found, EEPROM_GP=0x90000000
[    5.861086] iwlagn 0000:03:00.0: Unable to init EEPROMThis is clearly the issue. I have googled it and not seen anything suggesting a fix.

I wonder if it has anything to do with swapping out the card.> I just changed out the Broadcom wireless card in my Dell Mini 9 for the Intel 4965.

---

### Post by mercerudy on 2009-12-01
Thank you both for your replies.

Yes, the Broadcom card worked fine, but I "upgraded" to the Intel 4965, as it had space for another antenna as well as support for packet injection (it would be great to use my dell mini for that).

What stumps me is that the card WORKED when I booted from USB live stick, but after a subsequent reinstall, the card is "UNCLAIMED" and

```
[5.861078] iwlagn 0000:03:00.0: EEPROM not found, EEPROM_GP=0x90000000
[5.861086] iwlagn 0000:03:00.0: Unable to init EEPROM                      
```What gives? Thanks again for your help...

---

### Post by mercerudy on 2009-12-01
So I've been reading some more, and the EEPROM problem has been associated with hardware wireless kill switches before (Fn 2 in my case with the Dell Mini 9).  I've never used Fn 2, but after trying to toggle it, there is still no change, the network interface is still "UNCLAIMED."

Could this help anyone to help me? Please?

---

### Post by chili555 on 2009-12-01
You might try some of the workarounds here: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/193970?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/193970?comments=all)

This one looks promising:> hit the wireless button, then do
 sudo modprobe -r iwl4965
 sudo modprobe iwl4965

---

### Post by mercerudy on 2009-12-01
Thanks again, Chili.

I've already tried all of the workarounds that I could from that bug report, but my network manager isn't even picking up the wireless card, so I couldn't try all of them.  Also, that bug was reported as "fixed" with Ubuntu...

I tried
> hit the wireless button, then do
 sudo modprobe -r iwl4965
 sudo modprobe iwl4965                      but this did not return the wireless, it did however, make the output for

sudo /etc/init.d/networking restart

change to...

```
 * Reconfiguring network interfaces...                                                                                [ OK ] 
```instead of...

```
 * Reconfiguring network interfaces...                                                                                       Ignoring unknown interface eth0=eth0.
                                                                                                                      [ OK ] 
```

but I don't think that has anything to do with my problem.  The Intel Card is still "UNCLAIMED" according to:

sudo lshw -C network

I don't know what I should do, downgrade the os or downgrade the card.  I don't want to do either :cry:

---

### Post by teward on 2009-12-01
Okay, I read your error.  I know a few things:  If it can't read the EEPROM, it means your card is bad because something killed it.  The EEPROM is the chip on/in/part-of the card which processes everything,  If it can't read it, its dead, and you should swap it out for a new card.

---

### Post by mercerudy on 2009-12-01
Oh, and by the way...

```
sudo rmmod iwl4965
ERROR: Module iwl4965 does not exist in /proc/modules

```

:shock: :-k

---

### Post by mercerudy on 2009-12-01
Hey sorry TrekCaptain, I didn't see your post in time...so the card is bad, no question about it?  Could it not have anything to do with the module not being found?  Plus, the card worked under USB boot when I first installed it.

Thanks in advance...

---

### Post by zaphod777 on 2009-12-01
try installing the backports from synaptic manager. I had to install it before wireless would work on my xps1530 that has the 4965 adapter.

---

### Post by mercerudy on 2009-12-02
> try installing the backports from synaptic manager. I had to install it before wireless would work on my xps1530 that has the 4965 adapter.

Sounds promising...I'm sorry, but I'm pretty newb to all of this.  What are you talking about exactly? :oops:
Thanks.

---

### Post by teward on 2009-12-02
> **mercerudy said:**
> Hey sorry TrekCaptain, I didn't see your post in time...so the card is bad, no question about it?  Could it not have anything to do with the module not being found?  Plus, the card worked under USB boot when I first installed it.

Thanks in advance...

The probability that the card is bad is about 35% that its bad, and 65% that its still operational.  The issue with EEPROM is that it can be read in multiple ways... if the OS isn't configured to correctly read the EEPROM's information/data, then you'll get such an error as your EEPROM error.  However, lets assume for a moment that the OS is not the problem (as in, install the backports for your computer.  don't ask me, I don't know how to do that).  If the OS (operating system) **is** correctly configured to read the card, yet you still get an EEPROM read/access error, that makes the probability of the card being bad about 75% and the probability its still functional 25%.  The problem is where you use two different OS (like my computer), and one OS reads the card and the other doesn't, which usually means an issue with how the OS reads the data.

My recommendation to test if its the card failing is to (NOTE: If you don't know how, have a tech do this) get a new or confirmed-functional card of the same type and swap it out with the current one and try to load it.  If you get an EEPROM error again, then the problem is not the wireless card, but your OS.  However, if the new card works and you don't get an EEPROM error, then it means your card was bad.

And yes, if the module itself isn't being detected, then it means Linux and your wifi card don't have working drivers, in which case your system wouldn't be able to detect it correctly anyways.


Sorry for the long post, I'm really high on coffee and caffeine right now.  :P :P :P

---

### Post by mercerudy on 2009-12-02
> Sorry for the long post, I'm really high on coffee and caffeine right now.  :razz: :razz: :razz:

No problem!  I really appreciate it!  I would love to get my hands on another card, but I don't have the funds for that unfortunately.  I suppose another option would be to dual-boot and see if XP picks it up (I've already completely reinstalled Karmic trying to fix this problem, so it wouldn't set me too far back).  Before I go into trying that...if zaphod777 or someone could let me know about installing the backports, that would be great!

Thanks again.

---

### Post by teward on 2009-12-02
> **mercerudy said:**
> No problem!  I really appreciate it!  I would love to get my hands on another card, but I don't have the funds for that unfortunately.  I suppose another option would be to dual-boot and see if XP picks it up (I've already completely reinstalled Karmic trying to fix this problem, so it wouldn't set me too far back).  Before I go into trying that...if zaphod777 or someone could let me know about installing the backports, that would be great!

Thanks again.

Yeah, the OpSys test (dualbooting, at least temporarily) is a perfect way to test the card.  If Windows reads it fine, then its an issue with Ubuntu, where you might be missing files or something.  Otherwise, I can only assume the card died.

---

### Post by zaphod777 on 2009-12-02
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

system -> administration -> synaptic package manager

type backports into the search and you can select to install them

in the pic attached you can see the ones highlighted in green that I have installed.

I think if you run this from the command line

```
sudo apt-get install linux-backports-modules-karmic
```

that should do the trick and then reboot

---

### Post by mercerudy on 2009-12-02
No luck with the backports, but thanks anyway zaphod.

I'll try booting XP next and see if the card is even alive...

---

### Post by teward on 2009-12-02
If the card is dead, you'll have to (depending on whether its a laptop or desktop) go to the manufacturer of the computer (if laptop) or some other tech person who will charge you (if a desktop).

*yawn*  Well, back from a good nights rest, and I've been thinking:  If the card is not dead then perhaps the Intel card is not compatible with Linux.  I've noticed this with a few pieces of hardware, where the device doesn't know how to work with Linux, and you're stuck with it working only on Windows.

---

### Post by mercerudy on 2009-12-02
> If the card is not dead then perhaps the Intel card is not compatible with Linux. I've noticed this with a few pieces of hardware, where the device doesn't know how to work with Linux, and you're stuck with it working only on Windows.

Thanks again, TrekCaptain, but there are two things which stand at odds with that in this case...

> I decided to try booting from my live stick, and it worked! The card was recognized and performed beautifully. So, I decided to just go ahead and reinstall Ubuntu (just my "/" partition), and again, the card worked. After rebooting, the card was not seen again...

> So everything I've read tells me that the necessary drivers have been present since kernel 2.6.24.Doesn't that suggest that the card is somehow compatible?

---

### Post by pbrane on 2009-12-02
Are you sure you have linux-firmware installed? It must install by default, but I'm not sure. You may need this in order to use the intel card.

**dpkg -l | grep linux-firmware**

This site suggests that the card has linux drivers. Intel has open sourced most of their drivers for linux.

[http://intellinuxwireless.org/]("http://intellinuxwireless.org/")

---

### Post by teward on 2009-12-02
The possibility is also that as I stated a long time ago the card is truly dead.  Or, you might try what the poster before me said, and make sure that linux-firmware is installed.  Because booting off the stick, it already loads the firmware.  Perhaps the linux-firmware wasn't transferred to your computer...  have you tried it with the Live disc again to confirm it works?

---

### Post by mercerudy on 2009-12-02
I tried reinstalling the firmware and backports...no change

> have you tried it with the Live disc again to confirm it works?Yes, that was the first thing I tried after reinstalling (when the card began showing "UNCLAIMED"), but it behaves just the same as booting from my ssd now.  I just don't see how the card could go out on me like that after doing a simple reinstall...

One more thing I just noticed...

**sudo modprobe -r iwl4965 && modprobe iwl4965**
Returns:
```
WARNING: Error inserting mac80211 (/lib/modules/2.6.31-15-generic/updates/cw/mac80211.ko): Operation not permitted
WARNING: Error inserting led_class (/lib/modules/2.6.31-15-generic/kernel/drivers/leds/led-class.ko): Operation not permitted
WARNING: Error inserting iwlcore (/lib/modules/2.6.31-15-generic/updates/cw/iwlcore.ko): Operation not permitted
FATAL: Error inserting iwlagn (/lib/modules/2.6.31-15-generic/updates/cw/iwlagn.ko): Operation not permitted

```Does that mean anything?  When I tried the two commands separately, they returned nothing.

And when I try:

**sudo rmmod iwl4965**

I get:
```
Module iwl4965 does not exist in /proc/modules

```Meaning the driver isn't even present? :confused:

I'm going to set up a dual boot with XP soon to make sure about the card...

---

### Post by chili555 on 2009-12-02
> Meaning the driver isn't even present?There is no *iwl4965*. Your card uses *iwlagn*. Please try again and let us know the result.```
sudo rmmod -f iwlagn && sudo modprobe iwlagn
```

---

### Post by mercerudy on 2009-12-02
> There is no *iwl4965*. Your card uses *iwlagn*. Please try again and let us know the result.Thanks, that is correct, but
 [FONT=monospace]
[/FONT]```
sudo rmmod -f iwlagn && sudo modprobe iwlagn
```

made no change

The modinfo for iwlagn listed my card, but it's still unclaimed...

Any other suggestions?  Still trying to work out installing XP via USB so I can see if the card is alive or not.

---

### Post by teward on 2009-12-02
Got a question... is this a netbook?

If it is, netbook hardware is even more finicky/tempermental than normal laptop hardware.  Just switching out the card(s) is enough to kill it.  Also, on Dell computers and similar, if you don't hook up the connecting wires right, your card will go *BOOM* and die on you the moment you turn on your computer.

So it's possible that the installation of the card killed it because of incorrect installation.  But since it worked with the Live USB boot, then i don't know.  maybe because you were trying to load incorrect drivers?

---

### Post by mercerudy on 2009-12-02
> Got a question... is this a netbook?

Yes, it's a Dell Mini 9, and I know that the card is installed correctly.  The only wires are 2 antennae.

> maybe because you were trying to load incorrect drivers? 	

You're not saying the card might have died because of the wrong drivers, are you?

---

### Post by linux6994 on 2009-12-02
I had wireless trouble with Karmic also and tried many, many things. I ended up loading Liunx Mint which is also Karmic based and it works fine, just a thought.

---

### Post by teward on 2009-12-02
Okay, I contacted some of my friends who are much more experienced techs (they work with Windows computers, but have VAST knowledge regarding hardware issues), via IRC chat.

Here's the convo log (I'm Trek, one of my friends is Milborn):
> 
<Trek> now for my turn.
<Trek> someone decided to swap out the wifi card in their laptop (originally Broadcom) to an Intel card.  Their computer detected it for all of 5 seconds.
<Trek> now when they try and manually configure it (the Intel card, and in any OS) it returns one of two errors:  not present, or EEPROM input/output errors.
<Trek> can we safely assume the card isn't functioning properly?
<Milborn> pretty much or its just not compatible
So, because we know the card is compatible with your OS, and it **should** be compatible with your hardware (I have a Dell Latitude laptop, and it uses an Intel card, possibly the same model as you), we can assume that the Intel card died or was damaged somehow during installation.  Or, perhaps the card was DOA (Dead on Arrival).

---

### Post by teward on 2009-12-04
> **mercerudy said:**
> Yes, it's a Dell Mini 9, and I know that the card is installed correctly.  The only wires are 2 antennae.



You're not saying the card might have died because of the wrong drivers, are you?


Wrong drivers can result in the hardware being screwed up by receiving in-compatible commands.


The only two wires are antennae?  Okay, I work with laptops, and there are occasionally more than one contact point on the card.  If you don't hook it up correctly, the card can get fried.

Further, understanding that it is a Dell means that its possible for me to figure out whether the intel card works with your model.  I'll be back in a little bit.

---

### Post by mercerudy on 2009-12-05
> The only two wires are antennae? Okay, I work with laptops, and there are occasionally more than one contact point on the card. If you don't hook it up correctly, the card can get fried.

Yes, that is true, but it's not the case here.  Here's a picture of the card that I found if you'd like to see it - [http://pixca.net/wp-content/uploads/2008/07/pp1050774.jpg](http://pixca.net/wp-content/uploads/2008/07/pp1050774.jpg)

It has 3 antenna hookups, but I only used 1 and 2 (I planned to put in a third later), which shouldn't have been a problem, right?

Any way, I put Windows XP on my mini today and the error I got back in the hardware properties was something to the effect of "The device could not be started," even after I manually loaded the correct drivers.

So TrekCaptainUSA, I believe that you were right all along, the card itself must be faulty.

The Broadcom will have to do for now, and I'm only down about $25 for the Intel Card... :-|

Thank you all for your help.  It was a great learning experience!

---

### Post by teward on 2009-12-07
I'm going to be a bit evil and cut up your last post and respond to it in parts. MUAHAHAHAHAH!

Anyways...

> It has 3 antenna hookups, but I only used 1 and 2 (I planned to put in a third later), which shouldn't have been a problem, right?
Sometimes, even if there's 3 antenna hookups, or any number of contacts, you're only supposed to use 2 of them, and even then sometimes specific ones of the hookups.  But this information is null and void in this case, as Windows was unable to access the device as well.

> Any way, I put Windows XP on my mini today and the error I got back in the hardware properties was something to the effect of "The device could not be started," even after I manually loaded the correct drivers.
So TrekCaptainUSA, I believe that you were right all along, the card itself must be faulty.
Usually this is the case, especially when two operating systems can't access the card.

> Thank you all for your help.  It was a great learning experience!
No problem.  We're here to help you out, and to help you learn about Ubuntu and stuff.  Feel free to stop back whenever with any questions you might have.  :)

---

### Post by waliays on 2009-12-16
May this help someone:
I had exactly the same symptoms, same story, but it turned out there was nothing broken at all.

My bios was set to turn off wlan when wired lan was available. So during most of the testing and cursing wlan did not work though I knew that once upon a time it had worked for a minute or so...
Solution: PLUGGING OUT THE CABLE did the trick! Telling bios not to be so smart didn't help btw.

Network manager wicd can also be configured to use wire only, when possible. But in my case wicd didn't even see the card cause it was shut down somehow. Nevertheless it was visible in iwconfig and *sometimes* in ifconfig. In wicd the card disappears and reappears when the wire is disconnected/connected.

---

### Post by w1zard on 2011-12-17
Very late to reply to this thread, but thought I would add I have just had *exactly* the same experience as you.

Upgraded a Mini 9, from the Dell Broadcom card that is fitted as standard, to an Intel 4965.

The wireless actually worked on the first and second boot. Perfectly - tested websites, downloads, etc.

Came back to the laptop 30 mins later, and the card didn't work. Long story short, I was getting the same EEPROM errors you were getting - no matter what I did, the card wouldn't work. After around 4 hours of various kernels, fixes, patches and updates, I gave up.

I have no idea what causes this, but as I'm using a very different version of Ubuntu to you (11.10), I can only assume the Dell Mini 9 does not like the Intel 4965 wireless card. I hope this serves as a warning to others!

I'm back to the old Broadcom card for now, and will attempt to upgrade to a Broadcom chipset 802.11n card instead when I have 'recovered' from this experience :)

---

