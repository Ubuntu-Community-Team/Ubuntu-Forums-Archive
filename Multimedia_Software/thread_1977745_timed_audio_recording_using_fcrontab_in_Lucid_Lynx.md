---
title: "timed audio recording using fcrontab in Lucid Lynx"
date: 2012-05-10
forum: Multimedia Software
---

### Post by metso on 2012-05-10
hi,

When I record a sound clip from line input of the computer using command "sudo arecord -d 10 -r 20000 -c 1 -v -v 1.wav", I get a working sample of 10 seconds of recorded audio.

But, when doing the same thing timed with "sudo fcrontab -e" command (fcrontab line: "08 09   *   *   * arecord -d 10 -r 20000 -c 1 -v -v /home/<my_username>/2.wav"), I get a sample of 10 seconds of silent data. Anyone have an idea why this happens?

My guess is that the fcrontab uses different alsamixer settings, probably recording from mic input instead of line in. I have nothing connected to the mic input. How can I adjust mixer settings that the "sudo fcrontab" uses? Apparently it uses different settings than plain sudo arecord command (as with 1.wav file recording).

Please, any ideas?
mikko

---

### Post by ginjabunny on 2012-05-12
I have recently had experience of recording using crontab, took a while to get it working.

The problem with crontab apparently is it runs in some sort of separate user space so even though it maybe running as your userid (as opposed to root) it does not interact with your profile, so to get round this I have to get crontab to use "at" to run my commands, but there is a catch in that you can't get "at" to run commands directly so you point it at a file with the commands in you want to run. 

I start VLC command line from crontab which works until you try and get it to display on the screen and the reason I wanted to do this was because I have a wireless speaker and the dongle needs to be detected and get output from pulse audio which is user profile based, so I figured out how to get my server to start VLC on the display and record and forward on using TCP. So I auto-login the user at boot time and when crontab starts "at" which runs he script then I can see the VLC app on the desktop and the wireless speaker works and it records the stream and I can pick up the forwarded stream on other PCs with VLC player (or another).

So this is how I did it

(I use uuid to create unique filenames, get it from apt)

1) in ~/radio/scripts I created a script called "run_at.sh" which puts the command string pased to it into a file which "at" then uses, this is it 
```

#!/bin/sh
FILEUUID=`uuid`
echo "AT to run: $*"
echo $* >/tmp/at_$FILEUUID
sleep 1
at now +0 minutes -f /tmp/at_$FILEUUID
sleep 1
rm /tmp/at_$FILEUUID

```
2) I created other scripts for what I want to do, for example I called one "live_play_stream_rec.sh", I have to use DISPLAY=:0.0 to get it to display on the desktop, so this may look like this 
```

#!/bin/sh
DISPLAY=:0.0 timeout 1800 vlc --quiet --no-video --no-qt-error-dialogs --live-caching 4000 --sout-keep --sout-file-append --sout "#duplicate{dst=display,dst='transcode{aenc=ffmpeg,acodec=mp3,ab=128,channels=2,samplerate=44100}:duplicate{dst=std{access=file,mux=dummy,dst=PROGFILE.mp3},dst=std{access=http,mux=dummy,dst=192.168.1.1:8080}}'}" PLAYLIST.pls

```
3) in my crontab I put 
```

30 18 * * 1-5 radio/scripts/run_at.sh radio/scripts/live_play_stream_rec.sh

```
so at 18:30 Mon-Fri it starts VLC, with the radio stream in PLAYLIST.pls which I can then pick up around he house on other PCs and my wireless speaker in the bathroom, and it records the stream to PROGFILE.mp3 and quits after 30 minutes.

Hope this helps

GB

Btw I found all the complicated VLC stuff on the VLC wiki

---

### Post by metso on 2012-05-15
Thank you, GB, for your advice.

I tried it by creating a run_at.sh script exactly as yours, and then another one named startRec.sh with only a command "arecord -d 10 -r 20000 -c 1 -v -v /home/mikko/2.wav". To fcrontab I put a line "25 18   *   *   * /home/mikko/scripts/run_at.sh /home/mikko/scripts/startRec.sh". Still, the file 2.wav is all so silent. Did I misunderstand your description?

Best,
mikko

---

### Post by ginjabunny on 2012-05-15
looks ok to me, when I get time I will try it out and report back

---

### Post by ginjabunny on 2012-05-20
I think was I put would only work for pulse reliant programs, but as arecord is alsa based it should work all the time.

I just tried what you did orginally and it works (but I didn't use sudo)

played an mp3 with vlc
used alsamixer to set it so I could hear it, a set mic level to 3
connected line-out to mic with a cable
in terminal ran - arecord -d 10 -t wav -f cd 2.wav
played back 2.wav and can hear it 
connected line-out to mic with a cable
put it in crontab
47 17 * * * arecord -d 10 -t wav -f cd 21.wav
played back 21, wav and can hear it

so seems to work ok for me

btw what is fcrontab? I just used crontab -e

---

### Post by metso on 2012-05-27
GB,

According to your description you used mic input for alsa recording source. I need to use line input. Could you try it with line input, also using sudo? The mic input works for me too, presumably because the alsa settings of "cron user" are set to use mic input. With cron user I mean the mysterious one that is used when the system runs sudo crontab. My sound source outputs line level signals and those cannot be used with mic input.

fcron is an improved version of vixie cron
[http://www.gentoo-wiki.info/Fcron](http://www.gentoo-wiki.info/Fcron)

Regards
mikko

---

### Post by ginjabunny on 2012-05-27
I was doing it on my laptop and don't have line in, mic should work fine

---

### Post by metso on 2012-05-28
Unless anybody has any other suggestions it seems that this will remain a mystery. Bummer, and I definitely don't wanna go back to Windows OS :(

mikko

---

