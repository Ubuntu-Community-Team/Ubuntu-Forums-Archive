---
title: "nm-applet icon missing from panel"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by frisket on 2011-07-02
In 11.04 on a Dell Latitude D610 laptop, there are two logins. User1 has sudo privs, User2 does not.

When either user logs in, network-manager picks up on whatever remembered wireless network is available, connects, and the nm icon shows in the panel.

If the other user logs in (via Switch User), the connection persists, but the nm icon does not show in the panel.

Under 11.04 it appears there is no way to put the nm icon back in the panel, even when the connection is set to "available to all users", and even when the user missing the icon is User1 (who has sudo privs).

If control is now switched back to the first user who logged in, the nm icon is still there, and the system is still connected, but if that user logs off (rather than clicking Switch User), the connection is dropped, and when the other user gives their password to resume their session, there is now neither connection nor an icon with which it can be re-established.

This would appear to be a bug, but is there a way to ***FORCE*** the nm icon to appear in the panel? The connection is already set to "available to all users", and doing a networking start does not do anything.

Under 11.04 it appears that there is no way to make any icon appear in the panel if it is not already there.

---

### Post by MaindotC on 2011-07-03
Please move this discussion to [http://ubuntuforums.org/showthread.php?t=1795451](http://ubuntuforums.org/showthread.php?t=1795451)

---

