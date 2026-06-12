---
title: "smbtree fails -- connection refused"
date: 2012-09-19
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2012-09-19
When I attempt to run "smbtree" to get the share names of WinXP boxes on my LAN, I get no output at all even though I can connect to those shares via "smbclient." Running "smbtree -N -d=10" to get maximum debugging output gives this (greatly trimmed) result: > name_status_find: name found, name XUBUNTU2 ip address is 192.168.0.5
Connecting to host=XUBUNTU2
Running timed event "tevent_req_timedout" 0x21f66268
Connecting to 192.168.0.5 at port 445
Running timed event "tevent_req_timedout" 0x21f66530
Connecting to 192.168.0.5 at port 139
Error connecting to 192.168.0.5 (Connection refused)
cli_start_connection: failed to connect to XUBUNTU2<20> (192.168.0.5). Error NT_STATUS_CONNECTION_REFUSED
XUBUNTU2 is the hostname of the 12.04.1 machine that is running a WinXP box in VirtualBox. It has no firewall at all configured; "iptables -L" shows that the default policy for all three chains is ACCEPT and no rules are in place.

My question is "Where should I start looking for whatever is causing the connection to port 139 to be refused?"

Things obviously were working when I initially set up the connections for smbclient, but that was with an ancient P4 machine that housed the VM under Xubuntu 10.04.4. That machine bit the dust and had to be replaced, so I installed 12.04.1 on the new box, and then copied the virtual machines over to it. While existing connections work just fine, I cannot create any new ones -- and I particularly need to connect some virtual machines across my LAN to the printers on the new box, which is rejecting all connection attempts!

---

### Post by JKyleOKC on 2012-09-19
It took a few hours of digging in past history but I finally found a very old thread elsewhere that mentioned "smbd server not present" as a cause of this message. While "ps ax|grep smbd" showed that it was indeed working, with two instances of it in the result, the process IDs for the instances were separated by more than 100. That looked suspicious, so I did "sudo service smbd restart" and that cleaned everything up. Problem solved.

Strangely, I had restarted the entire box a couple of times, following updates, without having any effect on the problem. However the restart of just the smbd daemon did the trick, and I can now access the shares correctly.

---

