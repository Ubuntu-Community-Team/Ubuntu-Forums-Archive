---
title: "YouTube!"
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by NewWaves on 2006-09-16
Hi,
Since I got this new computer, I've been having problems trying to view my YouTube videos... It says I need flash, which I installed all the plugins from the repostories, but no luck.  What am I doing wrong?!

---

### Post by th3t1nm4n on 2006-09-16
Try this:
```
sudo apt-get install flashplugin-nonfree --assume-yes
sudo update-flashplugin
```

---

### Post by NewWaves on 2006-09-17
automatic installation failed due to network problems or upstream changes

^^ Returns with sudo update-flashplugin

---

### Post by tseliot on 2006-09-17
Try with:
```
sudo dpkg-reconfigure debconf
```

and select "medium"

Then try to install flash again

---

### Post by NewWaves on 2006-09-17
Hi,
I reconfigured debconf selected medium and when i go to install flashplugin -nonfree i get 


The installation of the plugin failed. Try again with /usr/sbin/update-flashplugin or get the plugin from [http://macromedia.mplug.org/](http://macromedia.mplug.org/) and follow the instructions you find with the plugin.

I then downloaded that file to my desktop, ran the install again, and it still failed... I'm at a loss...

---

### Post by Sukarn on 2006-09-17
> **th3t1nm4n said:**
> Try this:
```
sudo apt-get install flashplugin-nonfree --assume-yes
sudo update-flashplugin
```
Isin't that ```
sudo apt-get --force-yes -y install flashplugin-nonfree
sudo update-flashplugin
```
I mean I have never seen --assume-yes being used before. I have always used --force-yes

EDIT: Totally unrelated: lynx is nice, I am posting this from command line with lynx-cur

---

### Post by NewWaves on 2006-09-17
Hi,
I tried with the force flag instead, i then go to run update-flashplugin and i get this:

automatic installation failed due to network problems or upstream changes

---

### Post by th3t1nm4n on 2006-09-19
Yeah, I heard about that, something was up with the flashplayer website which it got the data from.
When its back up, that method may work again. Until then I'd just do that manual install, its not hard at all: [http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4)

```
cd Desktop
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz
tar -xvf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux/
sh flashplayer-installer
```
Enter, Enter, Enter, Y, N
```
cd ..
rm -rf install_flash_player_7_linux*
```

and then grab the fonts if you don't already have them:
```
sudo apt-get install gsfonts gsfonts-x11
```

Good luck.

---

### Post by NewWaves on 2006-09-20
HI,
I've already tried both routes... Everything worked on my old PC when I upgraded from breezy to dapper instead of my new one where I just installed dapper... I really don't want to have to restart from the top again!

---

### Post by bhaumik_thacker on 2008-03-13
hello everybody,
I hope everyone here knows that when watching a video on YouTube, the video is downloaded and temporarily stored on your computer. Does anyone know the path where it is stored? In windows it is somewhat like "c:/documents and settings/...temp/..." and to view this all hidden files need to be made viewable.

---

### Post by eye208 on 2008-03-13
It's in /tmp.

Audio files are not cached in /tmp but you can find their download links using the about:cache URL in Firefox.

---

