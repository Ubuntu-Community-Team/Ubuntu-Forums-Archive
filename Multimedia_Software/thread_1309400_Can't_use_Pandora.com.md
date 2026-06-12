---
title: "Can't use Pandora.com"
date: 2009-11-01
forum: Multimedia Software
---

### Post by cecilx22 on 2009-11-01
I can load the Pandora page, log in, and have it play music, but I can't click any of the buttons (thumbs up, thumbs down, etc).

I've tried several versions of the Java/etc plugin. (the one from the repos, direct download from sun, Icedtea, etc)

Other java sites load and work fine (pogo.com for instance, which is INSANELY picky.)

Anyone else having this problem?

Help!!

Thanks

---

### Post by Spccowboy on 2009-11-01
I'm having a similar problem. I can log in, but my inability to click on any of the buttons extends to not being able to get the music to play. 

I'll let you know if I find a fix.

---

### Post by Spccowboy on 2009-11-01
So I reinstalled the Java plugin and the Ubuntu restricted extras. That seems to have solved the problem with getting stations to play. Now I'm having the same problem as you. Can't thumbs up/thumbs down, skip or change stations.

---

### Post by Spccowboy on 2009-11-01
Apparently if you click repeatedly it will eventually respond. Not a true fix, but functional.

---

### Post by cecilx22 on 2009-11-01
Glad I'm not the only one.  Your "fix" (lol) dosen't seem to work for me though.  Maybe I need to click faster?  Can anyone tell me how to fix this?  I can post whatever logs/etc that might be helpful

Thanks!

---

### Post by Spccowboy on 2009-11-01
Reinstalling flashplugin-installer and flashplugin-nonfree via synaptic seems to have cleared up the issue for me. Hope it helps you alos.

---

### Post by cecilx22 on 2009-11-01
okay, tried this: 

```
sudo apt-get install flashplugin-installer flashplugin-nonfree --reinstall
```

and then restarted, but it's still not working.

So, I want to try to remove ALL the java/java like systems installed, and reisntall just the 'non-free' one.  should apt-get autoremove'ing the appropriate packages do the trick for this?  What packages should I nuke?  Also, where else might pluging for firefox be hanging out?

---

### Post by allspiritseve on 2009-11-01
I am having this same problem on my Dell e6400 running Karmic. I also noticed I couldn't click submit buttons in Eclipse, though I could press enter to submit. Maybe that is related?

---

### Post by cppbari on 2009-11-02
I'm also having the same problem with pandora in 64-bit 9.10 (clean install).  I've also tried several other flash-based websites and was able to navigate them with no problems, so I'm stumped.

---

### Post by cascade9 on 2009-11-02
I cant use pandora.com either. It seems to navigate fine, but no radio, etc. Because of this- 

> We are deeply, deeply sorry to say that due to licensing constraints, we can no longer allow access to Pandora for listeners located outside of the U.S.

[http://www.pandora.com/restricted](http://www.pandora.com/restricted) 

I hate that. :(

---

### Post by whlspacedude on 2009-11-02
> **cecilx22 said:**
> I can load the Pandora page, log in, and have it play music, but I can't click any of the buttons (thumbs up, thumbs down, etc).

I've tried several versions of the Java/etc plugin. (the one from the repos, direct download from sun, Icedtea, etc)

Other java sites load and work fine (pogo.com for instance, which is INSANELY picky.)

Anyone else having this problem?

Help!!

Thanks


Same problem. Clicking works before music begins to play.
Ubuntu 9.10 64bit

tried this and it doesnt work either
<code>
sudo apt-get install flashplugin-installer flashplugin-nonfree --reinstall
</code>


will

---

### Post by Spccowboy on 2009-11-02
You might find it easier to use the package manager and search for java/flash and either mark for reinstall or removal of the packages you have installed. This should ensure that you get them all.

---

### Post by cecilx22 on 2009-11-02
Yeah, I did try that.  However, I've also done a manual install of Java, and I don't know where that dumps stuff...  Any good way to find out?

For instance, if I remove the global *.so files for Java, then run firefox of chromium and go to a java page, it still loads.  0.o

---

### Post by Spccowboy on 2009-11-02
> **cecilx22 said:**
> Yeah, I did try that.  However, I've also done a manual install of Java, and I don't know where that dumps stuff...  Any good way to find out?

For instance, if I remove the global *.so files for Java, then run firefox of chromium and go to a java page, it still loads.  0.o
Hmmm. You've got me stumped. Sounds like you've tried everything I would know to do. I suppose you could do a full search of the filesystem and see if that turns up any hidden installs. 
Hopefully someone else will know specifically where else to look.

---

### Post by allspiritseve on 2009-11-02
The script mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=1232816&highlight=flash](http://ubuntuforums.org/showthread.php?t=1232816&highlight=flash) worked for me. I had to download the .so file separately, though as the wget link in the script didn't work.

---

### Post by whlspacedude on 2009-11-02
I had the same problem downloading the .so but it still did not work after manual download... 
I tried the gnash and swfdec players and viewers as well with no success. Flash in youtube DOES work for me.

---

### Post by cecilx22 on 2009-11-02
> **whlspacedude said:**
> I had the same problem downloading the .so but it still did not work after manual download... 
I tried the gnash and swfdec players and viewers as well with no success. Flash in youtube DOES work for me.

likewise, I can't click on embedded youtube videos, but videos on youtube work fine (most of the time)

-Ben

---

### Post by whlspacedude on 2009-11-03
I found this. Cant try it yet(on the wrong computer) Let me know how it goes!!!

[http://www.ubuntugeek.com/fix-for-flash-is-not-recognizing-mouse-clicks.html ]("http://www.ubuntugeek.com/fix-for-flash-is-not-recognizing-mouse-clicks.html")


Will

---

### Post by cecilx22 on 2009-11-04
> **whlspacedude said:**
> I found this. Cant try it yet(on the wrong computer) Let me know how it goes!!!

[http://www.ubuntugeek.com/fix-for-flash-is-not-recognizing-mouse-clicks.html ]("http://www.ubuntugeek.com/fix-for-flash-is-not-recognizing-mouse-clicks.html")


Will

Fantastic, method 1 seems to have worked for me.  I've reposted said method below.  If anyone can explain what exactly this is doing, I'd appreciate it!  Also, is there a bug report for this issue yet?

First you need to edit /usr/lib/nspluginwrapper/i386/linux/npviewer file from terminal

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

```

Add the following line **before** the last line of text

```
export GDK_NATIVE_WINDOWS=1

```

Save and exit the file

Note:- when you try to upgrading your system next time you need to revert back the changes

---

### Post by whlspacedude on 2009-11-04
Tried it out this morning. Seems to be working with pandora!!! :p

---

