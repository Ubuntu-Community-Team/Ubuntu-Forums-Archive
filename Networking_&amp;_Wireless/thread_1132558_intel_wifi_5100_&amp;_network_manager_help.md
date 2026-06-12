---
title: "intel wifi 5100 &amp; network manager help"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by Dalai0lama on 2009-04-22
Well first I'm completely new to linux so please be easy on me. 
 
I recently installed intrepid and I'm having problems connecting to my network. I have a intel wifi link 5100. I did find out that the device is disabled but I can't seem to find a way to enable it. I hoped that visiting intel's site would help but of course i didn't find any. I finally visited the help & support but to enable the card it says to use "network-"manager". My luck I couldn't find "network-manager" anywhere. Synaptic package or update (again a complete noobie sorry) says it's installed. Also there is no network icon on the taskbar. Am i just missing something obvious?

---

### Post by geekswithguns on 2009-04-24
I'm having the same problem. Brand new laptop (Sager), running Jaunty Jackalope with an Intel WIFI Link 5100 card. It shows up as UNCLAIMED. 

Tried the "Windows Wireless Driver" utility (ndisgtk)to no avail. The driver is installed, but I get an error of "Unable to see if hardware is present" (Even though under the driver it says "Hardware Present:Yes"). Then when I click on "Configure Network" it responds with an error stating "Could not find network configuration tool." 

I also followed the "Getting compat-wireless on Ubuntu" instructions from linuxwireless.org:

"With Ubuntu you have the option of either installing compat-wireless yourself or of installing the package that provides it built by the Ubuntu kernel team. The Ubuntu package that carries compat-wireless is called linux-backport-modules and it has more backported modules than just your wireless subsystem. Its updated whenever major updates are pushed out into the wireless-testing git tree. 

# For Ubuntu 9.04 Jaunty users:
sudo apt-get install linux-backports-modules-jaunty"

Still no luck....

---

### Post by geekswithguns on 2009-04-25
So any advice from long time Ubuntu users for us new guys (and gals)?

---

### Post by geekswithguns on 2009-04-25
OK- this fixed it for me: 

Fresh install

sudo apt-get install linux-backports-modules-jaunty

and that was it!

---

### Post by ilhamwk on 2009-04-28
This doesn't resolve the problem on my laptop, unfortunately.

---

