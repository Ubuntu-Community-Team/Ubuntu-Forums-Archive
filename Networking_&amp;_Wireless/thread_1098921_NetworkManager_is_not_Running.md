---
title: "NetworkManager is not Running"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by justutkarsh on 2009-03-17
always when  i left click on NetworkManager applet
it says NetworkManager is not Running.

which was working fine before i installed blueman and anyremote

i have tried following
       1. apt-get remove network-manager   apt-get install network-manager
       2.open the file
         /etc/NetworkManager/nm-system-setting.conf
         and set
         manage=true
     

   This is the output when i try to run it from console
        

 root@UFC:~# NetworkManager --no-daemon
NetworkManager: <info>  starting...
NetworkManager: <WARN>  nm_dbus_manager_start_service(): Could not acquire the NetworkManager service.
  Message: 'Connection ":1.72" is not allowed to own the service "org.freedesktop.NetworkManager" due to security policies in the configuration file'
NetworkManager: <info>  disconnected by the system bus.
NetworkManager: <WARN>  main(): Failed to start the dbus manager.
root@UFC:~# 

i am a linux newbie but i don't think its a bug
any help would be appreciated

---

### Post by justutkarsh on 2009-03-18
solvled by removing blueman
it somehow tinkered with dbus settings

---

