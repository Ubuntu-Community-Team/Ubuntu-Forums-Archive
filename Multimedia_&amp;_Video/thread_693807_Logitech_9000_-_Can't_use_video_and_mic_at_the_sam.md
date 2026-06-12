---
title: "Logitech 9000 - Can't use video and mic at the same time"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by potion on 2008-02-11
This is really frustrating... I've got both the video and the microphone on my Logitech 9000 working, but they don't work at the same time.

I've compiled the latest UVC driver. I've compiled ALSA so it recognizes the camera as a USB audio device. And the thing is, everything works great, just not all at once.

Here are some screenshots from Ekiga, first without the microphone, then with it. More or less the same thing happens in Skype. I get these jagged green lines, and I can just barely make out the image behind it. In Skype, when I end the call, there's a split second where the interference disappears and the image is perfect. Not sure if it's moving at that point.

Does anyone have any ideas? I guess there's no other driver I could try, is there? Clearly the camera and microphone functions are getting in the way of each other somehow, but what can i adjust so that doesn't happen?

Thanks very much for any help you can give me.

---

### Post by Cimmo on 2008-02-22
we had a similar issue with Skype and an usb headset, plugging the usb headset to a different usb bus than the one used by the webcam fixes the problem.

Try to use different usb bus for webcam and another one for others usb stuff and let me know.
Seems a bug/bandwidth saturation with usb module in the kernel or maybe a conflict between alsa and usb modules.

a question:
do you have usb 1.1? If yes and you have 2.0 try it ;)

bye
Marco

---

### Post by potion on 2008-04-29
Thanks for your help, Marco, sorry I didn't see it when you first posted.

So I'm taking another crack at this, and I had a thought... It's probably true that I'm just not getting enough power to the webcam. When I use just the camera or just the mic, each works fine individually, but when I try to use them both together, things go haywire.

So my thought was, what if I used something like [this]("http://www.usbfirewire.com/Parts/rr-usb2-2am-af-1ft.html") to boost the power? Would that work?

One thing I should point out is that the three USB ports on my laptop all seem to be on the same bus, if I understand correctly. Here's what lsusb gives me with just the webcam plugged in, no other devices:

```
jon@ubuntu:~$ lsusb
Bus 003 Device 002: ID 046d:0990 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

If I then unplug it and plug it into a different port, it'll change to:

```
jon@ubuntu:~$ lsusb
Bus 003 Device 003: ID 046d:0990 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

The bus never changes. That being the case, could I still get additional power if I got a cable attachment that draws power from two ports at once? Anyone know?

Thanks!

---

### Post by Cimmo on 2008-04-29
> **potion said:**
> Thanks for your help, Marco, sorry I didn't see it when you first posted.

So I'm taking another crack at this, and I had a thought... It's probably true that I'm just not getting enough power to the webcam. When I use just the camera or just the mic, each works fine individually, but when I try to use them both together, things go haywire.

So my thought was, what if I used something like [this]("http://www.usbfirewire.com/Parts/rr-usb2-2am-af-1ft.html") to boost the power? Would that work?

One thing I should point out is that the three USB ports on my laptop all seem to be on the same bus, if I understand correctly. Here's what lsusb gives me with just the webcam plugged in, no other devices:

```
jon@ubuntu:~$ lsusb
Bus 003 Device 002: ID 046d:0990 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

If I then unplug it and plug it into a different port, it'll change to:

```
jon@ubuntu:~$ lsusb
Bus 003 Device 003: ID 046d:0990 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

The bus never changes. That being the case, could I still get additional power if I got a cable attachment that draws power from two ports at once? Anyone know?

Thanks!

yeah maybe it's a problem of power who knows.
So with both camera and headset you have the problem even trying to change usb to the camera? If yes then I have no idea how to fix it.

---

### Post by potion on 2008-04-29
> **Cimmo said:**
> yeah maybe it's a problem of power who knows.
So with both camera and headset you have the problem even trying to change usb to the camera? If yes then I have no idea how to fix it.

I don't have a headset, the mic is part of the camera. So it's one device that consists of both a camera and a mic, and only one USB cable. As long as I'm only actually using one component or the other, either works fine, but I can't use both at once. Which made me think you might be right about it being a power issue.

Think it might work to double up by connecting to two ports at once with one of those special cables? Or maybe it wouldn't make a difference, since all three of my ports seem to connect to the same bus...

Thanks very much for your help!

---

### Post by Cimmo on 2008-05-03
> **potion said:**
> I don't have a headset, the mic is part of the camera. So it's one device that consists of both a camera and a mic, and only one USB cable. As long as I'm only actually using one component or the other, either works fine, but I can't use both at once. Which made me think you might be right about it being a power issue.

Think it might work to double up by connecting to two ports at once with one of those special cables? Or maybe it wouldn't make a difference, since all three of my ports seem to connect to the same bus...

Thanks very much for your help!

ah they are on the same usb, understood were two separate things.
Then I have no idea how to solve your issue, I'm sorry.

---

### Post by potion on 2008-05-07
No problem, thanks all the same, Cimmo.

---

