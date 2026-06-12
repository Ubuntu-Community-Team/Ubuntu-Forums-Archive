---
title: "Not able to watch films rented through Youtube Movies"
date: 2012-04-21
forum: Multimedia Software
---

### Post by andreagrosso on 2012-04-21
Hello,

The problem I am experiencing is strictly related to the films that are available to rent on youtube.com/movies. More in particular it's related to the pay-per-view films. In fact, any other type of free Youtube video (both the free films found on the same website and the usual videos found on youtube.com) is successfully loaded and streamed to my Asus EEE1000.

The error I receive once I access a film that I just purchased is "An error occurred. Please try again later."

Few information:

Ubuntu version: 11.04.
Mozilla version: 11.0.
Adobe Flash Player plugin version: 11.

I have tried to explain the problem to the Youtube "Report a problem" service, but they reply only with automated e-mails letting me know about the refund.

Any help is appreciated!

---

### Post by lovinglinux on 2012-04-24
Without access to the videos is difficult to troubleshoot, specially when some DRM is involved. 

If you are using a 64bit system, you could try the development build of Chrome browser, which comes with PepperFlash. I hate to recommend that, but who knows...

Anyway, please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'pluginreg.dat' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat ~/.mozilla/firefox/**/pluginreg.dat >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by DaveWard on 2012-05-26
It might be a little late for the solution to this problem, you have to have hal installed from the reposiroty in order to play DRM protected flash content from the you-tube movie rental service (or from the google play store as it seems to be the same thing). 

Adobe provide instructions.. [http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html](http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html)

In summary: 

sudo apt-get install hal

clear out the relavant cache files from your home folder..

cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2

Head over to you tube and you will find that the content should now play. 

Bloody DRM!

---

### Post by andreagrosso on 2012-06-04
Sorry for the super-late reply!

Thanks a lot, the Hardware Abstraction Layer (hal) module was indeed required to correctly play the rented movies.

Thanks again for the help!

---

### Post by lovinglinux on 2012-06-04
> **DaveWard said:**
> It might be a little late for the solution to this problem, you have to have hal installed from the reposiroty in order to play DRM protected flash content from the you-tube movie rental service (or from the google play store as it seems to be the same thing). 

Adobe provide instructions.. [http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html](http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html)

In summary: 

sudo apt-get install hal

clear out the relavant cache files from your home folder..

cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2

Head over to you tube and you will find that the content should now play. 

Bloody DRM!

Thanks for providing the solution.

---

### Post by Upedro on 2012-09-23
It bloody works!!!!!  :D

Didn't think there was a solution. 

Thanks guys

---

