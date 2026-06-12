---
title: "How do I create a user account that has no Internet"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by Keypel on 2010-11-09
How do I create a user account without Internet access?

---

### Post by grahammechanical on 2010-11-09
Go to System>Administration>Users and Groups. Click Add. Do what the program asks you to do to set up a new user. You can then assign that user to three levels of privileges, administrator, custom, or desktop. Under Advance Settings you can control exactly what each user can access. I have not tried this as I am the only user my machine. This is what I would try if I wanted to do what you want to do.

Regards.
Regards.

---

### Post by Keypel on 2010-11-09
I didn't see anything in User privileges that would limit Internet access to  a user.

The closest thing I saw was 

"Connect to the Internet using a modem."

I tried that setting and did nothing to prevent said user for accessing the Internet. (All of my PC's and Laptops in the house are connected via router.)

I'm going out on a limb and guessing it has something to do with iptables??

---

### Post by chili555 on 2010-11-09
How about the setting just below it? Please see attached.

---

### Post by Keypel on 2010-11-09
> **chili555 said:**
> How about the setting just below it? Please see attached.

I just just tried that, didn't work either.

I changed the 2nd user account as suggested then I switched users (making sure not to log off on the 1st user account)

The 2nd user account still has Internet.

I want to make sure any programs running on the first user account has Internet and any programs running on the 2nd user account does not.

That way my kids can play there offline games on the 2nd while not interrupting any programs on the first.

I'm new to Ubuntu and still having a hard time figuring out how to secure a system.

---

### Post by chili555 on 2010-11-09
> I switched users (making sure not to log off on the 1st user account)Is that really how you'd use the feature? Wouldn't you log off completely and turn over the computer to SecondUser? Is the behavior changed if you do that? If you reboot and log in as SecondUser?

---

### Post by Keypel on 2010-11-09
> **chili555 said:**
> Is that really how you'd use the feature? Wouldn't you log off completely and turn over the computer to SecondUser? Is the behavior changed if you do that? If you reboot and log in as SecondUser?

Precisely,

That way my kids can play offline games on the 2nd account while not interrupting any programs accessing (downloading) Internet on the first.

I want to somehow edit the 2nd user account so that any network requests are blocked. How can I do this?

---

### Post by SeijiSensei on 2010-11-09
You could remove NetworkManager from the second account so that it can't start a connection to the network.  Other than that, if someone is logged into the machine, and the machine is connected to the Internet, there's nothing you can do to block them.

Now it would be possible to block web browsing if you had another computer between this one and your router that ran Squid in transparent proxy mode and required authentication to use the proxy.  Then other users wouldn't be able to browse the web without logging into the proxy.  But this is a very complicated solution.

Part of the problem is that an ordinary user's account has no privileges to rewrite the network connection.  For example, one approach might be to delete /etc/resolv.conf at login so DNS resolution wouldn't work.  Unfortunately an ordinary user can't do that; only the root user can.

If you're using wifi, then you could simply not let the restricted account open a KDE "wallet" or the equivalent in GNOME, and make sure your router requires a strong password.  Then it wouldn't be possible to log into the router and make a connection to the network.

---

### Post by Keypel on 2010-11-11
Any other suggestions?

---

