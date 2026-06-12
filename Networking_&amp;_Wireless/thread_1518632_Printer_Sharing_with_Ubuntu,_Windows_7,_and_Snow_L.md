---
title: "Printer Sharing with Ubuntu, Windows 7, and Snow Leopard"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by Hobbesie on 2010-06-26
Hey all,

I'm brand new to Ubuntu, and installed it on a desktop today to try it out. So far I'm loving it and have gotten everything to work except for one thing:

There's a printer connected to it (HP PSC 1600), and I'd like the other computers on the network to be able to print to that computer. The other computers are running Windows 7, and one is running Snow Leopard. 

When I plugged in the printer, Ubuntu recognized it almost immediately and installed it. Wonderful! I then went ahead and set it to be Shared, and hoped for the best. Neither the Windows machine or the OS X machine could find the printer...even after I pointed them directly at what I thought was the CUPS address (\\mycomputername:631). To make matters even more confusing, I was able to set up shared folders and have the other computers be able to view them.

What am I doing incorrectly? Any suggestions would be **greatly** appreciated. 

Thanks in advance!

---

### Post by marshmallow1304 on 2010-06-26
In System->Administration->Printing, open Server->Settings and make sure "Publish shared printers connected to this system" is checked.

---

### Post by Hobbesie on 2010-06-27
> **marshmallow1304 said:**
> In System->Administration->Printing, open Server->Settings and make sure "Publish shared printers connected to this system" is checked.

Good call! I'll try that out and let you know what the result is.

---

### Post by Hobbesie on 2010-06-27
Alright! Partial success! Your suggestion worked quite well for the most part. The Windows 7 machines are now happily printing to the Ubuntu shared printer. It didn't find them automatically, but once I put in the actual address it worked out just fine.

The computers running OS X, on the other hand, are still having a bit of an issue. They don't seem to be able to find the printers on the network, even when I punch in the IP address of the Ubuntu machine. I've tried using IPP, Jetdirect, and the other option (can't quite remember what it is :P ), but to no avail.

The help you've given me so far has been invaluable...thanks so much!

---

### Post by Morbius1 on 2010-06-27
In the IP section are you using entries with this type of format:
 
**Protocol:** Internet Printing Protocol
[B]
Address:[/B] 192.168.0.100:631
[B]
Queue:[/B] printers/Linux-Printer-Name

---

### Post by Hobbesie on 2010-06-28
> **Morbius1 said:**
> In the IP section are you using entries with this type of format:
 
**Protocol:** Internet Printing Protocol
[B]
Address:[/B] 192.168.0.100:631
[B]
Queue:[/B] printers/Linux-Printer-Name

Went ahead and plugged all of that in...OS X recognizes the location as a valid address, and doesn't throw any errors. It lists the printer without a name, only as an IP address. When I try to print, it initially starts printing and then says that the print job has been paused.

Any suggestions?

---

### Post by Morbius1 on 2010-06-28
> **Hobbesie said:**
> Went ahead and plugged all of that in...OS X recognizes the location as a valid address, and doesn't throw any errors. It lists the printer without a name, only as an IP address. When I try to print, it initially starts printing and then says that the print job has been paused.

Any suggestions?

I assume osx asked you for a printer driver?

Does the printer name have spaces in it?

When you say it starts printing, do you mean it physically starts printing and then stops or the print dialog says it's printing and then stops.

---

### Post by Hobbesie on 2010-06-28
> **Morbius1 said:**
> I assume osx asked you for a printer driver?

Does the printer name have spaces in it?

When you say it starts printing, do you mean it physically starts printing and then stops or the print dialog says it's printing and then stops.

Interestingly, OS X didn't ask me for a printer driver. It just went ahead.

The printer name has dashes in it, no spaces (PSC-1600-SERIES).

Lastly, the printer doesn't physically do anything. The dialog comes up, then shows as paused.

---

### Post by Morbius1 on 2010-06-28
Creating a new printer from the "IP" button seemed quirky to me so this is the exact method I used to connect a macbook to a linux attached printer. If nothing else it will give your Mac more functionality :p

1. Apple menu > Print & Fax 
2. Click the + button under the printers list to add a printer.
3. Press the Control key while clicking the "Default" icon then choose Customize Toolbar from the  menu.
4. Drag the Advanced (gear) icon to the toolbar and then click Done.
5. Click the Advanced icon that was added to the toolbar.
6. Choose "Internet Printing Protocol" from the Type pop-up menu.
7. In the URL field, type the printer's address:
    
ipp://192.168.0.100:631/printers/PSC-1600-SERIES

NOTES:
If the printer name contains spaces, replace each space with "%20" (without quotation marks).

In the Name field, type the name you would like to use for this printer in Mac OS X.

Choose the appropriate PPD or printer driver from the "Print Using" menu.

---

### Post by Hobbesie on 2010-06-30
> **Morbius1 said:**
> Creating a new printer from the "IP" button seemed quirky to me so this is the exact method I used to connect a macbook to a linux attached printer. If nothing else it will give your Mac more functionality :p

1. Apple menu > Print & Fax 
2. Click the + button under the printers list to add a printer.
3. Press the Control key while clicking the "Default" icon then choose Customize Toolbar from the  menu.
4. Drag the Advanced (gear) icon to the toolbar and then click Done.
5. Click the Advanced icon that was added to the toolbar.
6. Choose "Internet Printing Protocol" from the Type pop-up menu.
7. In the URL field, type the printer's address:
    
ipp://192.168.0.100:631/printers/PSC-1600-SERIES

NOTES:
If the printer name contains spaces, replace each space with "%20" (without quotation marks).

In the Name field, type the name you would like to use for this printer in Mac OS X.

Choose the appropriate PPD or printer driver from the "Print Using" menu.

I went ahead and tried that, but no dice. Pretty much the same thing happens. 

I've also noticed something bizarre...the printer won't print any PDFs if they're printed from Windows.

I feel like we're getting very close!

---

### Post by Morbius1 on 2010-06-30
I decided to try something completely different and go to the Apple Forums and I found something rather interesting:

[http://discussions.apple.com/thread.jspa?threadID=322338&tstart=0&messageID=1554050](http://discussions.apple.com/thread.jspa?threadID=322338&tstart=0&messageID=1554050)
> 
- Driver. The driver provided by HP doesn't work for network printing,  because it has USB comm built-in in the driver, efffectively limiting it  to USB. You need a CUPS driver to print via network. You can probably  use the HP Deskjet 900 Series Gimp-Print driver included in Tiger, but  if that doesn't work, install hpijs and ESP ghostscript from:
[http://www.linuxprinting.org/macosx/hpijs/](http://www.linuxprinting.org/macosx/hpijs/)It talks about tiger as this is rather old but here's another one that's more recent:
[http://discussions.apple.com/thread.jspa?threadID=2172648&tstart=399](http://discussions.apple.com/thread.jspa?threadID=2172648&tstart=399)
> The reason you don't see the driver when trying to print via Windows PC,  is that the driver provided by HP was intentionally limited to USB  only. You need to install the hpijs 3-part driver set, which provides a  CUPS driver that IS capable of Windows printing. HP Jetdirect protocol  is for printers that are directly connected to ethernet by internal or  external print server. With the correct driver installed, you can read  about how to add the printer in Mac Help. Search for "share windows  printer."

[http://www.linuxfoundation.org/en/OpenPrinting/MacOSX/hpijs](http://www.linuxfoundation.org/en/OpenPrinting/MacOSX/hpijs)         This one talks about accessing a Windows attached printer but CUPS is CUPS.

I think that the default printer driver for this printer in OSX is not capable of accessing a remote networked or shared printer and another driver needs to be installed. This is just a guess on my part :wink:

---

### Post by Hobbesie on 2010-07-02
> **Morbius1 said:**
> I decided to try something completely different and go to the Apple Forums and I found something rather interesting:

[http://discussions.apple.com/thread.jspa?threadID=322338&tstart=0&messageID=1554050](http://discussions.apple.com/thread.jspa?threadID=322338&tstart=0&messageID=1554050)
It talks about tiger as this is rather old but here's another one that's more recent:
[http://discussions.apple.com/thread.jspa?threadID=2172648&tstart=399](http://discussions.apple.com/thread.jspa?threadID=2172648&tstart=399)
This one talks about accessing a Windows attached printer but CUPS is CUPS.

I think that the default printer driver for this printer in OSX is not capable of accessing a remote networked or shared printer and another driver needs to be installed. This is just a guess on my part :wink:

It worked! The iMacs can all happily print (once in a while they get portrait/landscape confused) after following your instructions! Thank you so very much!

All I need to do now is figure out why PDFs don't print from Windows, and everything will be taken care of!

Mobius, you've been more than helpful...I really appreciate the aid.

---

### Post by Morbius1 on 2010-07-02
>  All I need to do now is figure out why PDFs don't print from Windows,  and everything will be taken care of!
Actually I have this problem as well but not all pdf's just some of them. I have no idea what's going on with this.

---

### Post by rh10023 on 2010-09-06
Anyone try using the hplip 3.10.6?  I was able to get printing working using the IPP route.  But it still begs the question about what is different about printing between Ubuntu 8.04 and 10.04 that Mac OSX clients can't see the printers on the Ubuntu box through Bonjour?

I had shutdown cups before running the hplip-3.10.6.run.

---

