---
title: "Ubuntu 10.10 64Bit |Flash player stops with live streams."
date: 2011-05-04
forum: Multimedia Software
---

### Post by Sikez on 2011-05-04
Not sure if I'm asking this in the right area of the forum.

I've been having a problem for quite sometime now with Ubuntu 10.10 64Bit (KDE desk top & Gnome) and flashplayer.I have also spent a week looking through this forum & google for a solution and have not found one yet.

Here is the problem I'm having.
Flasher player seems to work fine on sites like youtube and most other pre-recorded type video sites.
However,when I try to view a flash stream that is live (in real time) from like a news channel or
a live sporting event or even a live webcam feed embedded on a site the player 
starts up and the feed works fine for about 1 minute or 2 at the most, then the feed
stops/freezes and I have to reload the entire page.
I have tried many live feed/stream sites and it happens with all of them.

One of first things I tried was Flash Aid 2.0.8 that was suggested on this site numerous times and that did not help with this problem at all.
I have also updated flash and also tried numerous versions of flash player even 
the 32 bit ones with still no luck.
I have even tried different browsers up to FireFox 4,under Gnome & KDE.
Nothing seems to work to fix this problem.

Could this be more then just a flash problem?
Has anyone else had this issue?
What else could I check try to trouble shoot?
My Internet connection is fast and very stable also.

This link here ( [http://bcove.me/fz8lfrx9](http://bcove.me/fz8lfrx9) ) would be an example of a pre recorded video that stops after a couple of minutes for me.
However I'm able to watch it fine on a 10 year old tosibia satelite laptop running windows 98 with hardly any ram lol,so it is obviously not the video and the problem is not on their side of the stream.
The box I have Ubuntu 10.10 is newer system less then a year old with 16GB                         of ram.....so I know it is not a resource issue and the system stays cool.


Any help would be greatly appreciated.
Thank you.

---

### Post by Sikez on 2011-05-04
Any advice at all? :)

The system setup I have is 64bit ,I had set it up mainly for watching online live video events and surfing the web as sort of a play computer...with a big 30 inch monitor.And the reason I went to (switched to) ubuntu 10.10 64bit was because I liked the KDE Desk top environment ,it looks super cool on a big 30inch monitor. 

I really don't want to go back to windows vista64 or 7 on this setup if I don't have to.But I have a few grand invested into the hardware side of this setup and would like it to work for what I wanted it to do at the full potential of a 64bit system.  

Does anyone know where I can get some support for this issue ,a forum or whatever other then adobe(where i went first).

Any help at all would be greatly appreciated.
Thank you again for reading.

---

### Post by Sikez on 2011-05-05
Upon looking into this issue a little more.
It seems that what is happening is that the flash player
disconnects from the stream. I went to a few live stream
sites and a couple of them gave me a disconnect error.

[B]Could this be an issue with the graphics driver I'm using
(ATI/AMD proprietary FGLRX graphics diver)???[/B]
Anyone?

Should I switch to the "free open source radeon/ati driver"?
(It says my card has Accelerated 3D support with that driver so I would still have 3d)
Any thoughts on if this would make a difference with the problem I'm having?
Has anyone used both these drivers...pros & cons?

Also would updating to 11.04 possibly solve this issue?
Any advice would be appreciated!
Thanks._****_[URL="http://ubuntuforums.org/showthread.php?t=1744693"]
[/URL]

---

### Post by Yellow Pasque on 2011-05-05
The best thing I can suggest is removing all Flash players from your system and using sevenmachines' PPA: [https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

If that doesn't work, start firefox (or other browser) from the terminal and attempt watching the stream.

I also use fglrx on my laptop and I will try and view your video when I get home and have a better connection.

---

### Post by Sikez on 2011-05-05
> **Temüjin said:**
> The best thing I can suggest is removing all Flash players from your system and using sevenmachines' PPA: [https://launchpad.net/~sevenmachines/+archive/flash]("https://launchpad.net/%7Esevenmachines/+archive/flash")

If that doesn't work, start firefox (or other browser) from the terminal and attempt watching the stream.

I also use fglrx on my laptop and I will try and view your video when I get home and have a better connection.

Thanks for the reply.
I purged all the flash players  from my system and installed                 flashplugin64-nonfree,but still no luck.
Also tried opening browsers from the terminal,still the same problem. 
Also, Justin.tv would be an example of a live feed site that disconnects from flash player after about 2 minutes,then it starts back up again. 

However,one thing I did find is that installing the most updated version of wine and then installing opera-browser under wine,I was able to play live streams and also that video above without it disconnecting.The video quality wasn't all that great and the browser sorta lagged a bit,but it did work.

---

### Post by handy on 2011-05-06
I'm using 64bit Arch, Firefox 4.0.1, & the beta version of the FlashVideoReplacer add-on. 

I can watch the linked to live video streaming page, with all cookies blocked, no problems at all, sharp & clear?

Whether that add-on is helping me or not I don't know, I only installed it last night, after which another Flash problem that I was having disappeared. :)

---

