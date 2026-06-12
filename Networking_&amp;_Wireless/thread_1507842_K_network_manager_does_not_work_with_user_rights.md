---
title: "K network manager does not work with user rights"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by gs42 on 2010-06-12
Hi,
 

 On system start of kubuntu (10.04) the K network manager starts with user rights and appears as tray icon. I can open the configuration dialogue to add a new connection, but if I press the OK button – no connection is set up.
 With root rights all works fine:
 
[LIST]
[*]kill  K network 	manager user process
[*] 	gksudo  	knetworkmanager – Now I can configure connections.
[/LIST]
 After system reboot 	the K network manager runs with user rights again, and the 	connections configured with root right are not shown. 


 Is there a possibility to start the K network manager with root rights on system start? Or the better way how can I get the K network manager work with user rigths?

---

