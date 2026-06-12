---
title: "Releif on the horizon: analog video capture cards"
date: 2011-01-29
forum: Multimedia Software
---

### Post by Patrick M. on 2011-01-29
Reading the various forums and community help blogs it is apparent to me I am not alone. there are others like me. People with analog video. We wait, hope and suffer. Hiding in shame on windows or mac while our digital Linux neighbors sail into cyberspace. Our hours of analog footage, created long before anyone invented the internet sit idle, degrading over time as magnetic media does. 

No more. I have been testing out the SVN (development) version of LiVEs, with good result. the are a few things about it that are slightly buggy, but it is after all the development version. By and large there is finally a reliable, fairly easy way to use devices like the Bt848 based Hauppauge and SAA7136 based video capture cards. 

I do have to change playback default in Lives from mencoder to xawtv to be able to set the input to the card, which presents other issues. Fortunately Lives has a great GUI so it is easy to deal with. One must remember to change back to mencoder before adding any audio track, though, or the whole thing ( Lives, xawtv, sound recorder)  crashes. The default option seems to be PAL, so good for them, My stuff is all ntsc. 

Video capture is good, with user variable frame rates, audio and video codecs, etc.
I use sound recorder to capture an audio track. So far it has been fairly easy to synch the two with the multi track mode in Lives.

Again, before adding any captured audio, switch back from xawtv to mencoder.

I did have some luck also with tvtime as the default playback instead of mencoder, but if you forget to switch back to mencoder before adding any audio to the project, tvtime freezes and won't release the tv card unless you reboot. So I use xawtv, which is a little more forgiving.

I would suppose there is something I could permanently set in mencoder to open the video 0 input1 ntsc, etc but iI don't know what it is or where to write it.

---

