---
title: "automatic updates error"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by tsizzle on 2009-02-02
hello,
      I'm not really sure where this should go because I'm still pretty new in the forums and to Linux OSs, but I guess I'll post it here. I'm currently on a school network and luckily enough my school doesn't require that I install Cisco Clean Acess Agent on my computer even though its required for all windows based computers. I did however get an error message today from my computer which says 
Update Information
Apt Authentication Issue
"Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check". the problem is I'd like to know what the action I'm about to run is being as it requires me to out in my password.

---

### Post by utnubuuser on 2009-02-02
Everything in Synaptic/Update is done with administrator privileges, so password is always required.
Open a terminal and type> sudo apt-get update this will update your system info.  
Then do as the error message suggests and run the update manager manually.

System>>Administration>>Update Manager>>Check

---

### Post by tsizzle on 2009-02-02
thanks

---

