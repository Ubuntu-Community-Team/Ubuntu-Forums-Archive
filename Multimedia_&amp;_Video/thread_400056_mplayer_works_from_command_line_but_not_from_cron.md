---
title: "mplayer works from command line but not from cron"
date: 2007-04-03
forum: Multimedia &amp; Video
---

### Post by bananabob on 2007-04-03
The Background
I am trying to record a real player stream. The stream is not live, just a 30 minute recording. I set this up to be done once a week after the new recording is made available on the website. To do this I have written a script which I call from cron at the appropriate time.

The Problem.
Sometimes, and not everytime, when cron runs the script mplayer aborts about 30 seconds after it starts.  I get the following messages 

> 
No bind found for key 'W'.                         
No bind found for key 'B'.                         
No bind found for key 'B'.                         
No bind found for key 'C'.                         
No bind found for key ':'.                         
No bind found for key 'c'.                         
No bind found for key 'c'.                         
No bind found for key 'c'.                         
No bind found for key '_'.                         
No bind found for key 'G'.                         
No bind found for key 'C'.      


These messages vary each time. In other words they are not the same each time mplayer fails.
I have read somewhere that when these messages are issued, there may be something wrong with the stream.


I have changed the call to mplayer so that it now runs with -v option, and here is the output from that

> 
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


[file] File size is 39 bytes
STREAM: [file] /tmp/Im_Sorry_I_Havent_a_Clue.txt
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
Parsing playlist file /tmp/Im_Sorry_I_Havent_a_Clue.txt...
Trying asx...
Trying Winamp playlist...
Trying extended m3u playlist...
Trying reference-ini playlist...
Trying smil playlist...
Trying plaintext playlist...
Playlist successfully parsed
get_path('codecs.conf') -> '/home/bananabob/.mplayer/codecs.conf'
Reading /home/bananabob/.mplayer/codecs.conf: Can't open '/home/bananabob/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' '-novideo' '-quiet' '-nortc' '-nojoystick' '-prefer-ipv4' '-nolirc' '-playlist' '/tmp/Im_Sorry_I_Havent_a_Clue.txt' '-ao' 'pcm:file=/home/audio/download/Im_Sorry_I_Havent_a_Clue.wav' '-vc' 'null' '-vo' 'null'
init_freetype
get_path('font/font.desc') -> '/home/bananabob/.mplayer/font/font.desc'
font: can't open file: /home/bananabob/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Using nanosleep() timing
get_path('input.conf') -> '/home/bananabob/.mplayer/input.conf'
Parsing input config file /home/bananabob/.mplayer/input.conf
Input config file /home/bananabob/.mplayer/input.conf parsed: 60 binds
get_path('1230_mon.ra.conf') -> '/home/bananabob/.mplayer/1230_mon.ra.conf'

Playing rtsp://rmv8.bbc.net.uk/bbc7/1230_mon.ra.
get_path('sub/') -> '/home/bananabob/.mplayer/sub/'
STREAM_RTSP, URL: rtsp://rmv8.bbc.net.uk/bbc7/1230_mon.ra
Filename for url is now rtsp://rmv8.bbc.net.uk/bbc7/1230_mon.ra
Filename for url is now rtsp://rmv8.bbc.net.uk/bbc7/1230_mon.ra
Resolving rmv8.bbc.net.uk for AF_INET...
Connecting to server rmv8.bbc.net.uk[212.58.240.195]: 554...
Cache size set to 640 KBytes
STREAM: [realrtsp] rtsp://rmv8.bbc.net.uk/bbc7/1230_mon.ra
STREAM: Description: RealNetworks rtsp streaming
STREAM: Author: Roberto Togni, xine team
STREAM: Comment: ported from xine
CACHE_PRE_INIT: 0 [0] 0  pre:131072  eof:0  

Cache fill:  0.00% (0 bytes)   

<repeats several time>


Cache fill:  0.00% (0 bytes)   
vo: x11 uninit called but X11 not inited..

Exiting... (End of file)



I assume that mplayer works for this stream when issued from the command line because X11 is, of course, running.


The Question

How can I fix this so that it will run from cron?

---

### Post by souki on 2007-04-03
if your x11 session  is running :

- set the cron to run as your uid

- export the DISPLAY
DISPLAY=:0.0 /your/command

---

### Post by bananabob on 2007-04-03
Well thank you, that appears to work.

---

### Post by bananabob on 2007-04-04
I am glad I said appears to work.
On the next stream it does not. what happens is the following
> 
No bind found for key 'B'.                         
No bind found for key 'B'.                         
No bind found for key 'C'.                         
No bind found for key ':'.                         
No bind found for key 'c'.                         
No bind found for key 'c'.                         
No bind found for key '_'.                         
No bind found for key '_'.                         
No bind found for key 'J'.                         
No bind found for key 'B'.              


> 
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


[file] File size is 39 bytes
STREAM: [file] /tmp/The_Goons.txt
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
Parsing playlist file /tmp/The_Goons.txt...
Trying asx...
Trying Winamp playlist...
Trying extended m3u playlist...
Trying reference-ini playlist...
Trying smil playlist...
Trying plaintext playlist...
Playlist successfully parsed
get_path('codecs.conf') -> '/home/bananabob/.mplayer/codecs.conf'
Reading /home/bananabob/.mplayer/codecs.conf: Can't open '/home/bananabob/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' '-quiet' '-nortc' '-nojoystick' '-prefer-ipv4' '-nolirc' '-playlist' '/tmp/The_Goons.txt' '-ao' 'pcm:file=/home/audio/download/The_Goons.wav' '-vc' 'null' '-vo' 'null'
init_freetype
get_path('font/font.desc') -> '/home/bananabob/.mplayer/font/font.desc'
font: can't open file: /home/bananabob/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Using nanosleep() timing
get_path('input.conf') -> '/home/bananabob/.mplayer/input.conf'
Parsing input config file /home/bananabob/.mplayer/input.conf
Input config file /home/bananabob/.mplayer/input.conf parsed: 60 binds
get_path('0800_mon.ra.conf') -> '/home/bananabob/.mplayer/0800_mon.ra.conf'

Playing rtsp://rmv8.bbc.net.uk/bbc7/0800_mon.ra.
get_path('sub/') -> '/home/bananabob/.mplayer/sub/'
STREAM_RTSP, URL: rtsp://rmv8.bbc.net.uk/bbc7/0800_mon.ra
Filename for url is now rtsp://rmv8.bbc.net.uk/bbc7/0800_mon.ra
Filename for url is now rtsp://rmv8.bbc.net.uk/bbc7/0800_mon.ra
Resolving rmv8.bbc.net.uk for AF_INET...
Connecting to server rmv8.bbc.net.uk[212.58.240.197]: 554...
Cache size set to 640 KBytes
STREAM: [realrtsp] rtsp://rmv8.bbc.net.uk/bbc7/0800_mon.ra
STREAM: Description: RealNetworks rtsp streaming
STREAM: Author: Roberto Togni, xine team
STREAM: Comment: ported from xine
CACHE_PRE_INIT: 0 [0] 0  pre:131072  eof:0  

Cache fill:  0.00% (0 bytes)   
Cache fill:  0.00% (0 bytes)   
Cache fill:  0.00% (0 bytes)   
Cache fill:  0.00% (0 bytes)   
vo: x11 uninit called but X11 not inited..

Exiting... (End of file)



and all in about 5 seconds of starting.

---

### Post by goatboy78 on 2007-06-16
Cron has something of the night about it.

I had a similar problem recently. In desperation I installed fcron, with the intention of using it instead of cron. However, when synaptic retrieved it, it also pulled down a load of other support files.

So, I tried cron one last time and hey presto, it worked. Those support files for fcron must have given cron the kick in the stones that it needed.

Give it a whirl, you never know.

---

### Post by Gwasanaethau on 2007-06-16
> No bind found for key 'B'.
No bind found for key 'B'.
No bind found for key 'C'.
No bind found for key ':'.
No bind found for key 'c'.
No bind found for key 'c'.
No bind found for key '_'.
No bind found for key '_'.
No bind found for key 'J'.
No bind found for key 'B'. 

I get something like this when I run mplayer from the command line the first time after booting. It won't accept any commands from the keyboard (including ctrl-c), and I usually have to kill it from a second terminal. Each subsequent running of mplayer works perfectly, though. Seems very odd - anyone know what might be causing that too?

---

### Post by bananabob on 2007-06-16
I fixed the problem when running in cron using the option 
> -noconsolecontrols

---

### Post by bananabob on 2007-06-16
@Gwasanaethau
I believe that these messages are caused by an incorect header in the stream. BUT don't quote me on that!
Using the BBC are you?

---

### Post by Gwasanaethau on 2007-06-17
> **bananabob said:**
> @Gwasanaethau
I believe that these messages are caused by an incorect header in the stream. BUT don't quote me on that!
Using the BBC are you?

Ahh, I see.
No mine seem to appear when I try to press a button on the keyboard. For example, when I press 'q' to stop playing a video, it comes up with something like that. In fact - I'll paste the actual message:
```
No bind found for key 'JOY_AXIS2_MINUS'.-q
```
I get '-c' if I try pressing ctrl-c, '-]' after trying to speed up the video, etc.

This only started happening since upgrading to Feisty, and only happens the first time after booting.

P.S. What's this about the BBC? :-s

---

