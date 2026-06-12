---
title: "Mythbuntu Choppy Video/No Sound fix?"
date: 2009-05-03
forum: Multimedia Software
---

### Post by Jr. on 2009-05-03
Hey, I just installed mythbuntu 9.04 using a pcHDTV 5500 card. For starters, video works. However, it doesn't work well. I have 2 main issues:

1. The video quality is horrible, choppy, there is the white and black bar on the top, refresh rate is really low. It's just all around bad.

2. No sound.

I know these are common issues and I've been searching all over the forums for fixes. Everyone has different fixes and none of them have worked for me. Can someone who has had these exact problems post a link to a fix that worked for you? Thanks for the help.

---

### Post by gnulogic on 2009-05-03
turn off compiz (advanced desktop effects).

---

### Post by Jr. on 2009-05-03
Thanks for the suggestion gnulogic, but mythbuntu doesn't have compiz.

---

### Post by Jr. on 2009-05-03
Ok, I got audio working. I have an audio card that took up dsp0 so I just changed the sound card to dsp2 under the capture card setup. However, I can barely hear the sound. Even at full volume it is extremely quite. Also, video quality is still horrible. It seems like it could just be a refresh rate issue. How do I change the refresh rate?

---

### Post by Jr. on 2009-05-04
I just tried mythdora and I couldn't even get live tv playback... I just bought this [http://www.newegg.com/Product/Product.aspx?Item=N82E16813130182](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130182)... I was having a lot of other issues with my mobo and graphics anyways. I've been hearing of issues with jaunty and ati so I'm gonna dump my ati mobo and go with on board nvida.

---

### Post by DominicF on 2009-05-07
Hi,

Which graphics chipset are you running, intel or Nvidia?

I'm having a similar issue, I'm running with onboard intel graphics (945GM) on my motherboard and I think there is something wrong with the intel drivers.  I then install an Nvidia card and drivers and the choppy video problem was gone.  For me, ubuntu 8.04 worked well with my onboard Intel graphics but 8.10 and 9.04 I have this problem with choppy video (refresh rate issue).  I don't really want to install the Nvidia card as it will use up a free slot on the MB as I want to use for something else.

---

### Post by Jr. on 2009-05-07
I was using ati, just switched to nvida. Still have issues though... I'm gonna work on it tonight and see what i can do.

---

### Post by DominicF on 2009-05-11
Just a thought, when you switched to the nvidia setup did you remember to activate the Nvidia driver through the Mythbuntu Control Centre and perform a re-boot?

---

### Post by pauna on 2009-05-11
> **Jr. said:**
> Hey, I just installed mythbuntu 9.04 using a pcHDTV 5500 card. For starters, video works. However, it doesn't work well. I have 2 main issues:

1. The video quality is horrible, choppy, there is the white and black bar on the top, refresh rate is really low. It's just all around bad.


Play with your playback profile settings. Some settings require a lot of CPU power and may cause choppiness. 

See more from [http://www.mythtv.org/wiki/Playback_profiles](http://www.mythtv.org/wiki/Playback_profiles)

---

### Post by Jr. on 2009-05-11
Ya I've seen stuff about the playback settings, but I don't know where it is that I change them...

---

### Post by pauna on 2009-05-12
> **Jr. said:**
> Ya I've seen stuff about the playback settings, but I don't know where it is that I change them...

My MythTV GUI is not in English so the exact menu item names may be a little off.

But when you get to the MythTV main screen (where you can select watching TV etc), selet the last option (Utilities/Setup?). From there Setup -> TV Setup -> Playback. This has about 9 screens full of various options, the playback profile is in 3/9.

---

