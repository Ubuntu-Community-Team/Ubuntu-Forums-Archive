---
title: "Recommend MP3 Encoder For Audio Books"
date: 2009-12-29
forum: Multimedia Software
---

### Post by fullsailj on 2009-12-29
Hi,
 
I installed ubuntu on a p3 that I would like to use for encoding audio book CDs. I like to compress to 48 kbps. This machine has 3 optical drives.
 
I've tried 3 or 4 programs, but they all have some limitations: 1) drive selection is buried under preferences, 2) can't encode to mp3 or can't select bit rate. In the wintel world, I've used to cdex for 10 years or so on thousands of CDs.
I've tried searching the forums, but for some reason I'm not finding much that is relevant.
 
Can someone recommend an application I should try, or perhaps pay more attention to?
 
Jim

---

### Post by -=hazard=- on 2009-12-29
What programs have you used?

Install encoding and decoding library:
```
# sudo apt-get install ubuntu-restricted-extras
```
and try again with same programs you have used.

---

### Post by fullsailj on 2009-12-29
I tried that command and got:
[FONT=Courier New][SIZE=1]
sha256sum: arialb32.exe: No such file or directory
arialb32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for arialb32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ubuntu-restricted-extras (36) ...
Setting up unrar (1:3.9.3-1) ...
update-alternatives: using /usr/bin/unrar-nonfree to provide /usr/bin/unrar (unrar) in auto mode.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/SIZE][/FONT]
I tried 3 times thinking maybe there were transmission errors.

Suggestions?

---

### Post by FakeOutdoorsman on 2009-12-30
I recommend abcde.  It's command line, but don't let that scare you away from it.  andrew.46 from these forums has a well written guide:

[abcde: Command Line Music CD Ripping for Linux](http://www.andrews-corner.org/abcde.html)

You can copy the MP3 version of Andrew's *abcde.conf* and mess around with the LAMEOPTS line to customize your settings, for example:
```
LAMEOPTS='--preset voice'
```

According to [LAME - Hydrogenaudio Knowledgebase](http://wiki.hydrogenaudio.org/index.php?title=LAME), *--preset voice* is an alias for *--abr 56 -mm* which works well for plain voice recordings, although you may want a higher quality setting.

---

