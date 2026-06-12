---
title: "Generic remote control config"
date: 2010-01-18
forum: Multimedia Software
---

### Post by sjvega on 2010-01-18
Hello, I've been trying to configure this generic remote that came with a TV tuner card (saa7134) a while ago but I haven't been able to do so.
 The thing is that the remote works, in fact some buttons are recognized properly... but some are not. I'm not using lirc!, from I have been reading there is support for generic remotes in the 2.6.31 kernel, besides, i can't configure lirc, it doesn't let me load the kernel modules to start up the daemon for the ir.
 So the question is, is there a config file for the button mapping of the native remote support in kernel 2.6.31?. Been searching it but couldn't find it.
Thanks in advace.
Sorry for the bad english.

---

### Post by sports.car.guy on 2010-01-18
More info would be good. There could be support in Lirc for your remote if the kernel is able to take events from it. Then setup of key bindings would be so much easier.

What is the manufacturer and model of your card?

---

### Post by sjvega on 2010-01-18
The card is an Encore ENLTV-FM

---

### Post by sports.car.guy on 2010-01-19
I just read something and it clicked..

**You need to have an lirc configuration file before the service can be started.**

Where you have none, of course the service will fail. You could try using the Mythbuntu Control Centre's Lirc config app to create a basic config that will get it up and running and you can tweak it from there.

As I said in my last post it should work with Lirc where the kernel generic interface is detecting it.

---

### Post by sjvega on 2010-01-19
Ok, I'll give it a one more go when I get home (at work right now). But the problem wasn't that the daemon claimed the configuration, it said that the modules in the kernel weren't load.

---

### Post by sports.car.guy on 2010-01-19
Are the modules even on the system then?

---

