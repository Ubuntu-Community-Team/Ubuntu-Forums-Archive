---
title: "Songbird and WMA'S.. I don't have coreGStreamerSimple- Help!"
date: 2008-12-21
forum: Multimedia Software
---

### Post by d-d-d-d-d-d-card on 2008-12-21
Hi, after ages of trying to find it, I don't seem to have coreGStreamerSimple.jar (the file I need to edit in order to enable WMA support) anywhere on my computer, even though I have installed and have been running Songbird for months :S

So at the moment my music library is pretty useless :(

Could anyone perhaps send it to me or put it up on a file hosting site so I can put it into my Songbird installation or reccommend how I could get my hands on it?

Many thanks

---

### Post by cariboo on 2008-12-21
Make sure you have the ubuntu-restricted-extras meta package installed, as well as w32codec from the Medibuntu repositories.Go [here]("http://help.ubuntu.com/community/Medibuntu") to add the Medibuntu repositories. You may not be able to play some wma files because of drm. There are ways to get past drm, but I'll leave that up to you, it is just a simple goole search to find out how.

Jim

---

### Post by mc4man on 2008-12-21
> I don't seem to have coreGStreamerSimple.jar
That was a hack for much older versions of songbird. You should have no problem with .wma in songbird as long as mentioned not protected and not wma lossless.
Maybe upgrade to 1.0 release.
For wma lossless use Amarok, mplayer , maybe a few others, most xine based are good for lossless.

---

### Post by Foolishgrunt on 2008-12-31
> **mc4man said:**
> That was a hack for much older versions of songbird. You should have no problem with .wma in songbird as long as mentioned not protected and not wma lossless.
Maybe upgrade to 1.0 release.

Not quite true: [http://getsongbird.com/features/](http://getsongbird.com/features/)

The developers make no claim of supportng wma files on linux. And that doesn't make sense to me. I know I don't know the first thing about multimedia frameworks, but if I have wma playback enabled in Rhythmbox, shouldn't the files also work in Songbird? They both use Gstreamer.

---

