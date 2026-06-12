---
title: "Mount SMB with Kerberos Workaround"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by Spenzer4Hire on 2009-07-05
Hi All,

I've been searching all day about mounting cifs using kerberos.  For some reason I've been getting "Operation not supported" when mounting with -o sec=krb5.  I found a workaround that works for me.  I haven't seen this method posted elsewhere so I figured I'd document it here.

Ubuntu 9.04 joined to domain using likewise-open5.  Had to remove mdns entry from nsswitch.conf for that to work.

Edited lssasd.conf to assume default domain name.

Added domain user to same groups as initial Ubuntu user.

At some point I installed smbfs.  I don't know if that is important for the following.

I noticed that in Nautilus when I went to Places>Network, browsed to the server, and double-clicked on the share I wanted that it didn't prompt for username and password.  Even though it didn't prompt I had the proper write permissions.  So I'm assuming that Nautilus is using kerberos to authenticate against the server.

Once you have browsed the share in Nautilus it shows up in the Places list.  It turns out that Nautilus is using Gnome-VFS (gvfs) to mount the share.  Some non-Gnome apps can't see these directories (Firefox is one of these).  When gvfs mounts the share it isn't mounted in the usual /media or /mnt directories.  It actually gets mounted in "<home directory>/.gvfs/<share name> on <server name>".  You can browse to this location with a non-gvfs-aware app and get to the mounted share.  To make things easier I made symbolic links to the folders I wanted in the root of my home directory.

The last step is getting this to mount on login.  The command line command to create the gvfs mount is:

```
gvfs-mount smb://<server name>/<share name>
```

(Don't forget, if you have spaces in the share name you have to escape them by preceding them with a "\".)

Go into System>Preferences>Startup Applications.  Add a new entry and use the command above.  Now the share will be mounted on login.  (If you aren't using Gnome you can still install gvfs and use the above command.)

I am using this on a single-user computer as a means of inter-operating with an established Windows domain.  This works for me.  I can imagine that a talented bash scripter could turn this into a very fancy/useful logon script that could work in a much larger environment.  If someone develops this idea more I would be very interested in hearing your progress.

-Spencer

---

### Post by dmizer on 2009-07-05
Somewhat more verbose howto is located here: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877) :)

---

### Post by Spenzer4Hire on 2009-07-05
So it is.  Don't know how I missed that one.

---

### Post by ChrisSnow on 2009-07-30
> **Spenzer4Hire said:**
> I am using this on a single-user computer as a means of inter-operating with an established Windows domain.  This works for me.  I can imagine that a talented bash scripter could turn this into a very fancy/useful logon script that could work in a much larger environment.  If someone develops this idea more I would be very interested in hearing your progress.

-Spencer

Thanks for your post. It gave me the idea to solve my problem. I've been trying to get every user logged in using likewise-open to mount a share of the same name as their username on a 2K3 file server in the same domain.

How to get the command ```
gvfs-mount smb://<server name>/$USERNAME
``` (which handles the mount of the same name as the username) to run when every user logs in?

Knowing that there are several apps that run at startup in Gnome in System>Preferences>Startup Applications as you pointed out, I figured that the default apps must be configured somewhere! After a bit of searching I found them in /etc/xdg/autostart.

I took a look at some of the existing files in that dir and made myself the following file called gvfs-mount.desktop

```

[Desktop Entry]
Type=Application
Name=Mount Windows Share
Exec=sh -c "exec /usr/lib/global_gvfs_mount.sh"
Icon=system-run
Comment=Mount the share of the same name as the username

```

Then I just created the file /usr/lib/global_gvfs_mount.sh which simply contains the following:

```

gvfs-mount smb://<server name>/$USERNAME

```

The only other thing to do was ```
chown root:root /usr/lib/global_gvfs_mount.sh
```

Works a treat for all AD users.

There are obvious drawbacks like this will fail for locally configured users but in my network that's not a problem! Also I understand that some apps can't access the gvfs mounted share. Will cross that bridge etc! Perhaps ln -s will help there?

Hope this helps!

---

