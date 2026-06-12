---
title: "rsync and gopher or map gopher drive"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by dreaminhere on 2010-06-20
I've been browsing gopher sites and have a list of files I want to download.  Is it possible to rsync a gopher site or to map a gopher site as a network drive so I can rsync it?
What would be the best way to download those files without right click>save on each one.

---

### Post by dreaminhere on 2010-06-21
bump

---

### Post by dreaminhere on 2010-06-23
anyone have any idea or is this the wrong forum?

---

### Post by dreaminhere on 2010-06-25
bump3

---

### Post by dreaminhere on 2010-07-03
I found a way to do what I wanted to do. I was trying to rsync the repository on something other than port 80.  You can do this by rsync -r -t -v --progress --delete rsync://mirror.aarnet.edu.au/ubuntu/archive/dists/lucid /DESTINATION/

---

