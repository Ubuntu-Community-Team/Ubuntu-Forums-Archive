---
title: "What network layer does ifconfig operate at?"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by nirvana21 on 2010-12-09
What layer does ifconfig operate at when setting a MTU. Does it set the MTU for the physical device (Network Interface Layer) or the MTU of the packet (Internet Layer)?

By executing
```
ifconfig eth0 mtu 1300
```
it leads me to believe this is causing the Network Interface Layer to be restricted because an interface must be specified. I am not sure of this though.

Can anyone confirm this for me? Furthermore, if anyone has a good source that would be great!

---

### Post by uRock on 2010-12-09
I would say the transport layer.

---

### Post by bab1 on 2010-12-10
> **nirvana21 said:**
> What layer does ifconfig operate at when setting a MTU. Does it set the MTU for the physical device (Network Interface Layer) or the MTU of the packet (Internet Layer)?
 
Layer 2 (Ethernet) where [FONT="Courier New"]**ifconfig **[/FONT]sets the MTU size.  The MTU you are referring to is the *frame *size and for Ethernet (see [**_here_**]("http://www.networkingreviews.com/2008/02/29/the-base-of-ip-networks-osi-model/")) it is normally 1500.  See [**_here _**]("http://compnetworking.about.com/od/networkprotocols/g/mtu-maximum.htm")for a basic discussion. 
> 
By executing
```
ifconfig eth0 mtu 1300
```
it leads me to believe this is causing the Network Interface Layer to be restricted because an interface must be specified. I am not sure of this though.

That is correct.> 

Can anyone confirm this for me? Furthermore, if anyone has a good source that would be great!

Here is a pretty good [**_Google search_**]("http://www.google.com/search?q=tcp+layers&btnG=Go!#sclient=psy&hl=en&q=ethernet+mtu+definition&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=df5e37d3d2fae155").

---

### Post by nirvana21 on 2010-12-10
> **bab1 said:**
> Layer 2 (Ethernet) where [FONT="Courier New"]**ifconfig **[/FONT]sets the MTU size.  The MTU you are referring to is the *frame *size and for Ethernet (see [**_here_**]("http://www.networkingreviews.com/2008/02/29/the-base-of-ip-networks-osi-model/")) it is normally 1500.  See [**_here _**]("http://compnetworking.about.com/od/networkprotocols/g/mtu-maximum.htm")for a basic discussion. 
That is correct.

Here is a pretty good [**_Google search_**]("http://www.google.com/search?q=tcp+layers&btnG=Go!#sclient=psy&hl=en&q=ethernet+mtu+definition&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=df5e37d3d2fae155").

Thanks for the confirmation.

---

