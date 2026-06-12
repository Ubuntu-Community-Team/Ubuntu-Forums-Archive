---
title: "Installing Samsung 2851ND printer on network with Ubuntu"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by Dingo_aus on 2010-02-11
I bought a new Samsung ML-2851ND.

I intend to connect it via the ethernet port is has.

Under Ubuntu you cannot just plug and play.  To set it up you need to connect it via a USB cable (Ubuntu will have all the needed drivers to operate as soon as you plug it in).

Then you can go into the advanced settings for the printer and set up the network settings with the right gateway, subnet and IP address.

Once you do this you can http into the address and play with all the other settings.

Please note that Samsung have fantastic Linux support and you can download the driver etc here:
[http://www.samsung.com/au/consumer/print-solutions/print-multifunctions-copiers/mono-laser-printer/ML-2851ND/XSA/index.idx?pagetype=prd_detail&tab=support](http://www.samsung.com/au/consumer/print-solutions/print-multifunctions-copiers/mono-laser-printer/ML-2851ND/XSA/index.idx?pagetype=prd_detail&tab=support)

All options are supported (1200dpi, duplex, toner save etc).

Kudos to Samsung for making a Linux friendly product.  This is the second Samsung I have and I bought it because the first worked so well with Linux. If I need to buy another Samsung are my first preference.

---

### Post by dc46and2 on 2010-11-27
I had a slightly different experience and I'm sharing for other's reference.  The printer worked as soon as I plugged it in via USB and added the printer via System > Admin > Printing.

However, it was apparently using a generic Postscript driver, and not all of the printer's options were available (such as toner saver).  I download the driver archive from samsung, extracted it, and copied cdroot/Linux/noarch/at_opt/share/ppd/ML-2850ps.ppd to /usr/share/ppd/custom/.  Now I deleted and re-added the printer via System > Admin > Printing and now I have options such as toner saver.  The only thing that doesn't seem to work is the toner level display.  You can use the "Smartpanel" utility from Samsung's website if you really need to see the toner level.

I did not however, see any options for configuring the network settings as the OP mentioned, but it turns out this was not necessary.  I connected the printer to my wireless router via the ethernet port, and logged on to my laptop.  I then opened System > Admin > Printing and hit the Add button.  In the devices list, I expanded the "Network Printer" line and waited until the progress indicator in the bottom left disappeared (about 10 seconds).  Now there was a line that said "Samsung ML-2850".  After clicking on that, the description said "IPP network printer via DNS-SD".  I clicked forward and pretty soon I was printing.

If you need to do advanced configuration (or check toner level) over the network, look at the DHCP tables on your router for the IP address.  Mine was listed under hostname SEC0015996C05D1.  Then just point your browser to that address.  Also note, that if you have the printer connected to an Ubuntu computer via USB, Ubuntu will happily share it for you, so it is not necessary to connect the printer directly to the network.  I wanted to be able to print from my laptop even when my desktop is off, so I have it connect to both the network and to my desktop via USB.

Great printer meets great operating system!  Thank you!

---

### Post by mattexxx on 2011-10-19
[SIZE=2]I've the printer ml-2851NDR.

 I've some difficulties under ubuntu-Mint to work fine with this printer, over Lan (rj-45 connection). 
 
Problems:

[/SIZE]
[LIST]
[*][SIZE=2] -sometimes prints are slowest, when I print pdf (apparently normal documents, with text also with only 1-2 pages), apparently resolved changing the pdf viewer (problem appear with adobe reader)[/SIZE]
[*][SIZE=2] -Difficult to set toner save option that I can't find in the options driver, but only via http:\\printerip (I'm not sure that the option have effect, I'm confused because there are also other option like resolution that normally I set at print time..and via http:\\printerip seem to be fixed ) [/SIZE]
[*][SIZE=2]-Image, or graphical content are often very dark (much!). I desire tune the luminosity but I can set it only with a number via driver (default 100), but there isn't difference apparently. Alternatively there are 3 &quot;darkness&quot; grades via http:\\printerip but I'm just on &quot;Light&quot;. [/SIZE]
[*][SIZE=2]-comuniccation data speed: viewing via netrwork monitor (gnome) the  speed appear to be very slow <1Mb/s[/SIZE]
[/LIST]
[SIZE=2]
I doubt of driver installation method. Also not understand very well what are linux drivers that samsung offer .
I've also read that is possible to use windows driver extracting them via wine cabextract.



if anyone has suggestions...[/SIZE]

---

