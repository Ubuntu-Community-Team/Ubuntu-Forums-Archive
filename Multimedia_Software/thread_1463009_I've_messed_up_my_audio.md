---
title: "I've messed up my audio"
date: 2010-04-26
forum: Multimedia Software
---

### Post by Pomegranete on 2010-04-26
Hey folks,

I'm in need of some help. 

First, some background. I'm using an Acer laptop which is great but with abysmal sound in the inbuilt speakers/soundcard. Under Windows I bought a Creative X-Fi Go external USB soundcard, which was working perfectly. When I switched over to 9.10, it didn't work. I researched online and found there are no drivers for it under the default Ubuntu sound system (which is ALSA, correct?). I also found out that there was a beta driver for it on OSSv4. I followed a tutorial and installed OSSv4, and it worked a little bit. It didn't work with most programs, AmaroK being one of the few wherein it did. This was all last night. I started back up this morning and now nothing sends audio through the external soundcard (and speakers), some playing through the inbuilt audio, and some playing nothing.

I fear that with my attempts to use workarounds that I've messed up the system audio. When I go to System>Preferences>Sound, it 'searches for sound system' but to no avail.

I've used Ubuntu a few times over the years, and I'm not completely incompetent, but some simple help would be greatly appreciated, preferably with how to get my soundcard to work under OSSv4 (which it did before) and how to get the system to play well with it, but if not, then just how to get the system reverted to default.

Thanks,
Pome.

---

### Post by Pomegranete on 2010-04-27
bump; anybody at all, please? I really need some help, if I can't get this sorted I'm just going to have to switch back to windoze.

---

### Post by Yellow Pasque on 2010-04-27
You haven't configured your applications for OSS:
[http://www.opensound.com/wiki](http://www.opensound.com/wiki)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

