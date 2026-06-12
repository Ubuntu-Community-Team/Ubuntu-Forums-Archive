---
title: "Assign IP Address"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by mthalis on 2009-07-12
My one server issue ip's using dhcp, when client plug network cable their machine they get ip address that issue my server. My problem is if client not enable "Obtain ip automatically" how can i give ip address to client without configuring client machine. software or hardware solution.I'm waiting for your solution. 
Thank you.

---

### Post by mthalis on 2009-07-13
Any comments....

---

### Post by sanemanmad on 2009-07-13
Hi, that is not possible,  as far as I know, the DNS settings would either have to be static or dynamic. Second, How would a client machine know of your network without any broadcasts? It wouldn't. 

In short, it is not possible.

---

### Post by mthalis on 2009-07-13
One of my friend go to foreign hotel, in hat hotel this incident happen, he assigned static ip for his laptop, after go that hotel he plug network cable and go Internet without configuring any thing his machine he also said he go Internet using wired and wireless both way. Is it possible or any hidden thing happen. Please i want you're comments.
please...

---

### Post by sanemanmad on 2009-07-13
I am confused. In your first comment you are asking about IP auto-assignment without configuring client machines, not possible. However if you were suggesting you are connected to a network that does not use DHCP, then you would yes, assign a static IP and use some DNS servers (i use opendns.org 208.67.222.222). however without knowing the default gateway you may have intermittent network connectivity.

---

### Post by mthalis on 2009-07-13
Brief idea of my second comment
He surfed Internet without choosing "Obtain IP automatically". In his machine also have local(home) IP address. He did it in wireless and wired ways. He is lying or any other thing happen..

I need you're comments.

---

### Post by sanemanmad on 2009-07-13
Well I dont know about *lying*, maybe unaware of the settings.

---

### Post by mthalis on 2009-07-13
Below picture show his default setting, without changing network setting he surfed Internet

---

### Post by sanemanmad on 2009-07-13
Right, he is using Windows so in this case the user has specifically specified IP settings and then went a step forward and assigned multiple network addresses in the advanced settings. That is possible, however you should keep in mind.... that is in NO WAY automatic. Those settings were statically assigned.


So basically you could be at 
hotelA > GW=192.168.0.1
then visit hotelB > GW=10.0.0.1

You would be able to browse at either location without changing any settings by explicitly assigned the correct IP address/GW and Mask for each location.

Bear in mind however should another pc/device already leased that IP you will have a conflict.

---

### Post by mthalis on 2009-07-13
I think you don't understand that picture correctly, In that picture shown his ip address before go to hotel. After he go hotel and surfed Internet without touching his network setting. I'm asking any new hardware or software solution behind that. I want your comment, please give some idea.

---

### Post by sanemanmad on 2009-07-14
Sorry... I Know what I see and those settings were not "Automatically" set. I am an IT administrator and I have never seen any MS os change the IP settings to "Use the Following" let alone go into the Advanced section and further specify alternate IP settings for Multi-Network functionality. I think you need to do some research on your own... as aparrently you are "unaware or uneducated".

---

### Post by mthalis on 2009-07-14
How about this one...
[http://zeroconf.sourceforge.net/](http://zeroconf.sourceforge.net/)
I need your comments..

---

### Post by aesis05401 on 2009-07-15
> **mthalis said:**
> How about this one...
[http://zeroconf.sourceforge.net/](http://zeroconf.sourceforge.net/)
I need your comments..

Zeroconf is not what you are looking for.  It is a standard and the client must be running a daemon for the system to interop with their machine. 

What you asked in the first post is not possible without breaking some laws. 

As for what happened with your friend - either the network device properties that he already had in place were within the DHCP range being handed out by the server or the service provider is utilizing an exploit.  

I can guarantee you that Windows is not supposed to just adjust network interface properties without user interaction.

---

### Post by lisati on 2009-07-15
> **mthalis said:**
> I think you don't understand that picture correctly, In that picture shown his ip address before go to hotel. After he go hotel and surfed Internet without touching his network setting. I'm asking any new hardware or software solution behind that. I want your comment, please give some idea.

The picture appears to me to be something your friend had to set himself, to be used at home. I would be very surprised if his computer worked at the hotel with those settings, because there is no guarantee that the hotel's network requires the same settings. If someone else was connected to the hotel's network with exactly the same settings, there would likely be an IP address conflict, making it difficult for the hotel's network to know if it was your friend's computer or the other person's computer that it was talking to.

---

### Post by mthalis on 2009-07-16
Any body use zeroconf to assign IP addresses for clients.

---

### Post by redmk2 on 2009-07-17
If you look at the attachment carefully you will see that the wired connection is disconnected.  So the 10.x.x.x IP address is irrelevant.  If the system at the hotel is capable of handling the 192.168.101.44 address (by design or by misconfiguration) then so be it.  The term "obtain an IP address automatically" means that the client is configured to ask for an IP address via DHCP.  IT MUST REQUEST IT!  It is not broadcast, it is a specific request.  This client has never requested a DHCP address in it's present state.

There is no way around the DHCP protocol.  It is what it is.  In addition zero-conf only comes in to play when a DHCP request goes unanswered.  This is not the case with this host.

---

### Post by lisati on 2009-07-17
(from a PM)[QUOTE=mthalis]Sorry to Disturb you
Do you ever heard about zeroconf [http://zeroconf.sourceforge.net/](http://zeroconf.sourceforge.net/) using that can I assign IP to clients. Do you know how to configure it?[/QUOTE]
Sorry, haven't used it.

---

### Post by redmk2 on 2009-07-17
> Do you ever heard about zeroconf [http://zeroconf.sourceforge.net/](http://zeroconf.sourceforge.net/) using that can I assign IP to clients. Do you know how to configure it?

Hmmmmm,  Zero-Conf means just that; zero configuration.

You don't assign IP addresses the avahi-daemon does that on Ubuntu systems.

---

### Post by mthalis on 2009-07-17
redmk2 can you give more details about you're last post? If i used wireless(wifi) is it possible?

---

### Post by redmk2 on 2009-07-17
> **mthalis said:**
> redmk2 can you give more details about you're last post? If i used wireless(wifi) is it possible?

Is what possible?  If you mean zeroconf; the answer is yes.  On an Ubuntu host just insure that the avahi-daemon is running and that the host will request an IP address via DHCP.  No DHCP server is needed on the LAN.

Avahi will supply the 169.254x.x IP address.  Another way to look at it is that the avahi-daemon is the DHCP server of last resort.

---

### Post by mthalis on 2009-07-17
Can tell me how to do it(references/sites) Please it is very important..

---

### Post by redmk2 on 2009-07-17
I think it's time for you to do the good work.  It's all there on the internet.  Google avahi and zeroconf.

I will be back tomorrow.

---

