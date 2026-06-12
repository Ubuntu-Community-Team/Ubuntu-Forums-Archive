---
title: "Can't get NVIDIA 195.36.24 driver installed"
date: 2010-05-19
forum: Multimedia Software
---

### Post by gizmocan on 2010-05-19
Hi!

I have a Zotac IONITX-F-E motherboard (Intel Atom Dual Core 1.6 GHz + Nvidia ION) -based box with Ubuntu 10.04 64-bit installed. My goal is to play back 1080p video.

I read somewhere that the nouveau driver that installs by default with ubuntu 10.04 does not support VDPAU. So, my first step is to install the nVidia proprietary driver.

I tried following a half-dozen different guides for doing this, none of which worked. Let's take this one for example: 

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

I purge. I reboot. I run the Nvidia installer (NVIDIA-Linux-x86_64-195.36.24-pkg2.run). I get:

```
ERROR: Unable to create '/usr/lib/nvidia-current/libGL.so.195.36.15' for copying (no such file or directory).
```So, I run:

```
sudo apt-get install nvidia-glx-185 nvidia-185-modaliases
```I try the nvidia installer again. It works. I reboot. 

I get a message saying that ubuntu is running in low graphics mode, because loading the nvidia kernel module failed.

I check /var/log/messages and see:

```
API mismatch: the client has version 195.36.24 but the kernel module has version 195.36.15.
```I take a Tylenol and here I am.

Help!

---

### Post by Rumpty on 2010-05-20
You didn't want to let it download and install the Nvidia driver itself then? Does the 64-bit aspect complicate things?

---

### Post by gizmocan on 2010-05-20
> **Rumpty said:**
> You didn't want to let it download and install the Nvidia driver itself then? Does the 64-bit aspect complicate things?

By "it" do you mean the Synaptic Package Manager?

The first thing I tried was using Synaptic to install the 'nvidia-current' driver package. That caused my "refresh rate" (not sure if that's the right term for what I mean) to become very slow. For example, if I click on a menu, it takes about a full second for the screen to get repainted with the menu open and I can see the horizontal line progressing down the screen as it refreshes.

I hadn't removed or blacklisted nouveau at that point though. Would that have helped? 

When I went searching for a solution, I only found howtos describing the manual approach exemplified by the link in my first post. Is the manual approach to installing the nvidia drivers not the best bet?

---

### Post by gizmocan on 2010-05-20
I'm sure there must be lots of people who have an almost identical set up to mine and who've managed to get 1080p playback going...

---

### Post by Rumpty on 2010-05-20
Hello gizmocan. By "it", I meant the automatic method, using System - Admin- Hardware Drivers, and letting the download and installation of the "current driver" take place. I assumed we no longer had to use the messy manual method.

I did not blacklist nouveau, or anything else. Didn't know that nouveau even existed! That very slow re-drawing of the screen that you have suggests something isn't right, I think.

My hardware is nothing like yours, but 1080p video plays ok in smplayer. My video card is the Nvidia 8400GS, and the video preferences in smplayer are set to use vdpau output driver.

---

### Post by gizmocan on 2010-05-21
Ok, so I've uninstalled the 195.36.24 nvidia driver using the nvidia installer.

I then used Synaptic to install nvidia-current (which looks like the not-quite-current 195.36.15 version of the nvidia drivers). I also installed nvidia-current-modaliases, libvdpau1, nvidia-current-dev, libvdpau-dev.

When I rebooted, I don't get the 'low graphics mode' warning, but I am once again facing the very slow repaint rate I described earlier.

Is this potentially related to not having the right OpenGL libraries installed? What versions/packages should I have installed?

---

### Post by mc4man on 2010-05-21
> I then used Synaptic to install nvidia-current...
After installing nvidia-current (or switching back to thru update-alternatives) you should run this and restart

```
sudo nvidia-xconfig
```

---

### Post by gizmocan on 2010-05-22
Thanks for the tip, but I had already done that.

I noticed something very funny though. I left my computer on all night (unintentionally), and when I went to use it this morning, the slow repainting problem was gone! Unfortunately, when I rebooted, it came back. :(

---

### Post by gizmocan on 2010-05-23
I found this post:

[http://ubuntuforums.org/showthread.php?t=1470343#10](http://ubuntuforums.org/showthread.php?t=1470343#10)

And followed the steps. It allowed me to install the nvidia 195.36.24 driver successfully, however the slow repainting problem manifested itself as before.

Has anyone ever seen a problem like this before?

---

### Post by gizmocan on 2010-05-24
The slow repainting problem is always present when I first boot up, but if I continue using the system (i.e., surfing the web in Firefox, executing commands (like cd, ls) in a terminal), it eventually goes away. I've seen it take about a minute and other times considerably longer. 

If I just walk away after my system has booted up, the problem doesn't seem to fix itself after up to 20 minutes.

I'm not even sure where to look for what might be causing this...

Could this be related to not having nvidia-glx-195 and nvidia-195-modaliases installed?

---

### Post by gizmocan on 2010-05-27
This is seriously annoying. I've tried several different work-around methods, but nothing works consistently.

Anybody?

---

### Post by gizmocan on 2010-05-31
I don't know if this really counts as a solution, but I've gotten around  the problem by going into System -> Preferences -> Appearance,  then clicking on the Visual Effects tab and changing the option to None.

Now my desktop looks a little more boring, but it isn't slow!

---

