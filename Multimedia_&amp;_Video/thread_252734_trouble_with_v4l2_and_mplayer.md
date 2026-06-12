---
title: "trouble with v4l2 and mplayer"
date: 2006-09-07
forum: Multimedia &amp; Video
---

### Post by El_Matthews on 2006-09-07
Gents,


I am trying to build a PVR with freevo and I got stuck on the configuration of mplayer.

when I try to watch tv via mplayer with command 
mplayer tv:// -tv driver=v4l:width=320:height=240 everything works fine. I got sound and video. This works if I tuned on a channel first with tvtime or an other tv app.

Now when I try to do the same this with :
mplayer tv:// -tv driver=[COLOR="Red"]v4l2[/COLOR]:width=320:height=240
I get the image but no sound.

After searching through the ussual support channels I tried to unmute my sound with :
v4lctl volume mute off
Now I got the sound of the TV even without having a tv app open, help ?

Once this works I would like to be able to capture this sound with mencoder where I have the same problem, but here even if I unmute the sound it is still not recorded.

Who can help me troubleshoot this problem or help me on the right path ?

I am using ubuntu dapper drake 6.06 with all latest updates.
the mplayer version = 2:0.99+1.0pre7try2+cvs20060117-ubuntu8

---

### Post by El_Matthews on 2006-09-18
Gents

Is this so difficult that nobody replies ? I can't imagine that nobody from all those big linux specialists available on this forum can give me a tip to solve this.

Please help me ](*,)

---

### Post by stacktracer on 2006-10-01
I'm having the same problem. (Actually worse, since v4l distorts the video for me.) Here's the best I've been able to find so far:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2006-January/057899.html]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2006-January/057899.html")

> It appears that sound recording doesn't work with Linux 2.6.15 and V4L2. It used to work with 2.6.14...

The post is from 8+ months ago, but matches my experience.

---

### Post by stacktracer on 2006-10-01
Here's a better one:

[http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2006-February/040587.html]("http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2006-February/040587.html")

> A change was made in 2.6.15-rc5 to the bttv driver.  audioset, part of the returned v4l2_input struct defaults to zero now.

...

The problem is mplayer depends on the audioset value to test for audio capabilities.



The post includes a (very) simple patch. It looks like this patch was not included in the Dapper package.

I will try the patch and let you know how it turns out.

---

### Post by stacktracer on 2006-10-01
So I began building the mplayer package ... and found that it's a big pain. It takes lots and lots of dev packages to compile mplayer with all the various codecs and capabilities. Bleh.

A better option, at least for me, is to use the mplayer package from Edgy (which does include the magic "audioset" patch).

I don't know how hard it is to install the Edgy package on a Dapper system ... but even if it means upgrading my whole system, I'll probably just do that. (I'd be upgrading in a few weeks anyway, right?)

---

### Post by El_Matthews on 2006-10-02
Hello stacktracer,

Thank you for the reply. I already tried installing mplayer from the edgy repository but it didn't solve my problem.  

If you want to test it, just update your sourcelist with the edgy repository, remove and reinstall mplayer.

Let me know if it solved your problem.

I think my next step will be to try with the binaries from debian unstable.

---

### Post by El_Matthews on 2006-10-31
Gents

Just for further reference, if you also upgrade the package mencoder to the edgy version everything will work. My fault was that I only upgraded mplayer to edgy and that didn't solve the problem but upgrading mencoder does.

let me know If you need help on how to upgrade those packages.

---

### Post by El_Matthews on 2006-10-31
How can I close this thread ?

---

