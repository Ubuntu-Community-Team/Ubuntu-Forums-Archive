---
title: "Dual monitors playing video"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by tekDragon on 2008-03-12
OK I have an odd problem with my dual monitor setup after searching I haven't found any fixes (I admit I might have missed some).

I can't play video properly on my second monitor. The .avi files play properly, but when the player is in windowed mode the file's centre is offset to the left so I can only see the right half of whatever I'm playing, though I have reason to believe that the whole frame is being rendered. If I go to full screen I get a black screen. Also...  when I move the window around there is a threshold at the right and left edges of the monitor where the portion of the video being played goes black.

On my main monitor everything works fine.

Specs:

ATI Mobility Radeon X700
Laptop display at 1280x800 external LCD pannel at 1680x1050
Latest ATI binary drivers

I'm running dual monitors using bigdesktop with a paired resolution of 2960x1050 and it works fine in every other way. I can't run compiz yet but I haven't tried really hard yet though compiz does work fine if I have a single monitor (just the laptop).

I've tried multiple media players so I doubt that's the issue. I've also tried both 8.06 Alpha 6 and 7.10 and the behaviour is exactly the same. 

So..  I guess I want to know a couple of things.

First is it even possible for me to get this working properly? Sorry to put it this way but if I can't play video properly on my second monitor I cant switch to linux. I dont mind switching to open source drivers if I have to and I can live without compiz for now.

Second, has anyone with a similar setup gotten it to work? How? where would I look for solutions? I've been back and forth at this for a while now and I'm thinking I should give up on linux (again) for another 6-9 months.

Any help would be great.

---

### Post by jessika-kaos on 2008-03-12
[http://www2.ati.com/drivers/linux/catalyst_83_linux.html]("http://www2.ati.com/drivers/linux/catalyst_83_linux.html")

That link says > "There is no support for video playback on the second head in dual head mode. Further details can be found in topic number 737-26985 "

That might be your problem. Maybe in a future release it'll be fixed.

---

### Post by tekDragon on 2008-03-12
Ah right...  now why didnt I spot that last week? before wasting hours on this.

damn.

Well that's it for me and linux for the foreseeable future.

:(

---

### Post by tekDragon on 2008-03-12
What about with the open source driver?

---

### Post by jessika-kaos on 2008-03-12
looks like the open source one might work with the x700. see here fore more:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by tekDragon on 2008-03-12
cool..  I'll look into it and report ASAP.

many thanks

---

### Post by tekDragon on 2008-03-12
Wow... ok it seems to be working with open source ATI and xrandr (on Hardy).  Now I just have to figure out how to edit xorg.conf in a way that doesnt make me re-run the xrandr command every time.

Any chance this will also work with compiz?

---

### Post by tekDragon on 2008-03-13
Re: to anyone interested.

I managed to get dual monitors + compiz working with the open source driver on Hardy. I had to change my screen layout fom left to right to above so that my total texture size was within the range permited by compiz (2048x2048 if I recall correctly). With the "above" setup I have a 1680x1850 virtual desk which is fine except that now I have to re-rean not to mouse right to go to my other screen.

Good times...  and it only took me 2 weeks of screwing around.
:p

---

