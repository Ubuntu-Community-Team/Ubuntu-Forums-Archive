---
title: "Ubuntu 9.10 Karmic Koala-No Sound"
date: 2009-10-31
forum: Multimedia Software
---

### Post by Gandalf_the_Grey on 2009-10-31
I just completed the upgrade to Ubuntu 9.10, and now I don't hear any sound.  My speakers are plugged in, the Ubuntu system volume is at 100%, and I still don't hear a thing from Totem, Rhythmbox, or SuperTux.  My sound card is a C-Media CM8738.

---

### Post by vor_lord on 2009-10-31
I have the exact same problem, same sound card.

Alsa picks up the sound card just fine, but the new sound preferences do not show it at all (only my onboard sound):

```

strongbad:home/brett> cat /proc/asound/cards
 0 [CMI8762        ]: CMI8738-MC8 - C-Media CMI8762
                      C-Media CMI8762 at 0xe800, irq 16
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ff8000 irq 22
strongbad:home/brett> cat /proc/asound/modules
 0 snd_cmipci
 1 snd_hda_intel

```

If I blacklist the on board sound, then only a dummy null output is available in the sound preferences.

Alsa seems fine with the cmedia, but for some reason the whole pulseaudio system and sound preferences don't see it.

[IMG]http://brettandbecky.net/images/sound_prefs.jpg[/IMG]

I did attempt both solutions for the second item listed on:
[http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html]("http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html"):
> 
Check that slmodemd is not running if you're seeing a dummy/null sink in the volume control applet. Arguably PulseAudio's module-udev-detect should allow the device instead of bailing when detecting it, and an approach is under discussion for future versions. In the meantime, you can either instead load module-detect in /etc/pulse/default.pa (or ~/.pulse/default.pa) or kill slmodemd.


If I load module-detect, then the sound preferences simply says "Waiting for sound subsystem" and I get no sound configuration at all.

I could not find slmodemd running, nor could I find it in the init subsystem, so I could not try that one.

I'm not really sure it is related, but if you only had a single sound card that was CMI, it would look just like this issue.

---

### Post by claud10 on 2009-10-31
Hi everyone,

I had the same problem in Kubuntu. Seems like pulse is not installed by default or it remains at an old version. Simply run

```
sudo apt-get install pulseaudio
```

Then, open Kmix (gnome volume control in Ubuntu) and make sure that Master, PCM and Speaker channels are ON.

The reinstall of the pulse sound server should have added a new entry in the Devices List found at System Settings->Multimedia, called "*Playback/recording through the PulseAudio Sound Server*". use this as default sound server and voilà.

That solved the problem for me (I repeat, in Kubuntu Karmic)

---

### Post by Gandalf_the_Grey on 2009-10-31
Solved!

How I got sound:

Run "alsamixer" in the terminal, then turn up PCM.

Problem solved!  :D

---

### Post by Gandalf_the_Grey on 2009-10-31
OK, not quite solved... :(

My YouTube videos now have sound, but it sounds like static, mixed with the tiniest bit of the original sound of the video.  If I download it to my computer, it still has the static.  This video sounds just fine under Ferdora 10.  Also, Pingus has some slight static on certain notes of the main menu soundtrack, and SuperTux just sounds like a motorboat.

At least my MP3 files now work... :)

claud10: PulseAudio already installed and latest version, PCM, Master, and Speaker all on.  No change in symptoms.

---

### Post by vor_lord on 2009-10-31
Gandalf,

For the overdriven (i.e. static sound) problem, check out the link I posted in my first post.  One of the items there might help you.

---

### Post by Gandalf_the_Grey on 2009-10-31
OK, found another simple solution.

I installed the package paman, then loaded the PulseAudio Volume Control.

I then turned up System Sounds to 100%, then loaded [http://www.youtube.com/watch?v=NRpTn75W9Dg](http://www.youtube.com/watch?v=NRpTn75W9Dg), and... NO STATIC!!!! :D  Pingus fixed, Totem fixed, YouTube fixed, etc.

Thanks for the help.

---

### Post by dmt0 on 2009-10-31
I just upgraded from jaunty and now have no sound at all.
It's an onboard card on nforce2 chipset.

When I do /sbin/alsa force-reload, I get this:

 lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dmt/.gvfs
      Output information may be incomplete.
Terminating processes: 3217lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dmt/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dmt/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dmt/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-usb-audio snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-usb-lib snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-usb-audio snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-usb-lib snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-deviceWARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
...
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.


Anyone's got a fix for that?

---

### Post by vor_lord on 2009-10-31
Well, simple solutions abound.  I did a hard reboot (i.e. not a restart) and the card appeared when I booted.](*,)

---

### Post by markackerman8@gmail.com on 2009-11-01
Hey Guys I am having real problems with sound too after a clean install of karmic. ARghhhhhh I have looked everywhere and tried all the troubleshooting guides with no success double arghhhhh

Everything that points to an output device only shows the"dummy" (WITH PADEVICECHOOSER or system/preferences/sound_preferences),

but when I:

ack@Titan:~$ gnome-alsamixer ... it shows "Realtec ALC268"

or
ack@Titan:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 0/1
Subdevice #0: subdevic

or
ack@Titan:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Subsystem: Hewlett-Packard Company Device 30cc
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

ANY SUGGESTIONS?????

---

### Post by salingova on 2009-11-02
I'm trying everything, but nothing helps. Koala doesn't seem to recognise any sound hardware. Pls help

---

### Post by fire_beast on 2009-11-02
I'm a little confused myself as to whats going on with Karmic's sound.  I upgraded yesterday from 9.04. I get absolutely NO sound from any of the programs that come with gnome/ubuntu, and nothing from internet radio/video sources.  my onboard sound card isn't seen in the volume preferences.  I have alsamixer with all outputs unmuted and turned up.  The computer does recognize my onboard when I do aplay -l.  and I have sound when I run mixxx 1.7.1, as it uses my onboard's secondary output @ 48000(4 channels: 2 for speakers, 2 for headphones) vs the onboard primary 2ch @ 44100.  so, could this be a sound config problem?  I've also notices A LOT of pulseaudio coming up in my conky log.  says "ratelimit.c (insert a number here, so far its been up to 124) events suppressed"  and "module.c module detect is predecated. Please us module-udev-detect!".  I may try a sudo init 0 and see if that knocks anything loose lol  Any help with this would be appreciated!

---

### Post by Gandalf_the_Grey on 2009-11-02
Have you installed the paman (PulseAudio Manager) package, and have you then turned up System Sounds on the PulseAudio Volume Control's Playback tab?

---

### Post by salingova on 2009-11-02
Yes, I did install paman from deb file I downloaded. I don't know whether I went to the same menu you have in mind to check the volume settings though. Is the PulseAudio Volume control the same thing as if you go to system/preferences/sound? If it is I don't know where to find a playback tab, there is only Sound Effects, Hardware, Input, Output, and Applications.
THX

---

### Post by 5nak3 on 2009-11-02
Hi there, I'm also having a similar problem in regards to sound in karmic. Unlike most of you my sound card was detected with no problems, however, I've found Karmic's volume manager much more complex than jaunty's.

Is there anyway to get Jaunty's sound applet/manager running in Karmic. I had complete control of headphones, PCM, master mono and master volume all from the applet in my taskbar. With Karmic however, I need to open terminal and run "alsamixer" as well and having had to install Pulseaudio's paman and all the related packages.

many thanks

---

### Post by Nausser on 2009-11-02
I have upgraded from 9.04 to 9.10 and also have no sound. I have tried all attempts at resolutions on this thread as well as others found elsewhere. I even upgraded my alsa per these instructions:

[http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/)

Still no prevail. I've installed paman and checked the volume controls. My issue is that my hardware does not show up at all in the sound prefs.

The two screen-shots are attached.

I think there are several cases like mine happening to people. I have an Acer TravelMate 2480 and have been happily using Ubuntu since Hardy. Never have I had sound issues where its completely gone.

Let me know if there is specific info you need from me.

Thanks!

---

### Post by dirkop on 2009-11-03
Hello!

After a clean installation of Ubuntu 9.10 the sound is working on my laptop. I figured out that after I started Skype 2.1 (beta) my output device is no longer available :( There is only the "Dummy"-output and I have no idea how to get my intern output device back.
So, I have sound as long as I do not start Skype.

---

### Post by VertexPusher on 2009-11-03
You can fix these issues by removing PulseAudio.

---

### Post by fire_beast on 2009-11-03
I've noticed that sound works fine when I boot into KDE, but not when I boot into Gnome.  I guess I can do all of my websurfing and media related things in KDE and use my specific DJ hardware in Gnome.  also, does anyone know why I have the option to boot either at login?  I was unaware of this feature on previous releases...and it isn't offered on my wife's laptop which got a fresh install of 9.10, where as mine was an update from 9.04.  Also, if one were to remove pulse audio, wouldn't we lose the ability to control sound via a well located volume control, or would we just have to use the alsa volume control instead?  just curious

---

### Post by ratcheer on 2009-11-03
> **5nak3 said:**
> Hi there, I'm also having a similar problem in regards to sound in karmic. Unlike most of you my sound card was detected with no problems, however, I've found Karmic's volume manager much more complex than jaunty's.



I agree, 100%. In Karmic, I am having to set the Pulse Audio volume up from zero for each individual application that uses sound. This is a major pain. Who the hell thought this would be a good idea?

Tim

---

### Post by uniden9 on 2009-11-03
I fixed my pulseaudio issue with videolan/ vlc, by editing the /etc/default/pulseaudio 
This may or may not fix your issues. But I too had no sound, and everything worked perfectly in 9.04

changing the:
# Prevent users from dynamically loading modules into the PulseAudio sound
# server. Dynamic module loading enhances the flexibilty of the PulseAudio
# system, but may pose a security risk.
# 0 = no, 1 = yes
DISALLOW_MODULE_LOADING=1

to 

DISALLOW_MODULE_LOADING=0

---

### Post by JS36 on 2009-11-03
> **uniden9 said:**
> I fixed my pulseaudio issue with videolan/ vlc, by editing the /etc/default/pulseaudio 
This may or may not fix your issues. But I too had no sound, and everything worked perfectly in 9.04

changing the:
# Prevent users from dynamically loading modules into the PulseAudio sound
# server. Dynamic module loading enhances the flexibilty of the PulseAudio
# system, but may pose a security risk.
# 0 = no, 1 = yes
DISALLOW_MODULE_LOADING=1

to 

DISALLOW_MODULE_LOADING=0

That worked for me, i have tried the other options too but this was the only that worked for me. Thanks alot :D

---

### Post by minhato on 2009-11-03
I upgraded my kubuntu 9.04 to kubuntu 9.10.
When I finished, I had not any sound from the web, amarok, spotify, system ... But the sound system appears to be correct.

Then I went to ubuntu forums and read that some people have a similar problem. I tried some solutions, but any of them worked.

Finally, I did that VertexPusher said
> You can fix these issues by removing PulseAudio.In my case:
```
apt-get remove --purge pulseaudio
```Then I reboot the system and that works for me. Now the sound system is OK.

(Sorry for my english, I'm from Galicia-Spain)

---

### Post by fire_beast on 2009-11-03
I updated to pulseaudio 1.0.21 and changed the etc/default/pulseaudio to allow module loading.  i seem to have sound now.

---

### Post by Gandalf_the_Grey on 2009-11-03
> **salingova said:**
> Yes, I did install paman from deb file I downloaded. I don't know whether I went to the same menu you have in mind to check the volume settings though. Is the PulseAudio Volume control the same thing as if you go to system/preferences/sound? If it is I don't know where to find a playback tab, there is only Sound Effects, Hardware, Input, Output, and Applications.
THX

It's under Applications>Sound & Video.

---

### Post by VertexPusher on 2009-11-04
> **fire_beast said:**
> I've noticed that sound works fine when I boot into KDE, but not when I boot into Gnome.
That's because Kubuntu does not use PulseAudio. As I said before, remove PA and your troubles will be gone.

> does anyone know why I have the option to boot either at login?
It seems you installed the kubuntu-desktop package at some point. It's possible to have both ubuntu-desktop and kubuntu-desktop installed side by side.

> if one were to remove pulse audio, wouldn't we lose the ability to control sound via a well located volume control, or would we just have to use the alsa volume control instead?
Yes, in Gnome you would have to use a different volume control, e.g. gnome-alsamixer. However, in KDE nothing would change.

---

### Post by stewie17 on 2009-11-04
[FONT=Trebuchet MS][SIZE=2]Hey all. I had everything working fine in jaunty and when I upgraded to karmic everything worked for the first half-hour, or so (after reboot). However, after I installed the first batch of updates I lost all sound. I don't know if files were re-allocated, or what, but after going through a half-dozen threads I found what might be the solution. That is to upgrade the **grub**. 

[html]$ sudo apt-get install grub2[/html]After that I went to **System>Preferences>Sound** and tested all sound devices and everything was working properly. This also got my [/SIZE][/FONT][FONT=Garamond][SIZE=2]**Logitech ClearChat PC Wireless**[/SIZE][/FONT][SIZE=2] headset to work, as well.
[/SIZE]

---

### Post by stewie17 on 2009-11-04
Where can I find the deb package for paman?

---

### Post by Gandalf_the_Grey on 2009-11-04
In the Synaptic Package Manager, search for it, or in the Terminal:

"sudo apt-get install paman"

---

### Post by rbolio on 2009-11-04
HA! purge pulse audio and it works 100%! don't forget to get a GUI tho.!

---

### Post by salingova on 2009-11-04
Still nothing for me, I tried removing pulseaudio which didn't do anything, but my audio settings disappeared. Grub upgrade nothing and paman noting either. I tried editing the pulseaudio file in /etc/default/pulseadio but did not help either. I am thinking of downgrading ubuntu, do you guys know whether it is possible to do it without having to reformat the partition?

---

### Post by coldsystem on 2009-11-05
try  this  :[http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala](http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala)

---

### Post by furoraest on 2009-11-05
I had very strange problem - i had sound after installation and it disappeared mystically some days later.
Even the soundcard was gone.
 I checked updates, didn't worked. Finally i followed hints on some forum and restarted alsa with "alsa force-reload".
It worked just perfect but after reboot it gave me same problem.
Finally i found a hint that slmodem disabling could help and it actually did it.
So there must be some kind of disunderstanding what is the right soundcard if slmodem is also loaded.

---

### Post by hughcrowther on 2009-11-05
you know what, all these sound problems get worse with every ubuntu release. I had sound too but no mic now cannot even play a cd or dvd, real player just crashes every time you put in a new url and movie player keeps asking for an unobtainable plugin. What the heck is going on ?

---

### Post by waltclay on 2009-11-05
> **coldsystem said:**
> try  this  :[http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala](http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala)
At the site linked, this command
```
 sudo apt-add-ppa repository: ubuntu-audio-dev/ppa 
```
not found. Can anyone correct it?

---

### Post by Wildscot on 2009-11-05
> **waltclay said:**
> At the site linked, this command
```
 sudo apt-add-ppa repository: ubuntu-audio-dev/ppa 
```
not found. Can anyone correct it?

You can install these by following the directions here: [https://launchpad.net/~ubuntu-audio-dev/+archive/ppa]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa")

I've yet to discover if this will help with my intermittent sound problems since an upgrade to 9.10. I've lost my volume control on the panel too and can't seem to get it back, there's just no entry in the 'Add to panel' dialogue. Oh well, that's for a different thread...

---

### Post by gillza on 2009-11-06
@OP, just out of curiosity, which kernel are you running now?  

There is a bug which results in grubs menu.lst not being properly updated and loads a wrong kernel. I had this issue and it manifested itself in the audio not working..

---

### Post by salingova on 2009-11-06
> **coldsystem said:**
> try  this  :[http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala](http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala)

still no success; I really don't know how to work this thing out, I've spend so much time trying already

---

### Post by mantisdolphin on 2009-11-06
Very basic but fixed sound on a multi-boot system this way: 

After Karmic upgrade, the old grub from another distribution on another partition was still booting the Jaunty kernel. 

Jaunty doesn't work with Pulse audio as well as Karmic does.  Sound was dead in Karmic upgraded Ubuntu with Jaunty kernel.

So I took the Karmic partition's menu.lst from /boot/grub and copied it to the old partition's /boot/grub, overwriting the old menu.lst.

After a reboot, sound worked in Karmic.  True Karmic kernel Pulsed audio bliss.

Now grub is, well, grubby on my system, but there's sound in a working Karmic.

---

### Post by debayanm on 2009-11-06
hi all,

I have a dell inspiron 1525, quite new, 2 GB ram 160 GB HDD, core 2 due T 5750 processor, 2 MB Cache, etc etc

I downloaded ubuntu 9.10 desktop version and ubuntu 9.10 netbook version..They are in ISO version..but when i am running them using DAEMON tools lite, and restarting system, they UBUNTU is just showing a small logo and after that , system is going black..

Plz help..

---

### Post by dkh503 on 2009-11-06
> **salingova said:**
> still no success; I really don't know how to work this thing out, I've spend so much time trying already
Didn't work for me either. Since I am using this computer as an audio workstation, this upgrade has been a monumental waste of time thus far. My fault for not checking this forum before upgrading; if I would have known so many users were having problems with audio under Karmic, I would not have bothered.

dave

---

### Post by kaapstorm on 2009-11-07
Thanks furoraest, that did the trick for me:

sudo alsa force-reload

My symptoms are the same as yours. Audio works when I boot up, and then a day or two later, PulseAudio "loses" my hardware. "lspci" shows it, "aplay -l" shows it. gnome-volume-control an paman can't see it, and show only dummy audio.

Unlike most of the posters on the thread, I really like the Karmic's audio control! I like that I can set different applications' volume, and that I have one master volume instead of hundreds of volume sliders for PCM, Master, Front, CD, etc. etc. etc. And Skype! Wow! The slog that it took to find exactly which sliders and checkboxes to tweak to get my microphone to work. Now I just select "Microphone 1" and set the input volume. What a pleasure!

So I'm sorry for the loads of people who are having trouble. I'm sure the people at Canonical/Ubuntu are feeling very guilty about your problems. But for those who persist, and manage to get PulseAudio working for them, there is, at least IMHO, a reward: finally a decent audio interface.

---

### Post by mefarmerdan on 2009-11-07
Until an hour ago, I had no sound on my laptop since I installed Jaunty three months ago and then upgraded to Karmic last week.  Don't think this is a "work around" but a "fix"--got the idea from this thread.  Thanks to all.

I installed linux-backport-modules-alsa.  Since I'm not really familiar with apt yet, i used the Synaptics Package manager.  Searched on "alsa" and found the backport.  Even the "cutesy" sounds for applications and failures now work.

Dan

---

### Post by dkh503 on 2009-11-07
This is my last attempt before chucking Karmic entirely. Apparently, one of the issues has to do with the Karmic vs Jaunty kernels. As one of the many posts I have found had me do, I ran 'sudo update-grub'. The script output indicates that I do indeed have the Karmic kernel(s) on my machine, [I have both the generic and realtime kernels installed] and that 'update-grub' has successfully updated the menu.lst. No errors, no permission issues, it plainly lists the new kernels that I have and reports that they have been successfully added to menu.lst. Upon further review, however,  menu.lst is NOT being updated and my machine is defaulting to my most recent Jaunty kernel the next time I start the machine (cold boot). I ran 'ls -l' to check on the timestamp, and the timestamp shows that I did indeed update menu.lst in the several minutes. I opened menu.lst in 'vi' and absolutely no mention of the existence of my v9.10 kernels is listed, and I can find no visible differences in the "new" menu.lst. I edited the file by hand to include the 9.10 kernels using the format for the 9.04 kernels, and damn near got it to work, but performance was unstable, I'm guessing because I don't know how to generate or locate the UUIDs for these new kernels. (BTW 'uname -a' reported that I was indeed running the Karmic kernel, I wasn't fooling myself). Running audacity for instance from the command line under these hacked kernel entries generated 'cannot open audio device' error messages, tho the program did open and run well enough to play .wav files, (first time ever I got any kind of audio output in Karmic) but it couldn't record sound without crashing the program, and the monitored sound while recording was ridiculously distorted. Sound preferences while under the Karmic kernel indicated that I do indeed have a soundcard installed (under the Jaunty kernels, like right now for example, all I get is "dummy output" and no recognition of any audio devices in my machine).  Any ideas on why update-grub is lying to me, or should I go to another forum? I am hoping to avoid a complete reinstall of the OS, as I would really like to get back to RECORDING MUSIC.

dave

---

### Post by fester225 on 2009-11-07
I had the same problem with 2 separate machines. Both were fixed by going to the master volume control icon on the top toolbar. The upgrade to 9.10 decided to turn on the mute function. I had to go to the master volume control to turn off the mute.

Having turned off the mute, one of the machines turned it on again in time for reboot.

---

### Post by karabashmi on 2009-11-08
Similar problem: No sound after update to 9.10.
Please help. Here is the info

1)aplay: device_list:223: no soundcards found...

2)lspci:
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
**00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)**
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

3) System->Preferences->Sound->Output gives only Dummy Output

---

### Post by musarraf172 on 2009-11-08
I am having a very bitter experience with ubuntu 9.10.on my IBM R51 2887 AE4 laptop.

9.04 worked flawlessly with any problem. Sound , wifi , booting time
everything was very good. But after 9.10 upgrade I had the following issue.

1. Can not boot with 2.6.31-14 kernel. The boot process does not end
while premounting local file systems.

2. Can boot with old 2.6.28-16 but synaptic touchpad does not work. It has conflict with ps2 mouse. ps2 or usb mouse is working. Sound hardware is not detected.Tried manual probing but without success.

3. Total system is jerky. Firefox stucks. Boot time is longer than 9.04..

4. If the default uspalsh theme is changed system does not boot.

5. got touchpad working by this work around : "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"

6. X server hangs when system is idol for a long time. If we change the console and again comeback tty7 then x is working again


Any help will be greatly appreciated.,,,,,,,,

---

### Post by salingova on 2009-11-08
> **dkh503 said:**
> This is my last attempt before chucking Karmic entirely. Apparently, one of the issues has to do with the Karmic vs Jaunty kernels. As one of the many posts I have found had me do, I ran 'sudo update-grub'. The script output indicates that I do indeed have the Karmic kernel(s) on my machine, [I have both the generic and realtime kernels installed] and that 'update-grub' has successfully updated the menu.lst. No errors, no permission issues, it plainly lists the new kernels that I have and reports that they have been successfully added to menu.lst. Upon further review, however,  menu.lst is NOT being updated and my machine is defaulting to my most recent Jaunty kernel the next time I start the machine (cold boot). I ran 'ls -l' to check on the timestamp, and the timestamp shows that I did indeed update menu.lst in the several minutes. I opened menu.lst in 'vi' and absolutely no mention of the existence of my v9.10 kernels is listed, and I can find no visible differences in the "new" menu.lst. I edited the file by hand to include the 9.10 kernels using the format for the 9.04 kernels, and damn near got it to work, but performance was unstable, I'm guessing because I don't know how to generate or locate the UUIDs for these new kernels. (BTW 'uname -a' reported that I was indeed running the Karmic kernel, I wasn't fooling myself). Running audacity for instance from the command line under these hacked kernel entries generated 'cannot open audio device' error messages, tho the program did open and run well enough to play .wav files, (first time ever I got any kind of audio output in Karmic) but it couldn't record sound without crashing the program, and the monitored sound while recording was ridiculously distorted. Sound preferences while under the Karmic kernel indicated that I do indeed have a soundcard installed (under the Jaunty kernels, like right now for example, all I get is "dummy output" and no recognition of any audio devices in my machine).  Any ideas on why update-grub is lying to me, or should I go to another forum? I am hoping to avoid a complete reinstall of the OS, as I would really like to get back to RECORDING MUSIC.

dave

Interesting, I was pretty sure that I was booting with the right kernel as well, so after I updated to the newest version of grub I thought that this solution would not work for me. I would like to try editing the file manually. Could you help me with that, or could you post a link to a different thread? THX

---

### Post by mefarmerdan on 2009-11-08
> ...I ran 'sudo update-grub'. The script output indicates that I do indeed have the Karmic kernel(s) on my machine, ...I opened menu.lst in 'vi' and absolutely no mention of the existence of my v9.10 kernels is listed, and I can find no visible differences in the "new" menu.lst. I edited the file by hand to include the 9.10 kernels using the format for the 9.04 kernels, and damn near got it to work, but performance was unstable, I'm guessing because I don't know how to generate or locate the UUIDs for these new kernels.Many of the suggestions you find in these fora may work for some people, but they tend to get others with subtlely different problems, which, however, exhibit similar systems, to start "easter-egging" rather than trouble-shooting.  That's where I think you are headed and why I'm jumping in.

First, the UUID does not refer to the kernel but to the device which contains the kernel.  In the old days the statement was:

root=hd(x,y)

now it's 

root=UUID=big string of numbers

Consider the following two entries made AFTER the "## End Default Options ##

title           Ubuntu 9.10, kernel 2.6.31-14-generic
uuid            c6f373b5-7550-447b-8c91-743429b96f6c
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=c6f373b5-7550-447b-8c91-743429b96f6c ro quiet splash 
initrd          /boot/initrd.img-2.6.31-14-generic
quiet


title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            c6f373b5-7550-447b-8c91-743429b96f6c
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=c6f373b5-7550-447b-8c91-743429b96f6c ro quiet splash 
initrd          /boot/initrd.img-2.6.31-14-generic
quiet

They boot the same kernel.  Just their titles are different.

My suggestion is go back to stable--hope you backed up your menu.lst.  Then in your favorite editor copy the stanza, like the above, to be the first listed in your menu.lst.  Then change the title, the vmlinuz and initrd.img to reflect the kernel you wish to run under that title.  Also make sure that the "groot" and "kopt" statements in the Automagic section have the same UUID statements as are in your kernel stanzas.

I think you're on the right track about the kernel thing.  I'm suspecting that the sound problem is associated with the alsa modules.  After you get stabilized, try the back port alsa modules.

Good luck.

Dan

---

### Post by dkh503 on 2009-11-08
> **mefarmerdan said:**
> Many of the suggestions you find in these fora may work for some people, but they tend to get others with subtlely different problems, which, however, exhibit similar systems, to start "easter-egging" rather than trouble-shooting.  That's where I think you are headed and why I'm jumping in.

First, the UUID does not refer to the kernel but to the device which contains the kernel.  In the old days the statement was:

root=hd(x,y)

now it's 

root=UUID=big string of numbers

Consider the following two entries made AFTER the "## End Default Options ##

title           Ubuntu 9.10, kernel 2.6.31-14-generic
uuid            c6f373b5-7550-447b-8c91-743429b96f6c
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=c6f373b5-7550-447b-8c91-743429b96f6c ro quiet splash 
initrd          /boot/initrd.img-2.6.31-14-generic
quiet


title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            c6f373b5-7550-447b-8c91-743429b96f6c
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=c6f373b5-7550-447b-8c91-743429b96f6c ro quiet splash 
initrd          /boot/initrd.img-2.6.31-14-generic
quiet

They boot the same kernel.  Just their titles are different.

My suggestion is go back to stable--hope you backed up your menu.lst.  Then in your favorite editor copy the stanza, like the above, to be the first listed in your menu.lst.  Then change the title, the vmlinuz and initrd.img to reflect the kernel you wish to run under that title.  Also make sure that the "groot" and "kopt" statements in the Automagic section have the same UUID statements as are in your kernel stanzas.

I think you're on the right track about the kernel thing.  I'm suspecting that the sound problem is associated with the alsa modules.  After you get stabilized, try the back port alsa modules.

Good luck.

Dan
Thanks Dan, real good info...turns out part of my problem lies in the 'update-grub' routine itself. Basically, it doesn't work. It reports that you have new kernels, it reports that it is updating menu.lst, but it is indeed lying to you. You have to rm the menu.lst, THEN run update-grub, it will fail to find a menu.lst, ask you if you want to generate one, you hit 'Y' and voila you have a new menu.lst with your new kernel(s). The new generic kernel made my system usable (at least it recognized I do indeed HAVE a soundcard and it would at least play mp3's and .wavs and default system sounds) but the new rt kernel crashed mightily at boot three consecutive times. So I am back to a vanilla install of Karmic (which apparently has no problems with basic audio functions once you reinstall gstreamer for mp3's and the flash-plugin-installer for Firefox), and some time in the future when I have a bit more positive attitude, and I have time that I don't know what else to do with, I will attempt to run serious audio apps under Linux.

---

### Post by paviel on 2009-11-08
[email]markackerman8@gmail.com[/email]

try 

sudo gedit /etc/modprobe.d/blacklist-modem.conf
blacklist snd_hda_codec_si3054

save and reboot

---

### Post by undegaussable on 2009-11-08
I was about to pull my hair out, I tried literally everything I found... new grub2 installation, made sure I am running the new kernel, removed PulseAudio, reinstalled PulseAudio, installed Pulse Audio sound control, installed backport ALSA, restarted ALSA...

At some point, something worked, or maybe something was never broken, because I found out that the front audio jack of my computer works... just nothing comes out of the back jack!  If anyone knows how or why this is happening, I would appreciate an explanation... I'm totally baffled, but at least now I do have **some** sound!

**UPDATE**:  There are four audio output jacks on the back of my Dell Dimension 5150... I had it plugged into the black one and it worked fine in Ubuntu 9.04... now only the yellow and blue ones get any output.  I can't explain this, I don't even know what the colors mean... but whatever, I have sound now because I plugged into the yellow one!  Go figure.

---

### Post by antipode888 on 2009-11-08
My M-Audio Revolution 7.1 sound card worked beautifully in 9.04.  With fresh install of Karmic Koala, I suddenly can't capture from the microphone.  I tried everything.  And no, it isn't the mixer levels.

When I boot a 9.04 amd64 live CD, the sound card works flawlessly.  I can use the Sound Recorder and play back the sound I just recorded.  Without changing anything, I boot the 9.10 live CD and the Sound Recorder shows no recording level (and nothing is recorded).  I've tried clicking every checkbox and sliding every slider to no avail.

What finally worked on my 9.10 desktop?  (As others in this thread have reported.)

sudo apt-get purge pulseaudio

Not an expert on sound stuff, but everything seems fine for my purposes without pulseaudio.  I can paste all that alsa-info.sh stuff if anyone's interested.

---

### Post by SyberKowboy on 2009-11-09
Did the trick for me too.

---

### Post by Pappy-D on 2009-11-12
If this thread is still open, I have one comment.MY audio disappeared with upgrade to Karmic. I tried all the suggestions I could find with no solution. However on this thread earlier someone asked what kernal was listed in menu.lst. I checked mine and found out that I was still using the 2.6.28-13 Kernal. I ran grub-update. It found the new kernal and said that menu.lst was updated. It was not changed. I had to rename menu.lst and rerun grub-update. Then in order to get my dual boot stuff I copied from the new menu.lst into the backup and renamed again. I hope that is clear. I now have sound. 
Duane

---

### Post by zap.iso on 2009-11-18
so i was having problems with pulseaudio back in 9.04 (caused TF2 to quit randomly), so i switched to OSS and it fixed everything. 

i decided to try alsa and pulse again when i upgraded to karmic now that i dont really play TF2 anymore, but I ran into all the problems everyone here was getting, and none of the fixes were working.

long story short, back to OSS and everything is working fine.

if anyone is having trouble with pulse and alsa and just cant get it to work, i'd really reccomend just switching to OSS.

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by 3bobbo3 on 2011-04-26
Since I always make use of years old threads for fixing some quirky pulseaudio or ALSA issues, I'm not afraid to ghost this one and fully prepared for the consequences!

[necro mode]
Now, I just fixed my month-long fixathon, for a cmi8783 soundcard. Turned out it was a silly option on the cards own interface.
The "output" option had only a "mute" switch, in kMix as well as in alsamixer. Sure enough I didnt want my output to be muted, so after I had dicovered this I made sure to set it to "unmute".

Of course this switch is no audio channel, hence cant be muted. It was the direct control for allowing output from the card or not, duh!

So before tearing apart all your config files and messing up the whole sound system, try this simple trick. Maybe you "unmuted" it somewhere on the way and forgot about it.
[/necro mode]

I hope this will save some hours for someone, good luck!

---

