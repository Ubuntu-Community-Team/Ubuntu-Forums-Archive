---
title: "Adding network printer?"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by LinuxBob on 2009-08-10
I am using 9.04 on a new PC from Zareason.

The whole add printer interface looks different  System > Administration > PRinting > Server > New > Printer , the only printer found is the USB attached photosmart.   I have two other HP (LaserJet 4L and All In ONe 6110 Office Jet) connected via print servers with assigned IP addresses.  I Can ping the LAserJet addy, and it works with over the network with my other Ubuntu 9.04 machine (used IP address to add a few months ago but forgot exactly how, in any event the new interface looks different). 

So I know it works, how do I get it to work with this new PC?

---

### Post by ForMar on 2009-08-11
I find it easy to use the web interface though its not for everyone

in the address bar put the address of the computer followed by :631 

ex:
192.168.1.2:631

hope that helps gl

---

### Post by LinuxBob on 2009-08-11
:631?

I will try it when I get home.  The computer IP address preceding the :631 is the print server?  I am not using a PC for this function.  I have a Netgear print server and a Dlink print server with assigned IP addresses.

---

### Post by ForMar on 2009-08-11
humm im not sure then it depends what protocol they are using which might just be the source of your problem which unfortunately is beyond my scope. What i do know is that *unix uses a protocal called CUPS developed by apple and anything that runs CUPS *should* have a web interface at port 631 this could be different for you or they could not be using cups thats something you should look into.
good luck

---

### Post by LinuxBob on 2009-08-11
Look I know people on here have done this.  I want to add a network printer using dedicated hand-szed print servers with assigned IP addresses.  Apaprently, Ubuntu has changed the printing interface as I describe above.  How do I add the printer?

---

### Post by LinuxBob on 2009-08-11
> **ForMar said:**
> I find it easy to use the web interface though its not for everyone

in the address bar put the address of the computer followed by :631 

ex:
192.168.1.2:631

hope that helps gl

This did not work, web page came back as though I were offline yet I can ping the print server IP just fine.

---

### Post by Cope57 on 2009-08-11
Type or click **[http://localhost:631](http://localhost:631)** in the address bar of your browser.
This will bring you to the local cups page if **cups** is installed.

You will find printer settings there for printer server.

---

### Post by LinuxBob on 2009-08-11
Cope 57

Making some progress but says printer is busy.  What should be my device URL with sassigned IP to print server?  The attached printer is HP LAserJet 4L.


By the way, what si the "localhost" I am connecting too?  My laptop? another PC on LAN?  Print server?

---

### Post by LinuxBob on 2009-08-11
OK success acessing HP LaserJet via DLink print serve doing the following from another thread:

*** the localhost:631 option worked perfectly when installing my networked HP Photosmart P1000 printer using a DLink DP-311U print server. For those of you new to Linux (as I am!), here's how:

* Open your web browser and type in "http://localhost:631" into your address box.
* Click on the "Add Printer" button.
* On the "Add New Printer" page, enter the following information:
- Name: <name for your printer, BUT DON'T USE ANY SPACES! For example, mine is simply "HP1000">
- Location: Doesn't matter. Leave blank, if you want. Or enter the location of Jimmy Hoffa's body, for that matter. Yer choice.
- Description: Doesn't matter. I entered the full name of my printer, which is "Photosmart P1000".
* Click "Continue"
* You should now see a box marked "Device". It's a drop-down menu. Since I'm using a DLink print server, I chose "LPD/LPR Host or Printer". You may have a different device.
* Click "Continue"
* You should see a box named "Device URI". Again, if you're using a DLink 311U (as I am), type in "socket://<DLink IP address>. For example, the IP address of my DLink is 192.168.100.55. So, I typed in "socket://192.168.100.55".
* Click "Continue"
* You now need to enter the manufacturer of your printer. I scrolled down and selected "HP".
* Click "Continue"
* Yet another page that might trip you up. You need to select the particular model of your printer. The problem is that there are several models of "HP Photosmart P1000" listed. I selected the "HP Photosmart P1000 Foomatic/hpijs (recommended) (en)". There seems to be one that is "recommended" for each model. I suggest going with that for the first try. If it doesn't work, you will have to try others.
* Click "Add Printer"
* If everything works, you should see a message such as, "HP1000 successfully added!"

You should see a tab along the top of the page that says, "Printer". Select that, then look for a button "Print Test Page". If you press that button and get a proper print-out, you're set!***

Now the weird part.  Doing the samer thing from my new Zareason Ion Breeze I can set up the networked printer but when I hit print tests page the Ion Ubuntu tells me everything printed out fine, no wait, no delay, all is cool.  But it isn;t.  Nothing printed out.  I changed the 4L device and same thing.

Any ideas????????

---

### Post by LinuxBob on 2009-08-11
bump

Surely people have done this successfully.

---

### Post by LinuxBob on 2009-08-17
bump

need ot get this working

---

### Post by AJB2K3 on 2009-08-17
Have you tryed the HPLIP package as that's what I use to connect to my HP photosmart 8450 via the network but for some reason I have to shut down the firewall to print

---

### Post by LinuxBob on 2009-08-18
The network printing problem is solved.  I bought a new all in one wireless capable printer and it worked first time with the Zareason using the localhost:631 network printer setup.  That led me to believe the Dlink printer server had a permission issue.  That was the case, though difficult to get pointe idn that direction when CUPS tells you the print job completes OK.

The DP-301P+ requires a mac address when the user permission feature is turned on.  The Dlink accepts a mac address with a space between the hexadecimal pair of numbers, not a colon.  

Thanks for all the helpful responses to my posts.

---

