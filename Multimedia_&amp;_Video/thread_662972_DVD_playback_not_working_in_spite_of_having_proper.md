---
title: "DVD playback not working in spite of having proper libraries"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by Barrett1734 on 2008-01-09
As the title says, I have installed gstreamer, ubuntu restricted extras and xine and nothing has worked. When I try to playback the files in Totem it tells me to download libdvdcss, which I have. The same happens when I try to rip the discs using Thoggen. I'm completely out of ideas.

---

### Post by barisurum on 2008-01-10
try the last entry on this threat:

    [http://ubuntuforums.org/showthread.php?t=662353](http://ubuntuforums.org/showthread.php?t=662353)

---

### Post by Barrett1734 on 2008-01-10
If I set a region code, am I limited in the number of times I can change it like I would be under windows?

---

### Post by Yellow Pasque on 2008-01-10
> **Barrett1734 said:**
> If I set a region code, am I limited in the number of times I can change it like I would be under windows?
I believe so. It's a device limit, not a Windows limit.

---

### Post by Barrett1734 on 2008-01-10
That's what I thought. Too bad.

---

### Post by AJB2K3 on 2008-01-10
Im getting the same but when i ran gxine I found the fault. the dvd is scrambled/encrypted.
bah have to get my xp machine set back up.:(

---

### Post by AJB2K3 on 2008-01-10
Solved, just install dvdcss2 using the guide featured some ware.

---

### Post by manimal347 on 2008-01-10
Yes, libdvdcss2 isn't included in ANY official Ubuntu repository as it's usage is illegal in many if not most locales. Indeed, the cracking of CSS code caused a flurry of lawsuits and DMCA takedowns, culminating in the arrest of some kid, back in 2000 or so. There have been few threats since, but most Distrubtions are still understandably skittish about codecs, especially when we remember the LZW/GIF and Fraunhoffer/free MP3 encoders Internet drama that spurred PNG and OGG.. Unless you use VLC (probably also illegal) or have a Dell that runs Dell-shipped Ubuntu, you'll need libdvdcss2 to watch most commercially sold DVD's.

If you want the file and believe it is compatible with your current legal climate, add the Medibuntu repository.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) (tells you how...)

Then, either grab "libdvdcss2" through searching synaptic Synaptic, or get it with "sudo apt-get install libdvdcss2" using your terminal or terminal emulator (eg, Xterm, Konsole, Eterm).

While you're at it, grab the also legally questionable win32dcodecs if you can. They will enable such goodies as Realplayer and WMV decoding.

Both these files SHOULD work with Totem on both the Xine and Gstreamer backends, Gxine, as well as MPlayer (Highly recommended), Ogle (libdvdcss2 only), Kaffeine (KDE) and many other common media/DVD players.

---

### Post by Barrett1734 on 2008-01-10
I installed all the medibuntu libraries and codecs and Totem still won't playback dvds. I also changed the region code on my drive, which didn't help either. What it did seem to do was smooth out the previously jagged playback of VLC. This is acceptable, since VLC is certainly a better player than Totem to begin with.

---

### Post by Jerrac on 2008-01-10
Well, it won't work for me. The dvd's menu will show up, but playing the actual video gives me: The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

totem-xine is installed, libdvdcss2 is installed, my region is set right. So, any clues?

---

### Post by Barrett1734 on 2008-01-11
Totem still will not playback DVDs for me either, try VLC and see if that works. Every other application I've tried; Acip Rip, DVD Rip, Thoggen, VLC and GXINE all seem to work, but Totem just wont.

---

### Post by Jerrac on 2008-01-11
Well, no program works for me. Though I tried an older DVD I had and it worked fine. Did they upgrade the encryption on the new releases?

---

### Post by Barrett1734 on 2008-01-11
I believe that there is a new type of macrovision protection on newer discs, but this shouldn't be an issue.

---

