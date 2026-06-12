---
title: "Can't Play .VGZ file"
date: 2010-10-27
forum: Multimedia Software
---

### Post by dogbitedavehumphreys on 2010-10-27
Folks:

Am running Lucid and am attempting to open a .vgz file from a security camera and just can't.  Have attempted to open them with VG Player_En.exe in Wine but can't because it is .exe and Gecko only wants to open the audio, which there isn't.

Have looked for solutions in threads, etc. but am coming up short.

Any help here would be greatly appreciated.

v/r

dogbitedavehumphreys

:guitar:

---

### Post by coffeecat on 2010-10-27
I have no experience of vgz files, but according to this:

[http://en.wikipedia.org/wiki/VGZ_Video](http://en.wikipedia.org/wiki/VGZ_Video)

...they are compressed. Have you tried unpacking them with Right-click > Open with Archive Manager? If that doesn't work, one google hit suggested you need to use an extraction app that recognises RAR files. A search of the forum should bring up which packages you need for this.

Once you've uncompressed the file, I would think the best bet would be the Swiss Army knife of media players, VLC. It's in the repo.

---

### Post by mc4man on 2010-10-27
> Have attempted to open them with VG Player_En.exe in Wine but can't because it is .exe

The player can open fine in wine (tried VG player 5.1 and 5.5) - whether it works can't say, don't have any .vgz files nor much hope of finding any.

If wine is refusing to run the player just r. click on the .exe -> properties -> permissions and enable the 'Allow executing file as program'
(or 'execute' box if using advanced permissions

---

### Post by dogbitedavehumphreys on 2010-11-07
Thank you Coffeecat and mc4man for the replies.  I tried to open up the files on another machine running Lucid and it works and another running Jaunty and it basically works (Jaunty is on a netbook and the screen is real small which is causing some problems with the player controls).

At this time, I am going with bad Wine install on the first Lucid machine.

Thanks again for your timely responses, power to the people.

---

