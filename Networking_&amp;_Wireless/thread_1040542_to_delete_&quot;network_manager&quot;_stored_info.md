---
title: "to delete &quot;network manager&quot; stored info?"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by Salute on 2009-01-15
I'm using xubuntu gutsy and have changed isp and router info (ie essid+passkey), but I'm having trouble with nm-applet and cannot use the new wireless network -it has connected for a second, then dropped the connection -also I've rebooted straight away (hoping to save the new config and boot to a good connection) only to have nm-applet try to connect to the old account/essid... I've also tried to right-click the applet but do not have the option there to change settings -only enable/disable

How can I delete the old essid+pass+keyring please?

:guitar:

[edit] I found -via- $locate /network ,the ~/.gconf/system/networking/wireless/networks/ ,and have deleted %gconf.xml and the old account file ,this is working ,but I'm not sure I've done the best thing as I'm a little new to this ,please comment on 'better' ways if possible

---

