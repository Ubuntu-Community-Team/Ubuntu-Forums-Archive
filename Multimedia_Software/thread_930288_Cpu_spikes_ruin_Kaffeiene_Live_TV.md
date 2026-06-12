---
title: "Cpu spikes ruin Kaffeiene Live TV"
date: 2008-09-25
forum: Multimedia Software
---

### Post by Patto77 on 2008-09-25
When watching Live TV with Kaffeine 0.8.6, the video periodically goes haywire (glitches, jerky)while the audio remains smooth.  More often than not I have to change the channel and then change it back to regain normal playback.

Watching the system monitor on a second screen, I have noticed that whenever the network sends/receives the cpu usage spikes which interferes with the Live Tv playback.  When watching a SD channel, the average usage over both cores is about 30-35%.  When watching HD channels the average usage is between 60-80%. Add the network usgae and the usage on both cores spikes to 100% and there goes the video playback.  HD channels suffer much worse than the SD ones.

Does anybody know how I can fix this? I'm not even sure what the network is sending/receiving. It's small whatever it is.  It's becoming very frustrating.  TV playback is smooth as silk under VMC.

I'm using 8.04 in a gnome session.  I have the same issue under a KDE session as well.

Any ideas???

---

### Post by Patto77 on 2008-09-26
It would appear that it's not just kaffeine that is affected.  Both VLC and Totem suffer jerky playback when the CPU spikes.

What has got me a little perplexed is that I have no issues watching a video file over the network apart from the periodical CPU spikes.

I'm still lost as to how to find the culprit.

---

### Post by laceration on 2008-09-26
I don't know how Kaffeiene works.  If it encodes the stream before it outputs it, that would be putting a burden on your system.  I use mplayer, with a channels.conf file in your ~/.mplayer folder you just
```
$  mplayer dvb://
```
hd is a massively large amount of info to process, you do need some horsepower.  I have an amd 64 dual core 4400 and a nvidia 8500 graphics card and my cores run at about a 30% ave when watching hd.  You should shut down any processes or programs that are using up system resources while watching tv.  Sometimes glitches are simply caused by bad reception too.  Maybe upgrading some of your hardware is your solution.  A good video card will process what is done by the cpu with a weaker onboard adapter.

---

### Post by Patto77 on 2008-09-26
It looks like the culprit was actually the Firefox add-on Fast Dial.  It appears that the tiles were set up to automatically refresh every ten minutes which caused the periodical CPU spikes.  Shutting down Firefox seemed to do the trick. Live TV and .avi became smooth after that.


I only stuck with kaffeine because it was the first player to work with my DVB card.  I think it's time to give mplayer a go.

Thanks for the help.

---

### Post by laceration on 2008-09-27
Here's some cool mplayer tricks for you:

```
$ mplayer dvb://stationname -dumpstream -dumpfile filename
```

then in another terminal
```
$ mplayer filename
```
and you have a simple dvr!  You can pause, skip over ads, etc.  

A q from the keyboard will quit the player, a ctrl+c in the 1st terminal will stop the recording.  Be careful if you fall asleep watching hd, you can wake the next morning with 50 gb on your harddrive!  In another terminal you can
```
$ sleep 2h;killall mplayer
```
and it will all shut down in 2 hours.

I've written some script that does with a remote control and mplayer's menuing system--A little more work and I plan to share it.

---

### Post by Patto77 on 2008-09-27
I started playing with mplayer yesterday and initial results are promising. PQ looks better than using Kaffeine.  Unfortunately I'm not getting sound on my HD channels and one or two channels are a little shy of smooth, but it's a start.   


Thanks for the tips mate :)

---

