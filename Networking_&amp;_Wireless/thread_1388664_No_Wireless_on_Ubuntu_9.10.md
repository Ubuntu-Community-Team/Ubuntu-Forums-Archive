---
title: "No Wireless on Ubuntu 9.10"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by dancewithpratik on 2010-01-23
Hi Folks ,
I have installed Ubuntu 9.10(dual boot with Windows 7) on my HP Pavillion dv51106 ax model.I am unable to start Wi-Fi from Ubuntu as the touch-pad key dosent get enabled. Hence i am unable to connect Wirelessly.

Please Help...
Waiting for the reply Folks ....

---

### Post by drpaul on 2010-01-23
Must say you're not the only one. I just install 9.10 over 8.04, and networkmanager has disappeared, manual wifi connection doesn't work, lots of applets seem to have disappeared.

My suggestion is to keep looking in this subgroup for applicable threads and hope that help magically appears.

Paul

---

### Post by bkratz on 2010-01-23
> **dancewithpratik said:**
> Hi Folks ,
I have installed Ubuntu 9.10(dual boot with Windows 7) on my HP Pavillion dv51106 ax model.I am unable to start Wi-Fi from Ubuntu as the touch-pad key dosent get enabled. Hence i am unable to connect Wirelessly.

Please Help...
Waiting for the reply Folks ....

First thing we need to find out is what your wireless card is.

Go to the terminal  (Applications>>Accessories>>Terminal) and type in
lspci  (that is LSPCI in lowercase). Copy/paste the output back here for additional assistance. 
You might also want to post the output of
sudo lshw -C network (that is LSHW in lowercase, C in uppercase). Note that this will require you to input your password, which will not be echoed, not even ***, just press enter when input

---

### Post by drpaul on 2010-01-23
My experience may not work for you, but ....

I installed wicd and dropped NetworkManager and was then able to connect to my router with wireless. I have an HP with Intel chips.

HTH

Paul

---

