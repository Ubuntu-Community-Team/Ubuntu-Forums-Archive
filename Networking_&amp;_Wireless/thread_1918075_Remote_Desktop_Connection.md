---
title: "Remote Desktop Connection"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by Muhnamana on 2012-01-31
Ok, so I finally figured out how to connect to a VPN in Ubuntu. I open up Remote Desktop Viewer, enter some information and I either get a black screen or a blank screen, never fully seeing the other desktop.

I've read some suggestions to open the terminal and type rdesktop but nothing opens up with that either.

Am I missing some configuration somewhere?

---

### Post by satanselbow on 2012-01-31
The connection maybe firewalled at the other end ;)

On my local network I rdesktop into my account on an xp machine with the line below - not be best way to do it if you going outside your network though ;)

```
rdesktop 10.0.0.149 -u XPUSERACC -p XPUSERACCPASS -g 1280x800 -r sound:remote -r clipboard:PRIMARYCLIPBOARD -x l -T 'RDP: DIM8400 Windows XP'
```

-u / -p = user acount cred on dest machine
-g = window dimensions to fit my laptop
-r = leave the sound on the dest machine
-r = make clipboard data available
-x = tune data transfer for lan usage
-T = windows title on client machine

Hope that helps - or gets you started at least.

---

### Post by Muhnamana on 2012-01-31
Connection maybe firewalled at the other end? Would this be tied to the OS?

Reason I ask, is I can VPN and log into my machine from Windows, using Cisco VPN and Remote Desktop Connection, so I don't think its a firewall issue though, unless its tied to the OS, which wouldn't make sense.

I can connect to the VPN but can't seem to show my desktop at work.

> **satanselbow said:**
> The connection maybe firewalled at the other end ;)

On my local network I rdesktop into my account on an xp machine with the line below - not be best way to do it if you going outside your network though ;)

```
rdesktop 10.0.0.149 -u XPUSERACC -p XPUSERACCPASS -g 1280x800 -r sound:remote -r clipboard:PRIMARYCLIPBOARD -x l -T 'RDP: DIM8400 Windows XP'
```-u / -p = user acount cred on dest machine
-g = window dimensions to fit my laptop
-r = leave the sound on the dest machine
-r = make clipboard data available
-x = tune data transfer for lan usage
-T = windows title on client machine

Hope that helps - or gets you started at least.

---

### Post by satanselbow on 2012-01-31
Could be anything from the graphic bit depth, closed ports (3389 is default) to a bad implementation of rdp (as in WXPSP2)

You're not really giving much away as to what you have done so far... which makes offering any further assistance very difficult...

---

### Post by Muhnamana on 2012-01-31
What more information would you like?

I'm still fairly new when it comes to this stuff, so I can help give you as much information I can, I just dont know what you need.

---

### Post by Muhnamana on 2012-01-31
This Terminal Server Client looks very similar to the Windows counter part, but I've read it doesn't work well in 11.10.

[http://mixeduperic.com/ubuntu/how-to-remote-desktop-a-windows-server-ubuntu.html](http://mixeduperic.com/ubuntu/how-to-remote-desktop-a-windows-server-ubuntu.html)

Other suggestions mentioned rdesktop from the terminal, but that returned no results on my end.

---

