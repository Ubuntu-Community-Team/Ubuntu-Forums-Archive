---
title: "how do I browse a shared drive via openvpn in thunar"
date: 2013-06-27
forum: Networking &amp; Wireless
---

### Post by landersohn on 2013-06-27
I have a probably silly question: my employer created an OpenVPN server. I would like to know, how I can get access to the shared drives
I have wicd installed and openvpn. I do have the client.open file.

I run 
sudo opencpn --config client.open
from a terminal window and it seems to connect, althougth only when I run this as root. In a user context I get a bunch of errors

ifconfig shows a new interface (tun0)

Question is, how do I get to browse the shared drives? The server is windows. 
I tried to open thunar, and use "go"-"Open Location".

smb://<server-name> but only get an error "failed to retrieve shared list"

When I enter
smb://<server-name>/<shared directory> I get
"failed to mount windows share".


What am I doing wrong? BTW I am happy with command line in general, I'd prefer a solution that doesn't include network-manager-gnome

All posts I found focus on the initial connection to the VPN server which seems to be working fine

---

### Post by landersohn on 2013-06-27
I figured it out. The trick was to add the following lines to the [global] section in smb.conf:

client lanman auth = yes
client ntlmv2 auth = no

with this change, the authentication works ok and I can get to the drive I need to get to.

---

