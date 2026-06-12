---
title: "adsl and fwbuilder"
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by klaarnou on 2011-09-25
Hello,
I have the following setup:
-	DSL modem in bridge mode dialled using pppd
-	FWBuilder firewall script

I would like to do the following:
-	Run the fwbuilder script during startup (currently I have   to run it manually since it does not work to run if from rc.local)
-	Run the fwbuilder script each time my IP address changes since I have up address forwarding in the script that stops working if the IP changes
-	Monitor the DSL connection since it is giving me some trouble. (Log the PPPd log files to a separate log file?)

Thank you.
Bernard.

---

