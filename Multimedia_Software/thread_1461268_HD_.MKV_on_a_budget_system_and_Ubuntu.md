---
title: "HD .MKV on a budget system and Ubuntu"
date: 2010-04-24
forum: Multimedia Software
---

### Post by Stigmata13 on 2010-04-24
Hello. I'm a novice Ubuntu user, and I have a problem. I have an anime series (about 24 episodes, each 325-350 megabytes each) encoded in .mkv format, high quality (1280x720). It took quite some time to download this series, however no matter what I do, I cannot get the files to play correctly under Ubuntu. I have tried several different media players, including VLC, Movie player, and Mplayer, and none work correctly. VLC will play the first 15-20 seconds fine, and then stop the video and go back to the beginning. I however, do realize that my laptop isn't high-spec, and isn't really built for HD video playback (1.6ghz single core athlon CPU, 4 gigs of ram, integrated radeon x1250 graphics chip.)
So my question is, does anyone know a way I can play these files on my system and have them play correctly? (Without lag or stuttering?) Also the anime is subtitled, so I would want to make sure the subs work correctly, and preferably have the audio in sync with the video. I would also have no objections against converting it to a friendly .avi format, but I have tried a couple programs already, and either it doesn't work, or it says it will take 18+ hours per episode, which really isn't an option for me.
Any advice anyone can give would be greatly appreciated! Thanks in advance!

---

### Post by kerry_s on 2010-04-24
gnome-mplayer with some mplayer settings. see pic
```

-nodouble -lavdopts skipframe=nonref:skiploopfilter=all

```

if thats not enough you might want to try the rt kernel(linux-image-rt)

works for me on my system "atom 230 1.6ghz 1gb ram", watched that 1080p hd ghost in the shell innocence mkv just the other day.

---

### Post by Stigmata13 on 2010-04-24
Thank you so much! I gave it a shot, and it worked, beautifully. I'm so glad I didn't have to resort to windows for this ;).

---

