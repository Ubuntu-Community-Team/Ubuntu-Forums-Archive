---
title: "vpn X application"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by ghoran on 2009-03-01
I connect to work using the Cisco Systems VPN Client Version 4.8.01 (0640)

All works great but, I would love to be able to run an X application that is on my UNIX server (work) and have it display locally on my UBUNTU machine.

I create a telnet session onto the UNIX machine.

I set the DISPLAY environment variable to the client address seen here :
VPN tunnel information.
Client address: XXX.YYY.ZZZ.AAA

with :0.0

It looks like it is timing out:
Error: Can't open display: XXX.YYY.ZZZ.AAA:0.0

I might simply be asking for too much.

Will I need to install any X app that I like locally on my Linux box and have it point to my unix server for data?

---

### Post by ghoran on 2009-03-19
I solved this so I wanted to post the answer.

ssh is your answer.
ssh -fCX -c blowfish {user}@{server} "{full path to xterm}xterm"
-f sends it into the background as a daemon.
-C is "compress data," so things are faster. 
-X is "tunnel X protocol"
-c blowfish, which says "use blowfish as the session cipher" - as a
block cipher,

Once you do this from your ubuntu terminal you can run an xapp from the {server}
I have done this from 3 of my servers at work.
It ROCKS!

- you might have to do xhost + from the ubuntu command line


Some issues I ran into was that I needed the system administrator to
- turn X11Forwarding on in the sshd_config file
- restart sshd with a "-4" option for IPv4 mode only. <- This might be related to the operating system version.

---

### Post by uzi09 on 2009-03-19
That's awesome, thanks for the update.

However, have you tried [FreeNX]("https://help.ubuntu.com/community/FreeNX")?

It's already quite secure because it runs over SSH, but if you're really paranoid, you could probably run it over a VPN connection too!

---

