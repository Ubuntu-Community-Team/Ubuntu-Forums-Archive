---
title: "Help MP3's were playing but aren't now."
date: 2006-12-24
forum: Multimedia &amp; Video
---

### Post by raid517 on 2006-12-24
Hi when I first installed Ubuntu Breezy 6.10 one of the first things I did was run automatix and install all of the required win32 codecs and so on. After doing this I was able to play MP3's normally. However after a recent batch of updates, both Amarok and Kaffeine have suddenly decided to stop playing MP3's.

The only common thread I can find between them is the xine engine - so I can only assume that MP3 support in the included xine-engine in Ubuntu has been disabled (as is the case on Suse).

The question is how do I re-enable it?

I would try automatix again, however since originally installing Breezy 6.10, I have now upgraded to the Feisty repositories  and now automatix will no longer run and it claims it is not compatible with that version of Ubuntu.

Something else that is odd that I noticed too however is that many KDE specific apps have stopped being able to play MP3's, like Amarok, Kaffeien, Kaboodle and so on - and I can no longer sample/preview MP3 music files in konqueror either - but all non KDE specific apps can still play MP3's - such as XMMS, Real Player, MPlayer and so on. So this seems to be related to KDE somehow.

Can anyone advise what might be going on?

---

### Post by raid517 on 2006-12-24
Bump...

---

### Post by clueless on 2006-12-28
Same thing happened to me today... I didn't even restart or turn off the computer. Just woke up, started Amarok and there was no mp3 support. I read somewhere in this forum that changing output from Alsa to OSS or viceversa and then back to the original helped, but not in my case. So...
Bump

---

### Post by clueless on 2006-12-28
Apparently this is not a very common problem, but has happened before. [This link]("http://linuxfud.wordpress.com/2006/12/03/amarok-suddenly-stops-playing-mp3s/") helped me, I hope it is good for you too.

---

### Post by T113 on 2007-09-07
You, Sir, are my Hero.

The article mentioned tells you to delete your ~/.xine folder.

Only thing in there is a file called catalog.cache where xine apparently keeps track of its components.  I renamed said file to catalog.cache.wtf and xine created a nice new one, and amarok now plays MP3's again.

Was pulling my scant few hairs out over this.
Reinstalled the codecs, no joy.  Removed amarok, rebooted and reinstalled, no joy.  Ran the install-mp3 script in the amarok folder,no joy.

Thanks again!
:guitar:

FWIW, Kubuntu Feisty - Amarok ran fine until the most recent updates.

---

