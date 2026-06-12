---
title: "Meerkat Wireless WEP Issue"
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by cinnabubbles on 2012-10-08
Hi all. 

I'm hoping you could help a girl out.

I'm using a Dell Mini 12 with a Broadcom card.

I did a fresh install of Ubuntu 10.10 today, set up wireless with no problems. I went through Update Manager to update as it popped up. (not upgrade, just update packages and such.) It went off without a hitch and asked me to reboot (as there was a kernel update.)

I rebooted, it asked for my login keyring as usual.

Now I'm having a problem with the wireless not connecting at all. It asks for my WEP key, cycles through like it's going to connect and eventually doesn't. It will connect just fine to my neighbor's unsecured network. 

Did I do a huge D'OH! by allowing the distro to update itself?

*NOTE* I cannot change the WEP security as my nephew often visits with a Nintendo DS and he likes to play online.

Any help or directions to other threads with a fix would be greatly appreciated!

---

### Post by robtygart on 2012-10-08
Are you sure your using WEP and not WPA/WPA2? There should be other options for those.

---

### Post by cinnabubbles on 2012-10-08
> **robtygart said:**
> Are you sure your using WEP and not WPA/WPA2? There should be other options for those.

Yep using WEP affirmatively, because of the DS. DS systems don't have support for WPA.

And I'm the one who set up the router, so I'm sure on it's security. :)

---

### Post by varunendra on 2012-10-09
Hi cinnabubbles, welcome to the forums !

Are you sure you did a 'fresh' installation of **10.10** and got updates ? I'm asking because 10.10 has reached its [end-of-life on April 12.04]("http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/") , and thus I don't think you can get any updates from the official channels anymore.

Besides, if it is a fresh installation, I would suggest to replace it with a fresh installation of 12.04 to get the advantage of latest stable kernel and packages. If the hardware specs are a problem (minimum 1GB RAM is recommended for default Ubuntu), try Xubuntu or Lubuntu instead.

If, for some specific reason, you still want to use 10.10 anyway, then please run the following command (just copy-paste it in a terminal):
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
``` and post back the contents of the "netinfo.txt" file it creates in your home directory. It will give us a detailed info about your wireless settings.

---

