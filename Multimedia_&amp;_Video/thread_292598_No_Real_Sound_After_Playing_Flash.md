---
title: "No Real Sound After Playing Flash"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by jackn on 2006-11-04
Remark: Problem solved. see post #4.

After I play a Flash video on Firefox, my system won't play a RealPlay audio segment. It pops up the 'sound device is used by another application' message.


I emphasize that I have no problems with either Flash or RealPlayer audio on their own. All posts I have studied on this topic deal with Flash not working in general, which is not my case. It's rather about losing Real audio after playing Flash.

I believe this has to do with OSS (the former sound standard, Open Sound System), as the above popup message is associated with it in other posts, and oss is known to have trouble once one app has used it. It is reminiscent of trouble with Skype which also uses OSS.

My default startup is to disable the gnome-volume-manager, as has been suggested in some posts.


Each time it happens, I have to restart.

I'm sure there's something cleverer to do, but what?...

Thanks, 
Jackn

---

### Post by richardward101 on 2006-11-27
try this: [http://planet-geek.com/archives/003048.html]("http://planet-geek.com/archives/003048.html")
Its for debian rather than ubuntu so you'll have to put some "sudo"s in there, but that should make everything firefox uses use alsa instead of oss. Hopefully.

---

### Post by jackn on 2007-01-07
Thanks a lot, Richard.

I'm sorry for answering late. Took a long while to get around to it.

I only meant to thank you, but it turns out it still doesn't work.

I've done what your post suggested, both the also-oss install, and the editing to set up 'aoss' as a wrapper for the Firefox sound module.

There is an improvement: I don't get the popup about the sound device being taken, but I don't get any  sound either.

Real and Flash work a treat, but Real has no sound if I first play a Flash segment...

---

### Post by jackn on 2007-04-08
The solution is to be found in the [Ubuntu Edgy guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28RealPlayer_10.29"):


 > To avoid issues with sound
Make sure you have ALSA OSS driver. 

```
sudo aptitude install alsa-oss
```

then edit the startup script (/usr/lib/realplay-10.0.8/realplay) and changed line 73 from

```
$REALPLAYBIN “$@”
```

to

```
aoss $REALPLAYBIN “$@”
```


Have fun, 
Jackn

---

