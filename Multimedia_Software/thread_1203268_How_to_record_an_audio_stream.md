---
title: "How to record an audio stream"
date: 2009-07-03
forum: Multimedia Software
---

### Post by hellocatfood on 2009-07-03
I'm using VLC 0.9.9a and really need to know how to stream audio from a website to a file. I have found a few tutorials online but they seem to be for older versions of vlc and the instructions don't match.

fyi, I'm trying to record an interview from a radio station I was on

---

### Post by andrew.46 on 2009-07-03
Hi hellocatfood,

> **hellocatfood said:**
> I'm using VLC 0.9.9a and really need to know how to stream audio from a website to a file. 

Can you give the address of the stream? This way a specific solution can be given :-).

Andrew

---

### Post by hellocatfood on 2009-07-04
It used to be located here [http://www.bbc.co.uk/iplayer/aod/playlists/98/3h/30/0p/RadioBridge_1300_bbc_wm.ram](http://www.bbc.co.uk/iplayer/aod/playlists/98/3h/30/0p/RadioBridge_1300_bbc_wm.ram) but that show has expired now.

Do you have any tips for downloading .ram streams?

---

### Post by andrew.46 on 2009-07-04
Hi hellocatfood,

> **hellocatfood said:**
> Do you have any tips for downloading .ram streams?

Well, I normally use MPlayer for such streams. First downloading the stream as a wav file:

```
mplayer -cache 2048 -playlist *stream.ram *\
        -vc null -vo null -ao pcm:fast:waveheader:file=stream.wav
```

and then converting the wav file to ogg:

```
oggenc stream.wav -q 6 -o outfile.ogg
```

Bu vlc should be able to convert such streams for you without all the commandline athleticism. Can you select :

media ---> Convert/Save ---> Network ?

The 'Convert / Save' button here should allow you to specify the required output format.

All the best,

Andrew

---

### Post by jmwink on 2009-07-05
I have the same question. I've tried a variety of suggested options -- including VLC, and MPlayer, as well as streamripper -- and none of them seem to actually be saving the output file. 

At first, I thought perhaps my problem was that I was specifying the file incorrectly, but even when I don't specify the directory and direct MPlayer, VLC, or Streamripper to save a file in the home directory, when I exit the program, I have no file named "stream.[wav, mp3, or ogg]".

The only time I successfully received output was from streamripper when I enabled an option to write each 1 second interval as an individual file. But, that's not tremendously useful.

Here's my MPlayer command options:
```
mplayer -cache 2048 -playlist http://wxyc.org/wxyc-mp3.m3u \ -vc null -vo null -ao pcm:fast:waveheader:file=test.wav

``` 

Here's Streamripper:
```
streamripper http://wxyc.org/liveG2.ram -A -l 10 -d ~/Music
```

And VLC:
```
vlc -vvv http://wxyc.org/wxyc-mp3.m3u --sout file/ogg:stream.ogg

```

with the VLC above, I receive an ogg file that is clipped static, and somehow improperly encoded. 

Any help would be appreciated. 

My reasons for doing this is that I am a DJ at this independent radio station and would like to be able to record my show to listen to later. If someone can think of another solution for this purpose, I'm all ears.

---

### Post by arnoldjames on 2009-07-05
I use the prog 'icecream' to record i-radio streams.  Installed with 
**$ sudo apt-get install icecream** 
in a console.  

This is a command line prog for which I've found nothing else (but I have never looked much farther, this works so straightforwardly).  To find commands, again in a console [B]
$ man icecream[/B] 

My usage has been just with the **-t  **option to split the stream into tracks: 

[B]$  icecream -t  [http://website-of-station](http://website-of-station)

[/B]It will name the tracks per whatever the station calls them as far as I can tell. 
It handles m3u and pls.  I've only every used it with .pls links myself.  Hope this works for you.

---

### Post by mc4man on 2009-07-05
Whether mplayer is suitable for what you want, not sure, but to clear up something

> Here's my MPlayer command options:
Code:

mplayer -cache 2048 -playlist [http://wxyc.org/wxyc-mp3.m3u](http://wxyc.org/wxyc-mp3.m3u) [COLOR="Red"]\ [/COLOR]-vc null -vo null -ao pcm:fast:waveheader:file=test.wav

Remove what's in red (\)
Andrew used that to show you it was one command, shouldn't be in the command.

For vlc I'm not up on how to from a .m3u (the 1.0 Rcx versions have a 'record' button that works fairly well on many streams, including yours (records as is, in this case to a .mp3

Edit 
for vlc try the location, at present moment
[http://152.46.7.128:8000/wxyc.mp3](http://152.46.7.128:8000/wxyc.mp3)

---

### Post by jmwink on 2009-07-05
thanks for the replies. icecream appears to be a very simple solution with which i have already had success. thanks for the reply.

i will try the vlc option later, and see what sort of action i get with that. 

thanks again!

also, tune in, if you like each tuesday from 3am-6am EDT to [WXYC]("http://wxyc.org/wxyc-mp3.m3u") for some great music.

---

### Post by andrew.46 on 2009-07-06
Hi jmwink,

> **jmwink said:**
> also, tune in, if you like each tuesday from 3am-6am EDT to [WXYC]("http://wxyc.org/wxyc-mp3.m3u") for some great music.

Just to give MPlayer another plug: Since this is an mp3 stream it can be captured quite neatly by MPlayer without any extra conversions. This time on only *one* line:

```
mplayer -playlist http://wxyc.org/wxyc-mp3.m3u -dumpstream -dumpfile output.mp3
```

Andrew

---

### Post by jmwink on 2009-07-06
Mplayer does work nicely, now that I understand the command ;)

I'm finding the Icecream tool very useful for this project because it so easily allows me to record streams on a timer.

(Just one more reason why I like Ubuntu and the forums -- always many options)

---

### Post by hellocatfood on 2009-07-11
> **jmwink said:**
> I have the same question. I've tried a variety of suggested options -- including VLC, and MPlayer, as well as streamripper -- and none of them seem to actually be saving the output file. 

At first, I thought perhaps my problem was that I was specifying the file incorrectly, but even when I don't specify the directory and direct MPlayer, VLC, or Streamripper to save a file in the home directory, when I exit the program, I have no file named "stream.[wav, mp3, or ogg]".

The only time I successfully received output was from streamripper when I enabled an option to write each 1 second interval as an individual file. But, that's not tremendously useful.

Here's my MPlayer command options:
```
mplayer -cache 2048 -playlist http://wxyc.org/wxyc-mp3.m3u \ -vc null -vo null -ao pcm:fast:waveheader:file=test.wav

``` 

Here's Streamripper:
```
streamripper http://wxyc.org/liveG2.ram -A -l 10 -d ~/Music
```

And VLC:
```
vlc -vvv http://wxyc.org/wxyc-mp3.m3u --sout file/ogg:stream.ogg

```

with the VLC above, I receive an ogg file that is clipped static, and somehow improperly encoded. 

Any help would be appreciated. 

My reasons for doing this is that I am a DJ at this independent radio station and would like to be able to record my show to listen to later. If someone can think of another solution for this purpose, I'm all ears.

This worked for me :-D thanks!

I think I'll check out icecream in future. Seems like a useful option too

---

### Post by mukluk1 on 2009-12-04
Hello. Im new. Ive been browsing the forums for some time and finally decided to subscribe.

My problem is i cant figure how to use mplayer to capture streaming content for later listening on my portable device.

[http://www.wfmu.org/listen.m3u?show=33822&archive=57170](http://www.wfmu.org/listen.m3u?show=33822&archive=57170) 
is location of stream

ive tried:
 mplayer -playlist [http://www.wfmu.org/listen.m3u?show=33822&archive=57170](http://www.wfmu.org/listen.m3u?show=33822&archive=57170) -dumpstream -dumpfile billkelly.mp3
I get:
[1] 11478
Resolving [www.wfmu.org]("http://www.wfmu.org") for AF_INET6...
Couldn't resolve name for AF_INET6: [www.wfmu.org]("http://www.wfmu.org")
Resolving [www.wfmu.org]("http://www.wfmu.org") for AF_INET...
Connecting to server [www.wfmu.org]("http://www.wfmu.org")[216.118.106.242]: 80...
Cache size set to 320 KBytes
Error while parsing playlist
Warning: empty playlist
Error parsing option on the command line: -playlist
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
-dumpstream: command not found

I am humbly asking for any advice on this matter. thanks in advance for any advice.

---

### Post by arnoldjames on 2009-12-04
I took a look at the site you're trying to record from.  I found the command line program 'icecream' works just fine. If you wish to try this option, you need to install icecream, then from a console do:

$ sudo apt-get install icecream 
$ icecream -t [http://wfmu.org/wfmu.pls](http://wfmu.org/wfmu.pls)

The -t divides it up into named tracks as mp3s.  

This is also posted abut above in this thread.

---

### Post by andrew.46 on 2009-12-04
Hi mukluk1,

> **mukluk1 said:**
> ive tried:
```
 mplayer -playlist http://www.wfmu.org/listen.m3u?show=33822&archive=57170 -dumpstream -dumpfile billkelly.mp3
```


The shell does not react well to some of the characters in that address so you simply need to place some apostrophes in place:

```
 mplayer -playlist **[COLOR="Red"]'[/COLOR]**http://www.wfmu.org/listen.m3u?show=33822&archive=57170**[COLOR="Red"]'[/COLOR]** -dumpstream -dumpfile billkelly.mp3
```

All the best,

Andrew

---

### Post by sds on 2010-06-03
A noob question (and sorry to bring up an old thread) - I'm trying to record a radio stream using icecream, used the following command:
icecream --stop=180min --name=EastFM -v [http://41.215.22.2:8000/mediumstream.ogg](http://41.215.22.2:8000/mediumstream.ogg)

Any idea where it saves files? I've had a look in a few places and can't find any anywhere.

---

