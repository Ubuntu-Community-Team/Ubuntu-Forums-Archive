---
title: "HP Deskjet 3050A All-In-One scanner function &quot;computer not found&quot;"
date: 2012-07-30
forum: Networking &amp; Wireless
---

### Post by Anthony T on 2012-07-30
I have a HP Deskjet 3051A all in one printer. I got it installed wirelessly using cups. Everything works fine when initiated from hplip or terminal. But when I press the scan button on the printer it says "Computer not found. Ensure the HP software has been installed on the computer." I installed HPLIP for Ubuntu 12.04 (the one i have) from HPs website. I think it is a driver or something because i even set it up using the USB connection and it still didn't work. I need all possible problems and how they can be fixed. If there is any other info needed or if you want to help me my email is: [email]Hellomotto68@yahoo.com[/email] please help

---

### Post by ajgreeny on 2012-07-30
That way of scanning does not work on my computer either, USB attached to an HP Deskjet F2180 multipurpose printer/scanner.  I had not even noticed this until today as I have always opened either xsane or simple-scan when I need to scan anything.

I can not remember if either of those are installed by default in ubuntu, but install and open one or other of those two and your scanner should be found.  Xsane is my favourite as it is much more flexible, but you may prefer the simplicity of simple-scan.

---

### Post by kurt18947 on 2012-07-30
> **Anthony T said:**
> I have a HP Deskjet 3051A all in one printer. I got it installed wirelessly using cups. Everything works fine when initiated from hplip or terminal. But when I press the scan button on the printer it says "Computer not found. Ensure the HP software has been installed on the computer." I installed HPLIP for Ubuntu 12.04 (the one i have) from HPs website. I think it is a driver or something because i even set it up using the USB connection and it still didn't work. I need all possible problems and how they can be fixed. If there is any other info needed or if you want to help me my email is: [EMAIL="Hellomotto68@yahoo.com"]Hellomotto68@yahoo.com[/EMAIL] please help

I don't have an HP AIO so don't have experience with HPLIP.  I do have a Brother and have read wireless documentation for it.  A wireless connection is a network connection.  For Brother's on-machine buttons to work, it's necessary to open port(s) on the router.  I wonder if HP has a similar requirement.  Just something to research if you're so inclined.

---

### Post by lindsay7 on 2012-07-30
You may need the latest hplip-3.12.6.  Look here for the information,

[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)

---

### Post by Anthony T on 2012-07-31
I forgot to mention it but I do have the latest version of HPLIP. I like the idea of opening ports on the router. That sounds very plausible. I think I am going to research that. Maybe go to the tech support chat that I usually do and have someone who is better with Ubuntu than I am help me. Thanks for your help. If there is anyone else who has any further input on this subject feel free to email me (hellomotto68@yahoo.com) as I will probably not get back on this thread.

---

### Post by lindsay7 on 2012-07-31
you my think you have the latest version but if it is not in the repository for the version of Ubuntu you are using you do not. The info I gave you will let you install the new version that is not in the repository yet. Loot at what you have installed by checking synaptic package manager and I bet it is not the latest version of hplip.

---

