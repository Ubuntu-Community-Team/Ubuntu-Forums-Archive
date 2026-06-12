---
title: "Checklist before I install Hardy"
date: 2008-05-18
forum: Multimedia Software
---

### Post by MidBSD on 2008-05-18
I tried Hardy Heron three weeks ago on my Aspire 5103 laptop but I couldn't get a number of things working properly.

I'd really like to update but I'm worried I'll still have the same problems.

Can someone tell me if there are solutions to the following:

1) Drives no longer automount but they're listed in Nautilus. When I click them they mount - will I cause a conflict if I mount them under fstab?

2) I can't get video to play with the correct codec. I'm not sure how to explain the problem other than to say that it looks blocky and pixellated and consumes more CPU than would normally do. I had ATI drivers installed using Envy. I don't have this problem in Gutsy.

3) Wifi won't automatically connect. I have to keep typing in the password everytime I reboot. I think I needed to do this for Gutsy too but I automated this with some utility. Is this necessary in Hardy too?

If I can get these solved I'll be able to update to the latest.

---

### Post by MidBSD on 2008-05-18
Oops - I've posted to the wrong forum!

Can a mod move this to general help for me plz?

---

### Post by MidBSD on 2008-05-19
Should I just re-post this instead? I don't want to cross-post if that's not allowed :(

---

### Post by cor2y on 2008-05-19
If you want automounting install the ntfs-3g package, reboot and then enable it.
```
sudo apt-get install ntfs-3g ntfs-config
```Applications->System Tools->Ntfs Configuration
Enable write support for internal/external devices and from now on anytime you reboot its always automounted.
Beats messing around with fstab manually.

Video codecs, i try to stick with one media player but of course i have two installed :) , the default media player totem-gstreamer needs all its codec pliugins installed and a recompile of one, so enable the restricted , multiverse, universe repos search via synaptic for gstreamer and install all the plugins ,also add the medibuntu repos you will need the w32codecs from there as well as dvdcss, dvdnav, dvdread library for dvd playback.Also mplayer because it has the better browser plugin (mplayer-mozilla) than the default one that ships with ubuntu (totem plugin is lacking)
Video driver if your video chipset worked in gutsy it should work in hardy but thats no guaranty the ioen source ati drivers have greatly improved but if you need 3d support check to see if your chipset is supported with the closed drivers,  the sticky in this forum should help or this [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

Wifi thats a whole another thing not to familiar with it since it works for me (lucky that wifi chipset is support by default) but they improved the wifi connection you may need to install/edit some extra things to keep from having to reconnect or enter the password everytime you connect.

So at the end of the day you need ntfs-3g, totem-gstreamer's plugins, mplayer (for the browser plugin), closed source video driver (perhaps)

---

### Post by MidBSD on 2008-05-20
> **cor2y said:**
> If you want automounting install the ntfs-3g package, reboot and then enable it.
```
sudo apt-get install ntfs-3g ntfs-config
```Applications->System Tools->Ntfs Configuration
Enable write support for internal/external devices and from now on anytime you reboot its always automounted.
Beats messing around with fstab manually.

Video codecs, i try to stick with one media player but of course i have two installed :) , the default media player totem-gstreamer needs all its codec pliugins installed and a recompile of one, so enable the restricted , multiverse, universe repos search via synaptic for gstreamer and install all the plugins ,also add the medibuntu repos you will need the w32codecs from there as well as dvdcss, dvdnav, dvdread library for dvd playback.Also mplayer because it has the better browser plugin (mplayer-mozilla) than the default one that ships with ubuntu (totem plugin is lacking)
Video driver if your video chipset worked in gutsy it should work in hardy but thats no guaranty the ioen source ati drivers have greatly improved but if you need 3d support check to see if your chipset is supported with the closed drivers,  the sticky in this forum should help or this [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

Wifi thats a whole another thing not to familiar with it since it works for me (lucky that wifi chipset is support by default) but they improved the wifi connection you may need to install/edit some extra things to keep from having to reconnect or enter the password everytime you connect.

So at the end of the day you need ntfs-3g, totem-gstreamer's plugins, mplayer (for the browser plugin), closed source video driver (perhaps)

That's great - thanks for that cor2y!

The ntfs-3g sounds like it'll fix the automounting problem.

I didn't manually enable the multiverse/medibuntu repos - can you confirm that these aren't already enable automatically in Hardy? I ask because I do remember being asked if I want to download a whole batch of codecs and 'restricted' software (which I said yes to). I also installed VLC previously but that didn't work either.

As for the wifi - it's a Broadcom and it does work fine but I just have to manually enter the password every boot.

---

### Post by cor2y on 2008-05-20
Well if you use mplayer just installing the w32codecs with dvd libraries is enough.
However for the default media player totem you need all of the media plugins for multimedia playback.
Here are the needed gstreamer plugins
gstreamer0.10-ffmpeg (ffmpeg support)
gstreamer0.10-fluendo-mp3 (mp3 support/playback)
gstreamer0.10-pitfdll (to use the w32codec pack if installed)
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

Optional Plugins
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-fluendo-mpegmux

If you don't see some of these in synaptic you will need to enable the mulitverse, universe, and perhaps restricted repos, then reload
Also don't forget libdvdcss2, libdvdread libdvdnav for encrypted dvd playback
On the other hand if you don't want gstreamer theres totem-xine which requires these plugins for all mulitmedia playback
libxine1-ffmpeg
libxine1-gnome (if gnome)
libxine1-bin
libxine1-misc-plugins
libxine1-plugins
libxine1-x

---

### Post by MidBSD on 2008-05-22
> **cor2y said:**
> Well if you use mplayer just installing the w32codecs with dvd libraries is enough.
However for the default media player totem you need all of the media plugins for multimedia playback.
Here are the needed gstreamer plugins
gstreamer0.10-ffmpeg (ffmpeg support)
gstreamer0.10-fluendo-mp3 (mp3 support/playback)
gstreamer0.10-pitfdll (to use the w32codec pack if installed)
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

Optional Plugins
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-fluendo-mpegmux

If you don't see some of these in synaptic you will need to enable the mulitverse, universe, and perhaps restricted repos, then reload
Also don't forget libdvdcss2, libdvdread libdvdnav for encrypted dvd playback
On the other hand if you don't want gstreamer theres totem-xine which requires these plugins for all mulitmedia playback
libxine1-ffmpeg
libxine1-gnome (if gnome)
libxine1-bin
libxine1-misc-plugins
libxine1-plugins
libxine1-x

Thanks again Cor2y - It surprises me that they don't all use a common set of plugins - would save a lot of duplication.

---

