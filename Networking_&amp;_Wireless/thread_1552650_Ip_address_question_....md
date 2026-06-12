---
title: "Ip address question ...?"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by masamunedark on 2010-08-13
Hi, I want to know what my IP is. The problem is that I'm connected  through wireless with more than one PC and all of them give the same ip  address when I use services like whatsmyip.org. So I thought maybe that  ip is for my wireless router (or whatever the name is). so for example  if I want to ping one of my PC's from the other one what IP should i use  ???
I hope the information is enough for you guys to be able to give me hints regarding my problem.
Sorry for my bad English (not a native speaker), and by the way I don't  have (as you can see XD) much information about networks and such, so  please give as much information as possible, as I am only asking this  question for knowledge not cause i have a real problem, and thanks.

(And by the way was this the right way for posting this? cause i am not used for posting stuff on forums)

---

### Post by squaregoldfish on 2010-08-14
If you type ifconfig -a in a terminal, you'll get all the details of the network connections on your machine. Wired connections are labelled eth0,eth1 etc, and wireless connections wlan0.

You can ignore the interface labelled lo - this is a special 'loopback' interface to your machine used by various programs.

Steve.

---

### Post by Iowan on 2010-08-14
> **masamunedark said:**
> ... all of them give the same ip  address when I use services like whatsmyip.org. 
That would be the "external" address (of the router). The machine's IP address can be found several ways - one as **squaregoldfish** mentioned. A terminal is available Applications>Accessories>Terminal. Another way (in Lucid) is System>Administration>Network Tools. Select the network device (eth0, etc) and look at the IP information.

---

### Post by masamunedark on 2010-08-14
[LIST]
[*]Ok, thanks for the answers guys. But now there's something i still don't understand, is my local IP address used only inside my lan (as the name suggests), or is it used by any machine trying to send information to  me?? And if it's not only used locally, then does that mean there's no other machine using the internet which have that same IP??
[/LIST]

---

### Post by capscrew on 2010-08-14
> **masamunedark said:**
> Ok, thanks for the answers guys. But now there's something i still don't understand, is my local IP address used only inside my lan (as the name suggests),
Yes, the local IP address is unique to that computer  on you local network.> 

 or is it used by any machine trying to send information to  me?? 

If the machine sending your computer is on your local network it sends you computer the information based on (a) your computers IP address and (b) the MAC (hardware) address of your computer.

If the sending computer is on another network (internet) then the data is sent to the external IP address of the MODEM/Router.  The ultimate destination of you computer is translated by the router using NAT (Network Address Translation).
> 

And if it's not only used locally, then does that mean there's no other machine using the internet which have that same IP??


Private IP addresses can be used in any LAN, so yes, they are used over and over by local LAN's.  The IP addresses must be unique in the LAN (no duplicates).

Public addresses must be unique throughout the Internet.

---

### Post by masamunedark on 2010-08-14
Ok, thank you very much, now i get it. :P

---

