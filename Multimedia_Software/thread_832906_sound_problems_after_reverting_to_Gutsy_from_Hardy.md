---
title: "sound problems after reverting to Gutsy from Hardy"
date: 2008-06-18
forum: Multimedia Software
---

### Post by ubukool on 2008-06-18
Hi everyone,

I was wondering if you could help me with a problem.  Just to give you some background to this, I recently decided to upgrade from Gutsy to Hardy.  I backed up my Gusty with partimage and upgraded.  After the upgrade I was having horrible sound problems (my soundcard is an Intel ALC883) so I decided to revert to Gutsy by rewriting my / partition from the image that I had.  I rebooted and everything seemed to be as it was....except now I was having sound problems!

Zattoo sound doesn't work at all (it did before the upgrade and revert).  Sometimes sound stops in Flash and often, for no apparent reason, my Amarok won't play and it says "Audio output unavailable; the device is busy. xine parameters: "

Arrrrrgh!

I've tried recompiling ALSA using module assistant but I've still got problems, so can anyone help?  Why should there be sound problems when I completely reverted to the system I had where there were no problems?  It's a linux mystery!  Thanks for your help.

Ubukool

---

### Post by ubukool on 2008-06-20
Hi everyone,

I've managed to find a  fix/work around it for anyone who might be in the same situation.  Firstly, the problem seems to exist only in Totem.  I've played videos in SMplayer and VLC and they work fine.  I'm not sure why Totem doesn't work but I'm simply not using it.

About Zattoo, I deleted my .zattoo folder in my home directory and now sound works fine!  If you have a similar problem you can try this.

There was another problem too.  I had a file in my home directory
called asound that had this content:

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

My understanding is that this was put there by Hardy and it sets pulseaudio as the default.  Of course when you revert to Gutsy, there is no pulseaudio....ummmm....not surprisingly this is going to cause problems! Deleting the file has helped to fix things.

Since I deleted asound and deleted the .zattoo folder, I haven't had any more problems with xine in Amarok.  I'm using SMplayer now as my default media player.  The only thing that's slightly bugging me is why there is no sound in Totem when it used to work okay...oh well, there have to be some mysteries in life!  I haven't marked this thread as solved because, although from a practical point of view everything is working again, Totem doesn't work normally.

If you've got sound problems you might find this article useful:

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

If you have similar problems, I hope this helps! :)

---

### Post by borobudur on 2008-06-29
I think Zattoo does some own configuration with the sound. When you reinstall or install an other sound package, it seems that you loose your sound in Zattoo completely. 

Have you tried reinstalling Zattoo?

---

