---
title: "FireWire audio interface setup!"
date: 2007-11-22
forum: Multimedia Production
---

### Post by artrbinfo on 2007-11-22
Hi!
 I'm new to Ubuntu ( ubuntustudio ) and I'm using two Phonic Audio Interfaces ( firewire ). I'd like to know how can I set them up on ubuntu. I know that they don't support with driver for linux, but maybe there is some standert driver for firewire audio interfaces.
 Thanks

---

### Post by nalmeth on 2007-11-22
FFADO (known as FREEBOB in Ubuntu) supports firewire audio devices, but I don't know whether your device specifically is supported.

[http://www.ffado.org/?q=devicesupport/list&page=2](http://www.ffado.org/?q=devicesupport/list&page=2)
This page shows a couple Phonic Audio devices "reported to work", but then you didn't mention what model you have.

To get started, install the JACK audio server. open Applications -> Accessories -> Terminal

Run these commands:
```
sudo apt-get install jackd qjackctl
sudo adduser <username> disk (where username is YOUR username)
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'

```Reboot.

Open qjackctl (which is an interface to control JACK). Go into settings, and change the audio driver to FREEBOB. Check the realtime option, and try to start the device (after restarting qjackctl). 

Its possible your device is not supported, but if the above steps do not start your device, just post the errors you encounter.

---

