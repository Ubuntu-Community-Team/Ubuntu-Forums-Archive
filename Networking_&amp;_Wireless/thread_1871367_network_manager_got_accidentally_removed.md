---
title: "network manager got accidentally removed"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by den372 on 2011-10-28
Hi I am running Ubuntu 10.10. I had apache 2 installed I tried to remove it using synaptic. Some how network manager has been removed in the process. I do not have Internet access but I do have access to a machine that does and a usb drive. Does anyone know the location and packages deps of this  module. I was hoping to download and then install them one by one. I have tried several suggestions but the packages are never compatible with the OS. Any help on this matter greatly appreciated.

---

### Post by den372 on 2011-10-29
Hi I found the package [http://packages.ubuntu.com/maverick/i386/network-manager-pptp/download](http://packages.ubuntu.com/maverick/i386/network-manager-pptp/download). I downloaded this on a different computer and then installed it on the broken one. I used the standard ubuntu software center installer. I verified that network manager was installed afterwards. I think that if any outsatnding dep were needed they would have shown up during the install process, is that right. Aftre installing it I tried to launce the nm applet to test its prsence with 
nm-applet --sm-disable

this caused a core dump and shutdown. I was wondering if any one knows of a tool that would find
all the nesecarry packages and dep for a given product like network manager
any help appreciated

---

### Post by den372 on 2011-10-29
I forgot to mention I am running Ubuntu 10.10
                - the Maverick Meerkat

---

### Post by den372 on 2011-10-29
solved thanks

---

