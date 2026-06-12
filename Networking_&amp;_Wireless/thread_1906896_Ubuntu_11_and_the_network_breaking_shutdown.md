---
title: "Ubuntu 11 and the network breaking shutdown"
date: 2012-01-10
forum: Networking &amp; Wireless
---

### Post by stonneway on 2012-01-10
Hi chaps

We have a problem with a number of Lenovo E30 machines running Ubuntu 11 which appear to crash the network when they shut down.

We have the same machines running Windows without any problem but recently we have installed Ubuntu on 8 of them and so far 3 of them have caused the switch they are attached to to crash during the shutdown of the OS and several others are suspected of causing other crashes. Removing the machine from the switch brings the switch back up again. 

When this happens the machines appear to lock up mid shutdown and the keyboard lights don't respond. Powering off the machine or rebooting it also works to get the switch back up.

The switches are Draytek 24 port managed gigabit switches. We've replaced the two of the switches 3 times a piece and are confident that the switches themselves aren't at fault.

Has anyone else seen this?

The specifics are as follows;

Lenovo E30 (machine type 782436G)
 - Intel 82579LM onboard NIC
 - Ubuntu 11.10

Switch is VigorSwitch G2240
 - Firmware v1.42




Olly

---

### Post by jonobr on 2012-01-10
Hello


I've seen posts like this on smaller scale home routers, but this is the first big one:D

When you say crashed, do you mean the whole thing is inaccessible?
Can you console in? 

I have seen solutions propose many things in the past,
reducing MTU size on the connected machines (maybe match the MTU used on your windows system) and disabling IPV6,
upgrading firmware on the unit (yours is at the latest) and others of upgrading memory and so on, also irrelevant to you.
Also NTP cuasing problems wioth SMC routers, but that was on bootup rather then shutdown

All the above being said, I have never seen a related post indicating this was solved (with the exception of SMC and NTP) but no harm suggesting to you I think.

On the vendor side, I work for telco companies and this kind of problem had two sides, for equipment manufacturers

1- A device/card/action or event caused our device or card to lockup or hiccup, that was a concern and we would inform customers and beat up on the other vendor.
2- More concerning was that our device could not prevent itself from shutting down. This was always a P1 issue for us. Yes, its not our fault, but we should be able to prevent ourselves going belly up and bringing down the whole network. The concern being, a competitors device may be affected by the client  but not have the same dire consequences.

For point, Im saying the vendor should have skin in the game even though its not his fault and try and figure out the issue also. Im not sure if you have a support contract , but maybe accessing their forums may help.
If they dont want to help, thats understandable, but short sighted. again, it is not their problem, but stopping their device shutting down should be of interest to them


What I would try is to replicate in a lab, away from the production environment, have a hub with another laptop and run a wireshark capture , taking note of everything leaving the box on an ip or mac level.
Once you have the thing replicated and know whats being sent out , (hopefully that list would be small) you can start to prevent packets from being sent, getting down to the one or ones that are causing trouble.

It may be a bit of effort, but all I can think of:-0

---

