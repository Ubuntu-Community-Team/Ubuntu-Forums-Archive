---
title: "Need help with Totem-xine to play mms streaming"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by fable on 2007-05-14
I am using totem-xine for multimedia and video.  It works fine with most of the sites I am interested.  However, I cannot play the streaming video from the following sites:

[http://www.bnn.ca/](http://www.bnn.ca/)

[http://news.bbc.co.uk/2/hi/video_and_audio/default.stm](http://news.bbc.co.uk/2/hi/video_and_audio/default.stm)

For the BNN site, when I select a streaming video, I got the error message "Totem could not play /mms://boradcast2.globeinteractive.com/streaming_ads/generic/generic_ad_wm_high.wmv'
The connection to this server was refused".  Is there some dependencies that I need to install for totem-xine to play mms streaming?

For the BBC site, when I select a streaming video Real Player will open but I only get audio and no video.  Is there some option that I need to set with Real Player to play video from BBC?


:confused:

---

### Post by fable on 2007-05-15
For the BBC site, I cannot get it to work if I choose the Windows Media Player option, i.e. no video and no audio.  If I choose Real Player, I have audio but no video.  

However, for other sites that requires Windows Media Player or Real Player, I don not have any problems.

Ubuntu Feisty is great and I love it.  However I have some technical background and is willing to put up with the difficulty to deal with the multimedia problems.  if Ubuntu cannot solve the multimedia support or licensing issues, it will be difficult for the general public to adopt it as their desktop OS.

---

### Post by bob1234 on 2007-05-31
Hey Fable, 

I could not agree more. I have also been trying very hard to get bnn.ca to work but with no luck.

If anyone has any ideas please suggest. 

I would hate to have to dual boot over something like this.

Thanks All :)

---

### Post by auryn21 on 2007-05-31
I don't know about BNN but BBC works fine for me. I use the Totem Mozilla plugins with all of the gstreamer plugins installed and I can watch video if I choose the wmv option. I can also watch video if I choose the Real Player option. MPlayer mozilla plugin won't work for BBC, you have to install RealPlayer and configure Firefox to use it instead to handle .rm files.

---

### Post by fable on 2007-06-05
I use Totem-Xine instead of gstreamer.  I have problem with gstreamer and mplayer for other sites so I switched to Totem-Xine.  Xine seems to work for most sites I am interested in except for BNN and BBC.

---

### Post by rfurman24 on 2007-06-05
I can play both using mplayer and mplayer plugin with the second link set on windows media.

---

### Post by bob1234 on 2007-06-17
I seem to have mplayer working but only mplayer will work and not gmplayer... Does anyone know if there is a way to get bnn to play with a program that will let you pause/fastforward the stream? Thanks

---

### Post by Kismet on 2007-06-19
I'm not sure this will solve the bnn issue,  but I'm a football fan, and MLSNET uses Windows media MMS streams for their season ticket. I was unable to get this to work with the standard Totem(gstreamer), the plugin would just pop-up and say "stopped" with no explanation as to why it wasn't working. When I tried to copy the media url and open it manually in totem, it would say unable to open stream. I first solved it by using kaffeine, but then noticed that kaffeine uses xine instead of gstreamer. 

Long story short, installing totem-xine allowed me to watch my precious games online in either firefox or standalone totem. :p

---

### Post by fable on 2007-06-21
I tried mplayer.  My computer has Realplayer 10 installed.  With mplayer installed, when I played realplayer files, I only get audo no video.  I don't know why realplayer is affected.

---

