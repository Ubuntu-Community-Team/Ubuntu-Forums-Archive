---
title: "Access our minecraft server via ssh?"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by avatarmonkeykirby on 2011-09-21
Hey forums,

Here's our setup. We have an ubuntu natty server running in the other room with a static ip so we can access it via SSH just fine. We have our minecraft program running, it is running in the terminal on the actual server. So how can I access this program and give it commands as if I where at the actual computer?

So to re-iterate (in slightly clearer words): how do I access a running command line program on Ubuntu server via ssh?

Thanks you guys =)

---

### Post by daraeman on 2011-09-23
This would probably be better served on the minecraft forums, but you're probably looking for a setup like this
[http://shiftycow.net/running-minecraft-headless-on-linux/]("http://shiftycow.net/running-minecraft-headless-on-linux/")

Otherwise you could look into using Minecraft RemoteToolkit.
Also if you wanted a web interface I would also use [craftbukkit]("http://bukkit.org/") for the server and then use a web panel plugin like [MilkAdmin]("http://forums.bukkit.org/threads/admn-info-web-milkadmin-v1-4-08-04-administration-backup-server-data-whitelist-banlist-1060.17249/").

---

### Post by i.r.id10t on 2011-09-23
Kill the program on the server, run screen (install it if needed), re-start the minecraft server, disconnect from your screen session, and log out.  Log back in (local  or via ssh doesn't matter), reconnect to your running screen session.

---

