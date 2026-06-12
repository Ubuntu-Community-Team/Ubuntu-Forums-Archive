---
title: "Live installation using USB Key as Home Drive"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by couger77 on 2007-01-27
Ok gents,

I have successfully run Ubuntu live on my work laptop by booting with CD. I have also formatted a 1 GB USB key so that my settings will be saved without accessing internal HD.

Everything is peachy king, however, I would like to be able to watch my .AVI vids of The Office :P on the laptop in Ubuntu. But I get error:
[I]
                "You do not have a decoder installed to handle this file. You might 
                  need to install the necessary plugins"[/I]

Searching for the problem on everybody's favorite search engine came up with the solution: Add the following text to the /etc/apt/sources.list. Problem with THAT is it's on the CD, not the USB, which is the only media I can write to given its a LIVE Install. 

I am wanting to use VLC to view my vids. Any thoughts or solutions?

Thanks,

Jer

---

### Post by kidders on 2007-01-28
Hi there,

Theoretically, you could mount something on top of /etc ... say a small partition on your USB drive. That would let you modify your repository list. However, actually installing something would require even more parts of the system to be writable. Even if you *could* make it work, it's likely that your multimedia performance would be absolutely diar! After all, your LiveCD runs off an optical disc, has no swap, and would be writing to USB flash memory all the time. Alone, any one of these would kill Ubuntu's performance!

Maybe it's time to think about installing Ubuntu ... although I'm pretty sure you wouldn't be asking this question if there were a way for you to do so.

---

### Post by couger77 on 2007-01-28
Thanks for the reply

What if I were to install Ubuntu on the flash drive and run solely off that?

---

### Post by kidders on 2007-01-28
Hey again,

I'd say it would be intolerably slow, and could dramatically shorten your flash disk's lifespan. In any case, 1GB would be _miles_ too small. :-(

Is your laptop's hard disk too small for two OSs? (It's a tight squeeze on mine!) Personally, I'd go mad if I had to put up with LiveCD-style performance for any more than about half an hour! Would another (smaller) Linux distro be more suitable for you, maybe?

---

### Post by couger77 on 2007-01-28
I am using my company laptop which unfortunately is tighter than a drum when it comes to security. 

So I am basically hijacking everything but the HD to use it at home.

Everything is working great, if I could just figure out how to watch movies on the darn thing.

Thanks for your input just the same.

Jer

---

### Post by kidders on 2007-01-28
Ahhhh, now I'm with you. You're using a LiveCD because the laptop's own OS won't let you so much as swing a cat?

Well, it would be tough as hell for them to stop you putting Ubuntu onto it (effectively impossible, I think), although having said that, I imagine you'd prefer not to antagonise your company, right? Unfortunately, that really only leaves you with the option of installing Ubuntu on a USB hard disk ... assuming, of course, that the BIOS even supports USB boot-ups. Not all do.

I suppose there are two remaining alternatives:

1. Roll your own LiveCD. You could tune it to be as lightweight as humanly possible, and pre-install VLC on it. This would require quite a lot of work though.

2. Download VLC's or mplayer's source, compile it yourself, and run it in situ. This would be more realistic, but...
[LIST]
[*]I wouldn't attempt to compile it on a USB flash disk if at all avoidable. How much RAM do you have?
[*]I would be prepared to fail, since the LiveCD environment may not be able to handle large or complex media in any case.
[/LIST]

If you wanted to give #2 a try, I'd be pleased to help you out. Of course, if you don't feel like compiling the media player yourself, you *might* be able to find a plain old tarball. The idea would be that you would run it directly off your USB drive (ie without actually installing it).

**Edit:** One other suggestion just popped into my head. You could use the LiveCD to take a disk dump of your laptop's hard drive as it is right now, and completely re-install its current OS. If there came a time when you needed to put everything back the way you found it, you could just dump the image back onto your laptop.

---

