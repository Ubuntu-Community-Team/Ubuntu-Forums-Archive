---
title: "4GB ZEN MP3 Player"
date: 2009-01-11
forum: Multimedia Software
---

### Post by baller_2003 on 2009-01-11
Hey guys,
I had been running Windows Vista for the past year or so. I got tired of it one day and decided to upgrade to ubuntu. The system works fine on my acer laptop, but I can't get my Creative ZEN MP3 player to work with the os.The system recognizes it as a usb device, but I can't access it. Every time I try to it says: "Unable to mount to location, No media in drive." So I read some posts that I found on the ubuntu websites about ZENs. One user recommended installing Gnormad 2, so I did. I don't think this helped my problem any because now I get: "No jukeboxes found on usb bus." If anyone can help, I would greatly appreciate it. I have posted screen shots of the errors in here for you guys.

Thanks

---

### Post by helenka on 2009-01-12
I actually have a similar problem, the only differences being make of computer (Dell) and that the OS doesnt even acknowledge the presence of a USB device. Any suggestions?

---

### Post by baller_2003 on 2009-01-12
Well I actually read that some Creative ZENs will actually work if you install Gnomad 2, onto your os. This may work for you, but I couldn't get it to work for me. I guess it also depends on what type of ZEN you have. My ZEN is called Mosaic. Like I said you might try it and see if the program will work for you. Send me something if you need help installing it.

---

### Post by banana jama on 2009-01-12
i also have a creative zen i got mine to work by opening rythmbox and going to edit ---> plugins and checking off portable player mtp. once you do that rythmbox will recognize your zen and using ryhtmbox you can put/take music/videos on your zen by draging and droping. only ryhtmbox will be able to recoginize your zen not the os which means you will have to use rythmbox to do all of your mp3 managing. hopes this helps.

---

### Post by baller_2003 on 2009-01-15
Sorry it took me so long to get back with you guys, but that last solution didn't work for me either, I did figure out that my laptop isn't even recognizing it when I plug it in to the usb. I was mistaking for what it was detecting for my printer. Any more suggestions?

---

### Post by joanmunoz on 2009-01-27
Same problem to me. And tried lot of usb libraries, Gnomad2 libraries, bla, bla, bla...nothing seems to work!!

---

### Post by baller_2003 on 2009-01-29
Ok here's how I got mine to work finally. I created a Virtual Machine of XP using virtual box. I'll have to admit that it took a little bit to get the usb interface going, but after that it was all smooth sailing. If you decide to try this and you run into the same problem I had with the usb, please visit the following link: [http://linuxmini.blogspot.com/2007/10/virtualbox-usb-setting-on-ubuntu-and.html](http://linuxmini.blogspot.com/2007/10/virtualbox-usb-setting-on-ubuntu-and.html) . If you have issues with this and your not sure what to do, just pop a reply back and I will help you any way I can.

---

### Post by ghohn on 2009-04-01
Seconded.  Rythymbox worked for me with MTP checked.  Thanks!

---

### Post by adm1968 on 2009-05-20
[FONT="Georgia"]My system does see my Zen Mosaic:

art@pavilion:~$ lsusb
**Bus 001 Device 010: ID 041e:4161 Creative Technology, Ltd** 
Bus 001 Device 005: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 004: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller
Bus 001 Device 002: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

but neither Amarok, nor Rhythmbox, nor Gnomad, nor KZenExplorer detect anything at all

:-?[/FONT]

---

### Post by dave r on 2009-05-20
I have one of these [http://audiovisual.kelkoo.co.uk/p-mp3-players-122701/creative-zen-32-gb-19363312](http://audiovisual.kelkoo.co.uk/p-mp3-players-122701/creative-zen-32-gb-19363312) 32gb player. I don't have a problem with the computer seeing the player. At the moment I am using the Banshee music player to drag and drop music into it. With my original  8.10 and the amarok player that came with it I was using amarok to transfer music to the player, Since the upgrade to 9.04 and the new amarok both amarok and rhythmbox players will see the player and drop music files into the player but then the player won't see the music, some sort of problem with the tag information? The other player, gnomad, would not see the player

---

