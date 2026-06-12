---
title: "libavformat-extra-53"
date: 2012-07-16
forum: Multimedia Software
---

### Post by luangwa on 2012-07-16
Is there anyway to install libavformat-extra-53 on Lucid? I am trying to use Serviio in Lucid to serve photos,music, and movies to my tv. I have followed all the install procedures on [http://wiki.serviio.org/doku.php?id=howto:linux:install:ubuntu](http://wiki.serviio.org/doku.php?id=howto:linux:install:ubuntu) with the exception of libavformat-extra-53. I get the following message when I enter: sudo apt-get install libavformat-extra-53

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libavformat-extra-53

I am able to select Serviio from my television. I can select the directories where the photo's, etc. are stored but when I choose the directory I receive "No Data Available". I believe libavformat-extra-53 is my missing link to getting Serviio to work. 

Thanks for your anticipated help on this matter.:confused:

---

### Post by bobsan on 2012-07-17
I don't know anyway to install it in 10.04, but apparently you shouldn't even if you find a way because you will screw up other things such as ffmpeg.

[http://askubuntu.com/questions/110656/ffmpeg-unmet-dependencies](http://askubuntu.com/questions/110656/ffmpeg-unmet-dependencies)

---

### Post by cottfcfan on 2012-07-17
I think you need the medibuntu repository enabled to install libavformat-extra-53.
[http://medibuntu.org/repository.php/](http://medibuntu.org/repository.php/)
I personally haven't found it to screw up anything, and in 12.04 need it for Devede to function properly.
But just be careful what it asks to remove when installing software  from it.

---

### Post by bobsan on 2012-07-17
> **cottfcfan said:**
> I think you need the medibuntu repository enabled to install libavformat-extra-53.
[http://medibuntu.org/repository.php/](http://medibuntu.org/repository.php/)
I personally haven't found it to screw up anything, and in 12.04 need it for Devede to function properly.
But just be careful what it asks to remove when installing software  from it.

OP is using Lucid, there is no libavformat-extra-53 in medibuntu, the proper version for Lucid is 52.

---

### Post by BicyclerBoy on 2012-07-17
This ppa has old & new ffmpeg abi packages..
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg?field.series_filter=lucid](https://launchpad.net/~jon-severinsson/+archive/ffmpeg?field.series_filter=lucid)

Seems to work okay with std lucid packages, but then I build the important ones from source.

---

### Post by FakeOutdoorsman on 2012-07-19
Question looks similar to [How to install libavcodec53 on Ubuntu 10.04 LTS?](http://ubuntuforums.org/showthread.php?t=2025371)

---

