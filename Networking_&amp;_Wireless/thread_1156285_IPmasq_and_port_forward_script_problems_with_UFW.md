---
title: "IPmasq and port forward script problems with UFW"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by _UsUrPeR_ on 2009-05-11
Hey all. I would appreciate some suggestions pertaining to a UFW script I am trying to write to allow port forwarding and IPmasq. This particular script will be used for secure internal connections with diskless clients, so security is not a concern. My intentions were to turn on and permanently enable IPmasq and port forwarding across the board in one fell swoop. The problem I am running in to is: ufw starts itself completely locked down. I only want to use it for it's forwarding capabilities.

Here's the small bash script I have written up:

```
#!/bin/sh

#Changes  default forward to accept and creates a copy of the old config in it's original place
cd ~
sudo mv /etc/default/ufw ~/ufw.old
sudo chmod 777 ~/ufw.old
sed 's/DEFAULT_FORWARD_POLICY="DROP"/DEFAULT_FORWARD_POLICY="ACCEPT"/' ~/ufw.old > ~/ufw
sudo chmod 644 ~/ufw
sudo chown root:root ~/ufw
sudo mv ~/ufw /etc/default/ufw
sudo chmod 644 ~/ufw.old
sudo mv ~/ufw.old /etc/default/

#This should permanently allow ip forwarding
sudo mv /etc/ufw/sysctl.conf ~/sysctl.conf.old
sudo chmod 777 ~/sysctl.conf.old
sed 's/\#net\/ipv4\/ip_forward=1/net\/ipv4\/ip_forward=1/' ~/sysctl.conf.old > ~/sysctl.conf
sudo chmod 644 ~/sysctl.conf.old
sudo chmod 644 ~/sysctl.conf
sudo chown root:root ~/sysctl.conf
sudo mv ~/sysctl.conf /etc/ufw
sudo mv ~/sysctl.conf.old /etc/ufw

#this should open up firewall rules prior to starting the firewall
sudo mv /etc/ufw/before.rules ~/before.rules.old
sudo chmod 777 ~/before.rules.old
sed 's/COMMIT/\#/' ~/before.rules.old > ~/before.rules
echo "" >> ~/before.rules
echo "# nat Table rules" >> ~/before.rules
echo "*nat" >> ~/before.rules
echo ":POSTROUTING ACCEPT [0:0]" >> ~/before.rules
echo "" >> ~/before.rules
echo "# Forward traffic from eth1 through eth0." >> ~/before.rules
echo "-A POSTROUTING -j MASQUERADE" >> ~/before.rules
echo "" >> ~/before.rules
echo "# don't delete the 'COMMIT' line or these nat table rules won't be processed" >> ~/before.rules
echo "COMMIT" >> ~/before.rules
sudo chmod 644 ~/before.rules.old
sudo chmod 644 ~/before.rules
sudo chown root:root ~/before.rules
sudo mv ~/before.rules.old /etc/ufw/before.rules.old
sudo mv ~/before.rules /etc/ufw/before.rules


sudo ufw disable && sudo ufw enable
```

Thanks, guys

any help would be appreciated.

---

