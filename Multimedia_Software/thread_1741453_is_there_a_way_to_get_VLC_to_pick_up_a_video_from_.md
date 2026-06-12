---
title: "is there a way to get VLC to pick up a video from where you stopped it last.."
date: 2011-04-28
forum: Multimedia Software
---

### Post by shantiq on 2011-04-28
it might be simple but i have never been able to find this function on VLC

it is default on SMplayer and available on MoviePlayer though not default but i have looked around VLC carefully and see it nowhere

Maybe it simply is not there which is a shame as it is SO useful


Anyone knows?

---

### Post by mc4man on 2011-04-28
Only in a bit of a roundabout way. - maybe more useful in some specific instances than general use, though simple to do..
You'd need first to create a bookmark at that spot, playback > bookmarks (probably pause - then create is best
After the bookmark is created then you'd 'save playlist to file'. When doing so the bookmark(s) info will be stored in the playlist file
You can save multiple bookmarks if desired

To return then you'd open the playlist in vlc, then playback > bookmarks and choose


Edit: when saving a playlist - doesn't much matter what type you use (m3u or xfps format are good here), just make sure you add the appropriate  .ext to playlist name when saving

Ex. of a vid saved to .m3u  with one bookmark
```
#EXTM3U
#EXTINF:872,sintel.mp4
#EXTVLCOPT:bookmarks={name=sintel.mp40,bytes=14408302,time=114}
/home/doug/Videos/sintel.mp4
```

---

### Post by shantiq on 2011-04-28
thanx mc4 always a fount of knowledge excellent trick works really well


so no easy automatic one button option here.  VLC is so amazing it is always astounding to find that it is not God :KS


you would think they would have added that as a feature it is so handy for any film one watches

---

