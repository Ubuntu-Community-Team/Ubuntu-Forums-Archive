---
title: "WIll this Work: 7300GS, HDMI, sound"
date: 2009-12-18
forum: Mythbuntu
---

### Post by GuiGuy on 2009-12-18
My main front end has an nvidia geforce 7300GS which feeds video to the giant TV over HDMI.

Sound is currently using onboard SPDIF using a separate optical cable going to the amp.

I note the video card has a connector for SPDIF sound, ostensibly so sound can be ported over the HDMI cable as well. It works under Windows, but under 9.10 it doesn't. 

Before I start mucking about, does anyone know if it should work?

---

### Post by nickrout on 2009-12-19
It should do, this is a good resource:

[http://www.mythtv.org/wiki/AllensDigitalAudioHowto](http://www.mythtv.org/wiki/AllensDigitalAudioHowto)

---

### Post by GuiGuy on 2009-12-19
> **nickrout said:**
> It should do, this is a good resource:

[http://www.mythtv.org/wiki/AllensDigitalAudioHowto](http://www.mythtv.org/wiki/AllensDigitalAudioHowto)

Thanks

---

### Post by ian dobson on 2009-12-19
Hi,

It should work. I'm using SPDIF passthrough on my mythfrontend,  the graphic card is a 9600.

I had to unmute the IECxxxx in alsacontrol then change the default audio output device in alsa to point to the SPDIF output and set passthrough in mythfrontend.

Regards
Ian Dobson

---

