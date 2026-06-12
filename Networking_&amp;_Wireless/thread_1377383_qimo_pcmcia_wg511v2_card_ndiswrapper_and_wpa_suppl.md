---
title: "qimo pcmcia wg511v2 card ndiswrapper and wpa_supplicant"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by dwjoy on 2010-01-10
Hi all,

I have two questions.


My system:
laptop Compaq Armada E500
PCMCIA wireless card Netgear WG511v2
Qimo 1.0 based on Ubuntu version 8.10 and kernel version 2.6.27-9

I have installed ndiswrapper and it works fine without encrypton. Problem is when I want to add encryption.

With instructions from the net I tried to configure wpa_supplicant. At some point I'm supposed to create a config file etc/wpa_supplicant.config. I don't have write access to etc/ location. Permission denied even when using su. How can I obtain permission to create that file? Is there a workaround?


Second problem:

ndiswrapper-utils-1.9 dependencies problem.

Package broken
Installed version: 1.52.1ubuntu1


depends: libc6 (>=2.4)
depends: ndiswrapper-common
suggests: ndiswrapper-source


instaled libc6 version:
libc6                      2.8~20080505-0ubuntu9
libc6-dev               2.8~20080505-0ubuntu9
libtext-iconv-peri   1.7-1build1
libc6-i686              2.8~20080505-0ubuntu9


So, as you can see, I have updated libc6, libc6-dev and libc6-i686 packages.
Dependencies are still there.

I would relly appriciate help here. Wireless works, but auto update of system fails because of it. 

Thanks in advance.

---

### Post by mbabauer on 2010-01-10
Did you try
```
sudo vi /etc/wpa_supplicant.config
```

This will open the file as root.  Or, if you are lazy like I am, I just do
```
sudo -s
```

And become root out-right in a shell.

---

### Post by dwjoy on 2010-01-10
Thank you. I created file /etc/wpa_supplicant.config

I will try to configure wep encryption now. 

Problem with dependencies is still present though.

---

