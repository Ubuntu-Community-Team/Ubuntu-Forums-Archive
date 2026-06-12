---
title: "Wireless connection on server with no GUI - terminal only"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by Gyurltrini on 2011-12-12
Hi!
I recently had to reinstall my server to 11.10 and I can not install a GUI / desktop on top of it (because the desktop files seem to corrupt the start up sequence & can not boot the server).

So, that being the case I have the server running in terminal mode only and I would like to enable my wireless ralink card to work with it, however I can't figure it out.

I did some research and I've already checked, the server can detect the card and the driver that is installed seems to be the correct one, but we can't figure out how to enable it, and we are not that proficient in using terminal, so can someone explain to us how to do this?

Edit: 
1. alternately is there a way to do this via webmin?
2. we did try using ndiswrapper, but also could not get that goin.

---

### Post by jonobr on 2011-12-12
Hello

Maybe my post [here]("http://ubuntuforums.org/showthread.php?t=1893196") can help

If the network has a password you may need to supply that in the sudo iwconfig wlan0 essid "mynetwork" command

---

### Post by Gyurltrini on 2011-12-15
ok thanks ... I tried the first command line and got nothing (I mean after entering my password, it just went straight to the next place where I have to enter a command line).

The second command line worked in as much as it provided the ESSID's for all the wireless connections it could detect

The third command line, like the first, brought up nothing.

The fourth command line ... nothing happened

However, I will note that when I do sudo ifconfig, it shows that it's detecting the wireless card, but no ip address or netmask, etc. is associated with it.

Edit: in my research, in the past I needed wireless tools to be installed, but for some reason it does not seem to be installed and I can't seem to find the package for it (using sudo aptitude)... however, I did notice some other wireless package tools which apparently can be installed but are unsupported. I don't know if this is affecting anything I'm trying or not.

---

### Post by jonobr on 2011-12-15
If you see the wlan0 in the ifconfig maybe try doing a dhcp renew to reacquire an IP address.

---

### Post by Gyurltrini on 2011-12-15
Ok thanks I will try that ... also wondering ... I also have a regular (wired) connection temporarily connected to the server (just to do updates, etc.) until I can get the wireless working ... could that be interfering with getting the wireless to work?

Btw. what's the command for dhcp renew? I just tried sudo dhcp renew and got "sudo: dhcp: command no found"

---

### Post by jonobr on 2011-12-15
No , The wired connected and working should not stop the wireless from requesting and using an IP address

For renewing you could use

```
sudo /etc/init.d/networking restart
```

compare ifconfig commands before and after

Cheers

Jonobr

---

### Post by Gyurltrini on 2011-12-15
ok I tried that and this is what I got:
> * running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
* reconfiguring network interfaces ...
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, eg. service smbd reload

Since the script you are attempting to invoke has been converted to a upstart job, you may also use the reload(8) utility eg. reload smbd RTNETLINK answers: file exists

Problem is I'm not really sure I understand what it's saying to do.

Never the less, "sudo ifconfig" brings up the following information on wlan (nothing's changed from before):

> wlan0 Link encap: Ethernet HWaddr: xx.xx.xx.xx.xx.xx
      UP BROADCAST MULTICAST MTU:1500 Metric: 1
      Rx packets: 0 errors:0 dropped:0 overruns:0 frame:0
      Tx packets: 0 errors:0 dropped:0 overruns:0 carrier:0
      collisions: 0 txqueuelen:1000
      Rx bytes:0 (0.0.B) Tx bytes:0 (0.0.B)

*as you can see, there are two lines missing (inet, broadcast, mask, inet6, and scope information)

---

### Post by jonobr on 2011-12-15
> Problem is I'm not really sure I understand what it's saying to do.

all it means is we are getting older and things change,


try 
```
sudo dhclient wlan0
```

---

### Post by nothingspecial on 2011-12-15
If you have a wired interface to install packages with, perhaps wicd-curses may work for you :)

---

### Post by Gyurltrini on 2011-12-15
ok, jonobr, I tried that and all that happened was the cursor went down to another line which is blank. It currently reads:
> me@myserver:~$sudo dhclient wlan0
[sudo] password for me:
_

*where the _ represents the cursor blinking at the beginning of blank line

nothingspecial, I did look into wicd, but I got the impression that you need a gui / desktop interface to run it ... I need something that does not require a desktop / gui.

---

