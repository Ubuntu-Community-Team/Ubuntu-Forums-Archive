---
title: "Wireless can't find my connection after restarting?"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by Ayami on 2011-12-13
Hello~ I just installed ubuntu after some failed attempts and the first time I used them, everything was great with my connection. Then I tried to use Empathy but it wouldn't log in. Then Ubuntu software center couldn't connect. I could still use Firefox just fine though.

I restarted my computer and this time it wouldn't show my internet connection (though it does shows my neighbour's :S) Any ideas? My wireless adapter is Atheros AR928X on a Vaio PCG8272M

Thanks in advance!

---

### Post by sekacorn on 2011-12-13
have you installed the broadcom wireless driver?
If you havent then use a and ethernet cable plug it in the ethernet and see if you could access the internet

---

### Post by sekacorn on 2011-12-13
if you are able to go online go to dash home type in driver then click on the green icon that says" additional drivers"
click on broadcom STA driver then click at the bottom activate. wait for it to downlaod and install . then it will ask you to restart

---

### Post by Ayami on 2011-12-13
> **sekacorn said:**
> if you are able to go online go to dash home type in driver then click on the green icon that says" additional drivers"
click on broadcom STA driver then click at the bottom activate. wait for it to downlaod and install . then it will ask you to restart

I tried that but I don't get a broadcom STA driver choice, only some ATI graphics drivers =/
Sometimes I get internet to work but emesene still can't login

---

### Post by sekacorn on 2011-12-13
1-if you have synaptic package manger installed then go to step 2 if you  do not  go to  Ubuntu download software center. type in synaptic.  on  results click on synaptic package manager then click install
after installation open up the package manager from dash home and search broadcom

2-You will see a package named "bcmwl-kernel souce".  if it is already  installed you will see box on the left highlighted. if it is not click  on it and you will get an option click "mark for installation" or  "mark". then click appy tab at the top of the synaptic

awindow  called summary will come up " click ok" and it will install.

go back to the dash home. type "driver" and you will see a green icon saying "additional drivers" open it/ you should be able to see the  broadcom STA  wireless driver with a green bubble at the left. if the bubble is not green the click activate

---

