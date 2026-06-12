---
title: "Sound not working ubunut 12.04"
date: 2015-03-26
forum: Multimedia Software
---

### Post by tapasweni_pathak2 on 2015-03-26
[FONT=arial][COLOR=#333333]Sound from both speakers and headphones was working fine. After a recent update, the sound from speaker was not working but it was working from headphones, to fix the issue I did something I don't remember :(, which also stopped the sound from headphones. But I was getting a sound while login in headphones, no sound other than that. To fix this I did this([http://askubuntu.com/a/295556](http://askubuntu.com/a/295556)). Now there is no sound at all.[/COLOR]
[COLOR=#333333]There is also one more strange thing I observed, when I plugin my headphones the options in output in play sound through does not show headphones, it only shows Analog Output (*Built-in Audio*).[/COLOR][/FONT]
[FONT=arial][COLOR=#333333]lsb_release -a gives
[/COLOR][/FONT]
    No LSB modules are available.
    Distributor ID: Ubuntu
    Description:    Ubuntu 12.04.5 LTS
    Release:    12.04
    Codename:   precise
[FONT=arial][COLOR=#333333]
Alsainfo gives [this]("http://pastebin.com/RE8L22aa").[/COLOR]
[COLOR=#333333]
alsamixer on terminal shows[/COLOR]
[COLOR=#333333]*This sound device does not have any controls.*[/COLOR]
[COLOR=#333333]
aplay -l gives [this]("http://pastebin.com/3GSXah09").[/COLOR]
[COLOR=#333333]Can someone please help me to fix this?[/COLOR][/FONT]

---

### Post by dino99 on 2015-03-26
you should install 'paman' then test the 'output devices' options ( from menu -> pulseaudio volume control) to find which ones are good (maybe also first tweak the 'config' tab

---

