---
title: "Lenovo Easy Camera"
date: 2010-10-27
forum: Multimedia Software
---

### Post by wjdenny on 2010-10-27
I know this might seem like a repeat thread, but my case seems to be somehow different than earlier posts I've read on here and the Skype forum. My webcam shows only a bright green screen, sometimes vauge static or lines are through it.

I tried the LD_PRELOAD export (both as multi-line sh script and as a single-line command, neither changed the result. I've tried reloading the uvcvideo module, as well as XLIB_SKIP_ARGB_VISUALS=1, and every combination of the two.

I also made sure my /dev/video0 was chmod'd to 777, (it was originally 660)
Tried running all the above in sudo, and probably a few other things I can't remember.

The main difference from other posts is that the cam worked fine in one program but not in others. Mine does not work in any of them. I suspect the solution is to compile a newer version of the uvcvideo driver; but that is a bit of a shady area for me so I'm ruling out other possibilities.

If it helps, I've attached the output from lspci, lsusb, lshw, and lsmod | grep uvc .. I think my first problem is that I can't find my camera in the pci or usb lists. For most people with the same equipment I think it comes up as 'Lenovo Easy Camera' .. but I don't see that anywhere. I know I have one, and cheese/vlc/skype recognize a camera at /dev/video0 -- it just shows nothing but green.

Any ideas?

---

### Post by no2498 on 2010-10-28
odd your dev's are set
did you try the cam in cheese webcam booth
look in sound&video for it

---

### Post by wjdenny on 2010-10-30
I thought it was odd too. Yes I tried cheese, as I said earlier also vlc and skype, all have the same green screen.
Recently I put on a fresh install of lucid, which I then upgraded to maverick.. I'm having this problem in both versions of the distro. 
I read somewhere that some folks had success by reverting to an earlier kernel, but that was back for intrepid or some other previous version, and that it had been fixed since then.

I'm not sure where else to look, everything I can find in Google is a similar problem, but solved by doing things that haven't been working in my case.

---

### Post by no2498 on 2010-10-30
in/on 10.04 i have video4linux control panel
look in system preferences for it 
it is the only way i can set any thing for my cam with
i did not install it is why i say look for it

---

### Post by wjdenny on 2010-11-03
I'm not sure if you were suggesting something specific.. but I do have that control panel as well. I fiddled with every control, nothing substantial. It seems to recognize the webcam though...
driver: uvcvideo
card: Lenovo EasyCamera
bus_info: usb-0000:00:1d.7-3
version: 0.1.0
capabilities: 0x05000001

still getting green screen of nothingness :(

---

