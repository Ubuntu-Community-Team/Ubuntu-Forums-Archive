---
title: "imon_pad remote with Silverstone case (9.04)"
date: 2009-10-26
forum: Multimedia Software
---

### Post by knowtown on 2009-10-26
I have been working on getting this remote control working with Mythbuntu and with all the help here in these forums I have made some progress but just cannot seem to get over the last few hurdles. Since there are so many threads dealing with this problem and various suggested solutions I suspect I am mixing things up on my end. 

Here some basics on what I have running:
```
$ uname -a
Linux jarmatter-mythtv 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux

lircd -v
lircd 0.8.6

lsusb |grep Sound
Bus 003 Device 003: ID 15c2:0038 SoundGraph Inc. 
```

I am getting output in irw so I know that things are talking at some level. In order to get the output for the touch pad in irw I have to first click the mouse/keyboard button on the remote but after that it works. The track pad works as a mouse correctly when I am not in myth frontend.

When I am in Myth Frontend watching live tv the only buttons that work on the remote are Chn+ and Chn- but it just brings up the OSD for the channels up or down and doesn't actually change the channel. No other buttons seem to work in live tv. If I am watching videos then Volume works, Play, Pause, rew, ffw, but nothing else.

I really want to get a remote working but there is so much conflicting info about should you use a csv lirc install or just the Mythbuntu packages, do you need a patch or not, etc...

So really if someone knows the answer to some basic questions I will keep chasing this tail.

1. What versions of lirc will work with this remote/receiver? Do I need csv? patch? Mythbuntu packages?

2. Would it be easier to get a different remote? Do other remotes work with the SoundGraph 0038 device?

I don't mind trying to work it all out and get things working but it would be nice to know what tools work well with each other. If anyone can shed some light on this that would be great. I would appreciate any help I can get.

Thanks,
James

---

