---
title: "Authentication Problems: RNX-N180UBE + WNDR4000"
date: 2013-03-01
forum: Networking &amp; Wireless
---

### Post by cantecleer on 2013-03-01
Hi. First I want to say I am completely new to ubuntu/linux, and I apologize if this has already been solved. I looked [here]("http://ubuntuforums.org/showthread.php?t=1579295") and [here]("https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455"), but I don't think that addresses my problem...

I am running Ubuntu 12.04, fresh install (w/updates via a wired connection). It recognizes the wifi adapter, which also recognizes my SSID. The problem is that it keeps asking me for my network password.

I have put in the password repeatedly, even showing the password to make sure I am not typing it incorrectly, but every time the "Authentication required by wireless network" still pops up and the adapter cannot connect to my router. 

I am wondering if I have something set wrong on my router that is preventing authentication. The security is WPA-PSK [TKIP] + WPA2-PSK [AES], if that matters at all.

If anybody has any advice, I'd really appreciate it. Thanks in advance.

---

### Post by oldcity11 on 2013-03-31
I think you are trying to access a WPA2 network. You would need to enter 
the passphrase or password given to you by the owner of the network.
hth

---

### Post by gordintoronto on 2013-03-31
Do you have other devices which connect to the router? What is the SSID? (Simple lower-case SSIDs work best.)

The Newegg reviews of your wireless adapter are great, especially among Linux users. The Router, not so much -- and it's an expensive router.

---

### Post by cantecleer on 2013-04-11
I apologize for missing your replies. I'm not sure how, but I managed to get things working. Even so, TY both for the help.

Sorry to take up space and not offer a better explanation for "fixing" whatever the problem was. I wish I could say more, in case somebody else has the same problem, but hopefully it was just something I was doing wrong.

In any case, thanks again.

(I'm unfamiliar with this forum, so if there is a way to mark this solved or archive it so it is out of the way, please do.)

---

