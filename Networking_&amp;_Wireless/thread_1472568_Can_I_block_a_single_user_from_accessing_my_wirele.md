---
title: "Can I block a single user from accessing my wireless?"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by rob22941 on 2010-05-04
Ok, I'm in college and my roommate hasn't paid me his share of the internet bill or electric for that matter for the past 3 months and each time I ask for the cash or if he has it he says no. So I'd like to screw with him just in time for finals. You mess with me I mess with you.

Is there a way to block his ip address from accessing my router for internet access? I set up the internet and the works. I used windows 7 to originally set up the internet but I also have 2 other computers with ubuntu built on. I don't care if I use ubuntu or windows to block him. Do I need to get on his pc to get his ip or can I view who is logged on through my pc? Thanks much amigos.

---

### Post by Iowan on 2010-05-04
If it's your router, and it is also the DHCP server, you can assign a static lease based on MAC Address. If that address is outside the subnet, it *might* not work well (eg 127.0.0.1). A static address will quickly bypass this "security". The router itself might also have (MAC address) filtering options.

---

### Post by Littleweseth on 2010-05-04
I'm just going to leave this here:

[http://www.ex-parrot.com/pete/upside-down-ternet.html](http://www.ex-parrot.com/pete/upside-down-ternet.html)

Have fun.

- Lewis.

---

### Post by rob22941 on 2010-05-04
> **Littleweseth said:**
> I'm just going to leave this here:

[http://www.ex-parrot.com/pete/upside-down-ternet.html](http://www.ex-parrot.com/pete/upside-down-ternet.html)

Have fun.

- Lewis.

If it's something clever he will know I'm screwing with him. And he'll accuse me immediately. I do however like the idea. I think it will just be most appropriate to simply cut him off of my wireless.

---

### Post by rob22941 on 2010-05-04
> **Iowan said:**
> If it's your router, and it is also the DHCP server, you can assign a static lease based on MAC Address. If that address is outside the subnet, it *might* not work well (eg 127.0.0.1). A static address will quickly bypass this "security". The router itself might also have (MAC address) filtering options.

I'm not quite sure what you mean. However I would just change the password but I have a total of 3 roommates and I don't want any of them to know my intentions.

---

### Post by Iowan on 2010-05-04
Starting to sound a bit more sinister :-k
You should be able to block access to the router from the router itself. The manual should be able to tell you how to set up a static lease (reserved address) or filter by MAC address. If you'd care to mention router make/model, that info may be on Web, as well... but if you're only cutting off a deadbeat roomie, why the clandestine activity? If it's for vengeance alone, this is the wrong place for help...

---

### Post by rob22941 on 2010-05-04
> **Iowan said:**
> Starting to sound a bit more sinister :-k
You should be able to block access to the router from the router itself. The manual should be able to tell you how to set up a static lease (reserved address) or filter by MAC address. If you'd care to mention router make/model, that info may be on Web, as well... but if you're only cutting off a deadbeat roomie, why the clandestine activity? If it's for vengeance alone, this is the wrong place for help...

Well I think it would be useful knowledge. I also would like my roommate to not rely on ends of my wallet. I'm going to take a closer look at ex-parrot.

---

### Post by Keith1212 on 2010-05-04
I use mac address filtering. Just add the mac addresses of all your stuff and then either dont add his or add his and put a check mark next to it so it doesn't allow him. This is how it works on my belkin anyways.

---

### Post by rob22941 on 2010-05-04
Doing it now. Thanks all, I also found what I thought to be a useful link:

[http://www.technipages.com/block-connections-to-your-linksys-router-by-mac-address.html](http://www.technipages.com/block-connections-to-your-linksys-router-by-mac-address.html)

---

