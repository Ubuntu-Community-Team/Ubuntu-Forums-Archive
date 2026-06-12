---
title: "Streaming Videos Freezes"
date: 2009-10-22
forum: Multimedia Software
---

### Post by Varda on 2009-10-22
Hi!! I'm very new in Linux I installed yesterday in my Acer Aspire One AO751h (1gb ram, intel atom 1.33 mhz, GMA500 graphics) the Ubuntu Remix 9.04. I have several problems with video streaming (avi, mkv, mp4). I tried of course downloading VLC player, Mplayer, all codecs I found but the movies freezes, I don't know what to do.

 I'm worry about the configuration of drivers or something like that, I recently configured GMA500 problems with Compiz ([https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h) and [http://comulinux.blogspot.com/2009/09/habilitar-efectos-3d-usando-gma500.html](http://comulinux.blogspot.com/2009/09/habilitar-efectos-3d-usando-gma500.html)) and maybe I broke something... I don't know how to start, so I need your help. Sorry for my bad english and thanks!!

---

### Post by RichardLinx on 2009-10-22
You probably don't have the multimedia codecs installed. Here's how to install them; Open a terminal and type: (Note: You can open a terminal through Applications --> Accessories --> Terminal)
```
sudo apt-get install ubuntu-restricted-extras
```

Enable Medibuntu repositories: ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu))
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```
DVD codec:
```
sudo apt-get install libdvdcss2
```
w32 codecs:
```
sudo apt-get install w32codecs
```
I recommend the kaffeine multimedia player for video:
```
sudo apt-get install kaffeine
```

Then:
```
sudo apt-get autoclean
```
```
sudo apt-get autoremove
```

I've noticed a lot of users have had this same problem lately. Ubuntu really needs to make it a little more obvious why these codecs aren't installed and how to install them.

Hope this helps. :)

---

### Post by Varda on 2009-10-22
Thanks a lot!! I'm working on it right now! :D

---

