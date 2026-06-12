---
title: "Networking on a Virtual Machine"
date: 2006-04-21
forum: Networking &amp; Wireless
---

### Post by Ruskie on 2006-04-21
Hello,
I installed Kubuntu on a VmWare Server, as I did with a Windows machine. On the linux one I have a problem when accessing the Internet from a corporate network.
For those of you that does not know how VmWare networking works, I outline it here. The option I chose is to work via NAT, that is a virtual network card is installed on the host machine, a virtual network is set up between the host computer and the guest virtual machine, and the host computer acts as gateway for the virtual machine.

  VM --- Host---Internet

Now, I tried to use this environment in two different networks: my home network and a corporate network, that could be depicted as follows:

HOME

  VM --- Host --- UsRobotics Router --- ADSL Modem --- Internet

CORPORATE

  VM --- Host --- Proxy --- Internet

The HOME network would seem more complicate, but... When I use a Windows VM everything works fine in both environments (if I set up the proxy password in the latter, of course). If I use the Linux one, instead, I can go on the internet from HOME, but nothing could make me pass the proxy in the CORPORATE network! :confused: 
What's strange is that networking DO WORKS! Infact, I can see web pages on the host machine, and even on other machines in the corporate network, but nothing that is beyond the proxy... This happens even if I set the proxy in Firefox / Mozilla and if I set it in System setup...

Could anybody help me on this, please?
Thank you

Marco

---

### Post by Ruskie on 2006-04-21
Ok, never mind... Problem solved.
Yesterday evening at home I updated the VM adding new kernel, new packages and so on, and now it works even from the corporate environments.
It seems that in the end, the original 5.10 Kubuntu release was very buggy indeed... And I know it was, as for example it didn't support well usb sticks and, now I see, proxies. :)

---

