---
title: "Remote DVD ISO Playback"
date: 2012-07-26
forum: Mythbuntu
---

### Post by jlp_engineer on 2012-07-26
I have a nagging issue that I hope can be resolved.  I have Master/Slave systems connected via Gigabit Ethernet to a few remote Frontends.  Everything works, but the video on one of them seems to skip a few frames every couple of minutes.  LiveTV and recorded TV work fine on this same FE.  

The FE that works flawlessly is the Zotac MAG with nVidia ION graphics (1.6GHz Atom dual core and essentially 9000 series graphics GPU), while the one that is skipping video on DVD's ISO files pulled from the Master Backend, is running off a slim chassis Lenovo Thinkcenter PC with 2GB of RAM, a 2.0GHz Core2 Duo CPU, and a low profile GT 520 for graphics (ZT-50604-10L).  

Using the Playback Data option, I can see that DVD ISO playback on both FE's get about 900 Mbps "Storage to Buffer", but only about 1 - 2 Mbps "Buffer to Decoder".  Codec is MPEG-2 and the decoder is vdpau on both.  Both playback profiles are set to VDPAU Normal.  Do I have a setting wrong?

I am not sure if the problem is with the video or the network connection, but I am guessing it is one or the other.  Any ideas on how to isolate the problem?

Thanks.

---

### Post by nickrout on 2012-07-27
> **jlp_engineer said:**
> I have a nagging issue that I hope can be resolved.  I have Master/Slave systems connected via Gigabit Ethernet to a few remote Frontends.  Everything works, but the video on one of them seems to skip a few frames every couple of minutes.  LiveTV and recorded TV work fine on this same FE.  

The FE that works flawlessly is the Zotac MAG with nVidia ION graphics (1.6GHz Atom dual core and essentially 9000 series graphics GPU), while the one that is skipping video on DVD's ISO files pulled from the Master Backend, is running off a slim chassis Lenovo Thinkcenter PC with 2GB of RAM, a 2.0GHz Core2 Duo CPU, and a low profile GT 520 for graphics (ZT-50604-10L).  

Using the Playback Data option, I can see that DVD ISO playback on both FE's get about 900 Mbps "Storage to Buffer", but only about 1 - 2 Mbps "Buffer to Decoder".  Codec is MPEG-2 and the decoder is vdpau on both.  Both playback profiles are set to VDPAU Normal.  Do I have a setting wrong?

I am not sure if the problem is with the video or the network connection, but I am guessing it is one or the other.  Any ideas on how to isolate the problem?

Thanks.

What sort of network? Are they both wired? EDIT: sorry just re-read and they are wired gigE. Perhaps one has a dicky network card? Or bad wiring?

---

### Post by Boppy3125 on 2012-07-27
Best way I can think of is to take network out of the equation, copy the iso locally.

---

### Post by jlp_engineer on 2012-07-29
> **nickrout said:**
> What sort of network? Are they both wired? EDIT: sorry just re-read and they are wired gigE. Perhaps one has a dicky network card? Or bad wiring?

I will test the network connections tomorrow and post back.  Hopefully there is a good network monitor application that will log the data for analysis.  I will also drop a new CAT5e line to the switch to check the wiring.

Thank you Nick.

---

### Post by jlp_engineer on 2012-07-29
> **Boppy3125 said:**
> Best way I can think of is to take network out of the equation, copy the iso locally.

Good idea - I will do that and post the results.

---

### Post by jlp_engineer on 2012-08-02
OK,

I have tried the following:

1 - I copied an ISO DVD file to the local hard drive, but noticed the same dropped frames or stuttering in the video, or whatever this is.

1 - Tried an identical Lenovo 6072, using the same software load and low profile GT 520 video card...same results.

2 - Tried an old Gateway BTX with the same speed Core 2 Duo CPU, and using the same GT 520 video card...same results.

3 - Tried the same Gateway BTX tower, but put in a GT 430 video card, and used the same software load (hence he same driver)...same results, but perhaps the issue happens with a little lower frequency.

Could I be looking at an interaction of the VDPAU decoder with the Samsung 7900 Series TV I have?

Are there any known issues with the Samsung 55" 7900 series TV when viewing DVD's encoded and then decoded through VDPAU over HDMI?

Am I missing something here?

---

### Post by tgm4883 on 2012-08-02
> **jlp_engineer said:**
> OK,

I have tried the following:

1 - I copied an ISO DVD file to the local hard drive, but noticed the same dropped frames or stuttering in the video, or whatever this is.

1 - Tried an identical Lenovo 6072, using the same software load and low profile GT 520 video card...same results.

2 - Tried an old Gateway BTX with the same speed Core 2 Duo CPU, and using the same GT 520 video card...same results.

3 - Tried the same Gateway BTX tower, but put in a GT 430 video card, and used the same software load (hence he same driver)...same results, but perhaps a little less frequency in the issue.

Could I be looking at an interaction of the VDPAU decoder with the Samsung 7900 Series TV I have?

Are there any known issues with the Samsung 55" 7900 series TV when viewing DVD's encoed and then decoded through VDPAU over HDMI?

Am I missing something here?

Is it possible you have a bad ISO

---

### Post by jlp_engineer on 2012-08-02
> **tgm4883 said:**
> Is it possible you have a bad ISO

Nope - Happens on all of them, but some less than others.  I can even get it to happen on HiDef content recorded from one of my ATSC tuners, but it happens much less often, than when viewing DVD ISO's.  Even happens when I play an actual DVD.

I just wish there was a way to isolate where this is happening!

---

### Post by anonymousdog on 2012-08-02
Take the TV out of the loop.  Test these on another LCD.

---

### Post by jlp_engineer on 2012-08-02
Yes, that is next on my list of things to try.  May take a few days to set it up, however.  I will post my results here.

---

### Post by nickrout on 2012-08-02
yes, perhaps a frame rate mismatch?

---

### Post by jlp_engineer on 2012-08-03
OK people...are you ready for this???

The issue was caused by a setting on the TV.  There is a "feature" called "Auto Motion Plus" that is supposed to reduce blur, etc., when there is fast motion on the screen.  However, for me it causes a sort of "stop motion jitter" on the screen with fast motion.  I changed the setting from "Smooth" to "Clear" and viola, the issue is gone.  

I guess one setting does not work for every situation, but clearly the default in this case was wrong for the content I was playing.  I guess you just expect more from a $3000 TV :-(

---

