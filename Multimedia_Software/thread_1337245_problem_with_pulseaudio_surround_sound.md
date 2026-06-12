---
title: "problem with pulseaudio surround sound"
date: 2009-11-25
forum: Multimedia Software
---

### Post by PureRumble on 2009-11-25
Hello. I've got a problem with the soundserver pulseaudio in ubuntu. The server doesn't get it that my speaker setting is 5.1, and insists that it is 7.1 (if only it had been so...).

This becomes evident when I run speaker-test -c 6. Rear speakers say nothing. However if I do speaker-test -c 8 then I get some noise from the rear speakers, although that noise is half of what I get from the other speakers and -c 8 is actually for 7.1.

In pavucontrol I have chosen a 5.1 setting.

Any help? Movies without surround kinda sucks :-/

---

### Post by Shazaam on 2009-11-25
What does your /etc/pulse/daemon.conf show on this line?...
```
default-sample-channels = 5
```
Mine is set to 5 (4.1 surround) as you can see. Try putting a 6 there. Oh, and the ";" is a comment in this file just like a "#". Remove the ";" to un-comment (enable) it. You will have to edit the file as root...
```
gksudo gedit /etc/pulse/daemon.conf
```

---

