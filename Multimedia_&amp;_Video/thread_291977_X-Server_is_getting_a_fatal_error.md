---
title: "X-Server is getting a fatal error"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by DizzyThermal on 2006-11-03
Hey guys, I'm getting an error when I am booting up Ubuntu.

When I first installed it I was using my nVidia GeForce FX5200 and it worked fine, then I wanted to get my dual monitors working and tried getting drivers for my nVidia GeForce 6600 GT

I installed drivers off of Ubuntu Add/Remove Programs list and now any time I boot up with either one of the cards or both I get an X server fatal error and I can't even boot up to the desktop...

I can get a command line but I am unsure of what command(s) I should use...

If you could give me a guide to uninstalling and reinstalling the drivers I used and help me get the xserver working I'd be wicked grateful.

Thanks in advance guys!  :)

---

### Post by Paul41 on 2006-11-03
You can reset your xserver settings with this. When you run it it will take you through some prompts to set things up.
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by DizzyThermal on 2006-11-03
I did that and should I select   NV or Nvidia for the Xserver Driver???

I identified the card as   NVIDIA FX 5200

It just keeps going on with stuff about the keyboard,  How can I just boot into Ubuntu...

That's all I want to do :(

---

### Post by tseliot on 2006-11-03
> **DizzyThermal said:**
> I did that and should I select   NV or Nvidia for the Xserver Driver???

I identified the card as   NVIDIA FX 5200

It just keeps going on with stuff about the keyboard,  How can I just boot into Ubuntu...

That's all I want to do :(
select "nv" and press ENTER every time you don't know the answer

---

