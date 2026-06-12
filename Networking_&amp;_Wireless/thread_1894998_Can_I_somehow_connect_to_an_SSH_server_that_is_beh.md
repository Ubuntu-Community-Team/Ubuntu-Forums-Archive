---
title: "Can I somehow connect to an SSH server that is behind a router with no ports open?"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by runesvend on 2011-12-13
Hi

My objective is basically stated in the title. I have a computer behind a router (at my parents' house) that I want to connect to via SSH to see how it's doing. The problem is that there are no ports opened on the router behind which the computer is.

I've read about SSH tunneling, but I don't understand it well enough to figure out if it could be used for this purpose. The idea would be that the computer behind the router connects to an SSH server at my place. If it loses the connection it should reconnect. Using this approach I can, whenever I want to connect to the computer behind the firewall, send a request over the connection *it* opened to me, and thus I should be able to communicate with it.

To me it seems it's at least possible in theory, but I don't know if it's easily done in practice. Can anyone answer this question?

Thank you for your time.

Regards,
Rune Svendsen

---

### Post by theyain on 2011-12-14
If you had a program of some sort running on the ssh server that would send a couple of packets to a listed IP address on the SSH protocol (eg, your home network), you could use this to open up an SSH session.

I've been meaning to write this for a year or two now but have been just to lazy to do so.

So yes, it is possible...

---

### Post by kgoess on 2011-12-14
The ssh command you want to run on the machine at your parents' house would look something like this:


```
ssh_port=22
any_unused_high_port=2222
address_of_your_place=1.2.3.4
yourname=theyain

ssh -R $any_unused_high_port:localhost:$ssh_port $yourname@$address_of_your_place

```That connects port 2222 on the (R)emote machine, the one at your place, to port 22 on your parents' machine.

On the machine at your place you would connect like this:

```
ssh localhost -p2222
```But that doesn't address the problem of what you do when the connection goes down, how you recognize that and re-open the connection.  On  the desktop of my mother-in-law's imac I have a shell script called "get help from son-in-law" that she can click on when I need to help her by doing remote debugging. It also runs vnc and sets it up so I can see her desktop.

Hope that helps!

---

### Post by runesvend on 2011-12-16
Thanks for your input all.
kgoess, that might be exactly what I need. I thought about the case of the connection going down too, which *is* necessary to account for. There's this program called [autossh]("http://www.harding.motd.ca/autossh/") which is supposed to take care of this. I haven't tried it out though.

I found out that on the router at my parent's house, which I don't have access to, UPnP is enabled. So it was as simple as using the script from [this guide]("http://www.howtoforge.com/administrating-your-gateway-device-via-upnp") to open up a port on the router. I was able to connect to an SSH server running on the same machine from which I was connecting, so as far as I could tell it worked. I will be checking, when I get back in a week or so, if the port forward is still active. If it is still open, it seems to be all that is required. But the other trick might come in handy if the ISP decides to close this port again for some reason. Or perhaps I would just set up a cron job that opens up the specific port every hour. I'll see when, or if, it comes to that.

---

