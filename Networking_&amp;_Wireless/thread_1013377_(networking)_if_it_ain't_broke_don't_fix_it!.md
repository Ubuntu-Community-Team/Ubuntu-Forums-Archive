---
title: "(networking) if it ain't broke don't fix it!"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by touchlikefire on 2008-12-16
I've been using ubuntu--nay, linux-- for years now, and I've NEVER had **wired ethernet** break.

I reformatted my hdds last night with a vanilla install of Intrepid and now whenever my pc resumes from sleep wired ethernet doesn't work.

Hardy, Gutsy, Feisty, Edgy, and Dapper never had a single problem with wired ethernet, and I'm pretty miffed about this, since I'm knee deep in a term project and can't really afford to reboot my PC.

"ifconfig" is showing no IPV4 address for  my nic, "sudo /etc/init.d/networking restart" and "force-reload" are worthless (no DHCP lease from the network), and "sudo dhclient" doesn't do anything either.

"vim /etc/network/interfaces":
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

So, I'm pretty stumped and would sure welcome any advice you may have.

---

### Post by touchlikefire on 2008-12-16
I pinpointed the issue to the **forcedeth** driver.  Following step 2 here: [http://ubuntuforums.org/showthread.php?t=967646&highlight=reload+forcedeth](http://ubuntuforums.org/showthread.php?t=967646&highlight=reload+forcedeth)
 is a work around for the issue.

Step 1 indicates this is a bug listed on launchpad.

---

