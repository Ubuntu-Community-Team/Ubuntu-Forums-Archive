---
title: "Video Conversion Advice"
date: 2011-05-05
forum: Multimedia Software
---

### Post by gofurygo on 2011-05-05
Hello

Over the past months, I have tried to find a decent video converter/ripper under ubuntu with a nice (working) gui-frontend. But to no avail. In particular, I tried to convert videos for my mobile which - appearantly - seemed to be a hard task if you are not really into command line - like me.

So I tried the following:

**Arista**: [http://www.transcoder.org/](http://www.transcoder.org/)
From the pre-installed profiles nothing matched my mobiles data. There are downloadable presets, submitted by users, and you can create your own presets, too. I tried that, but the videos just wont play on my mobile. In general, Arista aims towards simplicity which I like, but unfortunately doesnt give you options to adjust your encoding parameters.

I also tried **Transmageddon **but this project has been discontinued.


I desperately tried to find a nice frontend for mencoder or ffmpeg:

**Transcoder** as ffmpeg frontend: [http://transcoder84.sourceforge.net/](http://transcoder84.sourceforge.net/)
This one looked very promissing with nice simple frontend but yet enough options to adjust. I loaded my video for conversion, set all parameters I needed, hit encode... failed :-( All it ever did was to create an 0kb file as output but didnt even start conversion... so the search went on

**jMencode** is a java based frontend to ...guess what... mencoder: [http://jmencode.sourceforge.net/](http://jmencode.sourceforge.net/)
Alright, downloaded, moved to /opt... added link in gnome menu... I loaded the video, adjusted all parameters, hit encode... crashed... closed by itself without doing anything :-(

**WinFF**: [http://winff.org/html_new/](http://winff.org/html_new/)
WinFF has also predefined profiles. For creation of new profiles you need to be versed in command line, too. Recently, my WinFF keeps freezing up when editing profiles...

It was hard to believe there is no decent frontend for "me"... btw.. some of you may say...why you didnt use Avidemux... I personally dont see the point of installing a video-editor for simple encoding jobs...sorry.

So what to do now... I remembered, under windows I always used **Xmedia Recode**: [http://www.xmedia-recode.de/](http://www.xmedia-recode.de/) (sorry, website is in german, but program is available in english, too)
The advantage of this software is the huge number of predefined profiles for a zillion devices out there. I tested the video conversion for my mobile under windows and guess what, it played just fine. So I thought... " what the heck... lets try this beast under wine". Said and done...
Installation went painless, startup too.
I ran the same conversion parameters as on windows and the videos converted perfectly. 

There are 2 minor limitations while running Xmedia Recode under wine:
1) No video preview on the "crop/preview" tab
2) The profile selection is messed up. This needs some explanation. 

    In Windows the setup is "select profile" eg. Samsung...then it will give you eg. 20        different Samsung models in the subcategory to choose from. Under wine, this is completly messed up. What it does is, it will give you 20 Samsung entries in the "select profile" menu, mixed with all HTC, LG, Apple profiles. Now your job is to find the right one for you by trying them 1 by 1 until you can locate your mobile. This isnt too bad, because once you found it it will save that setting until you open Xmedia Recode the next time ;-)

[IMG]http://www.xmedia-recode.de/media/image4.jpg[/IMG]

So for me, Wine+Xmedia Recode is definetly the way to go. Hopefully this will give some of you a little help when you are close to being frustrated about video conversion...

Feedback, corrections or suggestions are highly appreciated ;-)

Cheers

---

