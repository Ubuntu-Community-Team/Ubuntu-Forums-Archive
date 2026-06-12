---
title: "Xorg CPU usage goes to 100% - Feisty + NVidia"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by steelpagoda on 2007-04-24
Hello all,

I have had a completely stable Edgy install, with no issues running Nvidia proprietary drivers and Beryl.  I upgraded to Feisty and also had no issues.  Within the past two days, my desktop will apparently freeze after a random amount of time (measured in a few minutes.) The hardware cursor is still working, but otherwise the session is unresponsive.

Ctrl-Alt=Backspace does not kill the X Session.

I can ssh into the machine from another.  If I do and run top, I see Xorg has 100% of the CPU.

This happens regardless of the window manager I use (metacity, compiz or beryl.)  I've also tried all available versions of the Nvidia driver, invcluding the Beta version, to no avail.

Interestingly, I switched to Ubuntu from Fedora Core after my stable install suddenly went bad after an update. I'm wondering if there's a bug in a recently updated Ubuntu library?

My system's an AMD 64 X2 4200+ w/a GeForce 6600 and 1.5GB ram.

Anyone else seeing something similar?

---

### Post by Shmifty on 2007-04-24
I am having the same problem, although I mostly notice when I have my screensaver enabled.

---

### Post by rmachan on 2007-04-29
I am having the same problem.  I'm using the nv driver and no screen saver except that I have
the monitor go to sleep after 20 minutes.  When I wake the monitor up I see 100% cpu usage.

It does not happen every time but does frequently.

Bob

---

### Post by Slade Winstone on 2007-04-30
Hi,

I'm running an Asus Laptop A8M, Feisty + Nvidia.

I find that when I shut the lid on my laptop, and the screen locks, sometimes when I unlock the screen I find the CPU runs at 100%.  It seems to step back to 2% for 30 seconds every couple of minutes and then back up to 100% again.  

I've tried killing firefox, but the CPU usage remains the same.

Very strange... :confused: 

Slade.

---

### Post by tfx on 2007-04-30
i have the same prolem with feisty here...

---

### Post by LKRaider on 2007-05-01
That's a nvidia driver + xorg bug.
If you try dmesg you'll probably see some Xid errors from the nvidia driver.

There are many bugreports about this, but I'm affraid only nvidia themselves can fix this (proprietary drivers and such, you know).

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109453](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109453)

---

### Post by Slade Winstone on 2007-05-04
LKRaider, thanks for the heads up... sigh no desktop effects for a while then :(

---

### Post by boralyl on 2007-05-13
I actually have this same issue with Feisty and Xorg, however I'm using ATI drivers for my video card.  Like others had said, not every time, but usually after returning from a screensaver Xorg is using over 90% of the CPU.

---

### Post by unconcrete on 2007-05-19
> **steelpagoda said:**
> Hello all,

I have had a completely stable Edgy install, with no issues running Nvidia proprietary drivers and Beryl.  I upgraded to Feisty and also had no issues.  Within the past two days, my desktop will apparently freeze after a random amount of time (measured in a few minutes.) The hardware cursor is still working, but otherwise the session is unresponsive.

Ctrl-Alt=Backspace does not kill the X Session.

I can ssh into the machine from another.  If I do and run top, I see Xorg has 100% of the CPU.

This happens regardless of the window manager I use (metacity, compiz or beryl.)  I've also tried all available versions of the Nvidia driver, invcluding the Beta version, to no avail.

Interestingly, I switched to Ubuntu from Fedora Core after my stable install suddenly went bad after an update. I'm wondering if there's a bug in a recently updated Ubuntu library?

My system's an AMD 64 X2 4200+ w/a GeForce 6600 and 1.5GB ram.

Anyone else seeing something similar?

Yes, I have too that problem. 
I have a HP Pavilion computer with NVIDIA FX5500 video card. I have also succesfully installed Compiz and AIglx in a Edgy Eft computer.  My driver is NVIDIA-Linux-x86-1.0-9746-pkg1.run. 
At first the computer performed well, but since about a month I have serious serious serious problems: after a few minutes my CPU run out 100% and I am forced to reboot my system. Current downloads ad works have been lost.
Thus I've left system monitor opened at startup in order to know what caused my problem. In the processes list is displayed the following item:
...
sh
-----run-parts
       ----------------------apt
                 --------------------------------unattended-upgr 89-100% CPU - user= root
The rest is kept by Xorg 15-20% CPU.

I kill the unknown process and all seems ok again but I don't understand what is the cause of the unattended upgrade. System Monitor can show me the memory space used but I don't know how to see the unattended-upgr source. I'd like to have control over that damned process.
I'm sorry for the lack of information but I don't know how to obtain it. 
Any help?
:confused:
Unconcrete

---

### Post by Chaoticwhizz on 2007-05-20
> **rmachan said:**
> I am having the same problem.  I'm using the nv driver and no screen saver except that I have
the monitor go to sleep after 20 minutes.  When I wake the monitor up I see 100% cpu usage.

It does not happen every time but does frequently.

Bob

I am having this same problem with Similiar system. Im on Fiesty with an Nvidia 6200 card This problem only started happening when I upgraded to Fiesty. At the same time I had to upgrade my Nvidia driver to the 9755 driver since that was the only way I coudl be the Fiesty GUI to come up. This only happens when I come out of monitor sleep mode. I will turn off teh monitor power saving features to see if it stops.

---

### Post by unconcrete on 2007-05-22
Hi all, after I've run system monitor I've seen that muy prob arises not only in NV drivers and Xorg (15-30%CPU) but from an unidentified upgrade process called unattended-upgr (89-99%CPU). I don't  know if ùnvidia bugs are included. The only way to submit my crazy computer is to kill that process. I know it's a newbie prob, but I'd like to know how to check what processes are automatically upgrading my system in a so ugly way.
Thanks in advance,
unconcrete

---

### Post by dannyboy79 on 2007-05-22
i'd like to know this as well. It appears as though we may be getting somewhere with this stupid freezing bug. so you're saying that if my screen freezes, but I can move my mouse (i have a GeForce 6200 128mb), that if I exit to the terminal (ctrl-alt-F1), I should be able to issue, "ps aux" and find the pid of the unattended upgrade process and kill it, and then be able to go back to the desktop, (ctrl-alt-F7) and it shouldn't be frozen anymore? I sure hope this works as at least then we can examining why this is occuring because as it stands now, no one has any idea why this is occuring yet there are many many threads started with similar results. (simple tasks freeze like gedit, then have to force quit, then panels freeze after selecting the "show desktop icon", then FF freezes BUT mouse still works, some their keyboards don't work but mine does, then the only way to solve is either quit gdm and restart it or restart entire machine. This is horrible!!!! I mean this is happening to me using the nv as well as the nvidia 9755 and the beta nvidia 100.xx.xx drivers so I don't have much of a choice here. I wonder how bad vesa would be. Hell, if it happens with vesa, than we can almost certainly rule out a nvidia issue and lean more towards this unattended upgrade thingy. Hope it's that easy!!

---

### Post by unconcrete on 2007-05-24
I'm going on monitoring my system. This time the computer freezes with a dramatic attack on CPU because of PID4722. The process concerns a program callled ANACRON that I ignore the role. The sequence is similar:
SYstem Monitor:
....Processes:
anacron (pid4277) >sh(pid 5461)>run parts (pid 5462)>apt (pid 5473)>unattended-upgr( pid 5488 )> http(pid 5732)
Now I'll searh a documentation about anacron since I'd prefer to avoid uninstall an important component of Ubuntu 6.10.
I've seen a new behaviour too: after 10 minutes anacron performs the same pids and sub-pids but the CPU% spending decreases to 46%. What do you think about?

unconcrete

---

### Post by dannyboy79 on 2007-05-24
I can tell you that Anacron is NOT critical what so ever to Ubuntu. All anacron is is basically a failsafe for cron jobs. It's good to have anacron on any computer that you know is not on 24/7 365. so what it  does is basically keeps track of when cron jobs are suppose to be run and if the computer was off when the job was suppose to run, it will be run the next time the computer gets turned on. unless you have 100's of cron jobs that were suppose to run when your computer was off. I can't imagine that anacron would make your cpu go nuts but then again I am not in front of the machine as you are.

None the less, I just bought a new PCI-E video Card, XFX GeForce 6600 GT OC 128 GDDR3 for $29.99 after $50 rebate and 2gb of DDR2 PC6400 800mhz for $89.99 after 40 rebate so maybe that'll fix it.

---

### Post by unconcrete on 2007-05-25
**This post could be related to an Ubuntu bug filed at**: modem hang up exit code=16 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				:(
Do you know something aganist unwanted upgrades? If not, can you gimve me a suggestion about information gathering in Ubuntu 610?

Thanks
unconcrete

---

### Post by dannyboy79 on 2007-05-25
> **unconcrete said:**
> **This post could be related to an Ubuntu bug filed at**: modem hang up exit code=16 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				:(
Do you know something aganist unwanted upgrades? If not, can you gimve me a suggestion about information gathering in Ubuntu 610?

Thanks
unconcrete
I wish I could help but I can't understand your sentence. As far as "information gathering", well what kind. If you want to know what kind of hardware your computer has you can use this command to see the pci bus's
lspci -v
and if you want to know what kind of hard drives, that would be
sudo hdparm -I /dev/hdX 
NOTE: hdX, the X is whatever drive you want info on (ide channel 0 master is hda, ide channel 0 slave would be hdb and so on and so forth)

If you want to gether info about the system and processes and what's going on in the background, check out the log files located within /var/log/.

As far as the unattended-upgrades being the issue of why our machines are freezing, that's NOT my problem. I must have a different bug. I created a new thread here: [http://ubuntuforums.org/showthread.php?t=454394](http://ubuntuforums.org/showthread.php?t=454394)

---

### Post by dannyboy79 on 2007-05-25
i thought originally a problem with the nvidia modules was causing a bunch of freezing of misc apps on my computer when opened with gksudo or gksu BUT
UPDATE FROM ME.
I am happy to inform everyone that a fresh install of Fiesty (no other hardware changes) has fixed the issue of the frozen commands when using gksu or gksudo which would eventually bring gnome-session and or X-server and or gnome-panel to it's knees. Meaning I could only exit to a tty or ssh into the box to restart it. So it obviously had something to do with something I installed along the way. Apps include pretty much everything in Automatix2, rkhunter, chkrootkit, tripwire, Exim4 and then sendmail, samba as a local master browser, and ssh. I can't think of much else I installed. Obviously the nvidia from the restricted modules manager, then the 100.xx.xx which both had this freeze. Then the freeze even occured in nv and vesa so who knows what the cause of it was I am just glad it's gone and I'll be sure to check it before and after every single I install!!!

There are 2 errors I am getting now that I am not applying any boot options like noapic or nolapic, they are:

[    2.937741] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node df85989c), AE_BAD_HEADER
[    2.937854] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PDC] (Node df8597fc), AE_BAD_HEADER

We'll see how it goes from here.

---

### Post by unconcrete on 2007-06-02
I have an AMD Athlon 3700+ processor + Geforce FX 5500  in a HP Pavilion computer I bought more than a year ago. My Ubuntu distro is very slow now, and I'm worried about installing a more powerful release.  Moreover, I've faced a little hell in my effort to install new NV drivers for Compiz and Aiglx for a better desktop. I know it's a simple business for you, not for me. I hope that a workaround esists for Edgy. Meanwhile I'm downloading the NVIDIA-Linux-x86-1.0-9755-pkg1.run in order to replace my older NVIDIA-Linux-x86-1.0-9746-pkg1.run. Do you think it can solve my nv problem (unattended-upgr)?
Sincerely,
unconcrete

---

### Post by dannyboy79 on 2007-06-04
so you're saying that you're using Edgy still and when using the NV drivers for Compiz and Aiglx  your comp is really slow? Oh course it's going to be, the NV driver is NOT the 9746 driver, it's a totally FREE driver that was reverse engineered from some1 who doesn't even work at nvidia I don't believe. If you want direct rendering and good graphics, you need to use a Proprietary Nvidia driver. Your card is supported by the 9755 I believe, so, yes, use that one. Also, you'll need to possibly blacklist the "nv" driver so that it uses the 9755 driver. Please show me the output of theses commands after you boot up with your current setup (current setup means whatever you had or have BEFORE you do the 9755 upgrade)

dmesg | grep NVIDIA

cat /etc/X11/xorg.conf | grep Driver

cat /etc/default/linux-restricted-modules-common

If you show me the results of those 3 commands I can maybe help.

---

### Post by itismike on 2008-02-07
Just from watching the output from 'top' after starting my system for the first time in several months, I'm pretty sure that 'unattended-upgr' is the automatic upgrade manager doing it's business in the background.  As soon as my CPU cycles freed up, unattended-upgr disappeared, and the icons for 'System Restart Required' and 'There are 27 updates available' appeared.

I have updates [System | Admin | Software Sources | Updates tab] set to: 'Install security updates without confirmation', so this is expected behavior.

---

### Post by narcisgarcia on 2008-04-12
In the thread:
[http://ubuntuforums.org/showthread.php?t=124450](http://ubuntuforums.org/showthread.php?t=124450)
somebody says "*It's update notifier - kill it and CPU will drop down. It's been reported as a bug already in Malone.*"

BUT:
I've instaled an Ubuntu GNU/Linux 7.10 (Gutsy) in a computer (CPU AMD3200, RAM1.5GB, MB Asus K8V) with a VGA "NVIDIA GeForce FX5500", and when applied the NVidia's driver downloaded and compiled on March 2008, I've found the same problem.

I've tried to disable the "update-notifier" service, but the problem persists. And sometimes the Xorg process colapses CPU when not logged yet in a Gnome session. I've tried to execute "/etc/init.d/gdm stop" with a terminal, but the logon screen remains active, and Xorg process doesn't die. With "killall Xorg" I've never got any result.

In my case, when a CPU/Xorg colapse situation occurs, I execute "sudo reboot" from a terminal but this problem reproduces again and again on each system session during some time (half an hour..?). **Can be this symptom of a hardware issue?**]

---

