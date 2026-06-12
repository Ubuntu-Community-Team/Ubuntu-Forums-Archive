---
title: "Ekiga has no network-settings"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by mogliii on 2009-08-24
Hi,

please see the attached screenshot. My ekiga (3.2 from Ubuntu 9.04 as well as compiled 3.2.5) has no "Network settings". Compare to this [[COLOR="Red"]screenshot[/COLOR]]("http://gundy.org/wp-content/uploads/2006/10/ekiga-net.jpg")

There is no setting to include a stun server in my Ekiga.

I am trying to connect but everybody is always writing: use STUN. But I can't.

Can anyone tell me what went wrong?

---

### Post by mogliii on 2009-08-25
Can anyone with Ubuntu 9.04 please open his Ekiga 3.2 and tell me if he has "Network Settings"??

That would already help me a lot for the beginning.

---

### Post by jonobr on 2009-08-25
Hello


You may or may not need a stun server.

A stun server allows the udp traverse NAT, so if your using UDP across NAT then ok, you would need a stun server.

Im not sure though that the lack of a stun server would stop you registering,
Im thinking that this would only affect calling inbound/outbound, and no audio issues.

Are you able to register with your registrar?
Have you tried inbound / outbound calling?
Does the far/near end ring?

In my 3.2 build I have no network settings, just general and sip settings

Thanks 

and sorry for all the questions



ADDTIIONAL- Doing some putsing around, I notice network settings was in ver 2 Ekiga and not in Ver 3.
Also removed from V3 ekiga was a Stun support option, which surprises me,
Im going see if this is changeable in the config ( usually ~/.gconf/apps/ekiga/something or other)

---

### Post by mogliii on 2009-08-26
> **jonobr said:**
> Hello


You may or may not need a stun server.

A stun server allows the udp traverse NAT, so if your using UDP across NAT then ok, you would need a stun server.

Im not sure though that the lack of a stun server would stop you registering,
Im thinking that this would only affect calling inbound/outbound, and no audio issues.

Are you able to register with your registrar?
Have you tried inbound / outbound calling?
Does the far/near end ring?

In my 3.2 build I have no network settings, just general and sip settings

Thanks 

and sorry for all the questions

Hi,

I have currently access to two networks:
1) Private Wireless LAN, but I can not access the router config to change any settings. In that case I can connect to ekiga.net (free account), but not to my sipgate.de.

2) University Network: I cannot connect to neither.

But skype works. C'mon, I want to get away from skype, but this is so cumbersome. 

Sorry, didn't mean to complain. Thx for your help.

---

### Post by jonobr on 2009-08-26
No problems 

I understand your frustration.

I have no idea why the STUN support was pulled out of Ekiga,
it seems as if they are implying using your router (which you cant do) to port forward.

Comparing skype and Ekiga is probably not a good comparison.

Skype was built specifically to bypass the firewall issues inherently present in normal private lac deployment.,

They encrypt their traffic and dont use any standard , they use a proprietary stack and AFAIK most network admins hate it, as it pretty much acts like a virus , trying to get out no matter how much you contain it.

By what you describe, your right, you do need STUN.

It does however sound as if your university network is activaly blocking port 5060 and not allowing to access the word externally.

On the connection to  sipgate.de, what is not working, the registration?
The voice call? 

The only real way to figure out whats going on in both situtations is to become familiar with wireshark to see if you packets are getting to the remote location through your network.
Messy I know, but Im thinking without some telling you want will and wont be passed through the network, its pretty much guesswork

---

### Post by mogliii on 2009-08-26
Thank you for your extensive reply.

So to conclude: As of August 2009, there is no real alternative to skype in ease of usage from any connection (from the user's point of view).

About your other questions:
Sipgate registration does not work. It sometimes tells me "Timeout", sometimes "Unauthorized". The only point is that I was once using sipgate with x-lite and I still have money there. But now I moved and my Win has some serious connection issues.

Anyway, soon I will have my own broadband connection with full access to the router. But still, would be nice if I could make calls from University...

---

### Post by jonobr on 2009-08-26
Im thinking one thing you could try is maybe running openvpn and vpning through your college network?

If you tunnel out and your sip stuff is encapsulated you may be able to bypass some of the sip restrcitions

Cheers

---

