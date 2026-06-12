---
title: "Hostname not on network"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by stychman on 2006-06-30
I have 2 computers on my network.  One is XP Home the other is Ubuntu.  I have a separate partition on my HD of the Ubuntu box that is running as a samba server to share between my two machines.  Until recently I've had no problems.  Tonight I noticed that my XP machine can not find the partition on the Ubuntu machine.  I can ping the Ubuntu box from XP using the IP address but not the host name.  I also can not connect using NX any more using the host name.  If I replace it with the IP address it works fine.  Any ideas?

---

### Post by scxtt on 2006-06-30
just out of curiousity, do you have a router and use DHCP?

---

### Post by stychman on 2006-06-30
Yes I have a router and yes I do use DHCP and I should have mentioned that in my posting.

---

### Post by scxtt on 2006-06-30
are both boxes named in your DHCP Client Table? -- i'm not entirely sure, but it's possible XP gets hostname --> IP mappings from it ...

---

### Post by stychman on 2006-06-30
It does show up on my DHCP client table on my router.  It seems odd though that my XP machine is .100 and Ubuntu is .102.  Where did 101 go to?
If this helps at all if I do a Net lookup *computername* it comes back as 127.0.0.1

---

### Post by scxtt on 2006-06-30
i've seen that happen when boxes were rebooted when others weren't ... on my old network it was me [2 computers], my brother [1], and my dad [1] - all using DHCP, i rebooted every now and then but both my dad and bro would turn their boxes off nightly ... so things got kinda ugly for my server box after reboot ...

my advice would be to give static IPs a go ... but i'm not sure how XP caches them (probably still looking for .101 still) or what it's /etc/hosts equivalent is ...

[color=red]EDIT[/color]: check to see if you have a C:\windows\system32\drivers\etc\hosts file that you can put the static IP address into ...

---

### Post by stychman on 2006-07-01
Thanks.  I just added my ubuntu box to my host file on my XP machine.  I can now ping it and log into NX with the machine name instead of the IP.  Now to get my samba working

---

### Post by stychman on 2006-07-01
Just to let you know.  My samba was not running.  I did testparm and it showed that /var/run/samba does not exist.  Used aptitude to reinstall samba and it now works.  Thanks for your help on the networking issues last night!  I love this forum!

---

