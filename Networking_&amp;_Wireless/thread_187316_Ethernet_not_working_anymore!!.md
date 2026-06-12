---
title: "Ethernet not working anymore!!"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by antimatter on 2006-06-02
Hi!
Upgraded to dapper this morning and everything seemed to have worked fine. My 3com pcmcia card Model 3CCFE574BT worked under breezy, but now with dapper it was renamed from eth0 to eth1 and it also stopped working. i've tried ifdown eth1 ifup eth1 but that didnt work. it would just say, no dhcpoffers received. so i figured, hey you could try the old kernel, so i booted that one. ifup eth0(and not eth1)!! and voila, it worked. ideas anyone?

---

### Post by h3h_timo on 2006-06-02
Well, you could try this:

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

If it doesnt work, then i dont know what to tell you.  I know your ethernet card is different, but its basically the same problem, with the same symptoms.

---

### Post by bt224 on 2006-06-02
This seems to be the silver bullet to fix this issue. I was having the same problem and this worked beautifully.

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by antimatter on 2006-06-03
it doesnt work for me sadly. i'm, still having the same problem ](*,)

---

### Post by kdawgud on 2006-06-03
I'm not sure if this is the same problem or not, but on one of my desktop computers I installed dapper kubuntu.  The ethernet connection worked perfectly fine while on the live cd, but after I installed to harddrive, the ethernet connection no longer worked in KDE.  

I would run ifconfig to see what IP address it had, and it had a good one, but no pings would go through and any further attemps to run /sbin/dhclient were fruitless at renewing any IP address.  I did find out, however, that booting in 'single user' mode let me run the ethernet just fine.  But if I re-initialized to run-level 2 (without even rebooting), the ethernet card stopped working.

I tried to lsmod and find which module was responsible for my ethernet card (so maybe I could remove it and reinstall it), but I'm not really sure how to tell.  Also, I'm guessing there's a decent possibility that the ethernet driver is compiled in with the kernel and not a module (anyone want to comment on this)?

Any ideas would be appreciated...   I don't know what brand the ethernet card is (the computer is at work and I'm at home :) ), but I had Fedora Core 3 working on it just fine before - and I'm planning on bringing in a different NIC to try on Monday.

Thanks it advance!

Kyle

---

### Post by wud on 2006-06-03
I'm having a similar problem with my ethernet not working after dapper install. I'm using an old Averatec laptop (3250 series) with a Via VT-6102 [Rhine-II] (at least, that's what the device manager is telling me). I'm typing this from a re-installed breezy, which has always worked ethernet-wise. I tried the above suggested davicom fix but that didn't work.

Here's what I've managed to gather so far. When I upgrade to dapper (any flavor, and both clean installs and upgrades) the internet via ethernet will stop working unless I stay in recovery text-mode. I can revert to the old breezy kernel, and internet will work again if I enter gnome/kde, but boot up is riddled with error messages and I'd rather not have to do this.

I think the issue is with the ACPI. If I disable it, I can get online, but I'd rather not do this either. Is there anyway to disable ACPI just for the network card?

---

### Post by kdawgud on 2006-06-04
[QUOTE=wud]I'm having a similar problem with my ethernet not working after dapper install. I'm using an old Averatec laptop (3250 series) with a Via VT-6102 [Rhine-II] (at least, that's what the device manager is telling me). I'm typing this from a re-installed breezy, which has always worked ethernet-wise. I tried the above suggested davicom fix but that didn't work.

Here's what I've managed to gather so far. When I upgrade to dapper (any flavor, and both clean installs and upgrades) the internet via ethernet will stop working unless I stay in recovery text-mode. I can revert to the old breezy kernel, and internet will work again if I enter gnome/kde, but boot up is riddled with error messages and I'd rather not have to do this.

I think the issue is with the ACPI. If I disable it, I can get online, but I'd rather not do this either. Is there anyway to disable ACPI just for the network card?[/QUOTE]

How do you disable ACPI on the dapper kernel?  I think I would like to give that a try.

---

### Post by toganet on 2006-06-04
I'm having similar issues with the same model laptop (Averatec 3250).  Activating wireless causes the system to hang, as does "ifdown eth0 ; ifup eth0".

I will investigate further and report back if I come up with a fix.  I have to keep rebooting into XP to post here, so it's very time-consuming...

---

### Post by currios on 2006-06-04
i have the same problem with the Averatec 3250, everything was working right with brezzy and hoary but with Dapper my network is not working at all.

---

### Post by mozetti on 2006-06-04
I'm having the same problem with an SMC 2632W 802.11b card. It's an atmel chipset. Worked find in Breezy -- wasn't detected during Breezy installation, but it worked right away on my first boot up. Did the upgrade to Dapper from the update manager and it won't pick up anything.

---

### Post by wud on 2006-06-04
[QUOTE=kdawgud]How do you disable ACPI on the dapper kernel?  I think I would like to give that a try.[/QUOTE]

I'm not sure how to do it once dapper's installed to the hard drive (could probably edit the boot up services and stop it there, but I'm new to linux). But you can test it out with dapper's install cd. At the first screen, add "acpi=off" (no quotes) to the end of the boot command. If I got that command wrong, it's also in the help section for special boot up parameters (F3?). I'm typing this from dapper live without acpi.

The good news, at least for us Averatec users, is that it's listed as a critical bug and has been assigned already, so it should be fixed soon:
[https://launchpad.net/distros/ubuntu/+source/linux-image-2.6.15-23-386/+bug/48263](https://launchpad.net/distros/ubuntu/+source/linux-image-2.6.15-23-386/+bug/48263)

---

### Post by currios on 2006-06-04
But it says that the bug ist Rejected, does that mean they are not working on it anymore?

---

### Post by vince21 on 2006-06-04
I am having the same problem. My Ethernet Pcmcia Card worked perfectly with Breezy and since five years with Linux (differents Flavors). But now ifconfig shows only the "lo" interface and when I try to launch Ethernet with
#ifconfig eth0 up 192.168.1.97 I get the following error:
eth0: unknown interface: No such device
SIOSCIFADDR: No such device

I am very puzzled :-k , maybe it comes from the Kernel 2.6.15?

Thank you for your ideas, I have tried a lot but since now nothing works.

Vincent

---

### Post by currios on 2006-06-04
My ifconfig shows all device but, i can't connect to the internet or to any other computer.

---

### Post by wud on 2006-06-04
[QUOTE=currios]But it says that the bug ist Rejected, does that mean they are not working on it anymore?[/QUOTE]

Hmm, it wasn't rejected a little bit ago when I posted that. Odd. Guess it probably won't be fixed then :-/.

---

### Post by kdawgud on 2006-06-04
[QUOTE=currios]My ifconfig shows all device but, i can't connect to the internet or to any other computer.[/QUOTE]

Thats the same symptom I see too.  Mine even gets a valid IP address on bootup, but can't connect to anyone after someone logs in (except when booted in the special 'recovery mode', in which case it works fine).

---

### Post by wud on 2006-06-04
I'm not quite sure what happened, but my ethernet's working again. I had reinstalled Kubuntu breezy after dapper didn't work, but today I decided to dist-upgrade and try to compile a new kernel and see if that worked. But I'm in dapper now, fresh off the upgrade, and it's working!

edit: Okay, so my sound isn't working. And neither is direct rendering. And my wireless card isn't being recognized. Wow, that really mucked things up.

---

### Post by codyjack on 2006-06-05
I am not quite sure how this fixes the problem for the Averatecs, but this is what I did.  

After the Averatec splash screen and before Ubuntu starts to boot, there is a grub menu that you can get into by hitting 'esc'.  I chose the first option 'Ubuntu, kernal 2.6.15-23-386' and hit 'e' to edit.  Then I went to the second line 'kernel /boot/vmlinuz-2.6.15-23-386...' and hit 'e' to edit.  At the very end of the line I added 'irqpoll' (without the quotes)  so that the options now look like:

ro quiet splash irqpoll

This allowed my ethernet to start working again.  I need to figure out how to make this a permanent change and figure out why it works :D And then on to the wireless.

---

### Post by Aleksey1977 on 2006-06-05
[QUOTE=codyjack]
After the Averatec splash screen and before Ubuntu starts to boot, there is a grub menu that you can get into by hitting 'esc'.  I chose the first option 'Ubuntu, kernal 2.6.15-23-386' and hit 'e' to edit.  Then I went to the second line 'kernel /boot/vmlinuz-2.6.15-23-386...' and hit 'e' to edit.  At the very end of the line I added 'irqpoll' (without the quotes)  so that the options now look like:

ro quiet splash irqpoll

[/QUOTE]

Same thing worked for me as well (Averatec 3255, clean Dapper install), you're definitely onto something

---

### Post by codyjack on 2006-06-06
Alright, I am online and untethered.  My wireless is working again in Dapper.  After getting the ethernet working again (see above) I set off to get the wireless working (it's no fun to be tethered to this desk by a network cable).  

In Breezy I had followed the instructions of kalosaurusrex found [here]("http://ubuntuforums.org/showthread.php?t=25683&page=27") (with the exception that I used the ndiswrapper-utils that comes with Dapper instead of building from the source.  saves a few extra steps if you get it from the Package Manager).  

But that wasn't enough.  Even after rebooting the wireless didn't come up.  It turns out that [the new Broadcom drivers for linux]("http://bcm43xx.berlios.de/") are included with Dapper and that was causing problems.  

After reading [this]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDriver%2FBroadcom43xx#head-641f02d713cfad8d50253292a3672dc3fc89998e") I was able to blacklist the new Broadcom driver and continue using the ndiswrapper.  I may toy around with the new drivers later, but I needed to be back online and I knew the ndiswrapper worked in Breezy.

Hope this helps someone out there.

---

### Post by toganet on 2006-06-06
Adding "irqpoll" to the end of the boot parameters did the trick for me, to a point.

Networking does work now, at least through the wired interface.  Another improement is the fact that activating the wireless does not hang the system -- but it does not seem to work, either.  I am using the rt2500 module.

I'm going to test some more, and if anything works, I will post back here.:KS

---

### Post by rts on 2006-06-11
I'm in a similar situation.

My wired ethernet worked perfectly upon upgrading from Breezy to Dapper on my laptop, but my rt2500 stopped working.  Network-manager attempts to connect to my wireless hub, spins for a while, then just gives up.  This was working perfectly (modulo some crashing) in Breezy.

acpi=noirq did not help (as suggested here [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48263](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48263)) and irqpoll caused the bootup sequence to hang at "Starting Hardware Abstraction layer hald"...

---

### Post by AndrewH on 2006-07-06
Hi all,

I'm new to Ubuntu and have been monitoring this and other threads relating to RA2500/Rhine system freezes under Ubuntu 6.06 on my Averatec 3250 laptop for a few weeks now.

I have all the symptoms already mentioned here and have tried all the fixes apart from 'irqpoll' which I am about to test!

I have to say I am a little surprised that there has been no apparent resolution of this problem by now from the Ubuntu team. 

Has anyone found a complete fix for this yet?

---

### Post by FamuLinux on 2006-07-29
The 'irqpoll' trick does work (averatec 3250HX-01)!

To make the change permanent simply go to [/boot/grub/menu.lst] and scroll down until you find the entry the corresponds to the one you changed at the Grub bootloader screen (it will look exactly like it). At the end of the line, add 'irqpoll' and save the file, making sure not to change anything else. When you reboot, network configuration will work like it should.

*I spent three days working on this issue, that could have been devoted to research towards my Master's thesis.

---

