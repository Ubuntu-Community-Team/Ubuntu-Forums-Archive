---
title: "accidentally modprobed the wrong driver"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by physics 1150 on 2009-10-01
hey everyone,

so today my atheros driver for some reason or another was acting up. (this happens from time to time, it will try to connect to my network and just give up after a while) 

So I did the following:
```
sudo ifconfig wlan0 down
sudo ifconfig pan0 down
sudo /etc/init.d/networking stop
sudo rmmod ath5k
sudo modprobe ath5k
sudo ifconfig wlan0 up
sudo ifconfig pan0 up
sudo /etc/init.d/networking restart 
sudo /etc/init.d/gdm restart
```

I think I accidentally modprobed ath5k and then modprobed ath9k. Now I can't start pan0 anymore, so I no longer have internet.

```
sudo ifconfig pan0 up
(something or rather)FLAGS: no such device
```

What should I do? I already unloaded the ath9k driver and reloaded the ath5k. What do I need to modprobe to get pan0 to launch?

Thanks! :)

---

### Post by renkinjutsu on 2009-10-01
is a good reboot really out of the question?

anyway.. ```
sudo lshw -c network
```

should give you all the information you need; such as:
logical name: (eth0 for me) but it says pan0 doesn't exist for you, so check `lshw` to see what it says.. also under `configuration:` it should tell you which module should be loaded, but i guess you already know

---

