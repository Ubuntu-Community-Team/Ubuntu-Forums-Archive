---
title: "Wifi goes up and down... sometimes stays down"
date: 2012-01-03
forum: Networking &amp; Wireless
---

### Post by MidnightJava on 2012-01-03
I've had intermittent Wifi issues since I began using Ubuntu 11.04 a few months ago. I'm now using the system in ways that make this unacceptable, so I've been doing web research looking for a solution.

I found several threads which may be relevant to my issue; so I have some ideas of how to proceed. The purpose of this post is to seek help on one aspect of the issue that I haven't seen reported by others.

My PC is connected to a wireless router (Actiontek provided by Verizon for Fios service) and a wired connection is not currently possible. The wireless signal is not as strong as I'd like (maybe 3 out of 4 bars), but it works reliably when I boot the PC into Windows 7. I've been at the PC and seen the wireless connection go away spontaneously and come back a few seconds later. But the main way I notice the issue is when ssh or vnc sessions from other computers in the house (wirelessly connected to the Actiontek router) suddenly go down. I can usually reconnect within seconds, but sometimes it takes minutes.

A typical interval between failures is an hour or two. Sometimes it stays up longer, but I don't think it's ever stayed up more than 24 hours. It fails when connections are idle and when I'm doing things on the PC.

Now for the part that's different. Sometimes (maybe once or twice a day) the connection goes away for good. I've been able to make it come back more than once by just moving the mouse to get the login screen to come up and entering my password to unlock the screen. I configured the Power Management preference to never have the computer sleep, and put the display to sleep after 15 minutes. I have the system configured to lock the screen when exiting screen saver mode.

So my question here is: are there other settings I should check that might explain why sometimes the connection goes away persistently? When I boot as Windows, I can have a vnc session up all day while I'm at work, but as Ubuntu it's good for a few hours at most and then gone until I get home and unlock the screen. I can't say that merely unlocking always brings it back. Maybe sometimes I've cycled the wireless connection off and on; but I'm sure that at least twice it came back by merely unlocking the screen.

---

