---
title: "Grant rights to change network to normal users?"
date: 2013-05-02
forum: Networking &amp; Wireless
---

### Post by Ashrael on 2013-05-02
Hi all,

I have been looking for awhile now for a sollution to this specific problem: My users (ubuntu 12.04) should be able to change network settings on their laptops, without typing the admin password (which they don have). Found many guides, but none specifically give me an answer to my problem, and many don work... I could go and study on this, but it would be so much easier if you already know how to do this :)

I DO NOT want them all to know the admin password, and I don want to get called out every day just to set a new network for them.

So, is there a way to just give them all rights to just the network settings?
[SIZE=6][B]
SOLVED! see my post below, it works...[/B][/SIZE]

thanks!

---

### Post by |{urse on 2013-05-02
[http://thenubbyadmin.com/2012/04/11/how-to-restrict-a-users-sudo-rights-to-only-specific-commands/](http://thenubbyadmin.com/2012/04/11/how-to-restrict-a-users-sudo-rights-to-only-specific-commands/) <-- this is probably what you're looking for

[COLOR=#110000]username [/COLOR][COLOR=#007800]ALL[/COLOR][COLOR=#110000]=[/COLOR][COLOR=#7A0874]**(**[/COLOR][COLOR=#110000]ALL[/COLOR][COLOR=#7A0874]**)**[/COLOR][COLOR=#110000] NOPASSWD: [/COLOR][COLOR=#000000]**/**[/COLOR][COLOR=#110000]usr[/COLOR][COLOR=#000000]**/**[/COLOR][COLOR=#110000]bin[/COLOR][COLOR=#000000]**/**[/COLOR]**[COLOR=#110000]network-manager[/COLOR]**

---

### Post by steeldriver on 2013-05-02
This may work for you (from a previous thread)

> **steeldriver said:**
> I've struggled with this several times in  the past, just made another attempt and there does seem to be at least  one workaround

1. If you just select one of the available networks from the nm-applet  list and try to connect to it, a non-privileged user will get a popup  saying "System policy prevents modification of networks for all users".  The only option is to 'Cancel'. This seems to be because the default for  any connection creation operation is 'Available for all users' which  implies write permission to the /etc/NetworkManager directory

2. Likewise if you select Edit connections --> Wireless --> Add,  the dialog box comes up with the 'Available to all users' box checked -  and greyed out! With this box checked, it is impossible for a  non-privileged user to save the new connection.

3. **The 'Available to all users' box only becomes editable after you type something into the SSID box** - you can then uncheck it and fill in the SSID and any Wireless Security tab / IPv4 / IPv6 details

4. You should then be able to go back and select the SSID from the list,  and it *should* connect - if not, make sure the 'Connect automatically'  box is checked and then try disabling and re-enabling wireless

I just tried this as an unprivileged user on my laptop running 12.04 and  it does seem to work - yes it's very confusing and ugly, even the  developers seem confused by it --> [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/964705](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/964705)

You will find another workaround on the web that involves modifying  the  network-manager polkit file - however I *think* that method allows   unprivileged users to modify *any* connection (not just to add their   own) and possibly allows them to see any stored wireless  passphrases.

---

### Post by Ashrael on 2013-05-02
Hi all, thanks for the replies.

@|{urse : Too dangerous...
@ Steeldriver : didn't work for me....

I found a really simple way to get where I want to be:

just edit: /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla

and change:

[Adding or changing system-wide NetworkManager connections]
Identity=unix-group:admin;unix-group:sudo
Action=org.freedesktop.NetworkManager.settings.modify.system
ResultActive=yes

to:

[Adding or changing system-wide NetworkManager connections]
Identity=unix-group:admin;unix-group:sudo**;unix-group:users**
Action=org.freedesktop.NetworkManager.settings.modify.system
ResultActive=yes

and in terminal do a:  adduser YOURUSERNAME users

Reboot and you're done...

---

