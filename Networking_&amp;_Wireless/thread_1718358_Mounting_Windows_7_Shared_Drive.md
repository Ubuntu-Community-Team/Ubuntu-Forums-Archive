---
title: "Mounting Windows 7 Shared Drive"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by BravoMikeZero on 2011-03-31
I have a HTPC running Windows 7 and I have an OpenPeak OpenFrame device running Ubuntu Netbook which I am trying to use to access the media on the shared drives on the HTPC.

There are 2 drives on the HTPC named Ex-HD1 and Ex-HD2, they are both 1TB drives. 

When I run the command

```
mount -t cifs -o guest,uid=user_name,gid=users //192.168.1.10/ExHD-1 /media/ExHD-1
```

It works without any issues. 

But when I run

```
mount -t cifs -o guest,uid=user_name,gid=users //192.168.1.10/ExHD-2 /media/ExHD-2
```

I get the error message

```
mount error(12): Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

I tried some of the fixes found around the web such as 

Setting “HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management\LargeSystemCache” to “1&#8243; on the Windows 7 PC

And also setting "HKLM\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\Size” to “3&#8243;.

And finally setting "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanmanServer
\Parameters\IRPStackSize" to 18.

I also tried the fix found [here]("http://ubuntuforums.org/showthread.php?t=1439495") with no change.

Any ideas?

---

