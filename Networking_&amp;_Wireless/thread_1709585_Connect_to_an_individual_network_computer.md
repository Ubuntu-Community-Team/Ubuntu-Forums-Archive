---
title: "Connect to an individual network computer"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by iambaz on 2011-03-18
Hi,

I have just installed Ubuntu 10.10 on my work computer. We have numerous machines on our Network, on Windows 7, I could never see the network machines listed but I could connect to individual machines simply by typing it's name in the address bar of the file explorer, such as:

//COMPUTER-NAME

When I connected my mac, I could access other computer's files using Apple + K 

smb://10.0.1.xxx

Is there any way I can connect directly to a computer using ubuntu?

Thanks

---

### Post by JRV on 2011-03-18
From the terminal type:
```
nautilus smb://HOSTNAME/SHARENAME
```

---

### Post by headvampyre@hotmail.co.uk on 2011-03-18
You could also browse the network through Nautilus.

Goto Places > Network > Windows Network > Whatever your workgroup/Domain is :)

or, just press CTRL+L then type:

smb://COMPUTERNAME

---

### Post by iambaz on 2011-03-19
Thanks for this guys

---

