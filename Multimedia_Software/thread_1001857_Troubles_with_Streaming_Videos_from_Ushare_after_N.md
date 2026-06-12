---
title: "Troubles with Streaming Videos from Ushare after New Xbox Experience update"
date: 2008-12-04
forum: Multimedia Software
---

### Post by dryicebomb on 2008-12-04
Hello, I was wondering if someone here can help me, i'm running Ubuntu 8.04 with ushare 1.1a I have been using it to stream videos to my xbox for the last 9 months without a hitch. However after the NXE update on my xbox it will no longer play any of my videos. It connects to ushare fine, and it sees all the videos in the share file, but says that it is an incompatible format. All the videos are .AVI Also please keep in mind that these same videos played just fine prior to the update. Is there a different format I need to re-encode all my videos to now? Is anybody else having the same trouble or is it just coincidence for me?

I would greatly appreciate any help

Thanks

---

### Post by timcredible on 2008-12-04
can you try copying a file to your linux machine, see if plays directly?  if not, then maybe the xbox has re-encoded all the files with the update.  if yes, then maybe the xbox won't send a plain .avi file, but is re-encoding it on the fly to make it so that only windows machines can decode them.

---

### Post by dryicebomb on 2008-12-04
Hi timcredible, 

Thanks for the response. 
The linux machine that runs ushare can play the videos fine using either vlc or mplayer. The videos in question are saved on said linux machine and it is the xbox that can no longer play the videos. 

any other thoughts?

thanks again.

---

### Post by viashimo on 2008-12-04
I have not had any issues playing .avi files on my xbox after the update. All I can suggest is restarting ushare. I am not sure which codec my .avi s use.

---

### Post by dryicebomb on 2008-12-10
Solved.

So the solution turned out to be quite easy, but something that took me a while to try. There was never anything wrong with ushare or the ubuntu machine that it was running on. All I had to do to fix this trouble is re-download the avi codec on the xbox. After that, all the videos worked again.

Thank you to everyone who helped me here.

---

