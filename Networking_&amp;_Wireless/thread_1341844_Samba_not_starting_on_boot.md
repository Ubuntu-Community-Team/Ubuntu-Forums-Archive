---
title: "Samba not starting on boot"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by Stian24 on 2009-11-30
Hello 

Samba is not starting as one of the process.
When I restart samba by using the command: sudo /etc/init.d/samba restart
(The outcome says that samba is not running). Smaba works just fine so I just want to get samba to start at boot. 

Output of command:
 * Stopping Samba daemons                                                  
 start-stop-daemon: warning: failed to kill 1319: No such process
                                                                         [ OK ]
 * Starting Samba daemons                                                [ OK ]

Hope some can help :)

Best Regard 
Stian

---

### Post by puppywhacker on 2009-11-30
I think the correct script for it is update-rc.d, but I never used it
```
sudo update-rc.d -f samba enable
```

in stead I do what the script will do, which is create a softlink in the runlevel 2 directory
```
sudo ln -s /etc/init.d/samba /etc/rc2.d/S70samba
```

The way this works is that during the boot up phase ubuntu will start up in runlevel 2. Scripts in the rc2.d directory starting with an 'S' will be started. in the order of the 2 digits (70) This means that samba will be started as one of the last service, long after the network comes up.

---

