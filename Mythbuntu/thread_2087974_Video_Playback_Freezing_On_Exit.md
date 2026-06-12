---
title: "Video Playback Freezing On Exit"
date: 2012-11-25
forum: Mythbuntu
---

### Post by MiniVanMan on 2012-11-25
I've got a strange problem, and Google has not yielded any advice.

My screen is freezing when I try to exit (I use a keyboard so the exit key is ESC) a video, whether recorded TV, a movie, or live TV.  The only thing to do at that point is a hard reset of the computer.  

I've narrowed down the issue to my audio.  Hear me out on this one.

I've attempted several reloads of both Mythbuntu and MythTV on top of a Xubuntu install.  I first encountered the issue with the Xubuntu install.  I couldn't figure it out, so I tried with Mythbuntu.  Mythbuntu worked fine in the beginning.

I run a virtual machine, which is critical to my Myth boxes so I can watch Netflix via a XP VM.  Xubuntu with MythTV, I had audio in both MythTV and the Virtual Machine.  With Mythbuntu, I didn't have audio in the Virtual Machine.

I noticed that Mythbuntu used ALSA while Xubuntu used PulseAudio.  Mythbuntu, everything worked fine on the MythTV side, the only issue was the audio in the Virtual Machine.  So, I loaded PulseAudio, thinking that since it worked in Xubuntu the way I wanted, it would work in Mythbuntu.  Loaded it, and immediately, my videos started freezing again upon exit.  I had audio in both Myth and the Virtual Machine, but the freezing issue was there.

So, the next step was go back to ALSA.  I got audio working again via ALSA and videos playing normally.  No audio in the virtual machine.  Thinking I'd narrowed down the issue to PulseAudio, I worked with ALSA, configured my .asoundrc file, set up dmix and voila, had audio in my virtual machine.  Was ecstatic.  Went back to watch a video in Myth, and wouldn't you know it, screen froze on exit.

I'm running audio via the HDMI out on an AMD 6450.  I'm using proprietary drivers.  The only thing I can think is it's an issue with the video card.  I have another frontend machine using the Xubuntu/MythTV combo with a Nvidia card that works just fine.  

Now that I've thought out loud for a bit, I'm going to pursue that route.  I wonder if it's driver related.

Anybody got any advice, seen this kind of issue, anything?

---

### Post by MiniVanMan on 2012-11-25
Update.

Just installed the Nvidia card that I use in another frontend.  The frontend is a Xubuntu, with MythTV installed on top of it.  Everything works fine there.

So, I'm running into the exact same problem with the Nvidia card.  I've reloaded the OS several times, trying both Xubuntu and Mythbuntu.  

It only starts to happen once I have sound configured correctly, or more specifically "dmix".  

Looking for some advice here.  I'm leaving for 2 weeks on business, and I'd like to get this done.

---

### Post by bbzzdd on 2012-11-28
I had the same problem and same resolution.  Hate to say it but using an ATI card for Linux is not a good experience.  I replaced my Radeon HD 6870 with a GTX 650 Ti and now everything is rock solid.  I could barely use the OpenGL renderer on the ATI card and it would crash on exit, now I am VDPAU high quality without a hitch.

---

