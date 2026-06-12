---
title: "madwifi works sporadically...is it my card?"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by smTdust on 2009-02-18
Hey,

I'm running 8.04 on an embedded system with a mini-pci atheros card. I'm using the built in Madwifi drivers that come preinstalled with the distribution. 

Two strange be haviors:

1) ath0 either shows up on bootup or I have to restart/power-cycle until it does. Why would it work sometimes and not other times? Anyone experiece similar issues. Should I use other driver versions? bad card?

2) putting ath0 commands into /etc/network/interfaces seems to do nothing. The only way i can bring it up and assign it a static IP is by putting the following into the rc.local file:

wlanconfig ath0 destroy
wlanconfig ath0 create nounit wlandev wifi0 wlanmode ap

only then can I ifconfig eth0 192.168.1.x

wlanconfig seems like an outdated command, and I'm not too stoked about having to use it.

It is specifically step 2 above that either works, in which case ath0 comes up, or I get FAIL: ioctl device does not exist or something like that.

thanks

---

### Post by SMADdie86 on 2009-02-18
The build in atheros HAL drivers arent the best.
I would suggest to install NDIS wrapper and to use the windows drivers. After disabling the old hal driver under system hardware drivers.

Another way that works pretty good is installing a new and better madwifi hal 
[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz)

Disbale the atheros hal in system hardware drivers
reboot
unzip the tar
make
sudo make install
sudo modprobe ath_pci
sudo reboot

and voila.

HAd some big issues with atheros wifi before so may the force be with you

ciao

---

### Post by binbash on 2009-02-18
madwifi.org is moved to madwifi-project.org

---

### Post by SMADdie86 on 2009-02-18
he he sorry,
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz)

the latest version

---

### Post by smTdust on 2009-02-18
Any particular reason to go for r3879 instead of r3942?

Also, do I have to use the hal drivers on 8.04. I'm not even sure what the ath5k stuff is or if it would even work.

thanks

---

### Post by Ketara on 2009-02-18
The madwifi driver won't work unless you disable the HAL driver in system->administration->hardware drivers.

Are you sure you know which Atheros chipset you have though? If the HAL driver works out of box for you then it's not the 5x or 9x series, which is what gives people the most trouble.

If you're not sure which card you have, post the output of

lspci

in terminal and we can tell you.

---

