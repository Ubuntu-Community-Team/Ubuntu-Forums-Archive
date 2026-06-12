---
title: "sound stops working when I suspend"
date: 2008-05-28
forum: Multimedia Software
---

### Post by TheMouse on 2008-05-28
I'm running Hardy on my Acer Extensa 5620.

Whenever I suspend my computer then wake it up, sound is gone. I've checked alsamixer, and the settings haven't changed. The sound panel in system preferences is set up correctly. Sound only comes back if I restart the computer, after which it works fine until I suspend it again.

Anyone have a clue what's going on? Thanks.

---

### Post by xfceuser on 2008-05-28
after you come back from suspend typein a terminal:
sudo /etc/init.d/alsa-utils restart
see if it work

---

### Post by TheMouse on 2008-05-28
> **xfceuser said:**
> after you come back from suspend typein a terminal:
sudo /etc/init.d/alsa-utils restart
see if it work

It outputs this:

* Shutting down ALSA...                                              [ OK ] 
* Setting up ALSA...                                                 [ OK ] 

And the sound isn't on.

---

### Post by xfceuser on 2008-05-28
try also:
sudo /etc/init.d/alsa-utils reset

---

### Post by TheMouse on 2008-05-28
It outputs this:

 * Resetting ALSA...                                              [ OK ]

And there is still no sound.

---

### Post by TheMouse on 2008-05-29
Anyone?

---

### Post by Moezzie on 2008-06-18
Here, try this:
```
sudo alsa force-reload
```
It works for me. I just dont know how to make it run automaticly after every return from suspend.

---

### Post by jadymitchell on 2008-06-19
This works for me as well.  Presumably, there's a script that runs on resume from suspend.  If we can find its name and edit, problem solved!

---

### Post by michael.p.mckenzie on 2008-06-20
If you use Kpowersave, you can run the command as an event on suspend from resume. Thanks for tracking down the rest

---

### Post by kjaleel on 2008-06-20
I haven't tried this yet, but if you edit "/etc/acpi/resume.d/67-sound.sh", and comment out the "alsa-utils start" line, and add:

/sbin/alsa force-reload

to it, it should automatically run the next time you resume from suspend. So the file should basically look like the following:

#!/bin/sh

# Get sound back
if [ -x /etc/init.d/alsa-utils ]; then
  #/etc/init.d/alsa-utils start
  /sbin/alsa force-reload
fi

Alternatively, if you don't want to touch the default Ubuntu supplied scripts, you can create your own script inside 'resume.d', and make sure it is executable. Give it a name with a number higher than any of the other numbers so that it is executed *last*.

---

### Post by jadymitchell on 2008-06-23
I tried both solutions with no success.  Is there a log you can go to see to which scripts are executed on resume?

---

### Post by TheMouse on 2008-06-27
I've edited /etc/acpi/resume.d/67-sound.sh. I've sudo force-reloaded alsa. Neither worked.

---

### Post by 3dOptics on 2008-06-28
I get the sound back when I run the following commands:

sudo /etc/init.d/alsa-utils restart
sudo /etc/init.d/alsa-utils reset
sudo alsa force-reload

---

### Post by RustyTrowel on 2008-07-12
I'm glad to have come across this discussion.

I am having similar problems with loss of sound after suspend.

/sbin/alsa force reload

works on my system for restarting the sound.  However, sticking that same line of script in the 67-sound.sh
config file doesn't seem to produce any sort of result.  I'm not very computer savvy, so I don't have any worthwhile ideas.  If it's worth anything, my system is as follows:

Hardy Heron 32 bit on 
ABIT NF-N2S AM2 socket Motherboard
1 GB DDR2 800 SDRAM
AMD Athlon 64 X2 4600+ 2.4GHz chip
EVGA GeForce NVIDIA 7600GT Graphics Card

---

### Post by RustyTrowel on 2008-07-12
Sorry.  There is an error in my last post.  What I meant to say is that I type:

sudo su
/sbin/alsa force-reload

into the terminal after I come out of suspend.

That seems to work on my system.  

-David

---

### Post by mkw87 on 2009-02-07
I am having the same problem, when I resume from suspend I have no sound.  When I execute either of the commands listed here I receive the following error.

```
jennifer@bangarang:~$ sudo /sbin/alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jennifer/.gvfs
      Output information may be incomplete.
Terminating processes: 9585lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jennifer/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jennifer/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jennifer/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
```

Anyone have any idea on what might be causing this?

---

### Post by hamidoo on 2009-04-25
Ok guys and found another workaround to automatically run the "/sbin/alsa force-reload" command after resume.

1-hit alt-f2 and type sudo nautilus (to have root privilege)
2-navigate to /etc/pm/sleep.d
3-create a file named "10-sound-after-resume"
4-edit the file with gedit and add the following

#!/bin/sh
/sbin/alsa force-reload

5-save the file and make it executable.

The only problem is that if you have any opened application that uses the sound card, it will be killed (closed).

BTW i use jaunty.

---

### Post by Nisuspi on 2009-07-03
I have exactly the same output as mkw87 above - and it's driving me mad. Been like this since the beginning of the year, and I have no idea what update caused it. Upgrading to Jaunty hasn't changed it, uninstalling and reinstalling Alsa, pulse and the Creative sound driver makes no difference. 

I could live with it, but whenever a sound event tries to play after resume, the whole system hangs. There's no log messages appearing at the same time, though, nor an identifiable process in system monitor...

I really don't want to have to try a clean install - the reason I switched from Windows was to get away from that sort of thing. But I don't know what else to try.

Has anyone got any ideas?

---

### Post by raistlin_kell on 2009-12-29
I'm having the same issue with Ubuntu Karmic 9.10. I'm using a HP NC6220 with 2gig of ram and a 160gig HDD. Its an old machine but a goodie and my traveling companion. 

Since doing a clean install of Karmic (not upgrade from Jaunty 9.04) I've noticed that the sound no longer functions after doing a resume from suspend. 

I never encountered the issue with Jaunty 9.04. 

I'm happy to live with the problem but it is annoying. Having the laptop stream radio on Rhythmbox from 1/2 way around the world while at work is awesome.

---

### Post by AnttiV on 2010-01-17
Same here. HP nc8230 laptop, Karmic 9.10 updated from clean 9.04 install. Sound disappears after waking from sleep (works perfectly before suspend). Only way to get it back is to run those three commands or restart the machine.

It's driving me nuts.

EDIT: Want to know something weird? Okay, here goes:

Computer is powered off, after booting up everything works perfect, sound included. I close the lid, putting the computer to suspend. Fine thus far.

Wake from sleep, sound disappears, everything else works fine. No amount of tinkering with GUI gets the sound back. Entering the aforementioned commands in terminal get sound back working. Life smiles.

THEN, the strange thing: After subsequent suspend/wake cycles, sound DOES NOT disappear. It works straight after a wake-up. Just that after a reboot the first time it suspends sound disappears. After entering the commands sound works across suspend/wake events until the next reboot.


Don't worry, I don't understand it either :D

---

### Post by nabilalk on 2010-02-17
> **hamidoo said:**
> 

BTW i use jaunty.
This problem persists with [Karmic (9.10)]("http://crunchbanglinux.org/forums/post/55645/#p55645"). Thanks for the fix without the need of sudo :D

---

### Post by michiganitis on 2010-10-05
This happens to me as well...

Except that sometimes, even when i restart, there's no sound. In such a case, if I restart into my Windows partition and then restart again into the Ubuntu partion, then I get sound back.

It's very odd...

BTW...I'm running 10.04 LTS on a Compaq Presario CQ62-225NR.

---

### Post by danaus on 2012-01-14
Regarding AnttiV's post.

I run Lucid on a [LG - M1 Express Dual] laptop with the following Intel soundcard and I have the same problem as the rest of you have: No sound after sleep/resume.

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: LG Electronics, Inc. Device 003a
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d8540000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

I have tried several different types of fixes (from CLI) but none worked.
After reading AnttiV's post I also tried repeating the sleep/resume-cycle. 

Miraculously, the sound came back. Before I have only tried the CLI fixes and the Mother-of-All-Fixes... Reboot (works every time). I feel a bit relieved for this temporary solution.

Only after the sound came back I remembered that the "sound doesn't return on resume" has previously been somewhat random. Might it have something to do with running programs which actively use soundcard? I haven't yet applied this theory to practice.

Thanx AnttiV

---

