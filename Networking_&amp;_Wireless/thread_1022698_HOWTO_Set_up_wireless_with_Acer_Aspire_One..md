---
title: "HOWTO: Set up wireless with Acer Aspire One."
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by Jakey_TheSnake on 2008-12-27
Download this wireless driver: [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz) 

Move it to your Documents folder and extract. 

Open up a Terminal (Applications > Accessories > Terminal)

Type:

```
cd /home/username/Documents/madwifi-hal-0.10.5.6-r3879-20081204
```

Press enter. Then type:

```
make
```

Will take a couple of minutes, wait until you get the correct prompt again. 

Then type:

```
sudo make install
```

Let it do it's stuff, then:

```
modprobe ath_pci
```

Restart laptop, then when you click your networks icon you should get that beautiful list of wireless networks to connect to. 

Hope this helps, 

- Jake.

---

### Post by f37u5g0d on 2009-01-01
Do you need to shut down the drivers shipped with ubuntu in preferences > hardware drivers?

Do you need to be on ubuntu 8.10?

---

### Post by Jakey_TheSnake on 2009-03-07
Don't need to disable anything in hardware drivers, haven't tried it on anything other than ubuntu 8.10. Other ubuntu ditros will probably work with it too, different linux distros will have different terminal commands though.

---

