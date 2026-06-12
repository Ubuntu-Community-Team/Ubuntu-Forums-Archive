---
title: "Mythbuntu not working"
date: 2013-02-16
forum: Mythbuntu
---

### Post by chewyboy000 on 2013-02-16
Whenever I try to select Mythbuntu from wubi and click install it says Cannot download metalink and therefore the iso. Here is where the error is:02-16 19:01 DEBUG  TaskList: ## Finished copy_installation_files
02-16 19:01 DEBUG  TaskList: ## Running get_iso...
02-16 19:01 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-16 19:01 DEBUG  TaskList: New task get_metalink
02-16 19:01 DEBUG  TaskList: ### Running get_metalink...
02-16 19:01 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/mythbuntu/releases/12.10/release/mythbuntu-12.10-desktop-amd64.metalink](http://cdimage.ubuntu.com/mythbuntu/releases/12.10/release/mythbuntu-12.10-desktop-amd64.metalink) > C:\ubuntu\install
02-16 19:01 ERROR  CommonBackend: Cannot download metalink file [http://cdimage.ubuntu.com/mythbuntu/releases/12.10/release/mythbuntu-12.10-desktop-amd64.metalink](http://cdimage.ubuntu.com/mythbuntu/releases/12.10/release/mythbuntu-12.10-desktop-amd64.metalink) err=[Errno 14] HTTP Error 404: Not Found
02-16 19:01 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/mythbuntu/daily-live/current/quantal-desktop-amd64.metalink](http://cdimage.ubuntu.com/mythbuntu/daily-live/current/quantal-desktop-amd64.metalink) > C:\ubuntu\install
02-16 19:01 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/mythbuntu/daily-live/current/quantal-desktop-amd64.metalink](http://cdimage.ubuntu.com/mythbuntu/daily-live/current/quantal-desktop-amd64.metalink) err=[Errno 14] HTTP Error 404: Not Found
02-16 19:01 DEBUG  TaskList: ### Finished get_metalink
02-16 19:01 ERROR  TaskList: Cannot download the metalink and therefore the ISO

---

### Post by Bucky Ball on 2013-02-16
*Thread moved to **Mythbuntu**.*

---

### Post by PhilWig on 2013-02-18
Have you tried  
[http://www.mythbuntu.org/downloads](http://www.mythbuntu.org/downloads)
Download, burn ISO to CD, boot from it?    Sorry if I am missing your point.
Phil

---

### Post by bcbc on 2013-02-19
It doesn't look like there is a 12.10 release of Mythbuntu. If you want to use Wubi, try the 12.04.2 version here: [http://releases.ubuntu.com/12.04/wubi.exe](http://releases.ubuntu.com/12.04/wubi.exe)

But, I don't expect many people are running Mythbuntu using Wubi.

---

### Post by Bucky Ball on 2013-02-19
> **bcbc said:**
> 
But, I don't expect many people are running Mythbuntu using Wubi.

! +1. If any ...

---

