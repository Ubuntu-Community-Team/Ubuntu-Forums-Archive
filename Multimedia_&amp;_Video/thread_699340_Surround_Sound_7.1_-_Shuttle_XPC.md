---
title: "Surround Sound 7.1 - Shuttle XPC"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by cenwesi on 2008-02-17
Hello Everyone, I am rewriting my issue i posted yesterday about the surround sound issue and i hope there is a guru out there that can help me solve this problem. I really need my surround sound to work.

I have a Shuttle's XPC SB86i system, some information about my system can be found here:
  -->>  [http://techreport.com/articles.x/7940](http://techreport.com/articles.x/7940)
  -->>  [http://global.shuttle.com/product_detail.jsp?PI=78](http://global.shuttle.com/product_detail.jsp?PI=78)

Just a brief history, i currently have Ubuntu v7.10(gusty, 64bit) running on my **main server** and works just fine. I use this server for my main file server, VM's and other stuff... 

On the **Shuttle xpc** pc, i installed Ubuntu v7.10 Gusty(32bit). Everything so far worked fine until i noticed that the **surround sound** is not working. The earphone/front speaker works fine but the rear, no sound.
I am setting up this pc to be used as an HTPC. I will be running SageTV, which by the way worked like a charm and it is then i noticed that the surround sound wasn't working. 

So far i have looked and tried alot of the settings found in some threads here but still no surround sound. I am sure there is someone here that has this pc and probably have surround sound working. I have looked at the [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) site and i am lost as to what to get...
Here are some of the command i did to get hardware specific information on the sound card....

```
 aplay -l
```
and i get:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I also did:
```
lspci | grep -i audio 
```
and i get:

```
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
```


PS: Currently running Windows XP and the surround sound works fine.
Please, if anyone knows how to get this working i would really like to know how to so i can switch completely away from Windows.

---

### Post by cenwesi on 2008-02-18
bump

---

### Post by cenwesi on 2008-02-19
I find it really hard that no one here knows how to get this working. I mean where are all the experts :) please someone help me.

---

