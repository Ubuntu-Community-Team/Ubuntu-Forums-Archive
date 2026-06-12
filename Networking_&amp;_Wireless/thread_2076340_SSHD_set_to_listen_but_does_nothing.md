---
title: "SSHD set to listen but does nothing"
date: 2012-10-25
forum: Networking &amp; Wireless
---

### Post by pkara on 2012-10-25
Hi,

I've had Nomachine NX server, node, and client 3.5 set up on my Ubuntu 12.04 LTS machine for a quite a while now and it has always worked fine.

Recently I tried to remote log in (from outside the subnet) and I've found that it no longer works.

I've narrowed down the problem to the SSHD daemon.  The port is set to a non default one, 8888.  

If I do:

ssh -v localhost

from the command line (non-root), it works fine and I see the appropriate [SSHD] messages in the auth.log file.

However, when I try to SSH log in from another machine, even within the same subnet, SSHD doesn't kick in at all and accept in the incoming request.  The putty client just "sits there" and says nothing for like 15 minutes and so I have to close it.  

However, the SSHD daemon does seem to be listening correctly:

paul@Paul-BluePC:/var/log$ ps -A | grep sshd
 3169 ?        00:00:00 sshd

paul@Paul-BluePC:/var/log$ sudo ss -lnp | grep sshd
LISTEN     0      128                      :::8888                    :::*      users:(("sshd",3169,4))
LISTEN     0      128                       *:8888                     *:*      users:(("sshd",3169,3))


Moreover, my sshd_config and hosts.allow files are set correctly (they are identical to other working configurations I have on other NX server machines).

Any thoughts?

I am not seeing any [SSHD] messages come up in the auth.log, so it makes me think SSHD isn't responding, but maybe it's not even getting the requests?

-Paul

---

### Post by pkara on 2012-10-25
as an additional note,  I've just figured out that I can SSH log in from other machines.  So the problem is the client specific.

However, the same client CAN log into other SSHD implementations on OTHER machines.   Moreover, other clients on other machines CAN log into this SSHD implementation.

Why would the client not be able to log into a specific SSHD impementation, yet be able to log into others, while other clients CAN log into this specific implementation?

---

### Post by pkara on 2012-10-26
I've further narrowed down the problem.

It seems that it only happens from Windows 7 machines.  That is, SSH works from ubuntu machines into the SSHD daemon running on another Ubuntu machine, but when I try to SSH in from Windows 7 machines it times out.

Perhaps this might suggest some ideas?

---

### Post by steeldriver on 2012-10-26
what client are you using on the Windows side? could it be some kind of GSSAPI timeout?

---

### Post by pkara on 2012-10-26
i've tried a couple different clients.  Putty being the main one from multiple win 7 machines.  I've also tried WINSCP.  Moreover, Nomachine NX won't work either and I'm assuming it's the SSH problem since it relies on it.

I can, however, Putty into another SSHD implementation running on a different machine from this same Win7 client, which suggests its a server side issue, and client specific to win7 machines using Putty, WINSCP, and NX at the least.  And again, it stalls on SSH-ing in from 2x win7 machines i've tried, both of which SSH fine into other implementations.

---

### Post by pkara on 2012-10-31
Ok i've narrowed down the problem further.  It seems to only happen when I have the sshd listening port set to a particular value.

If I go into the sshd_config file and set it back to 22 it works fine.

Why would the port make any difference?

---

### Post by dannyboy79 on 2012-10-31
are you tring from the win7 client using a hostname or the actual IP? also, are you sure you're specifying the port when it's set to a non-standard port number? Seems weird it works when you set port to 22 but doesn't when port is different, that leads me to believe in your client on win7 you weren't specifying the port.  just my 2 cents

---

