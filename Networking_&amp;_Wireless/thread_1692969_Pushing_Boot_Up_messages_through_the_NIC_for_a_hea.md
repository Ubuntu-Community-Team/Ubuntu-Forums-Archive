---
title: "Pushing Boot Up messages through the NIC for a headless Installation."
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by bisban on 2011-02-22
Hi All,
I have a Ubuntu installation(10.10) setup without any Display.
I have a wireless router( dhcp server running here) and the box is wired to the router.

I switch ON the box and wait for the system to boot up.
Then using my laptop which is already up and connected in my home lan using the router , i check the IP Address given to the Ubuntu box.

I then use SSH to login to the box and do my stuff.

Well, the question here is , 
i want to see the boot time messages in my laptop when my Ubuntu
box is just booting up. 

I have some ideas about how we can try accomplishing it ( just an idea) but i have just posted this question to find out if there are already some clever ways to achieve it rather then inveniting the wheel.

Awaiting comments

---

### Post by bisban on 2011-02-24
After some searching , i found the above functionality can be realized using NetConsole. This lets the Boot time log messages get pushed over the NIC when the box is booting up.

---

