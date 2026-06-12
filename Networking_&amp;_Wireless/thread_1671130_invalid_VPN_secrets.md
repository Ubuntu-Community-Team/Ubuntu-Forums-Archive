---
title: "invalid VPN secrets"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by haloflightleader on 2011-01-19
I keep getting this error message:

The VPN connection '<insert name here>' failed because of invalid VPN secrets

I have Ubuntu 10.10 installed on a Dell Latitude D600. It's a fresh brand new install. After I installed all the updates, I proceeded to install network-manager-vpnc. Then, I imported .pcf files so that I can connect to the office VPN, but it gives me the error message above.

I have gone to ~/.gnome2/keyrings and renewed everything. Tried moving them away, and then back again. Created a new keyring. Nothing.

Can someone please help? This is so frustrating.

h

---

### Post by haloflightleader on 2011-01-19
To test, I converted the .pcf into something vpnc understands. Then I called vpnc via cli and that connected just fine. I just can't connect using the Network Manager icon on the top right-hand corner.

What am I doing wrong?

---

### Post by haloflightleader on 2011-01-19
To test, I converted the .pcf into something vpnc understands. Then I called vpnc via cli and that connected just fine. I just can't connect using the Network Manager icon on the top right-hand corner.

What am I doing wrong?

---

### Post by haloflightleader on 2011-01-19
To further test, I installed 10.10 again in Virtual Box. I did the same vpnc configuration, this time it tells me:

The vpn connection '<insert name here>' failed because there were no valid VPN secrets.

What can I do?

h

---

### Post by haloflightleader on 2011-01-19
To further test, I installed 10.10 again in Virtual Box. I did the same vpnc configuration, this time it tells me:

The vpn connection '<insert name here>' failed because there were no valid VPN secrets.

What can I do?

h

---

### Post by haloflightleader on 2011-01-19
To further test, I installed 10.10 again in Virtual Box. I did the same vpnc configuration, this time it tells me:

The vpn connection '<insert name here>' failed because there were no valid VPN secrets.

What can I do?

h

---

### Post by haloflightleader on 2011-01-19
As another test, I created a PPTP VPN connection through network manager. This does not bring up the same error message.

---

### Post by nesquik on 2011-05-07
Have you tried checking "Available to all users"?

See my thread: [http://ubuntuforums.org/showthread.php?t=1750132](http://ubuntuforums.org/showthread.php?t=1750132)

---

