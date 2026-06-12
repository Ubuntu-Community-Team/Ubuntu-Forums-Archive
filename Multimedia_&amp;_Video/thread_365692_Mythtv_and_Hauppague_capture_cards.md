---
title: "Mythtv and Hauppague capture cards"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by wesmsl on 2007-02-19
I am in the process of buying and putting together a computer to record the tv shows I watch.  I am wondering if anyone has set up a mythtv box with a hauppague capture card.  Which card would you suggest me getting?  I would like a remote and my mind is set on the hauppague wintv pvr 150 with remote because of the low cost.  Would anyone recommend one of the more expensive cards?

---

### Post by ickyfeet on 2007-02-20
Personally, I would steer clear of the PVR 150 card.  I purchased the PVR 150 and returned it within a week because I simply could not get the remote control to work.  I must admit I'm not a Linux expert; however, I couldn't even get assistance from the forums as to how to get the remote control to function.  I do not have a suggestion as to what type of card to get but I would definitely think hard about the headache you're probably going to go through trying to get the remote to work.  That's my two cents . . .

---

### Post by williammanda on 2007-02-20
I have the Wintv pvr-150 card and it functions well along with my pchdtv-5500 and fusion hdtv5 rt gold cards. I don't use the remote as I am planning on using another.
Thanks

---

### Post by barney_1 on 2007-02-20
I have an older Hauppauge card that is basically the same as a PVR-250.  I'm very happy with it.  It didn't come with a remote so I an using a serial IR receiver via lirc.  I have a universal remote for my home theater system that works perfectly with it.

---

### Post by toorima on 2007-02-20
I have the Hauppauge PVR 150 (non MCE) with remote in my mythtv box and the remote works perfect, card also has great picture quality, highly recommend it

---

### Post by BikerGeek on 2007-02-20
HOW did y'all get the 150 to work?! I have tried EVERYthing!

I have a Radeon 9500 Pro and the 150 in a Dell Dimension 8100. Followed all available guides that I could find...multiple times. I tried open source ati, I tried the fglrx driver, everything! I EVEN tried OTHER distros. Same effect. I could capture just fine, but no way under the sun could I get it to let me watch the TV, wouldn't even access the tuner so I could scan for channels.

I gave up and just stuck the old bt-based WintTV GO back in and everything works fine with the open source ati driver, not so much with the fg binary.

SO, I'm guessing either the ivtv drivers didn't install correctly, although all the various checks indicated that they had, or the ivtv drivers just don't like the Radeon 9500. Especially since I had the same result with different distros.

Any thoughts towards a solution that uses the 150 would be greatly appreciated as I know I'm gonna miss the hardware encoding. I'm not opposed to buying a different video card although the only two worth puchasing seem to come with problems no matter what.<g>

NEVER thought I'd say it but...why can't linux be more like Windows?! Heheheheheheheh.

---

### Post by ickyb0d on 2007-02-20
i recently purchased the [pvr-500 MCE]("http://hauppage.com/pages/products/data_pvr500mcekit.html") from hauppage and have had little to no problems with it.  Just slapped it in, installed the [ivtv ]("https://help.ubuntu.com/community/Install_IVTV_Edgy?highlight=%28ivtv%29")drivers and everything worked fine.  

Essentially the 500 is 2 pvr-150's on one card (2 tuners!).  Apparently hauppage switched to samsung tuners and some people have complained about those.  I ordered my card directly from hauppage and haven't had any of the "samsung tuner" problems even though i have the samsung tuners on there.  I assume getting the 150 wouldn't be any harder than the pvr-500, so long as you just install the correct ivtv drivers (it's kernel dependent... so every time you upgrade the kernel... you need to update your ivtv drivers.)

---

### Post by majoridiot on 2007-02-22
i run a pvr-150mce... the card on a backend edgy box, the remote and lirc on a frontend edgy box.
both installed without incident and work flawlesly using these excellent guides:

for the pvr-150:
[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

for the remote:
[https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

i have no need for a better card, as it works great, and i use firewire with y cable box for a second
tuner.  if you have need/want to watch one channel while recording another, you might consider
a dual-tuner card, or dual pvr-150s (they're cheap enough...)

just **triple** check that whatever you settled on is supported by ivtv or other linux drivers.

---

### Post by superm1 on 2007-02-26
> **BikerGeek said:**
> HOW did y'all get the 150 to work?! I have tried EVERYthing!

I have a Radeon 9500 Pro and the 150 in a Dell Dimension 8100. Followed all available guides that I could find...multiple times. I tried open source ati, I tried the fglrx driver, everything! I EVEN tried OTHER distros. Same effect. I could capture just fine, but no way under the sun could I get it to let me watch the TV, wouldn't even access the tuner so I could scan for channels.

I gave up and just stuck the old bt-based WintTV GO back in and everything works fine with the open source ati driver, not so much with the fg binary.

SO, I'm guessing either the ivtv drivers didn't install correctly, although all the various checks indicated that they had, or the ivtv drivers just don't like the Radeon 9500. Especially since I had the same result with different distros.

Any thoughts towards a solution that uses the 150 would be greatly appreciated as I know I'm gonna miss the hardware encoding. I'm not opposed to buying a different video card although the only two worth puchasing seem to come with problems no matter what.<g>

NEVER thought I'd say it but...why can't linux be more like Windows?! Heheheheheheheh.
As major idiot pointed out, the pvr-150 should be straightforward to have set up per the above guides.  

Can you post what the output of 
```
dmesg | tac | sed -n '/=\ \ END INIT IVTV\ \ =/,/= START INIT IVTV =/p;/= START INIT IVTV =/q' | tac
```

Is for us to see what the error is when loading the driver?

---

