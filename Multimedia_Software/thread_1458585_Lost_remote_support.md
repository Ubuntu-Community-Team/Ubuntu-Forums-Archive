---
title: "Lost remote support"
date: 2010-04-20
forum: Multimedia Software
---

### Post by FrankSvan on 2010-04-20
Hi Guys (and Girls)

I recently bought a dvb-c USB tuner to my mythbuntu 9.10 box.

This tuner, which btw is a sundtek home media dvb-c tuner causes my allready installed hauppauge remote to stop working.

The hauppauge card installed, is working great, but the problem is just the remote. 

Now - i have tried typing "irw" but nothing is happening. 

When restarting lirc i seems to be functioning properly, so right now i dont know where to look to find out what is wrong.

I have just reinstalled (stop laughing) my mythbuntu box without the dvb-c tuner, and the remote is working properly.

Do you know where i should start looking

My best regards

Frank

---

### Post by sundtek on 2010-04-20
This is a feature of the sundtek driver to automatically support the remote which comes with it.

In order to disable this feature you can delete the configuration files which are responsible for this:

sudo rm -rf /etc/udev/rules.d/80-remote-eeti.rules  /lib/udev/rules.d/80-remote-eeti.rules

The script which finally causes the modification:
/opt/bin/lirc.sh

for questions regarding the driver you can also use
[http://support.sundtek.de](http://support.sundtek.de) (the english section).

---

### Post by FrankSvan on 2010-04-20
Woooohoooooo!!! Great !!!!

(it works)

Regards

Frank

---

