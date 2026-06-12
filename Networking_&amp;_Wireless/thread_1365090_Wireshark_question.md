---
title: "Wireshark question"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by Big_tone on 2009-12-26
I have Ubuntu 9.1 and just downloaded/installed Wireshark via synaptic. I am directly connected to the internet via cable.

When I got to setup my capture devices Wireshark doesn't recognize my ip address. Instead, I get this:
[IMG]http://i133.photobucket.com/albums/q57/tone_dog/wireshark_screenie.png[/IMG]

Anyone know why it does this and how to solve it?

---

### Post by adam814 on 2009-12-26
Are you connected to the internet over eth0?  (e.g. ifconfig eth0 gives you a valid IP address).  When you say directly connected via cable do you mean an ethernet cable directly to your modem or a USB cable directly to your modem or something entirely different?  If you are directly connected to the internet you'll most likely only be able to monitor your own internet traffic (which means you could probably use the pseudo-device for capturing on all interfaces in wireshark anyway).

---

### Post by zey on 2009-12-26
> **Big_tone said:**
> I have Ubuntu 9.1 and just downloaded/installed Wireshark via synaptic. I am directly connected to the internet via cable.

When I got to setup my capture devices Wireshark doesn't recognize my ip address. Instead, I get this:
[IMG]http://i133.photobucket.com/albums/q57/tone_dog/wireshark_screenie.png[/IMG]

Anyone know why it does this and how to solve it?


you must be be run it in normal user.
if you want wireshark working you should run it with root access.
run with this, open the terminal and type:
$ sudo wireshark

it must be solved your problem..



[http://z-computer-z.blogspot.com]("http://z-computer-z.blogspot.com/")[URL="http://ubuntuforums.org/z-computer-z.blogspot.com"]
[/URL]

---

### Post by zaphod777 on 2009-12-27
> **zey said:**
> you must be be run it in normal user.
if you want wireshark working you should run it with root access.
run with this, open the terminal and type:
$ sudo wireshark

it must be solved your problem..



[http://z-computer-z.blogspot.com]("http://z-computer-z.blogspot.com/")[URL="http://ubuntuforums.org/z-computer-z.blogspot.com"]
[/URL]

I took a look at your blog it has lots of good stuff. Just curious what country you live in it seams English isn't your first language.

---

### Post by Big_tone on 2009-12-27
What I meant by "cable" was 'cable interntet' (as apposed to dsl or dialup).
Sorry I didn't specify how I was connected.  I have a cable modem that is directly connected to my pc via an ethernet cable. Yes, it is auto eth0.
I was just wondering why my ip address was listed as 'unknown'. Perhaps there is some configuration adjustment that I am unaware of still. 
Thanks for the response.

---

