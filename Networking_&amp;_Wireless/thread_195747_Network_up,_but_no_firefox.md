---
title: "Network up, but no firefox"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by Bigslim76 on 2006-06-13
I installed Dasher clean with the server disk so the computer recognizes the internet.  It recognizes my network card in the GUI, but firefox cannot find the internet.
Any help?

---

### Post by localzuk on 2006-06-13
Can you ping any other computers on the network or the router? (Open a terminal and type 'ping' followed by the IP address of the other machine).

Also, can you ping external websites (same as above but try ping google.com)?

---

### Post by georgeous on 2006-06-13
I'm having a similar problem, network card is recognised by the OS, and picks up configuration (IP address, gateway, netmask, etc.) from the dhcp server on the router. I am able to ping the router, other computers on the network, external sites such as google. I can also use the 'host www.examplesite.com' command in terminal to resolve an IP address...

Despite this firefox won't load anything, and the package manager won't download an updated list. In both cases the download/pageload starts but never completes (progress bar doesn't move).

Help! I've followed the steps for disabling ipv6, etc. and this has appeared to have no effect. I had thought of a firewall, but dapper doesn't seem to have one installed in a default package, and the firewall should allow web access on port 80.

All i can think is either a configuration problem somewhere on my pc, or that linux doesn't talk to my router quite right... I have a D-link wireless adsl router, and am using a direct cable connection. (wireless is next step...)

Can anyone shed any light on this?

---

### Post by Bigslim76 on 2006-06-13
Tried to ping my other computer through my router.  Didnt work even when I turned off the firewall for windows.  Tried to ping google and it said unknown host.

---

### Post by ales on 2006-06-13
[QUOTE=georgeous]I'm having a similar problem, network card is recognised by the OS, and picks up configuration (IP address, gateway, netmask, etc.) from the dhcp server on the router. I am able to ping the router, other computers on the network, external sites such as google. I can also use the 'host www.examplesite.com' command in terminal to resolve an IP address...

Despite this firefox won't load anything, and the package manager won't download an updated list. In both cases the download/pageload starts but never completes (progress bar doesn't move).

Help! I've followed the steps for disabling ipv6, etc. and this has appeared to have no effect. I had thought of a firewall, but dapper doesn't seem to have one installed in a default package, and the firewall should allow web access on port 80.

All i can think is either a configuration problem somewhere on my pc, or that linux doesn't talk to my router quite right... I have a D-link wireless adsl router, and am using a direct cable connection. (wireless is next step...)

Can anyone shed any light on this?[/QUOTE]

I have Alcatel Speedtouch 530i and same problem. I have two ethernets onboard. I disbaled one but my problem continues. I have always to disable the card in Networking in Ubuntu and then enable, after this firefox works. It seems that starting Ubuntu doesn't configure the card correctly....

---

### Post by hkosturi on 2006-06-14
[QUOTE=georgeous]I'm having a similar problem, network card is recognised by the OS, and picks up configuration (IP address, gateway, netmask, etc.) from the dhcp server on the router. I am able to ping the router, other computers on the network, external sites such as google. I can also use the 'host www.examplesite.com' command in terminal to resolve an IP address...

Despite this firefox won't load anything, and the package manager won't download an updated list. In both cases the download/pageload starts but never completes (progress bar doesn't move).

Help! I've followed the steps for disabling ipv6, etc. and this has appeared to have no effect. I had thought of a firewall, but dapper doesn't seem to have one installed in a default package, and the firewall should allow web access on port 80.

All i can think is either a configuration problem somewhere on my pc, or that linux doesn't talk to my router quite right... I have a D-link wireless adsl router, and am using a direct cable connection. (wireless is next step...)

Can anyone shed any light on this?[/QUOTE]

I had the same problem but when i updated the firmware of my linksys router everything whent ok. Maybe this will help.

---

### Post by deepnum on 2006-06-16
I had a similar situation where I could connect to the linksys router that i have at home (typed 192.168.1.1 into the address bar of firefox) but couldn't seem to connect to the internet. I was pulling out my hair for the longest time on this. I could even ping google.com in the terminal but nothing showed up in firefox.

I found this on the forum somwhere so i don't take credit for it. It worked for me but might not for you.

1) in the address bar of firefox type "about:config"
2) type "ipv" into the filter at the top of the page
3) double click on the line starting with network.dns.disableIPv6 so that the value turns to true

that's all i did and the internet started to work for me :)

---

