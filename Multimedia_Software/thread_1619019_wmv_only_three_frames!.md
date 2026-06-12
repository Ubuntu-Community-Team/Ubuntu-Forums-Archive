---
title: "wmv only three frames?!"
date: 2010-11-11
forum: Multimedia Software
---

### Post by sigflup on 2010-11-11
I'm trying to convert this file: [http://hobones.dogsoft.net/hh.wmv](http://hobones.dogsoft.net/hh.wmv)

ffmpeg only decodes three frames. mplayer/mencoder and vlc crashes. What's with this file? how does an wmv become corrupted, that makes little sense to me? Is the rest of the movie recoverable? I've tried a windows-based re-indexer figuring it's windows bloody mux and maybe they have better support. I'm able to get the remaining frames but they look like trash... and I have to use windows so that's not good. :(

any help would be appreciated. Can you play that file?

I've tried mencoder/vlc on ppc and i32- both crash. :confused:

---

### Post by andrew.46 on 2010-11-11
Hi sigflup,

I downloaded your file and it looks hopelessly broken. The svn FFmpeg will not convert it and neither the svn MPlayer nor vlc-git will play it. I suspect you will need to trash this file unfortunately :(.

Andrew

---

