---
title: "Montlhly Backup NAS - how to only copy changed files and remove deleted"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by ggerri on 2010-02-22
Hi there :popcorn:

I have a 1TB ReadyNAS which I want to backup monthly on an external drive. I actually only want to copy changed files and have the ones removed, I've deleted on the NAS since the last backup. Nautilus doesnt allow 'overwrite only older files'. 

I dont want a backup program, which packs or stores the files in a proprietary format. Just want a nice copy :D

At the moment, I first clear the external disk and then copy all the files, which is kind of arrggghhh (copy time is about 15h)

Saw in the forum that synkron, grsync, backintime are recomended. Which one is would be the best for my needs?

Any help appreciated :-)

Gerald

---

### Post by dargaud on 2010-02-22
```
rsync -va --delete .../SourceDir/ .../DestDir/
```

---

### Post by ggerri on 2010-02-22
thanks dargaud, I'm still a beginner at the console, but will give it a try ;-) can you recommend grsync?

---

