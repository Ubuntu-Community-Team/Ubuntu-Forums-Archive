---
title: "Mencoder and Arecord problem"
date: 2009-12-14
forum: Multimedia Software
---

### Post by ben0mega on 2009-12-14
So I am trying to record by command line the audio and video from my analog to video card - Pinnacle 800i - and I am using arecord to get the sound (since i cant seem to get mencoder to grab it) and mencoder for the video.  The problem is that if a i record for around 4 minutes (see below) my audio file is 3 minutes 57 seconds while my video is 4 minutes 45 seconds.

I am using the following commands each in a different window

```
sleep $(($(date -d 10:06PM +%s)-$(date +%s)));arecord -D hw:1,0 -f dat foobar.wav ;
```

```
sleep $(($(date -d 10:06PM +%s)-$(date +%s))); mencoder -tv "input=1:immediatemode=0:mjpeg:decimation=1:fps=25:buffersize=756" -ovc copy -vf harddup -idx -noskip -mc 0 -ni -o ofile2.avi -nosound tv://
``` 

These i run in sudo -i
```
sleep $(($(date -d 10:10PM +%s)-$(date +%s)));kill YYYY
```
```
sleep $(($(date -d 10:10PM +%s)-$(date +%s)));kill XXXX
```
Where the XXXX & YYYY represent the process id's of the above processes.

I am using the ```
sleep $(($(date -d 10:10PM +%s)-$(date +%s)));
```
to sync up the times

---

### Post by gordintoronto on 2009-12-15
I think Kino can capture both at the same time.  Maybe Kdenlive as well.

Is there some reason you want to use the command line?

---

### Post by ben0mega on 2009-12-15
I would like to use a gui, but i havent been able to find one that can capture the video and sound correctly, with good time sync.  I could use xawtv for the video, it should up well, but i dont want to manually sync them up, wich is why i am using the command line - it is easier to sync the start time (except that the time recordings are confuzed).  I am unfamiliar with xawtv command line options - it doesnt have the same level of support mencoder does from what I have read.

Anyway, the problem that i run into with most of the video recorder programs is that I cannot get the recording to input 1 instead of input 0 (the input is specified in v4l2, but i am not sure programs fully work well with it).

Also the sound is not detected on any of the video programs i have come across (vlc, xawtv, tvtime, and a few others), it is /dev/dsp1 (versus /dev/dsp or /dev/dsp0 which doesnt exist).  Yeah, my command line sound thing, i think, works so all of those settings can be dissected from that (alsa input = 1).

---

