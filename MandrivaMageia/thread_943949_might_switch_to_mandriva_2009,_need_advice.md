---
title: "might switch to mandriva 2009, need advice"
date: 2008-10-10
forum: Mandriva/Mageia
---

### Post by smooth3006 on 2008-10-10
i see mandriva 2009 is out and it seems to be a good package. i also heard it is better than ubuntu ? the main thing i see in the 2009 build is it has full graphical syncing support for windows mobile phones. :KS

would you recommend this over ubuntu ?

---

### Post by SuperSonic4 on 2008-10-10
It really depends on what DE you choose. Mandriva > Kubuntu IMO. I've never tried their [mandriva's] gnome version  

Personally, I like mandriva, I think it is better than ubuntu except in support and apt. But urmpi is pretty good and [easy urmpi]("http://easyurpmi.zarb.org/") owns for adding sources just be sure to click PLF (you'll have the main ones already). Enabling backports will get you amarok 1.4.10 and k3b among others. 

I've not tried it with a mobile phone though. Personally, I'd go with a mandriva/ubuntu dual boot for now or mandriva outright

---

### Post by perlluver on 2008-10-10
> **smooth3006 said:**
> i see mandriva 2009 is out and it seems to be a good package. i also heard it is better than ubuntu ? the main thing i see in the 2009 build is it has full graphical syncing support for windows mobile phones. :KS

would you recommend this over ubuntu ?

Depends, if you like RPM then yeah you will like Mandriva, apt-get is nice for most, and .debs.  It does install all codecs, and video drivers automatically.  I liked it when I used it, but I prefer Ubuntu, so I came back.  In the end, the choice is yours, try it, if you don't like, come back to Ubuntu.

---

### Post by smooth3006 on 2008-10-10
not too sound like a total noob but mandriva has grub as the bootloader right ? i mean i should have no issues dual booting with vista already installed ?

---

### Post by SuperSonic4 on 2008-10-10
> **perlluver said:**
> Depends, if you like RPM then yeah you will like Mandriva, apt-get is nice for most, and .debs.  It does install all codecs, and video drivers automatically.  I liked it when I used it, but I prefer Ubuntu, so I came back.  In the end, the choice is yours, try it, if you don't like, come back to Ubuntu.

Not to mention the Mandriva Control Centre is beyond awesome.

It gets neither audio nor video codecs to my knowledge (I had to install them to get amarok working) but it does give you flash, java and video card drivers out of the box (at the one version does)


I'll have a look for audio packages

```
faac
gstreamer0.10-faac
libfaac0
libfaac-devel
libquicktime-faac
faad2
gstreamer0.10-faad
libfaad2_0
libquicktime-faad
xine-faad
libaviplayavcodec0.7
win32-codecs
libgmp3
```

---

### Post by perlluver on 2008-10-10
It does have Grub, as far as I know, and you shouldn't have any problems dual booting with Vista.

---

### Post by smooth3006 on 2008-10-10
> **SuperSonic4 said:**
> It gets neither audio nor video codecs to my knowledge (I had to install them to get amarok working) but it does give you flash, java and video card drivers out of the box (at the one version does)

I'll have a look for audio packages

i just read it does give you audio / video codecs.

---

### Post by SuperSonic4 on 2008-10-10
Yeah, mandriva does have grub, it is a graphical grub too. As with ubuntu just pick the top option

---

### Post by SuperSonic4 on 2008-10-10
> **smooth3006 said:**
> i just read it does give you audio / video codecs.

It could well do now it's not cooker. I know I needed to install mp3 support for movie player and amarok 1.4

---

### Post by smooth3006 on 2008-10-10
i guess i was wrong, in order to have all of the audio / video codecs you need to buy powerpack 2009. that sucks for them to charge for that. where can i manually download these codecs at ?

---

### Post by SuperSonic4 on 2008-10-10
Once you've installed it you can get the codecs that I've mentioned in a previous post but first you need to add the PLF sources from [http://easyurpmi.zarb.org/](http://easyurpmi.zarb.org/)
 
Autodetect should be fine for your system although pick 2009.0 if not and press "Add PLF media" then you can go into the Mandriva Control Centre and go to install software, search and select the packages I mentioned above. Selecting VLC package (from PLF preferably rather than MDV) should deal with video dependencies

---

### Post by smooth3006 on 2008-10-10
> **SuperSonic4 said:**
> Once you've installed it you can get the codecs that I've mentioned in a previous post but first you need to add the PLF sources from [http://easyurpmi.zarb.org/](http://easyurpmi.zarb.org/)
 
Autodetect should be fine for your system although pick 2009.0 if not and press "Add PLF media" then you can go into the Mandriva Control Centre and go to install software, search and select the packages I mentioned above. Selecting VLC package (from PLF preferably rather than MDV) should deal with video dependencies

thanks man im used to ubuntu not mandriva. i downloaded the gnome version so you know.

---

### Post by SuperSonic4 on 2008-10-10
> **smooth3006 said:**
> i guess i was wrong, in order to have all of the audio / video codecs you need to buy powerpack 2009. that sucks for them to charge for that. where can i manually download these codecs at ?

You have to remember that the codecs are non-free so they have to sell them or have a legal issue on their hands :p

> **smooth3006 said:**
> thanks man im used to ubuntu not mandriva. i downloaded the gnome version so you know.

No worries, I've never had the gnome version but I suspect they're the same package manager.

---

### Post by smooth3006 on 2008-10-10
i was hoping i could follow the multimedia / audio guide on this forum but i guess that's just for ubuntu. :lolflag:

one more question, i know the mandriva 2009 version comes with the newest linux kernel, what file system would you recommend formatting to, etx3 ?

---

### Post by AdamWill on 2008-10-10
To answer the original question - grab Mandriva and try it. Only you can answer the question for yourself. Of course, if you want my answer, Mandriva's the best, and Ubuntu will probably give you cooties. :)

On codecs - what Powerpack has is the Fluendo codecs (well, not all of them, a subset) which are codecs they've paid the patent holders for a legal license to. This means they're completely legal in the U.S., but it also means they cost money, they're not open source, and they're not freely redistributable. So we can only include them in Powerpack. You wouldn't get these for free in other distros either, we're not hiding stuff from you to make a buck.

With packages from the official repos you should be able to get most stuff playing. The most significant exception is AAC audio. The only way to get that is from PLF, and I should note that the patent-encumbered stuff in PLF is strictly illegal to use in the U.S. (thank the stupid software patent regime).

If you have trouble playing anything in particular, make a post here or in the official forums, and we'll help you out with that particular issue.

---

### Post by SuperSonic4 on 2008-10-10
Mine is ext2/linux native but ext3 does work I believe.

As for the multimedia guide the audio codecs should be in my post, I searched for faad,faac,mp3 and codec. Just make a topic if you need more help on them

---

### Post by smooth3006 on 2008-10-10
> **AdamWill said:**
> To answer the original question - grab Mandriva and try it. Only you can answer the question for yourself. Of course, if you want my answer, Mandriva's the best, and Ubuntu will probably give you cooties. :)

On codecs - what Powerpack has is the Fluendo codecs (well, not all of them, a subset) which are codecs they've paid the patent holders for a legal license to. This means they're completely legal in the U.S., but it also means they cost money, they're not open source, and they're not freely redistributable. So we can only include them in Powerpack. You wouldn't get these for free in other distros either, we're not hiding stuff from you to make a buck.

With packages from the official repos you should be able to get most stuff playing. The most significant exception is AAC audio. The only way to get that is from PLF, and I should note that the patent-encumbered stuff in PLF is strictly illegal to use in the U.S. (thank the stupid software patent regime).

If you have trouble playing anything in particular, make a post here or in the official forums, and we'll help you out with that particular issue.

could you guys give me a list of common codecs i may want to install ? im burning the iso to a dvd now as we speak. 

again what file system should i format too , ext3 ?

---

### Post by SuperSonic4 on 2008-10-10
ext3 sounds good. I don't think you'll have issues with ext2 or ext3 but I am running a stable system on the former.

As for audio codecs (some of these could be superfluous): ```
faac
gstreamer0.10-faac
libfaac0
libfaac-devel
libquicktime-faac
faad2
gstreamer0.10-faad
libfaad2_0
libquicktime-faad
xine-faad
libaviplayavcodec0.7
win32-codecs
libgmp3
```

Video

```
ffmpeg
gstreamer-0.10-ffmpeg
libquicktime
```

---

### Post by eternalnewbee on 2008-10-10
Hi guys,
This may sound strange, but my Ubuntu is like family to me.
I took a look at the Mandriva screenshots and they looked nice enough, but what with all that's going on with w#ndows, I feel this is not the time (for me) to switch to another OS, even if it's better in some areas, just to keep Ubuntu strong.
Live long & prosper.

---

### Post by AdamWill on 2008-10-10
supersonic: faac stuff is encoding, so you only need it if you want to encode AAC. faad is enough for decoding (playback). Otherwise your list looks good.

---

### Post by smooth3006 on 2008-10-11
i have a question about what driver to install for my graphics card ? i have a nvidia geforce 7150m but i don't see a proper driver for it ?

---

### Post by eternalnewbee on 2008-10-11
Doesn't Ubuntu automatically recognise the graphic card?

---

### Post by Antman on 2008-10-11
> **smooth3006 said:**
> i guess i was wrong, in order to have all of the audio / video codecs you need to buy powerpack 2009. that sucks for them to charge for that. where can i manually download these codecs at ?
If you want the codecs, just go to [http://easyurpmi.zarb.org/](http://easyurpmi.zarb.org/) and grab the PLF repos... than add the codecs you need (see Supersonics post above).

---

### Post by Antman on 2008-10-11
> **smooth3006 said:**
> i have a question about what driver to install for my graphics card ? i have a nvidia geforce 7150m but i don't see a proper driver for it ?
What Mandriva CD are you using to install from? I *think* the 'ONE' CD should have the Nvidia drivers already and install the correct one for you.

---

### Post by smooth3006 on 2008-10-11
> **Antman said:**
> What Mandriva CD are you using to install from? I *think* the 'ONE' CD should have the Nvidia drivers already and install the correct one for you.

yes im using the one cd, no during install it would not configure the x server. i had to do a text based install. the drivers available are geforce 6000 and up or geforce 7050.

---

### Post by AdamWill on 2008-10-11
You want 6100 or higher. In Mandriva I generally have the cards organized in big groups, because big groups of cards use the same driver setting. The 7050 entry is a special case because 'nv' doesn't apparently work with the 7050, so it's set to use vesa instead of nv for its free driver.

Usually One would configure the card automatically, but you're probably running into this:

[http://wiki.mandriva.com/en/2009.0_Errata#One_editions_fail_to_boot_to_a_graphical_desktop_.28xorg.conf_not_created.29](http://wiki.mandriva.com/en/2009.0_Errata#One_editions_fail_to_boot_to_a_graphical_desktop_.28xorg.conf_not_created.29)

---

### Post by Vulpus on 2008-10-13
> **smooth3006 said:**
> i guess i was wrong, in order to have all of the audio / video codecs you need to buy powerpack 2009. that sucks for them to charge for that. where can i manually download these codecs at ?
When you try to play a video or audio file that needs specific codecs Mandriva will tell you and ask if you want to download them. It will usually give you the choice of the fluendo or PLF versions.  THe PLF versions are gratis.

Note, I think the above only happens with certain media players such as Mplayer (Totem).  So if you install say VLC and try to play an AVI file it will just not work.  But if you try to play it in MPlayer you will get the above warning.  

What I do when I do a fresh install of Mandriva is try to play an example of every multimedia file I have in MPlayer and then install the codecs it says are missing.  It only takes about fifteen minutes and you only have to do it once.

---

### Post by karellen on 2008-10-13
> **smooth3006 said:**
> i see mandriva 2009 is out and it seems to be a good package. i also heard it is better than ubuntu ? the main thing i see in the 2009 build is it has full graphical syncing support for windows mobile phones. :KS

would you recommend this over ubuntu ?

to put it simply, yes ;)

---

