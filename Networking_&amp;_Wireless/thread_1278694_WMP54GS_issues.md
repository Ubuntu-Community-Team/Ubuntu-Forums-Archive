---
title: "WMP54GS issues"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by fisch on 2009-09-29
Hey,

I'm relatively new to Ubuntu (6 ish months) and have been running fine on a linksys wireless b usb. I just got a new routher though and switched to a linksys pci wireless g. I've done ndiswrapper, and it still has not worked. In hardware drivers I've got a broadcom thing but, as I don't have internet, I cant install it.

Any help would be great: I'm royally stuck

---

### Post by thoriumchameleon on 2009-09-29
I suggest that you first connect to the router via ethernet and make sure everything is a-okay. then after you can access the internet through ethernet you can try to use your pci card.. what type of card is it? mine worked out of the box no hassle... you may not need ndiswrapper. once your connected via wifi, if you don't have internet, first check to see if you're connected to the router.. open a web browser and go to 192.168.1.1

---

### Post by fisch on 2009-09-30
Its a linksys WMP54GS pci card connecting to a linksys wireless n router I' pretty sure I need to install a Broadcom driver and I would rather not move to ethernet connection as it is a long way a away and would be a pain to move. I need a way to install it other than connecting to the internet.

---

### Post by thoriumchameleon on 2009-09-30
I have a WMP54GS and it works fine out of the box... thats not an issue... you should uninstalll ndiswrapper and configure wlan0 to connect 2 your router... make sure the router is broadcasting wireless g also... your pci card can't connect via wireless n

---

### Post by fisch on 2009-09-30
I know that the router supports it and I have used ndiswrapper numerous times. I believe the issure is that I dont have the Broadcom firmware installed and cant figure out how to do it w/o internet and w/o moving my computer.

---

### Post by bkratz on 2009-09-30
> **fisch said:**
> Hey,

I'm relatively new to Ubuntu (6 ish months) and have been running fine on a linksys wireless b usb. I just got a new routher though and switched to a linksys pci wireless g. I've done ndiswrapper, and it still has not worked. In hardware drivers I've got a broadcom thing but, as I don't have internet, I cant install it.

Any help would be great: I'm royally stuck

[http://ubuntuforums.org/showthread.php?t=1233448&highlight=wmp54gs](http://ubuntuforums.org/showthread.php?t=1233448&highlight=wmp54gs)


Have you looked at this? If I understand it right it appears that what you are looking for is available on the installation disk????

Good Luck

---

### Post by thoriumchameleon on 2009-09-30
thats very interesting.. what distro are u using? it works out of the box with 8.04 or later 4 me

---

### Post by fisch on 2009-09-30
I have Jaunty 9.04. I tried the link that bkratz gave me and b43 -fwcutter is not listed in my synaptic package manager.

---

### Post by thoriumchameleon on 2009-10-01
im using 9.04 and it shows in my synaptic... try 
```

sudo apt-get upgrade
sudo apt-get install b43-fwcutter

```

---

