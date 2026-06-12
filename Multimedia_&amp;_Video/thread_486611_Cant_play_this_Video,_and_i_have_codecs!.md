---
title: "Cant play this Video, and i have codecs!?"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by Rick123 on 2007-06-28
Movie info:
**Type:**AVI video

**Size:**701.6 MB (735663716 bytes)

**MIME TYPE:**video/x-msvideo

**Video**

Dimensions:1024 x 800

Codec:ISO MPEG-4 (XviD, ffmpeg)

framerate:15 frames per second

here is some info on the movie, dont know if this will be to any help? But i have tried to play the movie in all the players and it will not work, i guess i need more codecs, If this is the problem, were can i get more codecs, i got the codecs that i installed from using Automatix, and what i thought was this all codes i need, but i guess i am wrong. So if i need more codecs direct me to the place and help me install them, i am not so good at insaling things in ubuntu, so if you want to take me step by step, that would be a great idea! :D
But maybe i have some other difficulties, dont know... Hope you can help me, if you need more info, just tell me how to type it to get the info and i get it for you here, so you can help me. Ps: i use Fiesty

---

### Post by koshari on 2007-06-28
> Ps: i use Fiesty

do you mind mentioning the player you are using, 

you could try xine with the xine extracodecs.

you could try vlc with its inbuilt codecs, or you could try totem with its gstreamer codecs, 

you could also install w32codecs from medibuntu.

where did you get the header info?

---

### Post by raul_ on 2007-06-28
Those ought to be enough. Have you tried the xine-ui player? It works for me, it plays anything I throw at it

---

### Post by Rick123 on 2007-06-28
The players i have tried...they are the following:
**gxine**
**kaffeine**
**Movie Player**
and
**VLC**

I have the w32codecs
I got the header info from right clicking on the movie and go to Properties... 
Dont know if its the movie that are broken, but i dont believe so.
Any other idea? 

Thanks for the answers and your time answering them!

Cheers!!

---

### Post by Noobish on 2007-07-04
> **Rick123 said:**
> The players i have tried...they are the following:
**gxine**
**kaffeine**
**Movie Player**
and
**VLC**

I have the w32codecs
I got the header info from right clicking on the movie and go to Properties... 
Dont know if its the movie that are broken, but i dont believe so.
Any other idea? 

Thanks for the answers and your time answering them!

Cheers!!

I'm also having the same issue in dapper 6.06 i did everything you did and i cant play AVI
i dunno what the **** i'm doing wrong.

---

### Post by Wiebelhaus on 2007-07-04
> **Noobish said:**
> I'm also having the same issue in dapper 6.06 i did everything you did and i cant play AVI
i dunno what the **** i'm doing wrong.

I absolutely love the fact that this dude's sig says "Thanks , Kevin" lol

---

### Post by Gremlinzzz on 2007-07-04
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
[https://help.ubuntu.com/community/RestrictedFormats/NonNativeCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/NonNativeCodecs?highlight=%28codecs%29)
for the noobs there is a help full guide
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty).
for divxs online and off
What i have too do to setup mplayer first i uninstall totem and its plugin.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/Re...t=%28codecs%29](https://help.ubuntu.com/community/Re...t=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
last but not least i test mplayer plugin at [http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
if its gray i config the settings by right clicking the video window and choose X11 video &ALSA audio
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.
these are the setup tweaks i learned for mplayer i could not find tweaks that match em for totem.

---

### Post by Noobish on 2007-07-04
> **sx66gns said:**
> I absolutely love the fact that this dude's sig says "Thanks , Kevin" lol

I'm just a noob i guess being polite and giving my name is acceptable in a forum.
Please respond to answers from post. Thanks<NOOBISH

---

