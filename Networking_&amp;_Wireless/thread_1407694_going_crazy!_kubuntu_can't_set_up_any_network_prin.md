---
title: "going crazy! kubuntu can't set up any network printers"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by bottleman on 2010-02-15
Hi, 

I've had Kubuntu 9.10 32-bit running on my laptop since it came out, but in the past month all its networked printers have disappeared from the configuration, and I can't set up any more.  

I've been through the forums again and again and cannot fix it.  I've installed and reinstalled lots of packages related to CUPS but it doesn't seem to make a difference.

I'm not sure what has happened, but I have lots of clues.  Since I'm reaching the limit of my know-how here, I'll just list all the clues.

I'm pretty sure the problem is in my Kubuntu laptop, because in my SOHO setup I also have a Kubuntu 9.10 desktop (this time 64 bit) connected to a printer, and I have successfully printed through that from both a Windows XP laptop and a Xubuntu 9.10 box.

On the Xubuntu 9.10 box, I just asked for the GUI print configurator and it automatically detected the network printer.  No muss no fuss.

But on the Kubuntu laptop, when I go into the print configurator, here's what happens:
- it shows two options, "new printer" and "server settings" (image a.png)
- entering "server settings" everything is greyed out and unchangeable (image b.png)
- entering "new printer" shows only one option for a connection, "other" (image c.png)
- after entering the address of a printer i know works (image d.png) the configurator has detected the printer (image e.png)
- but then attempting to move forward it crashes with no explanation.

Running the non-kubuntu version of the configurator GUI provides a bit more information before it fails.  When I try to access the desktop with the printer attached it wants a username and password.  (which wasn't necessary for the two client machines who successfully printed.) And at the end of the process there is an error: "there was an error during the CUPS operation: client-error-forbidden".

Two more clues:
- when I try to go with my browser to localhost:631 the browser can't establish a connection
- but I can see the cups page on the printer's host machine at 192.168.0.104:631 no problem.

Any help would be a great assistance to my sanity.  Thanks so much!

---

### Post by johnson.d on 2010-02-18
Server Settings are grayed out when cups service is not running on the localhost.You can check whether CUPS has been installed in your Kubuntu system by using the command:

```
$ sudo dpkg -s cups
```

If it shows "Status: install ok installed", It show that CUPS has been installed.

Then you need to check whether CUPS is running or not. You can do this by using the following command:

```
$ sudo /etc/init.d/cups status
```

If it is not running use the following command:

```
$ sudo /etc/init.d/cups start
```

Now you can follow the same procedure you were performing before and try again.

---

### Post by bottleman on 2010-02-18
Thanks Johnson.  The problem turned out to be a missing configuration file, cupsd.conf  .   Once I replaced that cups would start.  Described in more detail here: [http://kubuntuforums.net/forums/index.php?topic=3110088.0](http://kubuntuforums.net/forums/index.php?topic=3110088.0)

---

