---
title: "Flashplayer problem"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by tkrisz on 2007-07-14
Feisty 32-bit install. There's a site, where i would like to play some embedded videos. It doesn't want to play the videos and directs me to Adobe's dowload site.
I have the latest Adobe Flash plugin in my FF. Adobe's site recognize it as the latest version and also about:Plugins says:
```
Shockwave Flash

    Fájlnév: libflashplayer.so
    Shockwave Flash 9.0 r48

MIME-típus 	Leírás 	Kiterjesztés 	Engedélyezve
application/x-shockwave-flash 	Shockwave Flash 	swf 	Igen
application/futuresplash 	FutureSplash Player 	spl 	Igen
```
I also have a Dapper 64-bit install with 32-bit FF (with Kilz's script). It has a Flash 9.0 r31 and plays the videos perfectly. 
```
Shockwave Flash

    Fájlnév: /home/krisz/.mozilla/plugins/libflashplayer.so
    Shockwave Flash 9.0 r31

MIME-típus 	Leírás 	Kiterjesztés 	Engedélyezve
application/x-shockwave-flash 	Shockwave Flash 	swf 	Igen
application/futuresplash 	FutureSplash Player 	spl 	Igen
```
What can be wrong? I suppose the later the version the more videos can it play.

---

### Post by Gremlinzzz on 2007-07-14
post the site .ill see if it does the same to me.
:guitar:

---

### Post by tkrisz on 2007-07-14
Thx. It's a Hungarian singer talent searching contest and these are the videos of the candidates:

[http://galeria.tarsulat.hu/v/valogatas_200706/](http://galeria.tarsulat.hu/v/valogatas_200706/)

---

### Post by Gremlinzzz on 2007-07-14
Yeah nice had no problem watching.

---

### Post by Gremlinzzz on 2007-07-14
you could reinstall your flash this is the way that works for me .
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
save to desktop
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/

---

### Post by tkrisz on 2007-07-14
Everything was correct, just the videos were filtered out by the Adblock Plus plugin. (Which was a little stupid from it, but i should have think on that.) :-? Thank you for the help and sorry for taking your time by this.

---

### Post by Gremlinzzz on 2007-07-14
No problem glad you fixed it.
:guitar:

---

