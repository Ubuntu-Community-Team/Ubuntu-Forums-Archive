---
title: "Question: new 12.04 install, which Nvidia driver..."
date: 2012-09-26
forum: Multimedia Software
---

### Post by mfm3 on 2012-09-26
Howdy y'all,
Pretty long time user, but sadly I've been away from Ubuntu for awhile (since 10.04). Finally got a chance to get my Dell Vostro 3400 dual booting, very excited about all the new features of 12.04 (64 bit).

At this point I am fully functional. Had some issues with the Windows 7 partition, blah blah worked through it and now everything is booting fine.

However, this machine has one of the 'hybrid' graphics cards (Nvidia 310m), with Optimus technology. So by default there is no 3d acceleration, can't resize the launcer, etc. I've been digging around and it seems (of course) there are ways to get all this working. 

Normally I would just dig in and start trying things, but it looks like there are two different methods and I wanted to ask here FIRST instead of breaking the driver and having a blank screen like I used to do while banging my head against the nvidia wall. (Please keep in mind that I have been out of the game for awhile.) 

Method 1: So it looks like one way to get an nvidia driver working is with Bumblebee:
[http://www.bumblebee-project.org/](http://www.bumblebee-project.org/)
[https://wiki.ubuntu.com/Bumblebee#Installation](https://wiki.ubuntu.com/Bumblebee#Installation)
Never heard of this project, normally would shy away from a third party program but it seems pretty straight-forward and targeted to my problem. And its in the Ubuntu official wiki so that is somewhat re-assuring.

Method 2: The other way seems a bit more like what I'm used to doing, although I guess that doesn't necessarily mean it is any better:
[http://askubuntu.com/questions/132275/why-arent-3d-effects-working](http://askubuntu.com/questions/132275/why-arent-3d-effects-working)
Same instructions as this guy, who has the same laptop as me so I am sort of inclined to try this second method: [http://xlives.wordpress.com/2012/08/22/enabling-3d-effects-with-nvidia-310m-on-ubuntu-12-04/](http://xlives.wordpress.com/2012/08/22/enabling-3d-effects-with-nvidia-310m-on-ubuntu-12-04/)


And there are other suggested fixes too, like just installing the newest nvidia driver the "normal" way....but I think Ubuntu would have done that on it's own with the 'additional drivers'(formerly restricted drivers?) deal if that were going to work. Maybe not.

So can anyone advise me on which method to attempt in order to get 3D acceleration going? Any help or just thoughts would be much appreciated.

Thanks in advance,
Frank

---

### Post by mfm3 on 2012-12-08
Bump, still trying to get this sorted out.... any help would me most appreciated!

---

### Post by 2F4U on 2012-12-08
Bumblebee is a project that requires nVidia Optimus technology. Such laptops have two graphics cards, a discrete nVidia card and an integrated Intel card. If you don't have such a laptop, there is no benefit in using Bumblebee.

---

### Post by mfm3 on 2012-12-08
Thanks for your reply. I do have Optimus technology, the 310m, as stated in OP. Kinda wishing I didn't have it.

Today I went for it and used method 2, which essentially removes all nvidia drivers completely. 3D effects are now working, cool, but still no out to external display via HDMI. Still stuck using windows to watch stuff on the TV.

Installed Bumblebee. Works I think as it should - enables me to open an application using the nvidia drivers. But as stated here: [https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ](https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ) there is no HDMI support.

Anyone running an external display via HDMI with an Optimus card?

Thanks again

---

