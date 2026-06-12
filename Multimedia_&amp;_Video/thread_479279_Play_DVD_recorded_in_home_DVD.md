---
title: "Play DVD recorded in home DVD"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by alanmoore on 2007-06-20
Hello everybody. Spanish Ubuntu Feisty user here. I'm a starter in linux and have some problems. Here's one of them.

I have a home DVD player-recorder (Samsung DVD-HR721) which I use almost everyday to record DVD-RW in a dvd-rv format. I use dvd-rv because it lets me record a show, finish the disk, unfinish the disk, erase what I had previously recorded, and record again, all in the same DVD-RW.

With Windows XP I could watch the recorded shows in my computer using several media players. When I explored the recorded and finished disk I could see a folder named DVD_RTAV and two archives within, VR_MANGR.IFO y VR_MOVIE.VRO.

Since I migrated to Ubuntu (7.04 version) I haven't been able to watch any of these recorded shows. I can see a Desktop icon named "Samsung UDF Volume", so I guess ubuntu knows the disk is there and knows what it contains. When I explore within the disk I find an archive (surprisingly, not a folder) named DVD_RTAV. If I try to open the "archive" the system asks me to choose an application to open it. I've tried with VLC, totem and mplayer, and none of them can open the archive. In fact, I can't even see the VR_MANGR.IFO y VR_MOVIE.VRO archives within the DVD_RTAV folder.

My question is: What's wrong? Is it the UDF support? The dvd-rv format support? The DVD-RW support?
Help very much appreciated. Thanks.

---

### Post by alanmoore on 2007-06-21
Anybody???

---

### Post by alanmoore on 2007-08-16
Anybodyyyyyyyyyyyyyy????????

---

### Post by jrib on 2007-09-03
no idea, but I did have trouble with UDF on feisty:
[https://bugs.launchpad.net/ubuntu/+bug/106910](https://bugs.launchpad.net/ubuntu/+bug/106910)

---

### Post by alanmoore on 2007-09-03
Hi, Jason! I've unsuccessfully tried some of the solutions proposed in the link you provided. The bug you mentioned is reported; I don't know if It is the same bug I've experienced, but, anyway,  I hope they fix it in Ubuntu 7.10.

---

### Post by Bil-E-daKid on 2007-09-10
Hey there Alan,

Did you ever get around this or are we still hoping the next version fixes it?

I'm rather sheepishly having to use a Windows box at work to copy some DVD's made on a home DVD recorder (like yours) because I can't even read them on feisty.....

---

### Post by vanadium on 2007-09-10
Your DVDs are not in standard video DVD format, and apparently, Linux only copes with standard DVD video. You probably can "finalise" your recording using your DVD recorder. At that point, it will become a standard video DVD and play back on all players and computers, but you loose the possibility to add content later. In case of a DVD RW, you of course can erase the disk and start over.

---

### Post by lisati on 2007-09-10
Just a thought: I have a DVD recorder by Samsung as well, but a different model. I find that I have most trouble when I use the "VR" more when formatting disks, and tend to avoid that format.

---

### Post by alanmoore on 2007-09-10
Unfortunately, right now, it's impossible to me to avoid this bug. Don't know if it is a problem of Ubuntu, a problem of Gnome or just a problem of the Linux kernel. But the fact is that I can't watch my dvd's in Ubuntu Feisty, even if I finalise them. Obviously, I can always record my dvds in a format different than VR, but the VR formart is much more useful for me. Moreover, my old Windows XP can play those dvds, so I hope to  play them in a Linux distro someday.

Thank you, anyway.

---

### Post by alanmoore on 2007-09-11
I've received a private message from another ubuntu user who wanted to help me. I'm very grateful, Bablefish, but I think it's more approppiate to write it down in the forums. I must say it didn't work for me, but it may be helpful to other people. Here's the message:

> I had the same problem and heres my fix.

Open up Add/Remove programs from your Application bar.

Go to Sound&Video and Find and Check all of the packages below (easily done by searching for gstreamer)

* "GStreamer ffmpeg video plugin"
* "GStreamer extra plugins"
* "GStreamer plugins for aac, xvid, mpeg2, faad"
* "GStreamer plugins for mms, wavpack, quicktime, musepack"


Then go to Other subsection of Add/Remove and find

* "Ubuntu restricted extras"

Then this you enter in the terminal (by the way the same command can be found at the offical Medibuntu site)

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

finally run " sudo apt-get update "

But your also going to need the REAL codecs that will allow you to play DVDs they
can be found here through a program called Automatrix you can find it here.

[http://www.getautomatix.com/wiki/ind...e=Installation](http://www.getautomatix.com/wiki/ind...e=Installation)

The program it installs is borderline illegal act like your living outside
the US so you can install the codes you need. When you run this program.

Finally head back to Add Remove and look for the Kaffiene Player it frankly
plays DVDs better than any other program.

This should get DVDs to finally run for you, any DVD.


Meanwhile, I've been investigating a little bit more and found that, when I tried to open the files, Totem, Kaffeine and other media players showed a sign which said something along the lines of "permission denied". Then I started to think it was a "permission problem". I cannot change permissions  permanently, because every time I insert the dvd my settings are lost, but I can do it temporarily. In other words, I've finally been able to watch those dvds. Here's how:

We need to open the RTAV folder with root priviledges. I guess there are other ways to do it, but It worked for me using nautilus as root. So, in terminal, I write:

> 
sudo nautilus

Then a new window opens. I just have to go to the /media/cdrom folder. Inside I can see a RTAV folder (at last it's a folder, not an archive) with the .VRO file within. Now I can open the file with my favourite player (MPlayer, Kaffeine, Totem...; VLC doesn't work).

As I said, there must be other (maybe easier) ways to do it. I wonder about security issues because of the use of sudo nautilus. I hope everything is all right.

Thank you.

---

