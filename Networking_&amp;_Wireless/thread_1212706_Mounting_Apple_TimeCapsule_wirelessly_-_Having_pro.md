---
title: "Mounting Apple TimeCapsule wirelessly - Having problems ;F"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by jvainio on 2009-07-14
I am trying to mount an Apple Time Capsule (500Gb) to my Ubuntu laptop. I am running the latest release of ubuntu on a Dell Latitude D400 laptop.

What am I doing wrong on this mount command? Have no idea.

Which command should work? Or what commands should I input to fix this problem?

keko@keko-laptop:~$ sudo mount -t smbfs network://kekokapseli/Video/ /mnt/testi
[sudo] password for keko: 
mount: väärä tiedostojärjestelmän tyyppi, virheellinen valitsin, viallinen 
       superlohko laitteella network://kekokapseli/Video/, puuttuva koodisivu tai apuohjelma, tai muu virhe
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       Joissakin tapauksissa järjestelmälokista löytyy hyödyllistä
       tietoa - kokeile esim. komentoa &#8221;dmesg | tail&#8221;.

^^^ above says Wrong Filesystem Type, Error in the selection, erroneous superpartition on device..., missing code page or helper program, or some other error.

keko@keko-laptop:~$ dmesg | tail
[  207.200440] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  210.249181] wlan0: authenticate with AP 00:21:e9:ba:26:07
[  210.264292] wlan0: authenticated
[  210.264305] wlan0: associate with AP 00:21:e9:ba:26:07
[  210.271990] wlan0: RX AssocResp from 00:21:e9:ba:26:07 (capab=0x431 status=0 aid=1)
[  210.271998] wlan0: associated
[  210.273875] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  221.208261] wlan0: no IPv6 routers present
[  291.840150] smbfs is deprecated and will be removed from the 2.6.27 kernel. Please migrate to cifs
[  291.840162] smb_fill_super: missing data argument

keko@keko-laptop:~$ sudo mount -s -t cifs network://kekokapseli/Video/ /mnt/testi
mount: väärä tiedostojärjestelmän tyyppi, virheellinen valitsin, viallinen 
       superlohko laitteella network://kekokapseli/Video/, puuttuva koodisivu tai apuohjelma, tai muu virhe
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       Joissakin tapauksissa järjestelmälokista löytyy hyödyllistä
       tietoa - kokeile esim. komentoa &#8221;dmesg | tail&#8221;.

keko@keko-laptop:~$ dmesg | tail
[  210.264305] wlan0: associate with AP 00:21:e9:ba:26:07
[  210.271990] wlan0: RX AssocResp from 00:21:e9:ba:26:07 (capab=0x431 status=0 aid=1)
[  210.271998] wlan0: associated
[  210.273875] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  221.208261] wlan0: no IPv6 routers present
[  291.840150] smbfs is deprecated and will be removed from the 2.6.27 kernel. Please migrate to cifs
[  291.840162] smb_fill_super: missing data argument
[  513.373940] smbfs is deprecated and will be removed from the 2.6.27 kernel. Please migrate to cifs
[  513.373947] smb_fill_super: missing data argument
[  522.135463]  CIFS VFS: cifs_mount failed w/return code = -22


The harddrive contains about 170Gb of AVCHD video, and I've shot so much new stuff that I'd really need to access it fast, my girlfriend is all over me (not in good way) about this...

Also, is there a way to make this mounting automatic and how?

-J

PS: I've tried searching stuff about this, and tried a few stuffs but haven't been able to work it out.

---

