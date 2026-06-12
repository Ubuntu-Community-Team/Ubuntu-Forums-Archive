---
title: "wpa_supplicant connection script"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by patapra on 2011-03-29
hi there,

ive been working on a shell script to connect to different networks i use, but am having some trouble. in particular, the wpa_supplicant command fails often with this error:
```

Restarting network
 * Reconfiguring network interfaces..
wpa_supplicant: wpa_action is managing ifup/ifdown state of wlan0
wpa_supplicant: execute `ifdown --force wlan0' to stop wpa_action
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
ssh stop/waiting
ssh start/running, process 3229
run-parts: /etc/network/if-up.d/wpasupplicant exited with return code 1
```here is the script:
```
#!/bin/bash

# files to be edited
ifaces_file=/etc/network/interfaces
wpa_file=/etc/wpa_supplicant.conf

cur_iface=`sudo head $ifaces_file -n 1 | sed 's/^.*:\ //'`
if [ $cur_iface == $1 ]; then
    echo New and current networks are equal.. restarting network and quitting script
    sudo /etc/init.d/networking restart
    exit
fi

case $cur_iface in
ethernet)
    # ethernet
    echo $ifaces_file :: Commenting ethernet block
    sudo sed -i.bak -e '12,13 s/^/#/' $ifaces_file
    echo $ifaces_file :: Done!
    echo $wpa_file:: No action needed
    ;;
leviathan)
    # leviathan
    echo $ifaces_file :: Commenting leviathan block
    sudo sed -i.bak -e '18,21 s/^/#/' $ifaces_file
    echo $ifaces_file :: Done!
    echo $wpa_file:: Commenting leviathan block
    sudo sed -i.bak -e '4,15 s/^/#/' $wpa_file
    echo $wpa_file:: Done!
    ;;
tamulink-wpa)
    # tamulink-wpa
    echo $ifaces_file :: Commenting tamulink-wpa block
    sudo sed -i.bak -e '26,33 s/^/#/' $ifaces_file
    echo $ifaces_file :: Done!
    echo $wpa_file:: Commenting leviathan block
    sudo sed -i.bak -e '21,35 s/^/#/' $wpa_file
    echo $wpa_file:: Done!
    ;;
esac

case $1 in
ethernet)
    echo $ifaces_file :: Uncommenting ethernet block
    sudo sed -i.bak -e '12,13 s/^#//' $ifaces_file
    echo $ifaces_file :: Done!
    echo $ifaces_file :: Updating current iface to ethernet
    sudo sed -i.bak 's/:\ .*$/:\ ethernet/' $ifaces_file
    echo $ifaces_file :: Done!
    echo $wpa_file:: No action needed
    echo Restarting network
    sudo /etc/init.d/networking restart
    echo Done!
    ;;
leviathan)
    echo $ifaces_file :: Uncommenting leviathan block
    sudo sed -i.bak -e '18,21 s/^#//' $ifaces_file
    echo $ifaces_file :: Done!
    echo $ifaces_file :: Updating current iface to leviathan
    sudo sed -i.bak 's/:\ .*$/:\ leviathan/' $ifaces_file
    echo $ifaces_file :: Done!
    echo $wpa_file:: Uncommenting leviathan block
    sudo sed -i.bak -e '4,15 s/^#//' $wpa_file
    echo $wpa_file:: Done!
    sudo rm /var/run/wpa_supplicant/
    echo Deleted /var/run/wpa_supplicant/
    echo Restarting network
    sudo /etc/init.d/networking restart
    echo Done!
    ;;
tamulink-wpa) 
    echo $ifaces_file :: Uncommenting tamulink-wpa block
    sudo sed -i.bak -e '26,33 s/^#//' $ifaces_file
    echo $ifaces_file :: Done!
    echo $ifaces_file :: Updating current iface to tamulink-wpa
    sudo sed -i.bak 's/:\ .*$/:\ tamulink-wpa/' $ifaces_file
    echo $ifaces_file :: Done!
    echo $wpa_file:: Uncommenting tamulink-wpa block
    sudo sed -i.bak -e '21,35 s/^#//' $wpa_file
    echo $wpa_file:: Done!
    sudo rm /var/run/wpa_supplicant/
    echo Deleted /var/run/wpa_supplicant/
    echo Restarting network
    sudo /etc/init.d/networking restart
    echo Done!
    echo Connecting..
    sudo wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
    echo Waiting 5 seconds to request ip..
    sleep 5
    echo Requesting address from dhcp
    sudo dhclient wlan0
    ;;
esac
```a little bit about the script: 

1) there is one arg passed in to the script. this arg is the name of the network i want to connect to. at the top of my /etc/network/interfaces file i have a commented line that states the currently configured network.

2) the first case statement comments out the lines associated with the currently configured network in /etc/network/interfaces and /etc/wpa_supplicant.conf (this works)

3) the second case statement uncomments line in those files according to the network i want to connect to. then, it deletes /var/run/wpa_supplicant (i used to get an error about this file already existing). then, runs the wpa_supplicant command, waits 5 seconds to make sure it connects, and calls the dhclient command

this is one of my first shell scripts, so if you see areas for improvement, please let me know! also, i'm most curious about the proper protocol for restarting the network. i'm assuming there are steps i'm not doing, especially in regards to wpa_supplicant.

please let me know what i can do to help you answer my question!

Thanks!

---

