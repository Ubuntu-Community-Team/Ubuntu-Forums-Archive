---
title: "Problem to see TV on my Dapper"
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by cazz on 2006-09-29
Hi
I have a WinTV PCI card in my dapper that I try to see if I can see some TV on with xawtv.

When I write x```
awtv -hwscan
``` it show


```
This is xawtv-3.94, running on Linux/i686 (2.6.15-27-386)
looking for available devices
port 126-126
    type : Xvideo, image scaler
    name : NV10 Video Overlay

port 127-158
    type : Xvideo, image scaler
    name : NV05 Video Blitter

port 159-159                            [ -xvport 159 ]
    type : Xvideo, video overlay
    name : NVIDIA Video Interface Port

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video (Hauppauge (bt878))
    flags: overlay capture tuner

```

Then I write ```
xawtv -device /dev/video0
``` and that show 

```
This is xawtv-3.94, running on Linux/i686 (2.6.15-27-386)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  63
  Current serial number in output stream:  63
```

Nothing show when I start xawtv so what do I have to do and what do I have to install.

---

### Post by apoth on 2006-09-30
I'm getting the same error off my webcam.

---

### Post by apoth on 2006-09-30
Ah. Try xawtv -nodga -c /dev/video0

It worked for me for a few seconds, then crashed. Supposedly dga has been removed from the later nvidia drivers. No idea why.

---

### Post by cazz on 2006-09-30
When I try TVtime it work.
I just scan after new channel and I can see but not so good quality but it work :)

---

### Post by dabl on 2007-07-16
This thread is exactly the problem I'm having today:

- Hauppauge PVR-150 is set up and working correctly under Ubuntu Feisty
- Using an Nvidia card with current proprietary driver (i.e. won't support XF86-DGA)
- IVTV seems to run right - ivtv-tune works so I can tune channels
- xawtv appears to work when started with ```
xawtv -nodga -c /dev/video0
```
- I can right-click on xawtv and set the broadcast type, channel, etc.
- but no joy, when opening the video stream -- black static is all I see

When I issue command:
```
xawtv -device /dev/video0
```

The xawtv error says:
```
X: Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
```

Do I need to use tvtime instead?  Will it work even if xawtv doesn't?  What am I missing here?

TYIA!

---

