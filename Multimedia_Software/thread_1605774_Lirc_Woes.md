---
title: "Lirc Woes"
date: 2010-10-25
forum: Multimedia Software
---

### Post by dyvid on 2010-10-25
My Background:
I'm new to Linux, I started playing around in linux back last year (May-June 09).  I have been trying to configure mythtv, lirc, misterhouse and zoneminder (gave up and went with motion).  I perfer Intrepid, but I have been venturing into Karmic (all 32bit).

I have mythtv installed via apt-get with both Intrepid and Karmic.  I also built it once for karmic as directions for the hd-pvr.  My issue is I can never get lirc to create /dev/lirc0 and /dev/lirc1.  Sometimes I can get lirc0 working, but only for the remote.  I wanted to control my stb (directtv d1-100) with the blaster.

When I grep the dmeg I can see the modules are loaded, mythtv sees them but lirc won't make the proper nods(?) for them.

I have been trying different forums and threads to get lirc to work, but I can't seem to do it on any devices I have.

My current os/hardware is karmic32, hvr-1600, nvidia 8400gt, which all of them should work together.  (Yes I did the vm alloc thing to ensure they don't fight over the memory).

```
root@msiX2haup1600:~$ dmesg | grep lirc
[    9.522134] lirc_dev: IR Remote Control driver registered, major 61 
[    9.575579] lirc_zilog: Zilog/Hauppauge IR driver initializing
[    9.576481] lirc_zilog: initialization complete

```

The following hardware is what I have to play with:
hvr-1600 (yes I checked that is the 1600 I have)  [URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16815116033&cm_re=hauppauge_1600-_-15-116-033-_-Product"]link
[/URL]hd-pvr [link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116030&Tpk=hdpvr")
GP-IR02BK [URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16880121002"]link
[/URL]imon/veris basic [link]("http://www.avadirect.com/product_details_parts.asp?PRID=12708")
imon/veris external [link]("http://www.google.com/products/catalog?q=veris+ir&hl=en&cid=10049782188276861981&ei=LALGTKfJC6W4iwS7yPXNDQ&sa=title&ved=0CAcQ8wIwADgA#p")

I have tried ubunt, mint, mythbuntu, and mythbuntu post ubuntu install.  I can get all of these devices to read in the dmesg but none of them will make anything besides lirc0 or a lircd and lircd1 combo in my dev directory.

####

The truly funny thing though.  I have the hd-pvr on another machine with karmic, it sees the hdpvr in mythtv but I can't use it when I try live tv or record from mythweb....but I do have the blaster actually working.  I don't know why it won't work in mythtv (yes I did the cat > test.ts and it plays) but it is the only thing that actually blasts....the opposite from every other issue.

I appreciate any input and welcome any advice,
Dyvid

---

### Post by dyvid on 2010-11-04
If no one has any advice regarding this, let me ask a simple question:

What is a good, out of the box, MCE remote that will work with ubuntu and mythtv in the way of transmitting?

I know Philips has been thrown around, but is there one over another that works better or worse?

Just looking for a dual ir blaster that I can setup.

---

### Post by YfoMp5QBh2 on 2010-11-05
Invest in a Logitech Harmony, I have the Harmony 550 and I use it with the standard MCE IR receiver with Ubuntu 10.04 lucid lynx running XBMC with LIRC without any problems. :)

---

### Post by dyvid on 2010-11-05
The harmony remote doesn't come with IR blasters/transmitters/emitters, does it?

It would solve issues with live tv, but not for scheduling and recording tv.  I managed to discover the beauty of firewire for my friend (so now he has an older shuttle recording 2 comcast stb).

However, still being a student in a JC I am too cheap to buy my own comcast, so I just pay $5 a month off of my parent's plan.  

Sadly, DirectTV doesn't have firewire....Though they did have a usb port, but I have heard horror stories about that though.

Thanks for the input!

~Dyvid

---

### Post by YfoMp5QBh2 on 2010-11-06
Check out the Logitech website, I write on other forums too and alot of people swear by the Harmony (me included). You should be able to find an equivelent (if not better) remote you need for a reasonable price. Of course the nicer remotes with more functionality are more expensive.

---

### Post by dyvid on 2010-11-29
I was hoping for another reply.

The problem isn't the remote.  The problem is I need an ir transmitter that can control other appliances like my directv std, the tv, and the entertainment center (speakers).

My friend has a harmony remote, but the fact of the matter is I need something that will automaticly change channels when I am gone so mythtv can record different shows.

Does anyone know of a good IR blaster/emitter/transmitter?  (by good I mean works well, with little or no configuration)

---

