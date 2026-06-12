---
title: "[SOLVED] .avi files don't play"
date: 2008-09-27
forum: Multimedia Software
---

### Post by PoopyTheJ on 2008-09-27
I just had to reinstall my OS, and after getting my ATI driver back installed I installed xine and tried to play my avi files on my home directory. I cannot get them to play in either movie player or xine. In movie player I get a black screen although the progress bar moves and I hear sound I have no video. In Xine the screen is white, have sound and progress bar moves but no video. I've tried installing the gstreamer codecs, was prompted by movie player but no good. If anyone has any ideas I'd love to hear them. One wierd thing about my reinstall is after reinstalling and telling the installer to format the root partition I rebooted and my old desktop image was back with all my icons, and some of my programs remain seemingly in the system though I can't run any of them. I have my system setup with a / mount point and a home mount point on 2 separate partitions. Hope that helps and if anyone can point me in the correct direction I'd really appreciate it!

---

### Post by ajmorris on 2008-09-27
> **PoopyTheJ said:**
> I just had to reinstall my OS, and after getting my ATI driver back installed I installed xine and tried to play my avi files on my home directory. I cannot get them to play in either movie player or xine. In movie player I get a black screen although the progress bar moves and I hear sound I have no video. In Xine the screen is white, have sound and progress bar moves but no video. I've tried installing the gstreamer codecs, was prompted by movie player but no good. If anyone has any ideas I'd love to hear them. One wierd thing about my reinstall is after reinstalling and telling the installer to format the root partition I rebooted and my old desktop image was back with all my icons, and some of my programs remain seemingly in the system though I can't run any of them. I have my system setup with a / mount point and a home mount point on 2 separate partitions. Hope that helps and if anyone can point me in the correct direction I'd really appreciate it!

hi there,
you mentioned you installed the gstreamer codecs... have you run:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by PoopyTheJ on 2008-09-27
No I hadn't, how would I know to run that? I don't want to sound upset I'm just wondering is there something somewhere that would have told me to run it that I missed? Anyways running it now.

---

### Post by hansdown on 2008-09-27
Hi PoopTheJ.

One of the first things I do after a clean install, is go to [http://www.stchman.com/](http://www.stchman.com/)

---

### Post by PoopyTheJ on 2008-09-27
Ok ran that, took quite a while to finish, however after doing so still get the same results from attempting to play video. Is there so way to check and see what if anything I'm missing, like codec wise or, is it possibly something else?

---

### Post by PoopyTheJ on 2008-09-27
Restarted X everything is working fine. Thanks for the help!

---

### Post by ajmorris on 2008-09-27
> **PoopyTheJ said:**
> No I hadn't, how would I know to run that? I don't want to sound upset I'm just wondering is there something somewhere that would have told me to run it that I missed? Anyways running it now.

[https://wiki.ubuntu.com](https://wiki.ubuntu.com)  has some very useful info for things like this... i assume searching avi... or restricted codecs or something would yield results for knowing to run that command :)

AJ

---

