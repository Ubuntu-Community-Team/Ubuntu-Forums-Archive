---
title: "Print from XP on 12.04 USB printer via network"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by Corniger on 2013-03-06
Hey there,

I know there's [this thread]("http://ubuntuforums.org/showthread.php?t=1339956&page=3"), but it won't work and the thread is closed, so I'm starting a new one.
I'm trying to print on a printer connected via USB to a Ubuntu 12.04 LTS printer. It can't be found.
I can't alter the smb.conf file, as it's write protected. I also don't get a printer IP via [http://localhost:631/printers/Epson-Stylus-SX410](http://localhost:631/printers/Epson-Stylus-SX410), there's just the USB connection address displayed.
I've installed Gadmin-Samba, tried various ips I found via ifconfig or Samba, but XP can't find the printer. It keeps looking for several seconds, then denies access. 
I also tried to find the cups server ip, which is supposedly stored in client.conf, but that file is a) not where it's supposed to be and b) doesn't contain any ip address.

Please, can anyone help me with this, I've searched for days and am constantly being nagged why this doesn't work :P The printer we had before worked flawlessly, but had WLan, which the one connected now doesn't...

---

### Post by Corniger on 2013-03-11
OK; I'm replying to myself in case anyone else has that problem and needs help:

In Ubuntu:
To get the ip of the cups server: terminal -> ifconfig eth0
To find the exact name of the printer: [http://localhost:631](http://localhost:631)

In XP, add new network printer (last option) and enter this address:
http://{IP_of_CUPS_Server}:631/printers/{printer_name} 

That did the job.

---

