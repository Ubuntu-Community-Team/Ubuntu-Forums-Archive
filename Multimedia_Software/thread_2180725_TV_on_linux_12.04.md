---
title: "TV on linux 12.04?"
date: 2013-10-14
forum: Multimedia Software
---

### Post by donaldt on 2013-10-14
OK, so I have a capture device [/dev/dvb/adapter0], VLC and TVTime are installed and my mission is to watch LIVE TV on my computer.  I've read a lot of stuff about how to set up TV (I want the golf channel live) but nothing works.

I'm 6 years into Ubuntu, but not a geek.  Can anyone lead me through the process of setting this up?

Thanks if you can help!

DonaldT

---

### Post by howefield on 2013-10-14
Is this a dvb-t card ?

All I do is create a channels.conf file by installing dvb-apps and run a channel scan with...

```
scan /usr/share/dvb/dvb-t/uk-xxxxxx -o zap | tee ~/channels.conf
```

where xxxxxx is the name of my local transmitter. Load up VLC and navigate to > Media > Advanced open > Add .conf file and press play.

Having said that, kaffeine is much easier :-) but obviously brings in kde dependancies, which is a problem for some but not others.

Too long since I used TVtime to remember...

---

### Post by donaldt on 2013-10-14
thanks for the reply.  Yes, this appears to be a dvb-t card, at least that is what it says under capture device (tv digital) in VLC.

I'll try what you suggest...

DonaldT

---

### Post by donaldt on 2013-10-14
Just so there is no misunderstanding...I am looking for TV from the internet.  All of my digital HD TV comes off Sandia peak via a television tower.  I can see the towers out my window.  I get 30 stations free.  I no longer have cable/satellite/dish or any other cable service.  I get Fox, CBS, NBC, ABC, PBS etc. but no ESPN or Golf Channel.  

My interest in TV on my computer is to enable live sources such as the Golf Channel and ESPN for coverage of events no longer available after I cancelled COMCAST!

Thanks again for your help!

DonaldT

---

### Post by M7CPn4b on 2013-10-15
Hey,

what have you tried so far?

Have you tried Kaffeine? It can scan for DVB-T stations. Here's a quick tut: [http://www.linuxtv.org/wiki/index.php/Kaffeine#Example_of_Using_Kaffeine_for_.22over_the_air_broadcasts.22](http://www.linuxtv.org/wiki/index.php/Kaffeine#Example_of_Using_Kaffeine_for_.22over_the_air_broadcasts.22)

I think that's a good program to test if it works. Once you got reception, I'd have a look at the xbmc mediacenter as a frontend with tvheadend as a backend for live TV. Very comfy ;)

~Emily

---

### Post by donaldt on 2013-10-15
Hi,

Thanks for the tip.  However, I don't find Kaffeine with synaptic package manager.

When I try TVTime it opens the camera and I'm staring back at myself...  Escape takes me back to installed programs.  I'm really confused but do appreciate your help!

DonaldT

---

### Post by deadflowr on 2013-10-15
> **donaldt said:**
> Just so there is no misunderstanding...I am looking for TV from the internet.  All of my digital HD TV comes off Sandia peak via a television tower.  I can see the towers out my window.  I get 30 stations free.  I no longer have cable/satellite/dish or any other cable service.  I get Fox, CBS, NBC, ABC, PBS etc. but no ESPN or Golf Channel.  

My interest in TV on my computer is to enable live sources such as the Golf Channel and ESPN for coverage of events no longer available after I cancelled COMCAST!

Thanks again for your help!

DonaldT

You'll have to deal with those channels individually(unless there is an internet service which packages those channels).
They are paid subscription television channels and so, getting them legally from the net is up to how they provide them.

but, none the less, look into the me-tv package in the repos.

---

### Post by M7CPn4b on 2013-10-16
REading through your replies, I'm left a bit confused:

> **donaldt said:**
> I have a capture device [/dev/dvb/adapter0]

> **donaldt said:**
> this appears to be a dvb-t card

and then you say this:

> **donaldt said:**
> Just so there is no misunderstanding...I am looking for TV from the internet.

Are you looking for DVB-T television or live streams on the internet?

The first requires a DVB-T card/stick AND an antenna, but you seem to be close enough to the tower, to be able to use a small (diy ~$0-$15) indoor one.
The latter depends very much on the stations, if they provide a stream. Other ways to obtain streams are available, and questionable regarding whether or not they are legal.


Kaffeine is even available through the software center in Ubuntu 12.04. [https://apps.ubuntu.com/cat/applications/precise/kaffeine/](https://apps.ubuntu.com/cat/applications/precise/kaffeine/)

Could you also give me the output of "*dmesg | grep dvb"?*

-Emily

---

### Post by donaldt on 2013-10-18
Emily,

Thank you again and sorry i've been offline for a while.  I have downloaded Kaffeine and it is available.

Yes, I realize there is no convenient way to get cable channels from the internet.  Often, however, there are broadcasts that come from Europe (I'm in NM USA) and some are free and some require payment.  I just want to be able to use the TV capability on my computer.

You asked what was the result of "dmesg/grep dvb"  No such file or directory.

Best regards,

DonaldT

---

### Post by M7CPn4b on 2013-10-18
> **donaldt said:**
> You asked what was the result of "dmesg/grep dvb"  No such file or directory.

It's: dmesg | grep DVB (a vertical bar, not sure where it is on an US keyboard)

-Emily

---

### Post by Otto-C on 2013-10-27
Actually its called a pipe. Its located usually above the "]" key

---

