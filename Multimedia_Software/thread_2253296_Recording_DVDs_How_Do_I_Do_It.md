---
title: "Recording DVDs: How Do I Do It?"
date: 2014-11-18
forum: Multimedia Software
---

### Post by Smallwheels on 2014-11-18
I'm selling my computer with a DVD CD drive. I have a new laptop that doesn't have a disc drive. It is running Chrome OS. It is a Chromebook. There are a few movies on DVD that I want to record while I still have the tower machine. I know these discs are probably protected in some way. They are all from retail stores in factory packaging. 

What program do I need to record them whole? I would like to have the movie portion and the extras sections too. All of this will be put onto my external hard drive. The sooner I get this done the sooner I can list my tower for sale. 

Thank you.

---

### Post by TheFu on 2014-11-18
The shortest answer is to buy a USB DVD player.
Where I live, converting a commercial DVD into any other format is technically illegal. Perhaps someone else can help?
Retaining everything on the DVD with menus means retaining it in an ISO ... don't get pulled down the rabbit hole of transcoding, ripping, codec selections ...

**ddrescue** can be used to perform bit-for-bit copies - into an iso file.

---

### Post by mc4man on 2014-11-18
If there is no 'structure protection' on the title then vobcopy will serve your purpose. (vobcopy -m or read the help..
(- with vobcopy & disks in good shape SP will be apparent when vobcopy keeps retrying the same blocks for the default 10 read attempts
If there is structure protection then one could make (mis)use of dvdisaster to create a css encrypted, structure protected iso that will play back reasonably well in most cases.

Also k9copy could handle some early versions of structure protection

---

### Post by Smallwheels on 2014-11-18
mc4man thank you for your information. How do I know if there is structure protection on a DVD?

---

### Post by mc4man on 2014-11-19
> **mc4man said:**
> 
(- with vobcopy & disks in good shape SP will be apparent **when vobcopy keeps retrying the same blocks for the default 10 read attempts**

Mentioned previously. With disks with no SP but not in good shape there will be multiple read attempts but generally some will succeed while with SP the sectors are unreadable so vobcopy will try 10 times then move on.

---

### Post by SeijiSensei on 2014-11-19
Alternatively you could rip the DVDs to Matroska files with Handbrake. (Use the version in [this repository]("https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots").)  That's also technically illegal in the US and any other jurisdiction with [anti-circumvention rules]("https://www.chillingeffects.org/topics/12").

---

### Post by Smallwheels on 2014-11-19
Maybe these programs will work. Unfortunately they seem to require skills using the command line of which I have almost none. Are there any GUI suggestions for converting DVDs to files for my external driver for video playback?

This shouldn't be illegal because I bought each of these videos. With a good DVD I should be able to get a high quality recording. I don't want to watch movies recorded with low resolution.

---

### Post by TheFu on 2014-11-19
Many things shouldn't be illegal, but are.

I don't know of any GUI tools that work which also keep the menus. Sorry.

DVDs are either 480p (NTSC) or 576p (PAL) ... not exactly hidef (like 1080p), but I find this quality quite acceptable like you.  Transcoding is really good these days, but I've never gotten the DVD menu experience to work. If you can live with the main title(s) only, transcoding using handbrake (a gui tool) is fairly easy and my eyes cannot see any artifacts - i.e. the result is as good as the original.

---

### Post by mc4man on 2014-11-20
> **Smallwheels said:**
> Maybe these programs will work. Unfortunately they seem to require skills using the command line of which I have almost none. Are there any GUI suggestions for converting DVDs to files for my external driver for video playback?

This shouldn't be illegal because I bought each of these videos. With a good DVD I should be able to get a high quality recording. I don't want to watch movies recorded with low resolution.
Why don't you just go ahead & try vobcopy & see what happens
(- this assumes libdvdcss2 is installed, ie. you can play the dvd in a player

Insert dvd, close out any pop up
open a terminal, run this command (-v means verbose, -m means mirror the disc
```
vobcopy -v -m
```

---

### Post by SeijiSensei on 2014-11-20
> **Smallwheels said:**
> Maybe these programs will work. Unfortunately they seem to require skills using the command line of which I have almost none. Are there any GUI suggestions for converting DVDs to files for my external driver for video playback?

Handbrake is a GUI-based program.  There's also a command-line version, but the "handbrake-gtk" package includes a GUI.

You shouldn't see much if any loss of quality if you encode the files with H.264, the Handbrake default.  DVDs use the now rather ancient MPEG2 standard for encoding video.  MPEG4 codecs like H.264 produce smaller files with no real loss of quality.

---

### Post by Rob Sayer on 2014-11-20
Actually dvd copy protection does seem to be a problem in linux ... AFAIK there aren't any good up to date linux apps that decrypt newer dvds.  Generally Disney dvds are the torture test.  See:

[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

You may actually want to try running DVDFab HD Decrypter in Wine.  It's one of the most reliable decrypting programs but it's only available for windows.

[https://appdb.winehq.org/objectManager.php?sClass=application&iId=2377](https://appdb.winehq.org/objectManager.php?sClass=application&iId=2377)

---

