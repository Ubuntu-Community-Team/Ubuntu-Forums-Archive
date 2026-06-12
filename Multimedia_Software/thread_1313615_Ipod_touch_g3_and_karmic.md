---
title: "Ipod touch g3 and karmic"
date: 2009-11-03
forum: Multimedia Software
---

### Post by goodrench on 2009-11-03
I have just purchased an ipod touch 3rd gen and I have jailbroken it but I can't get it to play nicely with gtkpod or any other program.

I have installed ifuse from the ppa and I have installed ipod-convenience. The ipod will mount over the wireless but I get an error every time I open gtkpod.

```

Extended info will not be used.
Ipod Import Database failed: Illegal seek to offset 0 (length 4)in file '/media/ipod/IPod_Control/iTunes/iTunesDB'

Newly mounted iPod at /media/ipod could not be loaded into gtkpod.
```

Has anyone been able to get the new ipod touches working properly yet?

---

### Post by ndefontenay on 2009-11-03
I got a touch ipod. I tried to make it work with Jaunty before and it failed. I gave up after that. I tried a normal ipod this week end and it was working amazingly well with rythmbox.

If there's anything new on the ipod side of linux, I've got to try it tonight.Maybe the touch ipod finally works.

Will keep you posted.

Nico

---

### Post by brian183 on 2009-11-08
I'm also having this issue with my iphone 3G which I've jail-broken.  My guess is the 3.1.2 firmware and whatever nonsense the latest itunes does to sync music to the iphone is a step ahead of libgpod4 (which I think is the latest in karmic).  I'm going to attempt to build a svn of gtkpod and see if that works but I'm not hopeful.

I'm so glad I didn't buy this phone (or pay for the service) and I would never have bought it as I am running all linux and I despise itunes.  It'd be real nice if I could sync without having to use itunes in vbox though.

If I don't make another reply within the next day assume the svn failed.

---

### Post by pshotton on 2009-11-21
Same problem with me. I have an iPhone 3GS. It worked fine with Rythmbox until I jailbroke it; that's put the latest firmware on it and now I get the same "Illegal seek to offset 0 (length 4) in file /media/ipod/iPod_Control/iTunes/iTunesDB". I'm desperate to get this sorted so I can junk my Windows box.

---

### Post by umby24 on 2009-11-21
well, I would like to know how you even got gtkpod to reconize there was an ipod plugged in, and I can tell you why you have that issue, that would be because in the newer firmware ipod-touches, the mount point is

/var/mobile/Media

rather than /mobile/Media

---

### Post by goodrench on 2009-11-21
Since my first post I have removed the jailbreak from my ipod-touch and I am now using usbmuxd with ifuse.
I followed the instructions here

[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/)

It has been working great with gtkpod and there is no need to jailbreak. Transfer speeds are slower than using the wireless mount but I like using usbmuxd. 
It seems to work good and I don't get the errors I was previously getting with ipod-convenience.

---

