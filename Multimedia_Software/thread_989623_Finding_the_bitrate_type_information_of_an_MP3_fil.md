---
title: "Finding the bitrate type information of an MP3 file"
date: 2008-11-21
forum: Multimedia Software
---

### Post by kung fu buntu on 2008-11-21
I have several mp3 files and I would like to know if they are VBR or CBR.
Amarok and Konqueror can give me information on the bitrate value, however they don't tell me if it's VBR or CBR.

I'm almost sure that some of my files are VBR, but amarok and konqueror just give me a value for the bitrate, and don't tell me if they are VBR or not.

Any idea?
Thanks!

---

### Post by mc4man on 2008-11-22
you might want to try MediaInfo, it's availabe in cli or gui. the gui is very basic but gets the job done.
There may be a .deb around, no need really. Go here and download either the gnu_gui source (must be built ) or the GUI Linux  i386 for 32 bit installs, the x64 for 64 bit.

The GUI Linux just needs to be unpacked and then run, no need to install.

I'd suggest unpacking to home directory and then making a desktop launcher to run. For launcher command just browse to unpacked folder/mediainfo_gui

[http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90341](http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90341)

The 'Easy' veiw gives some info, the 'HTML' is more complete.
Gives good info for most all audio formats

---

