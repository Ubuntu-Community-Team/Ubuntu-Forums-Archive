---
title: "HP webcam support"
date: 2006-10-04
forum: Multimedia &amp; Video
---

### Post by digilink on 2006-10-04
I recently bought an HP webcam that I want to use under Ubuntu. It's an HP PG088AA. I have no clue what chipset is in it, and I have not found anything on countless google searches. 

I don't even really know where to begin as I have never used a cam under linux. 

Anyone know if this cam even works under linux or of a way to make it work?

---

### Post by pgatrick on 2006-10-04
Don't know too much about it, but first step I guess is to see if ubuntu recognizes it.. Try lsusb to see what's plugged in, it should tell you the chipset, then look that up. spca5xx ov511 etc are some of the more common drivers afaik.

---

### Post by digilink on 2006-10-04
It does appear to recognize it:

```
Bus 001 Device 003: ID 05a9:8519 OmniVision Technologies, Inc.
```

Now where to go from here!!!???? I am a real n00b when it comes to this type of thing.

---

### Post by pgatrick on 2006-10-06
[www.ovcam.org/ov511](www.ovcam.org/ov511) is probably a good place to start,I think that's the driver you'll need, if your webcam is supported.

---

