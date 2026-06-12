---
title: "ssh tunneling Question"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by pythonsyntax on 2010-07-15
I am useing bshellz and i want to know  how do i setup ssh tunneling in firefox when i am surfing the web.I newbie when it come to ssh tunneling.i hope someone can help me.

---

### Post by dmizer on 2010-07-15
Use the -D switch to set up a proxy server and configure firefox for a socks proxy.

More information here: [https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Dynamic%20port-forwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Dynamic%20port-forwarding)

---

### Post by pythonsyntax on 2010-07-20
How setup ssh tunneling?

---

### Post by dmizer on 2010-07-20
From the link I gave you above:

> Dynamic port-forwarding turns your SSH client into a SOCKS proxy server. SOCKS is a little-known but widely-implemented protocol for programs to request any Internet connection through a proxy server. Each program that uses the proxy server needs to be configured specifically, and reconfigured when you stop using the proxy server.

For example, say you wanted Firefox to connect to every web page through your SSH server. First you would use dynamic port-forwarding with the default SOCKS port:

```
ssh -C -D 1080 laptop
```

The -D option specifies dynamic port-forwarding. 1080 is the standard SOCKS port. Although you can use any port number, some programs will only work if you use 1080. -C enables compression, which speeds the tunnel up when proxying mainly text-based information (like web browsing), but can slow it down when proxying binary information (like downloading files).

Next you would tell Firefox to use your proxy:

    * go to Edit -> Preferences -> Advanced -> Network -> Connection -> Settings...
    * check "Manual proxy configuration"
    * make sure "Use this proxy server for all protocols" is cleared
    * clear "HTTP Proxy", "SSL Proxy", "FTP Proxy", and "Gopher Proxy" fields
    * enter "127.0.0.1" for "SOCKS Host"
    * enter "1080" (or whatever port you chose) for Port. 

You can also set Firefox to use the DNS through that proxy, so even your DNS lookups are secure:

    * Type in about:config in the Firefox address bar
    * Find the key called "network.proxy.socks_remote_dns" and set it to true 

The SOCKS proxy will stop working when you close your SSH session. You will need to change these settings back to normal in order for Firefox to work again.

To make other programs use your SSH proxy server, you will need to configure each program in a similar way.

---

