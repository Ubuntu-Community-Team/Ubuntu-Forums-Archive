---
title: "How can I capture internet radio streams with VLC?"
date: 2009-08-20
forum: Multimedia Software
---

### Post by NinjaNumberNine on 2009-08-20
Hi, everyone. I have tried to get this working for several hours (I know, that's not much, but I am doing this for [FONT=Arial][SIZE=4]the[/SIZE][/FONT] [SIZE=5]BOSS[/SIZE] and [FONT=Arial][SIZE=4]the[/SIZE][/FONT] [SIZE=5]BOSS[/SIZE][SIZE=1] [/SIZE] wants me to finish[SIZE=2][/SIZE] before I can stop work and play video games all afternoon:guitar:
Nonetheless, my ultimate goal (besides that of playing videogames for a standalone session of at least a week) :biggrin: is to capture _[this stream]("http://gateway.andohs.net/player/default_noax.aspx?nid=2920&sid=9098&customlogo=&shownav=&showfav=&showtuner=&nometa=")_. The actual stream filename is this: [http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf](http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf)
Can someone try and help me get this working? I waited till I got a migraine (unfortunately) and decided it was time to get on my knees and beg... :mrgreen:

  Anyway, Thanks in advance!


            NinjaNumberNine

---

### Post by tgalati4 on 2009-08-20
Well streamripper doesn't know how to handle a flash stream.

But a cheezy way to do it:

Play the stream in a browser:

[http://69.28.146.226/citadelcc_KARN_FM?MSWMExt=.asf](http://69.28.146.226/citadelcc_KARN_FM?MSWMExt=.asf)

Open your sound control panel.  Unmute and bring up the capture channel under the record tab.

Open a terminal.  

arecord -l

This will list recording devices you have available.

arecord karnfm.wav

This will record what is being played on the browser.

Control-C in the terminal window to quit.

Use sox or lame to convert to mp3 as wave files are large.

There may be better ways to do this.

---

### Post by -=hazard=- on 2009-08-20
If you want just to capture it, a easy way you can do it is by opening the link with Movie Player from Movie > Open Location or just Ctrl+L , past the link and click Open then to capture it, record the sound with the default Sound Recorder that Ubuntu allready have on Applications > Sounds & Video

This is really a easy way and I'm sure it will work.

Cheers.

---

### Post by NinjaNumberNine on 2009-08-20
How do you record just movie player though? I run a capture card too so the sound would conflict.

---

### Post by -=hazard=- on 2009-08-20
Sound recorder will capture only the sound, If you want to capture only sound of course...

---

### Post by NinjaNumberNine on 2009-08-20
I still don't understand.  I know soundrecorder just records the sound, but what do I set it to record to get ONLY the radio stream? :confused:

---

### Post by -=hazard=- on 2009-08-21
> **NinjaNumberNine said:**
> I still don't understand.  I know soundrecorder just records the sound, but what do I set it to record to get ONLY the radio stream? :confused:

To record with Sound Recorder, a music player (whatever you want) must be playing (whatever radio you want).

Adjust the volume and do some tests before you start record your favourite music.

Let me know.

---

### Post by NinjaNumberNine on 2009-08-21
What I mean is, can I record just the output sound of, say, mplayer if it is playing.
Thanks for replies!

---

### Post by andrew.46 on 2009-08-22
Hi Ninja,

> **NinjaNumberNine said:**
> What I mean is, can I record just the output sound of, say, mplayer if it is playing.

I am not sure if this is exactly what you are after but the following captures this stream:

```

mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile recording.asf

```

Hope this helps?

Andrew

---

### Post by -=hazard=- on 2009-08-22
I agree with andrew. That is the terminal way. The same thing do Sound Recorder.

Ps: Don' tell me you haven't even try?

---

### Post by NinjaNumberNine on 2009-08-22
This happened:
```
$ mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile recording.asf
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.53GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Creating config file: /home/ninja/.mplayer/config
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf.
Resolving citadelcc-karn-fm.wm.llnwd.net for AF_INET6...
Couldn't resolve name for AF_INET6: citadelcc-karn-fm.wm.llnwd.net
Resolving citadelcc-karn-fm.wm.llnwd.net for AF_INET...
Connecting to server citadelcc-karn-fm.wm.llnwd.net[68.142.121.73]: 80...
STREAM_ASF, URL: http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf
Resolving citadelcc-karn-fm.wm.llnwd.net for AF_INET6...
Couldn't resolve name for AF_INET6: citadelcc-karn-fm.wm.llnwd.net
Resolving citadelcc-karn-fm.wm.llnwd.net for AF_INET...
Connecting to server citadelcc-karn-fm.wm.llnwd.net[68.142.121.72]: 80...
Resolving citadelcc-karn-fm.wm.llnwd.net for AF_INET6...
Couldn't resolve name for AF_INET6: citadelcc-karn-fm.wm.llnwd.net
Resolving citadelcc-karn-fm.wm.llnwd.net for AF_INET...
Connecting to server citadelcc-karn-fm.wm.llnwd.net[68.142.121.72]: 80...
Cache size set to 80 KBytes
Stream not seekable!
```
Thanks for the help though, Andrew and -=hazard=- ! :)
Does the stream need to be playing in mplayer? :confused:
Or can I do it through Totem? :confused:
And what do you mean I can do the same thing it in Sound Recorder? :confused:
TY, NinjaNumberNine

---

### Post by andrew.46 on 2009-08-23
Hi NinjaNumberNine,

Are you sure that the file was not produced in the directory that you opened your terminal in?

Andrew

---

### Post by -=hazard=- on 2009-08-23
Ok ninja here it is.
If you do the andrew way you can just capture the stream without listening to that stream, so you are free to listen to something else (but you can listen it if you want). So, create a folder on your home folder, example name it captured_stream or whatever you want, then open terminal and type

```
$ cd captured_stream
$ mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile recording.asf
```

Eve if your output on terminal finish like this...

```
Connecting to server citadelcc-karn-fm.wm.llnwd.net[68.142.121.72]: 80...
Cache size set to 80 KBytes
Stream not seekable!
```

... dont worry, just go on the new folder you created, in our case captured_stream, and you will see that a file called recording.asf has been created and its getting bigger because you are recording.

From the other side you can do the exact thing with Sound Recorder. While you are listening whatever sound you want, [COLOR="Green"]with whatever player you want[/COLOR], sound recorder will capture it, its just that it have a GUI and it ask you where to save the file after you press the stop button.

I have done 3 screen-shots, the first one is with sound recorder while capturing your radio while I'm listening to it with MPlayer. The second and the third screen-shots shows while capturing from terminal without listening that stream (while you capture from terminal, in the same time you can listen with MPlayer or another program, whatever other music you want without making changes to the sound you are capturing from terminal)

I hope this helps!

---

### Post by NinjaNumberNine on 2009-08-23
> Are you sure that the file was not produced in the directory that you opened your terminal in?Oh, I had not checked that. It did make the file, but it saved it as a .asf file (you cant rewind or fast forward and it says that it is streaming media) and it sounds about like the Peanuts' teacher.:lolflag:

---

### Post by NinjaNumberNine on 2009-08-23
> From the other side you can do the exact thing with Sound Recorder. While you are listening whatever sound you want, [COLOR=Green]with whatever player you want[/COLOR], sound recorder will capture it, its just that it have a GUI and it ask you where to save the file after you press the stop button. You have said this already. I still don't understand if I can record just mplayer if tvtime is playing audio too!! Can you tell me no or yes? :)

---

### Post by -=hazard=- on 2009-08-23
> **NinjaNumberNine said:**
> You have said this already. I still don't understand if I can record just mplayer if tvtime is playing audio too!! Can you tell me no or yes? :)

OMG m8, I allready explained in the above post the 2 ways, I even did the screenshots for the both ways. I repeat that the first way with sound recorder, you will record the sound that you are listening to. [COLOR="Red"]With the second way, from terminal, you can record a stream and in the same time watch or listen to something else with another media player program.[/COLOR] Is it so difficult to understand and to try out before you ask?

---

### Post by NinjaNumberNine on 2009-08-23
> Is it so difficult to understand and to try out before you ask?     -Sorry, I seem to have a bad habit called "frusteration." :roll: (yes I guess it is generally caused by me) 
> I repeat that the first way with sound recorder, you will record the sound that you are listening to.I understand that now (I think) :mrgreen: but it is not what I want, since "I"  (i.e. "My Boss") need to run the tv too. I was hoping you could record the stream quietly in the background using Sound Recorder.   
> [COLOR=Red]With the second way, from terminal, you can record a stream and in the same time watch or listen to something else with another media player program.[/COLOR]
Okay, that works, but like I said, the audio sounds very garbled. 

Is there, nonetheless, a simple way to write the mplayer script as an executable file with a graphical shortcut on the desktop?  :confused:

Anyway, thanks for all the help (and the patience, I know I'm a headache) :lolflag:

---

### Post by NinjaNumberNine on 2009-08-23
Okay, problem solved as far as garbled sound goes. It turned out that my sterio headphones were warping the sound somehow- the speakers play it fine.  Now, if I can make the script, I will declare myself satisfied.
[SIZE=3][COLOR=Blue]I luv ubuntuforums![/COLOR][/SIZE]

---

### Post by -=hazard=- on 2009-08-23
I'm glad you resolved.

---

### Post by NinjaNumberNine on 2009-08-23
BTW, I got the script made, but now I can't find out how to stop it and my hard drive is filling up! Help! :)
(Yes, really)

Heres the script text: ```
#! /bin/bash
mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile recording.asf


```-It seems that I have created a supervirus...

Maybe I will make it available for download.:lolflag:
This runs totally in the background, but that is a little scary. How can I make a command to terminate it?

I had to use System Monitor, and that's a little exstream for capturing a stream.

---

### Post by -=hazard=- on 2009-08-23
> **NinjaNumberNine said:**
> BTW, I got the script made, but now I can't find out how to stop it and my hard drive is filling up! Help! :)
(Yes, really)

Heres the script text: ```
#! /bin/bash
mplayer 'http://citadelcc-karn-fm.wm.llnwd.net/citadelcc_KARN_FM?MSWMExt=.asf' -dumpstream -dumpfile recording.asf


```-It seems that I have created a supervirus...

Maybe I will make it available for download.:lolflag:

$ killall mplayer

?

Or you can restart PC :D

---

### Post by NinjaNumberNine on 2009-08-23
> Or you can restart PC :grin:
Haha, good one. :)

---

### Post by NinjaNumberNine on 2009-08-23
BTW I added onto the "help, I can't terminate" post.

Problem is, I don't (i.e. my boss don't ) want to have to run the terminal command everytime.

---

### Post by -=hazard=- on 2009-08-23
> **NinjaNumberNine said:**
> BTW I added onto the "help, I can't terminate" post.

Problem is, I don't (i.e. my boss don't ) want to have to run the terminal command everytime.

Well after you have started capturing with the script you created and you want to stop it with another script than create another script

!#/bin/bash

killall mplayer

---

### Post by NinjaNumberNine on 2009-08-23
Didn't think of that. That was the first script I ever made. Thanks! :)

---

### Post by -=hazard=- on 2009-08-24
> **NinjaNumberNine said:**
> Didn't think of that. That was the first script I ever made. Thanks! :)

You welcome. 

Here it is a very nice [[COLOR="Red"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=217328&page=2") for begginer and simple scripts, a little old but very useful.

Cheers.

---

### Post by NinjaNumberNine on 2009-08-24
Cheers in return- I just read that thread yesterday. :lolflag:

---

### Post by andrew.46 on 2009-08-25
Hi hazard,

> **-=hazard=- said:**
> Well after you have started capturing with the script you created and you want to stop it with another script than create another script

#!/bin/bash

killall mplayer

I have dealt with this problem before by running MPlayer as a background process, running sleep for a set time and then killing the last backgrounded process (MPlayer). Something like the following:

```

#!/bin/bash
mplayer ***[COLOR="Red"]<stream>[/COLOR]*** &
sleep 2h
kill $!

```

It is a clever idea that I wish I had actually come up with myself :-).

Andrew

---

### Post by -=hazard=- on 2009-08-25
```
#!/bin/bash
mplayer <stream> &
sleep 2h
kill $!
```
For sure that is a way better like this if you want to capture a certain period of time :)

---

### Post by NinjaNumberNine on 2009-08-25
Thanks for the idea! :)

---

