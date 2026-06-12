---
title: "Spotify not working on ubuntu 14.04"
date: 2016-07-06
forum: Multimedia Software
---

### Post by doxy1398 on 2016-07-06
These are the commands ive typed in terminal
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886
echo deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list
sudo apt-get update
sudo apt-get install spotify-client

```
After all these commands I get the following error.

```
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/universe libgsm1 amd64 1.0.13-4
  404  Not Found [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/universe libmp3lame0 amd64 3.99.5+repack1-3ubuntu1
  404  Not Found [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/universe libopenjpeg2 amd64 1.3+dfsg-4.7ubuntu1
  404  Not Found [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/universe libschroedinger-1.0-0 amd64 1.0.11-2ubuntu1
  404  Not Found [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/universe libva1 amd64 1.3.0-2
  404  Not Found [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/universe libx264-142 amd64 2:0.142.2389+git956c8d8-2
  404  Not Found [IP: 202.158.214.106 80]
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) trusty/universe libxvidcore4 amd64 2:1.3.2-9ubuntu1
  404  Not Found [IP: 202.158.214.106 80]
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libg/libgsm/libgsm1_1.0.13-4_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libg/libgsm/libgsm1_1.0.13-4_amd64.deb) 404  Not Found [IP: 202.158.214.106 80]


E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/l/lame/libmp3lame0_3.99.5+repack1-3ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/l/lame/libmp3lame0_3.99.5+repack1-3ubuntu1_amd64.deb) 404  Not Found [IP: 202.158.214.106 80]


E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/o/openjpeg/libopenjpeg2_1.3+dfsg-4.7ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/o/openjpeg/libopenjpeg2_1.3+dfsg-4.7ubuntu1_amd64.deb) 404  Not Found [IP: 202.158.214.106 80]


E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/s/schroedinger/libschroedinger-1.0-0_1.0.11-2ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/s/schroedinger/libschroedinger-1.0-0_1.0.11-2ubuntu1_amd64.deb) 404  Not Found [IP: 202.158.214.106 80]


E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libv/libva/libva1_1.3.0-2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libv/libva/libva1_1.3.0-2_amd64.deb) 404  Not Found [IP: 202.158.214.106 80]


E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/x/x264/libx264-142_0.142.2389+git956c8d8-2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/x/x264/libx264-142_0.142.2389+git956c8d8-2_amd64.deb) 404  Not Found [IP: 202.158.214.106 80]


E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/x/xvidcore/libxvidcore4_1.3.2-9ubuntu1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/x/xvidcore/libxvidcore4_1.3.2-9ubuntu1_amd64.deb) 404  Not Found [IP: 202.158.214.106 80]


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```
Was after some help please :)

---

### Post by X-RED_Tech on 2016-07-06
The error are from an Ubuntu official mirror. Try changing it and/or try again in a day or two as it may well be just a temporary network issue.

---

### Post by wildmanne39 on 2016-07-07
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

