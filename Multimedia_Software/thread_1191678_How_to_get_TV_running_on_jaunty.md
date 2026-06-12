---
title: "How to get TV running on jaunty"
date: 2009-06-19
forum: Multimedia Software
---

### Post by joy83 on 2009-06-19
So I bought this new desktop Gateway LX 6810-01 which came with Vista home premium and a TV tuner card with remote. I set up Windows media center and hooked my tv cable to the desktop and everything is fine I can watch TV and change channels and record and do everything. 

But I never intended to run windows so I installed Jaunty and now wondering how do I get back the old media center here so that I can watch TV. I know it prolly wont be as cool as WME but still even if I can watch TV it will be more that enough. I have tried Myth TV and ME TV but couldnt succeed. 

Anybody have any suggestions on what I need to do in order to get the TV running on my dektop? Thanks

---

### Post by lovinglinux on 2009-06-19
I would recommend setting up your TV card with a simpler applications first, like TVTime or Kaffeine. Once the TV card is working, then move into a full featured media center like MythTV, [Freevo](http://en.wikipedia.org/wiki/Freevo) [wikipedia.org] or others. I don't know if they offer TV card capabilities, but there is also [Moovida](http://en.wikipedia.org/wiki/Moovida), [XBMC](http://en.wikipedia.org/wiki/XBMC) and [Boxee](http://en.wikipedia.org/wiki/Boxee) [wikipedia.org].

For additional support, would help if you could specify your TV card model, if it is analog, digital or hybrid, because not all programs work wit all of them and configuration varies.

I have an analog TV card (Pinnacle PCTV) and configured it [this way](http://ubuntuforums.org/showpost.php?p=5971890&postcount=2).

---

### Post by joy83 on 2009-06-19
> **lovinglinux said:**
> I would recommend setting up your TV card with a simpler applications first, like TVTime or Kaffeine. Once the TV card is working, then move into a full featured media center like MythTV, [Freevo](http://en.wikipedia.org/wiki/Freevo) [wikipedia.org] or others. I don't know if they offer TV card capabilities, but there is also [Moovida](http://en.wikipedia.org/wiki/Moovida), [XBMC](http://en.wikipedia.org/wiki/XBMC) and [Boxee](http://en.wikipedia.org/wiki/Boxee) [wikipedia.org].

For additional support, would help if you could specify your TV card model, if it is analog, digital or hybrid, because not all programs work wit all of them and configuration varies.

I have an analog TV card (Pinnacle PCTV) and configured it [this way](http://ubuntuforums.org/showpost.php?p=5971890&postcount=2).

Since the card came with the desktop, i tried to search the manufacturer of the card without any success, this is the best I could find from the Gateway website 

Hybrid analog (NTSC/PAL/SECAM) and digital (DVB-T or ATSC format) TV tuner card, supporting hardware or software MPEG-2 stream encoding

Dont know if that will help.

---

### Post by lovinglinux on 2009-06-19
> **joy83 said:**
> Since the card came with the desktop, i tried to search the manufacturer of the card without any success, this is the best I could find from the Gateway website 

Hybrid analog (NTSC/PAL/SECAM) and digital (DVB-T or ATSC format) TV tuner card, supporting hardware or software MPEG-2 stream encoding

Dont know if that will help.

Yes, it helps. But unfortunately I have no experience with hybrid cards. Nevertheless, I'm sure someone will help you soon. Meanwhile, you might want to check these links:

**Quick links to similar threads:** [Google Site Search](http://www.google.com/search?q=dvb tv card+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0)

---

### Post by rightasrain on 2009-06-21
My gateway LX6810-01 shipped with an Avermedia M791 

[http://support.gateway.com/s/vidcard/AVerMedia/6008105R/6008105Rnv.shtml](http://support.gateway.com/s/vidcard/AVerMedia/6008105R/6008105Rnv.shtml)

I could only assume they all ship with the same model of tv tuner. I haven't got it running in ubuntu yet. I'm working on getting the remote to work. You might check out this site for the remote

[https://wiki.ubuntu.com/LircHowto](https://wiki.ubuntu.com/LircHowto)

Does anyone know what kind of remote the LX6810-01 ships with?

---

### Post by emal011 on 2009-06-22
Hey!

I have a Pinnacle SatPro Pci, and want to know, How can I mke sun with ubuntu 9.04?

lspci:
```
01:0a.0 Multimedia controller: Pinnacle Systems Inc. Royal TS Function 1
01:0a.2 Multimedia controller: Pinnacle Systems Inc. Royal TS Function 3
```lspci -v

```
01:0a.0 Multimedia controller: Pinnacle Systems Inc. Royal TS Function 1
    Subsystem: Pinnacle Systems Inc. Device 0048
    Flags: bus master, medium devsel, latency 128, IRQ 11
    Memory at dbfff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

01:0a.2 Multimedia controller: Pinnacle Systems Inc. Royal TS Function 3
    Subsystem: Pinnacle Systems Inc. Device 0048
    Flags: bus master, medium devsel, latency 128, IRQ 11
    Memory at dbffe000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
```where i can find info for make it possible to use?

---

