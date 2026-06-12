---
title: "OpenVPN or OpenVPN-AS?"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by mookie60 on 2009-12-10
I have zero server/networking experience.  I'd like to setup a vpn primarily for secure web access when I travel.  The server/client will both be Xubuntu (as the machines are a bit old).  

1)  I've tried (without success) Openvpn-AS.  "AS" seemed like it would be easier because of the gui.   Without getting into my specific problems setting it up, is this the simplest version for a basic installation?  Or should I be using the non-"AS" version?   Is there a reason to prefer one version to the other?

2)  Following Openvpn's "how to install openvpn-as software" (consisting of little more than running  ovpn-init), the installation of "AS" server on a new Karmic 9.10 seemed to go ok.   I ran the test on the gui which said the server was ready to accept connections.   After doing this installation, is it still necessary to do all the other server setup stuff like editing files, and building/generating server certificates/keys?   I've taken a look at this forum's "how to" (the Ubuntu forum how-to) for openvpn, and I'm just not sure if all the extra steps are also required for "AS".

3)  Similarly confused on the client side.  Openvpn's "how to connect to access server from a linux computer" consists of little more than running "openvpn --config client.ovpn".   Their "how to" makes no reference to all the other steps I've seen for setting up a openvpn client, like editing certain files and generating keys, etc.

4)  Am I better off starting over, forgetting about the "AS" version, and just following Ubuntu's how-to?   

5)  I've seen some comments in the forum that 9.10 might have some issues with openvpn, is it safer to stick with 9.04? 

6)  I can wipe the server OS and start over, but my laptop (client) is my main machine; are there any specific files/folders to delete from my previous client attempts?


I know I've asked quite a few questions, please forgive my confusion.

Thanks

---

### Post by madverb on 2009-12-10
I'd recommend following the Ubuntu how-to. If you run into problems there will be someone on here who could help.
I find a lot of the Ubuntu How-tos are very straight forward.

---

