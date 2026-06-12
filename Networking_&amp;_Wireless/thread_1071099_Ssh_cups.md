---
title: "Ssh cups"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by Recruit0 on 2009-02-15
I'm trying to setup my laptop so I can print to my university's printer after SSHing in. I must be able to do this without root access (on the server) so some solutions won't work. The printer is a HP LaserJet 9000 or 9040... MFP (not sure bout MFP part). I tried setting up a SSH tunnel and port forwarding but didn't work. I thought CUPS uses lp/lpr so I thought with SSH I could make CUPS send commands through the connection but can't find instructions online.

---

### Post by nixscripter on 2009-02-17
You should be able to tunnel it. What did you do, exactly?

The general procedure, as you probably know is this:

On your machine, run: ```
ssh -L 631:university.print.server.name:631 you@loginbox
```

And keep the ssh connection on. You can then connect to yourself with CUPS (port 631), and it will be forwarded.

Hope this helps.

---

