---
title: "JaUNTY DVD READ PROBLEM WITH VLC TOTEM-XINE"
date: 2009-06-01
forum: Multimedia Software
---

### Post by miousername on 2009-06-01
When i try to open a dvd vlc gives this error:


[00000421] main access error: no access module matched "dvd"
[00000418] main input error: open of `dvd://' failed: could not create access: no access module matched "dvd"
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title:
libdvdnav: DVD Serial Number:
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/capo/.dvdnav/.map'
libdvdnavVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnavVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnavVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnavVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[00000424] main access error: no access module matched "dvd"
[00000422] main input error: open of `dvd:///dev/sr0' failed: could not create access: no access module matched "dvd"
-------------------

P.S.:
libdvdread,libdvdcss, libdvdnav are installed in my system and the regionset is correctly set up...suggestion??

---

### Post by steeleyuk on 2009-06-01
Do you get any errors if you try opening the DVD with Totem?

---

### Post by mhgsys on 2009-06-01
what happens if you put this line in /etc/fstab 
with
```

sudo nano /etc/fstab

```
```

/dev/scd0 /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0   0 
```


and then do 
```
 sudo mount -a
```

Does it play when you open it with totem/mplayer/xine?

---

### Post by miousername on 2009-06-02
I've found a partial solution, i can open dvd with totem-xine (totem with xine library) in this way:

```

Movie-->open Location-->file:///media/cdrom0/

```

In this way dvd works fine with totem but vlc gives the same errors and i can't open dvd with menu.  

With the command:
```

$vlc /media/cdrom0/

```
vlc opens files .vob but no ifo...if i open as disc i've the same errors written before...:(

---

### Post by AliBi on 2009-06-03
same problem here!

thx for the workaround. =D> it took me an hour to find this.
one change though, had to start xine-totem with sudo. was getting a no permission error.
its a damn hassel to just play a dvd.

---

### Post by svivian on 2009-06-06
I'm also having the same problem. VLC was working fine a few weeks ago, not sure what changed...

I installed mplayer and the DVD seems to play with that, but VLC is much more usable and easy to control, I want to use that. Other media files play perfectly with VLC, but with DVDs I'm now getting this error:

> Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.

Any ideas what could be causing this? And where might the log it talks about be located?

---

### Post by AliBi on 2009-06-07
> **svivian said:**
> And where might the log it talks about be located?

press CTRL + M in vlc.

---

### Post by ddvanrooy on 2009-07-30
I seem to have a similar problem, and havent been able to solve it. Its seems to be related to the location of the dvd device.

I get the following message:

FAILED - could not access dvdrom: /dev/dvd

Either create a symbolic link /dev/dvd pointing to your cdrom device or set your cdrom device in the preferences dialog.

My dvd drive is a portable usb device, if it matters...... it works fine otherwise - just a problem with movie players.

Any ideas?

D

---

### Post by igorzwx on 2009-07-30
Perhaps, you installed an old buggy version of css from a wrong place:

You should have a hidden folder in your home folder

~/.dvdcss

delete all the content of this folder.

remove your buggy codecs

Then install new versions of all codecs
**[Howto make Ubuntu 9.04 (Jaunty Jackalope) Multimedia Ready]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")**

[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

---

### Post by cobb_cruiser on 2010-03-20
I am pretty much a newbie to Ubuntu.  I upgraded to 9.04, Jaunty, a few weeks ago and haven't been able to play DVDs since then. 

Over the last few days I spent hours trying to find a solution to the problem with Jaunty playing/reading DVDs.   I tried scores of "solutions" on many different sites & web pages but none worked.  

I finally read somewhere (don't recall in which of the dozens of pages I looked at) that the only solution was to upgrade to Ubuntu 9.10 - Karmic Koala.  I was hesitant to upgrade, but decided that this was the only option I hadn't tried.

Upgrading to 9.10 solved my problem completely!

---

