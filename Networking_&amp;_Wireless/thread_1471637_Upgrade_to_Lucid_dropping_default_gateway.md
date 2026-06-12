---
title: "Upgrade to Lucid dropping default gateway"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by stormcel on 2010-05-03
This is an unusual problem and I can't seem to find an answer on the forums.
I was running 9.1 server and my network is set for dhcp, and I never had a network issue.  I have a webpage served on the server with some status indicators for the box (checks for certain running processes and all ip settings) so as to make it simple to see if anything has gone wrong.
Updating to Lucid went smoothly, but when I went to sudo apt-get update I got a stream of fails, so then I tried to ping google by name and ip and both failed, when I checked ifconfig I was on the local network and was able to ping the router.
My status web page showed everything was fine but the gateway entry was empty.
then i manually set a default gateway and all was well, fully connected and able to resolve ip's, and my web status page had the gateway listed nicely.  On reboot I am able to resolve and connect, but my status page has the gateway back to blank and the route command returns an asterisk(*) as the gateway.
Is this expected behavior? Is this a bug? Is there a file to change to ensure that it gets a gateway from dhcp?

edit:
running ifconfig eth4 dhcp status returns dhcp, unknown host .......?

---

