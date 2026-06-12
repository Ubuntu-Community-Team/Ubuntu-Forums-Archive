---
title: "Ubuntu 9.04 not being able to browse one of my Windows XP computers and vice versa."
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by loktakwah on 2009-10-16
I have 3 computers on a network. We'll call them Windows1, Windows2, and Ubuntu.
Both Windows computers are XP Pro.

Windows 1 can browse Windows 2 and Ubuntu.
Windows 2 can only browse Windows 1.
Ubuntu can only browse Windows 1.

So basically everything works fine except that one of my Windows computers and my Ubuntu computer can't connect to each other.

Each computer can ping each other computer by both hostname and IP.

When I right click on Local Area Connection, my Windows computers each have Client for Microsoft Networks, File and Printer Sharing, QoS Packet Scheduler, NWLink NetBIOS, NWLink IPX/SPX/NetBIOS Compatible Transport Protocol, and Internet Protocol (TCP/IP) installed with the same properties/settings for each.

In Ubuntu, smb://Windows1 works fine in Nautilus. smb://Windows2 gives me the error: "Could not display "smb://Windows2". Error: Failed to retrieve share list from server Please select another viewer and try again."

In Windows2, \\Windows1 works fine. \\Ubuntu gives me the error: "Windows cannot find '\\Ubuntu'. Check the spelling and try again, or try searching for the item by clicing the Start button and then clicking Search."

All computers are using the same workgroup name.

I don't know where to go from here. Any help is much appreciated.

Update:
smbclient //Windows1ip/sharefolder connects fine.
smbclient //Windows2ip/sharefolder gives me:
> maliken@maliken-ubuntu:~$ smbclient //192.168.1.103/c
session request to 192.168.1.103 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Not listening on called name)


---

### Post by loktakwah on 2009-10-16
Update: The only thing I've found to try in the past couple hours is to run WinSockFix... It didn't fix it.

---

### Post by loktakwah on 2009-10-18
I figured I'd post my solution in case someone finds this thread.

I added another computer (Windows3) to the network and it could not communicate with Windows 2 either. So it seemed like I had one computer that could only communicate with one other computer. Everything else on the network worked fine no matter which OS it was running.

I used Zenmap to run a port scan on all of my machines and it showed me that port 445 was not open on the one machine that I was having problems with.

So the problem turned out not to be Ubuntu related.

My fix was to open Network Connections. Click the Advanced tab and scroll down to the Advanced Settings option. In Advanced Settings under the Adapters and Bindings tab, I selected my Local Area Connection. Under Bindings for Local Area Connection, the Internet Protocol (TCP/IP) box wasn't checked for File and Printer Sharing, nor for Client for Microsoft Networks.  I checked both the boxes, clicked "OK", and everything is hunky dory.

Hope this helps someone else. I don't know how it got unchecked in the first place.

---

