---
title: "Trouble Connecting to Wireless"
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by OPaul on 2006-03-08
I'm having trouble connecting to my wireless network. I'm currently using NetworkManager, but I was having trouble without too. 

I can detect the network fine, it then comes up asking me to unlock keyring, I do so. But then I can't get past the "Attempting to join wireless network 'blabla'..." It hangs there for a few minutes and then asks me for the wireless key, so I give it the key this time. But it still hangs, then it just gets stuck in a loop of asking for the key. I've found the following two items in the log that I thought might pertain. 
```
localhost dhcdbd message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
```

```
localhost kernel [4295121.342000] ndiswrapper (hangcheck_proc:312): wlan0 is being reset
```

Eventually the wireless will get connected, but of course as soon as that happens the laptop locks up. Very rarely I can get connected without the laptop locking up.

---

### Post by thnogueira on 2006-03-08
What kind of encriptation are you using? If it's wpa,  you'll need wpasupplicant. Maybe wiki pages can help...
[wiki.ubuntu.com]("wiki.ubuntu.com")

---

### Post by OPaul on 2006-03-08
It's 128bit WEP.

---

### Post by OPaul on 2006-03-10
Looks like the problem is with NetworkManager. I killed all the services for it and I have no problem connecting to my wireless network.

I'm also seeing the following in the syslog
```
localhost NetworkManager nm_device_set_mode: assertion `(mode == NETWORK_MODE_INFRA) || (mode == NETWORK_MODE_ADHOC)' failed
```

Are there any other logs I can look at to see why Network Manager keeps getting stuck in a loop asking for the key?

---

### Post by Bionic_Beefpile on 2006-09-09
I have the same problem fairly often.  I usually don't try to enter the WEP key when asked, I simply cycle "Enable Networking" in the Network Manager applet until it decides to connect.  I don't know how to fix it, though.  Sure would be great if someone could lend a hand

---

