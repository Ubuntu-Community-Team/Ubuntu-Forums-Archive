---
title: "Switch between hosts file based on connection"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by cagliano on 2009-12-28
Hi,
I am using Ubuntu 9.10 on my laptop and I am fully satisfied with it. there is only a minor issue that I'd like to iron out.

I use my pc both at work and at home.
I'd like to use a specific hosts file when I am @work and another one when I am at home ( I need to point towards the private ip's for our servers, where as from home, I just need to point to th regular DNS addresses )

I have two different hosts files and I know I can have these files used with a command like this.

```
sudo cp -f /etc/hosts-config2 /etc/hosts
```


The point is: I'd like to run a script with a command like this when the pc connects to a home network. How can I do?

eg: 
/etc/hosts-config2 = "home" hosts file
/etc/hosts-config1 = "work" hosts file

"work_wireless" = name of the work internet connection ( on network manager )
"home_wireless" = name of the home internet connection  ( on network manager )

 So, when the Network manager connects to "home_wireless" it also has to run 
 sudo cp -f /etc/hosts-config2 /etc/hosts.
when it connects to "work_wireless" it also has to run 
sudo cp -f /etc/hosts-config1 /etc/hosts


I hope my question is clear, let me know if it isn't.

thanks

---

### Post by bryonak on 2009-12-28
The WICD Network Manager is capable of doing exactly what you want. You can install it via Synaptic (or the Software Center).
Beware that since it does the same as the default Network Manager, this will uninstall the latter.
You can always swap back by installing the network-manager-gnome package.

With WICD, you can use different pre/post connection scripts for different wireless and wired networks.

In case you want to keep the default Network Manager, there is the option of putting scripts directly in the /etc/network/if-* folders... though I have little experience with those because I'm happily using WICD ;)

---

### Post by cagliano on 2009-12-28
Thanks, I'll give wicd a try

bye!

---

### Post by pi_31415926535898 on 2010-02-16
> **cagliano said:**
> Hi,
I am using Ubuntu 9.10 on my laptop and I am fully satisfied with it. there is only a minor issue that I'd like to iron out.

I use my pc both at work and at home.
I'd like to use a specific hosts file when I am @work and another one when I am at home ( I need to point towards the private ip's for our servers, where as from home, I just need to point to th regular DNS addresses )

[...]

I hope my question is clear, let me know if it isn't.

thanks

Cagliano,

I've raised the same question, and seen others ask it as well, but the only solutions at present seem to be Wicd (which I don't especially like, for what are likely purely cosmetic reasons), as stated before. What troubles me, though, is that with Hardy, it was possible to specify connection-specific HOSTS information without bothering with either a script or with a special connection management package. It was only after upgrading to Jaunty (Intrepid was installed only long enough to be upgraded), and now to Karmic.

I don't pretend to know why, but this key, though seldom used feature has been evidently axed in more recent versions, for shame...

--
Stan

---

