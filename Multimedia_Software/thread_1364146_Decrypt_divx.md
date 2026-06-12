---
title: "Decrypt divx"
date: 2009-12-25
forum: Multimedia Software
---

### Post by neojames on 2009-12-25
For Christmas I received the new star trek movie on a usb stick. To decrypt it I have to go to a website and at the end I get given a .tix file. What am I meant to do with this file on linux?

---

### Post by lovinglinux on 2009-12-25
This is the first time I hear about a .tix file, but I did some research and found this:

> From: [http://www.filesuffix.com/extension/tix.html](http://www.filesuffix.com/extension/tix.html)

TIX file is a DivX Ticket. When you pay for a video on a DivX partner's website, you are first served a TIX file. It is an empty file that triggers the download of the video (DIVX file) when opened in the DivX Player. Once the video file has started download, the TIX file should disappear.

So I guess you could try to download the Windows version of the DivX player from [http://www.divx.com](http://www.divx.com), then install it with Wine, start it and open the .tix file to get the real video. I'm not sure if it will work tho, so if you can backup your .tix file I recommend doing it.

BTW, the movie is really good. The best movie I have seen this year.

---

### Post by lovinglinux on 2009-12-25
Update: [http://ubuntuforums.org/showthread.php?t=1356363](http://ubuntuforums.org/showthread.php?t=1356363)

I'm afraid you are out of luck.

---

### Post by neojames on 2009-12-26
Oh dear, if I decrypt it in virtual box (I have windows there) than transfer out of the virtual hd the decrypted movie will it work?

---

### Post by lovinglinux on 2009-12-26
> **neojames said:**
> Oh dear, if I decrypt it in virtual box (I have windows there) than transfer out of the virtual hd the decrypted movie will it work?

I'm afraid not. Take a look at [DivX DRM page](http://www.divx.com/en/partner/content-distribution/content-protection). It seems it only plays on DivX products somehow associated with the user, to limit distribution. You can copy, but if you are not the authorized user, then you can't watch it. I guess the player must contact DivX servers before playing to authenticate the user somehow. 

Now you understand why a lot of people hate DRM. It doesn't stop piracy and just annoy legitimate buyers.

If I were you, I would contact DivX for instructions. If they say you cannot play it outside a DivX player/Windows, then request your money back.

---

### Post by neojames on 2009-12-26
What about viewing it in virtual box, I've got a win PC I can play it on (my dads) but it would be nice...

---

### Post by lovinglinux on 2009-12-26
> **neojames said:**
> What about viewing it in virtual box, I've got a win PC I can play it on (my dads) but it would be nice...

Yep, that's a "solution".

---

### Post by neojames on 2009-12-26
Hopefully divx may make a linux version now that linux is gaining momentum, until then I'll have to use virtualbox.

---

