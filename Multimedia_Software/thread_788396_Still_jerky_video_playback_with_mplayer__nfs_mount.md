---
title: "Still jerky video playback with mplayer / nfs mounts"
date: 2008-05-09
forum: Multimedia Software
---

### Post by Farenji on 2008-05-09
A while ago (a week or so before the official release of 8.04) I opened a thread on this: [http://ubuntuforums.org/showthread.php?t=758138](http://ubuntuforums.org/showthread.php?t=758138) but I didn't get *any* replies. And now the thread has been closed... so I try again.

The problem is that video playback of files on a nfs disk in mplayer is really jerky - every few seconds the playback freezes for a split second. It's no fun at all to watch a video like this. Video from local disks is fine but not from nfs disks. Almost all my videos are on a big NAS which I access using nfs so this really is an issue for me.

This seems to be a kernel issue as when I boot from the 7.10 kernel (2.6.22), everything works fine. Without changing any settings. Booting back to 2.6.24 gives the same problem again.

I tried everything else, like different video codecs, different audio codecs, disabling sound altogether, enabling cache, none of it makes any difference whatsoever.

I even downloaded the kernel sources, checked the kernel settings, but I can't find any differences in multimedia or nfs settings between the 2 kernels. And I'm not a kernel developer so I'm a little bit lost.

Of course I just could keep on using the old kernel (which I'm doing - I have no other options at the moment) but this seems a bug to me. And I do want to use the latest kernel. I'm thinking of downgrading back to 7.10 as I didnt have any problems with that version but I like the new 8.04 features!!

Please help on how to resolve this or how to find the cause. Should I file some bug report somewhere? I am not sure where. Is this an ubuntu specific problem? Or is it related to the kernel itself? Any advise is appreciated.

---

### Post by jmarius on 2008-09-19
I'm not sure if you ever resolved your problem, but I might have a solution. I had the same problem, so I enabled the cache option in mplayer. By default, the cache is disabled. For me it worked with the default value of 2048, but I assume it will depend a lot on the content you're streaming across the network. HD would probably require a larger cache.

---

