---
title: "hdmi port?"
date: 2008-07-23
forum: Multimedia Software
---

### Post by stoneofshadow on 2008-07-23
my ubuntu computer has an hdmi port and one of those red, yellow, and white holes on the back. if i plug a video game console into the hdmi port or the other one how do i make it show up on the moniter?

---

### Post by stoneofshadow on 2008-07-23
also if i plug an hdmi cable into the computer and the tv would the tv be used as the moniter?

---

### Post by brokenLockpick on 2008-07-23
Those ports may be exit only as far as data goes. I've got a "VIVO" port on my graphics card that is specifically designed for video in or out, but every time I've seen someone try to hook up a video game through such a device it's usually really lagged behind and impossible to play. But the HDMI port is VERY likely capable of using a TV as a monitor.

Edit: If you want to do video in, the first step is to find documentation about the video card, or motherboard that the ports are attached to, to know if it is even possible.

---

### Post by stoneofshadow on 2008-07-28
if i assume that it would work is there some program that i need to use to see the video?

---

### Post by brokenLockpick on 2008-07-28
Tv as monitor: In my case the nvidia drivers handle the tv output. All I had to do was add a line to the xorg.conf file to tell the card what format to use (I chose 720p rather than full 1080p due to the distance I sit from it). This may not alway be necessary but my HDTV wasn't recognized automatically using the RGB component out.
As I understand it the Nvidia control panel handles it for some HDTVs.

Incoming video: The drivers should handle the actual incoming video stream to make it avaiable to the rest of the system. I really have no expierence under linux with incoming video.

You still haven't mentioned whether you are using onboard(built in) or discreet(card) graphics. The manufacturer would be good to know too (nvidia, ati, intel, etc)


If you know your motherboard model, (or graphics card model using a card) maybe someone who is familiar with it can help or knows were to find online documentation.

---

### Post by ministoat on 2008-07-28
sorry to derail, but what line did you add for a 720p output? I haven't managed to work out to do it with my setup so far.

---

### Post by brokenLockpick on 2008-07-28
> **ministoat said:**
> sorry to derail, but what line did you add for a 720p output? I haven't managed to work out to do it with my setup so far.

```
Section "Screen"

    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "TVOutFormat" "Component"
    Option         "TVStandard" "HD720p"
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 1280x720 +0+0"
EndSection
```

Note that I had to tell it to use component in an option line, so the card knew from which outputs to send the signal, and note the TVStandard line saying HD720p. those are the two important ones, well metamodes is probably an important line as well

---

