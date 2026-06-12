---
title: "Cli mplayer enable .a s s subtitle styling"
date: 2008-05-11
forum: Multimedia Software
---

### Post by CraymelCage on 2008-05-11
Hi Hi. I've been using mplayer in different variants gmplayer and smplayer. I got curious and started using the cli version of mplayer. I watch a lot of anime with .a s s/ssa subtitles in .mkv formats so mplayer was essential for me(don't even try suggesting vlc). I only have on problem at the moment. I can't get mplayer to play .a s s subtitles properly. It renders them in the default HUGE style mplayer has. I'm using 2:1.0~rc2-0ubuntu using the medibuntu package (I added the medibuntu repository). I already know how I can play them by using a gui based solution replacing cli mplayer. I just want to try using the cli version. Please be very specific when explaining how to fix my problem. It would be great if you could just give me instructions as though I have no prior knowledge of any thing dealing with the command line.

Thank you very much.

---

### Post by shirilover on 2008-05-12
Either add -a s s -embeddedfonts to your command line, without the obvious spaces; or,
add the following to ~/.mplayer/config
```

## Enable stylized subtitles
***=yes
embeddedfonts=yes

```

---

### Post by CraymelCage on 2008-05-12
Thank you so much it worked thank you. I actually tried to edit the config in mplayer before and it didn't work. Today I realized I was editing the config file for mplayer plugin instead... woops.:KS

---

