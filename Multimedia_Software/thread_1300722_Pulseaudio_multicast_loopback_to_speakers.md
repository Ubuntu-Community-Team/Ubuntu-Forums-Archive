---
title: "Pulseaudio multicast loopback to speakers"
date: 2009-10-25
forum: Multimedia Software
---

### Post by 00arthuryu on 2009-10-25
Hello
I am using Karmic 9.10 and have been trying to get pulseaudio multicast loopback to work. If I send the audio to the multicast sink and tell it to loopback the sound will be fine for about 5 seconds after which it will start to speed up/down and change to a high/low pitch and eventually will become inaudible with huge stuttering.

However the 8.10 machine on the other end of the multicast will play the stream perfectly whilst the local machine stutters. I think this is an issue to do with receiving multicast streams. (This was also true for Jaunty therefore I did not upgrade).

I know this is a very niche problem but I surely cannot be the only one having this problem? :P
This problem was true for all the computers I've tried.
Anyone experienced the same?

Thanks!

---

### Post by 00arthuryu on 2009-10-27
bump? :(

---

### Post by markbuntu on 2009-10-28
This is a problem between pulseaudio and the kernel scheduler among other things.

There are some pulseaudio updates sheduled for the Karmic release. If these do not fix your problem please file a bug report at launchpad against pulseaudio. If you stop all your sound applications and kill pulseaudio and then start it again with

pulseaudio -vvvv

and restart your apps and your multicast and enable the loopback. You will see what is going on which is probably pulseaudio freaking out with resetting the buffer due to underruns/overruns and/or resampling.

I have a similar problem with the Simultaneous Output which freaks out if I try to use it for more than two of my 5 devices.

---

### Post by 00arthuryu on 2009-12-01
hasn't been fixed :(
will see about filing a report :)

---

### Post by eigenein on 2010-04-21
Also experiencing the same problem. Was any solution found?

---

### Post by manky_mank on 2010-04-21
I also have experienced this problem.  This is the only place I've found that mentions it, but I have the exact same symptoms with both server and client running karmic (pitch and speed of sound starts changing, then the frequency gets so high that it starts stuttering because it plays the section of sound too fast).

If a bug has been filed, would anybody be able to direct me to it?

---

### Post by eigenein on 2010-04-24
I've found this bug reported nowhere, so i've submitted this bug to launchpad: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/569378](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/569378)

---

### Post by eigenein on 2010-04-25
Installing the version from ppa:ubuntu-audio-dev for Karmic on the receiver side have fixed the problem.
**EDIT: **The problem was not fixed but now it takes more time to appear.

---

### Post by davidwillis on 2010-04-30
try this from a console:

pactl load-module module-loopback 


To turn it off:

first find the module number 

it gives it to you when you run the first command, or use this to find it:

pacmd list-modules

then to unload it use this with your module number:

pactl unload-module 27 


for more info see: [http://pulseaudio.org/wiki/Modules#module-loopback](http://pulseaudio.org/wiki/Modules#module-loopback)

---

### Post by i22yb on 2010-05-01
In addition to what DavidWillis said...

To fix the problem permanently, you need to load the modules when Pulseaudio starts. To do this, you need to add a line to the /etc/pulse/default.pa file with the following commands:

sudo gedit /etc/pulse/default.pa

Scroll down to the bottom of the file and add this line:

load-module module-loopback

Now the modules will load automatically and your line-in audio will always be available.

---------------------------------------------
Thanks go to Hacksaw Labs who's site I found the above info on after about 2 hours of Google searches!

Original Link:
[http://www.hacksawlabs.com/index.php?option=com_content&view=article&id=87:fix-line-in-audio-in-ubuntu-910-karmic-koala&catid=36:system-administration&Itemid=53](http://www.hacksawlabs.com/index.php?option=com_content&view=article&id=87:fix-line-in-audio-in-ubuntu-910-karmic-koala&catid=36:system-administration&Itemid=53)

---

### Post by davidwillis on 2010-05-01
Thanks i22yb, that is very nice but for me I don't want to have the loop-back on all the time.  The only time I want it on is when I am making a video recording where I want my voice and sounds from the computer recorded.

It would be nice if there was a box to check in pulseaudio, or something.  But for now at least it works.  If you want it on all the time then adding that line is great, and if you only want it on occasionally (like me) then you have to do it manually from the command line.  Unless I am missing something.

Even better would be if I could go to my recoding in volume control and select more than one source to record from.  The only options I have to record from are the internal analog stereo (the sound from my mic) and the monitor of internal audio analog stereo (the sound to my speakers).  So in order to record both I have to use the analog loop-back to put my mic out my speakers and record it.  However I would love to be able to record both streams without hearing myself (a half second delayed) and still be able to hear the normal sounds out my speakers.

Is there anything that is the reverse from the analog loop-back, meaning it will send my speaker sounds and mix it with the mic, instead of sending it all out the speakers.

---

### Post by davidwillis on 2010-05-03
Maybe someone more knowledgeable than myself can figure this out.  I have been trying to figure this out, but I am lost.  I did find this someplace, but it doesn't go into much detail.

> I have recorded the output of an application using pulseaudio - first, load-module module-null-sink for the application (creates a null sink or output). You can add a number with different names using the sink_name= option. If you want to simultaneously listen to the output and record, you can load-module module-combine slaves= and list the sinks you want to connect. You can send the audio stream to the combined virtual sink and record from the null sink.


It sounds like we could just make a null sink, and somehow send sound from both mic and applications.  Then record from that virtual sink.

But I can't figure out how to do it.

---

### Post by davidwillis on 2010-05-05
I got it!!!!    

This is how I did it.  First I created a null-sink, name it whatever you want..I named mine steam by accident, so that is what I am using...

> pactl load-module module-null-sink sink_name=steam

Then to get sound to it just use the loop-back (which just sends an input to a sink)

> pactl pactl load-module module-loopback  sink=steam

I did that twice, because I wanted two inputs.

Now go and look at volume control.  First go to Recording, and select show "all streams"  you should have two loopback to nulll output from.  One I selected "internal audio analog stereo", and the other I selected "Monitor of internal Audio analog stereo".   I had to turn the null output down from output devices, because I got a lot of noise when it was on 100%.

Now I just start RMD and monitor of null output, and I am recoding the mic and the speaker sounds and don't hear it!!!

 ;D

---

### Post by 00arthuryu on 2010-05-05
> **davidwillis said:**
> try this from a console:

pactl load-module module-loopback 

Still the same problem, it would still speed up and slow down the stream and raise/lower the pitch respectively and after 30seconds or so it becomes inaudible with stuttering

Here are some duplicates of the same problem:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/384028](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/384028)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/405360](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/405360)

---

### Post by davidwillis on 2010-05-05
Strange... I was trying do use the pulseAudio Preferences, and went to multicast and checke enable multicast/rpt receiver and enable multicast/RTP sender then marked send audio from local microphone and the loop back audio to local speakers.

But when I used that it would speed up, and slow down, crackle, etc.  The longer it was on the worse it got.

But then when I used the pactl load-module module-loopback, from a console I had perfecly clear sound with no speeding up or slowing down.  I am no expert, so I don't know why it is happening.

If you are trying to record from your speakers, and mic, try what I just mentioned.  Maybe creating a null sink to record from will help.

But other than that, I don't know, I just know what I did and what finally worked.

---

### Post by davidwillis on 2010-05-06
I just made a short video.  It shows how I set up recordmydesktop, and pulse to record both sounds.  

[http://www.youtube.com/watch?v=oJADNOY615Y](http://www.youtube.com/watch?v=oJADNOY615Y)

---

