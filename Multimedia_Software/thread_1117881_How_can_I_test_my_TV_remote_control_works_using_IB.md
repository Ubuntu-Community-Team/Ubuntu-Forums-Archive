---
title: "How can I test my TV remote control works using IBM T42 infrared port?"
date: 2009-04-06
forum: Multimedia Software
---

### Post by tedrogers on 2009-04-06
Hi all,

As the title suggests really, I have basic TV remote control that I need to test is actually transmitting IR signals like it should. 

I just want something that will print a verbose readout on the screen / terminal when an IR command is received at the IR port on the T42 laptop.

I've dabbled with LIRC and IRCP, but none of these seem to do what I want in a "SIMPLE" manner, or at least I can't work it out.

Also, the "Infrared Remote Control" application in the repo's doesn't seem to offer anything that might help me out.

I have a vague glimmer of hope in something called sersniff which claims to be a IR packet sniffer. Unfortunately I can't even get it compiled and installed from source, but I managed to find a DEB somewhere and used that. 

However, so far I've had no joy with it really.

Can anyone advise or provide any other options?

Thanks.

---

### Post by xc3RnbFO8P on 2009-04-06
You can try **irw** in Terminal and press the keys on the remote.

---

### Post by tedrogers on 2009-04-07
Hi there,

Couldn't find **irw** in the repositories, nor could I find it on the web. 

All I could find is these manual pages. Is this it?

[http://www.debian-doc.org/man/1/i/irw.html]("http://www.debian-doc.org/man/1/i/irw.html")

Is it part of **lirc**?

---

### Post by xc3RnbFO8P on 2009-04-07
> Is it part of lirc?
Yes it is.
> sudo apt-get install lirc

---

### Post by tedrogers on 2009-04-08
Okay, this is really testing me now. But I'm willing to learn which is was Linux is all about isn't it! :)

I thought the infrared port was **/dev/ttyS0** or **/dev/ttyS1**, but for some reason (maybe I'm wrong) **dmesg** doesn't show this anymore. I'm sure it used to. 

This is the last few lines of my **dmesg** output, I'm sure the **ppdev0** entries used to relate to **/dev/ttyS0** or **/dev/ttyS1**. Confused now :confused:

Also not sure why **ttyS1: LSR safety check engaged!** is showing there.

```
[  143.829823] ttyS1: LSR safety check engaged!
[  143.829842] type=1503 audit(1239194112.802:6): operation="capable" name="sys_admin" pid=6359 profile="/usr/sbin/cupsd"
[  144.920223] ppdev0: registered pardevice
[  144.968142] ppdev0: unregistered pardevice
[  146.095781] ppdev0: registered pardevice
[  146.144209] ppdev0: unregistered pardevice
[  147.387990] ppdev0: registered pardevice
[  147.436037] ppdev0: unregistered pardevice
```

Could this be because I installed **setserial** and run the following lines:

```
sudo setserial /dev/ttyS0 uart none
```

and...

```
sudo setserial /dev/ttyS1 uart none
```

Hope I haven't borked it up! Wouldn't know how to put it back if I have borked it.

Back to **irw** then, so when I run this, where **x** is either a **0** or **1**:

```
sudo irw /dev/ttyS**x**
```

I get this message returned:

```
connect: Connection refused
```

Sorry to burden you with this, but I'm stuck. If you can help it would be great.

Thanks.

---

### Post by xc3RnbFO8P on 2009-04-08
You can try **sudo dpkg-reconfigure lirc**
**dmesg | grep -1 lirc**

---

### Post by tedrogers on 2009-04-09
Did all of that but I have no idea what it did, if anything on my system!

Appreciate the effort though. Thanks.

---

