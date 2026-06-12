---
title: "KNetworkManager always asks for confirmation of wireless security details"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by WebDrake on 2011-11-02
Since upgrading to 11.10 I've had an unexpected (though benign) problem: whenever connecting to a wireless network with any kind of security, KNetworkManager always pops up the wireless network settings dialog, which must be OK'd before it will connect.

The wireless networks in question are set to connect automatically, and the security details are stored correctly -- all I have to do is click OK.

How can I get KNetworkManager to stop asking for confirmation of the security settings in this way?

---

### Post by Nir Friedman on 2011-11-02
I have this problem except that the password is not entered for me. This is despite the fact that I have it set to store the passwords in an unencrypted file (as opposed to prompting every time).

---

### Post by bhonermann on 2011-11-03
Same problem for me.  Can't find any evidence that knetworkmanager is even trying to store the password.  No files appear in ~/.kde/share/apps/networkmanagement/connections/  and kwallet doesn't have any storage credentials.

Anyone?

---

### Post by WebDrake on 2011-11-10
Hmm, I'm getting the same no-password-remembered problem as you describe in a new install where the password was not already registered in kwallet.

I've made a point of opening the wallet and editing the security details directly in the "Manage Wireless" settings; I'll confirm tomorrow whether this actually results in the password being remembered.

On my other system, where the wireless network details were carried over from an earlier install, the password is remembered without problem, it's just that I keep getting asked to OK it ...

---

### Post by WebDrake on 2011-11-11
OK, making sure that kwallet was open and then editing the network settings at least ensured the password was stored.

Nevertheless, I'm still getting the request to OK the network security settings every time I attempt to connect.  Anyone have any idea how to fix this?

---

### Post by Nir Friedman on 2011-11-11
I'm having crazy issues in general with wireless, I'm wondering whether a clean install is the way to go. God Kubuntu is pissing me off right now. WebDrake, did you do a clean install or ugprade?

---

### Post by WebDrake on 2011-11-11
Clean install, but kept /home directory intact from earlier install.

---

### Post by Nir Friedman on 2011-11-11
Ack, that makes me sad, I was hoping that a clean install would avoid these issues. Is network information stored in /home or /?

---

### Post by WebDrake on 2011-11-12
Wireless information I think is stored in /home/, associated with a single user, unless you set it up as a connection available for everyone.

---

### Post by Nir Friedman on 2011-11-17
If it is stored in /home, then maybe by keeping your /home from the previous install it led to some kind of problem. I have seen similar problems in other threads where deleting a whole bunch of config files solved it. To be honest, Ubuntu is just terrible at these distro upgrades, flash and wireless and at least one other random problem always get screwed up (for me, it was flash + wireless + microphone this time).

---

