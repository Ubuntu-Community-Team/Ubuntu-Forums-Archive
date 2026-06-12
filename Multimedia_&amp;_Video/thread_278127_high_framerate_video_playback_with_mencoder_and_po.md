---
title: "high framerate video playback with mencoder and pocket divx player on symbian phones"
date: 2006-10-15
forum: Multimedia &amp; Video
---

### Post by nbcthreat on 2006-10-15
Recently, divx.com released a mobile divx player that appears to play high-framerate (30 fps ish) video on new AND old symbian devices. I tested this on my Nokia 6682. (available free with Cingular contract from nokiausa.com) I had tried a few conversion methods, but couldn't quite get the same level of high-framerate playback as the sample files on the mobile.divx.com site, but today I figured out the settings for mencoder for almost-perfect encoding. This is a very big deal. It means high-framerate playback of downloaded video is now possible on your old (or new) nokia smartphone. Now I have NO need for the ipod. Here's the mencoder command I used to make this work. You can download the client for you symbian phone from mobile.divx.com. Clients are available for the latest Symbian S60v3 phones (N-series, E-series) and other phones as well. Check mobile.divx.com to see if they have a client for your smartphone. The client is free. By the way, encoding is VERY fast. Takes only about 5 minutes to encode a single 40-minute episode to disk on my Pentium 4.

I encoded this directly to the 512MB RS-MMC card that I have for my Nokia 6682.

```
mencoder Angel\ -\ 5x13\ -\ Why\ We\ Fight.avi -ovc lavc -oac mp3lame -lavcopts vbitrate=128 -lameopts abr=64 -vf scale=320:176,crop=208:176 -ffourcc DIVX -o /media/usbdisk/5x13.avi
```

---

### Post by nbcthreat on 2006-10-24
Oh, by the way. This doesn't work. I tried for quite a while to get the audio and video to sync up and it never worked. I DID, however, find a solution. The beta for TCPMP works brilliantly on Symbian S60v2 phones, like my Nokia 6682 (and almost all nokia smartphones sold in north America). Just shrink the file to the right resoltuion, copy to a video card and play.

Here's the mencoder line I use.

```
mencoder How.I.Met.Your.Mother.S01E20.HDTV.XviD-LOL.avi -ovc lavc -oac copy -lavcopts vbitrate=512 -vf scale=320:176,crop=208:176 -ffourcc DIVX -o /media/usbdisk/1x20.avi
```

Here's the install file for your phone.

[http://www.symbian-freak.com/forum/viewtopic.php?p=86856&s=phpBBmobile](http://www.symbian-freak.com/forum/viewtopic.php?p=86856&s=phpBBmobile)

---

