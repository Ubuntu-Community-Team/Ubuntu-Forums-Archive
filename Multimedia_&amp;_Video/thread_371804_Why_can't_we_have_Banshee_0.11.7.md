---
title: "Why can't we have Banshee 0.11.7?"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by karl_forshaw on 2007-02-27
Hi guys, 

Does anyone know why the Banshee in the Ubuntu Repositories is something like 5 versions old?
I've been testing Feisty on my other machine and I loved the new version of Banshee especially with the podcast plugin!!

Please please please, can somebody make a repository for this? I tried compiling from source but synaptic wont allow me to install the dbus1-dev package (says broken dependencies).

Has anyone got this version of Banshee running on edgy?

Thanks a lot guys

Karl

---

### Post by Bad Seed on 2007-03-01
> **karl_forshaw said:**
> Please please please, can somebody make a repository for this? I tried compiling from source but synaptic wont allow me to install the dbus1-dev package (says broken dependencies).
I'm using this repo on Edgy: [http://directhex.mfgames.com/]("http://directhex.mfgames.com/"), it has Banshee 0.11.7 and recent versions of the Mono framework.

Cheers.

---

### Post by karl_forshaw on 2007-03-02
Thank you very, very much dude. :guitar:

---

### Post by Bad Seed on 2007-03-02
You're welcome karl_forshaw :wink:[]("http://ubuntuforums.org/member.php?u=183466")

---

### Post by 6205 on 2007-03-10
Hmm....I have tried this repo on my Edgy, but i updated only mono framework + f-spot...
Banshee 0.11.7 won't install due depency problems.....frak :-(  any suggestions PLEASE ?

banshee:
  Depends on: libdbus-1-2 (>=0.60) but it is not installable
  Depends on: libnautilus-burn3  but it is not installable
  Depends on: libipoddevice0 (>=0.5.2) ale bude sa inštalova&#357; 0.5.1-0ubuntu1
  Depends on: libnautilus-burn3  but it is not installable

---

### Post by karl_forshaw on 2007-03-10
I had no success with this repo in Edgy either, but I compiled the newest Banshee from source with help from this thread.. See the last few posts.

[http://ubuntuforums.org/showthread.php?t=329260&page=6](http://ubuntuforums.org/showthread.php?t=329260&page=6)

---

### Post by Bad Seed on 2007-03-10
> **6205 said:**
> Hmm....I have tried this repo on my Edgy, but i updated only mono framework + f-spot...
Banshee 0.11.7 won't install due depency problems.....frak :-(  any suggestions PLEASE ?

banshee:
  Depends on: libdbus-1-2 (>=0.60) but it is not installable
  Depends on: libnautilus-burn3  but it is not installable
  Depends on: libipoddevice0 (>=0.5.2) ale bude sa in&#353;talova&#357; 0.5.1-0ubuntu1
  Depends on: libnautilus-burn3  but it is not installable
Fortunately I haven't had any problem with that repo. But I made a .deb from 0.12 source code, maybe you want to give it a try: [http://rapidshare.com/files/20341620/banshee_0.12.0-1_i386.deb]("http://rapidshare.com/files/20341620/banshee_0.12.0-1_i386.deb").

Cheers.

Mirror: [http://uploaded.to/?id=nxsaz4]("http://uploaded.to/?id=nxsaz4")

---

### Post by 6205 on 2007-03-10
Too many users downloading right now. Please try again in two minutes :confused: 

Hmm......I will try it as soon as possible :popcorn:

---

### Post by 6205 on 2007-03-10
> **Bad Seed said:**
> Fortunately I haven't had any problem with that repo. But I made a .deb from 0.12 source code, maybe you want to give it a try: [http://rapidshare.com/files/20341620/banshee_0.12.0-1_i386.deb]("http://rapidshare.com/files/20341620/banshee_0.12.0-1_i386.deb").

Cheers.

:lolflag:  IT'S WORKING !!!! THANKS DUDE !!! :guitar:

---

### Post by Bad Seed on 2007-03-10
> **6205 said:**
> :lolflag:  IT'S WORKING !!!! THANKS DUDE !!! :guitar:
Sometimes it's hard to download from Rapidshare :(. I'm glad to see it's working for you :mrgreen:

---

### Post by isecore on 2007-03-18
> **Bad Seed said:**
> Fortunately I haven't had any problem with that repo. But I made a .deb from 0.12 source code, maybe you want to give it a try: [http://rapidshare.com/files/20341620/banshee_0.12.0-1_i386.deb]("http://rapidshare.com/files/20341620/banshee_0.12.0-1_i386.deb").

Cheers.

Excellent work! Worked fine for me, when Rapidshare finally stopped being d***heads about everything.

EDIT: However, you should update its dependencies. When I installed your .deb it replaced the one in the Ubuntu repos, and all of a sudden the packages that the Ubuntu-version depended on were marked as "no longer in use" and without thinking I removed them - and discovered that Banshee of course crashed on startup since the libraries were gone. Reinstall of Ubuntu-version, reinstall of your .deb and everything was back to normal, but you might want to look into that.

---

### Post by Bad Seed on 2007-03-18
Hi again. I uploaded the deb file to Uploaded.to for those who are having problems downloading from Rapidshare.

The link is in my original post.

---

