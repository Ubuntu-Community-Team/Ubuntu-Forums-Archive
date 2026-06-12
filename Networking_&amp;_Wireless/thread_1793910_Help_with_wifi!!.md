---
title: "Help with wifi!!"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by hellomoto11225 on 2011-06-30
i have tryed everything from installing loads of drivers to watching solutions on youtube basically everything installed and still no wireless connections 

well you know the network icon in the top right it doesnt say enable wireless only says enable wierd so have i miss uninstalled something please get back to me asap

---

### Post by westie457 on 2011-06-30
> **hellomoto11225 said:**
> i have tryed everything from installing loads of drivers to watching solutions on youtube basically everything installed and still no wireless connections 

well you know the network icon in the top right it doesnt say enable wireless only says enable wierd so have i miss uninstalled something please get back to me asap

Hello welcome to the Fora.

To give everybody an idea of what we are looking for could you post the output of 
```
lspci
```

---

### Post by hellomoto11225 on 2011-06-30
> **westie457 said:**
> Hello welcome to the Fora.

To give everybody an idea of what we are looking for could you post the output of 
```
lspci
```


04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

that what you need?

---

### Post by westie457 on 2011-06-30
> **hellomoto11225 said:**
> 04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

that what you need?

Yes thank you that will do nicely I am using the same Broadcom wireless chip.

Go to _[here]("http://ubuntuforums.org/showthread.php?t=1604868&page=19")_

That should get you up and running. 

If you are having problems after that go to post #240 of that thread. There you will find a tutorial that explains in more detail what you need to do.

---

### Post by hellomoto11225 on 2011-06-30
> **westie457 said:**
> Yes thank you that will do nicely I am using the same Broadcom wireless chip.

Go to _[here]("http://ubuntuforums.org/showthread.php?t=1604868&page=19")_

That should get you up and running. 

If you are having problems after that go to post #240 of that thread. There you will find a tutorial that explains in more detail what you need to do.
theres another promlem it asks for my password and my keyboard stops writeing so i cant enter the password or continue

---

### Post by westie457 on 2011-06-30
> **hellomoto11225 said:**
> theres another promlem it asks for my password and my keyboard stops writeing so i cant enter the password or continue

When typing in your password to use SUDO the cursor does not move by design. Your keystrokes are still registering. So type in your password and hit enter.

---

### Post by hellomoto11225 on 2011-06-30
> **westie457 said:**
> When typing in your password to use SUDO the cursor does not move by design. Your keystrokes are still registering. So type in your password and hit enter.

ive done that and nothing happend

---

### Post by westie457 on 2011-06-30
My mistake sorry. Are you using 'Synaptic Package Manager' or using the 'Terminal' ?

---

### Post by hellomoto11225 on 2011-06-30
> **westie457 said:**
> My mistake sorry. Are you using 'Synaptic Package Manager' or using the 'Terminal' ?

using both and following tutorial 240 like you said on that page and still nothing :(

---

### Post by hellomoto11225 on 2011-06-30
> **westie457 said:**
> My mistake sorry. Are you using 'Synaptic Package Manager' or using the 'Terminal' ?

i can now see wireless networks but it says firmware missing?

---

### Post by westie457 on 2011-06-30
> **hellomoto11225 said:**
> i can now see wireless networks but it says firmware missing?

Hi apologies for the delay in getting back to you. Had to go to work. 

You are getting there. If all has gone to plan you should now install via Synaptic two packages. They are 'b43-fwcutter' and 'firmware-b43-installer'. Reboot now and wifi should be running and waiting for you to right-click the network manager icon at the top of the screen and select a network to connect to.

---

