---
title: "Mythbuntu 9.04 Alternate CD?"
date: 2009-04-25
forum: Mythbuntu
---

### Post by paisley_aus on 2009-04-25
Hi there,

I would like to install MythBuntu on to a linux RAID partition (created using mdadm).

Is there a MythBuntu alternate CD?

---

### Post by paisley_aus on 2009-04-25
It seems my question is answered here:

[http://www.mythbuntu.org/9.04/Release_notes]("http://www.mythbuntu.org/9.04/Release_notes")

*Note: alternate disks are no longer being made. They had a very low take rate, and we feel it's better to focus our attention on desktop disks.*


So how would I install Mythbuntu on a RAID system?

---

### Post by cat5 on 2009-04-26
I used the Alternate CD myself, then after it was complete, do the following:

```
apt-get install mythbuntu-desktop
```

I will download whats needed to finish off.

---

### Post by normdugas on 2009-04-26
It's a shame they are no longer producing the alternate CDs.  That said, what would be the best way to share the downloaded packages between my front and backends?  I've looked in the forums and nothing jumps out.  I'd  I'm thinking maybe NFS sharing /var/cache/apt or /var/cache/apt/archives.  This way, I'm only hitting the repository once instead of twice (or 3 or 4 times with my kubuntu boxes but with myth frontends installed)

---

### Post by superm1 on 2009-04-26
RAID is less important with storage groups, but the other alternative is

1) Install on one hard drive that will be just the OS
2) After install, set up another few drives with mdadm to mount at /var/lib/mythtv

---

### Post by superm1 on 2009-04-26
> **normdugas said:**
> It's a shame they are no longer producing the alternate CDs.  

At some point the LVM and RAID support will enter the desktop disks.  That's the only benefit that really came from alternates.  Otherwise, the systems set up by alternates was not nearly as feature complete as the system set up by a desktop disk.

You can always use lvm or mdadm after the system is installed too.
> That said, what would be the best way to share the downloaded packages between my front and backends?  I've looked in the forums and nothing jumps out.  I'd  I'm thinking maybe NFS sharing /var/cache/apt or /var/cache/apt/archives.  This way, I'm only hitting the repository once instead of twice (or 3 or 4 times with my kubuntu boxes but with myth frontends installed)

apt-cacher-ng or squid likely.

---

### Post by normdugas on 2009-04-27
> **superm1 said:**
> 
apt-cacher-ng or squid likely.

Thanks.  I'll check out apt-cacher-ng.  I've got a total of 5 various ubuntu boxes (3 mythbuntu and 2 kubuntu).  Hope I can cache all easily.

---

### Post by tgm4883 on 2009-04-27
> **normdugas said:**
> Thanks.  I'll check out apt-cacher-ng.  I've got a total of 5 various ubuntu boxes (3 mythbuntu and 2 kubuntu).  Hope I can cache all easily.

definitly apt-cacher-ng, works great for my network and should for yours too.

---

