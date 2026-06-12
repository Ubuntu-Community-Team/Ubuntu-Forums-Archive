---
title: "installing openvpn blocks all regular network connections"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by lubob on 2012-04-20
Hi there!

I am running 10.04 and I am facing a problem with NetworkManager and OpenVPN.

After installing Openvpn, everything works fine. I can establish a VPN connection and transmit data. I can close the VPN connection and use normal connections as usual and so forth...

However, if I reboot my machine, then none of my connections will work. "Not work" means, my machines connects to the router and the connections shows up as being active in NetworkManager but actually no data is transmitted.

Now the strange thing: After removing OpenVPN via the package manager, all my network connections work fine again.

So the current situation is like this: Whenever I want to use OpenVPN, I have to install it and after usage I have to remove it. Otherwise it will block the usage of my normal connections.

Any idea?

Lucius

---

### Post by SeijiSensei on 2012-04-20
My first guess is that you have different routing set up with the tunnel active than without it.

You certainly don't need to remove it each time.  At worst, you can bring down the tunnel either by running:

```
sudo service openvpn stop
```

or, if that doesn't work,

```
sudo ifconfig tun0 down
```

If you're using TAP, then replace tun0 with tap0.  To make sure that the interface is called tun0|tap0, run the command "ifconfig" after the tunnel is active.  You'll see the interface it has set up and the IP address assigned to it.

Reinstall OpenVPN, then before you start the tunnel, run the command "route -n".  Then start the tunnel and run the command again.  Does the routing table differ?

---

### Post by lethalfang on 2012-04-20
> **SeijiSensei said:**
> My first guess is that you have different routing set up with the tunnel active than without it.

You certainly don't need to remove it each time.  At worst, you can bring down the tunnel either by running:

```
sudo service openvpn stop
```

or, if that doesn't work,

```
sudo ifconfig tun0 down
```

If you're using TAP, then replace tun0 with tap0.  To make sure that the interface is called tun0|tap0, run the command "ifconfig" after the tunnel is active.  You'll see the interface it has set up and the IP address assigned to it.

Reinstall OpenVPN, then before you start the tunnel, run the command "route -n".  Then start the tunnel and run the command again.  Does the routing table differ?


Happened to me once. I just made /etc/init.d/openvpn non-executable by "sudo chmod a-x /etc/init.d/openvpn"
And if I want to start openvpn, "sudo sh /etc/init.d/openvpn start"

---

### Post by lubob on 2012-04-21
Thank you both of you. Problem solved :)

---

