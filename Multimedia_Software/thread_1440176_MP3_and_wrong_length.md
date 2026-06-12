---
title: "MP3 and wrong length"
date: 2010-03-27
forum: Multimedia Software
---

### Post by KillKRT on 2010-03-27
Hi!

 I have a problem with any MP3s and their length.
 Some players (such as Amarok and my car player) report a wrong length, so seeking becomes impossible!
 I noticed Amarok reports: 
 Bitrate: 128kbps
 Samplerate: 32KHz 

 While VLC:
 Bitrate: 320kbps
 Samplerate: 44KHz 

 That I assume to be the correct one! ;)

 I've already tried to fix this problem using **mp3check --fix-headers**, but it seems not work, it only returns this warning:

```

131072 bytes of junk before first frame header

```

 But it doesn't *fix* the MP3 header!
 Could you help me suggesting me a tool/script to fix this problem?

Tnx!

P.S.:
Sorry for my english! :redface:

---

### Post by TheBigBakedBean on 2010-09-28
If the MP3 files are encoded with variable bitrate (VBR), you can try VBRFix:
```
sudo apt-get install vbrfix
```

Sometimes the value in the 'length' tag (even of constant bitrate, or CBR, MP3s) is incorrect, so you'll need to remove it.  I'm not aware of any GUI mp3 tag-editing software that allows you to edit the 'length' tag, but if you're brave enough, you can write a perl script that uses MP3::Info ([FONT="Courier New"]libmp3-info-perl[/FONT]) to remove it.  If not, there's a Windows program called Mp3Tag (works in wine) that is capable of removing the 'length' tag.

---

