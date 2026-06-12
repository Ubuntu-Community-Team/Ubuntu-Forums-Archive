---
title: "disabling/deleting the wireless connection"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by ctrlmd on 2010-12-23
hi everyone,
i'm trying to delete the wireless connection and use the wired connection and when i press 
the delete button it keeps stack at the delete button with no further action 

how can i remove the wireless and use the wired connection 

thanks for the help

---

### Post by miegiel on 2010-12-23
> **ctrlmd said:**
> hi everyone,
i'm trying to delete the wireless connection and use the wired connection and when i press 
the delete button it keeps stack at the delete button with no further action 

how can i remove the wireless and use the wired connection 

thanks for the help

Maybe you need to disconnect from the wifi network before deleting it (in *edit connections > wireless* I assume). You also don't need to remove the connection to disconnect form the wifi network. If you remove the connection from the *edit connections > wireless* list you remove the configuration info for that connection (like passwords, authentication keys). If you want to prevent connecting to the wifi network you can change that option if you select *edit* in the *edit connections > wireless* window.

Alternatively, you can turnoff wifi with a key combination (Fn+F2 on my laptop). Or run
```
sudo ifconfig wlan0 down
```
in a terminal.

---

### Post by ctrlmd on 2010-12-23
if i remove the arrow from enable wireless connection it remain there
and if i try the cli command or delete the wireless connection my desktop froze 
the network icon on the panel display loading gif icon so im not even connected 

after couple of frozen desktop times i managed to delete it 

thanks for the help :)

---

