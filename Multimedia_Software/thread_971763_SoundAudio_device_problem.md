---
title: "Sound/Audio device problem"
date: 2008-11-05
forum: Multimedia Software
---

### Post by arzca on 2008-11-05
Hello

I have a weird problem with my sound device. Randomly some applications like skype, web-browser (firefox) etc. sounds stop working. And while those applications wont play any sounds, I can still play music with a rhytmbox-player. 
When I reboot my PC, all the applications starts to work like they should.

I have tried a several different Ubuntu sound drivers (ALSA, VL....), and the same thing happens with all of them.

Is there a way to "restart" sound device so I don't have to reboot the whole PC. Logout/Login to restart x wont wor either.   

My Sound card is Gainward Hollywood 7.1.

Thank for your help!

-Ari

---

### Post by numanoids on 2008-11-05
I'm not sure what version you're running, however I'm running 8.10 which I upgraded to from 8.04 and I'm having the exact same issue.

Sound just stops - the only way I can get it back is to kll the pulseaudio daemon and restart it:

```
killall -9 pulseaudio
```

Followed by

```
pulseaudio -D
```

However its getting progressively worse 

I'm running on an IBM T61 laptop with the following card:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Thanks

Num

---

### Post by |Porsche on 2008-11-15
I am in the same boat as you, My audio randomly stops working and so far I can only get it to work by rebooting the computer. 
These are the commands I have tried so far...

```
lsof | grep pcm
```

killing those processes.

I also tried...
```
/etc/init.d/alsa-utils restart
```

none of those did the trick.

```
killall -9 pulseaudio
pulseaudio
```

Did the trick!

Thanks!

---

