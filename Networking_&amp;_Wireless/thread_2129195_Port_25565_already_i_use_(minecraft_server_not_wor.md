---
title: "Port 25565 already i use? (minecraft server not working)"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by EpicMinerBackup on 2013-03-25
OK I'm getting 

```
jeff@jeff-Inspiron-560:~/CraftBukkit$ '/home/jeff/CraftBukkit/CraftBukkit.sh' /home/jeff/CraftBukkit/CraftBukkit.sh: line 1: !/bin/sh: No such file or directory
229 recipes
27 achievements
12:17:56 [INFO] Starting minecraft server version 1.5
12:17:56 [INFO] Loading properties
12:17:56 [INFO] Default game type: SURVIVAL
12:17:56 [INFO] Generating keypair
12:17:57 [INFO] Starting Minecraft server on *:25565
12:17:57 [WARNING] **** FAILED TO BIND TO PORT!
12:17:57 [WARNING] The exception was: java.net.BindException: Address already in use
12:17:57 [WARNING] Perhaps a server is already running on that port?
>



```

when it try to run it on port 25565 and i dont want to use a different port please help


~ and sorry if this is the wrong place for this

---

### Post by sanderj on 2013-03-25
What's the output of:

netstat -aon | grep :25565

---

### Post by EpicMinerBackup on 2013-03-26
It doesn't do anything

---

