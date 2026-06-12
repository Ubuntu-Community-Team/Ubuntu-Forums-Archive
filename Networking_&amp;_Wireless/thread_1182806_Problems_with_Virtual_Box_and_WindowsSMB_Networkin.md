---
title: "Problems with Virtual Box and Windows/SMB Networking"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by cspowers on 2009-06-09
Howdy, 

I am running virtualbox version 2.2.4 with windows XP SP 2 has the host OS. I've installed Ubuntu 9.04 on a VM in virtual box. The networking is set up for bridged networking. 

My local LAN has two XP machines in it. Both are in the workgroup "WORKGROUP" they each have several shares and each XP maching can read and write shares on the other. The shares are currently set up to give everyone "full control". I know this is not good, but I'll lock it down later. 

Let me call the machines A and B. 

Machine A is the machine that has virtual box and the guest ubunto system running in it. 

When I run Ubuntu, I can start up web browsers and sur the internet with no problem. So beasic TCPIP networking seems to be running fine. 

When I launch Nautilus anf go to the Network icon I can drill down into Network and then WORKGROUP and I can see both machine A and machine B in the workgroup. 

I can drill into machine B and see its shares. I can open the share and copy delete create files just fine. 

But whenever I try to drill down into machine A (the host machine) I get am "unable to mount location - failed to retrieve shared list from server" error message. 

Any theories on what might be going wrong. I am a newbie to Linux and don't know much about SMB/Windows networking. I did see a tutorial online recently discussing the need to open up Ubuntu's firewall ports to SMB traffic and it gave a set of UFW commands to open the ports, which I did. But that did not help the problem described above. 

The kicker is that if I manually enter an SMB URL and I include the ID on machine A, I can conncet to a share on machine A. So for example if I enter smb://powers@A/powers I can create a connection to it in nautilus. Go figure. 

So my question is, why can't I browse the shares in nautilus like I can for machine B?

---

### Post by superprash2003 on 2009-06-09
try accessing this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

