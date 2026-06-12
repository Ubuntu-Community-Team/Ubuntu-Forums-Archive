---
title: "Perfect picture @tvtimeand bad on myhtbuntu"
date: 2010-05-07
forum: Mythbuntu
---

### Post by ALiP-61 on 2010-05-07
Hey guys,

I just setup a "test" box to ensure that my TV Card is working, and yes it does.

But :

The Picture weren´t so good that´s why I tested the same Setup with tvtime with the result that I get a perfect Picture with it. 

Is there something like "tuning" "tweaking" or else ?


Greets & Thanks

System :

Sempron 2600+
1GB Ram
TV Card with saa7134 @ Analog
Nvidia 6600 @ VGA Port

---

### Post by tgm4883 on 2010-05-09
In the frontend settings, there are recording options. You probably need to bump up the resolution and bitrate. Unfortunately, I don't know what the difference in picture looks like. You should post screenshots.

---

### Post by ALiP-61 on 2010-05-13
Okay, let me formulate this in a other way, i don't get any picture @ mythbuntu ...

The card and the tuner are working correctly under tv time.

Greets

---

### Post by tgm4883 on 2010-05-13
Then it may be beneficial to get some backend logs when you attempt to watch TV

---

### Post by ALiP-61 on 2010-05-13
Okay, seems that the LOG grabber isn't working so I just uploaded logs and images to my ftp.

[http://cmp-systems.de/myth/tvtime1.png](http://cmp-systems.de/myth/tvtime1.png)
[http://cmp-systems.de/myth/tvtime2.png](http://cmp-systems.de/myth/tvtime2.png)
[http://cmp-systems.de/myth/tvtime3.png](http://cmp-systems.de/myth/tvtime3.png)


Logs:

[http://cmp-systems.de/myth/mythbackend.log](http://cmp-systems.de/myth/mythbackend.log)
[http://cmp-systems.de/myth/mythfrontend.log](http://cmp-systems.de/myth/mythfrontend.log)


A little more tuner Infos:

Typhoon 2000 @ saa7134 tuner 
set to : saa7134 card=3 tuner=59

Mythbuntu  shows a picture now, but it's very very broken, I can't even decrpyt which channel is it

Greets

---

### Post by tgm4883 on 2010-05-13
> **ALiP-61 said:**
> Okay, seems that the LOG grabber isn't working so I just uploaded logs and images to my ftp.

[http://cmp-systems.de/myth/tvtime1.png](http://cmp-systems.de/myth/tvtime1.png)
[http://cmp-systems.de/myth/tvtime2.png](http://cmp-systems.de/myth/tvtime2.png)
[http://cmp-systems.de/myth/tvtime3.png](http://cmp-systems.de/myth/tvtime3.png)


Logs:

[http://cmp-systems.de/myth/mythbackend.log](http://cmp-systems.de/myth/mythbackend.log)
[http://cmp-systems.de/myth/mythfrontend.log](http://cmp-systems.de/myth/mythfrontend.log)


A little more tuner Infos:

Typhoon 2000 @ saa7134 tuner 
set to : saa7134 card=3 tuner=59

Mythbuntu  shows a picture now, but it's very very broken, I can't even decrpyt which channel is it

Greets

Regarding the Log Grabber not working. [http://mythbuntu.org/node/341](http://mythbuntu.org/node/341)



Not sure what broken picture means, can you post a screenshot? I looked through the logs, and saw this error

```
2010-05-13 20:21:22.621 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2010-05-13 20:21:22.629 NVR(/dev/video0) Error: Unknown audio codec
```

Can you check you are using the correct codec for your card?

---

