---
title: "Problems with audio cds"
date: 2008-08-07
forum: Multimedia Software
---

### Post by lastchancetosee on 2008-08-07
I have the following problem:

1) when I insert an audio CD no audio-CD-icon appears on the desktop (works fine for DVDs or data-CDs/DVDs), plus the drive is not blocked as it usually is.
2) Clicking 'Add CD' in Audacious does nothing (as opposed to returning an error with no Audio-CD in the drive), totem has the 'Play Audio-CD'-option displayed but greyed.
3) autoplay (audacious, totem) doesn't work either (again, this works with DVDs and data-CDs (although two instances of thunar are opened when inserting data CDs))

HOWEVER

4) opening the audio-CD in VLC works fine


What I really don't understand is that on some level the system seems to notice that there is an audio-CD present (see 2) ) but doesn't seem to want to have anything to do with it ...

---

### Post by lastchancetosee on 2008-08-07
Update:

- I had removed the CD/DVD-drives from fstab because them beeing in there had always caused errors when loading DVDs, because the system tried to mount an already mounted device. So I tried it again with the drives present in fstab, which didn't help - no surprise since Audio-CDs aren't mountable anyway, right?

- I tried playing Audio-CDs with Banshee and Amarok, no problem. Banshee complains about DBus not beeing properly set up on my system. I don't know what DBus is (i was going to research that, but not tonight) but somehow I don't get the feeling that that's what is going wrong.

I could of course 'solve' the Audacious-problem by switching to Banshee or Amarok, but I'd still like to know what's wrong/get the icon on the desktop.


So, new question I guess: What is it that the system, totem and audacious do fundamentally different from Banshee, Amarok & Co.?

---

