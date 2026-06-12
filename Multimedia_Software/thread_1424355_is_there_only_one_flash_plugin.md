---
title: "is there only one flash plugin"
date: 2010-03-07
forum: Multimedia Software
---

### Post by degarb on 2010-03-07
I have old single core cpu and flash video looks more like slide show than video. I refuse to watch flash.

I assume flash is the problem and not bitrate since anything not flash plays fine. 

Is there some alternative plugin that will handle adobe flash?

PS. Adobe, I hate your pdf viewer as well.  Neither of these products work.  Bloated and neither run quickly and reliably.

---

### Post by puzzler995 on 2010-03-07
GNASH and SWFviewer. look in the repositories

---

### Post by degarb on 2010-03-07
> **puzzler995 said:**
> GNASH and SWFviewer. look in the repositories
  
I uninstalled adobe and installed gnash.  But gnash was more bloated and unresponsive than adobe.  even more slideshowish than adobe.

I then uninstalled and tried swf plugin.  I could only get audio to play with this.

So, I reinstalled adobe, for now.  Still horrible.

---

### Post by puzzler995 on 2010-03-08
Try all 3 at once. That's what I have

---

### Post by no2498 on 2010-03-08
if what they say does not help try this
open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to/    x window system (no xv)
rite down what its set to so you can set it back if it does not help

and you may need to restart the computer to see it work

gstreamer is in the add/remove if not installed

enjoy some nice movies now

---

### Post by degarb on 2010-03-08
> **no2498 said:**
> if what they say does not help try this
open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to/    x window system (no xv)
rite down what its set to so you can set it back if it does not help

and you may need to restart the computer to see it work

gstreamer is in the add/remove if not installed

enjoy some nice movies now

I must conclude that taking it off autodetect does nothing for flash.  And, it makes the wma play far worse, more like the slideshow of flash.

I don't see how installing all three flash product at once would do anything.  I am running this way now, and seriously cannot stand to watch anything flash, because there is nothing but a slideshow when watching flash, still.

---

### Post by puzzler995 on 2010-03-08
> **degarb said:**
> I must conclude that taking it off autodetect does nothing for flash.  And, it makes the wma play far worse, more like the slideshow of flash.

I don't see how installing all three flash product at once would do anything.  I am running this way now, and seriously cannot stand to watch anything flash, because there is nothing but a slideshow when watching flash, still.

Really this is why I cant wait for HTML5. gonna get rid of all this proprietary stuff

---

### Post by bigbeark on 2010-03-12
If you select Applications -> Sound and Video -> Movie Player, you can elect YOUTUBE from the drop down menu and play youtube videos that way - much less jerky then Flash
player.

This works because Movie Player does not use Adobe Flash - the resolution is lower but no jerking.

Unfortunately, YouTube seems to override Fireox preferences and force ue of lash player.

If you look on System Requirements  for latest Flash player you need a video card with 128MB and 512MB ram as a minimum.

There are archived versions of the Flash player you can download from Adobe, but you have to package and intall them yourself. Thye are in zip format.

If anyone has successfully done this or wants to try and let us know how it worked...

---

### Post by Yellow Pasque on 2010-03-12
Look for a FF extension called video download Helper, so you can save the videos to your hard disk and bypass Flash. I think there's also a dedicated program(s) for browsing ytube and/or hulu directly.

---

### Post by puzzler995 on 2010-03-14
> **Temüjin said:**
> Look for a FF extension called video download Helper, so you can save the videos to your hard disk and bypass Flash. I think there's also a dedicated program(s) for browsing ytube and/or hulu directly.
[QUOTE=bigbeark]If you select Applications -> Sound and Video -> Movie Player, you can elect YOUTUBE from the drop down menu and play youtube videos that way[/QUOTE]
The problem is that those arent the only flash enabled sites. For example my County School System's website is flash enabled [http://www.ccsweb.cabarrus.k12.nc.us/education/components/scrapbook/default.php?sectionid=1](http://www.ccsweb.cabarrus.k12.nc.us/education/components/scrapbook/default.php?sectionid=1)

---

### Post by chris1379 on 2010-06-19
I'm with you on this one. Did you find a solution? I use Downloadhelper for youtube and most other sites but it doesn't work for Hulu. Anyone have a good solution for Hulu. If I had Windows XP I could use StreamTransport at [http://www.streamtransport.com/](http://www.streamtransport.com/)
It works wonderfully on my XP PC. I wonder if it could run under Wine?

---

### Post by jimbob on 2010-07-15
I couldn't get StreamTransport to run under wine - don't know why but it doesn't present the video window at the top of the page the way it does in ex pee.

Has anyone else had any luck with this?

---

