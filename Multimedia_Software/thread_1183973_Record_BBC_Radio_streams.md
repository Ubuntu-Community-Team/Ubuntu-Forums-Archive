---
title: "Record BBC Radio streams"
date: 2009-06-10
forum: Multimedia Software
---

### Post by ajgreeny on 2009-06-10
I can record BBC radio streams to file, either as .mp3 or as .wav using the commands in terminal ```
mplayer -cache 2048 -playlist http://www.bbc.co.uk/radio2/realmedia/fmg2.ram -vc null -vo null -ao pcm:fast:file=BBCR2.mp3
```or ```
mplayer -cache 2048 -playlist http://www.bbc.co.uk/radio2/realmedia/fmg2.ram -vc null -vo null -ao pcm:fast:waveheader:file=BBCR2.wav
```Both work fine except for the fact that the mp3 files are recorded at a bitrate of 1411kbps, making the resulting file as large as a wav (~10mb/min).  The main reason for choosing mp3, or perhaps ogg, but I've not tried to record to that yet, was to reduce the file size.

Does anyone know a way of recording to a lower bitrate, by specifying that requirement in the command?  I'm sure there must be a way, I just don't know it.

---

### Post by andrew.46 on 2009-06-10
Hi ajgreeny,

> **ajgreeny said:**
> Both work fine except for the fact that the mp3 files are recorded at a bitrate of 1411kbps, making the resulting file as large as a wav (~10mb/min).  The main reason for choosing mp3, or perhaps ogg, but I've not tried to record to that yet, was to reduce the file size.

If you have a close look at both of the generated files you will see the solution: they are *both* wav files. When you use '-ao pcm' no matter what you call the output file MPlayer will generate a wav file. The solution would be to use an extra step and transcode to mp3 using lame and this is what I normally do myself.

All the best,

Andrew

---

### Post by ajgreeny on 2009-06-10
Thanks for the information, I did wonder about that.

What is the extra step I must take to get an mp3.  I assume I will have to add something extra to the command at some point and get rid of the *-ao pcm*, but what should I add instead, please?  I have lame installed as well as mencoder, ffmpeg and just about every codec known to computers, but I'm afraid my knowledge of how to use lame is a bit shaky.

From *man lame*, It looks almost as if I can just add "& lame BBCR2.wav BBCR2.mp3" to the end of the wav version of my command, but I suspect it is not that easy, and it will still leave the huge wav file behind if I do that, I think.
Perhaps you just mean to convert the wav file once it has been made and then delete it, but there must be a way to do it in the one command, surely.

Help me, please.

---

### Post by andrew.46 on 2009-06-10
Hi ajgreeny,

> **ajgreeny said:**
> What is the extra step I must take to get an mp3.  I assume I will have to add something extra to the command at some point and get rid of the *-ao pcm*, but what should I add instead, please?  I have lame installed as well as mencoder, ffmpeg and just about every codec known to computers, but I'm afraid my knowledge of how to use lame is a bit shaky.

From *man lame*, It looks almost as if I can just add "& lame BBCR2.wav BBCR2.mp3" to the end of the wav version of my command, but I suspect it is not that easy, and it will still leave the huge wav file behind if I do that, I think.

Hmmm..... you mean something like:

```

mplayer -cache 2048 -playlist http://www.bbc.co.uk/radio2/realmedia/fmg2.ram \
        -vc null -vo null -ao pcm:fast:waveheader:file=BBCR2.wav && \
        lame --preset fast standard BBCR2.wav bbc_radio2.mp3 && \
        rm BBCR2.wav

```

I regularly capture a radio stream using something a little like this but it becomes easier to use a script rather than stringing it all together with '&&' in particular if you need to automatically start and stop the stream. Have a look at:

Slackware and "For The God Who Sings"
[http://www.andrews-corner.org/ftgws.html](http://www.andrews-corner.org/ftgws.html)

and just ignore all the slackware stuff! I will be trimming this page soon and changing flac to ogg but you will see the general idea there...

Andrew

---

### Post by markbuntu on 2009-06-11
I just use kstreamripper to rip the stream and soundkonverter to convert it when I want to make mp3s. The gnome apps are streamripper and streamconverter. They are easy drag and drop.

My memory is not so good to remember all that command line stuff, lol.

---

### Post by ajgreeny on 2009-06-11
I use streamripper but can not get it to work with BBC streams.  Can I ask you how you have managed that, because I can't get kstreamripper to rip the bbc streams either.  No problem with mp3 streams, but the BBC's ram seems to be a no-go to me.

---

### Post by andrew.46 on 2009-06-11
Hi ajgreeny,

Mind you I have been reminded on another thread that vlc does a nice job transcoding such streams and I tried it with no problems with this BBC stream. I attach a couple of screenshots of the relevant sections of the vlc configuration, I am using vlc 1.0 rc3 though so if you are using a repository vlc it might look a little different.

All the best,

Andrew

---

### Post by ajgreeny on 2009-06-12
Hi Andrew.
Thanks for trying to help me out here.  I have just tried vlc (from the repos) which does look a bit different to your version and so far I can't get it to do anything other than produce empty mp3 files, which obviously don't play.  I will keep trying and perhaps get the newer version of vlc to try as well, but it is really a small matter, of little importance, and the reason I was looking for a cli way to do this, was so I can use cron to time recordings when I'm away from the computer as I do with streamripper for mp3 streams.  Now if I could get streamripper to rip a ram stream as suggested by markbuntu, it would be great, but as I said, it just won't apparently do it for ram.

---

### Post by andrew.46 on 2009-06-12
Hi ajgreeny,

> **ajgreeny said:**
> I was looking for a cli way to do this, was so I can use cron to time recordings when I'm away from the computer 

Well this is exactly what I do with the radio broadcast I describe on the page 'For the God who sings'. You are more than welcome to pillage this script which is started from cron and uses a timing mechanism as well. But since it is a rm stream there will be conversion to wav and mp3 at the end no matter what you do.

All the best,

Andrew

---

### Post by ajgreeny on 2009-06-13
Thanks again, Andrew.  What a pity there is no obvious way to do it all in one go and not have to do it in separate actions.  Never mind, at least I can now record BBC Radio without the need to actually be sitting in front of the computer, using cron to run either your script or my original one, both work OK.

---

### Post by linuxlinks on 2009-06-13
get_iplayer is great for downloading BBC radio

---

### Post by ajgreeny on 2009-06-13
Thanks, linuxlinks, I'll download and have a look at that.

---

### Post by BFG on 2009-07-17
> **linuxlinks said:**
> get_iplayer is great for downloading BBC radio

It looks great.  Shame there isn't a gui for it.

I've just downloaded this.  Anyone got any sample command lines?

---

### Post by tubunu on 2010-01-05
[http://linuxcentre.net/getiplayer/documentation](http://linuxcentre.net/getiplayer/documentation)

---

### Post by inet.dysk on 2010-01-05
I use this for ripping:
```

get_iplayer --type=radio --get --pid b00ph6s7 --raw --force --modes=iphone,flashaudio,flashaac,realaudio

mplayer -bandwidth 9999999 -noframedrop -dumpfile file.ra -vc dummy -vo null -dumpstream rtsp://rmv8.bbc.net.uk:554/radio1coyopa/radio_1_-_friday_2100.ra

```
(b00ph6s7 is pid of example radio programme)

---

### Post by ron999 on 2010-01-05
[

---

