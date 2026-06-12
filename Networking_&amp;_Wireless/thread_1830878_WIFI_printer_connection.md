---
title: "WIFI printer connection"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by gulmer on 2011-08-22
Here's the situation, I've got Ubuntu on a laptop and desktop. Laptop connects to the router wireless and desktop connects w/cable. Desktop is connected to printer with USB cable. I would like to connect to the printer using the router through the desktop to printer. Is this a possibility? A friend had her XP laptop and XP desktop configured this way and I would like to do the same.

---

### Post by praseodym on 2011-08-22
You can use cups to setup the printer as network-printer. In FF:

[http://localhost:631/admin](http://localhost:631/admin)

Or by terminal. On Desktop:

```
cupsctl --share-printers
```
On notebook:

```
cupsctl --remote-printers
```
After that you should be able to setup the network-printer on your notebook.

---

### Post by gulmer on 2011-08-22
Not sure what I did but I got the laptop to print with the printer connected to the desktop through the router. I just followed the prompts when adding a printer to the laptop,with the trouble shooting guide until it worked, took about 10 minutes. Just got to love Ubuntu.  :guitar:

---

### Post by praseodym on 2011-08-22
I have the same setup here: USB-Printer on a Desktop-PC connected to a router. Printing works with the notebook with this description.

---

