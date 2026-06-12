---
title: "need help diagnosing sound problems ubuntu 10.04"
date: 2011-01-16
forum: Multimedia Software
---

### Post by banana jack on 2011-01-16
So I installed ubuntu 10.04 with emc2 from emc's website and am running it side-by-side with xp. Even when I had 10.10 installed for a little bit, the speakers didn't work. Nothing's muted, I've checked already. Speakers don't work, but external speakers/headphones do. I tried the Comprehesive Sound Problems Solutions Guide, and I got to step 3. I'll go ahead and tell you what I got. 

samuel@samuel-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

samuel@samuel-desktop:~$ lspci -v
...
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: IBM Device 02f6
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d01c0000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
...

(I'm assuming that's my sound card. I'm...not the best with computers. To say the least. Born and bred windows, and nobody i know uses linux or is even good with computers)
So I went to [[SIZE=2]http://www.alsa-project.org/alsa-doc/[/SIZE]]("http://www.alsa-project.org/alsa-doc/") and couldn't find my sound card on there. So I skipped over that and went to step 4, but I didn't know what module I had and I wasn't sure how to find out, unless it's part of step 3.

but I did
samuel@samuel-desktop:~$ sudo modprobe snd-
Display all 212 possibilities? (y or n)
snd-ac97-codec           snd-hdsp                 snd-seq-midi-emul
snd-ad1816a              snd-hdspm                snd-seq-midi-event
snd-ad1848               snd-hifier               snd-seq-oss
...
...
one showed up: snd-intel8x0 that I recognized from when I was searching for the driver on alsa's page, so I tried that:
samuel@samuel-desktop:~$ sudo modprobe snd-intel8x0
WARNING: All config files need .conf: /etc/modprobe.d/emc2, it will be ignored in a future release.

I didn't know what that meant. And that's the extent of my abilities, right there.

---

### Post by BicyclerBoy on 2011-01-16
You have very well & you have tried..

The warning is about the change with file extensions..

All files in the modprobe.d folder (and others) need .conf extension.

You could try renaming your emc2 file to emc2.conf
or copying emc2 into sound.conf

I would have thought your modprobe option should be set  /etc/modprobe.d/sound.conf depending on your card.  The general format is: 
 options snd-hda-intel *OPTIONS*

OPTIONS is what you found from modprobe..

Personally I would upgrade the alsa modules from ubuntu audio-dev ppa.

The (super)user "lidex" is the sound guru..
His (or her ? ) advice is better than mine.

---

### Post by banana jack on 2011-01-16
to be quite honest, i didn't understand a lot of what you just said. I tried to rename my emc2 file to emc2.conf, but it wouldn't let me for some reason (if i right-click, the option is faded)
Then I just googled what you said and clicked on the first thing that popped up and followed the instructions to upgrade alsa modules from 1.0.21 to 1.0.23. We'll see if that has any effect.

this popped up sometime in the middle of it:
cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

then later on this:
samuel@samuel-desktop:~/alsa-utils-1.0.23$ sudo make
make: *** No targets specified and no makefile found.  Stop.
samuel@samuel-desktop:~/alsa-utils-1.0.23$ sudo make install
make: *** No rule to make target `install'.  Stop.

i don't know if they're something to worry about or not. Bu I think i got through it all okay, now it's time to find out.

---

### Post by BicyclerBoy on 2011-01-16
To be quite honest neither did I ..
Well I don't know what emc is except from an electrical/electronic engineering context. 

[http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240)

If you follow the bit about getting alsa you can't do any damage.

The /etc/modprobe.d/*.conf files are read-only to users.
You need sudo access.


But if your external speakers work then you probably just need to select the correct output device in System/Preferences/Sound/ output tab  pick an output & unmute..

These is a gnome applet to do this from menu bar somewhere..

---

### Post by BicyclerBoy on 2011-01-16
[http://www.spinics.net/lists/alsa-devel/msg39182.html](http://www.spinics.net/lists/alsa-devel/msg39182.html)

Your audio device is/was broken in kernel 2.6.36. This kernel should not be available to you without adding another ppa.
That kernel could be the std one with 10.10 so stay at 10.04.

What kernel are you running ?
uname -r

---

### Post by banana jack on 2011-01-16
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
That's where I got it from.

emc is just a program that drives the stepper motors on a cnc machine. (which is a milling machine controlled by computer)

samuel@samuel-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jan 16 2011 for kernel 2.6.32-122-rtai (SMP).
So i guess it worked, even though the steps it told me to take to check if it worked or not, didn't work.

well i can't get sudo access unless i do it through terminal right? I don't know how to change the extension of a file through terminal.

and i only have one output device right now, and it's not muted. it's just that i discovered that if i plug in headphones, all of a sudden the sound works. sound works when i'm running windows, too.

Well...i guess updating alsa didn't work.

---

### Post by BicyclerBoy on 2011-01-16
I do know what CNC machines are..

I've seen that alsa link...that's the hard way, compiling from source.

If you use the ppa in the XBMC link you get all package management benefits.

Could be that upgrading alsa breaks your audio more, but the patches may have been submitted !

sudo privileged access can be done thru' terminal & should be used only as necessary.

Have you installed & tried the gnome-alsa-mixer ??

---

### Post by banana jack on 2011-01-16
this is from the xbmc link.

samuel@samuel-desktop:~$ add-apt-repository ppa:team-iquik/alsa ppa:team-xbmc
Error: must run as root
samuel@samuel-desktop:~$ add-apt-repository ppa:ubuntu-audio-dev/ppa
Error: must run as root
samuel@samuel-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
samuel@samuel-desktop:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
samuel@samuel-desktop:~$ apt-get install linux-alsa-driver-modules-$(uname -r) --force-yes
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
samuel@samuel-desktop:~$ 

no i haven't, i've never heard of it and have no idea how to do it. But I'm all for the idea!

---

### Post by BicyclerBoy on 2011-01-16
Do you know anything about package management ?
aptitude
apt (apt-get)
synaptic

The software package management system is one of the key differences in Ubuntu linux & windoze.

This one of the best features of most linux distributions..

It is easier to add a new ppa via terminal "sudo add-apt-repos.." than using synaptic.

Synaptic package manager Gnome desktop menu:System/Administration/Synaptic

you need your sudo password.
click reload
search for gnome-alsamixer
tick install .

---

### Post by tjones00 on 2011-01-16
With Ubuntu linux the sudo prefix is required to perform administrative tasks in the terminal.

Any system modification that is not contained to your /home/user/ directory pretty much requires administrative (root) privileges. The old school term for administrative user/account in linux is root.

When working from a terminal use sudo before the command. An easy way to remember this is SuperUser DO = sudo although that's not what sudo stands for.

If you want to run a GUI application with administrative privileges use the gksudo command instead of sudo (for a gtk/gnome environment). You can launch GUI apps with sudo but it's not recommended.

eg. to launch the file manager (nautilus) with administrative rights to copy/paste/rename/move system files type the following in a terminal.

gksudo nautilus

An easy way to remember this is GraphiKal sudo and being new to linux having an file manager with administrative rights will help you modify system files until you learn the terminal commands.

---

### Post by banana jack on 2011-01-16
no, i don't know anything about package management... do you by chance have any links to someplace that just has a huge intro to linux? because i kinda feel bad that i can hardly follow anything you're telling me. edit. just kidding, i've found some myself i just need to read them. who knew, this forum has an absolute beginners section!

i assume you were telling me to get synaptic? i used samuel@samuel-desktop:~$ sudo apt-get install synaptic to do that, because when i went into aptitude i couldn't understand what was going on. it said synaptic is already the newest version,

all right i got gnome alsamixer, now i'm not quite sure what i do with it. i opened it up and a bunch of things have 'mute' checked, so i unchecked them all, just to see if it had anything to do with my sound problem. Nope.

---

### Post by BicyclerBoy on 2011-01-17
Synaptic is the Ubuntu Gnome GUI package manager.
It is always installed.

apt-get etc is the terminal text mode package manager
aptitude is an interactive text mode package manager.. 

Check all volume controls for level & mute..should be about 18 of them..some are inputs.

---

### Post by banana jack on 2011-01-17
yyeeeeaaaaahhhh!!! That did it!!! Thank you, sir!!!
'mono' was all the way down, i'm pretty sure that was the problem.
really though, thanks a ton for all your help.

---

