---
title: "Unable to play DVDs on XBMC"
date: 2010-08-30
forum: Multimedia Software
---

### Post by luisito on 2010-08-30
I regularly use XBMC on my htpc. Everything seems to work just fine except that I cannot watch DVDs with it. It just never detects a DVD. If I insert a DVD with XBMC running, it just lets me browse the files. If I select the video files it plays some of them (depending on the DVD apparently). If I click on the play button it says that no disk is detected. There is nothing that I can see in the log file and seems relevant. I really don't know what to do.

The computer is an HP z555. I just modified it by adding more ram and I changed the video card for an NVIDIA 8400GS. It is running Ubuntu Lucid and XBMC 9.11 installed from the PPA repository.

The dvds play well with totem, vlc and mplayer

---

### Post by gcastell on 2010-10-20
> **luisito said:**
> I regularly use XBMC on my htpc. Everything seems to work just fine except that I cannot watch DVDs with it. It just never detects a DVD. If I insert a DVD with XBMC running, it just lets me browse the files. If I select the video files it plays some of them (depending on the DVD apparently). If I click on the play button it says that no disk is detected. There is nothing that I can see in the log file and seems relevant. I really don't know what to do.

The computer is an HP z555. I just modified it by adding more ram and I changed the video card for an NVIDIA 8400GS. It is running Ubuntu Lucid and XBMC 9.11 installed from the PPA repository.

The dvds play well with totem, vlc and mplayer

I have the same problem with Kubuntu 10.10 and XBMC. Where you able to solve it?

---

### Post by luisito on 2010-10-23
No. I wasn't. I haven't tried it on 10.10 yet.

---

### Post by perspectoff on 2010-10-23
* You can install libdvdcss2 as a 64-bit .deb package without installing the Medibuntu repositories: 

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb

    or a 32-bit .deb package: 

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_i386.deb


for more info see:

[http://ubuntuguide.org/wiki/Ubuntu:All#DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:All#DVD_Playback_Capability)

or

[http://kubuntuguide.org/All#DVD_Playback_Capability](http://kubuntuguide.org/All#DVD_Playback_Capability)

---

### Post by luisito on 2010-10-23
I've always had libdvdcss2 installed from the medibuntu repositories. In fact, I don't think dvds would play on totem otherwise.

---

