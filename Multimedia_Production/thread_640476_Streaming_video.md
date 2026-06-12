---
title: "Streaming video"
date: 2007-12-14
forum: Multimedia Production
---

### Post by Nevon on 2007-12-14
I've been fascinated by live video streams for a while now. I've been thinking about setting up a live webcam feed from my apartment, but I haven't managed to get it to work. But now I've come up with a new idea; How about a live stream of my desktop? 
I would need to capture my desktop at all times, and display it in real-time on the internet, with my computer as the server. Would that even be possible?
I want to hear your thoughs.

---

### Post by Nevon on 2007-12-27
Okay, I've figured out how to do it. It's not all that hard really. 
I just need to set up some kind of screenshot software that takes a screenshot every second or so, and then saves it to a certain folder. Then I just write a php-file that automatically displays the newest screenshot. It's not 100% live, but I think that's the closest you can get.
As for my first idea, here's how to do it:
[http://www.aboutdebian.com/webcam.htm](http://www.aboutdebian.com/webcam.htm)

---

### Post by ian dobson on 2007-12-28
Hi,

It's not really streaming, but all you need to do is setup a webcam then create a html page that reloads the webcam image every x seconds.

If you go over to my site at [http://www.planet-ian.com](http://www.planet-ian.com) I've got sometime similar setup.

Regards
Ian Dobson

---

### Post by ian dobson on 2007-12-30
Hi,

Digging through my software archive, I've come accross a java class that uses "double buffering" to display an almost live picture from a webcam. It works by displaying one picture while downloading the next. 

The code isn't finished (I ran out of time) and at the moment it's hardwired to use only one server/page but when I get abit of time I'll see what I can bang up.

I've been meaning to finish it one day but I don't really like java, I'm more of a perl hacker. 

I'll update this thread when the code works.

Regards
Ian Dobson

---

