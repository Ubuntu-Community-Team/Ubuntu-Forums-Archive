---
title: "Banshee Lyrics Extension Not Working"
date: 2010-08-29
forum: Multimedia Software
---

### Post by Quantum Polagnus on 2010-08-29
I installed the banshee-extension-lyrics addon from the repos and it doesn't seem to have any effect on Banshee.  I've searched through Banshee's Preferences and the Lyrics option is already checked under the Extensions tab, but it doesn't work.

There is an option for the lyrics to be displayed is in the context pane, but it always says the same thing:

> Song Name Lyric

[http://www.lyricsvip.com](http://www.lyricsvip.com)

Powered by LyricsPlugin ([http://www.lyricsplugin.com](http://www.lyricsplugin.com))
The problem, then, is that although the Lyrics option is available and does _something_, it doesn't display actual *_lyrics_*!

I appreciate any help I can get,
-qp

---

### Post by Quantum Polagnus on 2010-08-31
It still isn't working. :(

If anyone can help, I'd greatly appreciate it.

Thanks,
qp

---

### Post by ENigma885 on 2010-09-01
Sounds like Lyricsplugin is down permanently, or hopefully, temporarily and redirects any request to another site.

You can try [COLOR="Red"]CoverGloobus[/COLOR]; It has access to many Lyrics databases like: LyricsWikia, Lyricscom and others.
To use the program, add its PPA to your repositories. Open a terminal window (*Applications>>Accessories>>Terminal*) and paste the following```
sudo add-apt-repository ppa:gloobus-dev/covergloobus && sudo apt-get update && sudo apt-get install covergloobus
```

Then you can launch it from *Applications>>Accessories>>CoverGloobus* and rightclick to configure which mediaplayer to be watched.
You will get something like:
[[IMG]http://img820.imageshack.us/img820/6484/covergloobus.th.jpg[/IMG]](http://img820.imageshack.us/i/covergloobus.jpg/)

****Some Hints:**
- Middle click is used to display the lyrics.
- From the configure menu, Lyrics tab, you can select one Lyrics Engine or make the program try others if nothing is found in the selected one by  "Try other engines..."
- In the same tab make sure "Refresh lyrics/tabs when ..." is checked.

---

### Post by Quantum Polagnus on 2010-09-01
Thanks a bunch!  That is a very good option, for now, although I'm still hoping that the Lyrics Plugin for Banshee will be fixed eventually.  Until then, though, I'll make use of CoverGloobus as it seems to work splendidly.  It doesn't seem to automatically refresh the lyrics window upon song change, though that's just a minor problem.

I'm not going to mark this topic as [SOLVED], just yet, though, since the original issue has not quite been resolved, but I greatly appreciate the help regardless.

Thanks,
qp

---

### Post by ENigma885 on 2010-09-01
> **Quantum Polagnus said:**
> It doesn't seem to automatically refresh the lyrics window upon song change...

That's why I wrote some hints> **ENigma885 said:**
> 
- In the same tab make sure "Refresh lyrics/tabs when ..." is checked.

---

### Post by Quantum Polagnus on 2010-09-04
Sorry, I didn't really phrase that well.  I had actually heeded your three pieces of advice, as well as I'd fiddled around with everything I could find to adjust to how I wanted it to run, but of the three bits of advice you mentioned I was only able to get one to work.

First off, middle click doesn't work for me, I'm not sure why, but I looked through the Preferences and didn't see anything about middle-clicking.  That doesn't really bother me, though.

I also checked the option to have it reload the lyrics automatically upon song change, but it never did.  I ended up having to close the lyrics, right-click the icon in the "system tray" then click Show Lyrics and it would fetch the new lyrics.

"Right-click, Left-click" isn't a whole lot of work to have it show new lyrics and it doesn't really bother me much, but it'd be nice if the program actually would do it automatically.  I don't know why it doesn't work quite like I thought it would.  

Maybe I'm doing something wrong?  Do I have to use CoverGloobus' window to change songs or can I let Banshee automatically move from one song to the next and have CoverGloobus recognize that the song has changed and automatically find the new lyrics?

---

### Post by ENigma885 on 2010-09-05
> **Quantum Polagnus said:**
>  First off, middle click  Middle click on the desktop widget; ie the small window displaying the album cover and not on the systray icon. My bad; I didn't state that clear enough.

> **Quantum Polagnus said:**
> .. Do I have to use CoverGloobus' window to change songs or can I let Banshee automatically move from one song to the next and have CoverGloobus recognize that the song has changed and automatically find the new lyrics? Either way works.

I have attached the configuration file of mine. Uncompress it and replace the one u have @ */home/YourUSERNAME/.config/CoverGloobus*

And make sure that Covergloobus is not launched while replacing.

**** Quick Hints** = )
- Any folder starting with a dot in its name is a hidden folder.
- To unhide it, hit "ctrl+H" at the parent folder. Meaning that, you have to hit "ctrl+H" at your *home directory* to be able to see the *.config*
- In my configuration, the "Status icon" is disabled. You can reenable it from the "configure" window  >> General tab >> Show status icon.

---

### Post by HLEBARKATA on 2011-02-06
Since this is still a problem for me/I started using banshee - See [https://bugzilla.gnome.org/show_bug.cgi?id=641669](https://bugzilla.gnome.org/show_bug.cgi?id=641669) on how to fix it.

---

