---
title: "nautilus still can't browse smb in 9.04"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by wincen on 2009-04-24
I just upgraded to 9.04 and I still cannot browse samba networks in ubuntu.
This is pretty sad... is anyone else having this problem?

Yes, I can still see smb shared if I use smbclient and I can still mount them; but it'd be nice if I could browse the network  again.  I think it's been since ubuntu 7.10 since I could last do that.

I know there was a post on how to fix it for 8.10 but it never worked for me and I think a few other posters as well.

any brilliant solutions out there?  please...

---

### Post by jimv on 2009-04-24
Hmmmm.  I had the same problem in 8.04...I couldn't see any shares in the Network browser, but I could access them by typing the full path to the share.

In 9.04 everything seems to be working perfect now.

Something to try though...uninstall avahi and see if that helps.

sudo apt-get remove avahi-daemon

Then reboot.

---

