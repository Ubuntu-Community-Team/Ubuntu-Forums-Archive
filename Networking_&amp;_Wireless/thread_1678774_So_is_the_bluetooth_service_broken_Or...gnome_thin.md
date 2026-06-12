---
title: "So is the bluetooth service broken? Or...gnome thinks bluetooth is off."
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by chunky bacon! on 2011-01-30
[FONT=Georgia][SIZE=3]I posted a similar reply in another thread, but wanted to see if I could get some assistance. 

I will admit that after I post this, I'm probably going to sleep, and will check back in the morning.

I've tried quite a bit to get this fixed, but the very basic thing that gets me is this:

In the gnome bluetooth applet, if I click "preferences," I get "bluetooth is disabled."  If I click the giant button that gives you hope that bluetooth will be turned on, nothing happens.

This is a Dell Vostro V130, Ubuntu 10.04 preinstalled.  I made the mistake of turning bluetooth off once, and now nothing.

I have searched and queried, so here are some things I've tried:

1. sudo gedit /etc/bluetooth/main.conf  and changed "RememberPowered" to "false"
2. uninstalled and reinstalled everything to do with bluetooth
3. using blueman instead of gnome applet gets similar result.  It says bluetooth is turned off.  If you try to enable it, it says "connection timed out."

 sudo /etc/init.d/bluetooth status results with:

*bluetooth is running.

And that's the big rub, to me.  If "*bluetooth is running," then why the hell can the apps not see that?  That above all really, really bothers me.  

Is there some other config utility that will actually recognize that bluetooth is running?

Now, the other steps

4. sudo hciconfig:

    hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
    DOWN 
    RX bytes:0 acl:0 sco:0 events:0 errors:0
    TX bytes:24 acl:0 sco:0 commands:8 errors:0

That bd address sure looks problematic, but does that just mean there no bluetooth devices connected? I would then say "well, of course not," because I can't use any config tools to connect them.

sudo hciconfig hci0 reset yields:

"Can't init device hci0: Unknown error 132 (132)"

And, finally, lsusb yields:


Bus 002 Device 003: ID 0cf3:3002 Atheros Communications, Inc. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b234 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[/SIZE]


[/FONT]

---

### Post by chunky bacon! on 2011-01-31
[FONT=Georgia][SIZE=4]Also, sometimes sudo hciconfig hci0 reset yields:

Can't init device hci0: Connection timed out (110)[/SIZE][/FONT]

---

### Post by chunky bacon! on 2011-01-31
[FONT=Georgia][SIZE=3][editing out a non logical post that didn't help anybody]


[/SIZE][/FONT]

---

### Post by chunky bacon! on 2011-02-02
[FONT=Georgia][SIZE=3]OK, well, it turns out that of course a lot of my post was premature.
It still isn't working, but I have found out, I think, exactly what is wrong.

The key is the device by [/SIZE][/FONT][FONT=Georgia][SIZE=3]Atheros Communications, Inc, which is their AR3002.

This is the device, apparently, that Dell is putting into this Vostro V130.
Here is the sales pitch for the device:

[http://www.atheros.com/technology/technology.php?nav1=49&product=103](http://www.atheros.com/technology/technology.php?nav1=49&product=103)

Here is where it gets a bit strange.  On a separate page, Atheros indicates that:

> As a proponent of open software, Atheros provides its own Bluetooth  stack for easy portability and also ***supports standard Bluetooth stacks  such as Blue Z on Linux*,** Chrome OS, and Android OS. All Bluetooth  profiles in Blue Z are supported, including headset and hands-free  profiles, A2DP, FTP, DUN, OPP, PAN, SPP and PBAP.

OK, so they say this device should support Bluez.  Well, I wonder, does Bluez support it?  Note that there are no linux drivers anywhere to be found on Atheros's home page.

So I go to the [Bluez ]("http://www.bluez.org/")page, and search for "atheros," and you find this:

[http://www.bluez.org/l2cap-extended-features-on-2-6-36/](http://www.bluez.org/l2cap-extended-features-on-2-6-36/)

Very briefly, it says "Support for the Atheros AR300x chip."

I would hope that "3002" is part of "300x," but I'm not sure.  I went ahead and added the natty packages to my repository, so that I could effectively install the bluez 4.87 and related packages

[https://launchpad.net/ubuntu/+source/bluez/4.87-1ubuntu1/+buildjob/2235686](https://launchpad.net/ubuntu/+source/bluez/4.87-1ubuntu1/+buildjob/2235686)

Well, this ends a lot of errors.  Now, when I launch blueman, I get no connection errors, or anything, but still no options to connect any devices.

This still happens:

[/SIZE][/FONT][FONT=Georgia][SIZE=3] sudo hciconfig:

    hci0:    Type: BR/EDR  Bus: USB
    BD Address: **00:00:00:00:00:00**  ACL MTU: 0:0  SCO MTU: 0:0
    **DOWN **
    RX bytes:0 acl:0 sco:0 events:0 errors:0
    TX bytes:24 acl:0 sco:0 commands:8 errors:0

Which tells me that the AR3002 is still not "seen."

sudo hciconfig hci0 up yields:
**Can't init device hci0: Connection timed out (110)**

Now, in a very rational sense, I believe I have hit the dead end.  The device is simply too new, I guess, to be supported.  

Is the proper procedure to turn in a bug request to the ubuntu developers?  Or do I turn in a bug notice to the bluez developer?



[/SIZE][/FONT]

---

### Post by MountainX on 2011-02-25
> **chunky bacon! said:**
> [FONT=Georgia][SIZE=3]

Now, in a very rational sense, I believe I have hit the dead end.  The device is simply too new, I guess, to be supported.  

Is the proper procedure to turn in a bug request to the ubuntu developers?  Or do I turn in a bug notice to the bluez developer?

[/SIZE][/FONT]

I'm interested in knowing the solution to this...

---

### Post by chunky bacon! on 2011-03-01
> **MountainX said:**
> I'm interested in knowing the solution to this...

[FONT=Georgia][SIZE=3]
Sorry, I forget to come back and check my posts to see if there are replies.  Perhaps I should subscribe to my posts?

Anyway, bug is here:[/SIZE][/FONT] [FONT=Georgia][SIZE=3]

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/71486](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/71486)[/SIZE][/FONT]  [FONT=Georgia][SIZE=3]


Doesn't seem to be movement on it, so far.  But, hopefully this is a reference point for someone at some stage.[/SIZE][/FONT]

---

### Post by chunky bacon! on 2011-04-28
Allright, for any lost V130 owner's out there hoping for some help, I finally got a fix:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/comments/10](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/comments/10)

Follow AceLan Kao's steps in post 10 exactly, and the issue will get fixed.  At least, that's what did it for me.

---

### Post by joelseff on 2011-05-29
> **chunky bacon! said:**
> Allright, for any lost V130 owner's out there hoping for some help, I finally got a fix:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/comments/10](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/comments/10)

Follow AceLan Kao's steps in post 10 exactly, and the issue will get fixed.  At least, that's what did it for me.

Worked like a charm!!!!!


Joe

---

