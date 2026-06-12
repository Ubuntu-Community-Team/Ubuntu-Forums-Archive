---
title: "Samba no longer works in Jaunty"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by puffyzacd on 2009-05-20
I'm having some serious trouble getting samba to "just work" on my clean install of Jaunty. I'm using the same smb.conf that I've used in all previous versions of Ubuntu, with the correct domain name and everything...

My problem: using nautilus, I can't see any windows shares, and my windows machines can't see my Ubuntu machine. I can ping all the machines in the network using IP addresses or the host names. Curiously, I **can** use smbclient to list the shares on the windows machines, but no matter what I try I cannot get nautilus to display them.

I will happily provide any details or debug output. I'm really struggling with this and I would greatly appreciate any help!

---

### Post by coffeecat on 2009-05-20
I'll give you three forum links:

[http://ubuntuforums.org/showthread.php?t=1135842](http://ubuntuforums.org/showthread.php?t=1135842)

[http://ubuntuforums.org/showpost.php?p=7157868&postcount=12](http://ubuntuforums.org/showpost.php?p=7157868&postcount=12)

[http://ubuntuforums.org/showpost.php?p=7075850&postcount=4](http://ubuntuforums.org/showpost.php?p=7075850&postcount=4)

I've got Jaunty on 4 machines. One I had to do nothing except set up a share on it. Another I had to edit both nsswitch.conf according to link 3 **and** smb.conf according to post #24 of link 1. (Note - the nsswitch.conf edit in link 1 differs from link 3.) The other two, I can't honestly remember, I did so much fiddling - I think I undid those posted edits but even so I can now browse shares with them. :|

Whatever, sometimes the shares appear, sometimes they don't. Sometimes they appear some time after booting up. :-k

Anyway, try those links. One thing that does seem to help is to set up a share on the computer (even an empty shared folder) you want to browse from.

What always works for me, even when nothing appears in Places > Network, is 'smb://servername/sharename' in the address bar of Nautilus.

**Edit:** sorry, just noticed you're also having trouble seeing the Ubuntu shares in Windows. That was not an issue for me, so everything I posted was about seeing Windows (or my smb NAS) in Places > Network in Nautilus. The only other thing I can suggest is to check and then double-check your Windows firewall settings.

---

### Post by swerdna on 2009-05-20
> **puffyzacd said:**
> I'm having some serious trouble getting samba to "just work" on my clean install of Jaunty. I'm using the same smb.conf that I've used in all previous versions of Ubuntu, with the correct domain name and everything...

My problem: using nautilus, I can't see any windows shares, and my windows machines can't see my Ubuntu machine. I can ping all the machines in the network using IP addresses or the host names. Curiously, I **can** use smbclient to list the shares on the windows machines, but no matter what I try I cannot get nautilus to display them.

I will happily provide any details or debug output. I'm really struggling with this and I would greatly appreciate any help!

There's a bug in one of the versions of Nautilus which prevents display of shares. What version of Nautilus are you using? (look in Nautilus --> Help ---> About). Here's the bug reference at Gnome Bugzilla Bug #524485: [http://bugzilla.gnome.org/show_bug.cgi?id=524485](http://bugzilla.gnome.org/show_bug.cgi?id=524485)

That might stop viewing of windows from Linux but not Linux from windows.

The latter problem (Linux from windows) is most likely due to inadequate name resolution. We would need to see the contents of smb.conf to comment on that.

---

### Post by puffyzacd on 2009-05-20
Thanks for the responses. I actually solved the problem myself.

It seems I had erroneously entered 255.255.255.255 as my netmask. All the other computers were on 255.255.255.0, so I guess they couldn't talk to eachother? In any case, I'm marking this as solved.

Thanks again all.

---

