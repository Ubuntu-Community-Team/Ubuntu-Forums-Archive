---
title: "Macchanger pre-up script not working (9.04)"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by pterosky on 2009-06-07
I want to have randomly assigned IP address on boot up, and followed the instructions from [https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses](https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses). I put:

```
# Randomize the mac address for the given interface
/usr/bin/macchanger -a $IFACE
```

in the file /etc/network/if-pre-up.d/macchanger, but the script doesn't seem to be called, since I am still getting the same IP-address.

Does anyone know why, or maybe another way of activating macchanger during boot up?

I am trying to make this work in Ubuntu 9.04.

Thanks.

---

### Post by pterosky on 2009-06-12
It seems like nobody knows how to make it work, so I wrote the author of the instructions. I will post here if I get a reply.

---

### Post by pterosky on 2009-08-12
For some reason it now works. I only changed --another to -a

Open this file:
```
sudo gedit /etc/rc.local
```

and add:
```
ifconfig eth0 down
macchanger -a eth0
sleep 3
ifconfig eth0 up
```

So it looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig eth0 down
macchanger -a eth0
sleep 3
ifconfig eth0 up

exit 0
```

---

### Post by pterosky on 2010-04-09
After upgrading to 9.10 the above stopped working, so I tried the "official" way of doing it and it doesn't seem to work either...

I tried running ```
sudo ifconfig eth0 down
``` and noticed that it took a few seconds to execute, so I added another sleep command.

This seem to do the job:
```

sudo ifconfig eth0 down
sudo sleep 5
sudo macchanger -A eth0
sudo sleep 5
sudo ifconfig eth0 up

```

I also ran this command in a terminal. I am not sure if it's needed to ensure that rc.local is run at startup:
```
sudo chmod a+x /etc/rc.local
```

---

### Post by Stem84 on 2010-11-15
> I want to have randomly assigned IP address on boot up, and followed the instructions from [https://help.ubuntu.com/community/An...rkMACAddresses]("https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses"). I put:

    ```

# Randomize the mac address for the given interface
/usr/bin/macchanger -a $IFACE 
```in the file /etc/network/if-pre-up.d/macchanger, but the script  doesn't seem to be called, since I am still getting the same IP-address.
Does anyone know why, or maybe another way of activating macchanger during boot up?It Works, i have random M.A.C. every boot :). You have to change $IFACE with wlan0 or eth0 and make it executable:
```
sudo chmod +x /etc/network/if-pre-up.d/macchanger
```

---

### Post by Stem84 on 2010-11-28
ops.. it worked for me only at the first boot :confused:,anyway you can run macchanger _**before**_ NetworkManager with this workaround (bottom page):
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/336736](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/336736)

---

