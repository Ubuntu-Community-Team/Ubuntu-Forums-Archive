---
title: "[SOLVED] sound juicer problems"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by LoneWolfJack on 2008-03-01
Hi folks,

I have some problems with sound juicer and I am looking for advice.

Problem 1: 
When ripping CDs, the slightest scratch (and I mean they are barely visible) may cause the program to rip garbage. I did rip the same CD before with dbPowerAmp under Windows (yet accidently converted it to 128kbit mp3) and had no such problems. I suppose the problem could be fixed by just telling sound juicer to rip more slowly, but I don't see how I would do that.

Problem 2:
The mp3 encoder keeps using wrong settings (or perhaps is trying to "optimze" them). I want my files to be ripped to 192kbit VBR, but no matter what I do, LAME always returns files with 160 kbits that vary by 20 kbits at most. Comparing a file that has been encoded like this with dbPowerAmp there should be passages where a bitrate of 112 kbit is used and some where the full 320 kbits are used, yet there's no such thing.

Any help would be appreciated.

---

### Post by cozmicharlie on 2008-03-01
You can adjust the settings in soundjuicer by going on the menu to edit>preferences>output format>edit.  To have more control though you may want to try another program.  I also use dbpoweramp and I love it - I have not found an equivalent in Linux (at least not a single program that can do everything dbpoweramp does)  (FYI - I believe dbpoweramp runs in Wine)The closest native Linux prgram I found was PACPL [http://pacpl.sourceforge.net/](http://pacpl.sourceforge.net/) - it is command line (unless you use kde) but it is easy and gives you more options. I also like SoundKonverter (with a k).  It is a kde program but it works fine in gnome.  It also has more options and better control than Soundjuicer.  Post back and let us know if any of these helped.

---

### Post by kshane on 2008-03-01
> **LoneWolfJack said:**
> Hi folks,

I have some problems with sound juicer and I am looking for advice.

Problem 1: 
When ripping CDs, the slightest scratch (and I mean they are barely visible) may cause the program to rip garbage. I did rip the same CD before with dbPowerAmp under Windows (yet accidently converted it to 128kbit mp3) and had no such problems. I suppose the problem could be fixed by just telling sound juicer to rip more slowly, but I don't see how I would do that.

Problem 2:
The mp3 encoder keeps using wrong settings (or perhaps is trying to "optimze" them). I want my files to be ripped to 192kbit VBR, but no matter what I do, LAME always returns files with 160 kbits that vary by 20 kbits at most. Comparing a file that has been encoded like this with dbPowerAmp there should be passages where a bitrate of 112 kbit is used and some where the full 320 kbits are used, yet there's no such thing.

Any help would be appreciated.

I use RipperX (available through Synaptic) and get 320kb in the final file.  Haven't had any problems because of scratches at all...  In fact, I haven't had any problems using RipperX.  Sound Juicer sux....

Kevin

---

### Post by LoneWolfJack on 2008-03-01
Thanks, I actually tried RipperX and solved Problem 1 but still didn't get LAME to behave properly. 

I'm now working to get dbPowerAmp running with WINE, the program itself seems to be running out of the box, but it fails to recognize my cdrom for some reason, even though other WINE apps do find it. Working on that issue now.

---

### Post by kshane on 2008-03-01
> **LoneWolfJack said:**
> Thanks, I actually tried RipperX and solved Problem 1 but still didn't get LAME to behave properly. 

I'm now working to get dbPowerAmp running with WINE, the program itself seems to be running out of the box, but it fails to recognize my cdrom for some reason, even though other WINE apps do find it. Working on that issue now.

In RipperX, under the Config button, choose the MP3 tab and you can set the bit rate from 32k to 320k.  You should also make sure that the Variable Bitrate is turned off (which sounds like it may have been your problem).

I tried tons of other programs and options, but RipperX did the trick, once configured properly.  

Kevin

---

### Post by LoneWolfJack on 2008-03-01
Well, I actually WANT VBR. :)

In fact, VBR will yield better results than CBR 320 because with CBR 320, the encoder will  split the 320 in half (160 for each channel) while with VBR the encoder will use a higher number on a channel if neccessary.

Also, I have a massive mp3 archive with about 8.000 files and encoding with 320 kbit would at least double the amount of data.

Still no luck with wine and dbpoweramp... some ALSA issue. Hm...

---

### Post by LoneWolfJack on 2008-03-01
Ok, got it:

the WINE config tool has an "advanced settings" dropdown for emulated drives that is set to  automatically detect the type of the drive. changing this from "automatic" to "cd rom" fixed the issue.

---

### Post by cozmicharlie on 2008-03-01
Excellent - which version of dbpoweramp converter did you use?  Do you have all the functions under Wine that you would under Windows?  Do you install the codecs from dbpoweramp or does it use the codecs already installed under Ubuntu?  I am curious because I have never used it under Wine - I tend to avoid Wine because I like the native Linux apps - though dbpoweramp is the one program I may make an exception for.

kshane - thanks for the tip on RipperX - I loaded it and will check it out.

---

### Post by LoneWolfJack on 2008-03-01
I'm using the most current version of dbpoweramp... r12.4 I think they call it. It comes with a default set of codecs, among them the LAME mp3 codec/encoder.

so far, I haven't found anything that doesn't work. and most important, the mp3 files actually have a variable bitrate now.

---

