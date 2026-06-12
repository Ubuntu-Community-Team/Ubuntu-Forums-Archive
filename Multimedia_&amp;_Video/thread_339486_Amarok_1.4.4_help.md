---
title: "Amarok 1.4.4 help"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by abou on 2007-01-15
[FONT=Times New Roman]Interesting problem for those of you on the boards.  Earlier today Amarok ceased being able to play ogg and mp3 files; it can still play FLAC files no problem, which is odd.  I tried reinstalling, purging and reinstall, and even downgrading to 1.4.3, but all to no avail.

Essentially, the error I get is that the ogg files are not supported and so not loaded into the playlist.  mp3 gets a similar error and then asks to enable mp3 support, but then the application hangs during the process.  Other xine-based programs still work no problem and so does XMMS.

If there is any other information that is needed, let me know.
[/FONT]

---

### Post by armware on 2007-01-16
i'd try reinstalling the mp3/ogg decoder libraries.

---

### Post by abou on 2007-01-17
Still nothing.  ](*,)

---

### Post by armware on 2007-01-17
i can only think of a few more things to try off the top of my head, but i need to get to sleep so this'll be my last post for today. i'll check in on it again in the morning.

make sure you have gstreamer libraries  (libgstreamer0.10-0, i believe)
mpeglib
libmad0
libogg0

try the package vorbis-tools

this is a bit much, i'd go one at a time to avoid installing extra crap (i have a bad habit of doing so).

these are a few libraries i have installed and i'm able to play mp3's (not sure about ogg).

---

### Post by oobuntoo on 2007-01-17
Try reinstalling libxine-extracodecs

---

### Post by Kratos on 2007-01-18
I have a similar problem and after following the instructions here, Amarok just plain crashes when I try to play mp3 files.

---

### Post by abou on 2007-01-19
Yeah, no luck.

---

### Post by abou on 2007-01-21
Bumping to see if anyone else can help.

---

### Post by jpoRS on 2007-01-22
I am having the exact same problem.

jim

---

### Post by stueyboy on 2007-01-22
Dunno if I can help really but I upgraded Amarok and it all works fine for me including being able to read collections off network drives without crashing when building the library.

Maybe if you asked me to look for stuff on my PC, I could help by comparing things for you guys

---

### Post by jpoRS on 2007-01-22
The issue isn't crashing.  Whenever I try and play something in amarok, I get an error telling me that mp3 support isn't installed.  I click the install support button, and nothing happens.  I also cannot play .ogg, but there is no error message for that.

jim

---

### Post by tikal26 on 2007-01-23
ok I had the same problem and I installed reinstaleld the libexine-extracodec package and the gstreamer ugly and bad plugins and the gstreamer-fluendo-mp3 so I don;t know which one did it for me since I jsut went online and read all the instructions and now I can listen to mp3 files

I followed his instruction plus the use gstreamer0.10-plugins-ugly-multiverse
[http://jordilin.wordpress.com/2006/10/28/amarok-and-mp3-in-edgy-eft/](http://jordilin.wordpress.com/2006/10/28/amarok-and-mp3-in-edgy-eft/)

---

### Post by jpoRS on 2007-01-23
Tried that, didn't find anything.

I ran amarok from terminal googled the error message and found this:
[http://ubuntuforums.org/showthread.php?p=1264009](http://ubuntuforums.org/showthread.php?p=1264009)

any relevance?

jim

---

### Post by tikal26 on 2007-01-23
ok so lets go back for a minute and try to figure this thing out.  I understand that you are running the following
Amarok  1.4.4
KDE 3.5.5
libxine1 1.1.2ubuntu2
gstreamer-fluendo-mp3
gstreamer-plugins-ugly and bad

libxine-extracodes or is it that you could not find the extra codecs and the gstreamer if that is the case then it is a repo problem and we can take care of that easily. Let me know if its that or if you are runnig something different that what I posted above

---

### Post by jpoRS on 2007-01-24
I checked and I only have Amarok installed.  I tried to install the rest and nothing came up.  Is this a KDE/gnome thing?  I see you run Kubuntu, and I am pretty sure the rest of us are running standard Ubuntu.

jim

---

### Post by jpoRS on 2007-01-28
Does anyone know if this would work?

[http://www.ubuntuforums.org/showthread.php?t=345739&highlight=amarok+mp3](http://www.ubuntuforums.org/showthread.php?t=345739&highlight=amarok+mp3)

jim

---

### Post by abou on 2007-01-30
I'm beginning to think that using Edgy wasn't the best idea because there are just a host of little problems.  

Granted, there is a sticky informing us about what Edgy is, but I didn't read that before hand.  I'll just stick to XMMS.

---

### Post by jpoRS on 2007-02-01
But that doesn't explain why amarok DID work, and then stopped.

jim

---

### Post by ksamvel on 2007-02-03
I confirm the problem. At the very beginning of using Edgy Eft my Amarok was working perfectly with mp3 as well as with ogg. But some day [don't remember the exact date... definitely that happened during the first month or so] some patch or update was released Amarok stopped playing MP3. It simply raises dialog suggesting to install MP3 support. Unfortunately pressing button does not produce desired result. Simply nothing changes that is weird.

Any ideas? Reinstalling Amarok does not solve current issue.

---

### Post by ksamvel on 2007-02-03
So, any help is appreciated.

---

### Post by jpoRS on 2007-02-03
I found a fix-

[http://www.ubuntuforums.org/showthread.php?t=349590](http://www.ubuntuforums.org/showthread.php?t=349590)

jim

---

### Post by abou on 2007-02-06
Ah, thank you very much for the link, jpoRS.  Also, thanks to you, theoldgit, if you are listening.

Also, in case it needs to be known, Amarok also wouldn't play .wav files, which is also fixed now.

---

### Post by SunRa on 2007-02-12
Hello, where can I find the .xine file, as in the fix in the url above? I am using xubuntu and have the same problem with amarok...:( 

Thank you

---

### Post by jpoRS on 2007-02-13
Go to Places> Home Folder.

Press CTRL+H or go to View and select "Show Hidden Folders".

Find the .xine folder, and move it to your desktop.

Restart Amarok, and you are fixed!

Let me know if this doesn't work out.

jim

---

### Post by Kratos on 2007-02-24
EUREKA! Much better. The only problem with this now, is that Amarok fails to match my current desktop scheme. :P

---

