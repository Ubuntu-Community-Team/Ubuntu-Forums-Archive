---
title: "Which Ubuntu Distro to get full ffmpeg install"
date: 2008-10-28
forum: Multimedia Software
---

### Post by ahickey on 2008-10-28
I have been running Ubuntu 8.04 and went looking for a way to convert videos to play on the PSP.

From my research my understanding is that the installed version of ffmpeg is a 'limited fuctionality' version which is why none of the commands I have used have worked.

I am considering doing a fresh install of my systems and was wondering which Ubuntu based distro will give me the fullest version of ffmpeg, so I can do this.

I'm considering
Ubuntu
Kubuntu
Mint
Medibuntu
UbuntuStudio
Mythbuntu

Also, I expect if some of the apps I want are not installed by default I can just add them through Synaptic.

Any info would be greatly appreciated.

Thanks,
Albert.

---

### Post by SunnyRabbiera on 2008-10-28
Well there is a lot of crap going on with ffmpeg right now with it being challenged with software patent bull.
I think its possible to get the full out version of ffmpeg working in any version of ubuntu though, it should not matter.
But rather if it really can do what you ask I am very unsure.

---

### Post by timcredible on 2008-10-28
make it easy on yourself and install winff - it's a gui for ffmpeg, and psp is one of it's preset formats.  ffmpeg doesn't really have any installation options, i think what you're running into is that the codecs aren't installed.

---

### Post by ahickey on 2008-10-29
Thanks. I'll install winff and see if it sorts me out.

Any idea which codec I need specifically for the PSP?
Would just copying a known good video file from my PSP to my system and opening it in gstreamer have me prompted to install the right codec?

I found the following link which I will try tonight to get the 'full' set of codecs.
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Albert

---

### Post by Yellow Pasque on 2008-10-29
Mint would be best for this purpose. 

If you choose to install packages from Medibuntu, make sure you go into Synaptic Package Manager and use the 'Force Version' and 'Lock Version' options under the Package menu so that Ubuntu doesn't automatically replace your custom-installed package with a later version with limited functionality.

---

