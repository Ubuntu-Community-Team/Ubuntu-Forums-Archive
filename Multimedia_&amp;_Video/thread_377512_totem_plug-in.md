---
title: "totem plug-in"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by newboy12 on 2007-03-06
can anyone help,

I have just installed ubuntu 6.10 (previously an XP user, so new to linux) and have tried accessing this link and similar links 

**[http://www.apple.com/trailers/fox/thesimpsonsmovie/trailer3_large.html](http://www.apple.com/trailers/fox/thesimpsonsmovie/trailer3_large.html)**

the following error is reported

[B]the totem plugin could not startup

could not open resource for writing.[/B]

i have installed automatix and i believed mplayer as suggested in a recent post, is there something else that needs to be configured??

---

### Post by expresso on 2007-03-06
It's because you might not have mplayerplug-in and because you have totem-plugin (or both). You must uninstall totem-plugin (but this will remove also ubuntu-desktop metapackage) or delete files having totem in name from /usr/lib/firefox/plugins/ (dirty hack but i use it and it works)

---

### Post by sdowney717 on 2007-03-06
works for me

DUMP TOTEM as in uninstall remove eliminate completely

Install mplayer and all the restricted codecs

And add the 2 lines in firefox (type in about:config in the address bar for mms streaming..

---

### Post by sdowney717 on 2007-03-06
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

check it out here for all the restricted formats

for flash use this
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

for realplayer you need realplay10gold.bin

then make it executable chmod +x NameOfFile.bin
then run it   ./NameOfFile

---

