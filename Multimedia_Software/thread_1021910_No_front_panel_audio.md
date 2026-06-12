---
title: "No front panel audio"
date: 2008-12-26
forum: Multimedia Software
---

### Post by akshayg on 2008-12-26
I am using vista and ubuntu 8.10 Intrepid Ibex ultimate mod 2. I have onboard realtek sound card. My problem is that audio jacks on back panel of my cpu are screwed. So I am using front panel audio inputs and they work fine in my vista. In ubuntu there is no sound :( 
Pls help...

---

### Post by linux_tech on 2008-12-26
If you are familiar with using alsamixer, this command will will show all the alsamixer settings
```
alsamixer -D hw:0
```
you can also use Gnome-alsamixer, but you will need to install it first.
```
sudo apt-get install gnome-alsamixer

``` 
Then to open gnome-alsamixer type

```
gnome-alsamixer

```
check all settings, make sure nothing is muted; 
make sure front, master and headphone is checked


If you havn't already installed these under Intrepid, installing these next they will probably improve your sound
sudo apt-get install alsa-oss

sudo apt-get install libasound2

sudo apt-get install libasound2-plugins
[/code]


Also to open volume control type:
```
gnome-volume-control

```

---

### Post by akshayg on 2008-12-26
Thanks for your reply.
I have alsamixer and gnome alsamixer installed. Also nothing is muted. Evrything you said is checked. I have alsa oss, libasound2 and libasound2-plugins installed.
Still no sound from front panel :(

---

### Post by akshayg on 2008-12-26
I downloaded realtek driver for linux from realtek website. While installing, I get an error - alsaconf not found :confused:

---

### Post by akshayg on 2008-12-28
bump #-o

---

### Post by akshayg on 2008-12-30
I GOT SOUND YAY............
I don't know what did it. This is what I did
Upgraded my kernel from package manager from 2.6.27.7 to 2.6.27.11, installed alsa mixer and played with its settings and also gnome-volume controls settings for a while and WHOLA I got sound from my front panels :D :D

---

### Post by metallica1025 on 2010-01-28
Awesome. Thanx for the help. Getting sound from the front panel.

---

### Post by ddr3XD on 2010-05-29
bump bump bump bump bump

Mine just doesn't work. plz help PLEEEEEASE!!! :(

---

