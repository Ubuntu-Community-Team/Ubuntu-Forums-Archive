---
title: "can you play this video on firefox in ubuntu 9.10 ?"
date: 2010-03-14
forum: Multimedia Software
---

### Post by johantri on 2010-03-14
Hello guys,

I'm an excited newcomer in ubuntu and i'm also an animator. and i have problem playing all streaming video from this particular website (the 11 second club), probably they use quicktime plugin or something. In addition, we can play the stream frame by frame so we can check the animation more details on poses.

could you guys help me out with this...? this website is an important learning centre for me, and definitely for many animators out there who use ubuntu.

here's an example:

[http://www.11secondclub.com/competitions/february10/winner/](http://www.11secondclub.com/competitions/february10/winner/)

Thank you in advance, :)

---

### Post by hxcobd on 2010-03-14
The movie appears to be an MP4 file, according to the source code.

Video plays fine for me in Google Chrome, using what I assume is Totem.

---

### Post by robertcoulson on 2010-03-14
I tried your movie and I can run it with no problem at all....I use Ubuntu 9.10 right out of the box
Robert

---

### Post by Uncle Spellbinder on 2010-03-14
Plays fine here as well on my 9.10, 32 bit  install.

---

### Post by Rasa1111 on 2010-03-14
plays fine here as well. 
also 9.10 32 bit. 

wish i could actually help, but i cannot. lol
sorry. 
good luck

---

### Post by robertcoulson on 2010-03-14
Hey Johantri...I went back and tried it again and got the same thing as you did..I clicked the button (progression button) and it then played ok...Give it a try.
Robert

---

### Post by 2hot6ft2 on 2010-03-14
Doesn't play if Adblock Plus is enabled but it works if it's off.

---

### Post by robertcoulson on 2010-03-14
How do you disable " Adblock Plus " and will it affect anything else...???
Robert

---

### Post by NightwishFan on 2010-03-14
It plays in Debian Sid, on Firefox. Totem plugin. If it does not for you, install gstreamer plugins, such as bad and ugly.

---

### Post by johantri on 2010-03-14
works on chrome here. however when i try to scrub the video frame by frame it plays jerky. and after googling i just find out that i dont have Adblock Plus in my firefox. so  i guess something must went wrong with my ubuntu... ~_~

thanks for all respons :)

---

### Post by steve161 on 2010-03-14
It played for me with adblock plus enabled and using gecko-mediaplayer plugin.

---

### Post by Rasa1111 on 2010-03-14
to disable ad block plus,  i think you have to go to tools>add ons> and click "disable" on the ad block plus add on. 
 (though this will disable it for all websites)
 when i used windows i had a little icon in my toolbar that i could disable it for a single page, but havent figured that out or tried it yet in ubuntu.

p.s.. there is also an "ad block plus preferences" in the tools tab.

---

### Post by polki@mac.com on 2010-03-16
Perfectly on 9.10 64-bit using gecko-mediaplayer in Firefox.

[Edit:] Adblock Plus active as well!

---

### Post by HotForLinux on 2010-03-16
Yes, I can see it perfectly well with Firefox in Hardy Heron

---

### Post by J_Stanton on 2010-03-16
works for me with the mozilla-mplayer plugin. try: sudo apt-get install mozilla-mplayer non-free-codecs

---

### Post by kalasoka on 2010-03-16
I too was able to view the animation on XUbuntu 9.10 with Firefox 3.6

I don't have Adblock Plus installed. But I do have the following plugins installed:
DivX Web Player
QuickTime Pugin 7.2.0
Shockwave Flash
VLC Multimedia Plugin
Windows Media Player plugin

I guess you need to download the different libraries required for playing audio / video.

---

### Post by ron999 on 2010-03-16
It's easy to download too with 'downloadhelper' addon for firefox.
Here:-[http://www.downloadhelper.net/]("http://www.downloadhelper.net/")

This is the file information:-
> General
ID                               : 668937332 (0x27DF2C74)
Complete name                    : Street_.ogg
Format                           : OGG
File size                        : 1.68 MiB
Duration                         : 19s 249ms
Overall bit rate                 : 732 Kbps
Writing application              : ffmpeg2theora-0.25+svn16656
SOURCE_OSHASH                    : 4fa847a7273ddff9

Video
ID                               : 6746277 (0x66F0A5)
Format                           : Theora
Duration                         : 19s 250ms
Bit rate                         : 630 Kbps
Nominal bit rate                 : 712 Kbps
Width                            : 560 pixels
Height                           : 316 pixels
Display aspect ratio             : 16:9
Frame rate                       : 24.000 fps
Bits/(Pixel*Frame)               : 0.148
Stream size                      : 1.45 MiB (86%)
Writing library                  : Xiph.Org libtheora 1.1 20090822 (Thusnelda)

Audio
ID                               : 2125166695 (0x7EAB7867)
Format                           : Vorbis
Format settings, Floor           : 1
Duration                         : 19s 249ms
Bit rate                         : 64.0 Kbps
Channel(s)                       : 1 channel
Sampling rate                    : 32.0 KHz
Resolution                       : 16 bits
Stream size                      : 150 KiB (9%)
Writing library                  : libVorbis 1.2 (UTC 2007-06-22)



---

### Post by 2hot6ft2 on 2010-03-16
> **robertcoulson said:**
> How do you disable " Adblock Plus " and will it affect anything else...???
Robert
Just click on the AdBlock Plus logo next to the search window and uncheck Enable AdBlock Plus.
May have to close the window and reopen it.

Just re-enable it when you're done.

---

### Post by wojox on 2010-03-16
Works here in Chrome and your not missing much ;)

---

### Post by 11sc on 2010-04-05
Hi. We actually use HTML5 video with h.264 or ogg/theora. In Firefox 3.6 you shouldn't need any plugins to view our video. It works in my Ubuntu 9.10 installation.

---

