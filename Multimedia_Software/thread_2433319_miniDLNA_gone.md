---
title: "miniDLNA gone?"
date: 2019-12-17
forum: Multimedia Software
---

### Post by johnnymcc on 2019-12-17
I'm using 18.04.3 server.  I'm trying to install miniDLNA but the package "minidlna" seems to be gone.  I found a .deb file but the dependencies are not there.  I found a site that showed using a new repo but adding that repo resulted in some messages that lead me to believe this was a bad thing to do.  I also tried snap for the first time with a snap version of miniDLNA, but I couldn't get that working and reading more about it suggested I probably never would.

I know I installed this just a few months ago on the same machine with the same version of Ubuntu Server, but I don't remember if I added a repo or not.  I reformatted it to try Open Media Vault, where miniDLNA worked great but getting nginx to work was a nightmare so I came back to Ubuntu server where I installed from the same USB stick that I used before.   

To be specific I do:  "sudo apt-get install minidlna" and I get :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package minidlna

Am I missing something?  Is there something else I need to do?

Thanks!

---

### Post by CatKiller on 2019-12-17
It's in the Universe repository.

---

### Post by ajgreeny on 2019-12-17
Seems to be a bug in the server version of 18.04.1 (see [https://askubuntu.com/questions/1081243/why-do-i-need-to-enable-universe-repo-in-18-04-isnt-it-default-enabled](https://askubuntu.com/questions/1081243/why-do-i-need-to-enable-universe-repo-in-18-04-isnt-it-default-enabled)) so perhaps it's a bug also in the 18.04.3 installer that leaves the Universe repos disabled.

I've never used a server iso, only a full GUI version of Xubuntu, but on all GUI versions the Universe repos are enabled by default.

---

### Post by johnnymcc on 2019-12-17
Thanks, universe repo seems to work.  I think I remember something about this now from before.  The problem is aggravated by an aging brain.

---

