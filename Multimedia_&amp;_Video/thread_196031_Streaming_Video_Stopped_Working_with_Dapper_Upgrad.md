---
title: "Streaming Video Stopped Working with Dapper Upgrade"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by BitWitty on 2006-06-13
I recently upgraded from Breezy to Dapper and I was no longer able to watch streaming videos on cnn.com, youtube.com, video.google.com, etc. I was finally able to trace the problem to the version of Firefox that came with Ubuntu 6.06. When I was running Breezy, I had installed Firefox 1.5 in a separate directory and managed to get everything working. But when I upgraded to Dapper, Firefox 1.5 was installed by default so I got rid of my other 1.5 installation. That's when I noticed I was no longer able to play streaming video from any of the usual sites. I downloaded and installed Firefox 1.5.04 in a separate directory and created symbolic links to all of the plugins in the /usr/lib/firefox/plugins directory and viola! Everything works again. Since the plugins are symbolic links to the plugins in the Ubuntu version of firefox, it's obviously the browser and not the plugins. Has anybody else had this problem?

---

