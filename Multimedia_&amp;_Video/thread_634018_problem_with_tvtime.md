---
title: "problem with tvtime"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by augusto_sf on 2007-12-07
I have downloaded and installed "TVtime" unfortunatelly it doesn't work. It just opens a window and closes it inmediately.

My OS is Ubuntu 7.10 and my lspci -v:

03:02.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR 150
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

Any help will be most appreciated.

Augusto

---

### Post by eldragon on 2007-12-07
check /etc/X11/xorg conf

go to the Device section 

```

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

```

thats what i got, i think you are missing the "VideoOverlay" option if im not mistaken.

---

### Post by Offoffoff on 2007-12-09
Another problem:
How to run tvtime like mplayer -vo x11? It tries to play on xv and plays good, but for me it is so ugly, when I drag window - video lingers.
And one more:
I can not get working sound to tvtime from every my sound sources in tv tuner (I have 03:02.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01), i.e. BeholderTV M6 Extra with audio-out pass, audio-PCI pass).

---

### Post by augusto_sf on 2007-12-15
Thanks Eldragon. 
I modified xorg.cong as you suggested and I now can see the TV screen which is a definitive progress. The problem now is that there is no image on the screen. I think the PC is incorrectly pointing to the Webcam and sends the message "no video source". I tried to change this in 'Setup>Input configuration>change video source' but the machine doesn't allow me to change anything in this option.
Have you got any idea of what to do?

Again thanks a lot for your help.

Augusto

---

