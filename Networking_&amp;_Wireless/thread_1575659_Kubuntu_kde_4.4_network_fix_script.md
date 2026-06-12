---
title: "Kubuntu kde 4.4 network fix script"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by kirkface8 on 2010-09-16
so basically its a common bug where the computer goes to sleep and when its turned on it fails to enable the network management
an easy fix is
```
sudo service network-manager stop

```then to move the config
```
sudo mv /var/lib/NetworkManager/NetworkManager.state /var/lib/NetworkManager/NetworkManager.moved

```then to renable the network management generating a new config file
```
sudo service network-manager start

```this becomes extremly annoying as it hapens to me on a daily basis
so i thought how could i put this into a script where it would work easily.
ive tried a shell script with each command after each but that does not work
any ideas on how to fix this or help with writting a script

---

