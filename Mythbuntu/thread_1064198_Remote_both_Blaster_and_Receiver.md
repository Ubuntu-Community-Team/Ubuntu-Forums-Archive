---
title: "Remote both Blaster and Receiver"
date: 2009-02-08
forum: Mythbuntu
---

### Post by mostr on 2009-02-08
I am installing mythbuntu for the firsttime on my main myth machine. I am coming from Fedora 6. I have used Fedora since 4 for my myth machine and had a successfull backend and front end.

I liked the looks of mythbuntu and thought I would give that a whirl. I have everything working except the two most critical pieces. The ir blaster and the remote receiver.

I am a little confused as to how to config the remotes. During installation I picked that my tuner device is a Bell Satellite and that I have a blaster on Com1. I have a Hauppauge PVR-350 as my tuner card, and I'm capturing video via SVideo. This part is working. I  need to setup the remote to receive on the I2C interface on the hauppauge card.

This is my master backend, and getting the remote to receive isn't that critical atm. I do however need to get the ir blaster working on Com1 to change channels on the satellite remote.

Am I missing a step or steps after picking the remote type in the myth control centre during configuration? Do I need lircrc files like I used to use on Fedora as well?

Thanks.

---

### Post by mostr on 2009-02-08
As a follow up to this, I have all the configs done except for the channel change script, and that is eluding me atm.

I have the blaster on COM1 and I haven't initialized the remote yet, but want to get the pvr to change channels on it's own before I start muching with the remote.

Thanks.

---

### Post by OffAxis on 2009-02-10
I haven't done an external channel changing system in a while (so I'm not much help), but have you read through the community docs for this?

[https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)

---

### Post by mostr on 2009-02-10
I've been thru that document and still can't seem to get the blaster working.

My issue is the blaster doesn't seem to be sending remote codes as I've looked at the blaster thru my digital camera and when I initiate the channel change script from a command line it doesn't seem to light up.

I have the dual-headed blaster from [www.irblaster.info](www.irblaster.info). I had it working well on Fedora when I used to use that. So I know the hardware works.

It is on COM1 and I have the .conf files edited. When I restart the lirc service I get [OK]'s on all lines.

A snippet of my /etc/lirc/hardware.conf file:

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Dish Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="dish/general.conf"
TRANSMITTER_LIRCD_ARGS=""

My /etc/modprobe.d/lirc-serial files contains:

#COM1 equivalent, /dev/ttyS0
options lirc_serial irq=4 io=0x3f8
#COM2 equivalent, /dev/ttyS1
#options lirc_serial irq=3 io=0x2f8


I can't seem to figure out what step I am missing to make this work.

Does anyone have any ideas? I have a Bell receiver which is like Dishnetwork. I think once I get the blaster to light up with testing, I should be good to go.

Thanks.

---

### Post by OffAxis on 2009-02-18
There was a bug in one of the lirc builds (.8.2) that caused serial blasters to not work; check your version number with

```
lircd -v 
```

and you have your blaster mapped to /dev/lirc1
Is it still this? (sometimes it changes)

---

### Post by azmyth on 2009-02-18
Post your /etc/serial.conf as you need to make sure that uart is set to none for COM1. Also, does your remote work and just not the IRB?

---

