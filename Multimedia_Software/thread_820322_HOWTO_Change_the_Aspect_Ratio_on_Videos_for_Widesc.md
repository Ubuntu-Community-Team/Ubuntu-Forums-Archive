---
title: "HOWTO: Change the Aspect Ratio on Videos for Widescreen Monitors"
date: 2008-06-06
forum: Multimedia Software
---

### Post by Cappy on 2008-06-06
[SIZE="4"]Mplayer:[/SIZE]

Run
```
gedit ~/.mplayer/config
```
and add the line
```
aspect="16:10"
```
or whatever your desired aspect ratio is (This will strech the image)

**MPlayers's command line options:**
```
gmplayer -aspect 16:10 /path/to/media
```

[SIZE="4"]VLC:[/SIZE]

Go to Settings-->Preferences-->Video (Tab)-->Scroll Down to the bottom

At the "Source aspect ratio" field you can enter in your desired aspect ratio, e.g.
```
16:10
```
(This will strech the image)

To crop the image in VLC so that the sides are cut off but the image is not streched use the "Video cropping" field instead.

**VLC's command line options:**
```

--aspect-ratio 16:10

```
and
```

--crop 16:10

```

[SIZE="4"]Totem:[/SIZE]

Doesn't seem possible.

---

### Post by sstusick on 2008-08-09
Perfect! 

Thanks!

---

