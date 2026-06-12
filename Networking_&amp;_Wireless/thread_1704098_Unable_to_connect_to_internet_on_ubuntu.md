---
title: "Unable to connect to internet on ubuntu"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by Dormenyo on 2011-03-10
I use Hasee L141 notebook and ever since I installed ubuntu, my internet connection using both wire and wireless does not work but for the windows it works alright. I asked friends to help me but it yielded no result. Is there anything that I'm missing? I re-installed it several times but still had the same problems. Someone please help me. I even tried installing using the wubi.exe but still the same problem.

---

### Post by grahammechanical on 2011-03-10
We need more information. Do you see the network manager icon? Is there a red exclamation mark (!) on it?

When you right click the icon do you see a tick mark against the lines Enable Networking and Enable wireless?

When you left click the icon do you see any networks listed as available.

Go to System>Preferences>Network Connections. What do you see listed under the Wired tab and under the wireless tab? Select each connection and select Edit and write down the information and post it to this thread.

If you see auto eth0 and auto eth1 edit these connections and tick the boxes Connect automatically and Available to all users.

When you get a connection to the Internet by Wire (ethernet cable) go to System>Administration>Additional Drivers. And activate any drivers that are available for your machine.

I hope that some of this information helps you.

Regards.




What messages do you see as the desktop loads?

---

### Post by Dormenyo on 2011-03-10
Hi!
I see the network manager icon. When I right click, I see the "Enable Notifications" and "Enable Networking" all checked. 
I don't have the enable wireless.
When I left click I see "wired Network" and under it I see "disconnected" and under the "disconnected", I see "Available" in a disabled appearance form and under that, I see "Auto eth0" and VPN connections

Under the System>Preferences>Network Connections>wired, I only have Auto eht0, on the edit tab, I have the connect automatically already checked. 
Device MAC address: 00:03:0D:5F:82:69
Cloned MAC address: blank
MTU: automatic

For the wireless, it's totally blank. I think there is no wireless adapter in my laptop
Basically this are the info I could see here.
Very helpful...
:(

---

### Post by leeshaub on 2011-03-10
it the install ubuntu 10.10 ? I had the same thing but reinstalling for me worked.

---

### Post by leeshaub on 2011-03-10
did you check the sys logs?

---

### Post by Mr Pickles on 2011-03-10
can you open a Terminal by going to 'Applications' -> 'Accessories' -> 'Terminal' and then type the following:

ifconfig

and press enter. Please post the result of that.

Thanks

---

### Post by smurphy_it on 2011-03-10
While you are in the  terminal you can get some more info for us on the network card(s).

```
lspci | grep [Nn]etwork
```

Also, you should check your system log for errors relating to your network cards.

```
dmesg
```
or
```
cat /var/log/syslog
```
assuming of course that is where you syslog is... if no luck, do a cat /etc/syslog.conf to find out where it is writing your syslog too.

---

### Post by Dormenyo on 2011-03-10
This is what i had when I typed ifconfig in the terminal

eht0         Link encap:Ehternet HWaddr 00:03:0d:5f:82:69
        inet6 addr: fe80::203:dff:fe5f:8269/64 scope:Link
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        RX packets:0 errors: 0 dropped:0 overruns:0 frame:0
        TX packets:0 errors: 0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
        Interrupt:16 Base address: 0x2000

lo        Link encap:Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:108 errors:0 dropped:0 overruns:0 frame:0
        TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:8304 (8.3 KB) TX bytes:8304 (8.3 KB)

---

### Post by smurphy_it on 2011-03-10
eth0 is "up", but could be hitting issues.  I also don't see an IP address associated to it.

You could try the following command:

```
sudo dhclient eth0
```

---

### Post by Newuser9 on 2011-03-10
> **grahammechanical said:**
> We need more information. Do you see the network manager icon? Is there a red exclamation mark (!) on it?

When you right click the icon do you see a tick mark against the lines Enable Networking and Enable wireless?

When you left click the icon do you see any networks listed as available.

Go to System>Preferences>Network Connections. What do you see listed under the Wired tab and under the wireless tab? Select each connection and select Edit and write down the information and post it to this thread.

If you see auto eth0 and auto eth1 edit these connections and tick the boxes Connect automatically and Available to all users.

When you get a connection to the Internet by Wire (ethernet cable) go to System>Administration>Additional Drivers. And activate any drivers that are available for your machine.

I hope that some of this information helps you.

Regards.




What messages do you see as the desktop loads?

I see the network manager with a red exclamation mark, but my mouse isn't currently working I'm hoping that problem will be sorted by getting my internet working.. is there any way of doing what you said, but with keyboard short cuts??

Edit: I can get to the network thingo with short cuts, I just need help otherwise.

---

### Post by smurphy_it on 2011-03-11
Hmm, I think that depends on your window manager.  Trying Alt-F2, that should bring up a run dialogue.  Now you would type in the command there which normally brings up your terminal.  As i'm not sure what window manager and what not you are running, that might be a little difficult to guess.

With xfce, this is mine:
```
/usr/bin/xfce4-terminal
```

---

### Post by Dormenyo on 2011-03-14
Hi guys!
I'm on now. My network is now working but as to how it started, i just can't tell, I just connected this morning and it indicated that the network is connected. Thanks very much for the support...:D

---

### Post by Shobuz99 on 2011-07-04
Post deleted. New thread created
[http://ubuntuforums.org/showthread.php?p=11030462#post11030462](http://ubuntuforums.org/showthread.php?p=11030462#post11030462)

(Rick) Shobuz99

---

### Post by Newuser9 on 2011-07-06
I sorted mine by going back to the version just before the newest.

---

