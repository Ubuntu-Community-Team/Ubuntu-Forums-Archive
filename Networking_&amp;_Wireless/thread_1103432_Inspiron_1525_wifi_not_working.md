---
title: "Inspiron 1525 wifi not working"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by mrsmuffin on 2009-03-22
Hi i am trying to fix the wifi on my dell inspiron 1525. The light is off and when i try to add a new network the ok button is greyed out and wont let me complete the form.

How do i go about getting the wifi to work?

I need to get this fixed very soon

Hope you can help

MrsMuffin

---

### Post by mrsmuffin on 2009-03-22
can anyone help?

---

### Post by MurrayW on 2009-03-24
Did you make sure the switch was up right beside the disc drive to enable the wireless card?

---

### Post by BillyPrefect on 2009-03-25
Try this

lshw -C network

if it says you have a broadcom wireless 43xx then try this string of commands 

rmmod b44
rmmod b43
rmmod ssb
modprobe wl
modprobe b43
modprobe b44
modprobe ssb

see if you have wireless after that stuff

---

### Post by MurrayW on 2009-03-25
I also have this exact laptop. What I did is I went system>administration>hardware drivers 

Activate the wireless driver.

---

### Post by mrsmuffin on 2009-03-25
Thankyou for helping :)

---

### Post by marano on 2009-06-15
Hi!
I have the same issue, but when i run the command (lshw -C network) it says my wireless card is UNCLAIMED.
How can i fix this?
Thanks!

---

### Post by sirlancelot on 2009-07-31
> **BillyPrefect said:**
> Try this

lshw -C network

if it says you have a broadcom wireless 43xx then try this string of commands 

rmmod b44
rmmod b43
rmmod ssb
modprobe wl
modprobe b43
modprobe b44
modprobe ssb

see if you have wireless after that stuff

Thanks! This worked perfectly on my Inspiron 1525. How do I get this to persist through restarts? Every time I restart the machine there is no wireless :(

---

### Post by emergingtechnologies on 2009-11-02
This solution will work if you can gain access to a DSL cable and God Bless you if you can't.

I just worked these following steps and after the hour I spent figuring out where to go, I was able to execute and solve the problem in about two minutes.  

These instructions are specific to getting the wireless on the DELL INSPIRON 1525 working with Ubuntu 9.10

You need to be temporarily wired to do these steps.

STEPS:


Use Synaptic Package Manager to INSTALL this package: b43-fwcutter.

When it asks you if you want it to do all the installation, click YES, or whatever is closest to affirmative.

BINGO.  That was it.  

I'm posting this with my wifi.  Awesome.

---

