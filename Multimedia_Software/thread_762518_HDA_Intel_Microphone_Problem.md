---
title: "HDA Intel Microphone Problem"
date: 2008-04-22
forum: Multimedia Software
---

### Post by brendonbrewer on 2008-04-22
Hi everyone. This is my first post here.

I've got an HP Pavilion DV6614tx laptop, which has the following inbuilt sound card:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

I'm running 32-bit Hardy Heron with all packages up to date and in particular ALSA 1.0.15-3ubuntu4, which I believe is the latest version. Sound playback works fine, but nothing I do seems to fix the microphone. I've tried heaps of Howtos on similar problems that I've found by googling, but none of them worked for me (apparently they worked for others).

When I record in Audacity I get nothing, and in sound recorder, I get the following bizarre results: [http://www.physics.usyd.edu.au/~brewer/whatever.ogg](http://www.physics.usyd.edu.au/~brewer/whatever.ogg)

I've tried running alsamixer to make sure everything is unmuted, and this has no effect. This is frustrating because I only keep my Windows partition for Skype and sound recording, and would free up a lot of space if I could get rid of it.

Thanks for your help.

---

### Post by schander on 2008-07-12
Hey,
I too am having this problem on my hp dv6799ea laptop. Its the only thing stopping me ditching winblows :-( 
I'm running hardy heron 64bit. I really want to us skype, video works great just audio.

Any help you be greatly appreciated.

Cheers
satpal

---

### Post by umuro on 2008-07-14
Same problem. My Indel HDA microphone stopped working after upgrading to hardy. It was perfect in Gutsy.

---

### Post by droundy on 2008-09-05
I thought I was seeing the same problem with my HP Pavilion HDX9494NR, which also has

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

running Hardy Heron 64-bit.

But after a bit more work, I figured out that if I run the program gnome-sound-recorder, and then select "Open Volume Control" from the File menu, I can get things working, if I then go to preferences and set everything visible, then go to the "Recording" tab, and make sure everything is set to recording, and is also unmuted, and has the knobs not set to zero.

Finally, I can set the input source using the "input source" popup menu in the options tab, with "Mic" being the built-in mic, and "Front mic" being the microphone jack on the front of the computer.

I don't know if any of this will help those of you having trouble, but I tried to describe exactly what I did to make the microphone work.

---

### Post by Benzaa on 2008-09-05
I have a similar problem with my laptop.

I have installed different versions of Ubuntu (kubuntu, 8.04, 7.10, 7.04) and none of them have corrected the microphone issue.

I've tried different solutions that I've seen on the web and none work.

I have a Packard Bell EasyNote A8202 and according to lspci | grep audio my sound controller is:

00.1e.2 Multimedia audio controller: Intel corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio controller (rev 04)

I really want to fix this issue to use skype and get rid of windows completely.

Please, HELP!!!!

---

### Post by Seinfeld on 2008-11-10
droundy... 

I do not know how to thank you.:popcorn:. "input source -> Front Mic" YESSS...This is the ONLY way to let the front Mic on my desk top work on Ibex. Both Mics (rear and front) were working flawlessly in Hardy until I upgraded to Ibex yesterday and had to lean forward to let the wire reach the back:).. 
Now solved.. Thank you VERY much.. 
FYI, folks who may have sound problems with Ibex.

There might be a problemm with PulseAudio in Ibex. It solved all my multimedia problems as Mplayer just hates it and does not work. I have an Intel-hda Realtek Alc888. 

Please refer to 
[http://ubuntuforums.org/showthread.php?p=6141506#post6141506](http://ubuntuforums.org/showthread.php?p=6141506#post6141506)


Thanks again..

---

