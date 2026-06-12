---
title: "convert video on intrepid"
date: 2009-03-01
forum: Multimedia Software
---

### Post by Naegling23 on 2009-03-01
I have always used winFF as the frontend to ffmpeg...but this seems to be broken in intrepid.  What is the best way to convert video now, or how do I fix winFF/ffmpeg?

---

### Post by practic on 2009-03-01
I use AviDemux, Handbrake, and Tab Encoder.

---

### Post by binbash on 2009-03-01
Did you install svn debs for ffmpeg?WinFF is not broken for me.You can also try handbrake or avidemux

---

### Post by Naegling23 on 2009-03-01
handbrake crashes when I try to encode anything.  Nothing seems to work.  WinFF will start, but I get errors everytime I try to convert a video, my current one is:

Warning: Could not start program '/home/naegling23/.winff/ff090301153257.sh' with arguments '/home/naegling23/.winff/ff090301153257.sh &'.

---

### Post by Naegling23 on 2009-03-01
this has turning into an absolute disaster!!!!!!!!!!!!!!!!!!!

ffmpeg is hosed with winff along with it.

Ive also lost kdenlive and am unable to bring that back as well.

all I want at this point is to get ffmpeg and kdenlive reinstalled....at this point, Ive wasted about 4 hours of my day and have actually put myself in a much worse situation than before....at this point, anything on my system that is connected to video processing is dead!

---

### Post by Naegling23 on 2009-03-01
and I upgraded ffmpeg to the svn version....I think this is the start of all the problems.

---

### Post by practic on 2009-03-03
Try removing the winff that is in your home directory and reinstall it using the instructions from their website:

[http://code.google.com/p/winff/wiki/UbuntuInstallation]("http://code.google.com/p/winff/wiki/UbuntuInstallation")

I followed those instructions, and while I did not test extensively, WinFF seems to run without difficulty on my Intrepid system.

---

### Post by Naegling23 on 2009-03-03
Everything is just too messed up, I cant install anything due to broken dependencies.  I stripped out ffmpeg and all programs associated with it, and reinstalled everything.  The problems still persist.  kdenlive wont install due to conflicts with libmlt....

Just out of curiosity, I installed, winff, and kdenlive on my laptop....everything went smooth as silk, zero problems....

So, im just going to wait for jaunty (so I can take advantage of ext4), move my home drive, and start over.  At this point, I think its best, besides, that computer has had ubuntu since dapper without a reinstall.

---

### Post by andrew.46 on 2009-03-03
Hi Naegling23,

Have you had a go at using FFmpeg itself? The *basic* syntax is pretty straightforward:

```
ffmpeg -i infile outfile
```

and you just embellish from there.

All the best,

Andrew

---

### Post by paul.gevers on 2009-03-04
> **Naegling23 said:**
> Everything is just too messed up, I cant install anything due to broken dependencies.

Does "Fix broken packages" in synaptic help? Your package manager should have such an option.

---

### Post by niceguy123 on 2009-03-05
> **Naegling23 said:**
> I have always used winFF as the frontend to ffmpeg...but this seems to be broken in intrepid.  What is the best way to convert video now, or how do I fix winFF/ffmpeg?

Thanks for the lead on winFF, I wasn't aware of it. Can you suggest what is a good format for uploading to youtube. And how can I make clips files smaller for quicker upload time?

And what about ripping dvd?

---

### Post by practic on 2009-05-03
I have not put anything on YouTube, so can't answer that one; but I have used AcidRip for dvd ripping numerous times and it worked well.

---

### Post by paul.gevers on 2009-05-03
> **Naegling23 said:**
> Warning: Could not start program '/home/naegling23/.winff/ff090301153257.sh' with arguments '/home/naegling23/.winff/ff090301153257.sh &'.

Ok, I figured out what the problem is here. The script created by winff does not work as-is in terminal that is in use on your system does. If you go to Edit -> Preferences -> Linux you can change the path to the "Terminal to run ffmpeg". I suggest you use xterm there, if you have that installed.

Can you please specify where your x-terminal-emulator points to by running ```
ls -al /etc/alternatives/x-terminal-emulator
```
in a command shell?

---

