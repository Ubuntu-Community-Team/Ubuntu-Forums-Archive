---
title: "vpnc doesn't prompt to resync RSA SecureID VPN Token"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by tram4 on 2010-10-26
I have a VPN connection setup using Vpnc which uses a hardware RSA token to connect to a Cisco VPN.  The username is saved in the config so I just have to enter my assigned PIN followed by the numbers that appear on the RSA token.  Everything works fine, but once in a while, when I try to connect, it fails.  No matter how many times I try to log in, it does not work.  It says the VPN Connection failed as soon as I put in my numbers.

After a bit of troubleshooting, I discovered that the reason is because the last login attempt failed due to inputting the wrong numbers (Human Error).  I found this out after trying on my Windows machine.  When I go to a Windows machine with a Cisco VPN Client, it recognizes this and asks me to enter the next passcode that appears on the token.  Once I do this, it connects fine on my Ubuntu machine with Vpnc installed.

It seems as though Vpnc is not configured to handle these synchronization requests, or it isn't supported.  I need to get this resolved so I don't have to go to a Windows machine every time the token needs to be synchronized.

Any Ideas?  Thanks in advance.

---

### Post by tram4 on 2010-10-27
Anyone?

---

### Post by stu31 on 2010-12-27
Hello,
  I was just googling around for the same thing, and found this:

[http://ubuntuforums.org/showthread.php?t=294628](http://ubuntuforums.org/showthread.php?t=294628)

Have you tried the --xauth-inter option?

Sound like this would do the trick. 
I haven't been able to try it out yet, though..

Best,
  -stu

---

