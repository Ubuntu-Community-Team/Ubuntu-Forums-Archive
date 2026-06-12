---
title: "XP Shared Docs?"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-06-19
I'd like to access the shared documents on an XP computer on the network. I know on windows you can start - run - \\PC Name Here and you'd see their shared docs. 

How can I do that from within Ubuntu?

---

### Post by swerdna on 2009-06-19
> **Roasted said:**
> I'd like to access the shared documents on an XP computer on the network. I know on windows you can start - run - \\PC Name Here and you'd see their shared docs. 

How can I do that from within Ubuntu?

Open a Gnome Terminal window and enter this: ```
sudo /etc/init.d/samba status
```If the return is "running" then Samba is installed and working. Then enter this to see the shares on the network:```
smbtree
```That should show you only one workgroup, some servers as icons and some shares if there are any.

For any of these shares you can write down the servername and the names of the shares

In Nautilus you can put in the address bar this address: ```
smb://servername/sharename
```
And you will see the contents

---

### Post by Roasted on 2009-06-19
Hm, I'm a little confused.

There's 3 XP computers on the network.

Curtdesktop
Tylerdesktop
Maindesktop

I see Maindesktop.
Tyler desktop is not listed.
Curtdesktop gave me this error under smbtree:

	\\CURTDESKTOP    		
cli_start_connection: failed to connect to CURTDESKTOP<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME


Any idea why?

---

### Post by swerdna on 2009-06-19
At some point \\curtdesktop was on the network, perhaps information conveyed from a browse master on the LAN, but the Linux box can't see it. Looks like poor name resolution. Are the Samba daemons nmb and smb running (you performed that test what did you get)?. Maybe it's that.

Also/otherwise, maybe your name resolution in the [global] stanza of the Samba config file is not configured. Run smb.conf through a diagnostic tool with this command in a terminal:```
testparm /etc/samba/smb.conf
``` and copy/paste the results back here. We'll see how it's configured from that.

---

