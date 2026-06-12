---
title: "mp3 to wav conversion with custom sample rate"
date: 2008-08-14
forum: Multimedia Software
---

### Post by TKoorn on 2008-08-14
Hey there,

I have recently started using Ubuntu and am using it mainly to do recordings. Some parts of these recordings come to me in mp3 format. I am using Ardour and since it won't import mp3's directly I have to use a convertor. However my Ardour doesn't want to work with my ac97  soundcard on any other bitrate than 48000. so the wave files have to be in that bitrate, or they are resampled on import. this all takes quite a bit of time so I would like to speed it up by converting to 48000

The convertor I have found doesn't seem to have any option for things like this and I was hoping there is some way of doing this in a batch either in a gui or commandline.

Thanks

Tinus

---

### Post by Rhubarb on 2008-08-14
sox will do all of this for you quite nicely.
First, you need sox:
```
sudo aptitude install sox libsox-fmt-sndfile libsox-fmt-all
```

Then, to convert an mp3 into a nice 48kHz wav file:
```
sox input.mp3 --rate 48000 output.wav dither
```
Where input.mp3 is the mp3 you wish to convert to wav, and output.wav is the resultant wav file that you want.


To make a bash script that converts all your mp3's into wav files, create a text file called "converter.sh", make it executable, and put this into it:
```
for i in *.mp3; do
    sox "$i" --rate 48000 "${i/.mp3/}".wav dither
done
```
Place your mp3s into a directory you wish to convert them all in, then copy the bash script to that directory, open up a terminal, and run it by typing in **./converter.sh**

---

### Post by Ferralll on 2009-10-08
You are super smart! 

Sorry to resurect this pretty old thread, but I got a Sony Walkman, and was trying to put a couple files on there (audio books) and it kept saying that it was the wrong format.  

I think the problem is/was the sample rate, and I search for a long time to figure out how to fix it, and then I saw your post! 
Thankyou soooooo much! 

Also, thankyou for going the extra distance and showing me the bash script to make it all easy and painless!

---

