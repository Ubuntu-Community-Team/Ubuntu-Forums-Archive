---
title: "UFW and Network Manager misbehaving"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by movingover on 2009-01-16
I'm using UFW to manage my firewall and Network manager to automatically connect to a VPN. I have three small problems that really irk me, as I'm trying to run a headless setup:

1) UFW, despite running "sudo ufw enable" countless times, does not enable on boot. I have to run that command again before any connection can be made (it denies ALL ports until it enables)

2) The Network Manager does not automatically connect to the VPN, possible due to issue #1. When I manually click it to connect, it asks me for my password for the keyring, which I'd like to disable so it can automatically connect.

3) When I connect to the VPN, the UFW disables again! So I cannot connect till I run "sudo ufw enable" again.

I ran a search on both issues and the closest I found was a fixed bug for UFW a long time ago. What steps should I take to provide more information so I can get this working?

Thanks in advance! :P

---

### Post by movingover on 2009-01-20
Anyone have some ideas on this?

---

### Post by oscarmeyer51 on 2009-02-02
FYI I Posted this in reply to a related issue elsewhere.

FYI -- There is a thread in this forum titled "[SOLVED] Uncomplicated Firewall Configuration" originally posted by urban48.

It that post there is a ufw setting that appears to have solved my connection issue on reboots.

The command is:

sudo ufw allow from any to any

the ufw has to be enabled to run this, but on reboot, I did not have to disable/renable ufw. I am certain this creates a huge gaping security hole, so I am searching for tutorials on ufw.

Here are some I found via Google.

[http://www.tutorialhero.com/click-30...untu_hardy.php](http://www.tutorialhero.com/click-30...untu_hardy.php)

[http://www.ubuntu-unleashed.com/2008...antage-of.html](http://www.ubuntu-unleashed.com/2008...antage-of.html)

Also avoid any address from google gruppi or ivihbk0, they only lead to porn and have no informational value for this issue.


There is also some good information on securing/hardening your laptop/desktop/network at
[http://www.linuxplanet.com/linuxplan...orials/6620/1/](http://www.linuxplanet.com/linuxplan...orials/6620/1/)

Hope this is helpful.

---

### Post by movingover on 2009-02-02
Sorry, but none of those links were helpful! :(
All three point to essentially 404 errors.
It looks like the links got "...."'d and are now broken.

I will take a look at that thread in a minute, is this the one you meant?
[http://ubuntuforums.org/showthread.php?t=1017749](http://ubuntuforums.org/showthread.php?t=1017749)
EDIT: Looked at that thread & it's mostly about which ports to open for ufw, which doesn't really relate to my issue - that ufw doesn't properly start up.

---

### Post by movingover on 2009-02-23
Can anyone else help me on this?

---

