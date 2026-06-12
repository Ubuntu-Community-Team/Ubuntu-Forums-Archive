---
title: "Problem with NFS after PXE  booting (Connection refused)"
date: 2008-09-11
forum: Mythbuntu
---

### Post by impossibilechecisiaquesto on 2008-09-11
Hi, i fixed my problem with pxe and tftp.

Now when i boot my client i load the startup logo and with ctrl+alt+f1 
i have many time
```
 Error: Connect: Connection refused
```
then i have 

```

mount:Mounting /rofs of /root/rofs failed: invalid argument
/init/init:14 cannot create /root/etc/resolvconf: Directory Nonexisten
/init/init:14 cannot create /root/etc/resolvconf: Directory Nonexisten
mount/ Mounting /root/dev on /dev/.static/dev failed : No such file or directory
mount/ Mounting /sys on /root/sys failed : No such file or directory
mount/ Mounting /proc on /root/proc : No such file or directory
Target filesystem doesn't have /sbin/init

```

My /etc/exports is

```

/home/massabuntu/MULTIMEDIA/  192.168.0.0/24(rw,no_subtree_check)
/opt/ltsp/ 192.168.0.0/24(rw,no_subtree_check)

/var/cache/mythbuntu-diskless/overlay/ 192.168.0.0/24(rw,no_root_squash,async,no_subtree_check)

```

I have two network cards, one connected on the web and have a esternal dhcp and my ip is 21.244.123.206 .
The other card is connected witch the switch where are connected the clients and i have a static ip 192.168.0.1.

I saw that mythbuntu auto configure my /etc/ltsp/dhcp.conf assuming my ip was 21.244.123.206 and i had to changed it manually in 192.168.0.1, so for the /etc/exports.

Maybe there's an incorrect setting in the client image. 

Can you help me?

Thanks, Martino.

EDIT: Fixed

---

### Post by anonymousdog on 2008-09-11
I had similar issues after some updates on the backend server running the diskless client support.  I don't know how much of this is necessary, but here's what I had to do to get it all working again (in the order I tried).
-- delete the overlay cache for the client...no joy
-- recreate the image...no joy
-- remove and reinstall the diskless client support...working diskless client!

Removal/reinstall of the diskless client support changed my NFS exports options a bit, but they look like yours do now.  Still, these operations seem like they'd have low danger of impacting anything else.  I just recommend backing up your dhcp.conf file if it has any customization (though it wasn't overwritten in my experience).

---

### Post by impossibilechecisiaquesto on 2008-09-11
Fixed , i had problem with the nbd configuration file.

---

### Post by laga on 2008-09-12
What was the problem with that configuration file? It shouldn't be needed at all.

---

### Post by impossibilechecisiaquesto on 2008-09-12
The File was /etc/nbd-server/config
 
Befare was blank, this is the good one

```


[generic]
# If you want to run everything as root rather than the nbd user, you
# may either say "root" in the two following lines, or remove them
# altogether. Do not remove the [generic] section, however.
	user = nbd
	group = nbd

# What follows are export definitions. You may create as much of them as
# you want, but the section header has to be unique.
[export]
	exportname = /opt/ltsp/images/i386.img
	port = 2000 
```

After changed the file obviously 

    sudo /etc/init.d/nbd-server restart

Hope may be helpful to someone.

---

### Post by laga on 2008-09-12
Odd. What do you have in /etc/inetd.conf? It should have been set up there.

---

### Post by thomsany on 2009-01-28
I had the same issue and your solution solved it for me!
Thanks so much and all the best.

Teo

---

