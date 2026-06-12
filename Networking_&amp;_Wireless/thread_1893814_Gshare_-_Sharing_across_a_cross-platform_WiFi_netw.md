---
title: "Gshare - Sharing across a cross-platform WiFi network"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by Albury_Boy on 2011-12-11
Hi all

Has anyone had any success using the gshare or gnome-user-share applications to share files in 11.04??

It looks like it's supposed to integrate into the GUI, but after install, the option in 'Personal File Sharing Preferences' is still ghosted out, and the text 'This feature cannot be enabled because the required packages are not installed on your system.' is still displayed. 

I can't seem to find any docs for this, and the couple of threads on the forum are about three years old. From the comments in the Software Centre I can see that I'm not the only confused person here.

Any suggestions??

Thanks

---

### Post by Albury_Boy on 2011-12-11
> **Albury_Boy said:**
> Hi all

Has anyone had any success using the gshare or gnome-user-share applications to share files in 11.04??

It looks like it's supposed to integrate into the GUI, but after install, the option in 'Personal File Sharing Preferences' is still ghosted out, and the text 'This feature cannot be enabled because the required packages are not installed on your system.' is still displayed. 

I can't seem to find any docs for this, and the couple of threads on the forum are about three years old. From the comments in the Software Centre I can see that I'm not the only confused person here.

Any suggestions??

Thanks


Figured it out. It was a broken dependency that wasn't highlighted. I needed libapache2-mod-dnssd

---

