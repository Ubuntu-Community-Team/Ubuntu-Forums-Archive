---
title: "Grip Flac"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by Lowfront on 2007-02-23
Invalid encoder executable 
check your encode config and be sure is specify the full path to the encoder executable.


I get this when I try to convert to flac.

And idea's do I need to download somthing else?
I am sopposed to just change encoder to flac right?

---

### Post by yabbadabbadont on 2007-02-23
sudo apt-get install flac

(if you haven't already done that)

---

### Post by Lowfront on 2007-02-23
ya thats was already done

---

### Post by Lowfront on 2007-02-24
?

---

### Post by yabbadabbadont on 2007-02-24
Are you just trying to rip your CDs to flac files?

---

### Post by Lowfront on 2007-03-07
Yes

---

### Post by yabbadabbadont on 2007-03-07
If you don't mind using a command line tool, I highly recommend abcde.  You'll need to read the manpage and copy the default config file to your home directory for modification.  I'll include my config file as an example for ripping to flac.  However, abcde lets you rip your discs to multiple formats at the same time if you wish.  Say you want a perfect flac copy, but you also want a smaller mp3 copy for use on a portable player.  You can do that with the proper settings in your ~/.abcde.conf file.

---

### Post by themajesticmoose on 2008-03-22
I'm having the exact same problem. And yeah, I could use another program, but why isn't this one working?

---

### Post by logos34 on 2008-03-23
Try this Grip config:

-set dropdown menu to FLAC

Encoder executable: > /usr/bin/flac
Encoder command-line: > -8 -V -o %m -T "ARTIST=%a" -T "TITLE=%n" -T "ALBUM=%d" -T "DATE=%y" -T "GENRE=%G" -T "TRACKNUMBER=%t" %w
Encode file extension: > flac
Encode file format: > ~/music/%A/%d/%t. %n.%x

(replace 'music' dir with your output target) 

ABCDE is a great little app too--better than Grip IMO and faster.  EAC or dBpoweramp on wine if you need assured secure rips

---

### Post by BoneSaw on 2008-03-23
[http://wiki.hydrogenaudio.org/index.php?title=Rubyripper](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper)

is my favorite cd paranoia frontend.

---

