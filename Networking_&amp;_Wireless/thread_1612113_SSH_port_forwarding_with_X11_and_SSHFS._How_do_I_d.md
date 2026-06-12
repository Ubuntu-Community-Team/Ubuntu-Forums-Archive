---
title: "SSH port forwarding with X11 and SSHFS. How do I do this?"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by Jarige on 2010-11-02
Hey guys,

I've used wake on lan and SSH on the local network for some time now. I also used SSH to mount a filesystem (SSHFS / sftp, same thing, right?) and I could forward X11, loved it. I used both these options for my convenience.

So I decided it was time to open up some ports on my router (Linksys WRT320n running dd-wrt) and try to set up a remote connection. This actually worked after some time, so I'm now able to turn on my home computer from the Internet (school in my case) and then log in to it through SSH.
I set this up using other ports then the default ports. Something like this (these are not the actual ports I use, just  examples):
port 2112 -> port 9 (for wol, wake on lan)
port 2113 -> port 22 (for SSH)

This information might be useful: I set this up using public and private keys. This is necessary for SSHFS to work properly I think and it also makes it more secure.

And then I found (and had some presumptions that this was going to happen) that both SSHFS and X11 were not working.

I'd rather not open up more ports on the router for security's sake though, so I'm asking for other solutions. And if there really aren't any other solutions then please tell me which ports to forward. And if forwarding is really necessarily then please tell me how to make the client use port 2114 for SSHFS and 2115 for X11 so I can forward those ports to the default ports.

Any help would be greatly appreciated :)

---

### Post by Jarige on 2010-11-04
BUMP

I would really like a solution :)

If there's a chance to get transmission remote gui working through SSH then that would be amazing :D Although this has much lower priority then X11 and SSHFS...

---

### Post by Jarige on 2010-11-04
Apparently I need to tunnel some ports from my computer to my netbook. Did some research on it, but couldn't find a guide that fits my needs. I tried to do some stuff on my own using some guides and bits of information here and there, to no avail.
I could figure out that X11 uses ports 6000-6063 but couldn't find out how to tunnel them. That is, I couldn't tunnel the range, I tried tunneling port 6000 but that didn't work:
```
ssh -D 6000 *name*@*ip* -p *port*
```

And I couldn't find anything about sftp :(

---

### Post by Jarige on 2010-11-04
I just realized that I've been pretty stupid xD I kept forgetting to add '-X' to the ssh command. I'll try again tomorrow to see whether that makes a difference.

SFTP/SSHFS remains unanswered though, I'm still trying to figure out how to do this...

---

