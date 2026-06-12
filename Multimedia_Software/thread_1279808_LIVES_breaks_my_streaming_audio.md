---
title: "LIVES breaks my streaming audio"
date: 2009-10-01
forum: Multimedia Software
---

### Post by blues2use on 2009-10-01
I installed LIVES from a .deb package without problems or dependency errors. I tried it, didn't care for it and removed it using the following:

bob@ubuntu:~$ sudo apt-get remove lives
[sudo] password for bob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dvgrab libtheora-bin libsox-fmt-ffmpeg libsox-fmt-all icedax libgdk-pixbuf2
  libsox-fmt-mp3 dirac
Use 'apt-get autoremove' to remove them.

I was listening to a radio stream when I ran the autoremove command and the streaming audio stopped immediately...closed Firefox, logged out and back in, started Firefox and radio stream...nothing...rebooted the system...still no streaming...checked in Synaptic for broken packages...nothing...I reinstalled LIVES and streaming audio is working again.

What do I need to do to remove LIVES and not break streaming audio?

Your help is most appreciated

Thanks

---

### Post by blues2use on 2009-10-01
> **blues2use said:**
> I installed LIVES from a .deb package without problems or dependency errors. I tried it, didn't care for it and removed it using the following:

bob@ubuntu:~$ sudo apt-get remove lives
[sudo] password for bob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dvgrab libtheora-bin libsox-fmt-ffmpeg libsox-fmt-all icedax libgdk-pixbuf2
  libsox-fmt-mp3 dirac
Use 'apt-get autoremove' to remove them.

I was listening to a radio stream when I ran the autoremove command and the streaming audio stopped immediately...closed Firefox, logged out and back in, started Firefox and radio stream...nothing...rebooted the system...still no streaming...checked in Synaptic for broken packages...nothing...I reinstalled LIVES and streaming audio is working again.

What do I need to do to remove LIVES and not break streaming audio?

Your help is most appreciated

Thanks

Here's what I did:

I autoremoved the packages first and that, in turn, automatically removed lives...no streaming audio problems now...maybe this will help someone else... I have no idea why this worked and the other method did not.

---

