---
title: "SSH tunneling NOT tunneling?  Need help."
date: 2012-07-28
forum: Networking &amp; Wireless
---

### Post by AlexBooton on 2012-07-28
Hi, I know I'm doing something wrong; but what?

I use putty to establish an SSH connection to a remote server.

The putty configuration; under SSH/Tunnels is set to forward source port 5901 to localhost:5901.  

And that looks like it is set correctly.  In putty under "Forwarded ports" it say: "L5901  localhost:5901".  So that should be correct.

I make the SSH connection and get a remote terminal window.  So-far-so-good.

Then I try to make a VNC connection to <remote server>:5901 and it doesn't work?  Syslog shows that the connection from my ip to the remote server's IP on DPT=5901 was blocked.

If I drop the firewall, it works.

It looks to me that my attempted VNC connection is NOT going through the tunnel!  It's trying to make a connection outside of the tunnel and failing.

So how do I get the attempted VNC connection to go through the tunnel???

Is there an additional step?  What am I missing?

Thanks

---

### Post by steeldriver on 2012-07-28
you are trying to connect to the wrong end of the tunnel - you should be making the vnc connection to **localhost**:5901 - that's the whole point of tunneling ;)

---

### Post by AlexBooton on 2012-07-28
> **steeldriver said:**
> you are trying to connect to the wrong end of the tunnel - you should be making the vnc connection to **localhost**:5901 - that's the whole point of tunneling ;)


Thanks for the feedback.  I must be confused.  I thought that's what I was doing.

```
  In putty under "Forwarded ports" it says: "L5901 localhost:5901".
```

Doesn't that indicate traffic destined for remote port 5201 is to be tunneled to that remote port?  The VNC server is listening on that port.

If not, how do I tell putty what to do?

Thanks

---

### Post by steeldriver on 2012-07-28
Your putty setup is fine I think - it's just that when you fire up your VNC client you should be putting 'localhost:5901' in the box where it says 'Remote host' (at least that's how it works with both the TightVNC and UltraVNC viewers)

i.e. the VNC data goes from the remote machine's local port 5901 (L5901) **into** the SSH tunnel - then comes out of the tunnel on **localhost**:5901 - which is where your VNC client grabs it

Unless I have completely misunderstood and you are doing some kind of reverse connection? (client listening for connections initiated by the server?)

---

### Post by AlexBooton on 2012-07-28
> **steeldriver said:**
> Your putty setup is fine I think - it's just that when you fire up your VNC client you should be putting 'localhost:5901' in the box where it says 'Remote host' (at least that's how it works with both the TightVNC and UltraVNC viewers)


AhHa!  I was putting '<remote server>:5901 in the 'Remote host' edit box.

Works like a charm.

Thanks so much!

---

### Post by steeldriver on 2012-07-28
OK that's good! it *is* confusing - I did the same thing at first

---

