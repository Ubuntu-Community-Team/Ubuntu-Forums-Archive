---
title: "Firefox Crashes (segfaults) on almost every flash site"
date: 2008-09-18
forum: Multimedia Software
---

### Post by psypher on 2008-09-18
Hello everyone,

Please help me I'm very frustrated. Since applying the suggestions on [this]("http://www.ubuntugeek.com/pulseaudio-fixes-system-wide-equalizer-support-in-ubuntu-804-hardy-heron.html") site my pulseaudio is working well with other apps  but I cannot go to most flash sites or firefox will close with a segfault. I have tried several suggestions like installing flashplugin-nonfree  nspluginwrapper libflashsupport in different combinations and also the latest flash from macromedia's site. All not working.

thanks in advance

---

### Post by Yellow Pasque on 2008-09-18
Try this:
- Remove the Ubuntu version of libflashsupport (with Synaptic or apt-get remove)
- Download the libflashsupport attached to this post to your desktop: [http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)
```
sudo apt-get install alsa-oss
cd ~/Desktop
gunzip libflashsupport.so.gz
sudo mv libflashsupport.so /usr/lib
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox-addons/plugins
sudo ldconfig
```

If you're a 64-bit user:
```
sudo cp /usr/lib/libflashsupport.so /usr/lib32/
sudo ldconfig
```

---

### Post by psypher on 2008-09-18
That doesn't seem to make a difference. Any other ideas? Should I maybe just start from scratch with firefox, pulseaudio and flash? Or instead roll back to a point that I just couldn't play from more than one app at a time yet flash worked as well as firefox?

thanks for the help so far!

---

### Post by markbuntu on 2008-09-18
Are you using 32 or 64 bit?
8.04?
Those instructions at that site seem a little incomplete to me and leave out a lot of things you should know about. Try my guide here and get rid of that stuff from launchpad. It is in Launchpad because it has not been proven to work well enough yet to get into even the proposed repositories.

Anyway, try my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by psypher on 2008-09-25
That seemed to have fixed it.

THANK YOU!!!

---

