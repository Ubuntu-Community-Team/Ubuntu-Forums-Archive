---
title: "Ubuntu 10.04 Network Manager (nm-connection-editor) can't set static IP or gateway"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by shinobitux on 2010-10-27
Recently I've noticed several other 10.04 users unable to set a static IP address using Network Manager (nm-connection-editor).

In one instance, I tried to set the IP address as static for a user:

1) I right-clicked the network icon, selected Edit connections
2) Under the "Wired" tab selected "Add"
3) Changed the default name, checked "Available to all users" and clicked on the IPv4 tab
4) Selected "Manual" for method and set IP: 10.208.13.24 mask 255.255.255.192 (as configured by the company) and gateway 10.208.13.1
5) Added two dns servers xxx.xxx.xxx.xxx, xxx.xxx.xxx.xxx and domain extension
6) Clicked "Apply" and got the password dialogue (policykit?)
7) filled in the password

The first time everything seemed to go fine, but I had no internet access. ifconfig showed the correct IP address but in network manager I looked at the settings and the gateway showed "0.0.0.0"

At first I thought I had a firewall-blocked IP address (don't ask) so I tried changing it to 10.208.13.29  but ifconfig showed no change from the original IP address. No matter how many times I try, I can't change the IP address using Network manager (nm-connection-editor). Nor, once I saw that the gateway was "0.0.0.0" could I change the gateway. I keep going back and changing them, hitting apply, and when I check back nothing's changed. Sometimes it asks for a password, sometimes not.

I have seen this symptom several times in 10.04 in the last two weeks, but even though I might be willing to disable Network Manager on my computer and use /etc/network/interfaces the users I'm helping are not.

This is reminiscent of issues I've had with policykit and Fedora, but by know means am I certain that's the issue.

So two things:

1) Anyone know a resolution for this?
2) Where does nm-connection-editor store its state information for the current user so I can manually change it?

---

### Post by Iowan on 2010-10-27
[Here]("http://ubuntuforums.org/showthread.php?t=1536584") is a thread that might be helpful.  The trick is to hit ENTER at the appropriate places... :)

---

### Post by shinobitux on 2010-10-27
You really think that's it? Bizarre. 

I'll give it a try as soon as I can.

EDIT:

Yeah, that did it alright. I guess I made the mistake of assuming that the Apply button would have handled that event :P

Regardless, thank you for the assist ^_^

---

### Post by freephile on 2010-12-21
Wow, same BUG here.  I spent a good half hour trying to set a static IP address configured.  I could not figure out what I was doing wrong (because I wasn't) such that the 'Apply' button was grayed out.

The UI interface elements should not depend on a particular behavior that otherwise would prevent the user from accomplishing the task.

---

