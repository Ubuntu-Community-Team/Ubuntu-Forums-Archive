---
title: "Lost all sound trying to fix popping noise"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by marriedman on 2007-12-07
This may be a little long winded, but I do not want to leave anything out. This all started when I wanted to rip a DVD. No matter what I tried, I could not get Hairspray (hey, it’s for the wife) to play as a DVD much less rip it. If I went to the disc and opened a VOB file it would play, but no menu’s would appear. I read a bunch of how-to’s and installed everything that all of the tutorials said to install to enable this. After 3 hours of fooling around with this thing I had the brilliant idea to try another recent DVD (transformers for me) and that one worked fine. Soit all turned out to be that particular DVD that was the problem.

So I washed my hands of the Hairspray debacle and wanted to listen to some Gov’t Mule to chill out. Every time the track changed, it sounded like a record needle being laid down on a records or bicked up. I opened up the mixer and started fooling around with the volume levels of all the channels. On the center channel and master volume slider, when they are moved it made the same sound only repeated as long as I kept moving it. So I went and removed the packages that I installed. No I have no sound at all.

So, with all that back story, I crawled around the forums here and the only thing close that I could find was this thread: [http://ubuntuforums.org/showthread.php?t=276497](http://ubuntuforums.org/showthread.php?t=276497)

And it  is not that close. But I think his solution would work for me. How do I reinstall everything related to the sound output and audio playback? After that, what should I put back onto my computer? Can gstreamer and xine play together? Thank you for any tips or pointers.

---

### Post by marriedman on 2007-12-08
Well, I got system sound back, but I still have popping everywhere and now I don't have sound on any websites.

Does this make sense to anyone?

---

### Post by Yellow Pasque on 2007-12-08
What kind of sound card do you have?
```
sudo update-pciids
lspci | grep "Audio"
```

---

### Post by marriedman on 2007-12-08
Looks like I was wrong, I do not have system sound back. I only have sound in Totem Movie Player. Nothing else.

My soundcard is:
paul@enterprise:~$ lspci | grep "Audio"
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

It is not a high def sound card thank goodness. I have read they are difficult to get working. I had everything working fine the other day. I don't know why it is doing this now. The popping sound happens whenever there is any activity. Logging on sounds like a needle being dragged across a record. :confused:

Thanks for the reply BTW.

---

### Post by marriedman on 2007-12-08
Well, I said screw it and just started over. Everything works now just fine. Since my /home is on a different partition I didn't even break a sweat reinstalling the OS.

God I love Linux for that.:guitar:

---

