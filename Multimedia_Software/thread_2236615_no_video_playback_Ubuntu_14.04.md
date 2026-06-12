---
title: "no video playback Ubuntu 14.04"
date: 2014-07-27
forum: Multimedia Software
---

### Post by mystmaiden on 2014-07-27
I've install the restricted extras and libdvdcss 64 bit but I must be missing something. Is there a command I can run to see what's there? I'm using totem (if that's the one marked simply 'videos' in the menu. Machine is an HP 110.

thanks,

mystmaiden

---

### Post by TheFu on 2014-07-28
"What's there?"

What what is there?  programs, packages, data files?

For packages, you can use **synaptic** or **dpkg** or **aptitude**.
For programs you can use tab-completion and for any file on the file system, you can use either **find** or **locate** or setup **recoll** and use that.

---

### Post by bapoumba on 2014-07-28
Have you run the install script for libdvdread4 ?
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by mystmaiden on 2014-07-28
Thanks for the replies. I've installed livdvdread4, and checked the disc - it plays fine elsewhere. I checked and the dvd player works on the windows side. I really don't know what the trouble could be :( When I try to play it with movie player, over on the right side it says 'dvd menu' and immediately shuts down. If I eject the disc and put it back, nothing happens. I can't even hear it spin. Though when I look at places, it is there. If I open vlc then insert the disc, vlc just sits there doing nothing. Any help would be greatly appreciated.

---

### Post by TheFu on 2014-07-28
The trouble is that DVD has DRM because anyone who rented or purchased the DVD is clearly a criminal.  I've had problems with newer DVDs playing back at all on any computer - the DRM has gotten to the point they make broken discs that only work on HW-DVD players now.  I've seen this more on high-cost movies that had major stars.  After all, [in the USA watching a DVD on Linux is technically illegal]("http://www.howtogeek.com/138969/why-watching-dvds-on-linux-is-illegal-in-the-usa/") unless you purchase a licensed piece of software specific for that purpose.

Have you tried to use VLC?  It has gotten to the point where I only use mplayer and VLC for videos on any platforms anymore.

I have used **ddrescue** to mirror a complete DRM'd DVD image into an ISO file, then put VLC after it for playback. That almost always worked, but it doesn't remove the DRM.  **vobcopy** is another tool that sometimes works, but not always.

I keep a $25 DVD player around just for those extra-difficult DVDs that need extra, special, alternate, viewing methods. Major hassle, but better than not being able to watch the content. 

Anyway - a few more ideas for you to consider.

---

### Post by mystmaiden on 2014-07-28
VLC just sits there doing nothing. This isn't even a movie dvd - its a tai chi video but it was expensive, more than most movies. I don't think that's the issue, because it plays on my regular dvd player, on xbox and in windows....

---

### Post by coffeecat on 2014-07-28
> **mystmaiden said:**
> I've installed livdvdread4

@mystmaiden, let's clarify one point. When you say that you've installed libdvdread4, do you mean from the repositories or did you run the command that bapoumba mentioned in post #3? Or both? You need to do both.

libdvdread4 is in the universe repository, but to get libdvdcss2 you need to run the script that bapoumba mentions. You need both libraries to decrypt commercial DVDs. Rather confusingly, the script for installing libdvdcss2 is in the /usr/share/doc/libdvdread4 folder.

---

### Post by bapoumba on 2014-07-28
Thanks coffeecat, I always get confused with these :)
All I do is install (l)ubuntu-restricted-extras and run the install script that I have copied into my cheat sheet. I own a fair amount of DVDs and never had problems reading them, but may be I got lucky.

---

### Post by coffeecat on 2014-07-28
@bapoumba, that's been my routine as well. :) I thought that the install-css.sh script checked for libdvdread4 and either downloaded it or error-ed out if it wasn't there, but looking at the script in 14.04, that doesn't seem to be the case. Perhaps it was revised when the source for libdvdcss2 changed from medibuntu to videolan. Whatever, installing *ubuntu-restricted-extras followed by running the script is a good idea, I agree.

---

### Post by mystmaiden on 2014-07-28
I seem to have accidentally discovered the fix. I uninstalled gstreamer 'bad' and that took care of it for vlc. Movie player just shuts down still. When my machine with 12.04 was still working I remember that mplayer was shutting down at odd times too. It seems to play regular videos fine though,

---

### Post by bapoumba on 2014-07-28
Well, ran it a couple days ago after fresh installs on 2 different machines. It did download 2 files (from memory and from the =======> symbols and wget-type dl completion I saw) but I did not pay attention and did not save the terminal output.

---

### Post by mc4man on 2014-07-28
> **mystmaiden said:**
> I seem to have accidentally discovered the fix. I uninstalled gstreamer 'bad' and that took care of it for vlc. ,

I'd call that coincidental instead of  accidental as vlc does not use the gstreamer bad plugin in any fashion (or any gstreamer plugin.

---

### Post by mystmaiden on 2014-07-28
This problem may be related or mplayer may have simply changed. Before I always used mplayer to play mp3s, as I dislike all the players that load my whole music list and often show the wrong album art for my japanese and korean music. Now I can't get it to play mp3s or any files that are just audio. Now it plays videos and only videos. I hope there is a fix for this.

---

### Post by mc4man on 2014-07-28
Do you mean "mplayer" ( a command line player) or 'movie player', aka Videos or Totem

Edit:
 if Videos/Totem then open a terminal & go - 
totem --gst-debug-level=1 /path/to/a.mp3

---

### Post by mystmaiden on 2014-08-02
movie player aka videos or totem is the one, sorry for the confusion on my part. That did fix my mp3 player, thanks soo much!!

---

