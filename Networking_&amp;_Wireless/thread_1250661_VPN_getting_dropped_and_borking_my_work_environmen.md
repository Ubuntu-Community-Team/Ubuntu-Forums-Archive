---
title: "VPN getting dropped and borking my work environment."
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by mslade on 2009-08-26
Hi.

Ubuntu 8.07.

This is going to be one of those annoying, vague questions.  I work remotely over VPN.  Once VPN'd, I use mount what I need using sshfs and work using local-looking paths.  I usually have Kate (text editor) open for this, as well as a few shells to the remote machine.

Occasionally throughout the day I will lose my VPN connection without ever noticing a network hiccup.  This in turn makes all my applications turn on me as if they want me to die.  This in turn makes me sad.

For example, Kate will lock up unforgivingly until I unmount sshfs.  Evolution locks up until I kill -9 it.  Obviously my shells lock up, but that's because when I reconnect the VPN I usually wind up with a new IP and the connection is gone.

Anyhow... I feel like my VPN connection is too sensitive to super brief hiccups in WAN connectivity.  Is there a way to make it more forgiving, so that the VPN won't drop at the briefest break in connection?  I'm not intimately familiar with the VPN protocol so maybe this question is just silly.

The next question is along the same lines.  It seems to my uneducated brain that when the VPN gets dropped, the OS still tries to use that (borked) connection and anything network-based (sshfs, email, ...) hangs mercilessly.  Is there a setting I can tweak to tell Ubuntu or the network manager to timeout quicker when the VPN isn't available?

I appreciate any help you can offer.  I will even tolerate some verbal abuse thrown in, if it includes some practical advice.

ms

---

### Post by mslade on 2009-09-02
Does anyone have any advice?

---

### Post by jonobr on 2009-09-02
Misery Likes company as they say,

I VPN to remote locations using KVPNC over vpnc.

I remote desktop to a remote set of windows boxes,
I come back after a while remote desktop appears to be frozen,
however, its actually the VPN not routing packets to the remote location.
The connection is shown as up,
Ifconfig shows the interface is still there, everything looks good, but it wont let me in.

Its rather frustrating, especially as windows servers dont like improper disconnecting of RD sessions and consider you still logged in.
The default terminal services manager, allows only 2 simultaneous connections and so it wont let in another connection if you have the two used up, meaning I have to get someone remotely to kick off the sessions.

I came up with a round about way  (of no use to you) of getting out of that.
I was thinking at the time it was an inactivity timer, but doubted that as I guess it should have disconnected the connection.

I thought sending a continuous ping may keep the link up but given my workaround, I was happy enough and did not go down that route.

I could not find anything in the Gui which had any answers for my problem.

Again, rather then a solution, this is more a "I feel your pain" response

---

### Post by sp0nge on 2009-09-02
Are these IPSec VPNs? And are either of you connecting wireless? I have recently encountered a problem where my IPSec VPN chokes if I conect wireless, but once I connect to the wire, it works just fine.

---

