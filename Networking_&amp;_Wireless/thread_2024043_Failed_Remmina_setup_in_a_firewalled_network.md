---
title: "Failed Remmina setup in a firewalled network"
date: 2012-07-13
forum: Networking &amp; Wireless
---

### Post by shayno90 on 2012-07-13
On Machine A, I start Remmina (0.8.0) and created a VNC Incoming  Connection profile. port 5900 was chosen, with a username and password. No  changes under advanced or SSH. I start the profile and it says  "Listening on port 5900 for an incoming VNCI connection..."
  On Machine B, I start Remmina and create a VNC profile. I set  machineA.local:5900 as the server, enter the username and password and  leave everything else as-is. I start the profile and it says "Connecting  to 'username@machinea'..."
  However this does not connect.

  So far I've:
  
[LIST]
[*]Made sure UFW isn't enabled
[*]Confirmed I can ping and ssh from Machine A to Machine B and vice versa
[*]Tried on other ports
[*]Tried without a username and password
[*]Enable the port 5900 and  Machine A IP address on the network firewall
[/LIST]
Diagram of setup:
Machine B ubuntu (VNC profile) --->Firewall----> Machine B ubuntu (VNC Incoming connection)


I want to establish an RDP session with another Ubuntu machine but Terminal server client fails with a black session screen and X11VNC fails with too. 

Running out of alternatives, has anyone setup an RDP/VNC connection successfully between 2 linux machines and if so how?


Thanks in advance.

---

### Post by shayno90 on 2012-07-13
Solved it. Very simple issue with the client itself.

Using TSclient or KRDC, (use RDP) in the connection settings do not enter any username or password as XRDP will
prompt you for these in the remote desktop screen which appears.

XRDP must have conflicted with the attempted login before the console windows opened.

---

