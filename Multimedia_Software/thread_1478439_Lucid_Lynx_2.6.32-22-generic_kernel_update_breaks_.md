---
title: "Lucid Lynx 2.6.32-22-generic kernel update breaks nVidia jockey recommended driver"
date: 2010-05-09
forum: Multimedia Software
---

### Post by Icarus315 on 2010-05-09
What I've found so far is this thread: [here]("http://ubuntuforums.org/showthread.php?t=1473902") but it is in installation and updates while I know it is a video problem so I'm posting in this subforum.  Here is what happened: today went over to my parents place and applied the pending updates from the last week.  One of them was the 2.6.32-22-generic kernel.  I watched the terminal output as the update manager installed everything and there were no errors at all.  On reboot the nVidia kernel module load failure message popped up when X started and I was given the option to start in a low-graphics mode.  So I did and went into jockey and removed the driver then reactivated it and rebooted.  It did not fix the kernel module failing to load.

So then I did something stupid.  I removed the recommended nVidia driver again in jockey and installed the latest driver from nVidia's website.  While installing this driver it said that the pre-installation scripts failed and asked me if I would like to install the driver anyway.  Stupidly I said yes.  On reboot everything appears to be normal until X starts and then the monitor enters power-saving mode.

The graphics hardware is an integrated nVidia 6150.  I've had all sorts of issues installing Lucid with it mostly ending up with specifying the "nomodeset" boot option to prevent the monitor from entering power-saving mode.  I forgot to try "nomodeset" with the computer and that latest driver before I left: that may get it to boot.

I'm asking for help here and I'm going back to my parents tomorrow to try and rescue the system.  What are the instructions to completely remove the downloaded nVidia driver?  I know for Ati it is "/usr/share/ati/fglrx-uninstall.sh" - I'm looking for the nVidia equivalent.  Please suggest anything at all that I can try as before I go back over to my parents tomorrow.  I'm going to print this page out and take it with me and hope something sticks.  Without a graphical mode it is very difficult for me to troubleshoot because I don't have access to here and I'm not a guru.

---

### Post by xjmg on 2010-05-09
Hi, I was having the same problem... but after reading a lot and a little imagination I fix it. What I did was using the Synaptic Package Manager uninstall everything that had to do with nvidia, even the "Hardware Drivers" tool (jockey-gtk) and reboot... then I re-install all the Nvidia thing I removed and the "jockey-gtk". Then activate the current Nvidia driver, reboot again.. (a little prayer in the middle) and done. This is the exact way I did it and it work. I hope this helps you.

---

### Post by Icarus315 on 2010-05-09
Thank you for the reply.  Anyone have any tips on how to and what can go wrong when uninstalling the nVidia downloaded driver from the recovery command line?  Hopefully once I am able to uninstall that mistake then I can get to low-graphics mode and then getting to Synaptic to find the nVidia packages.

---

### Post by Icarus315 on 2010-05-10
One bump a day allowed.  Anyone have any other suggestions or links to guides I can use when I go to my parents later today?

---

### Post by drdos2006 on 2010-05-10
Have a look in /var/log/syslog, seach for nvidia. In my case I had to go into BIOS and switch on 1 meg memory after turning on nvidia drivers. Also I have this in my syslog.

May 11 06:05:51 c2d-geoff-pc kernel: [  143.145437] nvidia: module license 'NVIDIA' taints kernel.
May 11 06:05:51 c2d-geoff-pc kernel: [  143.145442] Disabling lock debugging due to kernel taint
May 11 06:05:52 c2d-geoff-pc kernel: [  143.399945] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 11 06:05:52 c2d-geoff-pc kernel: [  143.399952] nvidia 0000:01:00.0: setting latency timer to 64
May 11 06:05:52 c2d-geoff-pc kernel: [  143.400167] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  
 As to the kernel being tainted, my original installation of Ubuntu 9.10 64bit could not find my AGP bridge. My solution is to just uninstall all nvidia drivers and ubuntu looks after the video which I am doing at the moment. Gigabyte motherboard, 6 gig RAM.
good luck.

---

### Post by doughoist on 2010-05-13
I for one am very upset that Ubuntu 10.04 LTS has this much trouble with graphics period. Why in the hell would cononical break my system where I have to jump through so many hoops to get a working system back. They should be ashamed of them selves. 
I have been really pushing Ubuntu on my friends an family and I hope to God they do not upgrade of clean install to 10.04 as this really sucks!

I have tried every tutorial on the net to work around this issue but it is rediculous that I should have to. WH did they choose to break somethong that was working just fine before?

I am goin to install XP on my machine now and dispite the 4 hour install with update, I'll have a working sytem quicker than scewing around with this lucid garbage any longer.

I am very upset if you can't tell. There is no sense in these types of problem courtesy of Cononical.

---

### Post by Icarus315 on 2010-06-19
Solved this issue by reinstalling Windows on that one machine.  I've never had issues with my Ati machine upgrading the kernel so mental note, buy Ati for future machines.

---

### Post by Stainesy on 2010-06-19
Instead of spitting the dummy you could have just booted from the previous kernel without drama and boo hoo, and waited for a fix.

---

### Post by Inoki on 2010-06-20
What I did was I went into low graphics mode, uninstalled the driver,  re-booted, re-installed the driver, re-booted and it worked perfectly.

Prior to that I went into Synaptic Manager and installed everything corresponding to my driver version, or at least a few essentials.

I don't know if it works similar to Windows, but the old trick of re-booting after doing something always works, as it safely removes used files so after the boot you're able to use them again, i.e. if you want to install or re-install something, always be sure to re-boot.

Since the driver you used to use used to work, it should work again  after you re-install it. It's also the recommended driver so it should  work.

---

### Post by Icarus315 on 2010-06-22
> **Stainesy said:**
> Instead of spitting the dummy you could have just booted from the previous kernel without drama and boo hoo, and waited for a fix.

That was also non-functional.  As well, this computer is at my parents house and they are non-technical.  To the point where they would resent having to choose a particular kernel in the GRUB menu.  My computer, different, is Ubuntu.  Someday hardware and software incompatibilities will be ironed and we won't need discussions like this.  Boo-hoo indeed, a factual statement of what was done does not need your kind of interpretation in my humble opinion.

---

