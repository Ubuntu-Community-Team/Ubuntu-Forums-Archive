---
title: "Adobe flash player not working"
date: 2009-01-28
forum: Multimedia Software
---

### Post by 81golfcaddy on 2009-01-28
upgraded to the latest ubuntu and went on youtube and it asked me to install the latest adobe flash player. so I did and it is not working at all. each time it will ask me to install it. I have uninstalled and reinstalled and restarted computer. no changes still not working. this is about the only issue I have had with ubuntu. need a little help please

---

### Post by mgol on 2009-01-28
Is Your signature true? That is, do You still use 7.04 Feisty Fawn? If so, upgrade, as this one is not supported yet.

The flash plugin is in flashplugin-nonfree package if You want it from Ubuntu (it works for most cases). If You need Flash v. 10, You need to download the script for the Adobe site, but for most cases it's not necessary.

Put in the terminal:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by 81golfcaddy on 2009-01-29
sorry need to change my signature. not using 7.04 now using 8.04. have tried updating using apt. but no success. still get a message asking me to install adobe flash player.

---

### Post by mgol on 2009-01-29
Have You tried to install the official one?
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
But remember - after You download it, close firefox, uninstall flashplugin-nonfree and only then install just downloaded Flash Player.

---

### Post by wolfen69 on 2009-01-29
in synaptic, completely remove flash you may have. then:
```
sudo apt-get clean && sudo apt-get autoremove
```
then go to the adobe link above that mgol gave and download the .deb for ubuntu and click to install.

---

### Post by xfacta on 2009-01-29
I was having trouble with my web site online authoring site, the file uploads would not work and I had to resort to a Windows machine. Some sort of flash software is used for the file manager.

This worked for me (Ubuntu 8.10, FireFox 3.0.5):

[LIST]
[*]Uninstalled all flash and SWF related software (gnash and non-free plugins)

[*]Went to [www.adobe.com](www.adobe.com) and downloaded the .deb for Flash player v10

[*]double clicked on .deb install file, closed and reopened Fire Fox.
[/LIST]

Flash now works fine and the FireFox plugin shows the correct version instead 9.999

---

### Post by 81golfcaddy on 2009-01-29
this is what I am getting still.
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. 
I looked at firefox applications is this correct ?
shockwave flash file application/futuresplash use movie player default
shockwave flash file application /x-shockwave-flash use movie player default.
thank you for your help so far.

---

### Post by 81golfcaddy on 2009-01-29
something like this really gets under my skin. I fixed it. Installed Linux Mint.

---

### Post by wolfen69 on 2009-01-29
> **81golfcaddy said:**
> something like this really gets under my skin. I fixed it. Installed Linux Mint.

you could have installed [Kiwi Linux]("http://kiwilinux.org/en/"). it is ubuntu (even looks the same) with all codecs and flash preinstalled. keep that in mind if you decide you don't like mint.

---

