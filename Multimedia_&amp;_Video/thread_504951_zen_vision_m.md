---
title: "zen vision m"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by vamsi80us on 2007-07-19
im on ubuntu fiesty

im unable to even see my zen recognized using lsusb.. any help is appreciated.

---

### Post by bdtgp on 2007-07-19
are you saying it doesnt show up in the file browser or what?  more detail is needed.

---

### Post by Devikyn on 2007-07-19
I'm likely having the same problem as him. On the Creative website they say Linux doesn't support most of their products, which kind of sucks, as I have a ZEN VIsion:M, SBS 580, and Sound Blaster Audigy SE. It's the same as if you were using Windows and didn't have the drivers installed.. it just plain doesn't recognize the ZEN. You can plug it in and charge it and all that jazz, but you can't copy any of your data off of it because there's no way to get to it. Is there a way to fix this? I'd assume not, but you never know..

Also, I'm having trouble with my SBS 580 surround system in that it won't play any sound whatsoever. If anyone has any helpful links or advice to give about that I'd appreciate it. I just installed Ubuntu today and I'm still learning the basics. :P

---

### Post by vamsi80us on 2007-07-22
after i connect my zen to the usb drive.  i check lsusb to see anything is detected.. only my mouse which is connected to the other port its detected.  i also tried insalling libmtp, libusb, amarok as suggested by others but those wont do much until the computer shows that it is connected right... 

btw, the zen does not charge even when it is connected.. works fine (as expected) in xp and vista

result of lsusb:
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by Arrdee on 2007-07-25
I've got one of these, and I use Gnomad 2 to manage my music/videos on it.

Pretty sure it's in the repos, too.

---

### Post by PrestonHerrmann on 2007-07-28
Amarok is also a great program for transferring music. No video support, but that can all be done in gnomad, 

By the way, If anyone tried to copy music from the Zen back to their computer in either gnomad or amarok, lemme know how that goes, I experienced a few annoyances when I did, and found that the programs couldn't handle all the music in one big transfer, but only by individual chunks, like one artist at a time.

---

### Post by vamsi80us on 2007-08-01
finally figured out that the "noapic nolapic" boot option causing USB 2.0 devices to not be recognized.   anyways amarok detects but it cannot play the music from the device... transfers to zen are working tho.   any help?

---

