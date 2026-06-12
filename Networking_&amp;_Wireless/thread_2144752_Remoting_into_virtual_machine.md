---
title: "Remoting into virtual machine"
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by kakashi_12 on 2013-05-13
I tried following the command below (from the source below), but it tells me the directory does not exist. Anyway I can figure out where the directory should be or what the cmd should be? Anyway I can do this manually in FireFox menu without the terminal?


sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts

[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

---

### Post by kakashi_12 on 2013-05-14
Source: [http://www.justanswer.com/software/6sqdc-anyone-familiar-linux-ubuntu-using-citrix-plugin.html](http://www.justanswer.com/software/6sqdc-anyone-familiar-linux-ubuntu-using-citrix-plugin.html)

Go to this directory:
 /usr/lib/ICAClient/keystore/cacert
copy the *.crt file into the folder

Go into FireFox, Edit, Preferences, Advanced Tab, View Certificates, Import. Import a certificate from the directory above (selecting one selects them all). Ok.
Choose "Select One Automatically" Radio button. Close.

---

### Post by kakashi_12 on 2013-05-19
By the way, how do I mark this thread as Solved?

---

### Post by kakashi_12 on 2013-10-09
If still getting errors, I need to run...
sudo update-ca-certificates

then run...
sudo update-ca-certificates


Not only does this stop the SSL error, but there is no more slow loading the virtual desktop. It usually takes 5 mins of freezing up. Now it launches immediately.

ALSO for future reference incase I need more...
"Make Firefox's certificates accessible to Citrix, e.g., sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts"
per [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

and [http://support.citrix.com/proddocs/topic/receiver-linux-12-1/linux-install-uninstall.html](http://support.citrix.com/proddocs/topic/receiver-linux-12-1/linux-install-uninstall.html)

and [http://support.citrix.com/proddocs/topic/receiver-linux-blackfoot/linux-deploy-system-requirements.html#linux-deploy-system-requirements](http://support.citrix.com/proddocs/topic/receiver-linux-blackfoot/linux-deploy-system-requirements.html#linux-deploy-system-requirements)
(install motif)

---

### Post by kakashi_12 on 2013-10-10
Still intermittently receiving "SSL error 38. Connection refused."
[http://forums.citrix.com/thread.jspa?threadID=307208](http://forums.citrix.com/thread.jspa?threadID=307208)

---

