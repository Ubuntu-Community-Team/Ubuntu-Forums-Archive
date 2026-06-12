---
title: "Need help with creating an audio CD image on Ubuntu 14.04 (64-bit)"
date: 2014-09-09
forum: Multimedia Software
---

### Post by tomdkat on 2014-09-09
I'm working on creating an audio CD as a gift for a friend.  I have the Ogg and MP3 files in a playlist I can load in Brasero just fine.  I can use Brasero to generate a set of CUE/BIN files and I can mount the CUE file in CDEmu just fine.  The issue is getting the CUE/BIN files transferred to my Windows XP system so I can load the image into iTunes on Windows to create the CD insert.

I tried creating an ISO file, on Ubuntu, with the idea I could transfer the ISO file to the Windows system, mount it using Daemon Tools Lite or some other utility, then open the CD image in iTunes and create the CD insert.  After hours of research and experimentation, it seems I can't make an ISO image from the CUE/BIN files because the ISO format won't support multiple tracks and I've got 19 tracks in the CUE/BIN files.

Any ideas how I can get the CUE/BIN files created in a way I can access on Windows XP?  Daemon Tools Lite on Windows XP displays a "Unable to mount image" errors message and exits.  The error is _just_ "Unable to mount image" with no other information or explanation.  The CUE file I created had a Unix/Linux LF new line sequence instead of the CRLF sequence Windows uses.  So, I manually saved the CUE file to use a CRLF new line sequence but that didn't make any difference.

Thanks in advance for your time and ideas!

Peace...

Tom

---

