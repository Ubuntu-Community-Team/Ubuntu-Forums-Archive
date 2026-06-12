---
title: "Mediaserver from NAS"
date: 2010-10-09
forum: Mythbuntu
---

### Post by brononi on 2010-10-09
Hey,

I've got a small NAS that runs a kind of mediaserver. So all my movies/music/pictures... are on here.
I know want to use Mythbuntu as a mediaplayer on my tv-screen.

How can i 'browse' the NAS so i can playback the movies on Mythbuntu?

---

### Post by mymythtv on 2010-10-11
Hi

My first guess would be to enable NFS on the NAS, configure them for export and then mount the NFS-shares on the mythbuntu BE/FE. You should now be able to configure mythtv to read from the shares..
Can't remember setup places off my head as I havn't tried it, but the shares end up just as directories, so....

Quick tutorial for NFS could be found here.
[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+mount+command](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+mount+command)

---

