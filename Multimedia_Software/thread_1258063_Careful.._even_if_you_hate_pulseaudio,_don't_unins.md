---
title: "Careful.. even if you hate pulseaudio, don't uninstall it"
date: 2009-09-04
forum: Multimedia Software
---

### Post by LeFou on 2009-09-04
In the course of fourteen different attempts to capture sound into a file, I noticed a great many posts saying "removing pulseaudio fixed a lot of my sound problems" so I did that (sudo apt-get purge pulseaudio). And rebooted.

And my wireless card stopped working. and the volume controller started failing, saying "No volume control GStreamer plugins and/or devices found"

So I reinstalled pulseaudio. I didn't realize that the whole Internet was a baby I'd be throwing out with the pulseaudio bathwater.

And I rebooted.

No improvement. Wireless does not work, and volume control still gives the no-plugins/devices message.

Machine is a Dell Mini 13 running Hardy.

---

### Post by jrings on 2009-09-04
Did you pay attention what else was uninstalled? When I try the command, I get the suggestion to also uninstall ubuntu-desktop. That sound serious...did you try reinstalling ubuntu-desktop?

---

### Post by LeFou on 2009-09-04
You caught me: I didn't really look it over b/c I was getting impatient. I have just reinstalled "ubuntu-desktop" (you're right that sounds like it might be important) and rebooted, with no improvement.

I also went into System->Administration->Drivers and enabled the proprietary driver for the Broadcom STA wireless. Rebooted again.
Now that driver is "Enabled" but "Not in use"

---

### Post by LeFou on 2009-09-04
Went from bad to worse, I'm afraid.
I found a thread dealing with the "no gstreamer plugins or soundcard not configured" issue, and it had some instructions about boot options in menu.lst and module-assistant commands to reload alsa's module, which I followed.

Sorry I can't link the exact thread, but the computer won't boot now. It goes to the ubuntu splash screen, makes progress across its little bar for a bit then says "Saving VESA state" and "cat */id no such file or directory" and a couple other things. Then the screen goes black and nothing else happens.

So.. is there a way to do interactive startup or anything like that? The Inspiron mini has no optical drive, so i can't boot from a disc...

---

### Post by Yellow Pasque on 2009-09-04
'ubuntu-desktop' is just a meta-package that depends on all of the packages in a default Ubuntu install. Removing it won't actually remove any packages and it is necessary to remove the meta-package if you want to remove one of the default Ubuntu packages (such as pulseaudio).

As for your issue, try booting without the splash screen (remove the 'splash' keyword from the boot line)

---

### Post by gwenn on 2009-09-04
Try to make a linux stick somewhere if is possible or find a connector cdrom -usb

---

### Post by LeFou on 2009-09-04
> **Temüjin said:**
> As for your issue, try booting without the splash screen (remove the 'splash' keyword from the boot line)

I cannot edit menu.lst (unless you can think of some way...) because the thing won't boot. I need to interrupt startup and drop to a grub prompt if possible

On my Fedora machines, grub presents the menu and I hit "c" to get the prompt.

Can probably try making a bootable usb stick, I guess. What's the *absolute easiest one?

---

### Post by bear24rw on 2009-09-04
Easiest boot up cd is any linux live iso you have lying around lol Arch also has im instructions for making a USB stick

---

### Post by Yellow Pasque on 2009-09-04
> I cannot edit menu.lst (unless you can think of some way...)
Press 'Esc' when your system starts to get into GRUB. You can edit the boot parameters there (change 'splash' to 'nosplash').

---

### Post by LeFou on 2009-09-04
> **Temüjin said:**
> Press 'Esc' when your system starts to get into GRUB. You can edit the boot parameters there (change 'splash' to 'nosplash').

hm.. I hit Esc right when the Dell boot-options screen disappeared. I got what looks like a prompt

MBR 2FA:

but this prompt doesn't seem to be accepting keyboard input. Typing has no effect; the cursor just sits there blinking.

I tried hitting Esc a bit later in the process, and it didn't do anything, got the "VESA" stuff as above.

---

### Post by killermist on 2009-09-05
If your /home filesystem is a separate partition from your root filesystem, and you haven't done a large amount of tweaking to the core system configuration, it may be faster/easier to just reinstall, wiping the root and (if a separate partition) /boot filesystems.  
As long as you don't have it format your /home filesystem during the reinstall, all of your user preferences will be retained.

If you've tweaked the host file, samba or NFS sharing, SSH/SSHd settings, or anything like that, I'd save a copy of those files to your home directory so you can merge the changes back into the new files after reinstall.

If your /home filesystem is not a separate partition, and is part of the root filesystem, then that makes things more complicated because you'll want to backup your /home directory tree before doing a reinstall.  Depending on how much stuff you've stored in your home directory, that could be a chore.  If your home directory is relatively unpopulated, a live CD and a good sized flash drive should make that an easy enough operation.

Sometimes, the quickest fix is a reinstall.  And with Linux as opposed to windoze, quite often reinstalls are quite painless.

---

### Post by LeFou on 2009-09-16
Warning and apology: sarcasm coming. This has frustrated me so much...

> **killermist said:**
> If your /home filesystem is not a separate partition, and is part of the root filesystem, then that makes things more complicated 


Yep. And that is how ubuntu sets itself up by default, no?

> **killermist said:**
> 
you'll want to backup your /home directory tree before doing a reinstall.  Depending on how much stuff you've stored in your home directory, that could be a chore.

True. In addition, i'll need to back up the dozen or so MySQL databases and the half-dozen websites and the Apache conf and the hosts file and make a list of all the software i've added since getting this machine and ... and ...

> **killermist said:**
> 
a live CD and a good sized flash drive should make that an easy enough operation.


So true. If this computer had an optical drive.

> **killermist said:**
> 
Sometimes, the quickest fix is a reinstall...

Not this time. As it turns out, I was able to use unetbootin to make a USB stick that did the trick.

And i was eventually able to get wireless back by going through the whole ndiswrapper process (Cf [http://ubuntuforums.org/showthread.php?t=1264483](http://ubuntuforums.org/showthread.php?t=1264483))

Still no sound though.

---

### Post by killermist on 2009-09-16
Ah.  I hadn't anticipated that you would have loaded up a workstation with so many different server functions.

Yes, by default Ubuntu likes to install the system as a really big root partition and a relatively small swap partition.  Personally that seems like a bad design decision to me, though for new users recently migrating from windoze, it's less "scary" than immediately being advised to reshape your entire hard drive differently than you're used to.

Regarding the SQL databases, those are stored on the drive either as really big files, or big clusters of small files that when SQL is shut down are "shelf stable", and can be backed up as files, for import into a different instance of SQL later, right?

And regarding server functions, I guess that's why I generally segregate functions requiring a high uptime away from the machine I use as my desktop because in spite of the generally high uptime that my desktop has, periodically a reboot is summarily followed by an OS wipe and replacement.  Whereas my bittorrent box and file server, running on <500Mhz hardware just sit and run for months on end, leaving me the freedom to occasionally nuke the hard drive on my primary machine (well, everything but the /home partition) and dabble.

If you're bent on trying to repair pulse audio (I wouldn't even know where to start), I'd recommend looking for solutions on Slackware forums and communities.  Where Ubuntu communities are great at following walkthrough, Slackware communities are pretty intimately familiar with the nuts, bolts, cogs, sprockets, and welds that make a Linux system work (and break).  Their solutions may not be clean, or nice, but they generally work, and you generally will learn something from the experience.

That's my $0.50 (which after tax may be $0.02).  I hope some of it helps.

---

### Post by LeFou on 2009-09-17
Thanks for replying and for not dressing me down for being a little bit grumpy.

> **killermist said:**
> Ah.  I hadn't anticipated that you would have loaded up a workstation with so many different server functions.
... I guess that's why I generally segregate functions requiring a high uptime away from the machine I use as my desktop 

That's not really an option here, as I develop websites and need dev copies of these on the netbook so I can work without being online.

> **killermist said:**
> 
If you're bent on trying to repair pulse audio 

meh. I didn't particularly care about pulse audio, or any "advanced" sound control capabilities, until I realized that removing it somehow boogers wireless and sound entirely.

> **killermist said:**
> Their solutions may not be clean, or nice, but they generally work, and you generally will learn something from the experience.


I certainly don't mind exploring and learning and usually love it when it comes to GNU/Linux. It just surprises/angers me that 
-Removing any software package would remove drivers, or make them unusable
-Removing a *sound package would remove a *wireless driver, or make it unusable.

---

### Post by killermist on 2009-09-17
Is the laptop capable of running KVM?
If so, you could work up a virtual machine that could run the server functions, and worst case scenario (well, really bad, not worst), you could back up the VM's hard drive image to another machine, wipe and repair the OS on the laptop, copy the VM image back over, and off you go again.

This may not help you whatsoever in your current predicament, but for future use, it might be helpful.

One of the great aspects of Linux is that there are ways and ways and WAYS of encapsulating different things from each other so that if one thing breaks down, it only does a small amount of damage that's moderately easy to repair, even if a "repair" really means a wipe and reload.

If you're going to invest the time in doing a backup and reinstall, which I'd personally recommend, knowing all too painfully that a backup can be a serious pain (having done quite a bit of that recently), I recommend wiping the drive and splitting up the HD space into several areas so that backup/reload functions are easier to do in the future.

I would recommend a configuration similar to this:
/ 10-15Gb
swap 1Gb
/data (or maybe /opt) 2-3x the anticipated max size of your databases
/home everything else


On the repair front, maybe do an install of the version of Ubuntu you're using in a VM and then go into it's filesystem and klepto some of the initial configuration stuff that was lost when pulseaudio was removed.

Just an idea.  Not sure if it's helpful or not since "hardware" in the VM is different from the hardware in the actual machine, and I have no idea how pulseaudio handles audio devices.

---

### Post by LeFou on 2009-10-19
This is quickly becoming one of my all-time favorite threads.

I can't say I'm interested in learning how to configure virtual machines with KVM, or repartitioning my hard drive, or shopping for usb optical drives.

My problem is a little simpler:
Removing pulseaudio removes things (in this case, wireless drivers) that, in my opinion, have nothing to do with audio.

Anyway, I went the ndiswrapper route (ah, fond memories of 2004...), successfully bringing back my wireless. Then, to see if I had escaped PA I did

apt-get purge pulseaudio

I know what you're thinking: LeFou! You're going to break your wireless again! And you'd be right. It broke, but thankfully I just had to

apt-get install pulseaudio ubuntu-desktop

And wireless came back after a reboot. Piece of cake. My only real question is: why? Does pulseaudio manage my wireless card, or its driver?

Back to the main point, which is that sound (the thing PA *should manage) hasn't worked for a couple months now. "Open Volume Control" yields "No volume control GStreamer plugins and/or devices found.
 
The driver seems to be gone.

See below for details about my attempt to use OSS4, but if you just want to help, you can skip all that. Here are my questions:

0) A working driver for this sound card existed once; I know because I played music & video for 6 mos. or so without incident
1) At what point did it get removed/disabled?
2) Why? By that I mean e.g. if it got removed when I purged pulseaudio, is it because pulseaudio assumes that if I don't want pulseaudio I don't want *any audio? It's OK with me if PA assumes that, I just want to know so that I can avoid purchasing machines that have PA on them.
3) Where would I look for the driver? (Alsa link below doesn't have mine) What would it be called, given lspci output below?

-------------------------
lspci -v has
00:1b.0 Audio device Intel Corp blah blah (SCH Poulsbo) HD Audio Controller rev 06
Subsystem: Dell Unknown device 02b1

"Comprehensive Sound Problems Solutions Guide" says to go

sudo modprobe snd-
and hit tab for the available modules

But I have no tab-completion for "snd-", even though the dir
/lib/modules/2.6.24-24-lpia/updates/alsa/ contains 3 pages of snd-*-.ko things

Meh. Anyway, he said he couldn't help me as there isn't a driver listed at [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

My problem seems identical (machine, distro/version, chip, everything) to
[http://www.mail-archive.com/ubuntuforums-unanswered@lists.launchpad.net/msg06068.html](http://www.mail-archive.com/ubuntuforums-unanswered@lists.launchpad.net/msg06068.html)

Another approach: Everyone seems awfully excited about OSS4. "Installing OSS4 on Ubuntu 8.04" ([http://brainstorms.in/?p=172](http://brainstorms.in/?p=172)) 

sudo apt-get install oss-linux
(I know what you're thinking: LeFou! Nothing is that simple. And you'd be right)

E: Couldn't find package oss-linux

Well, I've extracted source before so I'm not scared. Too bad they don't have source for my architecture (am I right that "lpia" is my architecture?) I wonder if the x86 will work

Guess not, b/c after
extract etc.,  blacklist alsa... 

dpkg-reconfigure linux-sound-base
[Select OSS]
and reboot, 

ossdetect -v
/dev/bus/usb/002: No such file or directory
USB support available in the system, adding USB driver
Detected Generic USB audio/MIDI device(BETA)

I should point out that I don't have a USB audio device that I know of. I would just like to plug in my earbuds and listen to music now and then.

soundon
OSS is already loaded

ossxmix
No mixers are available

soundoff
No mixers in the system

And, of course, my volume control stuff reports that no soundcards are configured.

dpkg-reconfigure linux-sound-base
[select ALSA]
alsa reload
Unloading ALSA sound driver modules (none loaded).
Loading ALSA sound driver modules: (none to reload)

So, now that I have, by my count, 5 applications competing for my soundcard and none of them winning, I wonder whether it's safe to uninstall any or all of the following:

pulseaudio (if I decide to give up on wireless and use my ethernet cable)
alsa 
oss4
esd
gstreamer

---

### Post by killermist on 2009-10-20
I'm not sure what the interplay is between the different sound drivers.
When given a choice, I've gone with or stayed with Alsa.
I don't know why or how disabling Pulse disables your wireless except to mention that I've heard that Pulse is also supposed to be "smart enough" to route sound from machine to machine if the machine you're at isn't the one that you told to play audio, and as such it has to manage 'audio over network' type components (like network, unfortunately).
It's possible there's a conflict between ESD and alsa, but that's not a certainty.  And I know that I know absolutely nothing about OSS4.  I know Alsa had an OSS compatibility plugin so old OSS programs could use a passthrough into alsa, but again it's details that I haven't gotten into.

I wish I knew how to help you.

---

