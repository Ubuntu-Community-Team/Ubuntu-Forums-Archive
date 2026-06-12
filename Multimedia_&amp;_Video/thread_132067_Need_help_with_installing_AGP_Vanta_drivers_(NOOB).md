---
title: "Need help with installing AGP Vanta drivers (NOOB)"
date: 2006-02-17
forum: Multimedia &amp; Video
---

### Post by am108 on 2006-02-17
Hi everyone

Im completely new to the whole Linux OS.

I have just installed Ubuntu 5.10 Breezy Badger (2.6.12-9-386)

The OS was working perfectly of my onboard MSI S3 graphics card, but i was getting a really wavy image so i decided to install my nVidia Vanta 16MB AGP card.

After putting the card in i started up Ubuntu (the first screen came up and started loading all the modules, but then it went to a funny blue screen saying "failed to start Xserver (your graphical interface)", after looking through the log im presented with a terminal command interface (i haven't a clue what to do or what drivers i need and how to load them)

Any help would be much appreciated because im clueless. Thanks

---

### Post by Teroedni on 2006-02-18
[SIZE="6"]Instruction[/SIZE]
Exit from the funny blue screen saying that you xorg failed to load

Yo know be put back into the blackconsole
put in the usernam and password if itask for it



then write
```
sudo nano /etc/X11/xorg.conf
```

[FONT="Comic Sans MS"]A text editor will now display your xorg.conf file[/FONT]

scoll down to you reach section device
I will look like this


[COLOR="Red"]Demo[/COLOR]
Section "Device"
        Identifier      "something"
        Driver          "xxx"
        BusID           "PCI:1:0:0"
EndSection
[COLOR="Red"]Demo[/COLOR]

The one you need to change is the driver and busid 
The driver should be
```
driver    "nv"
```
the busid should be ```
BusID           "PCI:1:0:0"
```

then you press
Ctrl+O at the same time. It has now saved the file

Then you press Ctrl+x.The nano program will then exit

Then you just need to rebbot and all should work well:)

---

