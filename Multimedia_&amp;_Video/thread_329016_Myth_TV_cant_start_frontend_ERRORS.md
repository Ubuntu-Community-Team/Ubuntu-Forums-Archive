---
title: "Myth TV cant start frontend ERRORS"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by rubrboots on 2006-12-31
Hello I have followed the Ubuntu documentation for installing Mythtv Edgy Backenf Frontent Destop config. Everything has gone well until I attempt to start the front end with the command "mythfrontend" then I get the following error

```
boots@mythbox:~$ mythfrontend
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2006-12-31 10:30:11.209 Using runtime prefix = /usr
2006-12-31 10:30:11.225 Gnome-Screensaver support enabled
2006-12-31 10:30:11.229 DPMS is active.
2006-12-31 10:30:11.230 Unable to read configuration file mysql.txt
2006-12-31 10:30:11.230 Trying to create a basic mysql.txt file
2006-12-31 10:30:11.230 Could not open settings file /home/boots/.mythtv/mysql.txt for writing
2006-12-31 10:30:11.230 Failed to init MythContext, exiting.
boots@mythbox:~$ 

```

If I use "sudo mythfrontend" than it will start. Any ideas??

---

