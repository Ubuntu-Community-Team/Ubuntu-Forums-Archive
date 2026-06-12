---
title: "sshpass script for connecting to two nested machines?"
date: 2012-05-25
forum: Networking &amp; Wireless
---

### Post by pinolo on 2012-05-25
I need a script to connect through sshpass from my machine "A" to a machine "B" and from "B" to a machine "C" (can't see C from A...).
The following script

```
sshpass -p 'psswd' ssh -X user@domainB.com
sleep 10
sshpass -p 'psswd' ssh -X user@domainC.com
```

doesn't work, it connects just to domainB. probably just because it is interrupted as I connect to B.

is there a way to write "sshpass -p 'psswd' ssh -X [email]user@domainC.com[/email]" when i'm connected to domainB? (without writing my password on a boot script on machine B)

thanks

---

### Post by papibe on 2012-05-25
Hi pinolo. Welcome to the forums!

The best solution for the situation you are describing is create an ssh tunnel by mapping the C ssh's port to an A local port (using a connection to B).

Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1926042&highlight=rsync+daemon") (specially post #4).

Also, you would need to send the first ssh command to the background, so you can execute the next command.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by pinolo on 2012-05-26
you mean something like

```
ssh -L 2222:machineC:22 machineB 

ssh -p2222 localhost

ssh -p2222 user@domainC.com  

```
?

how can I choose ports to use? do I risk conflicts?

---

### Post by papibe on 2012-05-26
Yes, but more like:
```
sshpass -p 'psswd' ssh -N -X -L 2222:machineC:22 machineB &
sleep 10
sshpass -p 'psswd' ssh -X -p2222 localhost
```
The second command will connect you to machineC.

> **pinolo said:**
> how can I choose ports to use? do I risk conflicts?
You just choose a port that is now being used, but it's a good idea to choose one in the dynamic range to avoid conflicts(49152-65535).

Tell us how it goes.
Regards.

P.S.: once you close the connection with machineC, you would need to kill the tunnel by doing:
```
kill %1
```

---

### Post by pinolo on 2012-05-29
I don't know if this code is correct

```
sshpass -p 'psswd' ssh -N -X -L 2222:user@domainC.com:22 user@domainB.com &
sleep 10
sshpass -p 'psswd' ssh -X -p2222 localhost
```

anyway I get the following error:

```
channel 2: open failed: administratively prohibited: open failed
ssh_exchange_identification: Connection closed by remote host
```

---

### Post by papibe on 2012-05-29
> **pinolo said:**
> ...user@domainC.com:22 [email]user@domainB.com[/email] ...
...
channel 2: open failed: administratively prohibited: open failed
ssh_exchange_identification: Connection closed by remote host


It could be a couple of things: (1) the server does not allow tunneling (option "PermitTunnel"); or (2) you are binding the tunnel using the server publics IPs, and the ssh it not bound to them (thus you are being rejected by either the firewall or the service itself).

Regards.

---

