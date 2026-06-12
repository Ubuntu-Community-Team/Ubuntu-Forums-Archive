---
title: "mp3 file that won't play in VLC if .mp3 is attached!"
date: 2008-11-19
forum: Multimedia Software
---

### Post by endersbean3k1 on 2008-11-19
Hey guys, really strange issue here. I have this file, it's an mp3 (right-click->Properties shows Type: MP3 Audio). When the .mp3 extension is in the file name, VLC won't play it! (Amarok does though, I'll get into why this is still a problem later). Knowing that .mp3 isn't really needed in linux, I chopped it off. It plays. Even added .wma, still plays. 

So when I take this file into a windows VM and try to open it with Sound Forge, no dice. 

Anyone know what the deal with this file might be? I've actually got a folder, of which only one of these mp3s works normally, about 10 of them exhibiting this behavior.

Thanks in advance.

---

### Post by aeiah on 2008-11-19
in a terminal, navigate to the directory it's in and ```
file filename.ext
```

eg:
```
$file Pigbag\ -\ Papa\'s\ Got\ A\ Brand\ New\ Pigbag.wrong_extention 
$Pigbag - Papa's Got A Brand New Pigbag.wrong_extention: Audio file with ID3 version 23.0 tag, MP3 encoding
```

---

### Post by endersbean3k1 on 2008-11-20
I consistently get

```
$file [Filename].mp3 
$[Filename].mp3: Audio file with ID3 version 23.0 tag, MP3 encoding
```

But I already knew the files were actually mp3s, which is what's so strange... they only don't work in vlc when they're labeled as mp3s.

Here's what I've done: Converted the files to .wav, and was then able to take them into Sound Forge, which was really the issue. If anyone knows what was going on though, I would love to hear ideas. I might have a hack-ish workaround at this point, but it's still really weird.

---

### Post by Eiríkr on 2009-02-15
I've got the same symptoms.  

[LIST][*]Fully updated Ubuntu Ibex, using generic kernel
[*]VLC v 0.9.4[/LIST]

VLC will play some .mp3 files with the extension attached.  VLC will also *not* play some .mp3 files, **unless the ".mp3" filename extension is removed or changed**.

File results for two sample files chosen at random from my collection:

```
eirikr@Boreas:/mnt/shared/Music/@SW/XTC/English Settlement$ file ./01\ -\ Runaways.mp3 
./01 - Runaways.mp3: Audio file with ID3 version 2.3, MP3 encoding
...
eirikr@Boreas:/mnt/shared/Music/@SW/Banco De Gaia/Farewell Ferengistan (2006)$ file ./01\ -\ Farewell\ Ferengistan.mp3 
./01 - Farewell Ferengistan.mp3: Audio file with ID3 version 2.3, MP3 encoding
```

VLC will play the XTC file, but not the Banco de Gaia file, unless I remove or change the .mp3 filename extension.  

VLC generates zero errors on the CLI when failing to play.  When VLC fails to play, it apparently opens the file, as the filename flashes across the GUI for a split second, but the file is shown as being 00:00 long.  Hitting the Play button just makes the filename flash again.  

After removing or changing the filename extension, VLC will play the file, but will show only --:-- as the file duration.  The current time position for the track appears to display correctly.  

[SIZE="3"]**Possible Clue**[/SIZE]

Examining the files more closely, I find that the XTC file that VLC will happily play is a set bitrate, 320kbps in this case.  Meanwhile, the problematic Banco de Gaia file is set at a variable bitrate, showing as 239kbps in the file properties as viewed in Nautilus.  Could it be that VLC is choking on VBR files with ".mp3" file extensions?  endersbean3k1, can you confirm this -- are your problematic files also VBR?

This sure sounds like a bug to me...

Cheers,

-- Eiríkr

---

