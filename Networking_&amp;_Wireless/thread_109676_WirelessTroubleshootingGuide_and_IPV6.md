---
title: "WirelessTroubleshootingGuide and IPV6"
date: 2005-12-29
forum: Networking &amp; Wireless
---

### Post by geor1712 on 2005-12-29
Hi,

after downloading and printing off the wireless trouble shooting guide - [https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide) I discovered that I couldn't get on the net due to the IPV6 settings. I followed the directions for firefox - and that works fine - I can get on the internet. However, I can't chnage the system wide ipv6 settings as the file is read only. I tied to change the pirmissons, but it say' sI didn't create the file.

Any ideas on how I can edit this file?

P.S - I'm a 100% newbie to Linux, it's my first time using it :):)

Thanks,
George Buckingham,
[http://www.poweredbythewind.co.uk/](http://www.poweredbythewind.co.uk/)
[http://www.georgebcukingham.co.uk/](http://www.georgebcukingham.co.uk/)

---

### Post by Lambert on 2005-12-29
You need root permission to access that folder as it's a system folder basically. There are two ways of doing it.

1. type alt+f2 to get a run/open dialog and type this in the box

gksudo nautilus

this open the graphical file manager. Browse to the folder and you can then open the file and edit it with root permission.

2. from command line type this command

sudo gedit /etc/sysctl.conf (I believe that's the right file, can't double check at this moment, change /etc/sysctl.conf to correct file path if I'm incorrect) this opens up the text editor with root permissions
If you're using kubuntu then change gedit to kate

---

### Post by geor1712 on 2005-12-29
Hi

Thanks for the reply, the first way you recommended worked fine :):)

---

