---
title: "[SOLVED] Cannot install nvidia-glx"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by ceecko on 2007-10-18
Hi guys,

I can see there are several topics about installing nvidia drivers, but none of them work for me :?
I installed fresh 7.10 and can't enable the desktop effects, it's saying I have to enable "NVIDIA accelerated graphics driver", if I enable it says "The software source for the package nvidia-glx is not enabled"...

I tried envy (couldn't install because of dependencies)
I also tried "sudo apt-get install nvidia-glx" which produces "E: Package nvidia-glx ha no installation candidate".

I have GeForce 4200Ti... Any suggestions please? I'd like to get rid of winxp :/

Thank you

---

### Post by pbournho on 2007-10-18
I had the same problem : ubuntu does not find the' nvidia-glx'  package . 
You should add the 'proprietary drivers depot' in the menu defining the synaptic software depots.

---

### Post by ceecko on 2007-10-18
Where do I add it? Is it in Synaptic Package Manager? Didn't find it...

Nevertheless I managed to install nvidia-glx, I had to edit /etc/apt/sources.list and add multiverse, that's why the package was not available.

Finally I can enable the desktop effects, took few restarts but it's working.

Thank you for your answer though!

---

### Post by zerix01 on 2007-10-18
What exactly did you add to the sources.list file?

---

### Post by ceecko on 2007-10-19
I'm using Slovakian mirror:

```
deb [http://ubuntu.ynet.sk/ubuntu/](http://ubuntu.ynet.sk/ubuntu/) gutsy multiverse
deb-src [http://ubuntu.ynet.sk/ubuntu/](http://ubuntu.ynet.sk/ubuntu/) gutsy multiverse
```

---

### Post by scouser84 on 2007-10-19
Sorry I'm abit new at this.. how and where in the .list file do you add it? and how do you save it?

---

### Post by ceecko on 2007-10-19
> **scouser84 said:**
> Sorry I'm abit new at this.. how and where in the .list file do you add it? and how do you save it?

I was using console, but what you can do is:
[LIST]
[*]Open up System > Administration > Software Sources
[*]Check Software restricted by copyright or legal issues (multiverse)
[*]Click close and then reload
[/LIST]

Now you should see nvidia-glx in your Synaptic Package Manager

---

