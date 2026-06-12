---
title: "TV programmes scanned but no EPG in Me TV or Kaffeine"
date: 2017-04-29
forum: Multimedia Software
---

### Post by jm101 on 2017-04-29
I am new to linux - have just installed Ubuntu 16.04 LTS on an old IMac. I am using a 2008 Elgato Hybrid DVB adaptor (made for Mac), which has been recognised and initialised in terminal. After running w_scan in terminal, I was able to get Me TV to scan for channels. But I can't get the EPG to show up in MeTV (the EPG window just isn't there), nor is there any video picture. There is an error message saying that the available Front End can't be accessed. I have the same problem with Kaffeine, incidentally (channels scanned OK, but no EPG). It seems to me that as I have the same problem with both programmes, that there it's likely that the Elgato Hybrid adaptor is not being recognised properly. Any suggestions (suitable for a novice) for getting EPG and pictures?
I have tried to install MythTV but it's too complicated for me at this stage, so I have uninstalled it again.

---

### Post by walterav on 2017-05-04
Is this the exact same usb-tuner adapter you are using, check terminal output of the following command:

```

lsusb 

#0fd9:0018 Elgato Systems GmbH EyeTV Hybrid

```

I got this tuner to work with EPG and 16.04 kernel 4.4.x with tvheadend, could you try to install tvheadend? It works a little different than Kaffeine or MeTV since its a backend server but can be used by frontend media clients like KODI and VLC even on other machines in your network also its very low on CPU/RAM resources. I wrote a howto for installing/setting up tvheadend in ubuntu, see the part "As a third DVB-C tuner we use the USB Elgato EyeTV Hybrid".

[https://ubuntuforums.org/showthread.php?t=2336566&p=13542231#post13542231](https://ubuntuforums.org/showthread.php?t=2336566&p=13542231#post13542231)

---

