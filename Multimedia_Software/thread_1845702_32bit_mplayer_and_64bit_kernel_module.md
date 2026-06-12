---
title: "32bit mplayer and 64bit kernel module"
date: 2011-09-17
forum: Multimedia Software
---

### Post by faroutliving on 2011-09-17
I'm running 11.04 64bit Ubuntu using a custom build 32bit version of mplayer so I can play Apple ProRes files. That seems to be ok, but I need to output to a Blackmagic DeckLink card.

I originally installed the 64bit DeckLink kernel modules using their source and dkms and even compiled and ran some test applications and wrote my own pass through code that works.

When I initially tried to use the 32bit mplayer, it complained that "libDeckLinkAPI.so: cannot open shared object file: No such file or directory" so I installed the 32 bit version of that link library.

But now when i try and play video to the decklink card, mplayer tells me:

[decklink] Could not find a Decklink device

My only guess is that I need a 32bit kernel module? Is that even possible? How would that work? This is (roughly) the steps I took to install the 64bit modules:

cp DesktopVideo-8.0.1rc4-x86_64/etc/udev/rules.d/20-blackmagic.rules /etc/udev/rules.d/
cp DesktopVideo-8.0.1rc4-x86_64/usr/lib64/blackmagic/BlackmagicPreferencesStartup /usr/lib64/blackmagic
cp DesktopVideo-8.0.1rc4-x86_64/usr/lib64/blackmagic/blackmagic-firmware-notify /usr/lib64/blackmagic
cp DesktopVideo-8.0.1rc4-x86_64/usr/lib64/libDeckLinkAPI.so /usr/lib64/blackmagic/

added /usr/lib32/blackmagic using ldconfig

cp -R DesktopVideo-8.0.1rc4-x86_64/usr/src/DesktopVideo-8.0.1rc4/ /usr/src
dkms add -m DesktopVideo -v 8.0.1rc4
dkms build -m DesktopVideo -v 8.0.1rc4
dkms install -m DesktopVideo -v 8.0.1rc4
modprobe blackmagic

I know, lots of bits are vague here, but I don't want make this post so long that someone will not look who might be able to help. I don't mind learning (I've learned a ton doing this so far) but need at least some hints that will improve my odds of success. I'm happy to provide contents of the 20-blackmagic.rules etc if it would help give an answer or suggestion.

I can _NOT_ use 32bit verison of the OS, or 64 bit version of mplayer (at least until someone release a 64bit codec for Apple ProRes, sigh...) so please don't suggest that!

Thanks,

Deron

---

### Post by CraigsBar on 2011-10-23
Hi,

I had a similar issue with a BlackMagic Intensity Pro card and kubuntu 64bit.

The solution I discovered is to link the 2 libDeckLink libs from /usr/lib64 to /usr/lib using symbolic links as follows.... 

```
sudo ln -s /usr/lib64/libDeckLinkAPI.so /usr/lib/libDeckLinkAPI.so
sudo ln -s /usr/lib64/libDeckLinkPreviewAPI.so /usr/lib/libDeckLinkPreviewAPI.so
```

I now have a fully functioning Intensity card and I can finally start ripping the content off my Sky+ HD box LOL

Regards

Craig

---

### Post by andrew.46 on 2011-10-25
It is a bit of a side-issue but you may be interested to know that the 64bit svn MPlayer can now play Apple prores files natively using ffprores. Might make things a little easier for you? Screenshot attached...

---

### Post by faroutliving on 2011-11-04
I did see the ProRes release! I'm using it instead of 32bit version of mplayer, but it still has some problems. For short video it runs ok, but longer (15+ minutes) it starts to drop frames and has audio sync problems. They even have an encoder now! Certainly a better situation than before! Thanks to all for the feedback.

---

### Post by paulinchen on 2012-01-25
Hi there, I got a new decklink studio 2 card and am trying to get that recognized from mplayer.
I compiled mplayer following this guide to have ProRes Support

[HTML]http://ubuntuforums.org/showpost.php?p=9338033&postcount=4[/HTML]

I installed DesktopVideo and MediaExpress

and following your post here i created the link to the /usr/lib

Is there anything else, what I have to do, to find decklink as videooutput in mplayer?

Thanks

---

