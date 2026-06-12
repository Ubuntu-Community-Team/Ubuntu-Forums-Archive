---
title: "Ubuntu 11.04 sound problems"
date: 2011-06-17
forum: Multimedia Software
---

### Post by Gushter13 on 2011-06-17
Ever since the Ubuntu 11.04 came out I've had trouble with sound on that version. I know my PC may be outdated, but I never had any problems on the previous versions.

My problem is this:

When I play any kind of audio (either MP3 or sound from a video) the sound start to stutter or crackle every half a minute or so. I may be just me, nut i think that the more I use my PC the more frequent the stuttering is. It's so annoying!

I've tried many things:

I did an upgrade from 10.10, a clean install, tried other variants, tried using ALSA drivers, tried changing pulseaudio buffering values in the daemon file, but to no avail! Also I've noticed that I don't have any problems on fedora 15. Any ideas? :confused: :confused: :confused:

I really hope that my soundcard isn't becoming unsupported! I'm using a Realtek AC'97 soundcard that is integrated on my Asus A8N-SLI motherboard.

---

### Post by lidex on 2011-06-18
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Gushter13 on 2011-06-18
The script doesn't seem to give me the link to the log.


I get this output:

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at 
Please inform the person helping you.

---

### Post by lidex on 2011-06-18
Just select n to save to your /tmp folder and upload here as an attachment.

---

### Post by Gushter13 on 2011-06-19
I got the script to upload!

Here's the link:

[http://www.alsa-project.org/db/?f=94fe70614687193763400af5b67f2fb91998a3a1](http://www.alsa-project.org/db/?f=94fe70614687193763400af5b67f2fb91998a3a1)

---

### Post by Gushter13 on 2011-06-19
Could the problem be caused because I'm running 32-bit version on a 64-bit architecture?

---

### Post by Gushter13 on 2011-06-19
I've tried everything from this thread and to no avail!

[http://ubuntuforums.org/showthread.php?t=1759570](http://ubuntuforums.org/showthread.php?t=1759570)

---

### Post by Gushter13 on 2011-06-19
Double post ... sry -_-

---

### Post by lidex on 2011-06-19
```

alias snd-card-0 snd_intel8x0
alias sound-slot-0 snd_intel8x0
alias snd-card-1 snd_hda_intel
alias sound-slot-1 snd_hda_intel
alias snd-card-2 snd_mpu401
alias sound-slot-2 snd_mpu401
```
Add that block of text to alsa-base.conf, save and reboot.
To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by Gushter13 on 2011-06-19
Didn't work. Somehow i think that it's linked to the kernel load, because when the pc is only playing music, the stuttering seems less frequent

---

### Post by imsushantjain on 2011-06-29
> **lidex said:**
> ```

alias snd-card-0 snd_intel8x0
alias sound-slot-0 snd_intel8x0
alias snd-card-1 snd_hda_intel
alias sound-slot-1 snd_hda_intel
alias snd-card-2 snd_mpu401
alias sound-slot-2 snd_mpu401
```
Add that block of text to alsa-base.conf, save and reboot.
To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```


Hi Lidex, i need your advice

i have 5742z, but the output from speaker is not upto mark.
this is the link i got after uploading info to alsamixer
[http://www.alsa-project.org/db/?f=0620d2470e90bab1b2144e9aafb1db47678289a6](http://www.alsa-project.org/db/?f=0620d2470e90bab1b2144e9aafb1db47678289a6)

---

### Post by imsushantjain on 2011-06-29
i mean Acer 5742Z

and you can see the configuration at [http://support.acer.com/acerpanam/notebook/2010/Acer/Aspire/Aspire5742Z/Aspire5742Zsp2.shtml](http://support.acer.com/acerpanam/notebook/2010/Acer/Aspire/Aspire5742Z/Aspire5742Zsp2.shtml)

please do suggest some good drivers as well

---

### Post by lidex on 2011-06-30
> **imsushantjain said:**
> i mean Acer 5742Z

and you can see the configuration at [http://support.acer.com/acerpanam/notebook/2010/Acer/Aspire/Aspire5742Z/Aspire5742Zsp2.shtml](http://support.acer.com/acerpanam/notebook/2010/Acer/Aspire/Aspire5742Z/Aspire5742Zsp2.shtml)

please do suggest some good drivers as well

You added the model=acer-aspire to alsa-base.conf, remove it please. Now update your kernel. You're using 2.6.38-8 and I believe 2.6.38-10 is available.

---

### Post by Heretic Zed on 2011-07-19
I'm having the same problem with my laptop, but it only started in the past few weeks.  up until then my sound was working fine.  Now, after a restart the sound plays fine for a while, the built in controls on my laptop work fine, then for no apparent reason I change songs and from then on I get garbled music.  If I close the player and wait a while the problem fixes itself for an indeterminate amount of time before the problem starts again.

Additionally, movie player no longer functions, sound will play but the window for the program itself will not display, preventing any play list editing or video.  this is another problem that had only started in the past few weeks.

I've switched my video watching over to VLC but the music thing is annoying.

The laptop is at least a five year old Toshiba.  11.04 worked fine until a few weeks ago.

---

### Post by lwtazt on 2011-09-01
The same problem in my laptop.But I can not find the solution now.Give me some advice.Thanks.

---

