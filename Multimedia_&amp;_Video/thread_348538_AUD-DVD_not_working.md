---
title: "AUD-DVD not working"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by Kintwa on 2007-01-28
I seem to be having a problem playing DVDs with Ubuntu. I downloaded and installed Automatix from their official website. Using Automatix, I installed Media Codecs and AUD-DVD. However, when I attempt to play a DVD, the DVD does not play. I've tried it on two different media players.

When I try to play DVDs with totem, I get the following message: "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

I know for a fact that libdvdcss is installed, because right after installing AUD-DVD from Automatix, I was notified of an update available for libdvdcss. Also, I did attempt to play a DVD before installing the update, and I recieved the same message as after installing it.

When I try to play DVDs with VLC, if I choose the option to play "DVD Menus", VLC terminates. If I choose the option "DVD", it does nothing.

I've tried several different DVDs as well. All give the same effect. Does anyone have any suggestions on how to fix this?

Thanks

---

### Post by RomeReactor on 2007-01-29
Did you run

```
sudo /usr/share/doc/libdvdread3/install-css-sh
```

after installing it?

---

### Post by jackrobinson on 2007-01-29
> **Kintwa said:**
> I seem to be having a problem playing DVDs with Ubuntu. I downloaded and installed Automatix from their official website. Using Automatix, I installed Media Codecs and AUD-DVD. However, when I attempt to play a DVD, the DVD does not play. I've tried it on two different media players.

When I try to play DVDs with totem, I get the following message: "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

I know for a fact that libdvdcss is installed, because right after installing AUD-DVD from Automatix, I was notified of an update available for libdvdcss. Also, I did attempt to play a DVD before installing the update, and I recieved the same message as after installing it.

When I try to play DVDs with VLC, if I choose the option to play "DVD Menus", VLC terminates. If I choose the option "DVD", it does nothing.

I've tried several different DVDs as well. All give the same effect. Does anyone have any suggestions on how to fix this?

Thanks

There seems to have been a recent issue with the libdvdcss2 package and Automatix has released an updated attempting to fix this issue.
upgrade to the latest version of automatix by doing:
```
sudo apt-get update
sudo apt-get upgrade
```
and then uninstall and reinstall the AUD-DVD codecs option

---

### Post by Kintwa on 2007-01-29
Thank you for your replies.
 
I have tried both methods, and neither seem to work :( Perhaps it is my DVD drive?

---

### Post by RomeReactor on 2007-01-30
I don't know if Automatix installs Gstreamer instead of Xine as its playback backend, but Gstreamer can't handle DVD's quite yet. Look in Synaptic for:

```
totem-xine
```

to see if it's the one installed. If you want DVD playback, it should be...

---

### Post by Dale Sanchez on 2007-12-31
Thank you RomeRactor. That is exactly what I needed. I am new to Ubuntu Linux. So far I love it and the support you can find. Thanks again

---

