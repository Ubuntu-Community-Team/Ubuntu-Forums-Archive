---
title: "sniff lan internet trough ssh"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by Wessly on 2011-09-27
Hello everybody,

I will explain in few words:

-computer A (LAN connected to computer B, without INTERNET)
-computer B (LAN connected to computer A, with INTERNET and ssh-server)

Is there a way to transfer INTERNET access from computer B trough ssh to computer A?

---

### Post by Dangertux on 2011-09-27
Yes you can do this through the creation of an SSH tunnel

You can do the following

on computer A

```

ssh -D 8080 username@computerB_IP

```

This will create an ssh tunnel to Computer B(you will be prompted for your credentials) with a proxy server on Computer A.

Then in your browser settings on Computer A edit the proxy settings and set your proxy to localhost port 8080.

---

### Post by Wessly on 2011-09-27
Solved!

---

