---
title: "Is There An Ink Level App For Network Printers?"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by hayhursm on 2010-07-28
[FONT=Times New Roman][SIZE=3]Is there an ink level app that works with network printers?  I am currently using Ubuntu Lucid x64 with a Canon MX860 printer that was installed using this tutorial: [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1488850[/SIZE][/FONT]]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1488850")[FONT=Times New Roman][SIZE=3] Everything seems to work fine (it prints) but I cannot get any of the ink level apps to work (Mtink or Inkblot).  After doing some research, my conclusion is those apps only work with USB connected printers…is that true?  Any help would be greatly appreciated![/SIZE][/FONT]

---

### Post by gasparov on 2010-07-28
> **hayhursm said:**
>  After doing some research, my conclusion is those apps only work with USB connected printers…is that true?  Any help would be greatly appreciated!

I can't help you because I am not familiar with Canon printers but I can tell that at the office we have a very expensive HP printer (ethernet) and I can see ink levels ( in my case as "pages" left since its a laser printer and doesn't have ink), it probably depends from the printer/driver combo.

---

### Post by hayhursm on 2010-07-29
> **gasparov said:**
> I can't help you because I am not familiar with Canon printers but I can tell that at the office we have a very expensive HP printer (ethernet) and I can see ink levels ( in my case as "pages" left since its a laser printer and doesn't have ink), it probably depends from the printer/driver combo.
 
 
[COLOR=black][FONT=Verdana]From what I read I believe that HP is more "Linux Friendly" then some of the other mfg's out their.  According to this article, they have their own Linux Toolbox for the Photosmart printer so I'm assuming they must have it for all of them.  [http://bobpeers.com/linux/hp_printing](http://bobpeers.com/linux/hp_printing)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks for the help, but I'm still looking for an ink level app that works with Canon PIXMA MX860.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I can't wait for the day when I can look on the back of a software or hardware box and it says: **"Compatibility: Any Linux Distro, PC/Windows, MAC/OS" **[/FONT][/COLOR]:D

---

### Post by hayhursm on 2011-01-03
> **hayhursm said:**
> [FONT=Times New Roman][SIZE=3]Is there an ink level app that works with network printers?  I am currently using Ubuntu Lucid x64 with a Canon MX860 printer that was installed using this tutorial: [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1488850[/SIZE][/FONT]]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1488850")[FONT=Times New Roman][SIZE=3] Everything seems to work fine (it prints) but I cannot get any of the ink level apps to work (Mtink or Inkblot).  After doing some research, my conclusion is those apps only work with USB connected printers…is that true?  Any help would be greatly appreciated![/SIZE][/FONT]


I found a solution to this, open Terminal and at command line type "sudo apt-get update", "sudo apt-get install ink", and then "ink -p bjnp" (all without quotes of course).  This detected my network printer and reported back the ink levels.  I haven't looked for a GUI to accommodate this command but I'm sure it can be done.  Hope this saves someone a lot of time!

---

