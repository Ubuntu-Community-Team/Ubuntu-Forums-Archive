---
title: "Wake-on-LAN worked 3 times then no more"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by DavidBanner on 2012-05-15
[COLOR=Purple]Update: My main theories for now are (see below for details):[/COLOR]
[COLOR=Purple][B]* Ubuntu system shuts down NIC power in standby mode?
* Realtek RTL8111 driver for 64-bit machines does not work?[/B][/COLOR]
[COLOR=Purple]Can anyone confirm or deny?[/COLOR]

- - - - -

I installed Ubuntu 12.04 a few days ago and got Wake-on-lan to work by sending Magic Packets from a different PC after having put the Ubuntu machine in standby via the desktop menu. I did this 3 times and it worked beautifully. Then suddenly it didn't work anymore! How on earth can this be possible?!

I know potentially 1000 things can be wrong when WOL doesn't work but the fact it worked 3 consecutive times rules out most of them. It worked 3 times (a few minutes apart) and after that has never worked. During the 3 times it worked and the followingh 10 unsuccessful tries the only thing I fiddled with was the firewall on the PC that sends the magic packets, and I soon switched the firewall off to eliminate that potential problem, and also verified the packets come through with wireshark (with the Ubuntu machine on then of course). I made a full update of Ubuntu a few hours before the tests started.

[SIZE=1][COLOR=Gray]Some facts and tests I've done (in-depth info, you should only have to read the black text to understand my problem):
[/COLOR][/SIZE]
[LIST]
[*][SIZE=1][COLOR=Gray]I tried adding "pci=noacpi", "pci=noapic", "acpi=force" and "apm=on apm=power-off" to /etc/default/grub (and I verified the changes in grab.cfg). One at a time of course (reboot after each).
[/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]I saw the NIC was disabled in cat /proc/acpi/wakeup, enabled it with command "echo -n LAN | sudo tee /proc/acpi/wakeup" and now LAN was enabled in the list[/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]Firewalls are disabled[/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]ethtool shows wol is in state "g" (I tried setting it to "pumbag", and also to "d" then "g"). [/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]It is an ASUS board with Realtek RTL1111/R8168B (driver R8169 came with the kernel and it was with that driver is worked 3 times; lately I changed to driver R8168 which wasn't easy but I can't see any difference and people seem to report R8169 should be used for all nowadays). [/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray] I also tried using wireshark on the Ubuntu machine to verify the magic packets got through to the PC[/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]Tried resetting CMOS RAM (both by jumper and removing battery for 5 minutes). [/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]NIC LED is not lit when in sleep but it's also not lit on my other PC when in sleep and WOL works for that PC. [/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]I tried enabling "Wake on when hit PS/2 spacebar" in BIOS, started Ubuntu, selected "Standby" from menu so that it got into standby, pressed spacebar, and it started. Also worked after Terminal command pm-suspend and halt -p (shuts down and reboots completely though) but does not wake after command halt. [/COLOR][/SIZE][SIZE=1][COLOR=Gray]Halt makes the OS shut down but the HW to remain on. Still ignoring WOL in all cases. [/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]When in standby the power LED blinks, fans and hard disk are silent, and this remains the same after WOL attempts[/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]Program used for sending magic packets is: [http://magicpacket.free.fr/](http://magicpacket.free.fr/) on a different (Windows) PC[/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]Settings for Magic Packet sender is UDP port 80 subnet mask 255.255.255.255 and that's the settings it worked with but I also tried ports 9, 7 and 0, TCp and mask 0.0.0.0. Have double checked MAC address but I entered it via copy-and-paste and it has worked with these settings 3 times as I mentioned.[/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]I have only used Ubuntu for a week (have some brief experience with Linux and Unix systems from long ago)[/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]I haven't added "ethtool -s eth0 wol g" (or "echo -n LAN | sudo tee /proc/acpi/wakeup") to startup scripts since I believe WOL should work ONCE if these things are set properly (script are needed to make it work after each reboot)[/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]The motherboard Asus AT5NM10T-I has no BIOS updates (is v0306)[/COLOR][/SIZE]
[*][SIZE=1][COLOR=Gray]Tried most things on these pages: 
[http://wiki.ubuntuusers.de/Wake_on_LAN](http://wiki.ubuntuusers.de/Wake_on_LAN)
[http://en.gentoo-wiki.com/wiki/ACPI/Fix_common_problems#Nothing_Works](http://en.gentoo-wiki.com/wiki/ACPI/Fix_common_problems#Nothing_Works)
[http://wiki.xbmc.org/index.php?title=HOW-TO:Enable_Wake-On-Device_for_Ubuntu](http://wiki.xbmc.org/index.php?title=HOW-TO:Enable_Wake-On-Device_for_Ubuntu)[/COLOR][/SIZE]
[/LIST]
Most of the time I feel like I'm just testing various things blindly. Is there for example any way to check that power isn't shut down for the NIC? And doesn't the "cat /proc/acpi/wakeup" being "disabled" mean something's wrong? 

There's lots of threads on WOL, I know, but none where it works perfectly for 10 minutes then stops working for no reason. A few threads mention problems with WOL after 12.04 was installed. My only remaining idea right now is to install Ubuntu 10. But that would just be a test, not a permanent solution, and a very time consuming test. And I'm sure RTL8111/RTL8168 isn't properly supported on older Ubuntus (there have been major problems with those NICs with older Ubuntus) which complicates such a test even more.

:confused:

---

### Post by markbl on 2012-05-15
I'll admit I have not read the detail of what you have tried above but my PC requires 2 things for WOL to work:

1. I have to set the relevant BIOS option. Just try a few settings that look appropriate.

2. I need a "ethtool -s eth0 wol g" added to the end of /etc/rc.local.

With this I can wake my pc from suspend, but also from a full poweroff shutdown (where only the network card remains with power).

---

### Post by DavidBanner on 2012-05-15
Thanks but since it did work for 3 times it must be something else, right? 

I know what to look for in the BIOS but forgot to mention it here: "Wake on LAN", "Power on by PCI" or "Power on by PME", and since it is an ASUS board, it is "Power on by PME" (PCI Power Management Events). I also enabled "Power on by Ring" since someone suggested that in a forum but I can't believe it affects WOL but also can't hurt. 

I think you can skip the grey text in my post and read only the black text, which covers the essential parts. The grey text is mainly there to show all things I tested (and my level of devastation.. :cry:).

Are you using Ubuntu 12.04?

---

### Post by markbl on 2012-05-15
> **DavidBanner said:**
> Thanks but since it did work for 3 times it must be something else, right? 


Presumably you have been playing around with different bios and linux commands and settings and thus may have not exactly recorded the particular incantation which was successful. :(
> 
Are you using Ubuntu 12.04?
Yes, clean install of 12.04. I have been using WOL for at least a couple of years on this PC and have clean installed every new ubuntu release in that time (i.e. probably at least 10.10, 11.04, 11.10, and 12.04). I have been adding that ethtool line to the end of my /etc/rc.local every time. That is all I have been doing for it to work, plus originally set my bios. I also have an ASUS motherboard and I had to set "Enable PCI" and "Enable PCIE" to auto power on under the APM settings page. I needed *both* of those settings enabled, they both default to disabled. This is  for the onboard gigabit LAN adaptor.

---

### Post by DavidBanner on 2012-05-15
> Presumably you have been playing around with different bios and linux commands and settings and thus may have not exactly recorded the particular incantation which was successful.Nope. As I said: *"During the 3 times it worked and the followingh 10 unsuccessful tries  the only thing I fiddled with was the firewall on the PC that sends the  magic packets"*. That's why this deserves its own thread. I did a lot of fiddling AFTER that but never got it to work again. And I kept track of every detail of my fiddling. I am a very structured fiddler. ;)

Good to know it works for someone with Ubuntu 12.04 at least. 

This NIC has been a lot of trouble for Linux users until recently. Do you also have RTL8111 (8168B) with the 8169 driver? One of the most common NICs I think.

---

### Post by DavidBanner on 2012-05-17
I actually tried reinstalling Ubuntu 12.04, and again it worked 3 times then after that is dead. (Actually this time it worked 1 time, then didn't work, then worked 2 times in a row, then never again.)

Some details which probably have no significance: It didn't work until I enabled Samba properly for file sharing between PCs in a workgroup. The 3 times it worked I did not have to send sudo ethtool -s eth0 wol g (sudo ethtool eth0 always reports it is in wol mode "g" so apparently my NIC starts in that mode). And sudo cat /proc/acpi/wakeup now always shows LAN as "enabled" now. This time I used the downloaded 12.04 without updates (Ubuntu's desktop said there were no updates), later (long after it stopped working) it said there were 136 updates, I installed them and rebnooted, still didn't work.

I also found 2 persons with the issue that WOL stopped working when Ubuntu 12.04 was installed: [http://askubuntu.com/questions/134841/replace-realtek-r8168-network-card-to-enable-wake-on-lan](http://askubuntu.com/questions/134841/replace-realtek-r8168-network-card-to-enable-wake-on-lan)

He uses the same NIC as me. Next logical step pfor me would be to install an older version of Ubuntu, if I find the time.

---

### Post by DavidBanner on 2012-05-18
Update:

[LIST]
[*]I tested with Ubuntu 11.10. It has the same problems, or a version of it: WOL seems to work about 1 out of 4 times. Doesn't suddenly stop working, just doesn't work every time (far from it).
[*]* Tested with Windows 7. Installed Realtek driver. Ticked "allow only magic packet to wake up" in NIC settings (HW manager) and it worked flawlessly, tested 5 times in a row. Note: First I didn't bother to install video and audio drivers and then only hibernation worked, but it did respond to WOL calls flawlessly. Installed video and audio driver plus "PC Probe II" which seems to have something to do with ACPI driver. Did this after I read in [Wikipedia on ACPI]("http://en.wikipedia.org/wiki/Sleep_mode#ACPI") that Windows might not allow standby (S3) if one device in the system doesn't support acpi.
[*]When in sleep mode (or hibernation) in Windows, I can still see this unit in the router's list of attached devices (but the LED on the NIC is out). (As I said before, for a different PC, it is not seen in this list even though WOL works, so apparently this isn't always the case). For this PC, however, it might indicate that the NIC hasn't any power, i e that the problem here is that Ubuntu shuts down the NICs power.
[*]I forgot to mention my machines are all 64 bit. It is not so uncommon that 32 bit drivers work while 64 bit drivers don't. So one suspicion is that the 64 bit Realtek driver still doesn't work properly on Linux with RTL8111 etc - I know there's been problems with these NICs for years which I read were solved rather recently, but can anyone confirm they have RTL8111/RTL8168&RTL8168B etc working with WOL on a 64 bit machine?
[/LIST]

So my main theories for now are:
[COLOR=Purple][B]* Ubuntu system shuts down NIC power in standby mode?
* Realtek driver for 64-bit machines does not work?[/B][/COLOR]

Where do you submit a bug report anyway?

---

### Post by DavidBanner on 2012-05-24
I give up. Have also tested with Fedora, OpenSUSE, Debian and Ubuntu 11.10 (didn't think it would help). After that tested on a different motherboard (Asrock 64-bit) bit with the same NIC. 

BTW, NIC is RTL8111E on both boards, even though Ubuntu reports it to be RTL8111/RTL8168B or if it was RTL8111B/RTL8168B. So perhaps it is the RTL8111E (64-bit) that is unsupported in Linux.

---

### Post by akastrin on 2012-06-01
Hi,

Any progress on this issue? I have quite a similar problem since I upgrade to 12.04. WoL works within a few hours, but  "crash" after a long shutdown (i.e., over night).

Any suggestions would be greatly appreciated.

Best, Andrej

---

### Post by Jerblue on 2012-06-26
Having a similar issue in Gentoo. Booting with acpi=off allows WOL to function properly, but inherently makes suspend stop working. 

...can't seem to have the cake and eat it to :popcorn:

---

