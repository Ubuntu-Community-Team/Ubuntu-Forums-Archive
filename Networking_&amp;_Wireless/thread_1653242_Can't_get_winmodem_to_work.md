---
title: "Can't get winmodem to work"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by Fibonacci on 2010-12-26
I'm trying to use the modem which came with my laptop to connect to the internet. Unfortunately it's a winmodem, like most.
The output of scanModem (attached) is not clear enough as to which driver should be used on this modem. I finally installed and configured sl-modem-daemon - but I still don't know which country should I specify, since Colombia (where I currently live) is not one of the available options.
It appears, nevertheless, that my system is talking to the modem. I can't connect to the internet, though, since I always get this message with either Gnome-PPP or WvDial:
```

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT019479472323
--> Waiting for carrier.
ATM1L3DT019479472323
NO CARRIER
--> No Carrier!  Trying again.

```
That happens **even after I've set Carrier Check = no** on wvdial.conf, so I'm stuck here.

Also: the exact same setup works under Windows XP, so I know there's nothing wrong with my hardware.

What else can I try?

Thanks in advance.

---

### Post by grahammechanical on 2010-12-27
Let me guess: 019479472323 is the telephone number of your ISP.

The message NO Carrier! means that you do not have a telephone connection. Do you have to go through a switchboard to get access to a phone line?

Regards

---

### Post by Fibonacci on 2010-12-27
> **grahammechanical said:**
> Let me guess: 019479472323 is the telephone number of your ISP.

Right.

> **grahammechanical said:**
> The message NO Carrier! means that you do not have a telephone connection.

And yet I do. As I said before:

> **Fibonacci said:**
> the exact same setup works under Windows XP

> **grahammechanical said:**
> Do you have to go through a switchboard to get access to a phone line?

Regards

No I don't.

---

### Post by Fibonacci on 2011-01-03
Update:

After rebooting, I get the following error message from both Gnome-PPP and WvDial:
```

--> Cannot open /dev/ttySL0: No such file or directory
--> Cannot open /dev/ttySL0: No such file or directory
--> Cannot open /dev/ttySL0: No such file or directory
```
Problem is, /dev/ttySL0 is there and world-writable.
OK, then, I'll try restarting slmodemd:
```

$ sudo slmodemd -c USA --alsa hw:0,6
error: locked memory limit too low:
error: need 8388608 bytes, have 65536 bytes
error: try 'ulimit -l 8192'
```
Oh well. Since sudo ulimit doesn't work, I need to start a root shell, THEN run the ulimit code suggested, THEN slmodemd -c USA --alsa hw:0,6, and THEN... nothing. I'm right back at the first post - no carrier.

What else can I do?

---

### Post by Wolf-Ekkehard on 2011-02-23
Fibonacci,

have you ever figured out how to solve this problem?  I am having the exact same problem - can't use slamr since I'm running amd64 and hence must use alsa.  The slmodemd command spits out
```
# slmodemd --alsa hw:0,0
error: mixer setup: Off-hook switch not found for card hw:0
SmartLink Soft Modem: version 2.9.11 Sep  6 2010 13:40:56
symbolic link `/dev/ttySL0' -> `/dev/pts/3' created.
modem `hw:0,0' created. TTY is `/dev/pts/3'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.
error: cannot set channels for playback: Invalid argument

``` messages when I try to use the modem with either efax or wvdial and the symptoms using wvdial are the same ones you are describing (no carrier).  I had the modem working on a different motherboard (32 bit) with slamr before I upgraded, and it worked just fine.

BTW running slmodemd involved the same hacking that you encountered, requiring a ulimit...

---

### Post by Fibonacci on 2011-02-23
This is what I was told on the linmodems list after trying several failed solution attempts:
> We do have cases like this.
The code base is quite old and has not been updated by Agere/LSI for years.

Consider investing in a Controller Chipset (hardware) modem, as
contrasted to a software modem

So I guess I'm out of luck.

---

### Post by Wolf-Ekkehard on 2011-02-23
I was just about to post, since I got a similar answer from one of the very helpful and very quickly responding linmodems.org guys:
"...the driver that you need is slamr which works well for 32 bit linux not 64 bit one :( (slmodemd + alsa) does not serve this modem, that is why you see the errors."

He also said that "...there have been no success reports for 64 bit versions of linux."

The linmodems.org answer was still very helpful since at least now I don't have to pull out my hair trying to figure out why I cannot get it to work.

With respect to using my modem under 64 bit Ubuntu or you using yours at all, however, you and I both are out of luck.

---

### Post by Fibonacci on 2011-02-24
Well, I had some hope since I'm running 32-bit Linux. Also I can't install a hardware modem on my laptop (for obvious reasons).
And apparently the code will not be updated, so I'm stuck with a useless (on GNU/Linux) modem.

---

### Post by withnail420 on 2011-02-24
Any way of using ndiswrapper to get round this? I'm not very experienced with it personally but I believe it could maybe let you use the windows driver.

I remember going through this years ago, in about 2004 and I eventually just got a hardware modem.

---

### Post by Wolf-Ekkehard on 2011-02-24
I too have been using ndiswrapper in the past on my laptop to get the wireless Ethernet working - it was a pain in the neck, and if there's no detailed HowTo somewhere out there, you may spend days trying to get it to work.

Fibonacci, a simpler option (depending on how much you think your time is worth) might be to go with an external modem, something like this [<External Modem Link>]("http://www.tmart.com/56K-Black-USB-Voice-Fax-Data-External-V90-V92-Modem_p97520.html?ref=nextag").  It is reasonably priced, but I haven't tried this and you may want to do more research to see whether the particular modem of your choice would work; but external modems are still out there, and they do also come with USB connection in case your laptop doesn't have a serial connector anymore. To install it see [<HowTo>]("http://ubuntuforums.org/archive/index.php/t-1091189.html") if it doesn't come up automagically.

---

### Post by Fibonacci on 2011-02-24
> **Wolf-Ekkehard said:**
> Fibonacci, a simpler option (depending on how much you think your time is worth) might be to go with an external modem, something like this [<External Modem Link>]("http://www.tmart.com/56K-Black-USB-Voice-Fax-Data-External-V90-V92-Modem_p97520.html?ref=nextag").  It is reasonably priced, but I haven't tried this and you may want to do more research to see whether the particular modem of your choice would work; but external modems are still out there, and they do also come with USB connection in case your laptop doesn't have a serial connector anymore. To install it see [<HowTo>]("http://ubuntuforums.org/archive/index.php/t-1091189.html") if it doesn't come up automagically.

I would have to test them on my laptop before buying. That means I can only buy it from my city, and so far I haven't found anything.
Still out of luck, until someone confirms that some external modem or other works out of the box on Ubuntu.

---

### Post by Mia1990 on 2011-02-25
Some of these modems need to be ran with sudo i don't think it's detecting your modem if your starting wvdial from the terminal try this command
> sudo wvdial

if your using gnome ppp change the command to start to
> gksu gnome-ppp

---

### Post by Fibonacci on 2011-02-25
> **Mia1990 said:**
> Some of these modems need to be ran with sudo i don't think it's detecting your modem if your starting wvdial from the terminal try this command

Well, you might be interested to know that I can hear the numbers being dialled when lifting a handset connected to the same line. It is in the middle of that response that I get the NO CARRIER error message.
I wonder how could the numbers be dialled if the modem wasn't detected, but I'll try your suggestion as soon as I have a phone line.

---

### Post by Fibonacci on 2011-02-26
> **Mia1990 said:**
> Some of these modems need to be ran with sudo i don't think it's detecting your modem if your starting wvdial from the terminal try this command


if your using gnome ppp change the command to start to

Tried it. Didn't make one bit of difference.

---

