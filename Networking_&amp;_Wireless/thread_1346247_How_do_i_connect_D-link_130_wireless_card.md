---
title: "How do i connect D-link 130 wireless card?"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by soundout on 2009-12-04
I have a d-link 130 wireless external usb card and i do not know how to connect to the internet. what drivers/files or w/e do i need to install for it to work?

---

### Post by bkratz on 2009-12-04
> **soundout said:**
> I have a d-link 130 wireless external usb card and i do not know how to connect to the internet. what drivers/files or w/e do i need to install for it to work?



That really depends on which  (I assume you meant DWA-130) version of the card you have there are 4-- a,b,c,d.  If you have version a or b you will have to use ndiswrapper and the windows drivers on the disk you received. B doesn't seem to work to well generally there are a lot of dropouts, C has Linux drivers available on the website and I don't know about D.  Which do you have?

---

### Post by soundout on 2009-12-04
> **bkratz said:**
> That really depends on which  (I assume you meant DWA-130) version of the card you have there are 4-- a,b,c,d.  If you have version a or b you will have to use ndiswrapper and the windows drivers on the disk you received. B doesn't seem to work to well generally there are a lot of dropouts, C has Linux drivers available on the website and I don't know about D.  Which do you have?

i have yes DWA-130 card a.
can you give me step by step directions.

---

### Post by bkratz on 2009-12-04
> **soundout said:**
> i have yes DWA-130 card a.
can you give me step by step directions.

Sure,

First you need two files from the section of device drivers used for XP from the disk Mrvw245.sys and netmw245.inf...
Put these somewhere.... like your home directory.

Go to system---administration--- Synaptic package manager
press reload (not really necessary) to update the listing
search for Ndisgtk and mark for installation
This will actually load 3 files
Allow it to load all three

When done go to system---administration--windows wireless drivers
Plug-in in the USB dongle
select install new driver
you then will have to "find" the .inf file you put in your home folder.
Install it
The pop-up box will still say hardware present:No , but ignore it
If you happen to press configure network it will say something like no tool found--ignore that too.
close it.

You will probably see it flash now.

The rest of the configuration is done from the icon on the top right of the screen.
Right click on it and select edit connections.
here is where you put in your particular information
select the wireless tab
press  add
enter your SSID of your A/P and tick available to all users
under IPv4  method=automatic (DHCP)
wireless tab is where you put in the security requirements.

This is important---right now there is a "bug" in ndiswrapper which prevents you from using encryption on your network. Hopefully, it will be fixed soon. For now you must use no encryption.

disconnect your ethernet cable

Close this and left click on the same icon--you should see any available networks including yours.
You should just be able to click on yours and connect.

I will subscribe to this thread and look tomorrow to see how it went for you.

---

### Post by camrant on 2009-12-07
What if you have Ver C? Can you give instructions for this card.

---

