---
title: "SOCKS, SSH proxy problem in firefox"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by neeagl on 2010-03-29
Hi,

I have two machines.. one server (A) and client (B).. I have internet running on my server A which is using my university's proxy. Now I install openssh server on this machine A.

Now on the second client machine B, I started socks proxy using ssh -D 9999 username@machineA
and then setting up socksv5 in firefox proxy settings with 127.0.0.1 and localhost both and port number 9999

But its not working :(

However, after doing the ssh to the server machine, wget is working at the shell.

Please help me out.

---

### Post by dmizer on 2010-03-29
> **neeagl said:**
> Hi,

I have two machines.. one server (A) and client (B).. I have internet running on my server A which is using my university's proxy. Now I install openssh server on this machine A.

Now on the second client machine B, I started socks proxy using ssh -D 9999 username@machineA
and then setting up socksv5 in firefox proxy settings with 127.0.0.1 and localhost both and port number 9999

But its not working :(

However, after doing the ssh to the server machine, wget is working at the shell.

Please help me out.

You will also need to manually configure DNS servers when running through a socks SSH proxy. More information on how can be found here: [https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

---

### Post by neeagl on 2010-04-01
Tried that.. but didn't work.. :(

---

### Post by dmizer on 2010-04-01
> **neeagl said:**
> Tried that.. but didn't work.. :(

How exactly did you configure the proxy settings in Firefox?

---

