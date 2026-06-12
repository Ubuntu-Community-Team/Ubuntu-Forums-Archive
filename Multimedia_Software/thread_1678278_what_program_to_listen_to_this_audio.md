---
title: "what program to listen to this audio?"
date: 2011-01-30
forum: Multimedia Software
---

### Post by claracc on 2011-01-30
Hello,
I want to listen to this audio file: [http://www.bbc.co.uk/worldservice/learningenglish/multimedia/btp/ram_files/winchester_audio1.ram](http://www.bbc.co.uk/worldservice/learningenglish/multimedia/btp/ram_files/winchester_audio1.ram) but my real player 11.0.0.4028 gold desn play it, it says that there is a codec 28_8 missing, I go to relaplayer page, download the last release available for linux systems, but the message is the same : audio codec missing and doesnt play the audio.

I havev tried to play the audio with smplayer (not luck), vlc can play the audio but the pause button doesn't work so I have to listen the entire audio all the time I stop it playing.

¿Is there any audio player capable od reproducing in the proper way this audio in ubuntu?

Other related question, No one of my video players totem, smplayer, realplayer or vlc are capable of playing this video: [http://www.bbc.co.uk/worldservice/learningenglish/multimedia/btp/ram_files/winchester_vid1.ram](http://www.bbc.co.uk/worldservice/learningenglish/multimedia/btp/ram_files/winchester_vid1.ram).

¿Does anybody knows how to play this video in ubuntu 10.04?

Thanks in advance

---

### Post by JC Cheloven on 2011-02-07
Hi Clara, me pregunto cómo estará mi playa favorita (Oyambre) en estas fechas :)

To the topic: I think you'll have to resort to ffmpeg. I learned to love this wonderful piece of software, because it sometimes works LOL. Please, first of all install these packages if you haven't: ```
sudo apt-get install ffmpeg moc-ffmpeg-plugin
```

Then open a terminal, navigate (cd command) to the directory where your winchester_audio1.ram and winchester_vid1.ram files are, and run 
```
ffmpeg -i winchester_audio1.ram  winchester_audio1.wav
```
For some reason, the process stalled for me when the file was 585Kb, so I simply terminated the process pressing 'q'. Despite of this, the generated .wav file seems fine, it is 37 secs long. It contains a short speech in english with a lot of dates and a final mention to Shakespeare and Dickens, if I at all understood. 

The video file plays in totem for me. It's 15 seconds long, and consists of a slideshow of photos of a statue (it's King Arthur I believe).  A subtitle appears: "beyond the postcard - Winchester - BBC english".
Only, I can't hear the sound. I wasn't able to extract it in a cuple of quick attempts, sorry (btw: ffmpeg reports a weird setup of 2 audio streams and 6 video streams for this file).

Cheers
JC

---

### Post by claracc on 2011-02-08
Hello JC Cheloven, thankyou very much for answering.

Por cierto Oyambre, está más bonita que nunca, sobre todo estos días que está haciendo tan buen tiempo.

I have tried the two advices:

Abot the audio ram file, I cannot convert it to wav with ffmpeg, the error showned is : winchester_audio1.ram: Invalid data found when processing input

About the video, I try to play it in totem, but it only appears the image of the statue of a king and no more, and not sound neither.

I tried to use realplayer for windows running in wine but no luck, also I tried to run real alternative in wine for the video file but I couldn't see any image. Trying vlc and smplayer goes better but there are problems too.

For now, It seems the only proper way to listen to or see this ram files is real player for windows, since trying them in ubuntu gives one or other problems

---

### Post by nothingspecial on 2011-02-08
I can get the audio with
```

mplayer -playlist http://www.bbc.co.uk/worldservice/learningenglish/multimedia/btp/ram_files/winchester_audio1.ram
```

But mplayer doesn`t seem to think there is any video :confused:

---

### Post by claracc on 2011-02-08
Thankyou nothingspecial

I have tried to listen the bbc audio ram file with mplayer, and yes, It works, so I'll use mplayer for bbc listenings (I haven't tried mplayer).

I think there are missing video codecs to play the video file in my ubuntu players: vlc, smplayer, mplayer, totem, also realplayer for linux

The video file, can be played  with real player for windows in my windows vista partition.

---

### Post by claracc on 2011-02-08
One thing I don't understand is that if mplayer can play de audio file [http://www.bbc.co.uk/worldservice/learningenglish/multimedia/btp/ram_files/winchester_audio1.ram](http://www.bbc.co.uk/worldservice/learningenglish/multimedia/btp/ram_files/winchester_audio1.ram) from xterm with the command mplayer -playlist [http://www.bbc.co.uk/worldservice/learningenglish/multimedia/btp/ram_files/winchester_audio1.ram](http://www.bbc.co.uk/worldservice/learningenglish/multimedia/btp/ram_files/winchester_audio1.ram), why smplayer ( the advanced frontend gui of mplayer) cannot play the file?

Any idea is very well welcome

Regards

---

### Post by nothingspecial on 2011-02-08
I haven`t used smplayer much but the underlying problem is that the bbc puts their listen again content in a link as a playlist - hence the -playlist option

If I type, for example

```
mplayer http://bbc.co.uk/radio/listen/live/r6.asx
```

which is a live stream, it doesn`t work but with the -playlist option it does.

```
mplayer -playlist http://bbc.co.uk/radio/listen/live/r6.asx
```

Have you tried adding the link as a playlist in smplayer (if this is possible)?

---

### Post by claracc on 2011-02-08
```
the underlying problem is that the bbc puts their listen again content in a link as a playlist - hence the -playlist option
```

It makes sense.

I cannot put the link to the listening as a playlist in smplayer.

Thanks

Regards

---

### Post by gordintoronto on 2011-02-08
For me, Firefox plays both the audio and video properly, after a delay of almost a minute. Previously, I enabled the Medibuntu repository and installed the non-free codecs.

---

### Post by mc4man on 2011-02-08
gnome-mplayer can play the video stream fine or as noted above it can be opened in firefox.
If using the gecko-mediaplayer browser plugin then it should open directly in a browser window.
If using the totem-mozilla plugin it probably won't but can be directed to gnome-mplayer as in screen. 

(note - only one browser plugin should be installed at once, if switching to gecko-mediaplayer then remove the totem-mozilla package, ect.

---

### Post by claracc on 2011-02-08
Thankyou very much to all of you.

As adviced, I have installed gnome-mplayer and gecko-mediaplayer plugin, gnome-mplayer can play any of the audio or video ram files, even though it takes long time to load the files. Also, they can be played directly in firefox with the plugin.

I am going to mark the thread as solved.

Regards

---

### Post by JC Cheloven on 2011-02-09
> **claracc said:**
> Hello JC Cheloven, thankyou very much for answering.

Por cierto Oyambre, está más bonita que nunca, sobre todo estos días que está haciendo tan buen tiempo.

I have tried the two advices:

Abot the audio ram file, I cannot convert it to wav with ffmpeg, the error showned is : winchester_audio1.ram: Invalid data found when processing input

About the video, I try to play it in totem, but it only appears the image of the statue of a king and no more, and not sound neither.

I tried to use realplayer for windows running in wine but no luck, also I tried to run real alternative in wine for the video file but I couldn't see any image. Trying vlc and smplayer goes better but there are problems too.

For now, It seems the only proper way to listen to or see this ram files is real player for windows, since trying them in ubuntu gives one or other problems

Glad you solved your problem either way.

It's still strange that ffmpeg worked for me for audio, and not for you. I'm also on Lucid, as you. Anyway, [here]("http://www.4shared.com/audio/WDLrKLHr/winchester_audio1.html") is my output file from ffmpeg, so you can check if it is complete, or whatever. 
Also strange that totem don't show the video for you. Surely I have installed a different set of codecs. As far as I can remember, all I have is ubuntu-restricted-extras and non-free codecs though.

Anyway. Cheers, and enjoy Oyambre, you the lucky one :) 
JC

---

### Post by claracc on 2011-02-11
Hello JC Cheloven,

I could also, with the help of ron999 in the Tutorials and tips subforum, convert the ram audio file to wav > Hi claracc
ffmpeg can't convert the link as it is.
Right-click on that link [http://www.bbc.co.uk/worldservice/le...ter_audio1.ram](http://www.bbc.co.uk/worldservice/le...ter_audio1.ram)

And 'Save link as...'.
You'll get a file named winchester_audio1.ram in your home folder.

Open that file with gedit text editor or similar.
You'll see that it says:-
rtsp://rmv8.bbc.net.uk/worldservice/learningenglish/beyondthepostcard/winchester1.ra?BBC-UID=144d2571dee4faed59a5a50dd10e5c0aa1f1b2cb709051 9424bff4f638d05eda&SSO2-UID=

You only need the part up till the question mark (?).
Which is
rtsp://rmv8.bbc.net.uk/worldservice/learningenglish/beyondthepostcard/winchester1.ra

Now you can use that with ffmpeg.
Like this:-
Code:

ffmpeg -i rtsp://rmv8.bbc.net.uk/worldservice/learningenglish/beyondthepostcard/winchester1.ra winchester_audio1.wav



Now, I can listen to the audio in wav format.

Thanks to you, who revive this thread, and so it could be solved.:)

Regards

---

### Post by JC Cheloven on 2011-02-11
> **claracc said:**
> 
Thanks to you, who revive this thread, and so it could be solved.
My pleasure :)
See u in the forums!
JC

---

