---
title: "[MythTV + Karmic] Terrible Video Quality"
date: 2010-02-10
forum: Mythbuntu
---

### Post by kdx on 2010-02-10
I recently reformatted my HTPC (eMachines EL1210-09 + Hauppauge HVR-1950 using analog cable) and installed Ubuntu 9.10 and MythTV, but I'm having some video problems that I just can't seem to solve.

My old installation (I think it was Jaunty) displayed a very similar issue right after a reboot, but it could sometimes be resolved by following a quirky routine that included rescanning the channels in the backend setup, modifying a random setting in the backend and then changing it back, running mythfilldatabase, and finally killing and restarting the backend.  I've always assumed that it was a tuning problem.  

Unfortunately, with the new installation, the channel scan freezes on the same channel every time I try to scan, and will never finish.  I've read that I should be able to fetch the proper channel info through my Schedules Direct subscription, but this still results in a garbled picture.  I would go back to Jaunty, but it doesn't support my wireless card, and even after installing the drivers I'd still have a finnicky wireless connection that would randomly disconnect.

The only time I've ever gotten a decent picture in the new install (it was actually a VERY nice picture...better than I had ever gotten with my previous install)  was after I had tried to check the TV video output in xawtv.  I was never able to get any type of video through xawtv (it kept freezing), but the next time I went into the MythTV frontend the picture quality was fantastic...except there was no sound!  Every time I'd try to use xawtv it would freeze and I'd have to close it from the system monitor, which would then break the sound in MythTV until I rebooted, thus resulting in poor picture quality once again.

For reference, I've attached a photo I took of my screen to demonstrate what the picture actually looks like.  It's far worse than what should be expected going from analog cable to an LCD screen, and is basically unwatchable.  

I've read that you can run a manual scan through the terminal to determine the frequency tables and then import them into MythTV, but I haven't found a sufficient description of how exactly that should be performed on analog cable.

If anybody has any ideas or any advice, I'd greatly appreciate it.

---

### Post by azmyth on 2010-02-12
I agree that's really bad. Are you controlling a settop box? This looks like a picture that's off when you're on the wrong main channel on a STB. I'd also try to anything like VLC, Kaffine to see what the picture looks like outside of myth even if this means putting it a Windows box and testing.

---

### Post by kdx on 2010-02-12
No set-top box, just cable straight from the wall.

I (fortunately or unfortunately, you decide!) don't have a Windows box to test it on.  I have somehow been able to get a really great picture, but only briefly, and I have no idea exactly how to do it again.

I'll try VLC and see what I come up with.

---

### Post by kdx on 2010-02-12
I haven't gotten a good picture in VLC, but I suspect that it's related to having to manually tune it.  I found [this]("http://www.jneuhaus.com/fccindex/cablech.html") list of US cable frequencies, but I'm still not finding a good picture with them.

---

### Post by azmyth on 2010-02-12
What kind of video card do you have? I remember having video issues with the base kernel nvidia drivers so I had to install the current ones.

This really shouldn't be this hard since you're just using analog as I don't remember every having to scan for analog (I did for HTDTV OTA).

Could also be a driver issue. Have you looked here.

[http://sray.squidpower.com/2009/02/18/hauppauge-wintv-hvr-1950-on-linux-mythbuntu-mythtv-analog-digital-video-including-s-video-and-composite-inputs/](http://sray.squidpower.com/2009/02/18/hauppauge-wintv-hvr-1950-on-linux-mythbuntu-mythtv-analog-digital-video-including-s-video-and-composite-inputs/)

---

### Post by kdx on 2010-02-12
That's the exact same tutorial I used to install the drivers.

I've got an NVIDIA GeForce 8200 video card in it and I'm using the NVIDIA accelerated graphics driver (version 185) with it.  It works perfectly elsewhere (Hulu, etc.).

What NVIDIA driver did you use?

---

### Post by azmyth on 2010-02-12
Yeah, 185 is the driver I used so that's good.

Start mythtv-setup

under capture card select the device

What does is say for card type, Probed info and default input.

Under mythfrontend. 

Utilities/Settings->Setup->TV Settings->recording profiles

what do you have listed?

If you have mpeg-2 Encoders listed under default, livetv, high quality, and low quality go into each one and tell me what you have listed as width and height. Also what codec is listed for each one.

---

### Post by kdx on 2010-02-12
From mythtv-setup:

Card type: IVTV MPEG-2 encoder card
Video device: /dev/video0
Probed info: WinTV HVR-1950 Model Category 7 [pvrusb2]
Default input: television

Listed under Recording Profiles:
MPEG-2 Encoders (PVR-x50, PVR-500)
Transcoders

Under MPEG-2 Encoders...
Default        (720x480)  
Live TV        (720x480)
High Quality   (720x480)
Low Quality    (720x480)

I don't see any codecs listed there, but all of the Transcoder profiles are using the RTjpeg codec for video and mp3 for audio.  Switching this to MPEG-4 didn't help.  I don't think it's transcoding Live TV anyway, so it makes sense that this wouldn't make much difference.

---

### Post by azmyth on 2010-02-12
All that looks good. If the resolution is off they display a horrible picture but your settings look good. What I would do is search for the previous model on google which is the PVR-USB2 to see if there are any suggestions on improving the quality. This page looks like a good starting point.

[http://www.isely.net/pvrusb2/pvrusb2.html](http://www.isely.net/pvrusb2/pvrusb2.html)

I guess I can't help you any further. Good luck on finding a solution.

---

### Post by kdx on 2010-02-13
No problem...thanks for trying!

---

