---
title: "[SOLVED] Flash information"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by Zeratul021 on 2008-03-25
Hi, how can i discover my currently installed flash plugin version?
The thing is im desperate with running flash on my opera browser, becasue of som incompatibility issues so i tried installing backwards version of flash (9.0.48 ) even reinstalling whole plugin sets, reinstalling browser with up/down versions but nothing is helping so iwonder where can iget very detailed information about my installed version of flash (its number, release, etc). Thats my last shot so any ideas are welcome. If someone manged to get opera work with youtube and other flash powered sites, he is very welcome to share it :)

---

### Post by kellemes on 2008-03-25
You can use [the beta]("http://www.opera.com/products/desktop/next/"), as long if you have removed gnash and you have "flashplugin-nonfree" installed.. works for me..

---

### Post by gandaran on 2008-03-25
Hi, how can i discover my currently installed flash plugin version?


type about:plugins on firefox navigator bar, it'll show you the flashplugin and version installed.
(it's about : plugins without spaces).

---

### Post by jaiball on 2008-03-25
This might or might not help you(but made a difference to me on Firefox) - If you have the old version of Flash along with a newer version it might be using the old version by default - try going into the plugin directory for Opera(not sure if there is one but where ever the flash file is put) and remove the older file. 

This is what I did to get the newest version working in Firefox.

J

---

### Post by gandaran on 2008-03-25
there is a solution for those that don't won't to install the opera beta, you can use the latest flash 9.0.115 on firefox and flash 9.0.48 for opera 9.26.
to do that you must uninstall flash from the file system, install flash 9.0.115 on the home/user/.mozilla/plugins folder for firefox, and install flash 9.0.48 on the home/user/.opera/plugins folder for opera, in this way there will be separate plugins folders, one for each browser

---

### Post by Zeratul021 on 2008-03-25
thanks all, i tried a lot of combination with version, its weird that mozilla says i have latest 115 plugin but synaptic says that there is newer version :) (i installed 48 ).

Gandaran, could youplease give more detailed info on howto?

Thanks

---

### Post by gandaran on 2008-03-25
> **Zeratul021 said:**
> thanks all, i tried a lot of combination with version, its weird that mozilla says i have latest 115 plugin but synaptic says that there is newer version :) (i installed 48 ).

Gandaran, could youplease give more detailed info on howto?

Thanks

how did you install the 48 package? was it a .deb or tarball ?
do you have the flashplugin-nonfree in synaptic installed?
the flashplugin in synaptic does say it's 48 but with the updates it really installs the 115!

if you want detailed instructions on how-to install flash in home folder, I can do that, but you must get the flash 9.0.48 tar.gz (tarball) package, I have done some searching but couldn't find any, only a .deb package, maybe it's better you upgrade opera to the 9.50 beta version, it works very well with the flash 115 installed on the file system.

---

### Post by Zeratul021 on 2008-03-25
well playing now: i got it from [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/) as deb because i couldnt handle tarball. So when watching install it said md5 mismatch so i downlaoded adobe archive (72mb) and installed flash 48 from that source and it was added to mozilla plugins (about : plugin) but still there was that damned 115. i dont knwo how to get him off there and mozilla is good with youtube etc just opera cant get anything from it. 

so my opera plugins are:
/usr/lib/firefox/plugins/flashplugin-alternative.so
application/futuresplash	
application/x-shockwave-flash
/usr/lib/firefox/plugins/libflashplayer.so

and mozilla:
    Meno súboru: libflashplayer.so
    Shockwave **Flash 9.0 r48**
and right under it
    Meno súboru: libflashplayer.so
    Shockwave **Flash 9.0 r115**

---

### Post by gandaran on 2008-03-25
> **Zeratul021 said:**
> well playing now: i got it from [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/) as deb because i couldnt handle tarball. So when watching install it said md5 mismatch so i downlaoded adobe archive (72mb) and installed flash 48 from that source and it was added to mozilla plugins (about : plugin) but still there was that damned 115. i dont knwo how to get him off there and mozilla is good with youtube etc just opera cant get anything from it. 

so my opera plugins are:
/usr/lib/firefox/plugins/flashplugin-alternative.so
application/futuresplash	
application/x-shockwave-flash
/usr/lib/firefox/plugins/libflashplayer.so

and mozilla:
    Meno súboru: libflashplayer.so
    Shockwave **Flash 9.0 r48**
and right under it
    Meno súboru: libflashplayer.so
    Shockwave **Flash 9.0 r115**

yes it does look you have both installed, go to synaptic look for flashplugin-nonfree and mark for complete removal and click the apply button, that should rid you of flash 115.

---

### Post by Zeratul021 on 2008-03-25
done, its uninstalled but mozilla stil recognizes both of them (dont knwo if restart si needed)

---

### Post by gandaran on 2008-03-25
> **Zeratul021 said:**
> done, its uninstalled but mozilla stil recognizes both of them (dont knwo if restart si needed)

no need to restart, look in synaptic for any other flash package installed, if you can't find any it means you installed both packages from a tar.gz (tarball) package, only solution is to delete the flash files, problem is knowing which one is the 115, but I think the 115 is in /usr/lib/firefox/plugins/flashplugin-alternative.so, have a look there.



I will be back here tomorrow.

---

### Post by Zeratul021 on 2008-03-26
bulls eye that was it, when i will get back from school i will continue, now mozilla says only 48 is installed
so what next? i have tar of 9.48 from that archive mega pack of adobe (that one installed by flashplugin-installer contains only 2 files like the latest one)

---

### Post by gandaran on 2008-03-26
> **Zeratul021 said:**
> bulls eye that was it, when i will get back from school i will continue, now mozilla says only 48 is installed
so what next? i have tar of 9.48 from that archive mega pack of adobe (that one installed by flashplugin-installer contains only 2 files like the latest one)

good, now to find where the 48 is installed, look in /usr/lib/mozilla or /usr/lib/mozilla-firefox and /usr/lib/flashplugin-nonfree, but I think as it doesn't show up in opera, it must be in home/user/.mozilla/plugins, if correct inside the plugins folder there should be a libflashplayer.so and a flashplayer.xpt file, (libflashplayer.so should do)
copy that plugins folder and paste in the home/user/.opera folder, in that way you have  firefox and opera with their own separate plugins folder,
go to the youtube site and see if flash works in opera now, (what version is your opera? 9.24, 9.25 or 9.26? ) if it works and you want the 115 for firefox, I will tell you later how to easily let firefox install directly from the adobe site to the home .mozilla folder.

can you post the contents of opera » tools » advanced » plug-ins?

---

### Post by Zeratul021 on 2008-03-26
Now you have earned a lot thanks from me and my pupils :). Not that my 9.26 works with flash its everything ok till the 9.5 is online. Thanks a lot im going to rewrite your guidelines and post it to other poeople.

---

