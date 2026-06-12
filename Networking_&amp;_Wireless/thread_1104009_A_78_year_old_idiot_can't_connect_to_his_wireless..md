---
title: "A 78 year old idiot can't connect to his wireless...HELP PLEASE!"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by jkjk222 on 2009-03-23
Hi....I'm sure the answer is somewhere in these forums, but heaven help me, I'm really stuck!   I have a LinkSys wireless router, which is working just fine for 2 Vista laptops, and was also working for an XP laptop (HP ze4805) before I did total install of Ubuntu 8.10, and formated the entire hd for Ubuntu.   8.10 working fine, except I simply can not get the notebook (laptop) to see the wireless signal for Ubuntu.  It might be a driver issue, but just don't know.  The ubuntu pc DOES recognize a little flash drive when plugged into the usb port, and also will read/copy files from the flash drive.   Any help will be appreciated...I'm frustated to the nines, but would really like to get 8.10 to work, and see if I like it as much as I think I might.    Thanks for any help.

PS.  I've used MS DOS and Windows for over 30 years, but am really a boob with Linus/Ubuntu.  I have a couple of books (The Official Ubuntu Book---second edition), and access to Ubuntu for Dummies and a couple move, but am really stumped...:(

---

### Post by BkkBonanza on 2009-03-23
I think people will need to know what wireless adapter your notebook has to help.
Make, model and sometimes even revision # matters.

---

### Post by ELD on 2009-03-23
Yeah we need to know what wireless card your notebook has to be of any help.

---

### Post by jkjk222 on 2009-03-23
Thanks to the two of you who responded so quickly.  If the old HP were still on windows, I could tell you something about the wireless card that is in there, but with it being on Ubuntu, I can't get there from here.  I'll bet there's a way with 8.10 to take a look at what hardware is on the notebook, but it will take me a while to figure out how to get into it enough to give more info on the wireless card.  I'll get to work on it right not.

---

### Post by BkkBonanza on 2009-03-23
Have a look at the sticky at top of this forum section about "what cards are supported". It gives details about how to determine your adapter type.

---

### Post by Kevbert on 2009-03-23
Please go to Applications-Accessories-Terminal and enter the following command
```
lspci
```
From this you should get a load of text including a line like this:
```
01:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```
This is the line you need to look for where it states the Network Controller (wireless card). We need the manufacturer(e.g. Broadcom), model (e.g. BCM4306) and revision (e.g. rev 03) from this we can recommend how to install the wireless drivers.

---

### Post by chili555 on 2009-03-23
Let's take the easy way out: ask the computer! Open up a terminal and do:```
sudo lshw -C network
```Post the result and we'll help you get it going.

---

### Post by jkjk222 on 2009-03-23
OK folks, and thanks for the replies.....I'm going from one notebook to the other, so rather slow here.

When I input lspci, one of the many lines that popped up was this"   Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02).


When I input sudo lshw -C network, and then my password, I got about 50 lines of stuff, which will take some time for me to copy here for you....however, included in the lines is "network:0 DISABLED"......and "network 1 DISABLED"

---

### Post by zmjjmz on 2009-03-23
The BCM4306 is supported, you just need an internet connection (wired) to download the driver. If I remember correctly, plugging it in to the ethernet and getting a connection then installing b43-fwcutter should work.

---

### Post by ELD on 2009-03-23
> **zmjjmz said:**
> The BCM4306 is supported, you just need an internet connection (wired) to download the driver. If I remember correctly, plugging it in to the ethernet and getting a connection then installing b43-fwcutter should work.

Yeah all you will need to do is to plug your notebook into your router and use that net for a minute or two to get the driver for it and you should be fine after that.

---

### Post by Spikerok on 2009-03-23
wired connection worked for me on 8.10, on 8.04 wireless works perfectly..

---

### Post by ELD on 2009-03-23
> **Spikerok said:**
> wired connection worked for me on 8.10, on 8.04 wireless works perfectly..

Your point being?

---

### Post by Kevbert on 2009-03-23
Have a look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13"). The firmware is attached and it details how to install the driver.

---

### Post by jkjk222 on 2009-03-25
Thanks again for the help...I've found and downloaded the driver and it's on my 8.10 desktop.  The folder contains several files.   But now I'm still stuck....which file(s) do I use, where do I place/paste them, and how do I activate the proper one so the notebook will be able to see my wireless modem?    Sorry to be such a pain....many thanks.

---

