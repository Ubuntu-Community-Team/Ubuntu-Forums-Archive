---
title: "Ethernet not recognized by Server 12.04"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by skunk.grunt on 2012-10-27
My onboard ethernet isn't detected after a re-install of Server 12.04. For reasons I won't get into here, I had to put the server's drive into another machine to install Ubuntu, then swap back into the server.

So the server starts up fine, except for the "Waiting for network configuration".

I read in another article that Server, by default, doesn't handle new mac addresses for hardware changes dynamically, unlike Ubuntu Desktop, but a look at /etc/udev/rules.d/70-persistent-net.rules shows only one ethernet interface. Shouldn't it show both the old, and the new?

lspci -vv shows an ethernet interface, so what the heck is going on?

I should mention that the onboard LAN is enabled in the BIOS.

And I know this isn't important, but all this started when I changed some network configuration settings in webmin before the re-install. It couldn't download any updates, so I tinkered a little. Broke, it, installed FreeNAS, which worked, but I didn't like it, then went back to Ubuntu Server, and now I'm in this pickle.

Thanks for any advice!

---

### Post by skunk.grunt on 2012-10-27
Whoops, forgot to mention...
Booted into rescue mode, and was able to download, install, and access Ajenti, so I *know* the network works, it's just a matter of getting it to work when running in normal server mode...

---

