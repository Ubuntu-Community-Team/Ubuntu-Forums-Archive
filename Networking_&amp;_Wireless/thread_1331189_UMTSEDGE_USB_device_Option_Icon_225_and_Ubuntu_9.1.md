---
title: "UMTS/EDGE USB device Option Icon 225 and Ubuntu 9.10 (karmic koala) patient group"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by phen on 2009-11-19
Dear all,

i am using an option UMTS/EDGE USB device from option. it is called iCon 225.

With Jaunty, you simply had to connect twice to get it working. Now with Karmic, it was working out of the box at the first try. Afterwards it stops working until I delete the connection in network-manager and reconfigure it. afterwards it works again for the first connect.

this is quite annoying. now, there is this website [http://www.pharscape.org](http://www.pharscape.org) , where you can find quite a lot of additional option drivers. I dont want to self-destruct my system by installing tools randomly.

what are your experiences? does anybody have the same problem, or maybe the solution?

t.i.a.and bye

---

### Post by gvoima on 2010-02-04
I know this comes a little bit too late, but..
I also have this same problem. Tried to update the firmware of the device, didn't help.
It works so good at the first try, but then stops working :(

Haven't found any solutions yet.

---

### Post by gvoima on 2010-02-04
Have you tried this?
[http://www.peck.org.uk/ozerocdoff.html]("http://www.peck.org.uk/ozerocdoff.html")

But I guess this is related to the NetworkManager rather than the device..

---

### Post by phen on 2010-02-04
Hello gvoima,

I found a solution in the meanwhile: set up a new connection, set the keyring to "accept once" and manually disconnect the UMTS Modem before shutdown or standby.

This way you should be able to use the connection without reconfiguring every time..

please tell me if this works for you!

---

### Post by gvoima on 2010-02-04
Yeah I always manually disconnect it before taking it off :)
Have to try the keyring solution.

But I'll try this in the meanwhile and report what happens [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by phen on 2010-02-04
try the keyring thing, because the modeswitch is working! dont mess up your system... you can see an authentication error appearing in syslog or dmesg (dont remember).

Somewhere i posted the problem, I try to find the exact error message..

---

### Post by phen on 2010-02-04
Here we go:


[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/488027](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/488027)


> Nov 24 21:18:23 schlepptop NetworkManager: <WARN> stage1_prepare_done(): GSM modem connection failed: Did not receive a reply. **Possible causes include:** the remote application did not send a reply, **the message bus security policy blocked the reply**, the reply timeout expired, or the network connection was broken.


hth

---

### Post by gvoima on 2010-02-14
Nice :)

I myself haven't had any luck with this matter, only works if I delete the connection and make a new one :/

---

### Post by Plumtreed on 2010-02-15
I have a similar problem with 9.10. Mobile Broadband works at first but then goes 'bad'. If I set it up again as a new install it seems to go well.

I have Crunchbang 9.04 in a dual boot situation and found that it works OK in that setup.

I assume you are using 9.10?

---

### Post by gvoima on 2010-02-15
> **Plumtreed said:**
> I assume you are using 9.10?

Yes, this is on my laptop that has 9.10 installed.

---

### Post by Plumtreed on 2010-02-16
I can't offer any support because my 'set-up' is now working in the way it should. Other than regular upgrading I haven't taken any remedial steps.

 I do connect after booting and prior to connecting I disconnect from any 'wireless'. However, I am not sure this has any effect.

---

### Post by gvoima on 2010-03-10
And I seem to have some luck to get it working correctly under the newest mainline kernel (2.6.33 atm.) or with default karmic kernel, by disabling the pin-code query from the used sim-card completely.

[edit]
so far it has found a network everytime and connected to it, when not using a pin-code..
[/edit]

---

