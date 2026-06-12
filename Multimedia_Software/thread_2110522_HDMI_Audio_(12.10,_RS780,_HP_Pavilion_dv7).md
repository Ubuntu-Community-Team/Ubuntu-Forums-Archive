---
title: "HDMI Audio (12.10, RS780, HP Pavilion dv7)"
date: 2013-01-30
forum: Multimedia Software
---

### Post by JGMorg on 2013-01-30
Good morning, 

I have an HP pavilion dv7 laptop, running just 12.10. It works great, actually a lot better than Vista used to. This is my first time using Ubuntu. 

When I plug in an HDMI cable, the picture shows up great but there is no audio from the tv (just the laptop). If I go to sound settings and switch it to HDMI/DisplayPort (RS780 HDMI Audio [Radeon HD 3000-3300 Series], the sound test and all other sound does not work. Additionally, while i have HDMI selected for audio out, all video plays at about 2 or 3x faster. 

When I had Vista on here, HDMI audio worked fine, so I am pretty sure that it is not broken.

I know this is a common problem, and I've been reading and working at this problem for about two weeks now, but have not been able to get anything to work. Thank you for any help and let me know if any additional info is needed

---

### Post by tlhIngan on 2013-04-29
I'm having the same issue.
Have you made any progress on this?
Is there any chance our sound card isn't fully supported?
I didn't see it listed at: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

What have you tried?

---

### Post by tlhIngan on 2013-09-24
I know it's an old thread.
I know I'm going to get killed by the moderators.
(God forbid we should actually solve issues here.)
I looked into this issue again yesterday and solved it.

1. make sure you are using the most recent Nvidia drivers.
2. make sure you have alsamixer installed (search for alsa in synaptic).
3. make sure your HDMI screen is connected and turned on.
4. launch "nvidia x server settings" and set your HDMI as your only active screen.
5. go to sound settings (speaker icon at the top of your screen, click and go down to sound setting) and set HDMI as your sound output.
6. open a terminal and launch alsamixer.
7. in alsamixer there is an additional S/PDIF slider all by itself to the far right, off the screen, in addition to the two S/PDIF sliders that are in plain sight.
8. scroll using the arrow keys and unmute that one (press 'm' when it's highlighted).
9. press 'esc' to quit
10. test your sound in sound settings (where you were before)

That's what got this working for me.
The left and right channels are inverted, but hey, I can flip speakers.
:)

---

### Post by bilkay on 2013-09-26
I had the same problem and your reply helped me solve it. Thanks!

My hangup was that I had to turn off the laptop display in order to have HDMI show up as a sound source.

This thread should probably be marked "solved".

---

### Post by tlhIngan on 2013-10-06
Mine is working on 12.04 LTS.
Fancy a downgrade?

---

