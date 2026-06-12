---
title: "Don"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by Donald Homme on 2010-10-05
Ubuntu 10.04   Firefox remains in offline mode.  Under "file" I can remove the "offline" check but cannot access internet.   Suggestion box  says check connections.  I can use another computer and connections work.  Suggestion, check firewall.  I cannot find firewall.  Suggestions?

---

### Post by alexfish on 2010-10-05
if the browser is not working check the "Work Off line" is unchecked {notable with Mozilla Firefox}
                                        [[FONT=Verdana]**Fix it HERE**[/FONT]]("http://kb.mozillazine.org/Toolkit.networkmanager.disable")
   
 Tip for the Mozzila Firefox fix , Connect to the link then open up a separate page for the Tools/Options

**Or from the terminal** ( fool Network Manager)

Code:

[COLOR=Blue]sudo su[/COLOR]

[COLOR=Blue]printf "\niface eth111 inet dhcp\n" >> /etc/network/interfaces[/COLOR]

this will remove some of the problems

but can you post details of resolv.conf

Code:

[COLOR=Blue]cat /etc/resolv.conf[/COLOR]

---

