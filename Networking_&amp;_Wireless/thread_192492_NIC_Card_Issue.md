---
title: "NIC Card Issue"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by dagr8tim on 2006-06-08
I've having an issue with the nic in the computer that I installed ubuntu [SIZE="4"][FONT="Fixedsys"]**5.10**[/FONT][/SIZE] (I know it's an older version but this is a PII 400, so I didn't want to push my luck).

Anyways, this computer is dual booted with 2k and 2k can use the ethernet just fine.  In ubuntu, I can see the mac address of the card from the device manager, but not from the network settings.

Any suggestions or help would be greatly helpful.  2k lists this card as:
3Com EtherLink PCI TPO NIC (3C900-TPO)

---

### Post by mindwarp on 2006-06-09
What is the output of
```

sudo ifconfig -a

```

If it doesn't appear there, it is theoretically possible maybe hardware detection missed it and you may have to add the module to /etc/modules.

---

### Post by dagr8tim on 2006-06-10
I want to thank everyone that read this thread.  After spending about 2 days tinkering (and learning some new things), I resintalled.  During the install it didn't detect the card/DHCP server but after getting reinstalled I was able to get into the network settings and activate the nic card.

After that, it worked.  I look foward to using ubuntu and learning more in the process.

---

