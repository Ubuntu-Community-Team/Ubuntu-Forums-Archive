---
title: "ffmpeg and audio capturing"
date: 2010-10-02
forum: Multimedia Software
---

### Post by James2k on 2010-10-02
I've been recently testing out the best methods of capturing my desktop for screencast purposes and tried a variety of software packages like XVidCap, gtk-recordmydesktop etc. Now I've been trying out ffmpeg which works great but I was wondering if it was possible audio capture as well.

I've be looking for guides but the official documentation on how to audio capture doesn't seem to work anymore since the changes to how Ubuntu manages sound.

I was wondering if anyone has successfully captured audio with ffmpeg?

Thanks.

---

### Post by ron999 on 2010-10-02
> **James2k said:**
> 

I was wondering if anyone has successfully captured audio with ffmpeg?


Yes
I used this tutorial here:-
[http://ubuntuforums.org/showthread.php?t=1392026]("http://ubuntuforums.org/showthread.php?t=1392026")

---

### Post by James2k on 2010-10-02
Thanks I'll check it out!

**Edit:** I now have sound with my video capturing, thanks a lot!

---

### Post by jeff_phil on 2010-10-03
I have a situation here that might not be that serious. heheh... somehow, when I record my desktop with ffmpeg, my desktop lags a bit. I have a dual core box @ 2.4 GHz and 2GiB of RAM. Is there something that I need to tweak in order to do a smooth desktop recording? My desktop has a resolution of 1680x1050.

---

### Post by FakeOutdoorsman on 2010-10-03
> **jeff_phil said:**
> I have a situation here that might not be that serious. heheh... somehow, when I record my desktop with ffmpeg, my desktop lags a bit. I have a dual core box @ 2.4 GHz and 2GiB of RAM. Is there something that I need to tweak in order to do a smooth desktop recording? My desktop has a resolution of 1680x1050.

Did you follow the instructions in the guide that ron999 linked to?  What is your ffmpeg command?  We can't give suggestions to your command without knowing what you did.  What Ubuntu version are you using?  Are you using FFmpeg from the repository or did you compile it?

Also, [cross-posting](http://ubuntuforums.org/showthread.php?t=1587237) is not recommended on this forum.

---

### Post by jeff_phil on 2010-10-03
Sorry if I cross-post. 

I did what the link suggested me to do. This is the command that I used, just to test the installation:

-for capturing
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv

I am using Ubuntu 10.04.1. I compiled it, just as the link suggested.

---

### Post by jeff_phil on 2010-10-03
Additional info:

I noticed that the frame rate stays at 1fps during recording, even though I forced ffmpeg to use 30 fps.

---

### Post by FakeOutdoorsman on 2010-10-04
That's odd.  Are you running Compiz or other desktop effects?  If yes, try disabling it and see if that helps.  I'm guessing here.

---

