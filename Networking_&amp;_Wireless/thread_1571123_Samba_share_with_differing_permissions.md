---
title: "Samba share with differing permissions"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by Another Monkey on 2010-09-09
&#65279;I&#8217;m an Ubuntu user in a Windows world and what I am trying achieve is read/write access for my MS domain account and read-only access for everyone else. In smb.conf I have this:
```
	map to guest = bad user
	usershare allow guests = yes
	username map = /etc/samba/smbusers
	security = user
;	guest ok = no
;	guest account = nobody

[RelayPoint]

    path = /home/amonkey/RelayPoint
    writeable = yes
    comment = Relay Point
    valid users = amonkey
```

I can access this fine with my MS domain account, what I can&#8217;t work out is how to give others read-only access to the same share.  I guess I could create a second share for the same folder with a different name and permissions, but that seems a bit clunky and I&#8217;d have to remember to pass on a different name to the one I am using.

I also tried using the Nautilus right-click &#8220;Sharing options&#8221; and then setting the folder permissions.  This works fine for giving others read-only access, but loses capitalisation of the share name and doesn&#8217;t seem to recognise my MS domain account as being valid.

Can anyone help me, please?  I've been searching for a while and can't seem to find the answer.

---

### Post by Another Monkey on 2010-09-09
I am such a tube.  The answer is so simple that I never thought of it.

Tell Samba to give everyone full access to the share.
Then set permissions on the folder to read/write for me and read-only for everyone else.

Works a treat!

---

