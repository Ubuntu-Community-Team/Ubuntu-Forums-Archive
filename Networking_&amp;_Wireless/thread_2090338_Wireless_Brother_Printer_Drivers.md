---
title: "Wireless Brother Printer Drivers?"
date: 2012-12-01
forum: Networking &amp; Wireless
---

### Post by Sunrise611 on 2012-12-01
I need to install the printer and scanner drivers for the Brother MFC-7860DW, a wireless printer.

However, the drivers are not  in the software repository.  I did not find them in Synaptics either when I ran a search.

I downloaded the drivers from the Brother website and can follow their instructions to install them (or try).  

Is there another way to install them that is better or easier?

---

### Post by pdc on 2012-12-03
if you are still there sunrise.........

Brother make an installer ......being linux it is open for everyone to read........ meaning you download the text of the script, and then save it into your system as a package to run.......

.......so to make things simpler......in post #4 here, 

[http://ubuntuforums.org/showthread.php?t=1999216](http://ubuntuforums.org/showthread.php?t=1999216)

Kurt has a link for the installer.........the instructions are here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

and to me they assume the installer is downloaded into your Downloads directory so if I offer some commands in red for you to copy and paste into a terminal....and hit the enter key after each paste..

> [COLOR="Red"]cd Downloads[/COLOR]

......if you want to see the list of what is in Downloads, 

> [COLOR="Red"]ls[/COLOR]

> [COLOR="Red"]gunzip linux-brprinter-installer-1.0.4-1.gz[/COLOR]

> [COLOR="Red"]sudo su[/COLOR]

> [COLOR="Red"]bash linux-brprinter-installer-1.0.4-1 Brother MFC-7860DW[/COLOR] 

[B][COLOR="Blue"]Brother say:
[/COLOR][/B]
[COLOR="SeaGreen"]The driver installation will start. Follow the installation screen directions.
When you see the message "Will you specify the DeviceURI ?",

For USB Users: Choose N(No)
[COLOR="Magenta"]**For Network Users**[/COLOR]: [COLOR="Magenta"]*Choose Y(Yes) and DeviceURI*[/COLOR].

The install process may take some time. Please wait until it is complete[/COLOR].

in post #9 here

[http://ubuntuforums.org/showthread.php?t=2039840](http://ubuntuforums.org/showthread.php?t=2039840)

the poster very nicely lays out how he configured his wireless........for the scanner bit of his MF device......

......is that any help?

---

### Post by Sunrise611 on 2012-12-03
Thank you, PDC!

I will review all of the links and try to get this to work.  

I will post my results tomorrow or some time this week.

Thanks again for the tip!

---

### Post by Sunrise611 on 2012-12-03
Thank you, PDC!

I will review all of the links and try to get this to work.  

I will post my results tomorrow or some time this week.

Thanks again for the tip!

---

