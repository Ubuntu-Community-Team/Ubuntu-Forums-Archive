---
title: "Creative x-fi pointless on Ubuntu?"
date: 2009-05-02
forum: Multimedia Software
---

### Post by ualnivek on 2009-05-02
Is there any benefit of using a Creative sound card over an on-board sound card if I am running Ubuntu? I've got basic third party drivers to get my SB Live card to play surround sound, but I miss the enhancements I get in XP.

Despite reading all the rumors or news that Creative will release drivers for Ubuntu, could I doubt it would provide full support to use all the card's features such as EAX? Would upgrading to an X-fi card and using Ubuntu be just a waste of money?

---

### Post by rabbit251 on 2009-05-02
I have a Creative X-Fi, and though I've been keeping an eye on [How-To: Creative X-Fi]("http://ubuntuforums.org/showthread.php?t=870001"), I haven't tried following the advice to get it working with Ubuntu. I'm suspicious of his recommendation to install the package "flashplugin-nonfree-extrasound", due to [HOWTO: PulseAudio Fixes & System-Wide Equalizer Support]("http://ubuntuforums.org/showthread.php?t=789578")'s strong cautioning against it:

> Ensure the evil "libflashsupport" library is not installed:

```
$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
```

[COLOR="Blue"]Note: the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks![/COLOR]

As for:

> Despite reading all the rumors or news that Creative will release drivers for Ubuntu, could I doubt it would provide full support to use all the card's features such as EAX? Would upgrading to an X-fi card and using Ubuntu be just a waste of money?

Unfortunately, I can't comment on the completeness of feature support with these drivers. But what's this about a waste of money?  I thought you already owned an X-Fi, or is it that you're considering buying one?

---

### Post by ualnivek on 2009-05-02
I have an old SB Live, not an X-Fi, on my desktop which is working ok with the OSS/ALSA drivers. I'm not sure if it's delivering the same sound quality as the on-board sound cos I don't wanna mess around with it since it took me a while to get the SB working with surround. However, I do know it doesn't sound the same as on XP because increasing the bass level muffles the sound on the speakers, rather than increasing it on the sub.

What I really want to get an idea of is, I also have a laptop running XP with the on-board sound, and it's alright, though I can really hear the quality difference using a SB Audigy2 ZS Notebook. With this laptop, I also want to switch to Ubuntu as well. The ZS, I'm sure is not supported under Ubuntu because I haven't found anything, or maybe I hadn't looked hard enough.

I love high quality audio in my music, and read there are beta official Creative X-Fi drivers for Ubuntu so I was thinking of buying an X-Fi Notebook Express34 to replace the ZS. However, I'm also thinking that with only third party drivers and beta official Creative X-Fi drivers for Ubuntu, the sound quality from this X-Fi card would only be as good as the on-board laptop sound. My thoughts are the beta Creative X-Fi drivers are "only enough to get the X-Fi sound card working like a generic sound card". This is why I asked if using a X-Fi card is pointless on Ubuntu, and a waste of money to get something that is already doing the same job.

---

### Post by picopir8 on 2009-05-02
You may also want to look into the Razer Barracuda.  I have not looked at soundcards lately but as of about a year or so ago, they had a slight edge over Creative, and just about everyone has better driver support than creative.  I found a barracuda dirt cheap on woot.com about 18 months ago and I jumpted to replace my old audigy.  I put it in a XP gaming box which also dual boots hardy. It works great in both environments.

---

