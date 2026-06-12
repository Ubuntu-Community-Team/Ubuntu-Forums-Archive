---
title: "Is there an easy way to share audio files on dual boot laptop"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by bblack1220 on 2007-06-26
I have a IBM thinkpad with dual boot Ubuntu Feisty Fawn/Windows XP.
I have been mostly using Ubuntu but I have some music files on windows because my creative zen vplus is program is installed there.  I was wondering if there is a way for Ubuntu to recognize these files without me having to copy them and transfer them manually.  
Just trying to make things easier, Thanks.

---

### Post by SneakyMonkey on 2007-06-26
You could just make your Ubuntu install mount the windows partition at boot and then you would always have access to that music. It is a little tougher if you want to get music from a Ubuntu partition using windows XP. You can always just keep the music on the windows partition and mount it so that way you have access to it using either OS.

---

### Post by LobbyDizzle on 2007-12-18
While in XP i'm trying to access my music that is saved in Ubuntu. I'm fairly new so I do not know how to do all of the stuff you just said. Please explain

The reason why I did this is because I fixed the sound in XP which, in turn, disabled my sound in Ubuntu. I posted that problem a few days ago and still have yet to get help...

---

### Post by ron999 on 2007-12-18
Hi
The Windows XP section of your pc is formatted in the NTFS system.
The Ubuntu section is formatted in the ext3 system.

It's possible to access the Windows files from Ubuntu by installing **ntfs-3g** in Ubuntu using Synaptic.
That's easy enough.

But to access the Ubuntu files from Windows you have to install some other software in Windows.
I've never tried this, but this is the type of software.
Here:-[http://www.fs-driver.org/]("http://www.fs-driver.org/")

Use Google to find some more.
8)

---

