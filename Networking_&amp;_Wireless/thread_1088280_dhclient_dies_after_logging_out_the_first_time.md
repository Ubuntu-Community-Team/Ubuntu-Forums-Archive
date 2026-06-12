---
title: "dhclient dies after logging out the first time"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by gid on 2009-03-05
Long time debian user here, but new to Ubuntu.  I recently bought a Dell Mini 9 and ended up doing an UMCP Intrepid install on it.  For the most part it works great, with a few hitches.  I have a wireless network setup with it.  I configured it using the NetworkManager applet that was installed by default.

I noticed on shutdown, after adding some cifs shares to in /etc/fstab, the shutdown sequence hangs with CIFS VFS errors, so I started digging, and apparently it's because the network is going down before the shares are unmounted.  This is a know problem with several work around, none of which are seemingly ideal for all situations.  I tried adding an /etc/init.d/mountcifs script that unmounts all cifs drives as K02umountcifs in rc0.d and rc6.d, but I'm still getting CIFS VFS errors.  I even downloaded a new network-manager deb that excludes itself from the sendsigs shutdown process so it will be stopped later in the boot sequence, all a no go.

So I started some testing by running a ping and finding out when the network dies.  Apparently, the first time I log out of X dhclient is dying.  So if I shutdown after logging in for the first time, dhclient dies immediately, and cifs drives are not umounted cleanly since the network is no longer available.  And if I select log out, then dhclient dies, but once I log in again, it's fine as expected.  But if I log out again after the first log out, dhclient survives and networking stays up.  Meaning if I start up my machine, log out, log back in, and THEN shutdown, cifs drives are umounted cleanly.  This is easily reproducible every time.  

Does anyone have any idea what in the heck this would be?  dhclient behavior should be consistent, and not die sometimes, but other times survive.  I'd like to hopefully get to the bottom of this so these cifs problems can be fixed once and for all.

bug about cifs timeout errors:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211631](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211631)

thread about umountcifs shutdown script:
[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

---

### Post by gid on 2009-03-06
Apparently this is because my wireless connection is not set as a "system setting".  If I click the system setting checkbox, it seemingly does nothing, and if I edit the wireless connection again, it is not remembered. 

But if I add a new wireless connection through the edit connections dialog, it remembers the system setting checkbox ( and even prompts for my password), but the connection doesn't work.  If I go in to edit this system connection manually, the "OK" button to save my preferences is greyed out, and my wep key is not remembered.

---

### Post by gid on 2009-03-10
I figured it out if anyone cares.  Apparently there's a bug in network-manager that prevents WEP encryption being used system wide.  This is fixed in jaunty but there's currently no backport fix for Intrepid.  The fix was to upgrade to WPA encryption.

---

