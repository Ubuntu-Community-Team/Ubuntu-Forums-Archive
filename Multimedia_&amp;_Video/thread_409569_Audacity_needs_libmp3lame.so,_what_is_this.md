---
title: "Audacity needs libmp3lame.so, what is this?"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by rainwalker on 2007-04-14
I used Audacity to cut a little bit off of the beginning of a song, and now I'm trying to export it as an mp3. When I try to do this, it says it doesn't export mp3 files directly, but instead uses the LAME library to handle the encoding. I'm supposed to obtain the libmp3.so separately, then locate the file for Audacity.
It says I can obtain it either by downloading it or building it from source, but I can't find it in Synaptic.
I found it on Sourceforge at [http://sourceforge.net/project/showfiles.php?group_id=290&package_id=309&release_id=450142](http://sourceforge.net/project/showfiles.php?group_id=290&package_id=309&release_id=450142)
but I have no idea where to go from there. Do I save it to disk or open it with "/bin/tar (default)"?

Thanks!

---

### Post by Nate53085 on 2007-04-22
Type into a terminal:

sudo apt-get install lame

This will install lame.  Then try to export as mp3.  Audacity will ask your for the location.  The file is 
/usr/lib/libmp3lame.so

---

### Post by jpeddicord on 2007-04-22
> **Nate53085 said:**
> Type into a terminal:

sudo apt-get install lame

This will install lame.  Then try to export as mp3.  Audacity will ask your for the location.  The file is 
/usr/lib/libmp3lame.soActually, the file is **libmp3lame.so.0**. Audacity will warn you about a bad filename, but it is the one you want. :)

Jacob

---

### Post by Nate53085 on 2007-05-01
> **jacobmp92 said:**
> Actually, the file is **libmp3lame.so.0**. Audacity will warn you about a bad filename, but it is the one you want. :)

Jacob

the .so is there without installing lame, once you install lame the regular file is there

---

### Post by BeastlyKings on 2007-08-14
Umm, I did sudo apt-get install lame but I still can't find that file, or anything that even looks like it at all. Help?

---

### Post by linux_rocks on 2007-08-14
> **Nate53085 said:**
> Type into a terminal:

sudo apt-get install lame

This will install lame.  Then try to export as mp3.  Audacity will ask your for the location.  The file is 
/usr/lib/libmp3lame.so

This worked...just it was /usr/lib/libmp3lame.so.0

Audacity warned about the file name but it still worked! :)

---

### Post by aysiu on 2007-08-15
This should help:
[http://psychocats.net/ubuntu/audacity](http://psychocats.net/ubuntu/audacity)

---

### Post by thecrwth on 2008-01-25
I have a similar problem, but I have LAME and AUDACITY installed.  LAME is latestet per sudo get-apt run today.  Still no libmp3lame.so.  Also Audacity does not offer me the options to choose file formats.  It just lets me chose a playback and recording device.

---

