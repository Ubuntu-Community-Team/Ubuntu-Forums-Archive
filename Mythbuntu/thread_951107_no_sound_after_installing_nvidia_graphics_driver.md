---
title: "no sound after installing nvidia graphics driver"
date: 2008-10-17
forum: Mythbuntu
---

### Post by skaggapa on 2008-10-17
The title pretty much says it all. I have also switched back to mesa(the ones you get before you get a chance to install nvidia) drivers and now i get sound.

Im running hardy with the following version of mythtv 
mythtv:
  Installerad: (ingen)
  Kandidat: 0.21.0+fixes16838-0ubuntu3.1
  Versionstabell:
     0.21.0+fixes16838-0ubuntu3.1 0
        500 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/multiverse Packages
     0.21.0+fixes16838-0ubuntu3 0
        500 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/multiverse Packages

The logs say

AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...

Dont mind the no video this is with mesa driver. I get video with nvidia driver.

Anyone? I havent found anything googling this. Im not even trying digital audio just simple rca to my tv that only have two speakers.

cheers
Anders

---

### Post by Whiplash78 on 2008-10-21
I'd like to know what's going on with this too.  I'd wager if I did the same thing installing the VESA drivers, I'd get audio also.

---

### Post by dotnick on 2008-10-26
I'm having the same issues.  I have the ACL888 chipset that show up as HD Nvidia.  When I use the "nv" driver for video, my sound is fine (using snd-hda-intel) but when "nvidia" is used for video my sound disappears.

EDIT:  I had no sound problems using the same hardware in 8.04.  These problems only occur for me in 8.10.

---

### Post by dotnick on 2008-10-27
I'm going to downgrade my nvidia driver from nvidia-glx-177 to nvidia-glx-173.  Hardy used 169, but it's not available in my current repositories... so if this doesn't work out, I'll search for the 169 version.  I'm at work right now, so I'll have to check it tonight to see if it works.

---

### Post by dotnick on 2008-10-27
No luck with an earlier driver.  However, I'm still convinced it's a driver issue.  I've reverted back to the 2.6.24 kernel from Hardy, and video and sound work fine.  I only have problems with the new 2.6.27 kernel.  Also... I couldn't try the 169 nvidia driver with the new kernel because the new kernel is a "xen" kernel and it is not supported.

This is not a good solution... but for now, using the 2.6.24 kernel seems to be my only solution.

I hope this is resolved soon.

---

### Post by Caps18 on 2008-10-28
It might be a long-shot, but have you tried changing the soundcard that MythTV uses to /dev/dsp2 or /dev/dsp1?  (It's in the main frontend program and usually is set to default).  I had to restart after I made that switch for it to work.  I am using 7.10 and a nVidia 6600 (6800?).

I know I had some issues getting both video and sound to work right, but my system is fine now.

---

### Post by dotnick on 2008-11-19
I decided to give it one more shot with the live cd only.

On first bootup... the OSS driver is used for nvidia so I update that using the hardware manager and a quick logout to kick in the proprietary drivers.

I pull up two consoles... 1 for playing a music file, the other for looking at which modules are used and alsamixer.

Initially all my drivers are loaded.  (snd-hda-intel and nvidia to be precise).  nvidia is used by 26 other modules and snd-hda-intel shows zero at this point).

I start playing the audio file.
snd-hda-intel is now used by 4 other modules.
mplayer shows that there was a problem connection to pulseaudio so it dropped back to Alsa 48000 Hz.

(so far no sound)

I open alsamixer (as a normal and as a super user).  I turned up the surround sound, master, and PCM columns and made sure that 00 was under them instead of MM.  They are not muted.  Still no sound.

I edit /etc/modprobe.d/alsa-base so that  "options snd-hda-intel model=6stack-dig" is added.

Quick restart of alsa (/etc/init.d/alsa-utils restart)

No sound.  This is a Realtek ALC888 chipset that shows up as Nvidia.  Even the aplay -l shows up correctly.

only /dev/dsp exists... dsp1..dsp2...etc do not.

Like I said earlier.  This was just with the live cd.  It was not installed on the hard drive.  So, in my opinion, this problem was shipped with the release.  And I also am just looking for the 2 RCA jacks to my TV.  Nothing fancy.

---

### Post by dotnick on 2009-03-28
I've made a revelation with my problem.  Using the new Jaunty Beta, I've found that my nvidia driver and sound card do actually work at the same time.  Great news right?  well, let me tell you about my setup.

hdmi output to tv and and rca cable from a single output of the sound card to the red/white jacks on the tv.  

when i do a ctl+alt+1 to a virtual terminal.... ta da, my sound is there, even when my graphical login is running.  

the one thing that is different that i didn't have before, is a set of plain jane computer speakers hooked up to another output of the sound card.  results:  THOSE SPEAKERS WORK!!!!

i still don't know why i can't get sound out of the tv (while watching the program).  i've tried switching around the plugs out of the sound card with no luck, but at lease i can get sound now.  it's a step in the right direction.

i'm going to try this with intrepid first... and if that doesn't work, upgrade to jaunty beta.  i'm tired of having subpar support for my gyration remote :-/ ....

---

### Post by jyavenard on 2009-03-28
I'm guessing you're connecting your video using a DVI or HDMI cable ?

The issue comes with the EDID returned by the TV telling your nvidia card that it supports sound via the video port.

I've seen this happening on my Sony LCD.

The solution was provided on the nvidia forum and sent again on the mythtv distribution list.

The idea on how to make it work is rather simple.
Download the EDID from your TV using the nvidia-settings application. Edit the binary file to remove the bits about sound and use that EDID in your xorg.conf file.
Read this:
[http://forums.nvidia.com/lofiversion/index.php?t88272.html](http://forums.nvidia.com/lofiversion/index.php?t88272.html)
and this:
[http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI](http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI)

you need to use the utility provided by the two links above:
[http://analogbit.com/node/23](http://analogbit.com/node/23)
to remove the extension field of the edid...

BTW, if you use my ubuntu repository, you can get much more updated mythtv packages for your hardy distribution, as well as VDPAU support.

[http://avenard.com/media/Ubuntu_Repository/Ubuntu_Repository.html](http://avenard.com/media/Ubuntu_Repository/Ubuntu_Repository.html)

---

### Post by dotnick on 2009-03-28
Thank you for the update... this is the first time i've seen any of this.  I'll try it soon.

---

