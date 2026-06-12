---
title: "Problem with video playback in LiveTV or Recordings"
date: 2008-07-22
forum: Mythbuntu
---

### Post by gndprx on 2008-07-22
I have a new install of 8.04.1 and I've finally been able to get the tuners configured and able to view source material.

The problem is when I try to watch LiveTV, it starts to show whatever is on and then freezes the frame.  If I press play it will jump to the current time in the recording and freeze frame again.  

The same thing happens when I try to view a recorded show.  

Hardware:

P4 2.6Ghz - 512MB RAM
Hauppauge PVR-500 with a DirecTV D10 receiver on SVIDEO1
ATI X1650Pro AGP 8X 512MB video card
Turtle Beach Riviera Sound Card

Currently it is doing simple VGA output to a 17" LCD as I configure the system.

I've verified that the capture card is set to use the PVR 350 / PVR 500 MPEG 2 hardware but don't know what else to look at.

It's also using the ATI driver from the restricted drivers list.  I really feel that it's in the playback and not the capture.

Any help would be appreciated as I don't know where to look next.

---

### Post by gndprx on 2008-07-22
Okay, I think I narrowed it down to a sound problem, not a video problem.

Now that I have the sound working (wasn't hooked to speakers previously) it's stuttering and not able to play back smooth at all.  Both on LiveTV and Recordings.

I'm not sure how to setup sound options or check the driver in XFCE.  Is there something in Myth I can try?

---

### Post by larsolav on 2008-07-22
Does /var/log/mythtv/mythfrontend.log give any clues or error messages?

---

### Post by gndprx on 2008-07-22
I've was working with that just now.

I get a ton of WriteAudio: buffer underrun errors in the frontend log.

Running top, when I go to live TV, CPU usage spikes to about 95%  

This shouldn't happen on a 2.4 with only one capture running.  Something has to be set wrong but I haven't found it yet and it has to be in Myth somewhere because VLC runs smooth as can be at around 18-20% CPU

Any thoughts?

---

### Post by gndprx on 2008-07-23
It seems this box is working okay as a backend only server.  I ran the frontend on my regular Ubuntu desktop and there was no performance issues.

However if I ran it at 1x speed, there were green "scan lines" across the whole screen.  If I slowed it down to .95x it cleared up and was watchable.

And I still can't use the front end on the backend box to watch tv.

Anyone have any more thoughts?

Thanks.

---

### Post by redneck1980wi on 2008-09-19
I am having this exact same problem, no fix yet

---

### Post by newlinux on 2008-09-19
Run mythfrontend with the -v playback option for more verbosity. I would guess you have a problem with your playback profile. Which one are you using (what settings)? try a couple of the other ones - or maybe create your own.

---

