---
title: "HDMI through amplifier problem"
date: 2012-08-17
forum: Mythbuntu
---

### Post by GuiGuy on 2012-08-17
When I route the mythbuntu box's HDMI output (1080p 60hz) through my amplifier's HDMI in, the screen  goes to a black screen every few seconds. The screen reports "no input" for about a second and then the picture is back for a few seconds. It does this continuously but only on the mythtv output. Desktop and VLC at the same resolution behave OK.

Any ideas what might be happening?

Thanks in advance...

---

### Post by Rotak on 2012-08-18
Could be a HDCP issue...

When desktop, VLC or myth menu is displayed, the HDCP is inactive. LiveTV (maybe recordings as well) have a HDCP signal, and therefore HDCP gets activated.

Did you try to route the signal of a normal set-top-box or a bluray player through the amp, using the same connector you use for your myth box?
The issue could be the connector, the PC card's (or the driver's) HDCP implementation, and so on.

---

### Post by GuiGuy on 2012-08-18
> **Rotak said:**
> Could be a HDCP issue...

When desktop, VLC or myth menu is displayed, the HDCP is inactive. LiveTV (maybe recordings as well) have a HDCP signal, and therefore HDCP gets activated.


I suspect you're right. It's a new amplifier. I generally don't read instructions until everything else has failed :), but I did eventually find mention of it in the amplifier's manual; it states that the screen goes to black every few seconds if the source device does not provide the HDCP signal. 

Am I correct in presuming there is no work around?

Thanks

---

### Post by Rotak on 2012-08-19
Umh. I expected the opposit. I expected, that the LiveTV/Recording signal WOULD have a HDCP signal, while the desktop or menus wouldn't have one. Now, I am puzzled.

I assume you installed the video card drivers. There should be a tool included, where you can check the HDCP status (in/active). I am sceptical, that it's sending HDCP signal on desktop, but doesn't send HDCP when watching TV/Recording.

---

### Post by BicyclerBoy on 2012-08-19
Unless you are running windows then there is no HDCP handshaking involving the computer.
HDCP is driven/negotiated from the source end, the display device does not demand it.

It is possible that the AVR has a private HDCP handshake with the display.
This should **not** involve the PC video card driver..

Does this effect MythTV video playback only or mythtv menus as well ?
Could be unsupported playback video mode ?
Is your AVR doing any upscaling ?

MythTV does do ELD (audio EDID) probing ..

dmesg | grep HDA

Did you run the frontend audio device scan tool ?

---

### Post by GuiGuy on 2012-08-20
> **BicyclerBoy said:**
> 

Does this effect MythTV video playback only or mythtv menus as well ?


Both. However, the problem stops when I switch to a virtual desktop. So the problem seems associated with the mythtv display at all levels.


> 
Could be unsupported playback video mode ?


I can't be sure, but suspect not. If I feed the HTPCs (mythtv) HDMI directly to the LED/LCD TV screen or through my old amplifier everything works fine. The new amplifier is SAMSUNG, BTW. It's spcs suggest that there isn't much it doesn't support...

> 
Is your AVR doing any upscaling ?


Possibly, but I won't be able to check until much later today (AU time).


> 
MythTV does do ELD (audio EDID) probing ..

dmesg | grep HDA

Did you run the frontend audio device scan tool ?

I have done the audio device scan. 

Thanks for the tips. I'll follow up as soon as I can.

---

### Post by GuiGuy on 2012-08-20
Thanks for the help, guys. As BicyclerBoy and others hinted, in the end it was in the settings. The clues were in [this thread.]("http://ubuntuforums.org/showthread.php?t=2043817") 

Once I changed to VDPAU SLim and VAAPI Accelerator decoder the problem stopped. My mythbuntu frontend is now playing fine through the amplifier. I have a minor criticism in that the rendered images are now a bit grainier.

Thanks again.

---

### Post by BicyclerBoy on 2012-08-22
Altho it is possible to make MythTV use VAAPI video acc on nVidia hardware (vdpau backend for vaapi), it is better to use VDPAU directly.

VLC can only use VDPAU h/w via the "vdpau backend for vaapi".

What video card/onboard video do you have ?

Hmm.. noticed some other posts..

You do realize that VDPAU only works on nVidia h/w 9400/ION & up excluding GTX 260/280 ??

VDPAU is an open std api published by nVidia but no one else is using it (yet).

---

### Post by nickrout on 2012-08-22
> **BicyclerBoy said:**
> 
You do realize that VDPAU only works on nVidia h/w 9400/ION & up excluding GTX 260/280 ??
No, 8xxx up.

---

### Post by GuiGuy on 2012-08-22
> **BicyclerBoy said:**
> 
You do realize that VDPAU only works on nVidia h/w 9400/ION & up excluding GTX 260/280 ??

Exactly! That's why I am confused why using the VDPAU settings on my ATI (on MOBO) graphics hardware fixed HDMI problem, albeit with a little image degradation. Maybe it's not VDPAU but the decoder setting?

Anyway, I'm going to experiment this weekend to see what's what.

Cheers

---

### Post by nickrout on 2012-08-23
> **GuiGuy said:**
> Exactly! That's why I am confused why using the VDPAU settings on my ATI (on MOBO) graphics hardware fixed HDMI problem, albeit with a little image degradation. Maybe it's not VDPAU but the decoder setting?

Anyway, I'm going to experiment this weekend to see what's what.

Cheers

But you didn't set it to vdpau, you set it to vdpau AND THEN CHANGED IT TO SOMETHING ELSE!!

---

