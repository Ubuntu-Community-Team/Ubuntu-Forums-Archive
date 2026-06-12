---
title: "BCM4318 Wireless card in Ubuntu 8.10 with ndiswrapper"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by DJYoshaBYD on 2009-02-24
OK.. This is how I got the Broadcom BCM4318 Wireless card in my Compaq m2105us to work.. this shoud work with just about every distro...

FIRST, download the following zip file.. it contains the correct version of this driver
[URL="http://fedorasolved.org/mobile/fc-wireless/80211g.zip/view"]
http://fedorasolved.org/mobile/fc-wireless/80211g.zip/view[/URL]

NEXT, bust out your Ubuntu CD and go to /pool/main/n/ on the CD.. Install EVERYTHING that says ndiswrapper.. 

Restart PC (this is just me.. ex windows user.. lol)

Now, go to system - Administration - Windows Wireless 

Next, unzip the file you downloaded somewhere handy, like the desktop, Home, etc..

NEXT, click INSTALL DRIVER

Browse to wherever you stored the extracted zip file..

Select BCMWL5.INF

It will install the drivers..

After a few minutes, you should see your wireless light on your notebook start to flash.. THIS IS OK.. I noticed that if it is not connected, it will flash, but will function just as normal, and will stop flashing when connected..

If anything, try a restart and see if it brings it up..

THIS WAS NOT DONE ON A FRESH INSTALL, BUT I DID UNINSTALL THE OLD B43 STUFF..

If you are having problems loading the driver at boot, then do the following:

go to a terminal

type:

sudo gedit /etc/modules


enter your password, then when gedit opens up, add the following at the bottom of the page on a free line

ndiswrapper

that right there will tell the system to load ndiswrapper at boot..

Now, this is just what I did.. I have seen (and tried) MANY different ways.. The only thing I noticed about ndiswrapper is it wont connect to  WPA secured network.. although, it may just be screwing something up.. B43-fwcutter works too, but I have VERY slow speeds, and I cannot connect to WEP networks and ones that are more than 20 feet or so away, if that..

With ndiswrapper AND THE DRIVER LISTER ABOVE, I can now get in to just about any open network and good distances... I just cant get WPA to work, but thats a different story..

I have had nothing but problems with doing this, and now that I got it right, I had to share..

Good luck, and feel free to email me or something if you have any questions

[email]DJYoshaBYD@yahoo.com[/email]

hope this helps.. I LOVE LINUX!!!!

Joosus:guitar::guitar:

---

### Post by DJYoshaBYD on 2009-02-25
soooo.. yeah.. I just did this again to 3 different laptops with the same card.. I also used ubuntu/kubuntu/xubuntu 8.04, 8.04.1, and 8.10.. all of them worked FLAWLESSLY...

I was just searching through and notices that someone else asked how to do this.. they are using b43-fwcutter... and they will most likely be back with probs just like I was.. lol..

again, hope this helps...

---

### Post by DJYoshaBYD on 2009-04-25
just wanted to bump this.. I just had to do a reinstall, and did this, and it worked perfectly...

---

