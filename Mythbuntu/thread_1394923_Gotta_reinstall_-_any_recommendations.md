---
title: "Gotta reinstall - any recommendations?"
date: 2010-01-31
forum: Mythbuntu
---

### Post by Juzz on 2010-01-31
OK, so I am basically at the point where I am about to reinstall mythbuntu in order to get my DVB-C cards to work.

My config is this:

Asus A8R32-MVP Deluxe
AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
2GB RAM
iMON PAD Remote Controller
GT200 [GeForce 210]

I currently use Hauppauge PVR 150 tuners, but I want to use my Terratec Cinergy C PCI DVB-C cards - however none of my attempts at getting them going have been successful.

Will it be ok to install a 64-bit version of mythbuntu?

My current checklist before the install:
[LIST]
[*]Backup the database
[*]Make a backup of my scripts for recording conversion (into x264)
[*]Make a backup of my xmltv scripts
[/LIST]

And of course taking out the hauppauge and putting in the dvb-c cards.

Any further recommendations?

---

### Post by williammanda on 2010-01-31
I'm not sure why your re-installing at this point but from a testing stand point I would go ahead and remove the pvr-150 and install the DVB-C cards and try it.

---

### Post by Juzz on 2010-01-31
Well that's what I've tried...

I've even tried compiling the drivers, banning ivtv - anything that has been suggested.

---

### Post by azmyth on 2010-01-31
I'd grab your channel icons too. I dl'd a bunch manually that the grabber couldn't find and entered into myth manually. I hate to do that again.

---

### Post by williammanda on 2010-01-31
I would install the dvb-c cards and then run lspci to see what is registering. You should get something like TDA10021 or TDA10023 or Philips SAA7146. It says on the linuxtv.org site that they are supported from kernel 2.6.22. Have you tried the cards out to see if they actually work?

---

### Post by Juzz on 2010-02-02
Thx for the tip on the icons.

I did put them in and compare the lspci with the linuxtv wiki and it's the same output.

---

### Post by diskmaster23 on 2010-02-03
Are you using 9.04 or 9.10?

---

### Post by Juzz on 2010-02-03
9.10

But it seems the mantis driver is missing?

---

### Post by Homer_DK on 2010-02-13
Hi Juzz

I dont think it will help to reinstall. I just got the Terratec Cinergy C PCI HD tuner, and just installed MythBunto 9.10. No tuner in sight

If i do a lspci i can see it as an Twinhan.

I tried this to get it to work:
Updated Mythdora (159 updates)
activated ati-driver
Installed kernel-sources

At this point system reboots fast and with no errors
(I'm missing sound with HDMI)
Then i tried this:

cd /usr/src
sudo apt-get install mercurial
sudo hg clone [http://jusst.de/hg/mantis](http://jusst.de/hg/mantis)
cd mantis
sudo make (i get 2 errors)
sudo make install (errors here also)
sudo reboot

My system reboots, but i get a black screen

I have to reinstall  :-(

---

### Post by Juzz on 2010-02-13
No, that's probably the ivtv driver conflicting with the mantis driver...

I've decided to sell the terratec cards and I've bought a knc1 card from electrola (quick delivery).

But if you insist on using the terratec then pull out the card, boot up and rename the ivtv and ivtvfb drivers to something else.

then you can put in the terratec card and boot up again.

---

### Post by Homer_DK on 2010-02-13
I don't insist on using the Terratec :-) I just got it, so i have to give it a go.

I try removing the ivtv driver and keep my fingers crossed. Thanks for the tip.

Please let me know if the KNC card is working out of the box.

Best regards

---

### Post by Juzz on 2010-02-13
The knc card worked out of the box, but the channel searching could be made easier...
(as in the drivers load and I can interact with the card)

I have gotten some info on the channels and all that and have made myth make a scan, but I've got to check the settings - 'cause it seems at least one channel isn't good (but I don't have the time to look at it today).

But if you go for the knc card - then reinstall the current kernel (to reinstall the modules and remove the compiled ones).

---

### Post by Juzz on 2010-02-14
I just found out that it was the old analog channels that was still in and that the tuner card had been set to try to start up on one of those in mythbackend...

After I've set it to a digital channel - it works :D

---

### Post by Homer_DK on 2010-02-21
Hi Juzz

Good news, happy to hear that it works. Maybe i should get me another card.

Did you get the KNC DVB-C or the plus version with the Cineview CI-modul? Do you know if the CI-modul works with Mythbuntu?

What do you mean by "the channel searching could be made easier"?

I know a lot of questions - sorry.

Best regards

---

### Post by Juzz on 2010-02-21
The one I have is the KNC DVB-C without the CI module.

You have to use w_scan to get the initial channels.conf and then load that up, when you have to scan for channels.

Take a look here:
[http://www.linuxtv.org/wiki/index.php/DVB-C_PCI_Cards](http://www.linuxtv.org/wiki/index.php/DVB-C_PCI_Cards)

---

