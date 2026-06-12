---
title: "can't access shares on a windows laptop"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by ahrimen on 2011-09-10
I have no problems getting to my shares on my ubuntu machine from the windows one, but I have not found any article on these forums, or anywhere that have been able to help.

The windows machine is set up to have sharing enable and I've followed all the steps in (for cifs, single user):
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

after setting up with the above tutorial when this command is used
```

sudo mount /mnt/winshare

```

the computer just hangs and after a while it will give error
```

mount error(110): Connection timed out

```

Also using the command 
```

findsmb

```

does not return a list that shows the windows machine.

This is very frustrating, been messing with this for a couple days now and would really appreciate help.

---

### Post by 2F4U on 2011-09-10
Is there a firewall on the Windows machine that may prevent the connection?

---

### Post by ahrimen on 2011-09-10
there is but I disabled it just to see if it was blocking me, and it the machine still would not show up when I used findsmb.

---

