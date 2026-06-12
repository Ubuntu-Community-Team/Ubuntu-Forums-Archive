---
title: "DVD movie won't mount"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by jmetal88 on 2007-10-28
I have a DVD here that I'm having trouble getting to mount in Gutsy. The DVD is a History of the World Part I that I bought at Wal-Mart. It played on Windows XP after I installed VLC and an extra mpeg2 codec, although it would only load up if I inserted the disc after breathing on it (don't know why). It played fine on my set top DVD player (CyberHome), but I no longer have that with me. When I insert the DVD while Xubuntu is booted up, the drive LED lights up and I can hear the disc spinning, which it does for a minute or so, then the LED starts slowly blinking, stops, and no DVD icon appears on my desktop. All my other DVDs work on this setup, even auto playing. My drive is a Lite-On, I don't remember the model number, but it had the number 18 in it, if that helps. Anyone else have this particular DVD you could try out and see if it works on you machine, or has anyone else even had this problem?

Thanks.

---

### Post by sonicsmooth on 2007-10-29
I'm having a mounting problem too.  I've learned a few things; the following might help.

1.  Can you mount a normal data cd in the drive?

Assuming your dvd is /dev/hdb (as it is in mine),
2.  Do you have /dev/cdrom pointing to /dev/hdb?
3.  Do you have /dev/dvd pointing to /dev/hdb?
4.  Do you have /media/cdrom0 pointing to /dev/hdb?
5.  Do you have /medo/cdrom pointing to /media/cdrom?

I think that's how it's supposed to be set up.  For me it's still not working, so I can't vouch for this, but i hope it helps.

Michael

---

### Post by jmetal88 on 2007-10-29
I'm sure everything's fine there, it's just the one DVD (History of the World Part 1) which won't mount. Everything else is fine.

---

### Post by jmetal88 on 2007-11-06
OK, I think the problem is something to do with the DVD's copy protection and my drive (like my drive has a hard time reading through it or something) 'cause all of a sudden the DVD just mounted, out of the blue.

---

### Post by jmetal88 on 2007-11-06
OK, I upgraded the drive's firmware, and it seems to like the DVD a whole lot better now.

---

