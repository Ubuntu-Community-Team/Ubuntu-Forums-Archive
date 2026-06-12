---
title: "VLC not playing video after updating to 9.10 Karmic"
date: 2009-10-30
forum: Multimedia Software
---

### Post by wewantutopia on 2009-10-30
Most of the update went fine.  VLC is giving me issues.  I try to play a avi file and I get sound but no video.

I also get this error:

No suitable decoder module:
VLC does not support the audio or video format "mp4v".  Unfortunately there is no way for you to fix this.

Of course this worked fine pre-update. 

Any ideas?

---

### Post by informer2000 on 2009-10-30
In my case it crashes the whole thing and I get back to the login screen! Karmic is really unstable and slow.. Why was it ever released now?!

---

### Post by promet on 2009-10-30
Other than VLC, Karmic is working fine for me so far, very brisk, and I think the most problem free Ubuntu upgrade so far, by far.

After the upgrade though, VLC is having problems playing AVI video. Stops and starts as if the AVI were, corrupted. On the upside, these same AVI files play as smooth as you please in the default Movie Player. 

Maybe some of the changes to the codec packages in the Karma upgrade? I'd like to try and figure out what the issue is here though; cuz VLC is my "woobie"...


;)

---

### Post by promet on 2009-10-30
Try checking your Video Output module in your VLC Preferences. MIne was set to "Default", I changed it to Xvideo, and it seems to have cleared up my AVI problems, give it a once-over.

Also, check this thread, from which I got the idea to check:

[http://ubuntuforums.org/showthread.php?t=1305629]("http://ubuntuforums.org/showthread.php?t=1305629")

---

### Post by wewantutopia on 2009-10-31
I have tried playing videos with all the different video output options and still no dice.  My vlc version is 1.0.2 Golden eye.  I have the ppa setup in my repositories with the correct Karmic version.  I have tried complete removal of all packages relating to vlc and then reinstalling via synaptic and no go.  Anyone else having this problem and having success?

---

### Post by promet on 2009-10-31
Also, I've had some issues with playing video (especially full-screen) with the compiz composited screen active. You may also want to try deactivating compiz effects (I do this through "System -> Preferences -> Appearance -> Visual Effects -> None") and see if that helps while you're watching video; then just flip it back to eye-candy mode when you're not watching video.

If this works you may also want to check out Fusion-Icon in order to abbreviate this task.

```
$ sudo apt-get fusion-icon
```

Or however you usually go about adding your packages...

Hope this is of some help...

Cheers!
Also, Happy Halloween (Samhain)  :twisted:

---

### Post by wewantutopia on 2009-10-31
have it, tried it.  didn't fix it.  The issue is stated in the error:  No suitable decoder module.  One of the best things about VLC all these years is that it pretty much plays anything without having to download codecs.  Now with this Karmic update it's broken?  Quite odd.

---

### Post by MuckMuck on 2009-11-01
i had the same problem. this is what i did

open synaptic package manager type in-> libavcodec52 <-install it

---

### Post by wewantutopia on 2009-11-01
open synaptic package manager type in-> libavcodec52 <-install it


THANK YOU MuckMuck.... worked perfectly!!!!

---

### Post by DustofDust on 2009-11-03
[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

has always up to date packages of vlc.

---

### Post by crysys on 2009-11-09
> **DustofDust said:**
> [https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

has always up to date packages of vlc.

I was using this PPA and still getting no love from VLC.


> **MuckMuck said:**
> i had the same problem. this is what i did

open synaptic package manager type in-> libavcodec52 <-install it

This however, solved the problem.  You rock sir!

---

### Post by ITA003 on 2009-11-09
> **wewantutopia said:**
> open synaptic package manager type in-> libavcodec52 <-install it


THANK YOU MuckMuck.... worked perfectly!!!!

Nice!! Works for me (same problem with Totem)!:D

---

### Post by leonard.pistol on 2009-11-13
Thank you. It worked like a glove. 

As an advice: pay attention at the libraries that are being removed when you update to Karmic. You might want to get them back.

---

### Post by Nemo_bis on 2009-11-27
I did have that library, so this didn't work, but [this]("http://ubuntuforums.org/showpost.php?p=8281817&postcount=18") did the trick.

---

### Post by mynevdull on 2011-04-20
Thought I'm on Debian Squeeze, not Ubuntu per se, I did find that removed vnc references in /usr/local/lib/ and reinstalling fixed my video problems.

Of course, it did re-break my audio issues, but one thing at a time, eh?

---

### Post by beew on 2011-04-20
> **mynevdull said:**
> Thought I'm on Debian Squeeze, not Ubuntu per se, I did find that removed vnc references in /usr/local/lib/ and reinstalling fixed my video problems.

Of course, it did re-break my audio issues, but one thing at a time, eh?

You do realize that this is a 2 year old thread, right? Karmic will reach end of life in two weeks and OP was talking about upgrading to karmic.:confused:

---

