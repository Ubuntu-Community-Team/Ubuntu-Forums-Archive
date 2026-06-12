---
title: "Network goes in and out? - Realtek RTL8187B"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by Honest AMish on 2011-01-31
Alright, I'm using a Realtek  RTL8187B wireless adapter (WG111v3 from NetGear) on Maverick Meercat. Installed the Windows .inf driver using NDIS-wrapper, and it recognizes the device fine. Now I have problem with connections...

The network drops in and out, and it's trying to broadcast a second network (from another computer trying to connect to a wireless network, it appears as NameOfMyNetwork 2). Whether or not it's coming from my computer or router, I do not know.

Anyone else having this problem?

---

### Post by Honest AMish on 2011-02-02
bump

---

### Post by Honest AMish on 2011-02-03
Bumping once again, would sure be nice to get some help on this.

---

### Post by Honest AMish on 2011-02-06
Another bump

---

### Post by arjuntank on 2011-02-06
wg111v3 should work out of the box, atleast thats what the wiki says. network manager sometimes makes second network if you already have one manually defined adhoc network. are you trying to connect to a wireless router or another adhoc?

---

### Post by Honest AMish on 2011-02-06
> **arjuntank said:**
> wg111v3 should work out of the box, atleast thats what the wiki says. network manager sometimes makes second network if you already have one manually defined adhoc network. are you trying to connect to a wireless router or another adhoc?

A wireless router, but I have the settings set as using it as a Gateway.

Is this fixable without completely undermining my network?

---

### Post by arjuntank on 2011-02-06
remove any networks other than your wireless router on your network manager list and connect again. check to see if the same problem exist with other computers on the network.

---

### Post by Honest AMish on 2011-02-10
> **arjuntank said:**
> remove any networks other than your wireless router on your network manager list and connect again. check to see if the same problem exist with other computers on the network.

In Ubuntu? The only networks that show up are two "Family Network" selections, and when I type in the WEP key to either one, it just sits there and connects for awhile, then loses the connection all together (I have the right WEP key, I promise).

On other computers, it shows two networks, "Family Network" and "Family Network 2". When other computers are on the "Family Network" and I start up Ubuntu, they are disconnected from the network and all that appears in the network manager list is the two networks, "Family Network" and "Family Network 2". They cannot connect successfully to either. Could it be that I have it named "Network" that is causing problems?

---

