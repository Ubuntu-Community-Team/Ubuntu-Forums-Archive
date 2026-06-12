---
title: "Using NVidia PureVideo DVD Decoder"
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by fatalGlory on 2008-03-14
I recently tried to watch a DVD in feisty and discovered that (to my surprise) libdvdcss2 was not quite decrypting it properly.  It managed to see some of the first title but then any player that tried to read past that point would crash (tried VLC, MPlayer, Totem-xine).  It seems that libdvdcss2's decryption is not as flawless as I thought (this is a copy protected DVD).

I verified that this was true for any case with libdvdcss2 by using the dvd with VLC on winXP (which has libdvdcss2 installed by default).

I was forced to reboot to windows to watch the DVD where I have the NVidia PureVideo DVD decoder available.  I have a license for this decoder, is there any way to use it in Linux and save me a reboot just for a few DVDs?

---

### Post by fatalGlory on 2008-03-14
Was able to rip disc by using a DVDFab Decrypter install copied over from windows in wine (the installer crashes in wine).  So that works if your stuck - but its a lot of effort to go to (and disc space to use) just to watch a movie.

---

