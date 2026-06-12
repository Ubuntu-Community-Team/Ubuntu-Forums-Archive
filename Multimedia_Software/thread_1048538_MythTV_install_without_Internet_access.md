---
title: "MythTV install without Internet access"
date: 2009-01-23
forum: Multimedia Software
---

### Post by canadianwriterman on 2009-01-23
I have a friend who is running Intrepid, but does not currently have Internet access. He has a TV tuner and would like to install MythTV. Is there a single .deb file that I can download for him, save onto a USB and give to him to install from? I suspect that it may not be as simple as that, but I'm not familiar with MythTV myself. Thanks for your help.

---

### Post by sully101 on 2009-01-23
> **canadianwriterman said:**
> I have a friend who is running Intrepid, but does not currently have Internet access. He has a TV tuner and would like to install MythTV. Is there a single .deb file that I can download for him, save onto a USB and give to him to install from? I suspect that it may not be as simple as that, but I'm not familiar with MythTV myself. Thanks for your help.

One way would be to download a mythbuntu cd and use the packages off that to install mythtv on your friends computer. the other option would be to open synaptic package manager and search for "mythtv" which is a meta package click on mark for installation then File > generate package download script. will give you a script that will download the all the *.debs. Save the file as mythtv.sh

```
mkdir ~/mythtvdownloads
cd ~/mythtvdownloads
~/mythtv.sh

```

---

### Post by canadianwriterman on 2009-01-26
Thanks for your help, sully101.

---

### Post by canadianwriterman on 2009-01-26
One other question, sully101. After following your process and then hitting "Apply," there is the option to "download package files only." Do I select that? Thanks.

---

### Post by sully101 on 2009-01-27
No you are only using Synaptic package manager to generate the script to download the files your friend needs. In fact now that I think about it your friend should create the script on their computer. Then transfer it to yours and execute it to download the files. Then you can copy them onto a usb stick or cd and install them on the computer without internet acess.

---

### Post by sully101 on 2009-01-27
> **canadianwriterman said:**
> Thanks for your help, sully101.

Here is the script. Copy and paste it into a new text document

```

#!/bin/sh
wget -c http://archive.ubuntu.com/ubuntu/pool/main/g/gawk/gawk_3.1.6.dfsg-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.67-0ubuntu6_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/libn/libnet-daemon-perl/libnet-daemon-perl_0.38-1.1_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/libp/libplrpc-perl/libplrpc-perl_0.2017-1.1_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/libd/libdbi-perl/libdbi-perl_1.605-1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.67-0ubuntu6_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/libd/libdbd-mysql-perl/libdbd-mysql-perl_4.007-1build1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-client-5.0_5.0.67-0ubuntu6_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server-5.0_5.0.67-0ubuntu6_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-client_5.0.67-0ubuntu6_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/mythtv-common_0.21.0+fixes18722-0ubuntu1_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/mythtv-database_0.21.0+fixes18722-0ubuntu1_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0_1.5.10-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/libf/libfreebob/libfreebob0_1.0.11-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/libjack0_0.109.2-3ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/libmp3lame0_3.98-0.0_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/f/faac/libfaac0_1.26-0.1ubuntu2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/f/faad2/libfaad0_2.6.1-3.1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-b-5ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/x/x264/libx264-59_0.svn20080408-0.0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu3_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/libx/libxvmc/libxvmc1_1.0.4-2ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/q/qt-x11-free/libqt3-mt-mysql_3.3.8-b-5ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/libmyth-0.21-0_0.21.0+fixes18722-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/mythtv-frontend_0.21.0+fixes18722-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/libf/libfame/libfame-0.9_0.9.1-0.2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/l/lzo/liblzo1_1.08-3_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.0.2+debian-2build2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mjpegtools/libmjpegtools0c2a_1.8.0-0.2ubuntu5_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/p/pvm/libpvm3_3.4.5-11_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/transcode_1.0.2-0.8ubuntu10_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/mythtv-transcode-utils_0.21.0+fixes18722-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/libn/libnet-upnp-perl/libnet-upnp-perl_1.2.4-1~intrepid1_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/libmyth-perl_0.21.0+fixes18722-0ubuntu1_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/mythtv-backend_0.21.0+fixes18722-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/mythtv_0.21.0+fixes18722-0ubuntu1_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/s/sox/libsox0_14.0.1-2build2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/s/sox/libsox-fmt-alsa_14.0.1-2build2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/s/sox/libsox-fmt-base_14.0.1-2build2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mjpegtools/mjpegtools_1.8.0-0.2ubuntu5_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-server_5.0.67-0ubuntu6_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv-theme-blootube/mythtv-theme-blootube_0.21.0-0ubuntu1_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv-theme-blootube-osd/mythtv-theme-blootube-osd_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv-theme-blootube-wide/mythtv-theme-blootube-wide_0.21.0-0ubuntu1_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv-theme-blootubelite-wide/mythtv-theme-blootubelite-wide_0.21.0-0ubuntu1_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv-theme-glass-wide/mythtv-theme-glass-wide_0.20080908-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/mythtv-theme-gray-osd_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/mythtv-theme-isthmus_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/mythtv-theme-iulius_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/mythtv-theme-iulius-osd_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/mythtv-theme-minimalist-wide_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv-theme-projectgrayhem/mythtv-theme-projectgrayhem_0.21.0-0ubuntu1_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv-theme-projectgrayhem-wide/mythtv-theme-projectgrayhem-wide_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/m/mythtv-theme-mythbuntu/mythtv-theme-mythbuntu_0.20080421_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/mythtv-theme-mythcenter_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/mythtv-theme-mythcenter-wide_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv-theme-neon-wide/mythtv-theme-neon-wide_0.21.0-0ubuntu4_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mythtv-theme-projectgrayhem-osd/mythtv-theme-projectgrayhem-osd_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/mythtv-theme-retro_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/mythtv-theme-retro-osd_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/mythtv-theme-titivillus_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/mythtv-theme-titivillus-osd_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/m/myththemes/mythtv-themes_0.21.0-0ubuntu2_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/s/sox/sox_14.0.1-2build2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/t/toolame/toolame_02l-6_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/p/pvm/pvm_3.4.5-11_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/transcode-doc_1.0.2-0.8ubuntu10_all.deb

```

Save it as ~/mythtv.packages

then in a terminal type

```


sudo chmod +x mythtv.packages


```
Make a folder for the debs to go in
```

mkdir ~/mythtvdownloads
cd ~/mythtvdownloads

```
download the debs
```

~/mythtv.packages

```

You should get all the *.debs needed in a folder called mythtvdownloads

---

### Post by hariks0 on 2009-04-03
Dear Sully101,

I am not able to connect to internet using ubuntu 8.10, Airtel, Nokia 6131 as bluetooth modem. But the same is possible with WXP. I have both OSs in my PC and would like to know if I can download the required files for mythtv by WXP and use the files to install in ubuntu 8.10 offline.

A reply with some example in this situation will of great help to newbies like me. Thanks in advance.

---

### Post by sully101 on 2009-04-05
> **hariks0 said:**
> Dear Sully101,

I am not able to connect to internet using ubuntu 8.10, Airtel, Nokia 6131 as bluetooth modem. But the same is possible with WXP. I have both OSs in my PC and would like to know if I can download the required files for mythtv by WXP and use the files to install in ubuntu 8.10 offline.

A reply with some example in this situation will of great help to newbies like me. Thanks in advance.

The problem you have is that for your linux OS to know which packages it needs it would have to connect to the internet. ( You can see the links to the files required in the above post, you could try removing all the "wget -c" and pasting the links into a download manager in XP )
Have you been down the road of getting an internet connection working with linux?

---

