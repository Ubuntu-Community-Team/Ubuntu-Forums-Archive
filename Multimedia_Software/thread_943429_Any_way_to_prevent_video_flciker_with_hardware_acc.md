---
title: "Any way to prevent video flciker with hardware acceleration enabled?"
date: 2008-10-10
forum: Multimedia Software
---

### Post by r2rX on 2008-10-10
Greetz guys.

I've just recently started using Linux and i've found Ubuntu to be quite stable.

Although, I (as well as many others) have encountered a small issue when trying to play video files.

If I set Ubuntu's Visual Effects to Normal or Extra (and/or use Compiz Fusion), playing videos start flickering and only clears up once the video is loaded full screen....when Windowed, the video flickers.

From some research (and personal testing) it seems that the only solution that "works" is disabling video hardware acceleration (xV).

So far, it's either have Visual effects set to None with proper hardware accelerated video, or have the Visual Effects on Normal or Extra and disable hardware acceleration for videos.

Is there no way to have both the Visual Effects set to Extra and have the hardware acceleration working without videos flickering? I'm using an ATi 4870 with ATi's Catalyst 8.9 proprietary drivers.

(Also, i've noticed that Ubuntu 'locks' "Restricted drivers" . Do I have to allow them in order to get full functionality of the ATi drivers?)

I'd appreciate the feedback. ;)

r2rX  :)

---

### Post by Jeanpaul145 on 2008-10-13
Now, I've just ordered a new pc (with some very nice specs, might I add), along with a shiny new HD4870. I haven't gotten it yet, but if your problem hasn't been resolved by the time I have my hardware, I'll try and find a fix (assuming I can reproduce the problem here, that is).

---

### Post by markbuntu on 2008-10-13
You can use the option TexturedVideo "off" to get rid of flickering windows when running compiz, or you can turn compiz effects off, either way the windows will stop flickering. This is not really a solution but a workaround like the one nvidia and the other gpu manufacturers use. Dri2 will fix this permanently and is coming very soon.

aticonfig --help

is your friend, use it.

---

### Post by r2rX on 2008-10-16
Thanks very much for the reply....i'll be looking out for Dri2 (B.T.W, the Compiz Website indicated that their latest version no longer has any flickering...not confirmed this, though).

B.T.W, i've gone through the aticonfig --help but didn't quite notice any entries concerning TexturedVideo'...could you point it out for me please?

But thanks for the responses so far.

r2rX  :)

---

### Post by markbuntu on 2008-10-16
> **r2rX said:**
> ...(B.T.W, the Compiz Website indicated that their latest version no longer has any flickering...not confirmed this, though).

B.T.W, i've gone through the aticonfig --help but didn't quite notice any entries concerning TexturedVideo'...could you point it out for me please?

But thanks for the responses so far.

r2rX  :)

For a long time now ati has been insisting that the flickering problem was due to faulty compiz code and compiz was denying it. It seems that progress is now being made from both sides which is a good thing.

For some cards, TexturedVideo is not an option in the newest drivers.

---

### Post by r2rX on 2008-10-17
Huh....well. After posting last, i'd google'd the TexturedVideo option for ATi, and there's an entry I must save into the *xorg.conf*...so i'm gonna give it a go. Hopefully, it'll solve the flickering and maintain the video hardware acceleration.

Thanks for the input, markbuntu.

r2rX  :)

---

### Post by kpkeerthi on 2008-10-17
Enable Video Playback plugin in Compiz Config Settings Manager to fix this issue.

Edit: linky!
[http://wiki.compiz-fusion.org/Plugins/Video](http://wiki.compiz-fusion.org/Plugins/Video)

---

### Post by Kougaiji on 2008-10-17
> **kpkeerthi said:**
> Enable Video Playback plugin in Compiz Config Settings Manager to fix this issue.

Edit: linky!
[http://wiki.compiz-fusion.org/Plugins/Video](http://wiki.compiz-fusion.org/Plugins/Video)

Sorry, I can confirm I have the same problem [with compiz on] but this mode has always been enabled and the problem persists.

HARDWARE: 64bit Dual-core Inspiron 1501 with Radeon Xpress.

---

### Post by kpkeerthi on 2008-10-17
Sorry about that. Video playback is smooth and buttery with my nvidia 7800 GTX + nvidia binary driver + Compiz Video Playback plugin.

---

### Post by r2rX on 2008-10-18
Hmm....well, i'm gonna install the latest version of Compiz and hope that it'll work. Otherwise, i'm going to have to take a look into the plugin you mentioned, kpkeerthi.

Great input so far.

r2rX  :)

---

