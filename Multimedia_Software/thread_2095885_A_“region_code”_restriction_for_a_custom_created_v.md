---
title: "A “region code” restriction for a custom created video DVD file"
date: 2012-12-18
forum: Multimedia Software
---

### Post by petar katsarov on 2012-12-18
[LEFT][COLOR=#000000][FONT=Arial]I want to create a video DVD (no menus, just "plug and play") from a few video files. I'm doing it like this:
[/FONT][/COLOR][/LEFT]
```
ffmpeg -i sample-media/hellboy-2.wmv -y -target ntsc-dvd sample-media-to-mpeg/hellboy-2.vob
dvdauthor -o sample-dvd -x dvdauthor-settings.xml
mkisofs -dvd-video -o hellboy-2-trailers.iso sample-dvd/
```[LEFT][COLOR=#000000][FONT=Arial]Where "dvdauthor-settings.xml" is:
[/FONT][/COLOR][/LEFT]
[HTML]<dvdauthor>
  <vmgm>
    <menus>
      <video format="ntsc" />
    </menus>
  </vmgm>
  <titleset>
    <titles>
      <pgc>
        <vob file="sample-media-to-mpeg/hellboy-2.vob" />
      </pgc>
    </titles>
  </titleset>
</dvdauthor>[/HTML][LEFT][COLOR=#000000][FONT=Arial]But when I try to play the iso file, no video play wants to play it.

Can someone tell me what I'm doing wrong?
[/FONT][/COLOR][/LEFT]

---

