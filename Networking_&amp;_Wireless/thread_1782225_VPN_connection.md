---
title: "VPN connection"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by mahi.aw on 2011-06-14
Hi all,

I need some help to figure out how to connect to the remote system using VPN connection..I will briefly summarized here what i did and what problem i have..

1: Remote server administrator gave me file k/a xyz.pcf file.
2: I have extracted the information from this file and saved that file as xyz.conf file.
3: I ran the vpnc command with the file xyz.conf file..it then prompt me for username and passward to connect to remote server..I have entered the details..and then it says VPNC started in background..pid(2101).

4.Once the vpn connection established, i tried to connect to remote system using terminal server client...but here it gives me error::::auto selected map-ins error unable to connect IP..

5. I have also try to connect via ssh but it says connection time out..

6.. Finally to check wether ports are opens on remote system i just tried nmap run and it says..

Host is up (0.066s latency).
Not shown: 999 open|filtered ports
PORT    STATE    SERVICE
520/udp filtered route

i don't know what exactly i should do..can any one help me to know what should i do to make the connection to remote system...

any help will be greatly appreciated...

---

