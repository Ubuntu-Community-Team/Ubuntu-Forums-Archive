---
title: "No audio playback in Kino 1.3.0"
date: 2008-05-28
forum: Multimedia Software
---

### Post by m3kan1cal on 2008-05-28
I'm new to the forum and Ubuntu. Love it. I've recently installed Kino 1.3.0 for video editing, and so far so good, except that I don't get audio playback when playing video clips on the timeline. When videos are rendered, audio is there and very crisp. 

Has anyone run into a similar problem with audio playback in Kino? Is there a setting I'm missing somewhere?

Thanks a bunch.

---

### Post by m3kan1cal on 2008-05-28
Weirdly I don't have audio playback in any of my video applications while on the timeline. Rendering video is fine, but no audio during playback.

Any ideas?

---

### Post by m3kan1cal on 2008-05-29
In case it helps anybody, fixed my problem by disabling onboard audio in the bios.

---

### Post by v4169sgr on 2008-07-07
I have a solution in search of a problem:)

For those not in the fortunate position of being able to fiddle with their BIOS, who are running Kino 1.3.0 compiled from source, and who experience video playback too fast with no audio, but otherwise have no issues with sound [and are running pulseaudio], then:

* In Kino, Edit -> Preferences -> Audio Tab -> Audio Device /dev/dsp

* Invoke with
```
padsp kino
```
This is because Kino with this setting is acting as an OSS application that is not aware of pulseuadio, so has to be told where to find the sound device.

This works for me, hope it helps someone else!:KS

---

### Post by pewjumper on 2008-07-28
I have audio but it's as much as 10 seconds ahead of the video.
Had a similar problem with windows but audio would lag the video usually
when burning the DVD. Note I work with 2 hour dvd full resolution not little file to send to utube

---

### Post by Steve413z on 2008-08-07
"v4169sgr" you are the man

---

### Post by csumm101 on 2009-02-15
I had the same problem. But in my system I have 3 audio cards installed! Can you tell I'm a musician?
I clicked on the menu item Edit, then Preferences, then clicked on the Audio tab. By default there was "hw:1" in the Audio Device field. I tried replacing that with /dev/dsp and that didn't work...
then I had the idea of taking a peek in the /dev/ directory and I found there are 3 files - dsp, dsp1, and dsp2
I assumed those stand for the 3 audio cards I have on my system, respectively. So, I thought I'd go through them one by one.

The first alternative I tried entering in the "Audio Device" field was /dev/dsp1

Viola! That worked! The audio and video was choppy at first but I tweaked the settings in the Edit/Preferences/Display tab. (Chose Reduced Xvideo and checked all three options)

Now I have good video AND AUDIO on my previews. Thanks!

---

### Post by WingNa on 2010-04-10
> **v4169sgr said:**
> I have a solution in search of a problem:)

For those not in the fortunate position of being able to fiddle with their BIOS, who are running Kino 1.3.0 compiled from source, and who experience video playback too fast with no audio, but otherwise have no issues with sound [and are running pulseaudio], then:

* In Kino, Edit -> Preferences -> Audio Tab -> Audio Device /dev/dsp

* Invoke with
```
padsp kino
```
This is because Kino with this setting is acting as an OSS application that is not aware of pulseuadio, so has to be told where to find the sound device.

This works for me, hope it helps someone else!:KS

For me (Kino 1.3.3) this works using device _/dev/adsp_

Change the default open command for *.kino files to "padsp kino"  as shown above and its fixed permanently.

---

### Post by marshcast on 2010-11-09
> **WingNa said:**
> For me (Kino 1.3.3) this works using device _/dev/adsp_

Change the default open command for *.kino files to "padsp kino"  as shown above and its fixed permanently.

Perfect :D

thanks all for that can't see the post from here, but for the tech result, and this one (I read the other a bit wrong, like...)

---

### Post by axMan5389 on 2010-11-12
> **WingNa said:**
> For me (Kino 1.3.3) this works using device _/dev/adsp_

Change the default open command for *.kino files to "padsp kino"  as shown above and its fixed permanently.

I'm using Ubuntu 10.10, Kino 1.3.4 (tried both Deb pkg and source).
Had the exact problem of "too fast playback with no audio"

Saw the above fix.  Perfect.
I tell Kino the audio device is /dev/dsp or /dev/adsp, doesn't seem to matter, both work.

Edit menu launcher or invoke Kino as said above:  "padsp kino"

Fixed.  :guitar:

---

### Post by repunante on 2010-11-19
> **v4169sgr said:**
> I have a solution in search of a problem:)

For those not in the fortunate position of being able to fiddle with their BIOS, who are running Kino 1.3.0 compiled from source, and who experience video playback too fast with no audio, but otherwise have no issues with sound [and are running pulseaudio], then:

* In Kino, Edit -> Preferences -> Audio Tab -> Audio Device /dev/dsp

* Invoke with
```
padsp kino
```This is because Kino with this setting is acting as an OSS application that is not aware of pulseuadio, so has to be told where to find the sound device.

This works for me, hope it helps someone else!:KS


Yes, I worked for me as well. Thank you so much  :)

---

### Post by selectstar on 2011-03-06
> **v4169sgr said:**
> I have a solution in search of a problem:)

For those not in the fortunate position of being able to fiddle with their BIOS, who are running Kino 1.3.0 compiled from source, and who experience video playback too fast with no audio, but otherwise have no issues with sound [and are running pulseaudio], then:

* In Kino, Edit -> Preferences -> Audio Tab -> Audio Device /dev/dsp

* Invoke with
```
padsp kino
```This is because Kino with this setting is acting as an OSS application that is not aware of pulseuadio, so has to be told where to find the sound device.

This works for me, hope it helps someone else!:KS

thanks a lot!! This really helped :guitar:

---

### Post by radard on 2011-09-05
In my case (Ubuntu 11.04 & Kino 1.3.4), I had no audio playback and an insane playback speed (100 x normal speed). I went to Kino Preferences/Audio and changed "/dev/dsp" to "default" and it worked again normally.

Hope this helps others.

---

### Post by area124 on 2011-09-05
> **v4169sgr said:**
> I have a solution in search of a problem:)

For those not in the fortunate position of being able to fiddle with their BIOS, who are running Kino 1.3.0 compiled from source, and who experience video playback too fast with no audio, but otherwise have no issues with sound [and are running pulseaudio], then:

* In Kino, Edit -> Preferences -> Audio Tab -> Audio Device /dev/dsp

* Invoke with
```
padsp kino
```
This is because Kino with this setting is acting as an OSS application that is not aware of pulseuadio, so has to be told where to find the sound device.

This works for me, hope it helps someone else!:KS

Thanks much!!! This work great!

---

