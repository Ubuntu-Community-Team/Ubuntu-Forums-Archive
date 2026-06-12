---
title: "Asus 1005HA wireless trouble...need explanation in simple terms..."
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by EmrysPen on 2009-08-02
Alright so I'm completely lost as to what I can do here. I know there are other threads that address this, but I've found most of them to be either (a) above my head or (b) outdated. I'm very new to Linux, and I need someone to help me out with this in very simple terms. Any help would be much appreciated.

(I do have limited experience in using the terminal, though)

I recently bought an Asus Eee 1005HA netbook, and it came with Windows XP. I decided that I wanted the computer to run Linux, so I downloaded and installed Ubuntu Netbook Remix. I found I didn't like that interface all, and then changed it to the desktop version of Ubuntu. I like this very much, and this is where I am now.

However, I can't seem to get internet on it. I click on the whole "Edit Connections" thing and nothing comes up under wireless (even though I know the network is working fine). The internet worked fine when I had XP on it.

I've tried the solution suggested in [this thread]("http://ubuntuforums.org/showthread.php?t=1191178"), but my Synaptic can't seem to find ndisgtk. 

I've tried a couple of other things too, but, like the above solution, I always get stuck at some step where I find that my computer is missing something.

Could someone help me out? I've been messing around with it for a day now and I have no idea what to do. And I'd preferably like not to have to use an external wifi adapter.

---

### Post by GeorgeVita on 2009-08-02
Hi **EmrysPen** and welcome to this forum.

Hoping that this is not a program/driver problem you can do 3 basic tests.

1. check if wireless is enabled from BIOS

2. looking up right on your desktop panel there is an icon showing 'signal bars'. This is the Network Manager Applet which when 'left click it' shows the WiFi networks received and 'right clicking' there are 2 Enable selections (networking and wireless). Check that they are enabled.

3. Open a terminal window (Applications > Accessories > Terminal) and try the command:```
sudo lshw -c network
```this will list all hardware information regarding the 'class' network. Copy and Post here the terminal respond. You can get more info about a terminal command by adding **--help** after the command or **man** before the command: **lshw --help** or **man lshw** To exit from 'man pages' press **: Q**

Regards,
George

---

### Post by EmrysPen on 2009-08-02
Thanks so much for your reply.

1. I checked, and my BIOS says "Onboard WLAN [Enabled]." Does that sound right? Everything under "Onboard Device Configuration" is [Enabled], in fact.

2. Hmm. This might be a problem. When I left-click, it says "No network devices available." When I right-click, there's no "Enable Wireless" option.

3. This is the output I got: 
  *-network UNCLAIMED
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:45:1c:7e:8d:02
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Does that look right?

---

### Post by walt.smith1960 on 2009-08-02
I had an identical problem. I was able to find a USB WiFi adapter that was recognized by the Eee1000HAB. Once I was able to establish a network connection, I typed this command in a terminal:

sudo apt-get install linux-backports-modules-jaunty

This command will download a driver for the installed Atheros WiFi.  The wired ethernet is more involved. I did download a nightly build of 9.10 netbook remix.  9.10 will have  much better netbook support once it's released.

---

### Post by GeorgeVita on 2009-08-02
Hi **EmrysPen**, I think the problem is on "UNCLAIMED", so this is a 'search string' together with '1005HA' and 'AR9285' which is the RF chip used for the WiFi.

*********
EDIT: as we post almost the same time with **walt.smith1960**, his idea is simpler using the external h/w to get the driver!
*********

Searching ubuntuforums I found: [http://ubuntuforums.org/showthread.php?t=1219931&highlight=unclaimed](http://ubuntuforums.org/showthread.php?t=1219931&highlight=unclaimed)

I think you must get wireless first from post#17 (updates kernel for Ubuntu Netbook Remix):
[http://ubuntuforums.org/showpost.php?p=7718408&postcount=17](http://ubuntuforums.org/showpost.php?p=7718408&postcount=17)

and then use wireless to update and 'look forward'! Think about posting there new questions as they all have the same hardware as you have.

Just for reference in my 1000H the **sudo lshw -c network** shows:
**RT2860 (RaLink)** for wireless and **L1e Gigabit Ethernet Adapter (Attansic Technology Corp.)** for ethernet.

Regards,
George

---

### Post by EmrysPen on 2009-08-03
RE: walt.smith1960
Thanks! Unfortunately, when I type that into the terminal, it gives me the following output:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-jaunty

I'm assuming that isn't right, correct?

RE: GeorgeVita
What does "UNCLAIMED" imply?
Also, what does that second part of what you said mean?
Thanks again!

---

### Post by GeorgeVita on 2009-08-03
Hi again, as I understand your WiFi chipset is not supported with the standard Ubuntu 9.04 distribution (kernel+drivers) and you must add/change some files as described in my link, or will be downloaded if you try the idea of **walt.smith1960**. He suggests to use an external USB WiFi interface that will work with the EeePC (I do not know which model) and as you have the internet connection you can update/upgrade to take the drivers from the 'backports'. You must have internet working in this case.

The idea from the link (in my previous post) is that you can copy a kernel image that supports this WiFi chipset (I have not tested) and then use the new kernel to 'make it work'.

I am sure that next version of Ubuntu (9.10) will have this WiFi chipset supported by default. So the 3rd idea is to try Ubuntu Karmic Koala (which is under development).

Regards,
George

---

### Post by EmrysPen on 2009-08-03
Ah okay, thanks.

If I change those files, do you think I will have to change them back once the new version comes out?

---

### Post by GeorgeVita on 2009-08-04
Hi **EmrysPen**,
there is always a possibility to 'loose' some 'trims' after an upgrade, so you have to 'keep track' on what you will do till the successful connection. As other users comment, newer kernel supports your WiFi card and also a driver exists.

Regards,
George

---

### Post by EmrysPen on 2009-08-05
It worked (the second link up that you posted)!!!!

Thank you so much! You've saved me from what could have turned into hours of frustration...I can't thank you enough!

---

### Post by walt.smith1960 on 2009-08-05
Hi

I'm glad to hear you were able to fix your problem. I don't know why the backports idea didn't work for you.  For others who may have the same problem and are wondering about USB adapters I've found 2 that work with Jaunty out of the box.


[LIST=1]
[*]Linksys WUSB 54G v.4
[*]TrendNet TEW-424UB H/W:3.1  I have an earlier TrendNet adapter same model H/W 2.1 which did **not** want to work so hardware versions matter here.
[/LIST]
I wish I could find the netbook version of Karmic in an .img instead of an .iso.  I know it's a work in progress but it looks like a nice release for the newer EeePCs.  I tried to install it as part of a multiboot system but GRUB seemed to not install properly and wouldn't boot. Rats!!

---

### Post by GeorgeVita on 2009-08-05
Hi **walt.smith1960**,

> **walt.smith1960 said:**
> ...I wish I could find the netbook version of Karmic in an .img instead of an .iso.  I know it's a work in progress but it looks like a nice release for the newer EeePCs.  I tried to install it as part of a multiboot system but GRUB seemed to not install properly and wouldn't boot. Rats!!

I am using Karmic fully installed to my EeePC via Live USB I created from System > Administration > USB Startup Disk creator

There you point to an .iso file and then you can "burn it" to a USB stick. Then the USB stick is bootable and if it is UNR it can be installed (I suppose) to the netbook. I am running also some SDHC installations (9.04, puppy 4.2.1, etc) to EeePC 1000H.

Regards,
George

---

### Post by mrwanlord on 2009-08-08
Hi

I have also the same problem ( i.e. 1005ha wifi not working).  I also tried 2nd solution [http://ubuntuforums.org/showpost.php?=7718408&postcount=17](http://ubuntuforums.org/showpost.php?=7718408&postcount=17)

and it worked.  But then Ubuntu updated it and now I am again with non working Wifi.  

I have tried to remove the later version (higer versions but no luck. )

Any word of advice please.

Kind regards

---

### Post by L2linux on 2009-08-09
Do do not need to remove the version you just installed. You need to redo the steps when ever you upgrade your system. Wired/wireless has to be reactivated if you upgrade, at least until you upgrade to 9.10. 

-Cheers.

---

### Post by GeorgeVita on 2009-08-11
> **mrwanlord said:**
> Hi
I have also the same problem ( i.e. 1005ha wifi not working).  I also tried 2nd solution [http://ubuntuforums.org/showpost.php?p=7718408&postcount=17](http://ubuntuforums.org/showpost.php?p=7718408&postcount=17)and it worked.  But then Ubuntu updated it and now I am again with non working Wifi.  
I have tried to remove the later version (higer versions but no luck. )
Any word of advice please.
Kind regards

Hi **mrwanlord**, as in above link a special kernel is used and probably the update installed a newer kernel, you can test booting the 'working' kernel by pressing ESC at the grub boot loader and choose it (up/down arrows).

Regards,
George

---

### Post by domsut on 2009-08-13
I had the same problem and got my wireless to work. but it sucks! I can't be more than 30 feet from my router. help

---

### Post by Sublex on 2009-08-19
So I've also followed the second link, and now I can see my wireless network.

When I try to connect, it tells me to put in a password.

My password is 6 digits, but I can only hit "Connect" when there are 5, 10 or 13 digits in the "Key" place.

Help?

---

### Post by CinemaFoto on 2009-09-20
Hello everybody!
Hopefully this post is not too old ... :)
I used [_[COLOR="Blue"]this[/COLOR]_]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/") tutorial (it is easiest end the most exact I've found) and my Asus eeePC 1005HA just works perfect!
Pay attention - in "Wired connection" section there is a phrase:
"*Until Ubuntu Karmic is released, every time you do a kernel update, you will need to re-run the last two steps (preceded by a sudo rmmod atl1e.ko).*"
Anyway, thanks a lot for the Writer of the Tutorial!

---

