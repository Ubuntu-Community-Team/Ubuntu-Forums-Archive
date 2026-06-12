---
title: "WMV video silent in Ubuntu Lucid 32-bit, plays audibly in XP"
date: 2010-06-04
forum: Multimedia Software
---

### Post by K7AAY on 2010-06-04
I have a WMV video which plays in XP but fails in 32-bit Ubuntu Lucid (same machine, dual boot), kernel 2.6.32-22 on a Lenovo SL400 w/ 2GB RAM, 36GB HD free and an Intel Core 2 Duo T5870 2GHz CPU.

Media player and Banshee fails with the error message
No packages with the requested plugins found
The requested plugins are
Windows Media Audio 9

Avidemux crashes when I try to open the 6.3GB file, which I can play with audio AOK in XP.
Assert failed :_offset<=pakSize
 at line 352, file /build/buildd/avidemux-2.5.2/avidemux/ADM_inputs/ADM_asf/ADM_asfPacket.cppADM_backTrack
asfPacket::pushPacket(unsigned int, unsigned int, unsigned int, unsigned int, unsigned int, unsigned int)
asfPacket::nextPacket(unsigned char)
asfHeader::buildIndex()
asfHeader::open(char const*)
ADM_Composer::addFile(char const*, unsigned char, fileType)
avidemux2_gtk() [0x809a16f]
FileSel_ReadWrite(void (*)(char const*), int, char const*, char const*)
avidemux2_gtk() [0x81ae352]
GUI_FileSelRead(char const*, void (*)(char const*))
HandleAction(Action)
guiCallback(_GtkMenuItem*, void*)
g_cclosure_marshal_VOID__VOID
g_closure_invoke

g_signal_emit_valist
g_signal_emit_by_name

g_cclosure_marshal_VOID__VOID
g_closure_invok


Mplayer tells me 
Fatal error!
Error opening initializing the selected video_out (-vo) device.

VLC says
No suitable decoder module:
VLC does not support the audio or video format "wmap". Unfortunately there is no way for you to fix this.

Mediabuntu is installed in Software Sources. I uninstalled it, then reinstalled it. I also disabled, then reenabled, 'Software restricted by copyright or legal issues (multiverse)'; no joy. Also uninstalled then reinstalled Mplayer and Smplayer, to no avail.
Did both repository install as per [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository) 
and also 
sudo apt-get install w32codecs 


Your generous assistance to this vexacious issue will be appreciated.
Thank you kindly.

---

### Post by Linuxforall on 2010-06-04
Try sudo apt-get install ffmpeg libavcodec-extra-52

---

### Post by K7AAY on 2010-06-04
> **Linuxforall said:**
> Try sudo apt-get install ffmpeg libavcodec-extra-52

Drat. No joy. Result:

[INDENT]libavcodec-extra-52 is already the newest version.
libavcodec-extra-52 set to manually installed.
[/INDENT]
Any other ideas?

---

### Post by zipperback on 2010-06-04
You need w32codecs for 32 bit Ubuntu or w64codecs for 64 bit Ubuntu.

You should read this guide it is VERY helpful for getting your system working with all the codecs and dvd playback and such.

```

http://ubuntuforums.org/showthread.php?t=766683

```

- zipperback
:popcorn:

---

### Post by K7AAY on 2010-06-04
Thank you, Zipperback. Although VLC didn't work, SMplayer did!

---

