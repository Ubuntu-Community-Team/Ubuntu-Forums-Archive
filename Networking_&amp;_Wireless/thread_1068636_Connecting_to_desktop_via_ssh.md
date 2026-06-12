---
title: "Connecting to desktop via ssh"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by taojian on 2009-02-13
I'm trying to remotely administer my parents-in-law's Ubuntu (8.10) desktop, in case they break it. Before I left their house last time I started the openssh server running, configured it as best I could, and took a copy of the sshd_config file (I couldn't test it at the time). Now I'm unable to log into my shell account there, and looking at the config file I noticed that this line is commented out:

#AuthorizedKeysFile	%h/.ssh/authorized_keys

That's where I put my key when I did the configuration (ie in the authorized_keys file under the home directory of the user I'm trying to log in as). If this line is commented out, does it mean it recognizes NO authorized keys files, or is there a default? Right now I can't tell why login is failing (ssh -vvv doesn't give any specific reasons for failure) and I'm wondering if this is my most likely culprit.

TIA,
Eric

---

### Post by taojian on 2009-02-13
Okay, what's happening is not what I thought was happening. I thought I was actually contacting the ssh server on the port I specified, but nc says it can't contact anything on that ip/port, so I tried ssh into a random port, and got the same response – like it's failing to authenticate with a ssh server, except I know there's no ssh server there. So I'm failing to reach the machine at all.

I don't really know what's happening now, I set the ssh server to listen on a certain (non standard) port. Now when I scan with nc, it says it finds tcp/ssh successfully on port 22 (where there shouldn't be anything running), while the port I specified in sshd_config still gets "Connection refused". Could it be that the ISP is blocking access to the port I specified? But then why would scanning port 22 succeed...?

---

### Post by issih on 2009-02-13
How is your parent's machine connected to the internet? Is it behind a router? if so do you have port forwarding set up?

Not really sure why port 22 would be open if you do have a router, unless the router itself allows remote access for configuration.

---

### Post by taojian on 2009-02-13
The machine is connected through a neighborhood LAN sort of thing -- it's a housing compound that provides connections to the residents. That means the ethernet comes straight in through the wall, and whatever routing is going on is strictly outside my control. I should have thought this through better while I was actually there, but it's too late now.

Is there anything besides port scanning that I can do to figure out exactly what the ISP is doing? At this point I will need to simply work around their setup; if that means changing the port that sshd uses, so be it.

Thanks!

Eric

---

### Post by taojian on 2009-02-13
I neglected to mention that this is a pppoe connection, though maybe that's obvious from the above.

I did a full port scan up to 1000, and only ports 21, 22 and 23 accept connections. Does this seem odd? Is there a chance that I'm actually connection to some sort of proxy/gateway machine?

---

### Post by issih on 2009-02-13
hmmn, hard to say to be honest, i think it being a pppoe means you are probably linked directly to a modem, but there are no guarantees on that. You really need to get the specs of the connection from whoever will know them, otherwise it will be impossible to know how to set this up.

One alternative possible solution might be to use ssh to connect through to your machine from theirs, and then set up a reverse tunnel which you should be able to use to connect to their machine.

this way all the onus is on you to sort out port forwarding and static ip/dynamic dns issues at your end.

All that would then be required would be for them to fire up a little script that ssh'ed to your box and set up a remote tunnel allowing vnc traffic through (probably port 5900).

You would then just connect to the forwarded port on your local machine and things should just work regardless of the network architecture at your parents end.

Hopefully that makes sense, if not give me a shout.

---

### Post by taojian on 2009-02-15
Cool, thanks for these tips. Guess I'd better bite the bullet and call the ISP. The reverse-tunneling method makes sense, and would certainly work, except for the extreme lack of technical ability on the part of my parents-in-law: I'd have to make a double-clickable bundle of some sort.

Thanks again,
Eric

---

### Post by kevdog on 2009-02-15
See reverse tunneling as suggested above -- will make your life a lot easier.

---

