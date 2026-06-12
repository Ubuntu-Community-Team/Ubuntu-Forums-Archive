---
title: "An (almost) one click solution for blu-ray playback"
date: 2011-08-15
forum: Multimedia Software
---

### Post by portablestew on 2011-08-15
Hi everyone, this is my first post, so please bear with me :)

TLDR: here is a script which makes blu ray easy for anyone

I've just rewritten the makemkv wrapper scripts that I use to play blu rays, with the goal of making a one-click solution, so that my wife has no more excuses to buy a dedicated blu ray player.  I think it turned out pretty well, so I wanted to share (scripts are attached).  

The installation process should be to just extract into any bin directory (I'm using my ~/bin).  You will need to have perl and zenity installed (it also uses makemkv, that should be installed  automatically).  Then just create a shortcut to "streamdisc" -- it's intended to be run from ui, not a terminal.  The "streamdisc" just calls some perl in the "streamdiscbin" folder which was also just extracted. 

When run, here's what happens:
 -display an ambiguous progress bar, which allows cancellation at any time
 -check http for a newer version of makemkv
  *if one exists (or this is the first run), download it and walk the user through installation (requires sudo, unfortunately)
 -call makemkvcon to get disc and title info (1-2 minutes)
 -run makemkvcon streaming server (1-2 minutes)
 -present a list box for the user to select title
 -launch the playback client (vlc by default)
 -repeat title/playback steps until cancelled
 -shutdown everything

If anyone would like to try out my script and provide feedback, it would be much appreciated.  My perl and shell skills are not as strong as they could be, so code review is totally welcome as well.  I'm running 32-bit Ubuntu 11. 

Hope this helps someone!

---

### Post by lalilulelo on 2011-08-15
I don't understand. What are you streaming? Are you talking about a program that lets you play a blu-ray disc, or something that lets you stream pirated blu-rays off of the internet?

---

### Post by portablestew on 2011-08-15
Sorry, in hindsight I don't think that post is very clear to me either.  I'm playing blu ray discs directly, no pirating funny business here :)

So let me try again, starting with some background: 

There's a utility called makemkv, which is intended to rip dvds and blu rays to the mkv format.  It works great at this.  

[http://www.makemkv.com/](http://www.makemkv.com/)
[http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224)

Makemkv also has a feature where instead of ripping, it can stream the contents of the disc over http.  So a popular method of playing blu rays is to launch makemkv, and then connect vlc to localhost.  Themediaviking.com has a great guide for this:

[http://themediaviking.com/2010/bluray-linux/](http://themediaviking.com/2010/bluray-linux/)

While this technique works very well, it's also very inconvenient.  Also, makemkv expires every month or so, with a new beta release.  It won't play anything until reinstalled.  

The "streamdisc" scripts that I've attached perform the same thing as the "mediaviking" technique, but it's much simpler to deal with.  Everything is automated (including installation/updates), and the UI is simple.  So just pop the disc in the tray, and enjoy.  

Also ... did I start this thread in the correct section?  Should it be moved?

---

### Post by PhatKat on 2011-10-02
Can u explain how one would go about playing Blu Rays in Mythbuntu with minimal fuss/loading times? I am trying to steer clear of Windoze :lolflag: Thanks in advance to anyone who could help ya :popcorn:

---

### Post by cqrity on 2011-10-10
Natty 11.04 32bit with perl and zenity installed.

Prior to downloading your script, I've already compiled and installed makemkv 1.6.14 with the following registration code:
T-LyW5B7qmbGataV5eGd_dWVklURVn0gV8o572y_cyhaZrANmfAlWh4MbYlxKfInkVCS

After seing the initial dialog "Please be patient while the disc is loaded. This may take a few minutes. " for about 1 second, the dialog window disappears and nothing else happens.

---

### Post by artships on 2011-10-31
portablestew:  Wow - It works, Ubuntu 11.10.  My perl was in a different place, and I commented-out the check-for-newer-version bit, but the rest worked.  Thanks! 

cqrity: Please edit your post to remove the registration code.

---

### Post by Tyguy7 on 2011-11-05
Just launches and then sits for a few seconds and then exits.

Tried running makemkv_install.pl, I get this:

Failed to download new bin package at makemkv_install.pl line 166.

---

### Post by BicyclerBoy on 2011-11-05
Have not tried it but..
Try changing the script (line 19)  to 1.6.16

I would download & build makemkv manually just to make sure its working..

Depending how good your web searching is etc, you can reportedly play BD using mythtv from the cmd line for 0.24.

[http://www.mythtv.org/wiki/High_Definition_Disk_Formats](http://www.mythtv.org/wiki/High_Definition_Disk_Formats)
This suggests the BD+ is not supported..

```
http://phoronix.com/forums/showthread.php?27031-MythTV-0.24-Brings-A-New-OSD-HD-Audio-Blu-ray/page2
```

Might be time to find out...

---

### Post by BicyclerBoy on 2011-11-14
MythTV can play your BDs direct from disk..without using makeMKV.

Readup:
- the mythtv HD disk formats page
- doom9 (read & read...)
Check you can get DumpHD working before moving to mythtv..
This part has been possible for > 2 yrs.

Install libaacs with git...
./bootstrap
./configure
make
sudo make install
sudo ldconfig

Myth cmd:
BD_DEBUG_MASK=8 mythavtest bd://media/<label-of-mounted-disk>
the expert opinion is that you should use bd://cdrom or /dev/sr0 etc but this does not work..

The KEYDB.cfg format of libaacs (&myth) is not the same as the "original".
Be very careful with "0x" & other formatting differences..

---

### Post by foreigner42 on 2012-10-19
Thank you!  I had to do a few tweaks to get it working - your script is a little bit out of date.

MakeMKV changed their binary file name format, so I had to change three lines in makemkv_install.pl:

$BASE_MAKEMKV_VERSION = "1.7.8"

my $MAKEMKV_OSS = "makemkv-oss-\%n";
my $MAKEMKV_BIN = "makemkv-bin-\%n";

I also had to manually install MakeMKV's required tools and libraries as described here: [http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224)

Finally a nit: when you run the script the GUI instructions suggest you copy the key from the browser, close it, and then paste them in to MakeMKV.  That's only going to work if you have a clipboard manager installed, which Ubuntu does not by default.  The workaround is to not close the browser until after you've pasted the code (or install a clipboard manager).

Thank you for this great script!  I bought this Blu-ray ages ago and finally I can watch it! :)

---

### Post by BicyclerBoy on 2012-10-19
It's great to have (semi)-commercial options (makeMKV, ANyDVD) especially for the latest problem titles..

VLC, MythTV, XBMC mplayer can play BDs directly.
Generally BD playback works better than DVDs.

---

