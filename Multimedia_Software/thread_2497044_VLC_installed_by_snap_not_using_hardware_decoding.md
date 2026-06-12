---
title: "VLC installed by snap not using hardware decoding"
date: 2024-04-21
forum: Multimedia Software
---

### Post by kzip on 2024-04-21
Hi,

I recently installed Ubuntu 22.04 and while almost everything worked out the box (great job!) I had some issues playing 4k video with VLC. The video was stuttering and unwatchable.

After spending some time searching various forums / websites I found the following thread from 1 year ago on Reddit:  [https://www.reddit.com/r/Ubuntu/comments/144y0he/vlc_does_not_do_hardward_decoding/](https://www.reddit.com/r/Ubuntu/comments/144y0he/vlc_does_not_do_hardward_decoding/)

Although they were discussing Ubuntu 23.04 they mention having the same issue with VLC installed by Ubuntu Software (the snap install) in that hardware decoding doesn't work. 
They recommended installing the Flatpak version instead. So I did that and it worked 100%, the 4k video playback in VLC from Flatpak was perfect. 
I'm not saying that the root cause is the same issue, it probably isn't, but it does appear that the VLC snap on 22.04 doesn't correctly use hardware video decoding.

Just thought I'd mention this for anyone else having issues - I'm not sure if this will still be a problem in the upcoming 24.04 release or not.

---

