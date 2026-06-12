---
title: "Samba &amp; Winbind issues"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by umaxtu on 2009-05-06
Alrighty heres the problem short and simple: I cant browse any work groups or domains. I am running Ubuntu 9.04 using b43-fwcutter for my wifi drivers. I've tried all the other threads but none of them work(yes i did try rebooting after making and changes) 

The only thing the other threads helped me with is diagnosing the problem. 
Running *smbtree *in the terminal gave me the following output:
> palumax@prometheus:~$ smbtree
Password: 
session request to 10.10.10.254 failed (Called name not present)
WORKGROUP
    \\MASTERXP1              
timeout connecting to 208.69.36.132:445
timeout connecting to 208.69.36.132:139
cli_start_connection: failed to connect to MASTERXP1<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
L2FDOMAIN
session request to 10.10.10.13 failed (Called name not present)
    \\L2F                    
timeout connecting to 208.69.36.132:445
timeout connecting to 208.69.36.132:139
cli_start_connection: failed to connect to L2F<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
HPNWG
    \\CRUNCHER1              
timeout connecting to 208.69.36.132:445
timeout connecting to 208.69.36.132:139
cli_start_connection: failed to connect to CRUNCHER1<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
HOMEPLANET
session request to 10.10.10.254 failed (Called name not present)
    \\LORE                   
timeout connecting to 208.69.36.132:445
timeout connecting to 208.69.36.132:139
cli_start_connection: failed to connect to LORE<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
    \\IT-1UMAGV3H7VDU        
timeout connecting to 208.69.36.132:445
timeout connecting to 208.69.36.132:139
cli_start_connection: failed to connect to IT-1UMAGV3H7VDU<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
    \\HOMEPLANETS1           
timeout connecting to 208.69.36.132:445
timeout connecting to 208.69.36.132:139
cli_start_connection: failed to connect to HOMEPLANETS1<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
    \\CP-E3400               
timeout connecting to 208.69.36.132:445
timeout connecting to 208.69.36.132:139
cli_start_connection: failed to connect to CP-E3400<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
I looks like I have two problems all computer names seem to resolve to 0.0.0.0 (my network is on 10.10.10.*) and for some reason access is denied. And if I remeber correctly Winbind is in charge of resolving names on a samba network to ip addresses so I think I have some configuration to do there but I can't find any documentation on that.

PLEASE HELP!

---

### Post by tw805 on 2009-09-27
hi, 

i have an identical issue currently. two ubuntu laptops on the wireless network that see each other fine. one windows laptop that can see the ubuntu machines, but neither ubuntu machine can see the windows box. 

exactly the same smbtree output as above; it times out, then shows that it has failed to connect to 0.0.0.0, then shows the nt_status_access_denied message. 

if anyone could provide any hints as to what we can do, that'd be great.

thanks,

tom

---

### Post by Iowan on 2009-09-27
Check [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To - there is a section on setting up */etc/nsswitch.conf* (after installing Winbind) that might be helpful.

---

### Post by tw805 on 2009-09-28
> **Iowan said:**
> Check [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To - there is a section on setting up */etc/nsswitch.conf* (after installing Winbind) that might be helpful.

Hey, thanks for the link. Went through all the steps (and some of the relevant additional ones throughout the replies) and still no luck. 

I think it's an issue with the Windows firewall settings. I've set it to allow the Ubuntu IP addresses, but when the request comes in, the firewall still blocks an IP address registered as 0.0.0.0, and I'm not sure whether to allow this as I've heard it means any unknown address? But I'll have a play around and report back here. 

Thanks again, 

Tom

EDIT: right... I solved my problem. Ran the Network Setup Wizard on the Windows box. Happens to the best of us!

---

