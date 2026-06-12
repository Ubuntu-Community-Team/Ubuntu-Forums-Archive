---
title: "How to play WMA 10 files with DRM encryption?"
date: 2009-10-02
forum: Multimedia Software
---

### Post by ToshibaLaptoplinux on 2009-10-02
Is it possible to play WMA 10 files with DRM encryption in Ubuntu/Linux?

I transferred some files from my old WinXP PC and can't play them in either VLC or MPlayer.

In VLC the time ticks and it appears to be playing but there is no sound and there isn't any error. In MPlayer it throws the error "file encumbered with DRM encryption MPlayer can not play this file"

When I "file" any of the tracks it returns "Microsoft ASF".

I am really hoping that I won't be forced to use Windows Media Player under wine (is that even possible?) because I am trying to wean myself off of windows and its applications.

Thanks.

---

### Post by bumanie on 2009-10-02
Go to [medibuntu]("https://help.ubuntu.com/community/Medibuntu") and follow the instructions. Alternatively go to the [Canonical shop]("http://shop.canonical.com/index.php?cPath=19&osCsid=60f6d0789028db1475a328f33494826d") and purchase codecs.

---

### Post by ToshibaLaptoplinux on 2009-10-02
> **bumanie said:**
> Go to [medibuntu]("https://help.ubuntu.com/community/Medibuntu") and follow the instructions. Alternatively go to the [Canonical shop]("http://shop.canonical.com/index.php?cPath=19&osCsid=60f6d0789028db1475a328f33494826d") and purchase codecs.

Thank you for the reply. The first place I checked before posting my original question was Medibuntu. I installed both the non-free-codecs and the win32codecs and I was still unable to play the media in question. Ar e these codecs suppose to be able to play wma10 drm encoded media?

I took a quick look at the commercial Fluendo codecs pack you referenced as well. It looks promising but the one review I found indicates that it "may or may not" be able to play DRM media. Do you have any idea if this is the case or not?

I saw on the Microsoft website that there is a way to transfer a license on DRM content but because I am using Linux/Firefox I can't get past the initial dialogue. [http://go.microsoft.com/fwlink/?prd=816&pver=7.1&sbp=DRM&plcid=0x409&clcid=0x409&ar=PersonalV2](http://go.microsoft.com/fwlink/?prd=816&pver=7.1&sbp=DRM&plcid=0x409&clcid=0x409&ar=PersonalV2)

Can anybody definitively say whether or not Ubuntu/Linux can play DRM media or can not. It doesn't matter to me if it is commercial or not.

Also is it possible to run WMP10 under wine and then play them? That would be my last choice but if it is the only way...

---

### Post by mc4man on 2009-10-02
If you're using a repo or ppa vlc then you won't get playback of wma3 (Windows Media Audio 10 Professional) whether drm or not, so your only choice would be mplayer which will not playback

I don't have any protected wma's to test on vlc though I'm fairly sure it won't either.

for wmp10 in wine maybe thru winetricks, here's the wine appdb page on, ratings are mixed
[http://appdb.winehq.org/appview.php?iVersionId=3212](http://appdb.winehq.org/appview.php?iVersionId=3212)

Note that the fluendo codecs are only good for gstreamer players

Edit:
created a protected wma on vista, no playback possible in linux

---

