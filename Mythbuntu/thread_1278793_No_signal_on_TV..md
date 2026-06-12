---
title: "No signal on TV."
date: 2009-09-30
forum: Mythbuntu
---

### Post by longreach on 2009-09-30
Hello all, apologies if this has been covered a billion times but I can't find anything on it.

My problem is that when I start my newly built HTPC I have no video on the TV. I do get the boot screen and if I go into BIOS the TV comes through fine. But once it gets to grub I have nothing. The PC itself appears to be working fine and if I plug a monitor up to the HTPC, the mythbunutu frontend is there, but nothing is being received to the TV. Any help appreciated.

For further info, the video is onboard the motherboard (P5QL-EM) and the TV is an LG 60PY2D. The video is being sent via VGA as there is no DVI on the TV.

---

### Post by longreach on 2009-09-30
Update: I have tried the TV on my laptop running Ubuntu and the TV shows up as 'unknown' on the display settings. I tried turning it on, but still no signal showing on the TV. Oddly enough, I had the TV hooked up to the laptop on XP a while back and it worked fine so I am thinking Linux won't work on the TV...? :confused:

---

### Post by SiHa on 2009-09-30
So, to summarize:

If you plug a monitor in, it works, but if you plug the TV into the same VGA port, it doesnt? What happens if you boot with the monitor connected, then 'hot-swap', unplug the monitor and plug in the TV?

If you still get nothing on the TV, then I'd suspect that the resolution or refresh rate that the PC is using is out of range of what the TV will accept.

Many TV's are very limited as to what they will accept over VGA, if the signal is out of range, some won't tell you about it, they'll just turn off.

---

### Post by longreach on 2009-09-30
Hi SiHa, thanks for the response.

Your right in your summary, monitor works, TV doesn't (except for the boot screen/menu).

I went out and bought a HDMI cable today and hooked up with that and BINGO! All works fine. Didn't really 'fix' the original problem but I have found a way around it.:guitar:

---

### Post by SiHa on 2009-10-01
Glad it's sorted. I was thinking about this one last night, and it occurred to me that Ubuntu generally boots into 800x600 using it's opensource drivers. 800x600 seems to have become slightly 'non-standard' lately.
The generally accepted minimum is 1024x768, and the default fallback is 640x480. At least one of my TV's will only accept 640x480, 1024x768 & 1280x768. 

Anyway, I'm waffling. I'll get me coat.

---

### Post by chipppy on 2009-10-01
Good Evening

Glad you got it running.  Quick story

I had a very similar sounding problem.  I found that I had to boot into recovery mode and repair the graphics.  then boot into safe mode and got a TV going.  then dowloaded the latest drivers for my graphics card and all fixed.  Just boot as per normal from then on.

I dont understand what the problem was but that was my fix.

Cheers
chipppy

---

