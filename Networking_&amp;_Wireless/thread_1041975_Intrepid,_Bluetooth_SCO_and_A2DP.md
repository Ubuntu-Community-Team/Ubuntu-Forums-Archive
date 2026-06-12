---
title: "Intrepid, Bluetooth SCO and A2DP"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by vavatl on 2009-01-17
Ok, this is the last issue with Linux I have to solve before moving from Windows completely - how do you switch from A2DP profile to SCO and back without restarting bluetooth stack?

I have Plantronics 590E headset, it supports both A2DP and mono profile.
I can use it with Skype, I can use it to listen to music but I can't answer a Skype call in the middle listening. More over, if I want to use Skype, I have to do ```
sudo /etc/init.d/bluetooth restart
``` And even that doesn't always work.
My .asoundrc file
```
pcm.bm {
    type bluetooth
    device 00:19:7F:47:7C:77
    profile "voice"
}
pcm.bs {
    type bluetooth
    device 00:19:7F:47:7C:77
    profile "hifi"
}

```

I can use bs to play nice stereo music with awesome quality and bm to chat with friends. 'profile "auto"' doesn't work really, it just using A2DP all the time (that's why so many people can't make it work with Skype by the way)

So is there a way to switch between them automatically as in Windows or at least with some command sequence that won't freeze Skype nor music player?

---

