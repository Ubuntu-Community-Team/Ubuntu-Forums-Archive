---
title: "Network LAN ip adress issues"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by Gosy on 2012-02-05
Hey everyone!

First off, i'm really new to the ubuntu OS and i'm running the server version of it, GUI-less. 
Why am i doing that? Well i thought that i'd learn ubuntu from the scratch which is the terminal! ( Atleast i think so ).

Well now over to my problem..

I'm having some issues with my dchp. I got openSSH installed on the server and when i try to reach it PuTTy with the LAN ip adress ( which is 192.168.1.10 ) it works. But when i close it and wait for 5-10 mins the LAN ip adress on my ubuntuserver changes automaticly and i have no clue to solve this!

Could any kind soul out there willing to help me out?

Forgott to add that i'm running the server on a VMbox ( Virtual Machine ) which is hosted from a Windows XP OS.

Thanks in advance

---

### Post by helgman on 2012-02-06
> **Gosy said:**
> I'm having some issues with my dchp. I got openSSH installed on the server and when i try to reach it PuTTy with the LAN ip adress ( which is 192.168.1.10 ) it works. But when i close it and wait for 5-10 mins the LAN ip adress on my ubuntuserver changes automaticly and i have no clue to solve this!

Here are two possible solutions:
[LIST=1]
[*]Set the server to use an static IP address
[*]Configure your DHCP server to always hand out the same IP address to the server
[/LIST]

You find information for option one [here]("https://help.ubuntu.com/11.10/serverguide/C/network-configuration.html"). Just head down to the "[Static IP Address Assignment]("https://help.ubuntu.com/11.10/serverguide/C/network-configuration.html#static-ip-addressing")" section.

Option two depends on the DHCP server software, but you'll need to know the MAC address of your Ubuntu server. Use [FONT="Courier New"]ifconfig [/FONT]and look for HWaddr. In the example in the "network configuration guide" the MAC address is [FONT="Courier New"]00:15:c5:4a:16:5a[/FONT] [[link to section]("https://help.ubuntu.com/11.10/serverguide/C/network-configuration.html#ip-addressing")].

Let us know how you're doing.

Regards,
Helgman

---

### Post by Gosy on 2012-02-06
Thanks alot for your help, i manage to set my ip to static via your helpful links! Thanks !

---

