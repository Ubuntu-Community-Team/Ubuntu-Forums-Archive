---
title: "Wireless Single Sign-On"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by tolkeinknoxy on 2009-01-30
Hello peoples!

I've got a problem, which I have been for quite some time trying to come up with a good working solution. Basically I have a set of Linux net-books, which can be issued out to students. Currently the netbook has to auto-login and provide an icon on the desktop, which users supply their credentials and if the machine is on the wireless/wired network it, mounts their samba shares. Although this works to some degree its a very inelegant solution.
 
What I would like is the netbook at GDM to request username and password, to first use these credentials to try authticating to wireless via radius. Probably a status message telling the user it’s trying to connect to wireless and then connects or fails would be useful after a certain timeout. And then use these same credentials to validate itself against the LDAP server, which we use for the fat clients authtication. This would be the ideal method, however I don’t mind if the machine uses machine credentials and logs onto the wireless on boot securely. However this would require the user to reboot if they were not near a hotspot but now are.
  
 The technology and process behind this sounds similar to Wireless Single Sign-On in windows Vista but obviously I am not going to use this. If this isn't the best way to go around this I'm more than open to suggestions.

---

