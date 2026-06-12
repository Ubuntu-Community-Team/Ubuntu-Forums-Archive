---
title: "unsupported audio codec on Thinkpad T400s??"
date: 2009-07-17
forum: Multimedia Software
---

### Post by aweck on 2009-07-17
My new Thinkpad T400s arrived a few days ago.  I've tried installing both 32bit & 64bit Ubuntu 9.04.  Most drivers appear to function well (more so than CentOS 5.3).  The only persistent issue I've ran into is getting the sound card to work on any of the platforms, both with or without the latest kernel updates installed.  I also tried compiling and updating the alsa drivers from 1.0.18 to 1.0.20 without success.  I'm wondering if this might be due to a relatively new unsupported codec (Conexant ID 5069) on the Intel chipset since I can't seem to find a reference to this anywhere.  I was wondering if anyone might have some insight or suggestions.  I've searched this forum and others pretty extensively, but have had no luck yet.  Further details are below:

user@yoda:~$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Conexant ID 5069

user@yoda:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

user@yoda:~$ sudo lspci -v
...
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Lenovo Device 20f2
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f2620000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

user@yoda:~$ sudo lshw -c multimedia
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

I've tried the following options in /etc/modprobe.d/alsa-base (in more combinations than I can count):
options snd-hda-intel {laptop|laptop-eapd|3stack|thinkpad|thinkpad-x200|lenovo}
options snd-hda-intel force_msi=1
options snd-hda-intel single_cmd=1

Any thoughts would be welcome.

Thanks,
aweck

---

### Post by h.codebilis on 2009-07-19
I unfortunately don't have a solution for you, but I'm about to follow your lead. My T400s is scheduled to arrive July 20, and I plan to dual boot Vista with Jaunty. I'll ping you if I find a solution.

---

### Post by snappca on 2009-07-21
Not sure if it helps, but I'm running 64bit Kubuntu on my T400s and the audio worked right out of the box.  As did the webcam and for the first time I've been able to make resolution changes and utilize the VGA connection via the display manager GUI.  My mic mute button doesn't work and I'm experiencing a lot of hassle with maintaining resolution changes when I dock/undock but that is getting off-topic.

---

### Post by igorzwx on 2009-07-21
HDA may work better with OSS4.
You can ask on OSS4 forum, perhaps.
There is a howto for HDA with OSS4 in Arch Linux Wiki.

---

### Post by aweck on 2009-07-22
> **snappca said:**
> Not sure if it helps, but I'm running 64bit Kubuntu on my T400s and the audio worked right out of the box. As did the webcam and for the first time I've been able to make resolution changes and utilize the VGA connection via the display manager GUI. My mic mute button doesn't work and I'm experiencing a lot of hassle with maintaining resolution changes when I dock/undock but that is getting off-topic.
 
That is useful to know (albeit frustrating for me).  If you issue 'cat /proc/asound/card0/codec#0 | grep Codec' what Codec is displayed?  Do you mind sharing the machine type of your T400s - mine is 2801-CTO.
 
I'll take a look at utilizing OSS4 as well.
 
Thanks,

---

### Post by snappca on 2009-07-22
Mine is also 2801 CTO with 6GB RAM, 2.53GHZ proc, and 128GB SSD.

Here is the output you requested which seems to show the same as yours:

```
~:$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Conexant ID 5069
```

Let me know if you need anything else.

Are you noticing any other issues (e.g. kernal panics, desktop effects crashing, or system hangs possibly associated with SSD)?

---

### Post by aweck on 2009-07-27
Well, I finally figured out the sound issue.  When the laptop arrived with Windows XP installed the sound worked.  Sometime between then and when I installed linux the hardware apparently stopped working.  For testing I reinstalled Windows and experienced the same sound issue I was having in linux!  I'm shipping back to Lenovo for correction.
 
Re: your note on other issues: I am experiencing kernel panics/hangs about half of the time when I go to shutdown or reboot.  It starts to shutdown and then just hangs.  If I press crtl-alt-del, it says 'shutting down all md devices' and finishes the reboot/shutdown.  I was going to start looking into this after I resolved the sound issue, but that will have to wait until at least next week.  (Also, this only occurred with Ubuntu 9.04; not CentOS 5.3 - I suspect a kernel issue.)

---

### Post by pbateman on 2009-11-12
Hey guys, I was wondering if your mic worked out of the box?
I just got my t400s yesterday and installed Koala on it. Everything seems to be working fine, I tested Skype though and it seemed the mic wasn't being picked up. I haven't been playing with it much since i got home late but was wondering if you had to tweak anything.
I'm running the 64 bit version also, dont know if it makes a difference. 
Also my wireless card (intel 5100 I believe), somehow is not connecting automatically after reboots...I'm sure I'll have to play around with it a bit since I just installed KK last night.  I am surprised at how most things work great with no tweaking required though...

---

### Post by snappca on 2009-11-12
To get my mic working properly I just had to adjust the volume levels in alsamixer.  Just type alsamixer in a console, then hit tab to get to the "Capture" screen, then adjust all three volume levels to 55, then hit ESC to save and exit.  After that Skype should work just fine.

Not sure on the wireless card; mine works fine in Kubuntu.

---

### Post by pbateman on 2009-11-12
Thanks I'll try that once i get home!

---

### Post by quiimpcif on 2009-11-12
OK,  cool!^_^ I just wanted to make sure I didn't do anything wrong :]

---

### Post by pbateman on 2009-11-12
Go figure...it had not occurred to me to fully test the sound yesterday night, I tested whatever sounds skype made and it seemed to work. I went to test today with some music or website and there's no sound. 
I checked the mixer to make sure nothing was muted, also ran the system test, but no sound either. There is sound however from the headphones jack.
I am currently installing Koala 32 bit to see if it makes a difference (I installed 64 bit yesterday). if this doesn't work I'll install XP or 7.....damn..

When I go into Sound preferences , under Hardware the only item listed is "internal Audio" Shouldn't is show the name eg. intel etc...

~$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Conexant ID 5069

---

### Post by pbateman on 2009-11-12
I spoke too soon...my 1 day old t400s has this problem, and im pretty sure it just came like that.  I called Tech support today, they wanted to send it to repair....a 1 day old laptop? No thanks. I told them i did not feel comfortable sending a 1 day old laptop for repair so i asked about either returning it and geting a new one or getting my money back. They told me to call Sales tomorrow (since its closed now) and talk to them and give them my support ticket number in case they ask.

Anyone had luck returning these laptops?...very disappointed. And to think I almost did not buy this laptop because i was afraid this would happen (...or random shutdowns that seem to be another problem). Should have gone with my gut.....now I just hope they dont give me a hard time returning it.
Sorry had to rant....

---

### Post by snappca on 2009-11-13
Wow, I'm sorry to hear you are still having issues.  I'm surprised you got anywhere with Lenovo support seeing as how you didn't have windows on the box.  I suppose the first thing I'd do is go through the hassle of getting the box back to the factory os to make darn sure the issue is hardware related.  I'd be surprised if Lenovo would let you return it with Linux on there.

My experience with my T400s has been 98% outstanding.  Keep in mind I've had mine sine July and have been running 64bit Kubuntu on it exclusively.  Here is the list of issues that I bumped into at one point or another:

* **slow graphics** - this was due to ubuntu's 9.04 (jaunty) shipping with a crappy intel driver;  graphics are nice and smooth on 9.10 (karmic)

* **ssd hangs** - this is because I didn't research ssd limitations...the only time I bump into this is when I'm doing a crazy amount of writes to the disk and the system becomes a bit slow to respond.  (rarely occurs....tweaks to ioscheduler might be helpful)

* **cpu whine** - boy that cpu squeal gets old after awhile; I resolved that by adding "processor.max_cstate=2" to the kernel line in my grub config file

* **dock/undock** - it used to be a hassle to drop the laptop in a dock to attach my external monitor but I resolved this with a simple bash script that triggers based on the a/c being plugged or unplugged and tells xrandr to check if I've just attached an external monitor

* **function keys** - these aren't that important to me, but I went ahead and implemented them with some acpi scripts (lock screen, sleep, hibernate...etc); the brightness and thinklight work fine out of the box

* **speakers** - the only issue I've had is that the speakers don't mute when I plug my headphones in; not the end of the world for me, but I can imagine it could be frustrating for someone else

* **mic mute button** - this is the only button that is still not working; but I don't particularly care much

As you can see, my experience with Kubuntu has been pretty darn good.  Now that I have Karmic on it with my nifty dock/undock script I'm ecstatic.  Everything has been chugging along nicely.

---

### Post by pbateman on 2009-11-20
My replacement t400s was shipped today, I'm keeping my fingers crossed.....

---

### Post by cmanfu on 2009-12-03
Snappca, could you tell us how you trigger a script to run based on the a/c being plugged or unplugged?  I would love to do that for myself!

---

### Post by snappca on 2009-12-03
@cmanfu

To be clear I am running Kubuntu rather than Ubuntu since I tend to prefer KDE rather than Gnome.  In any case, if you are running KDE you can just go to "System Settings" and into "Notifications".  From there select "PowerDevil" from the "Event Source" pull-down menu.  In the associated list you should see "AC adapter plugged in" and "AC adapter unplugged".  For each of those I've just browsed to my script file in the "Run Command" entry field.  So now when PowerDevil detects a change in the AC status it plays a sound and runs my script which does a quick test to see what displays are plugged in and runs the appropriate xrandr script to set things up the way I want them.

---

### Post by cmanfu on 2009-12-04
@snappca

I see, thanks.  Unfortunately I'm running Gnome, not KDE.  Any ideas how to do this in Gnome?

---

### Post by Alex Paderin on 2010-07-16
Try it _[http://wildmagic.ru/public/pinsensed.tar.gz](http://wildmagic.ru/public/pinsensed.tar.gz) . It's solve your problem._[]("http://sandro-omsk.livejournal.com/5703.html")

---

