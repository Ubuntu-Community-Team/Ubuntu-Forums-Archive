---
title: "Launch/disable vpn from command line"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by rmcd on 2010-02-23
I generally use NetworkManager (the applet in Karmic) for managing network connections, but I would like the ability to close a VPN connection from the command line. How do I do this? I have been searching and am quite surprised that there isn't (as far as I have been able to tell) a simple command.

If there is not in fact a simple command, can someone perhaps provide a link or resource that explains network manager and its relationship to other networking software such as wpa_supplicant?

Thanks!

---

### Post by Tweepy on 2010-02-23
Funny, was trying to do so an hour ago, in order to script it with proxydriver when I connect my lappy at school.
What I tried so far:
/usr/lib/network-manager-vpnc/nm-vpnc-auth-dialog -s org.freedesktop.NetworkManager.vpnc -u "UUID"
The UUID can be found by starting:
gconf-editor
then in "/system/networking/connection"
and find the one having a having a "vpn" folder and copy/paste the UUID
But... the command runs fine, but doent do anything like connection the VPNC
Good luck, we keep in touch

---

### Post by rmcd on 2010-02-23
Tweepy, thanks. Your suggestion doesn't work for me either. All it does is display my passwords on the command line!

This is strange that there is no simple way to start or stop vpn.

---

### Post by Julita on 2010-02-25
For coomand-line vpn,
poff NAME_OF_NETWORK

Since I don't use Network Manager (I establish the connection form commandline), I have no idea if this works for you.

EDIT: to start it, I type
pon NAME_OF_NETWORK

You should launch them as a root (my terminal is always under root) to avoid typing sudo each time, use
sudo su

---

### Post by rmcd on 2010-02-25
Julita, pon and poff may do VPN, but "man pon" says this is for PPP, with no reference to VPN. So I think you're right that this is independent from networkmanager.

---

### Post by Julita on 2010-02-25
In fact, VPN uses PPP, so it is relevant in this situation.

---

### Post by red_lego_man on 2010-08-20
Old post, I know, sorry, but I was looking for this, and I found the following, which sorted the issues everyone's having:

[http://ubuntuforums.org/showthread.php?t=800330]("http://ubuntuforums.org/showthread.php?t=800330")

---

### Post by jaraco on 2012-06-25
Looks like this is built into Ubuntu now (Precise is what I have) in a command called 'nmcli'.

---

### Post by sffvba[e0rt on 2012-06-25
> **jaraco said:**
> Looks like this is built into Ubuntu now (Precise is what I have) in a command called 'nmcli'.

Thanks for the info...

*Old thread **closed**.*


404

---

