---
title: "Cant share network connection"
date: 2010-07-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Kangarooo on 2010-07-23
in comp1 ive connected to wifi
xubuntu 10.10 on both
from comp 1 to comp 2 wire to share network doesnt work doesnt show any wired network available. shows wired networks disconnected. but thats not true. ive plugged 1 wire in both and in comp 1 settings is made config share to other comps. in comp 2 is made automatic.
eacg has only 1 lan port

---

### Post by ibuclaw on 2010-07-23
Moved to Maverick forums.

---

### Post by hugmenot on 2010-07-23
What does this have to do with maverick?

Are you using a [cross-over CAT5 cable]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable")? Otherwise it won’t work if you connect ethernet port to ethernet port directly.


After you got a cross-over cable, on Comp 1 did you setup the connection sharing with NetworkManager? It should be set to »Shared to other computers« (screenshot). Otherwise there will be no DHCP between the two computers and no routing established.

---

### Post by Kangarooo on 2010-07-23
> **hugmenot said:**
> What does this have to do with maverick?

Are you using a [cross-over CAT5 cable]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable")? Otherwise it won&#8217;t work if you connect ethernet port to ethernet port directly.


After you got a cross-over cable, on Comp 1 did you setup the connection sharing with NetworkManager? It should be set to »Shared to other computers« (screenshot). Otherwise there will be no DHCP between the two computers and no routing established.

Yes ive done that. its the usual Lan cable. by wiki pics its the same.
If i do the same with router then all is fone. but now i dont want to use router. i need it in another place. and comp to compt doesnt work.
yes shared to antoher comp is done.

also there wired showing disconected.. thats not true. when using router in the middle of 2 comps with 2 wires 1 in 1 out then all is fine..

---

### Post by cariboo on 2010-07-23
When connecting directly between to computers, you need a crossover cable. 

The crossover cable i have here looks exactly the same as any other cable, the only way I can tell, aside from using my cable checker, is that the place I buy most of my cables from sells only yellow colored crossover cables.

---

### Post by seeker5528 on 2010-07-23
> **cariboo907 said:**
> The crossover cable i have here looks exactly the same as any other cable, the only way I can tell, aside from using my cable checker, is that the place I buy most of my cables from sells only yellow colored crossover cables.

Every ethernet cable I ever had, the part that plugs in is clear plastic, so you can see what order the wires are in. So if you hold the two ends next to each other, the straight through cable will be the same on both ends, the crossover cable will have one pair, uhm, crossed over.  ;)

Later, Seeker

---

### Post by Kangarooo on 2010-07-23
ahaa ok thx
now i understand. LAN cable only different.. not usual..
but cant programm be made to send from card differently?

---

### Post by seeker5528 on 2010-07-24
> **Kangarooo said:**
> ahaa ok thx
now i understand. LAN cable only different.. not usual..
but cant programm be made to send from card differently?

As far as I know for all cards data out is always data out, data in is always data in, no option to flip the data pair.

On network hubs, switches, routers, etc... there is often a single port where there is a button you can push to cross the data lines, a dedicated uplink port where the data lines are always crossed, or a single internal port that is physically wired to two external ports where you can use the standard one or the crossed one but not both. The uplink port would be used to hook any two of these together, from the uplink port on one to a standard port on the other, like the computer to computer situation, if there was no uplink port, or the uplink port is already used, a crossover cable would be needed to hook them together.

In my locale, network cables are pretty cheap and a little 4 or 5 port network switch doesn't cost that much either.

Later, Seeker

---

### Post by hugmenot on 2010-07-24
[Actually…]("http://en.wikipedia.org/wiki/Auto-MDIX")

---

### Post by drdos2006 on 2010-07-24
You will need a crossover cable to connect two machines via ethernet ports. One computer will receive when one is transmitting and the other machine will transmit when the the other is receiving.
Routers and switches automatically set the connection for you.
regards

---

### Post by seeker5528 on 2010-07-26
> **hugmenot said:**
> [Actually…]("http://en.wikipedia.org/wiki/Auto-MDIX")

So it's an optional thing you *might* have *if* you have Gigabit ethernet.

The description of some switches I have seen makes it sound like they might handle the crossover, but in the real world it doesn't seem very reliable.

Maybe if it's more standardised with Gigabit ethernet it could work better, but if you can't hook two ports together that have Auto-MDIX enabled, that doesn't seem like a recipe for reliability. :?

Later, Seeker

---

