---
title: "Ekiga - works with druid tests, but won't connect to another ekiga user"
date: 2009-01-30
forum: Multimedia Software
---

### Post by bumanie on 2009-01-30
I have gone to considerable difficulty getting ekiga to a point where it connects to the ekiga '500' address and I can successfully do the audio test and get feedback during the druid setup phase. My account is recognized as being registered, but it won't connect to another ekiga user. It is stuck in 'standby' mode and does nothing, other than immediately disconnect. Previously I could connect to another ekiga user via an IM connection, but had no audio, due to having a 'symmetric' router issue. Now all the settings seem to be right, ie the 'sip:500@ekiga.net' connects, I have a registered account and I have a static IP address going to a STUN server - I get no IM, and no audio audio to another ekiga account. Anyone know what I am missing? There is precious little on google about this issue. Thanks to anyone who may have any ideas. I would prefer not to use skype. I am committed to the open source ethos and don't use proprietary software if an open source equivalent exists.

---

### Post by FSHero on 2009-06-01
Hi bumanie,

I have a similar issue with Ekiga. I'm at my uncle's place, and I'm using the same laptop that I do at my house.

At my house, Ekiga (2.0.12, from Kubuntu 8.04) detects the NAT as port-restricted NAT, and automatically sets up connection to STUN server. I am able to dial the echo test, hear the instructions then talk into the mic as the voice is returned. I have a Netgear DG834GT router at my house.

However, at my uncle's house, who has a Thomson TG585 v7 router, the NAT type detected is symmetric NAT. In fact, even after forwarding ports 3478-3479 and 5000-5100 to my laptop I get this message. I decided to press on anyway.

If I try to dial sip:500@ekiga.net, I do not hear any echo test instructions. It does say "Connected with 500@ekiga..." (cut off due to narrow window!), and "Out: PCMA/H261", "In: PCMA/H261".

If anyone could help, even just pointing me in the right direction, I would be extremely grateful. Ekiga does look like a promising solution, but unfortunately very difficult to set up.

Btw bumanie, you said that you *used to* have a symmetric NAT problem. How do you solve it?

---

### Post by FSHero on 2009-06-01
Just a quick thought: could my ISP be blocking the aforementioned ports? I think this because of the following:

I am trying to use [www.canyouseeme.org](www.canyouseeme.org) to check for open ports. For reference, here are the ports that I have forwarded in my router:
1720
3478-3479
5000-5100

The results I get when I try the following ports are:

1720: 
Success: I can see your service on 79.65.101.137 on port (1720)
Your ISP is not blocking port 1720

3478:
Error: I could not see your service on 79.65.101.137 on port (3478)
Reason: Connection refused

3479:
Error: I could not see your service on 79.65.101.137 on port (3479)
Reason: Connection refused

5000:
Error: I could not see your service on 79.65.101.137 on port (5000)
Reason: Connection refused

5060:
Error: I could not see your service on 79.65.101.137 on port (5060)
Reason: Connection refused

5063:
Error: I could not see your service on 79.65.101.137 on port (5063)
Reason: Connection refused

Thus, I'm not sure why the Netmeeting port 1720 is accessible externally, while the others are not, despite them all being in my "port forward" list.

---

### Post by FSHero on 2009-06-01
One last thing: In my router control panel, I have to "assign" the port-forwarding set of rules to a computer -- which I did to my laptop. Then, I got the results described in my previous post.

However, If I do not assign the rules to my computer, I get the following messages for all the above ports:

Error: I could not see your service on 79.65.101.137 on port (5060)
Reason: Connection timed out

So my question is: when my computer is assigned the port-forwarding rules, why is 1720 not being blocked but the others are?

---

### Post by FSHero on 2009-06-01
kk, I got something working just now!

I entered the following port ranges in my router to be forwarded to my laptop:

3478-3479
5000-5100
30000-30010 (I used this because when I ran "ekiga -d 5" from the console (i.e. debug mode), I saw this mentioned somewhere.)

Then, in Ekiga 2.0.12, I went to Edit --> Preferences, then on the LHS, I selected the Network Settings tab. I set NAT traversal method to None.

Sometimes a little guesswork and trial-and-improvement goes a long way! Now the echo test works well! Now to 'phone my family back home...

---

### Post by Keith_Beef on 2009-08-29
I'm trying to set up Ekiga behind a Netgear DG834G v.4.

I can call the 500 echo test, and that works. Video and audio work.

But the 520 callback test does not work.

Using Ekiga 3.2.0, I don't even see any network parameters in the preferences windows...

I set up a second Ekiga SIP account, to try getting a connection going between my main system and a laptop, and I can't call one machine from the other.

How can I tell if Ekiga has correctly set up the networking parameters, or if I need to go into my router and make a few rule changes?

K.

---

