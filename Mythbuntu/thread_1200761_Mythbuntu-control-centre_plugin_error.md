---
title: "Mythbuntu-control-centre plugin error"
date: 2009-06-30
forum: Mythbuntu
---

### Post by mitchell2345 on 2009-06-30
Hi,

I have had this issue for sometime and was hoping a update would fix it.  not so.

when i load MCC i get the following error:
```
Exception in caputureState of plugin plugins

Disabling Plugin
```

Pushing close i get the MCC button on the right and no plugins or diskless button.

How can i fix this?  I have done some searching and found this link but it doesnt help:
[https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/329616](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/329616)

I see there is a permisions error on /etc/mythtv/mythweb-digest.
```
-rw-r----- 1 mythtv   www-data   49 2009-06-08 15:54 mythweb-digest
```

Do i need to change the permsissions?

Running weekly builds on 9..04 *fully updated)

thanks,
Mitchell

---

### Post by tgm4883 on 2009-06-30
> **mitchell2345 said:**
> Hi,

I have had this issue for sometime and was hoping a update would fix it.  not so.

when i load MCC i get the following error:
```
Exception in caputureState of plugin plugins

Disabling Plugin
```

Pushing close i get the MCC button on the right and no plugins or diskless button.

How can i fix this?  I have done some searching and found this link but it doesnt help:
[https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/329616](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/329616)

I see there is a permisions error on /etc/mythtv/mythweb-digest.
```
-rw-r----- 1 mythtv   www-data   49 2009-06-08 15:54 mythweb-digest
```

Do i need to change the permsissions?

Running weekly builds on 9..04 *fully updated)

thanks,
Mitchell

Are you also running -testing?

---

### Post by mitchell2345 on 2009-06-30
yes i am.  I did a dpkg-reconfigure mythbuntu-repos and disabled testing.  but how do i fix the issue now?

---

### Post by superm1 on 2009-07-01
It's a bug in the mcc on the -testing repo.  I'll push a new one to -testing (it's fixed in karmic)

---

### Post by superm1 on 2009-07-01
OK, fixed MCC and -common are on testing.  You should be able to re-activate testing and upgrade for jaunty.

---

### Post by mitchell2345 on 2009-07-01
ok that fixed it!

I am still not able to get vnc service working.  When i enable it the progress hangs at finishing package operations.

Also the diskless options are still greyed out.
[[IMG]http://img244.imageshack.us/img244/3020/mcc.th.png[/IMG]](http://img244.imageshack.us/i/mcc.png/)
~edit.  nvm VNC is working, i just manually close out of MCC and tried a connect.  

~Mitchell

---

