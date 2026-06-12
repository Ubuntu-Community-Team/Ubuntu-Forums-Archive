---
title: "MP3 Lenghts"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by tommoyer324 on 2007-07-25
I have a large number of MP3 files that I used soundconverter to create, and the lengths are all over the place (anywhere but correct).  Is there a program I can use to easily fix the lengths of these files?  I'm looking for something that is automatic or can be easily automated since I have several gigs and don't want to do them one at a time.

---

### Post by diafygi on 2007-07-29
There is a discussion of this bug at [http://ubuntuforums.org/showthread.php?t=368046](http://ubuntuforums.org/showthread.php?t=368046)

This is also a registered bug for soundconverter at [http://developer.berlios.de/bugs/?func=detailbug&bug_id=8117&group_id=3213](http://developer.berlios.de/bugs/?func=detailbug&bug_id=8117&group_id=3213)

I would recommend a nautilus script for the bulk sound conversion:
-go to synaptic package manager and install "nautilus-script-manager" and "nautilus-script-audio-convert"
-make sure you "lame" installed as well
-go to the terminal and type "nautilus-script-manager enable ConvertAudioFile"
-when you open nautilus file windows again you should be able to highlight files and right click > Scripts > ConvertAudioFile.

I also use "Audio Tag Tool" to modify multiple Id3 tags.

---

### Post by tommoyer324 on 2007-08-01
I fixed this by using CBR instead of VBR.  May not be the best solution, but it works for now.

---

