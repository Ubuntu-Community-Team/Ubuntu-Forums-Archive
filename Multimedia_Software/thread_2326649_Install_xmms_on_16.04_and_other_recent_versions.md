---
title: "Install xmms on 16.04 and other recent versions"
date: 2016-06-03
forum: Multimedia Software
---

### Post by shantiq on 2016-06-03
[I]This is an updated [xmms]("https://en.wikipedia.org/wiki/XMMS") howto from an[ earlier thread]("http://ubuntuforums.org/showthread.php?t=1525072&highlight=shantiq+xmms") which still contains many tips and plugins still current ...   explore if you need any more info
Would appreciate constructive feedback here if you use the following steps to install: [/I]


Using[ ibidem]("http://https://launchpad.net/~ibid-ag/+archive/ubuntu/oldgtk1/+index?field.series_filter=&batch=75&direction=backwards&start=75") repository >>

```
sudo add-apt-repository ppa:ibid-ag/oldgtk1
``` 
```
sudo apt-get update
```


```
software-properties-gtk
```
then change both ibid lines to lucid


Then reload 




*DEPENDENCIES:*



```
wget -i- http://launchpadlibrarian.net/10162105/x-dev_7.0.11-1_all.deb \
http://mirror.esc7.net/pub/Ubuntu/pool/main/x/x11proto-core/x-dev_7.0.11-1_all.deb \
http://mirror.esc7.net/pub/Ubuntu/pool/main/x/x11proto-core/x11proto-core-dev_7.0.29-1ubuntu1_all.deb \
http://mirror.ip-projects.de/ubuntu-old/pool/universe/g/gtk+1.2/libgtk1.2-common_1.2.10-18.1build2_all.deb \
http://mirror.ip-projects.de/ubuntu-old/pool/universe/g/gtk+1.2/libgtk1.2-dbg_1.2.10-18.1build2_amd64.deb \
http://mirror.ip-projects.de/ubuntu-old/pool/universe/g/gtk+1.2/libgtk1.2_1.2.10-18.1build2_amd64.deb \
http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmikmod/libmikmod2_3.1.11-a-6.1_amd64.deb
``` 


```
sudo dpkg -i *.deb
```     then remove debs   ```
sudo rm *.deb
```


* now XMMS   [with xmms-cueinfo mp4 aac m4a wavpack ape crossfade]*


```
wget -i- http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu/pool/main/x/xmms/xmms_1.2.11-1ubuntu1+ppa4_amd64.deb \
http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu/pool/main/x/xmms-cueinfo/xmms-cueinfo_0.2.0-1ppa1_amd64.deb \
http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu/pool/main/x/xmms-mp4/xmms-mp4plugin_2006p_amd64.deb \
http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu/pool/main/x/xmms-wavpack/xmms-wavpack_1.0.3-1_amd64.deb \
http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu/pool/main/m/monkeys-audio/libmac2_3.99-u4-b5-0.1_amd64.deb \
http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu/pool/main/x/xmms-mac/xmms-mac_0.3.1-0.0~ppa1_amd64.deb \
http://ppa.launchpad.net/ibid-ag/oldgtk1/ubuntu/pool/main/x/xmms-crossfade/xmms-crossfade_0.3.10-1.2_amd64.deb
``` 

```
sudo dpkg -i *.deb
```     then remove debs   ```
sudo rm *.deb
```



*FLAC*:

```
sudo apt-get install flac
```

and add[ xmms-flac ]("http://ubuntuforums.org/attachment.php?attachmentid=205283&d=1319398314")
>> 

then you will need to move it from

```
cd /usr/lib64/xmms/Input
```
```
sudo cp * /usr/lib/xmms/Input
```



*Both on Lubuntu 16.04*

[[IMG]http://s20.postimg.org/kb9bi75p5/image.png[/IMG]]("http://postimg.org/image/kb9bi75p5/")[[IMG]http://s20.postimg.org/dyu68d2mx/image.png[/IMG]]("http://postimg.org/image/dyu68d2mx/")


SHORTEN

if you wish to use shorten format
[install first]("http://ubuntuforums.org/attachment.php?attachmentid=162586&d=1278411609")  
```
./configure 
make
sudo make install
```

Then use deb attached [made from [rpm file]("https://www.rpmfind.net/linux/rpm2html/search.php?query=xmms-shn")] with alien

---

