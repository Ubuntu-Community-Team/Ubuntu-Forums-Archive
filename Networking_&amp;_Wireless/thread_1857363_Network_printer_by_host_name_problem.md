---
title: "Network printer by host name problem"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by MonocleMike2 on 2011-10-10
Ubuntu 11.04 - Relative newbie.

I have two machines called mikelap and toshiba.  My HP deskjet is connected to mikelap via USB and works OK. At home mikelap and toshiba are both on the same broadband router. mikelap printer server says publish the printer. toshiba can see the printer both by server name and IP address but only works properly if I use the connection via the ip address.  I would prefer not to use a static IP address on mikelap as it is not always at home.  When trying to use the connection via name it appears to know where it is but it hasn't loaded the drivers.  I then loaded them and then using hp-toolbox I managed to print a test page but therefter the job gets queued but it cannot connect.  I've tried on mikelap turning on allow printing over internet but that doesn't help.  I thought it might be a DNS problem but then rejected it as it is finding it to set it up but just can't use it.  I thought it might be a firewall problem but then how did I print a test page through hplip.

PS
I have now added a newly built machine, sonyvaio, to the system.  I went into admin/printers and selected cups whereupon it "discovered" the HP on mikelap however it cannot print to it.  The job goes into the local print queue but gets no further.  Is it something simple I've omitted to do?

---

### Post by MonocleMike2 on 2011-10-22
I've updated the server (mikelap running 11.10), deleted the printer on the client (toshiba) and re-discovered it.  
It now works. :P
I reckon it was the updated cups service on the server that fixed it but it could have been some tidying up of machine names in /etc/hosts, /etc/hostnames, printer properties etc.

---

