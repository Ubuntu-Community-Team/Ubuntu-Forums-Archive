---
title: "Confused about aspect ratios"
date: 2009-02-14
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-02-14
I have a TV with a 16:9 aspect ratio. If I set my TV display in MythTV to a 16:9 aspect ratio, the picture appears as a letter box. If I set it to 4:3, it fills the screen nicely and looks right.

This is puzzling me. What's going on here?

Thanks
NM

---

### Post by newlinux on 2009-02-14
what resolution are you sending to the TV?

---

### Post by NautiusMaximus on 2009-02-14
Not sure: I think I just accepted default settings. How do I find out?

---

### Post by newlinux on 2009-02-14
It is your desktop resolution that I am interested in. System->Preferences->Screen Resolution

What is the native resolution of your TV? how is your computer connected to your TV (VGA/HDMI/DVI/S-Video/component/composite).

---

### Post by HyRax on 2009-02-15
Sounds to me that MythTV is assuming you are always using a 4:3 display, so when you set it to 16:9, it generates the black bars to format a 16:9 picture to suit a 4:3 display.

That said, however, my monitor setting in Myth is set to 16:9 and it formats correctly on my 16:9 monitor also.

---

### Post by NautiusMaximus on 2009-02-15
OK, I've checked the screen resolution, and it was set to 1024 x 768. That, of course, is a 4:3 ratio, not a 16:9 ratio, which I guess is what is causing the problem. So I set it to 1024 x 576, and now things work as expected. Setting my aspect ratio to 16:9 now fills my screen nicely.

Many thanks!

I actually don't know what the native resolution of my TV is. It claims to be "HD ready", whatever that means. I'm connecting via HDMI.

---

### Post by HyRax on 2009-02-15
> **NautiusMaximus said:**
> 
I actually don't know what the native resolution of my TV is. It claims to be "HD ready", whatever that means. I'm connecting via HDMI.

Pull out the manual and read the specs or Google up the model number of your TV.

If it accepts HDMI, then you should definitely have a native 16:9 display which means if it was a cheap one it'll be doing 1366x768 or if it's a good one, then you'll be doing 1920x1080.

Since you set your res to 1024x576, I'm guessting it's a 1366x768 native resolution.

---

### Post by NautiusMaximus on 2009-02-15
Strangely enough, the manual said to set the resolution to 1024 x 768 if you're connecting it to a PC. Rather odd since that's the wrong shape.

But as long as I have the aspect ratio right, does the presise resolution matter if I'm not watching Blu-ray or anything high definition like that?

---

### Post by HyRax on 2009-02-15
Not really. Everything you watch will be either scaled up or down to fit your resolution, that's all.

---

### Post by newlinux on 2009-02-15
> **NautiusMaximus said:**
> Strangely enough, the manual said to set the resolution to 1024 x 768 if you're connecting it to a PC. Rather odd since that's the wrong shape.

But as long as I have the aspect ratio right, does the presise resolution matter if I'm not watching Blu-ray or anything high definition like that?

I have two HDTVs  who's native resolution is 1024x768. This just means it uses rectangular pixels instead of square, and was fairly common for smaller (less than 42") HDTVs a few years ago. However, this caused problems when using the VGA input with myth's scaling (I had this exact same problem). However, both my sets accept 1280x768 through VGA so that would allow the set to scale it to it's native resolution (1024x768 ) and myth still know that I am outputing to a widescreen tv (1280x768 ). Through the HDMI inputs, however the TV accepts 1280x720 (720p) and I don't have this problem either - so that was the other solution.

You will lose detail on HD broadcasts if you are using 1024x576 since HD broadcasts have 720 or 1080 lines vertical resolution and your TV is capable of showing 768. So your TV will be upscaling everything it gets to fit 768 vertical lines of resolution, which probably looks better when the source has 720 or 1080. You will only be sending it 576. Whether or not you notice the difference is another question :).

If you are watching standard definition stuff which usually has 480 lines of vertical resolution or less, probably doesn't make much of a difference.

---

