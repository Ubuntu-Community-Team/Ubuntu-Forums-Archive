---
title: "No sound through Acer laptop"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by AmanoAcid on 2008-02-24
I have no sound coming out of my acer aspire 5570z speakers at all... but when I plug in my headphones everything is fine...

also on Audacity, nothing plays back... it says the sound device couldn't be loaded.. so it doesn't work even with the headphones.

Also I have an snes emulator that I'm using with wine.. that also has problems loading up the sound device...

but playback on the default media player works fine with headphones

I tried a couple of methods of fixing this, and each time I had a problem with the directions or it just didn't work...

also it might help to note I have a Realtek audio card.. i think

thanks in advance!

---

### Post by AmanoAcid on 2008-02-29
thanks for the help guys!!!

:mad:


ok so i discovered there is sound coming out of my speakers.. but it is so low that ya gotta put your ears against it to hear it.. after puting the volume all the way up.. ther probably is a slider somewhere to fix all this.. right? volume control doesn't have anything that fixed this...


and audacity still has the same problem i mentioned in my last post... i read around a lil and from what I understand it is a bug in my version of ubuntu (7.04).. true? I'm going to upgrade anyway so this problem should be gone once i do that

---

### Post by UBuddha on 2008-03-11
I installed Fiesty Fawn not to long ago and had the same problem.  No sound at all but only through my headphones.  I installed Gitsy Gibbon and same thing.  Don't know what it is or what to do to fix it, I'm new to Ubuntu and haven't had much time to play with it.  Still looking for an answer.

---

### Post by nothingspecial on 2008-03-12
This is how I got my sound working. Hope it helps.

1st - sudo apt-get install linux-backports-modules-generic

2nd - Follow this thread 
[http://ubuntuforums.org/showthread.php?t=568463&highlight=toshiba+sound](http://ubuntuforums.org/showthread.php?t=568463&highlight=toshiba+sound)

**IMPORTANT**
These instructions were kindly posted when the latsest alsa was 1.0.15
Now the latest version is 1.0.16
If you download the latest alsa files and copy and paste the code in that thread, it won`t work. Make sure you change any line of code with 1.0.15 in it to 1.0.16

Hope it works
:)

---

### Post by stevesmall on 2008-03-31
Ok i am new to ubuntu also but i have a acer laptop that had same problems heres what i did to have headphones and laptop speakers. double click the sound icon in the top left corner there should be a surround slider if not click edit then prefrences then find surround and tick the box next to it. then go back to the sound mixer and increase the volume on your surround and you should have audio through internal speakers.

---

### Post by Prefix100 on 2008-03-31
Don't know if this applies to this problem but try it anyway,

open a terminal, type alsamixer, and turn the volumes way up.

---

### Post by bran on 2008-03-31
could be the acer hardware idea    try the Fn and the up arrow key

---

### Post by lazy gun on 2008-04-01
have you tried editing:

/etc/modprobe.d/alsa-base 

?


If not then add this to the end of the file: 

"options snd-hda-intel model=acer"


NB: I have a HDA Intel sound card and hence "-hda-intel" in the above. I guess you would have to change this for your own system. 

LG

---

### Post by Dandelion007 on 2008-07-03
:lolflag:

I was having problems with a Acer Aspire 5920 sound volume when playing DVDs.  After reading the posts on this site, I tried listening to a mp3 file and yes the volume was fine.  I stumbled upon the goofy little jumping stick figure on the right side of the laptop just above the blue lit buttons.  Press it and the Acer Arcade Deluxe opens.  Click on Play Movie.  It's somewhat slow to load but the sound is much louder.

I do enjoy having choices when it comes to software but until a better solution can be found this is definitely a work around for me at least.

The sound also is what I would expect out of Virtual Surround Sound when playing through Acer Arcade Deluxe.

---

