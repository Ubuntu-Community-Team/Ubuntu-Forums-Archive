---
title: "New install, SD lip sync and picture issues, no problems on HD"
date: 2014-03-04
forum: Mythbuntu
---

### Post by tjobrien21 on 2014-03-04
Hi, 

I'm a n00b who just moved from Win7 Mediacenter to Mythbuntu due to the Mediacenter's propensity to freeze up. I downloaded it yesterday and it's all up and working, but there are a few issues I'd like to solve if possible. I searched online but haven't found what I'm looking for, or it's there and I haven't recognized it..

HD channels look and work great. SD however, looks worse than it did in Mediacenter. It seems almost like there are scaling issues causing it to have sharp edges in some places, and patterns like the roof of a house will animate rather wildly as the camera pans. The other issue with SD is sound. On HD channels, sound is sync'd with the content. On SD channels, it's not. 

I'm using the same hardware I used for the windows setup: Dell Optiplex755 PC (core2 duo, 4G of RAM), an Nvidia 1GB 8400 video card (if I remember correctly), and a HD Homerun network tuner. Network is wired, not wireless and the one machine runs the frontend and the backend both.

Could someone please point me in the right direction? 

Thanks,
Tim

---

### Post by david169 on 2014-03-04
it's been over a year since I've run myth so can't remember the exact settings but try enabling VDPAU.. they're in the frontend settings menu somewhere. I think by default myth just has a single playback profile for all content but you can fine tune it for each resolution...

[http://www.mythtv.org/wiki/Playback_profiles](http://www.mythtv.org/wiki/Playback_profiles)

I'm sure I've been able to resolve my issues by playing around with these options.

Your deinterlacing filter can make a big difference too

---

### Post by sdowney717 on 2014-03-05
Do you have the latest binary Nvidia driver? or are you using the free driver that comes with ubuntu.

---

### Post by tjobrien21 on 2014-03-05
Thanks David and Sdowney! David, I'll try making those changes and see if they help. Sdowney, I'm running the nvidia driver, not the open source one, which is supplied with Mythbuntu. Is that sufficient, or is there a better driver I should obtain and install? I'm not a complete Linux n00b, just MythTV so I can probably do it if needed. :)

---

### Post by newlinux on 2014-03-05
I'm not sure all 8400s suppurt VDPAU. You should make sure you know the model number and check for compatibility. that said, you still should try different playback profiles. What is the source of your SD recordings (what tuner do you have)? Although not an optimal solution, you can adjust the audio sync while you are playing a recording through the menu. You also might want to try playing your SD recordings with mplayer or VLC to make sure there is no problem withe recordings themselves.

---

### Post by sdowney717 on 2014-03-05
I am running mythtv on ubuntu 14.04 
It seems to me this way I get the most upto date software.
And easy enough to install the latest driver.

Whether that would help your case, I dont know.

If you have a PCI-E mb, I would get a more powerful video card, even used one off ebay.
I have a GTX 260 i216 core nvidia and that works fine.

---

