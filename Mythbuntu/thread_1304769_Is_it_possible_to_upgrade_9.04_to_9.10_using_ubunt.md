---
title: "Is it possible to upgrade 9.04 to 9.10 using ubuntu alternate disk?"
date: 2009-10-29
forum: Mythbuntu
---

### Post by dnuffer on 2009-10-29
I have 5 machines with mythbuntu 9.04 that I want to upgrade to 9.10. 
I can download the new bits using bittorrent in about 15-30 minutes. On the other hand, doing a network upgrade takes hours for each computer, and the whole process would take days. So I would prefer to upgrade using the alternate iso image. However since mythbuntu doesn't produce one now, I'm wondering if I could use the ubuntu alternate iso? Would the upgrade process still upgrade the mythbuntu specific packages over the network?

---

### Post by mrand on 2009-10-29
> **dnuffer said:**
> I have 5 machines with mythbuntu 9.04 that I want to upgrade to 9.10. 
I can download the new bits using bittorrent in about 15-30 minutes. On the other hand, doing a network upgrade takes hours for each computer, and the whole process would take days. So I would prefer to upgrade using the alternate iso image. However since mythbuntu doesn't produce one now, I'm wondering if I could use the ubuntu alternate iso? Would the upgrade process still upgrade the mythbuntu specific packages over the network?Howdy,

I believe there is at least one method of "offline" upgrading... google will be your friend.  One hit involved the words "Generate Package Download Script" and "Add Selected Packages".  There is also a method out there for using bittorrent.

Good luck,

[INDENT]Marc[/INDENT]

---

### Post by dnuffer on 2009-10-29
> **mrand said:**
> Howdy,

I believe there is at least one method of "offline" upgrading... google will be your friend.  One hit involved the words "Generate Package Download Script" and "Add Selected Packages".  There is also a method out there for using bittorrent.

Good luck,[INDENT]Marc[/INDENT]

Marc,
See [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading). The method of offline upgrading is to use the alternate iso image. However, mythbuntu has stopped producing the alternate iso image, so I'm hoping someone knows if using the ubuntu iso image would work.

---

### Post by Lindsay.Mathieson on 2009-10-29
I'm very interested in this as well for the same reason - also I'm very near my download cap :(

---

### Post by mrand on 2009-10-29
> **dnuffer said:**
> Marc,
See [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading). The method of offline upgrading is to use the alternate iso image. However, mythbuntu has stopped producing the alternate iso image, so I'm hoping someone knows if using the ubuntu iso image would work.Howdy again,

After a bit more looking around, I continue to suspect that there is a way to download the packages for an upgrade.  Here is a relatively recent thread about it: [http://ubuntuforums.org/showthread.php?t=1100816](http://ubuntuforums.org/showthread.php?t=1100816)

And as I mentioned, there is a way to update via bit torrent... search for apt-p2p.

<warning... wild guessing ahead> I suspect that you *could* use the standard alternate disk to do the upgrade.  Perhaps this would disable some packages (esp myth related) that aren't included in the alt disk if it runs into dependency issues, and you could re-enable them when it has access to the karmic repo after the main OS is finished upgrading via disk?</wild guessing>

If it were me, I'd probably just start it before going to bed (although make sure it gets to the downloading part before hitting the sack!).  But I have pretty fast internet and no cap (that I'm aware of).

Good luck,

[INDENT]Marc[/INDENT]

---

### Post by nickrout on 2009-10-29
there is no mythbuntu alternate cd for 9.10 > Note: alternate disks are no longer being made. They had a very low take rate, and we feel it's better to focus our attention on desktop disks. [http://mythbuntu.org/9.10/release](http://mythbuntu.org/9.10/release)

If you want to avoid multiple downloads doing  net upgrade, try apt-cacher-ng. Its cool, it caches the .deb downloads and every computer on your lan can get them locally rather than off the net.

---

### Post by Lindsay.Mathieson on 2009-10-30
Thanks mrand and nickrout, its good to know for sure. And generally useful links.

---

