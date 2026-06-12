---
title: "windows media 9 codec: no sound in mplayer / totem / vlc"
date: 2010-05-15
forum: Multimedia Software
---

### Post by Kleenux on 2010-05-15
I thought it could be a good idea to share with our dear Ubuntu users how I fixed my sound problems, that happened only for "windows media 9" videos, after struggling for days changing the players etc...

(using Ubuntu lucid 10.04 up to date)

First please search for "Ubuntu install w32codecs" (or w64codecs depending on your system bus width) and... install them as root or 'sudo'```
$ sudo apt-get install w32codecs (or w64codecs)
```

After updating totem to the very latest version (May 12, 3 days ago) the problem happened to be likely from the source: gstreamer. So I tried to install the latest version of gstreamer, and it worked (the default one packaged in Ubuntu is dated 2008...).

```
**try**
{
   install latest developer version
}
**disclaimer**
{
   this was my last alternative, and fortunately it worked well.
   but using the developer versions is always taking a risk...
}
```

To install the latest version automatically, follow [this link ]("https://launchpad.net/~gstreamer-developers/+archive/ppa").
In other terms, on 'lucid', as root or 'sudo' add 2 lines to a new file to complete your sources.list ; after the 2nd line, press control-D on a blank line to complete the edition```
$ sudo cat >> /etc/apt/sources.list.d/gstreamer-developers.list
deb http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu lucid main
```Add also the key to ensure the version you download is not altered```
add-apt-repository ppa:gstreamer-developers/ppa
```
Update that```
$ sudo apt-get update
$ sudo apt-get upgrade
```
Finally I did a reboot while I'm not sure it is necessary.

---

### Post by arindammanidas on 2010-11-04
Hi Kleenux.... Thanks man. You made my day. I followed your instructions. First i added the medibuntu repos to install w32codecs. Next Updated gstreamer by adding the gstreamer developer ppa and finally installed "gstreamer0.10-pitfdll" which makes gstreamer use w32codecs instead of others (although i m not sure the last step was necessary). Now i can play windows media streaming videos with audio even inside Firefox which uses the totem plugin. 
:guitar: :):):)

---

### Post by makyura on 2010-11-29
I created account on forum just to write thanks man. adding repository and upgrade is all it took to fix sound issues.

---

### Post by dimeotane on 2011-01-29
Thanks! This solution helped me too. You're a super :KS

---

### Post by Marais on 2011-04-29
Another solution a bit risky is to install the developer version of Totem (actually 2.91.92) here :
[http://www.icewalkers.com/download/totem/2066/dld/](http://www.icewalkers.com/download/totem/2066/dld/)

it worked for me for the moment:)

---

### Post by eduardofuentescaro on 2012-01-05
I registered only to say THANKS A LOT!! You made my day :p

---

### Post by petterwr on 2012-05-23
Thanks a lot! 

No restart necessary btw, tested with totem/mplayer.

---

### Post by l-x-l on 2012-06-10
Many thx for this.

---

