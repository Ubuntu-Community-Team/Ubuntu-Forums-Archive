---
title: "Clicking from speakers"
date: 2009-02-09
forum: Multimedia Software
---

### Post by lazman on 2009-02-09
I have a problem that is getting on my nerves. When I first boot up I have sound and it works great. If I leave the computer on over night however, it sometimes the next day the sound is not working and all I can hear is a quick clicking sound. Like a slow motor boat sound on an Atari. If I reboot the computer sound works great again. I have tried restarting alsa and as it's restarting the clicking will stop, then start back again after alsa has started back up. I have also tried adding my login name so it looks like audio:x:29:username where username is my login name. This hasn't helped any either. I know the drivers are installed because it will work after a reboot. Is there anything else I can do to try to track down the problem? Sometimes this will happen after just a few minutes of up-time. It's getting rather annoying to be rebooting all the time.

I ran this command  aplay -l
and got this for my sound card:

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7309
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at dfff4000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

The <access denied> has me wondering if a program that is running is locking the sound card or something. But I have no idea how to find out what software is using the sound card, something is making it click.

I'm using Ubuntu 8.1 with Gnome desktop. I have also made sure the mic settings are muted.

Any ideas?

Thanks!
~laz

---

### Post by lazman on 2009-02-09
I just found this [post]("http://ubuntuforums.org/showthread.php?p=2742327"). tigerstripedcat tells how to find what process is using the sound card and how to kill it. I ran this and now sound is working again without restarting! YAY

This is what I did.

sudo lsof | grep pcm

This revealed a process named pulseaudi (I think) The whole line looked like this:

pulseaudi  6053    laz  mem       CHR              116,6               12844 /dev/snd/pcmC0D0p
pulseaudi  6053    laz   38u      CHR              116,6               12844 /dev/snd/pcmC0D0p

I'm not exactly sure what all this means but the process part that is useful is the 6053. So Then I issued this command:

kill -9 6053

Then this one:

sudo /etc/init.d/alsa-utils restart

And TADA! No more clicking! I started up vlc player streaming a radio station and all is back to normal.

After doing a google search on pulseaudi I think it's like a driver set like alsa. I'm not 100% sure on this however. So, I'm thinking that I may have two different drivers trying to use the sound card or something, but I'm not sure if this is correct or not. I don't want to try to remove anything until I'm sure that I need to.

---

### Post by lazman on 2009-02-09
Well, I was going to add [solved] to the thread name but I guess I don't have the permissions. Maybe changing it on this post will do it.

---

