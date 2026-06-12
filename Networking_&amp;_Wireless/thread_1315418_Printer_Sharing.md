---
title: "Printer Sharing"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by october1917 on 2009-11-05
I've a HP LaserJet P1006 plugged to an Ubuntu machine. This is the server of a Lab Network called WORKGROUP.

There are also 4 hosts. 3 running Ubuntu and 1 running XP. 

I'm able to print from the Ubuntu Server. I can also share the printer, and perfectly print using the XP machine.

When I try to add a new network printer to the 3 Ubuntu hosts, I cannot even access it.

I go to System-->Administration-->Printing

In the new window which opens

--->New-->(wainting for printer searching)-->Network Printer-->Find Network Printer
Then I add to the host either the name (biofood-server) or the IP (192.168.0.1) and then press "Find" button, and it returns "No printer was found in this address".

Can you help me? Thank you in advance.

---

### Post by chili555 on 2009-11-05
May I assume that *biofood-server* is using a static IP address? Please make sure that under Properties of the printer attached to *biofood-server*, that 'Shared' is selected and under Server Settings, 'Publish' is selected.

Then on the hosts, you should be able to add a network printer, Internet Printing Protocol (IPP), of the general form: ipp://192.168.address.of.biofood-server:631/printers/LaserJetP1006

Port 631 is where CUPS expects printer traffic to appear.

Post back and let us know.

---

### Post by october1917 on 2009-11-05
So, from the list of Network Printer selection, I choose "Internet Printing Protocoll (ipp)"

And at the host field I put 192.168.0.1:631
At the field QueueI put /printers/HP_LaserJet_P1006

Underneath it writes by itself:

uri:   ipp://192.168.0.1/printers/HP_LaserJet_P1006

But when I press "Verify" it returns "**Inaccesible** The printer share is not accesible"

-------------------------
[I]Some more info: The printer uri at the Ubuntu server is appeared to be the following:

hp:/usb/HP_LaserJet_P1006?serial=AB0GY9R

Also, when I try to access the Ubuntu server share, from both the XP and Ubuntu hosts, it appears both the shared folders, and the shared printer.[/I]
------------------------

Is there anything wrong with ipp://192.168.0.1/printers/HP_LaserJet_P1006 ???
Is that sure that the port used is 631? How can I check it out?

---

### Post by chili555 on 2009-11-05
On every IPP network printer setup I have ever seen, including the laptop I am typing from right now, port 631 is required. The only part I question is 192.168.0.1. Is that the static IP of *biofood-server*? It looks suspiciously like the IP address of your router or switch. Perhaps *biofood-server* is also your router/switch/access point??

Here are my printer properties, as an example. This is a laptop. A USB printer is attached to a desktop upstairs.

---

### Post by Melcar on 2009-11-05
The printer/server needs a static IP to work (this is not the same as the router's IP address).  Make sure you have one.  Unfortunately I'm also having issues with sharing my printer, even though this same setup worked fine in Jaunty  :???:.

---

### Post by chili555 on 2009-11-05
Here are the server settings from the desktop with the printer attached.

---

### Post by Melcar on 2009-11-05
I'm interested if you got this to work.

---

### Post by chili555 on 2009-11-05
> I'm also having issues with sharing my printerWhat, for instance? This setup works perfectly for me in Karmic.

---

### Post by Melcar on 2009-11-05
It just can't find the printer.  It worked fine when I had Jaunty on my laptop, but now that I installed Karmic it gives me problems.  The laptop can network fine since I can share folders/files with my desktop.  I guess since my desktop still runs Jaunty some sort of incompatibility is at fault here.  Hopefully after I upgrade everything to Karmic it resolves itself.

---

### Post by drhiii on 2009-11-06
I can attest to this too.  Everything ran fine in 9.04.  After upgrading to 9.10, several things broke, including the printer share on the server.  Have gone through a series of troubleshooting things and still not able to get a client to connect to the server even tho the settings are exactly the same...



> **Melcar said:**
> It just can't find the printer.  It worked fine when I had Jaunty on my laptop, but now that I installed Karmic it gives me problems.  The laptop can network fine since I can share folders/files with my desktop.  I guess since my desktop still runs Jaunty some sort of incompatibility is at fault here.  Hopefully after I upgrade everything to Karmic it resolves itself.

---

### Post by JonathanAquino on 2009-11-07
After upgrading from Jaunty to Karmic, I found that I had to repeat the "Ubuntu Print Server" instructions in [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu) before I could print to it from WinXP.

---

