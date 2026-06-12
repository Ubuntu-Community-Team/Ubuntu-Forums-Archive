---
title: "HOW TO: Recording Internal Audio in Ubuntu"
date: 2010-03-28
forum: Multimedia Software
---

### Post by pyros on 2010-03-28
This how-to should show the steps required to record whatever audio is playing on your computer, similar to recording "stereo mix" in windows. This makes recording audio played by any application, including flash videos, possible.

I'm using the Sound Recorder application that comes in standard Ubuntu installations. To set this up using other programs (like audacity) just substitute it in these instructions.

[LIST=1]
[*] Install pavucontrol (PulseAudio Volume Control) using apt-get or the Ubuntu Software Center.
[*] Open PulseAudio Volume Control.  It should be in the applications menu under Sound and Video.
[*] Open Sound Recorder and start recording.  Playing any sound at this point would be helpful, as your level indicator should react once you have finished.
[*] Go to the "Recording" tab in the PulseAudio Volume Control window.
[*] Make sure that "Applications" is selected in the drop down menu on the "Recording" tab.
[*] Choose "Monitor of Internal Audio Analog Atereo" from the "Record Stream *from*" menu in the Sound Recorder entry of the application list.
[/LIST]

This appears to be persistent so that you will only have to do this once, but you will have to repeat these steps to record in another application.

---

### Post by DanielMC on 2010-04-07
You are awesome :o, 

I've been trying to record internal sound with xvidcap all afternoon, finally got it working with this. I wonder why such a useful tool is not included by default :confused:

Thanks a lot!

---

### Post by Malcy on 2010-05-04
Thanks, that's considerably easier to enable than it used to be.

 :guitar:

---

### Post by leeds_shrew on 2010-05-11
Fantastic! Thank you very much - no messing around with Audacity or anything overly complicated. Wickid Innit!

---

### Post by code_linux on 2010-05-29
thank you, very helpful!

---

### Post by acidblue on 2010-06-02
doesn't work for me.
get 'Stream contains no data' when ever I press the record button.

---

### Post by Eskorpio on 2010-06-04
Easier way [here]("http://www.ubuntugeek.com/how-to-recording-internal-audio-in-ubuntu.html") (read first comment)

---

### Post by Rytron on 2010-06-04
Thank you pyros. :popcorn:

---

### Post by randolf_ambrose on 2010-06-08
excellent one!!!

thanks a lot...

:-D

---

### Post by cybrsaylr on 2010-06-08
Excellent!
Thank you pyros.

One question. Sound recorder seems to record mp3s at only 128 bitrate.
How do you record at a higher quality bitrate, say 192 or higher if you want?

---

### Post by kshome on 2010-07-13
thanks a lot .. works like a charm.

---

### Post by pyros on 2010-07-17
> **cybrsaylr said:**
> Excellent!
Thank you pyros.

One question. Sound recorder seems to record mp3s at only 128 bitrate.
How do you record at a higher quality bitrate, say 192 or higher if you want?

I picked Sound Recorder because its a simple app to use as an example. I'd recommend using audacity for more options.

---

### Post by tomika on 2010-07-18
No audio on Skype just video with the internal webcam. Using a Microsoft USB head phone system I can get audio IN but not on Webcam. I know the webcam audio works because my dual boot Win7 works.

---

### Post by blknite on 2011-09-03
very helpful.

Thank you!

---

### Post by rcmistri on 2013-01-04
hi all,

I am also recording this way and really liked its simplicity.
but one day, I found that Audacity was not recording sound card output except mic. Tried and searched a lot but no success. Then I found below link \\:D/

[http://blog.zadco.me/2012/06/21/recording-internal-sound-in-ubuntu-12-04/]("http://blog.zadco.me/2012/06/21/recording-internal-sound-in-ubuntu-12-04/")

It shows some more settings for pavucontrol & ALSA that you accidentally or some application installation might have changed. Copy/bookmark/print do whatever you can to keep it for quick reference if u r not lx-pro.

---

