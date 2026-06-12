---
title: "Logitech Webcam mic problems with Ibex"
date: 2009-02-10
forum: Multimedia Software
---

### Post by am15 on 2009-02-10
I recently upgraded to Ubuntu 8.10 Intrepid Ibex.  I started using pulseaudio but it was giving me a lot of grief with weird errors so I removed it and went to esound.  Sound is working fine now except my Logitech Quickcam for Notebooks deluxe mic.  This was fine with Hardy and the drivers (it says) are preinstalled.  Why is it not coming up in Alsamixer or Sound settings as USB device then?

Here's what I get:

$ lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:08d8 Logitech, Inc. QuickCam for Notebook Deluxe
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Its obviously there but why is not working?

Please help otherwise I have to go back to Hardy :(

Aamina

---

