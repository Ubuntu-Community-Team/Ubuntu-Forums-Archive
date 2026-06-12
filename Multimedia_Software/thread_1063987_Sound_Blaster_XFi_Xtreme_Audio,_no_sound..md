---
title: "Sound Blaster XFi Xtreme Audio, no sound."
date: 2009-02-08
forum: Multimedia Software
---

### Post by Snufkin UK on 2009-02-08
This is make or break for me, need audio, and I do not want to replace my soundcard. How do I get it working in Ubuntu 8.10?

Tried installing XFi drivers from the guide but to no avail.

Thanks ina dvance.

---

### Post by DiegoBretti on 2009-03-03
> **Snufkin UK said:**
> This is make or break for me, need audio, and I do not want to replace my soundcard. How do I get it working in Ubuntu 8.10?

Tried installing XFi drivers from the guide but to no avail.

Thanks ina dvance.

To fix this problem install the following commands:

=> sudo killall pulseaudio
=> sudo alsa force-reload

and then go to "System > Preferences > Sound" and change everything to ALSA.

To fix 2.0 to 5.1 put this:

=> sudo gedit /etc/pulse/daemon.conf

Go down to the line that says "default-sample-channels = 2"
Change it so it looks like the following:
"default-sample-channels = 6"
Save and exit.

After you reboot, test your sound using:

=> speaker-test -Dplug:surround51 -c6 -l1 -twav

---

### Post by DiegoBretti on 2009-03-23
Snufkin UK, It works?

---

### Post by bseege on 2009-03-25
Hello,

I have the same sound card and also had no sound.
I didn't install any drivers but your commands

=> sudo killall pulseaudio
=> sudo alsa force-reload

made it work. Thanks for that ^_^

However it seems I have to repeat these commands after every reboot. Do you have any idea how I can change it so I don't have to? Maybe I could put it into some sort of script and run it on every boot?

---

### Post by Taus on 2009-03-25
sheesh! does this mean that someone actually made x-fi work in ubuntu!? wooohoooo! i have been struggling with that for ages!

have any of you guys made it work with spdif as well?

---

### Post by bseege on 2009-03-25
what's spdif?

---

### Post by Taus on 2009-03-26
it's the digital output of soundcards - i use coax to connect my x-fi to my DTS receiver. works awesome for dvd movies... in xp or vista that is. never got it working in ubuntu. *cries*

it might be what is also called "passthru" - not sure tho - but i think it's the same

---

### Post by Taus on 2009-03-26
i tried to install the xfi drivers from creative with no luck as well.

after that i tried to run the commands in this post. But i still don't get any sound from my xfi.

any of you know a guide i could try to follow?

any help would be very much appreciated - i'd love to watch a dvd movie with 5.1 sound in ubuntu.

---

### Post by bseege on 2009-03-29
Did you also set the audio settings to alsa? Maybe it's still set to your old sound card.

Sometimes those commands don't work on first try.

---

### Post by DiegoBretti on 2009-03-30
> **bseege said:**
> Hello,

I have the same sound card and also had no sound.
I didn't install any drivers but your commands

=> sudo killall pulseaudio
=> sudo alsa force-reload

made it work. Thanks for that ^_^

However it seems I have to repeat these commands after every reboot. Do you have any idea how I can change it so I don't have to? Maybe I could put it into some sort of script and run it on every boot?

You try?

"and then go to "System > Preferences > Sound" and change everything to ALSA." ?

---

### Post by bseege on 2009-03-30
> **DiegoBretti said:**
> You try?

"and then go to "System > Preferences > Sound" and change everything to ALSA." ?

correct, to be precise I can choose either 
"ALSA - Advanced Linux Sound Architecture"
or 
"X-Fi Extreme Audio [SBxxxx] CA0106 (ALSA)".
Both works.

---

### Post by Taus on 2009-03-30
Thanks for your replies guys.

i got the sound working with the analog outputs. but i can't seem to figure out how to use s/pdif.

---

### Post by SnackBoxAcid on 2009-03-30
> i got the sound working with the analog outputs. but i can't seem to figure out how to use s/pdif

I'm wondering if it is even possible with these cards.  I can't seem to find anyone who can say that optical audio out on these X-Fi cards (Xtreme audio aside) actually works in Ubuntu.

I already returned the "Xtreme (ahem) Audio" and bought a Titanium but I am not opening it until I know if optical audio is working.

---

### Post by DiegoBretti on 2009-04-04
> **Taus said:**
> Thanks for your replies guys.

i got the sound working with the analog outputs. but i can't seem to figure out how to use s/pdif.

You are welcome ;)

---

### Post by wombil on 2009-04-04
I also had similar trouble but with advice from EYE 208 I just disabled onboard sound in bios and all ok.

---

### Post by SnackBoxAcid on 2009-04-04
> **SnackBoxAcid said:**
> I'm wondering if it is even possible with these cards.  I can't seem to find anyone who can say that optical audio out on these X-Fi cards (Xtreme audio aside) actually works in Ubuntu.

Well, I had some success.  I finally found a review on amazon.co.uk where someone said that optical audio works with Linux, using NullHead's guide ( [http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001) ).  Using that same guide, I was finally able to get optical audio to my Z-5500's.

I had to upgrade to Intrepid from Hardy, but following the guide it worked right away.  

The downside is that it is stereo only, so that a bit of a kick in the pills.  But the 6 channel direct connections stills sounds better than the onboard AC97 did, so I am still somewhat ahead of the game.  At least, I'm telling myself it sounds better.  "It's real to me, damnit!!1"  ;-)

---

### Post by goofeyfoot on 2009-06-20
I also have the Soundblaster Extreme card and I tried what was said above regarding the force of ALSA.  Here is what I got when I tried the force Alsa thing in the terminal.

michael@michael-desktop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
michael@michael-desktop:~$ 

What should I do?  I would really like to get this Soundcard working.  It has been years now.  Idon't know alot about Linux but I can work commands if someone tells me what they are.

Thanks.

Michael

---

### Post by ikt on 2009-06-21
> **goofeyfoot said:**
> I also have the Soundblaster Extreme card and I tried what was said above regarding the force of ALSA.  Here is what I got when I tried the force Alsa thing in the terminal.

michael@michael-desktop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/michael/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
michael@michael-desktop:~$ 

What should I do?  I would really like to get this Soundcard working.  It has been years now.  Idon't know alot about Linux but I can work commands if someone tells me what they are.

Thanks.

Michael

kt@ikt-omg:~$ sudo killall pulseaudio
[sudo] password for ikt: 
ikt@ikt-omg:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ikt/.gvfs
      Output information may be incomplete.
Terminating processes: 3440lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ikt/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ikt/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ikt/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-usb-audio snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-usb-lib snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-usb-audio snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-usb-lib snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
ikt@ikt-omg:~$ 

sounds like we're close but no cigar :(

Anyone able to help?

---

### Post by andrew13321 on 2009-08-16
BUMP Last two replies are my problem.

---

### Post by lenkyroy on 2009-08-26
ok i'm very new to linux computers on a whole but i followed this tutorial [http://www.moobash.com/Blog/?p=815](http://www.moobash.com/Blog/?p=815)  to set up my x-fi surround 5.1 usb card right now i'm playing a .mkv movie in mplayer and all speakers play except center speaker and sub.....i see no volume control for the x-fi 5.1 can anyone help? please (step by Step since i'm new to linux please)

---

### Post by UAnovice on 2009-09-15
no sound from SB X-Fi
tried the steps, reboot 
no playback, but an endless loop saying

ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM plug-surround51
Playback open error: -2,No such file or directory
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM plug-surround51
Playback open error: -2,No such file or directory
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM plug-surround51
Playback open error: -2,No such file or directory

Then
xx@ubuntu:~$ sudo killall pulseaudio
[sudo] password for xx
xx@ubuntu:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/xx/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/xx/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

Conclusion: I'm lost

---

### Post by ikt on 2009-09-18
at this stage I am eagerly awaiting the beta of ubuntu 9.10 (which is when 9.10 will be installed on this pc) which includes alsa support for sound blaster x-fi cards at long last :)

[http://www.phoronix.com/scan.php?page=news_item&px=NzI3MA](http://www.phoronix.com/scan.php?page=news_item&px=NzI3MA)

> Takashi will be merging this into the mainline ALSA code-base soon so that it will appear in the next Linux kernel, which will be Linux 2.6.31. Finally there is an ALSA driver to provide support for the Creative Labs Sound Blaster X-Fi sound cards, which should begin appearing in desktop Linux distributions this fall.

---

### Post by UAnovice on 2009-09-20
Well, after messing everything up with alsa, oss, pulseaudio and trying umpty times, I swallowed the pill and did a clean install, good training for a novice.
Then I went trough the process of upgrading to alsa 20, well described on some post.
Now I have 2 speakers working out of 6 or something, no surround so far, but my radio channel streams are back.
So, if somebody can give me a couple of additonal speakers working instead of just humming, that would be great, could actually start looking for dvd player soft.:guitar:

---

