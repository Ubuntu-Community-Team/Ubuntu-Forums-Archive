---
title: "Lost sound out of the blue"
date: 2009-02-04
forum: Multimedia Software
---

### Post by CharlieNixon on 2009-02-04
I've been running 8.10 for a few days. No problems with audio. Then, today I logged in and my sound doesn't work at all. I tested the speakers on a different PC and they work fine. I did the System > Administration > Hardware testing and the audio test failed. Here is a snippet of my **lspci -v**

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
 
I followed the [[COLOR="Blue"]_Comprehensive Sound Problems_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449") post but it wants me to recompile alsa. That seems a bit drastic since I didn't make any changes to begin with and it worked originally. 

In troubleshooting I've used synaptic to remove and reinstall "alsa-base" and I've run **apt-get update** a couple times. 

Anybody help?

---

### Post by ddennedy on 2009-02-04
I just upgraded my 8.10 install yesterday since a few weeks and now my sound stopped working too! I am not running pulseaudio. I verified the mixer level/mute settings and speakers as well. I am using an Audigy2 ZS. lsmod shows the modules as loaded and aplay -l lists the PCMs...

I just returned from poking around some more, and I found that I had to toggle the "Audigy Analog/Digital Output Jack" switch in the mixer to make it work. Apparantly, it defaults to digital in the new version.

---

### Post by CharlieNixon on 2009-02-04
My sound came back, again out of the blue, after several reboots. Note - not one reboot, several reboots. 

*sigh* 

oh well, at least it's working

---

### Post by CharlieNixon on 2009-02-04
This thread is solved, but for some reason the option to mark it as such is not available in the "thread tools" menu.

---

### Post by Will May on 2009-02-04
> **ddennedy said:**
> I just upgraded my 8.10 install yesterday since a few weeks and now my sound stopped working too! I am not running pulseaudio. I verified the mixer level/mute settings and speakers as well. I am using an Audigy2 ZS. lsmod shows the modules as loaded and aplay -l lists the PCMs...

I just returned from poking around some more, and I found that I had to toggle the "Audigy Analog/Digital Output Jack" switch in the mixer to make it work. Apparantly, it defaults to digital in the new version.

Thanks for that! I've been wondering why the 28.11 upgrade lost all sound since the weekend!

I wonder whose bright idea it was to invert the meaning of a switch in a simple bug fix release?

---

### Post by mazz0 on 2009-02-06
Thanks guys, the "Audigy Analog/Digital Output Jack" was buggering it up for me too, but switching it has fixed it. :)

---

### Post by CharlieNixon on 2009-02-10
My sound stopped working again, this time after a gstreamer install. I would un-install it, but it was installed through the browser and I'm not sure which of the many gstreamer packages listed in synaptic is the one that broke my stuff. 

Maybe I'll try that analog/digital switch you guys are talking about? I don't see it in alsamixer, where is it?

---

### Post by CharlieNixon on 2009-02-18
Since my last post the sound started working again (after a reboot). Now I have a better problem description:

Every three or four days my sound completely stops working until I reboot. 

any ideas?

---

### Post by homeuser1 on 2009-02-21
As previous posts have mentioned, I lost my analog sound output after an upgrade a few weeks ago. I'm new to ubuntu, so I don't know how to restore to a pre-upgrade time. So, here  are my problems since that upgrade:

1) I can't find the analog/digital switch. I need help with this. I don't have a speaker icon on the bottom toolbar since the upgrade.
2) I lost the little green guy in the upper right corner to shutdown with. I now have to ctrl-alt-delete to shutdown.  This isn't a big issue, but it is something that changed. 
Any help would be appreciated.
Al

---

### Post by CharlieNixon on 2009-02-26
> **homeuser1 said:**
> As previous posts have mentioned, I lost my analog sound output after an upgrade a few weeks ago. I'm new to ubuntu, so I don't know how to restore to a pre-upgrade time. So, here  are my problems since that upgrade:

1) I can't find the analog/digital switch. I need help with this. I don't have a speaker icon on the bottom toolbar since the upgrade.
2) I lost the little green guy in the upper right corner to shutdown with. I now have to ctrl-alt-delete to shutdown.  This isn't a big issue, but it is something that changed. 
Any help would be appreciated.
Al

1) I don't know the answer to this myself. In fact, my audio works when I boot up but only for a while (few hours? maybe a day?) then it doesn't come back until a reboot.

2) right click your panel and choose "add to pannel" - it will give you a list of stuff you can add, look through the list to find what you're missing.

---

### Post by airjaw on 2009-02-26
It seems that this has been happening to quite a few users.
This happened to me yesterday.

The problems all seem to be related: 
all of a sudden, sound just stops working... seems to be a pulse audio problem. No settings were changed, so it might be from an update of some sort...

---

### Post by CharlieNixon on 2009-03-12
I figured out my issue. The sound is fine. Every so often it would just go mute. Then I realized the problem. I use the built in terminal services client quite often. It was set to play the sounds from the remote computer (which didn't really work, IIRC). After I disconnected my local sound would no longer work. This explains why it would be "fixed" after a reboot. 

So I adjusted the sound settings on the TS client and the problem is gone. 

The moral of the story is: if the sounds works sometimes, it's probably not a sound config problem, it's an application problem (in my case the TS client). 

Thanks all!

---

### Post by homeuser1 on 2009-04-26
> **CharlieNixon said:**
> 2) right click your panel and choose "add to pannel" - it will give you a list of stuff you can add, look through the list to find what you're missing.

Sweet! I know this is a little late, but this fixed my problem.  Now I can toggle back and forth between digital and analog.

I had forgotten all about this, until this morning while playing around with the LinuxMint6.0 iso.  I saw the famillar speaker icon in the toolbar which allowed me to get to the switches. I then came back to this post and saw Charlie suggested how to fix my problem back in Feb.  Thanks! 

Upgraded to Ubuntu 9.04 this morning.  Main issue right now is not being able to access the pandora website.  Won't load. I love this radio station.

---

