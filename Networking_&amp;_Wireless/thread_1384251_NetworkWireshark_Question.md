---
title: "Network/Wireshark Question"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by Blueberry786 on 2010-01-18
I think there might have been an intrusion on my sister's home network and I was wondering about a couple of things.

Firstly, I know that the clients use UDP ports 53 and 68 to communicate with the DNS and DHCP server on the router. Does this mean that these ports are open all the time on the clients (both Linux and Windows clients), and would it possible for someone to exploit these and gain remote access?

Secondly, I've set up Wirehark on one of the clients to monitor any network traffic. I was wondering though, if this computer has a rootkit installed on it, would it be able to bypass Wireshark, or does Wireshark capture everything?

I'd really appreciate any help.

---

### Post by Blueberry786 on 2010-01-21
Anyone?

Another thing I was wondering about as well, would it have been possible for the intruder to install a rootkit or packet sniffer on the router, and would resetting the router definitely erase it? It's a Netgear DG834GT.

---

### Post by iponeverything on 2010-01-21
> **Blueberry786 said:**
> I think there might have been an intrusion on my sister's home network and I was wondering about a couple of things.

Firstly, I know that the clients use UDP ports 53 and 68 to communicate with the DNS and DHCP server on the router. Does this mean that these ports are open all the time on the clients (both Linux and Windows clients), and would it possible for someone to exploit these and gain remote access?

Secondly, I've set up Wirehark on one of the clients to monitor any network traffic. I was wondering though, if this computer has a rootkit installed on it, would it be able to bypass Wireshark, or does Wireshark capture everything?

I'd really appreciate any help.

I quite sceptical generally when someone suspects an intrusion. What makes you think that someone has intruded.. What is her OS? If she is running windows, it is more believable.. you seem to be a bit short on information that might be useful for someone to to help you.   

- Wired network or wireless? 

- If wireless, is it using encryption?

- Does the router still have the default factory password set?  If not, is the password susceptible to a dictionary attack? Is it accessible from the external interface.. 

Anything is possible with a rootkit. Check your md5's on things like sshd, w, who, etc..

> 
Anyone?

Another thing I was wondering about as well, would it have been possible for the intruder to install a rootkit or packet sniffer on the router, and would resetting the router definitely erase it? It's a Netgear DG834GT.

It's not likely that a rootkit or sniffer can be installed on your router..

---

### Post by Blueberry786 on 2010-01-21
> **iponeverything said:**
> I quite sceptical generally when someone suspects an intrusion. What makes you think that someone has intruded..

I'd rather not say exactly, but her neighbour has been stalking her and we've got good reason to believe he might have gotten some personal info that way.

 > **iponeverything said:**
> What is her OS? If she is running windows, it is more believable.. you seem to be a bit short on information that might be useful for someone to to help you.   

- Wired network or wireless? 

- If wireless, is it using encryption?

- Does the router still have the default factory password set?  If not, is the password susceptible to a dictionary attack? Is it accessible from the external interface.. 

It's Windows Vista on a wireless network which was using WEP encryption. I knew WEP wasn't secure so I changed it to WPA2, but I'm still worried it's to late and the network is already comprised. She was using the default router password as well which I changed for her.

> **iponeverything said:**
> Anything is possible with a rootkit. Check your md5's on things like sshd, w, who, etc..


It's not likely that a rootkit or sniffer can be installed on your router..

Thanks, I'll check that as well.

---

### Post by iponeverything on 2010-01-21
> 
I'd rather not say exactly, but her neighbour has been stalking her and we've got good reason to believe he might have gotten some personal info that way.


If you have anything concrete, contact law enforcement.

---

### Post by Blueberry786 on 2010-01-22
> **iponeverything said:**
> If you have anything concrete, contact law enforcement.

That's the problem, we can't prove it. Thanks for your help though.

---

