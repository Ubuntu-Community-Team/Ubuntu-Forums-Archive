---
title: "Dell XPS m1710 Sub not working"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by SarahKH on 2007-01-27
Been playing with Ubuntu erm.. 6.10?  It's the one that doesn't play MP3's.  Anyone got the STAC 9200 to make use of it's subs? Or is it still a Windows only feature?

---

### Post by deadgobby on 2007-01-27
There reason mp3. will not play is because of codecs. You see they are not free, but there is a way to load them up. So there for you need to install the restricted codecs by you own hand.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 There is some scrip programs to automaticy load them up.
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
 Please read up before you install. 
Some people are able to play mp3's with out all those codecs using XMMS. That program can be found in Synaptic.
 However with all the cool codes install. Ubie rocks the house.
Gobby

---

### Post by SarahKH on 2007-01-27
Don't take this the wrong way. But, I already worked around the MP3 problem.  VLC, not pretty and doesn't like smb:// calls but kinda works.  Native MP3 support is on my list of things to work towards.  

The more important issue, is the lack of sub woofer.  I've seen some mentions of enabling the the mono channel kicking it in to life.  However, I can't seem to get this going using, either of the two CLI ALSA utilities.  Without it, the audio is less than pleasing...  any advice or cheats happily accepted.

---

### Post by mac.ryan on 2007-02-15
I have the same problem (lack of subwoofer) anybody managed to work it out?

The only contribution I can do to the discussion is mentioning this thread:
   [http://www.linlap.com/forum/viewtopic.php?t=38](http://www.linlap.com/forum/viewtopic.php?t=38)

At the moment there is nothing interesting there, but being on the same topic maybe in the future... :-/

---

### Post by m94mni on 2007-02-20
This is a known issue in alsa, and might be fixed in Feisty.

See [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2580](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2580)

You can solve it in the meantime by adding

snd-hda-intel model=ref

to /etc/modules. (Not 100% sure that actually works on edgy - you might need newer ALSA sources, which makes things a bit more complicated...)

---

