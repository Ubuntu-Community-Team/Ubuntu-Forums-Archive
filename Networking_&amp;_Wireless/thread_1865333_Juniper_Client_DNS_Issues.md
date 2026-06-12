---
title: "Juniper Client DNS Issues"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by StangGT325 on 2011-10-20
Hey guys. Looking to see if anyone else is using Juniper Network Connect to tunnel into another network. It was working in 11.04 just fine, but since I loaded 11.10, once I connect I can ping my gateway but not my remote network's DNS or any computer on that network. I get a proper IP on the correct segment, but no access. I have confirmed with the Sr. Network Engineer that remote access rights have not changed. Anyone else having this issue or know of a way to resolve this? Any help is greatly appreciated and thank you to all in advance.

---

### Post by StangGT325 on 2011-10-20
Here is the Diagnostics through Juniper client.

       o  NC Installation Check 	 Passed
       o  NC Diagnostics 			
             NC Service 		 Running
             NC Driver Test 		 Passed
             NC Tunnel Test 		 Established

       o  Host Details  			
             Hostname 			 XXXXXXX
             Domainname 		 (none)
             IP Routing Enabled 	 No
             IP Loopback test 		 Passed
             Nameserver Details 	
                 XX.XX.XX.XX 		 Ping Failed

                  XX.XX.XX.XX 		 Ping Failed
             Gateway Ping Test 			 
                 XX.XX.XX.XX 		 Ping Passed

---

### Post by StangGT325 on 2011-10-20
Reinstallation and reboot did not affect the outcome. Same log as before.

---

