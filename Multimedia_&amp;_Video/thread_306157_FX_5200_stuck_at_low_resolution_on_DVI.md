---
title: "FX 5200: stuck at low resolution on DVI?"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by fabecool on 2006-11-24
Hello everyone,

So I have been trying for days, even weeks to get my Nvidia FX5200 (Asus) display a 1280*1024 resolution on my flat panel through the DVI connector.

I have followed some guides, reconfigured my xorg.conf several times, updated it manually, searched for hints or tips, but I just could not get passed that 1024*768 resolution threshold. ](*,)  

Of course, I have tried, more successfully, to use the analog connectors on my LCD panel and graphic cards, but I can't get the result I'm hoping for. 

So here's what I get when I use the analog cable: although I have the 1280*1024, I'm stuck with a refresh rate of 60 Hz when my monitor allows for 75 Hz through the analog. Also, I do not get the Nvidia Logo when X starts. But I can access the nVidia settings panel, and the gears (I don't remember the command to display them right now) are spinning OK. But that's just not what I want: I would like to have my DVI working.

It does work under windows, so technically, it should be possible, right? Well, maybe not, what do I know. I'm a newbie, let's not forget it :).

Anyway, I've also tried a CRT monitor, reconfigured my xorg.conf, let the system detect the monitor, and there I get the nVidia logo, as well as the resolution I want. 

So I digged a little more, and I found some threads in which people had the same problem and said that the DVI on my card would just not work for I-don't-know-and-don't-wanna-know reason. Here is one of those threads:
[http://ubuntuforums.org/showthread.php?t=77292](http://ubuntuforums.org/showthread.php?t=77292)

Then, almost desperate, I opened a few more threads, and it seems that some people got it working at resolutions as high as 1400*900 or even my much wished for 1280*1024!!! Some of them are just at the next level where they just want an even higher resolution! Lol!
[http://ubuntuforums.org/showthread.php?t=167924](http://ubuntuforums.org/showthread.php?t=167924)
[http://ubuntuforums.org/showthread.php?t=261856](http://ubuntuforums.org/showthread.php?t=261856)

So what I would like to know is: should I keep fighting and try to get it work, and if so, how, what should I do, and tip will be welcome!

And if not, I have an older Geforce MX 440 (on an Aopen card) with a DVI connector. It's even less powerful than my FX 5200, but I don't care, I don't game that much (not at all actually). Would it work in 1280*1024 on the DVI?

Hopefully this thread will settle once and for all the answer to my question (FX 5200 + DVI = possible 1280*1024?) and will benefit others in my situation (there are several people on another forum that have the same hardware and the same problems).

Thanks a lot in advance!

Fa

---

### Post by Zentropic on 2006-11-24
Hi!  Your first link is my thread. I was rather angry that week. :-)

Most of what I said is true though, the FX series, particularly the 5200, has a cheap-*** chip that just doesn't cut it.

You say, "I-don't-know-and-don't-wanna-know reason", but you are going to have to face it sooner or later. Linux has made huge strides, but in multimedia and video it is still plagued with problems. No plug and play here, sorry. I've never had X get a resolution right without repeated tweakings of the conf file. And then the driver mess... But anyway...

You *should* be able to reach that resolution, but you'll have to do what everyone does, the modeline shuffle. Google up modeline generators and keep loading different xorg.conf files until it works.

---

### Post by drphilngood on 2006-11-24
Give [this]("http://ubuntuforums.org/showthread.php?t=83973") a try.  Pay close attention to the 
_**Adding custom modeline**_ section

---

### Post by fabecool on 2006-11-25
Thanks for the encouragement and the tips. It's good to know I've got some support! :) 

drphilngood: I had already come across that thread and I even have the modeline tool in my bookmarks. I've tried several different settings, but it just doesn't change anything. :-k 

Zentropic: knowing you've got that same FX 5200 working somehow at a resolution higher than 1024*768 gives me some hope. I'll keep trying and keep you posted.

Cheers!

Fa

---

### Post by faizkj on 2006-11-28
I've googled and found this thread.. and hi to all since this is my first post!
I have the very same problem.. I got 22" and would like to get 1600x1208 (or whatever number of hi-res) but stuck at 1024x768.. please keep me updated! thank you!

---

### Post by fabecool on 2006-12-08
Well, I've been struggling with it for a month now: I give up. I'll probably have to change my graphic card. If someone has some advice on what graphic card is well supported by linux and allows things like dual view, let me know :)

---

### Post by b0fh on 2006-12-09
I have that same issue and gave up. I tried it with a windows installation (shame on me), and even there it stucks with 1024x768 on DVI.
Does anybody know if a geforce 6600 or radeon 9600 can do 1680x1050 on a DVI? I would get one of those...

---

