---
title: "Sony DCR-TRV140 digital video camera recorder and linux"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by matthew on 2007-02-24
I was given a Sony DCR-TRV140 digital video camera as a gift. It's at least 5 years old. I have the original windows drivers disk (98se, 2000, XP), but that isn't of much use in an all linux household. The camera works by itself quite well. I can't get it to connect in linux via the USB interface.

I'm using Ubuntu 6.10 with kernel 2.6.17-11-generic on a laptop with the specs outlined in the "my hardware" link in my sig.

Has anyone used one of these with Linux of any kind, particularly in Ubuntu? How did you get it recognized/connected?

I've tried google and found drivers for windows and macOS but not one "hey, it works on linux" story. When I plug the usb cable into my laptop and turn the camera on it shows up in the device listing.

```
lsusb

Bus 001 Device 006: ID 054c:0045 Sony Corp.
```I have no way to interface with the device, however, in any program like Kino, etc.

Any ideas out there?? I'm stuck.

---

### Post by matthew on 2007-02-24
I intended to include this and forgot...here's the relevant part of the output of lshw:> 
*-usb:1
                   description: Audio device
                   vendor: Sony Corp.
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.00
                   capabilities: usb-1.00 audio-control
                   configuration: driver=snd-usb-audio maxpower=300mA speed=12.0MB/s
It doesn't list any video capabilities.

I'll also add that the camera is known to work when using the proprietary Sony software on windows. That's not an option for me.

---

