---
title: "What software to capture Hi-8 with Hauppauge WinTV PVR USB2?"
date: 2008-02-24
forum: Multimedia Production
---

### Post by eamann on 2008-02-24
I am a novice in the world of video and Linux, too.

I am looking for software with a GUI which would enable me to capture my Hi-8 cassettes with a minimum of hassle.

On the basis of what I read on various forums, I bought a Hauppauge WinTV PVR USB2 device, thinking it would work well with Ubuntu.

Now I discover that programmes like Kino, Kdenlive, etc., do not recognise the device!

I have just read lots of posts about video, but the more I read (video4linux, xawtv; mythtv, etc.) the more confused I get!

Any suggestions and advice as to how to easily digitalise my cassettes and then edit them in Ubuntu would be very welcome!

Thanks!

---

### Post by bryanagee on 2008-05-18
I am currently using my Hauppauge WinTV PVR USB2 to capture from RCA into [VLC]("http://videolan.org"). It doesn't show up as a Vid4Linux device, but if you hit Ctrl+A and select the tab that says "PVR", you can then open the advanced settings and set the channel to 1 or 2 (if you get audio and no picture, increase or decrease the channel til you do) you can grap video of the RCA inputs and transcode it. Works great for me, but let me know if it works for you.


BTW-
To install VLC, just do ```
sudo apt-get install vlc
```

---

### Post by eamann on 2008-05-26
Thanks very much for taking the time to reply to me!

Please excuse my delay in reacting: I was away on holidays for the last two weeks.

I'll try VLC and let you know how that went.

By the way, what is "RCA"?

Best wishes,

Eamann

---

### Post by bryanagee on 2008-05-27
RCA is a common name for the composite connections (the set of three pin and ring combos in yellow, white and red).

---

### Post by eamann on 2008-05-28
Thanks!

Eamann

---

