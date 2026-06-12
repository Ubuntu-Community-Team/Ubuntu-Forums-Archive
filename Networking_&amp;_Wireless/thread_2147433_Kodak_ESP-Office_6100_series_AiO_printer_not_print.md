---
title: "Kodak ESP-Office 6100 series AiO printer not printing"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by Nanur on 2013-05-21
Hey everyone!
So today I connected to my Kodak ESP-Office 6100 series AiO printer wirelessly by using the printer settings, it is connected fine. However, when I tried printing something the notification box came up that said the printing job was complete, but there was nothing in my printer.
Any ideas?

---

### Post by paulnewall on 2013-06-03
The following might help

 In /etc/cups/cupsd.conf
    Change LogLevel warn to LogLevel debug to get much more information in /var/log/cups/error_log
    This allows users who install a binary package to get logging data without needing to recompile.
Then looking at /var/log/cups/error_log might give some clues as to what is wrong.

---

### Post by paulnewall on 2013-06-03
Other ideas:
did the printer do anything at all? like display something that suggested it was being sent data?

You could try connecting with USB to eliminate the possibility that the problem is just to do with the network connection.

---

