---
title: "Microphone Won't Work"
date: 2011-01-22
forum: Multimedia Software
---

### Post by northerndude81 on 2011-01-22
I can't get the microphone to work in any application (Sound Recorder, Audacity, Skype, etc.) It's been this way for a while and didn't bother me, but now I need to use Skype for work so I desperately need to fix this over the weekend. I checked the Comprehensive Sound Guide, but couldn't find an answer there. As far as I know, my ALSA is up to date (I had to update it to get the sound working at all).

On a MSI Wind Desktop with 10.04, if that makes a difference. I'm not very knowledgeable about Linux (or computers in general), so if someone could help me without too much tech jargon, I would be very grateful.

Thank you!

---

### Post by xc3RnbFO8P on 2011-01-22
Install Gnome Alsa mixer (Synaptic Package Manager or Ubuntu Software Center)
Check Input, Capture and Mic

---

### Post by northerndude81 on 2011-01-22
Ok, I installed Gnome ALSA Mixer, but for some reason when I try to run the program it won't run. I get the spinning cursor for a few seconds, and there is a task bar for it at the bottom of the screen, but then the program never opens and the task bar disappears.

Any idea?

---

### Post by xc3RnbFO8P on 2011-01-22
Try to run it from Terminal:
> gnome-alsamixer

---

### Post by northerndude81 on 2011-01-22
When I type that into the terminal I get this:

> (gnome-alsamixer:8532): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed

(gnome-alsamixer:8532): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault

?

---

### Post by xc3RnbFO8P on 2011-01-22
Read this (last Page):
[http://ubuntuforums.org/showthread.php?t=881920]("http://ubuntuforums.org/showthread.php?t=881920")

---

### Post by northerndude81 on 2011-01-22
I tried everything on that page, but nothing worked. :( This is what I got:

> user@user-desktop:~$ alsamixer -D hw:0
cannot load mixer controls: Invalid argument
user@user-desktop:~$ alsamixer -D hw:1
cannot open mixer: No such file or directory
user@user-desktop:~$ alsamixer -c 0
cannot load mixer controls: Invalid argument
user@user-desktop:~$ alsamixer -c 1
invalid card index: 1
try `alsamixer --help' for more information
user@user-desktop:~$ sudo /etc/init.d/alsa-utils reset
[sudo] password for user: 
sudo: /etc/init.d/alsa-utils: command not found
user@user-desktop:~$ sudo apt-get install module-assistant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
module-assistant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@user-desktop:~$ sudo m-a update

Updated infos about 87 packages

Any other ideas?

---

### Post by xc3RnbFO8P on 2011-01-22
This:
[http://ubuntuforums.org/showpost.php?p=5583381&postcount=24]("http://ubuntuforums.org/showpost.php?p=5583381&postcount=24")

---

### Post by northerndude81 on 2011-01-22
I tried that one already. Didn't work. I got:

> user@user-desktop:~$ sudo /etc/init.d/alsa-utils reset
[sudo] password for user:
sudo: /etc/init.d/alsa-utils: command not found
user@user-desktop:~$ sudo apt-get install module-assistant
Reading package lists... Done
Building dependency tree
Reading state information... Done
module-assistant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@user-desktop:~$ sudo m-a update

Updated infos about 87 packages 

Sorry, what's next?

---

### Post by northerndude81 on 2011-01-22
Anybody? I have to solve this or I can't do my job on Monday. I'm in a bit of a bind. Help!

---

### Post by xc3RnbFO8P on 2011-01-22
Try this:
> sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

---

### Post by northerndude81 on 2011-01-22
Edit: Sorry, hold on one sec while I try that.

---

### Post by northerndude81 on 2011-01-22
Nope, still doesn't work. :(

When I try to record sound the little bar that moves from left to right as you record won't even move, it just sits there. Skype calls fail and System -> Administration -> System Testing hangs when it gets to the audio recording part.

Help!  :(

---

### Post by northerndude81 on 2011-01-22
Bump! Still looking for an answer to this one. Someone, please!

---

### Post by jsland on 2011-01-22
In terminal;

pavucontrol

does this work or crash like alsamixer?

---

### Post by northerndude81 on 2011-01-22
That works... kind of. It brings up a Volume Control window. I'm not sure what I should be looking for here.

What do you suggest I do next?

---

### Post by northerndude81 on 2011-01-23
Could someone help me figure this out, please?

---

### Post by xc3RnbFO8P on 2011-01-23
What are your computer specs?
and from Terminal 
**alsamixer**, 
does it work?

---

### Post by northerndude81 on 2011-01-23
**alsamixer** give me:

> cannot load mixer controls: Invalid argument

Computer specs are (from manufacturer's website):

> Wind Top AE2220

&#8226; Intel ® Intel Core 2 Duo T6600 / Pentium dual core T4300/T4500 Processor
&#8226; Ubuntu 10.04
&#8226; 21.5" (16:9), 1920 x 1080, Full-HD Multi-Touch Panel
&#8226; 4G DDR2 Memory / 640 GB Hard Drive
&#8226; NVIDIA GeForce 9300 Integrated Graphic with 256MB VRAM

And here is the audio device:

> Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: Micro-Star International Co., Ltd. Device 4570
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

Any suggestions?

---

### Post by xc3RnbFO8P on 2011-01-23
Install the ALSA backport (if you haven't):
> sudo aptitude install linux-backports-modules-alsa-lucid-generic 
Edit the alsa-base.conf file: 
> sudo gedit /etc/modprobe.d/alsa-base.conf 
and add the line 
**options snd-hda-intel add model=mb31** 
save and restart the computer.

---

### Post by northerndude81 on 2011-01-23
Ok, I did both of those things, but the microphone STILL isn't working. :(

I hope you have some more ideas! Thanks for all your help so far....

---

### Post by northerndude81 on 2011-01-23
Just FYI, the last step, adding the line to the config file, actually disabled my sound altogether. Not only did the microphone not work, but the speakers didn't work, either. So I deleted the extra line and now things are backe to "normal," i.e. the speakers work but not the mic.

What's wrong here? :(

---

### Post by northerndude81 on 2011-01-24
Help!! I have to get into a conference via Skype in a few hours! If I can't get this mic working, I'm in trouble. :(

---

### Post by northerndude81 on 2011-01-24
Bump! Somebody please! I wish I had a commercial OS so I could just pay someone to fix this for me and be done with it.

---

