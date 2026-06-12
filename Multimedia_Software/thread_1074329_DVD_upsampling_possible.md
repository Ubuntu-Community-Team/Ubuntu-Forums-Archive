---
title: "DVD upsampling possible?"
date: 2009-02-19
forum: Multimedia Software
---

### Post by wackman on 2009-02-19
Hey everyone,

This past Sunday, I spent my tax refund on my first HDTVs: a 42" in the living room and a 32" in my bedroom. The 32" is a cheapo Westinghouse, but it surprisingly rocks. Since it has a VGA connection, I thought I'd test it out.

So, I pulled out my "sometimes htpc" and installed Intrepid on it. I was shocked that it went off without a hitch. My desktop is beautiful and is at the full resolution (Ubuntu reports 1920x1080, but the user manual for the tv says max 1366x768 - hmmm).

Anyway, my main question is, is there a way to have a dvd player (xine, vlc, etc) upsample DVDs like the store dvd players do? I know if I just play a dvd like normal, the image is still going to be 720x480, it'll just blow it up to fill the screen. Instead, I just want it to upsample to 1080i resolution.

I apologize if this has been answered before, but everything I'm finding is talking about getting modelines right for different TVs. My situation is a bit different.

Thanks for any and all help,

Wackman

PS: Almost forgot to post my specs:

Athlon64 X2 4800+
Foxconn A74MX-K
2 GB RAM
nvidia 7300 (I know, rather underwhelming vid)
80GB HD
Hauppauge HVR 1250 (was going to record dgital cable, but I don't know anymore)
64bit Intrepid

TV is a Westinghouse W3223 32" LCD

Ha! Once I get this solved, come join me for a DVD :popcorn:

---

### Post by Mercury_Alpha on 2009-02-19
Your computer is already scaling the video feed when you maximize the media player's window. That's what upsampling is. You're just using the desktop metaphor instead of letting a DVD player do the work automagically. 

If you want to tweak around with it, though, [this is a pretty good guide]("http://blog.thewombat.org/2008/11/how-to-use-vlc-096-as-upscaling-media.html").

---

### Post by wackman on 2009-02-19
Let me clarify. I don't want to upscale (stretch the image to fill the screen). The image is still going to be 720x480, the pixels are just going to be bigger. Even if I can use filters to sharpen or blur the flaws away, I don't want a 720x480 signal to be stretched over my screen.

DVD upsampling is indeed different. The hardware players upsample the signal to 1080i. Rather than enlarge the pixels, they fill in the gaps, by making a best guess at what color the missing pixels will be.

All I want to know is if any of the software players can do this? Any special svn trunk or alpha software that experiments with this?

---

