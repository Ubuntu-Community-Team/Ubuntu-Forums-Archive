---
title: "Amarok doesn't play ogg files"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by Saija on 2007-03-19
Hi
First question here, i'm runnig amarok 1.4.3 on kde 3.5.6 runnig on kubuntu edgy eft, the problem is: Amarok play nice mp3's files, but doesn't play any ogg file i have... :confused: 
when trying to play that files it output the following error message:


> No hay un plugin de demultiplexado apropiado. Esto suele significar que el formato de archivo no está soportado.
file:///abc.ogg

in english it will be something like:

> There's no demux plugin available. This may occur because the format it's not supported.
file:///abc.ogg

and when i've tried to play it with Kaffeine the output is this:

> 
xine: demuxer failed to start
xine: found demuxer plugin: OGG demux plugin
xine: plugin de entrada encontrado: file input plugin(Spanish)
xine: input plugin find: file input plugin(English)


i've found something about delete the .xine dir in ~/ but doesn't worked, please somebody with any tip help me

Thanks ):P

---

### Post by ChrisNiemy on 2007-03-19
Try this for OGG-FIles:
```
sudo apt-get install amarok-xine libxine1 libxine-main1 libxine-extracodecs libogg0 liboggflac++2c2 liboggflac3 libvorbis0a libvorbisenc2 libvorbisfile3 vorbis-tools vorbisgain flac
```

In Amarok options choose the xine backend for sound.

I guess probably libxine-extracodecs and vorbis-tools are missing.



-------------
EDIT: Wah, sorry, it read the heading wrong. Following solution is about FLAC files.
Hi there!

I had this issue once. It was because I created these Ogg-Files with Grip.
But the tags that Grip produces for Oggs are not correct. That's way the xine library of Amarok won't play them. With Totem they did work for me.

If this is your problem, too, try this:
Rip a .wav from a CD. Then for example ```
flac -8 song.wav
```
So just converting a wave file into ogg vorbis with no tagging. I bet, that Amarok WILL play this file.

Check this thread, solution at the end there: [http://www.ubuntuforums.org/showthread.php?t=210683](http://www.ubuntuforums.org/showthread.php?t=210683)

---

### Post by Saija on 2007-03-19
Thanks for your response, exactly the problem appears to be with the riping method used to create the ogg, unfortunaterly totem can't open it, and i don't have the cd to riping it again, i'm gonna check the link to the other post to hunt this problem, bye ):P

---

### Post by Saija on 2007-03-20
I've read the entire post ChrisNiemy recommended and can't play that ogg files, somebody with another solution?

Thanks.

---

