---
title: "Cannot switch VPN connection"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by _Dan on 2013-02-14
Hello,

Only the first OpenVPN connection I use after booting works. I wonder if the credentials are getting cached for this one or something?

Subsequent attempts to disconnect then re-connect to a different VPN server give me the common "invalid credentials" error messages and the connection fails.

However re-connecting to the first one I attempted always works.

Any suggestions for switching VPN connections without rebooting would be much appreciated!

---

### Post by TheFu on 2013-02-14
Have you tried connecting using the CLI interface instead?  Then you can specify** --verb 9 **and get lots of extra data.  Is it possible that when you close the VPN, that the process is still running?  Can you kill it?

**$ man openvpn** might provide some more ideas.

---

### Post by ahallubuntu on 2013-02-14
~

---

### Post by _Dan on 2013-02-14
Thanks for the advice,

I've just been trying running openvpn directly from the command line, it's not something I've done before.

The strange thing is, at one point I was able to connect successfully to all the VPN servers one after another with that approach.

But then shortly afterwards it stopped working that way (maybe because I tried connecting through network-manager). And then wouldn't work that way even after rebooting...

( example output: [http://pastebin.com/qp2FTrPA](http://pastebin.com/qp2FTrPA) )

The only thing that really consistently works is selecting only a single VPN server in network-manager after booting.

This is Ubuntu 12.10. I'm pretty sure the certificates are valid, since I can successfully connect to each by using Network Manager after booting.

The openvpn process disappears after disconnecting.

---

### Post by ahallubuntu on 2013-02-14
~

---

