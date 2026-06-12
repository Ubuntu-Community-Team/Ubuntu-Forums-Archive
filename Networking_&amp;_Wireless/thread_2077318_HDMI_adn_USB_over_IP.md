---
title: "HDMI adn USB over IP"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by Scripting22 on 2012-10-28
Hello,

I'm looking for a way to send USB and HDMI signals over IP. Is there any software available for this purpose?  For USB sending there is USBIP, but I'm not sure if this will be good enough.

On one end of the line is a Kubuntu laptop, on the other end there is a Raspberry Pi and in the middle my router. So my goal is that the laptop connects wireless to the router, connects wired to the raspberry Pi and is able to stream all USB and HDMI signals to the Pi. On the Pi is a HDMI screen connected and some USB devices.

I've been searching on the internet for good documentation on these topics, but so far the information I found is very fragmented and unclear. The best way to do it would be to create an USB server, but I'm not sure if the samen is possible for HDMI . Any help or pointing in the right direction would be appreciated!

Cheers!

---

### Post by DAFlippers on 2012-10-29
> **Scripting22 said:**
> On one end of the line is a Kubuntu laptop, on the other end there is a Raspberry Pi and in the middle my router. So my goal is that the laptop connects wireless to the router, connects wired to the raspberry Pi and is able to stream all USB and HDMI signals to the Pi. On the Pi is a HDMI screen connected and some USB devices.
 
You could stream HDMI content using VLC however I suspect you are thinking of using the RPi as a client to provide remote display and USB connectivity. It really would help to know what you want to achieve.
 
Be aware that there are USB issues with RPi.
 
David

---

