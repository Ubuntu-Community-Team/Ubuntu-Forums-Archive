---
title: "GPRS connected but no data transfer"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by oldmankit on 2009-09-20
Hi,

Really impressed with ubuntu 9.04.  The easiest linux distro I've ever attempted to use!  I'm trying to use my Nokia ExpressMusic 5310 to connect to the internet through GPRS.  I'm doing this under windows nicely, but have to use the nokia PC suite software to get me there.

Here's how it goes.  I connect the phone using a usb cable, and after going through the wizard (in which it successfully finds my mobile service provider), it 'successfully' connects.  It all looks like it should work, only, I can't get any pages to load in firefox.

I know I'm probably not giving enough details for anyone to help me, but that's all I can think of for now.  FYI, I can't get it to connect using bluetooth, but USB is my priority, and I'll sort bluetooth out later.

I really appreciate any help.
Kit

---

### Post by oldmankit on 2009-09-21
Honk honk 
(I use my horn to avoid bumping)

I know the original post doesn't contain many details; I just can't think of any more to include to help troubleshoot.

LAN and wifi are working fine.

---

### Post by oldmankit on 2009-09-24
Patiently waiting for any suggestions how to get started tackling this....I don't have broadband at home, so rely on using my girlfriend's windows laptop to use the 'net right now...a little inconvenient.  Honk honk!

---

### Post by misfitpierce on 2009-09-24
Ummm you wanna chose pc suite on nokia phone and not sure what company you have but I have 6301 with T-Mobile and just chose T-Mobile WAP from the popup thing not the Internet one since I got phone not PDA and it worked instantly.

---

### Post by oldmankit on 2009-09-24
> **misfitpierce said:**
> Ummm you wanna chose pc suite on nokia phone and not sure what company you have but I have 6301 with T-Mobile and just chose T-Mobile WAP from the popup thing not the Internet one since I got phone not PDA and it worked instantly.

Wine complained that Nokia PC suite is 'rubbish' and that it basically will not work under linux.

---

### Post by oldmankit on 2009-09-30
Honk honk!  Still waiting to be able to use the internet at home!  All help is appreciated.

---

### Post by oldmankit on 2009-10-06
Twiddle twiddle
I have to twiddle my thumbs using windows until someone helps me!  Please!

To re-state the problem: connecting my nokia 5310 express music via usb cable to my neat new jaunty ubuntu installation, the 'mobile broadband' wizard successfully suggests my country (Thailand) and mobile service provider (DTAC).  When I click 'connect' from the connections menu, my phone says that it's connecting...and hey presto, a GPRS connection is opened on my phone.

The difference with the result of this procedure between windows and ubuntu is as follows.  After the GPRS connection has been established on the phone, in windows internet pages load, in ubuntu, they don't load.  Zilcho.

When my laptop is in the right place, I get wireless and ethernet internet on ubuntu very nicely.  Just GPRS isn't working.

Yours patiently,
oldmankit

---

### Post by Bharath on 2009-10-09
Hi,

I am on 8.04.... I can't completely understand what real problem is.... but I guess it is a basic issue.... From your mail what I see is that... you have not removed existing network settings.

Before connecting to GPRS .... Go to System->Network-> Network settings and remove all the connections (remove in check box) then connect... I guess you must be able to load pages.

Bharath
See also old way of doing things (if required): 
[http://www.zyxware.com/articles/2008/02/11/setting-airtel-gprs-ubuntu-nokia-communicator-9300-and-data-cable](http://www.zyxware.com/articles/2008/02/11/setting-airtel-gprs-ubuntu-nokia-communicator-9300-and-data-cable)
[http://ubuntuforums.org/showthread.php?t=1091189](http://ubuntuforums.org/showthread.php?t=1091189)

---

### Post by PrePenguin on 2009-10-09
just set it up as a usb modem if possible.. If needed i can do the same with my cellphone via the USB cable.

---

### Post by oldmankit on 2009-10-10
Hooray!

Thanks for the help.  Reference to [this]("http://forum.ubuntuclub.com/forum?topic=4239.msg21058#msg21058") page for the steps (it's in Thai).

I managed to set-it up with the following steps:

> sudo wvdialconf /etc/wvdial.conf
sudo gedit /etc/wvdial.confand adding/uncommenting the following lines:

> Phone = *99#
Username = ''
Password = ''
Stupid Mode = 1After that, using > sudo wvdial works a treat.

I truly don't understand why using the Network Connections wizard didn't quite work.  It opened a connection and on my phone it displayed the little logo to say that GPRS was operative, however, no information was getting through.  I couldn't load any webpages.

However, now it works, and that's the important thing.

---

### Post by misfitpierce on 2009-10-10
> **oldmankit said:**
> Wine complained that Nokia PC suite is 'rubbish' and that it basically will not work under linux.

Uh I said on the phone... You don't need to use PC Suite like actually. My 6301 connected instantly. Go to usb settings on phone and select choose at plugin and when the popup comes up choose pc suite on phone and then it should ask you to configure on laptop or manually do it under network settings and setup a wireless config for your provider. I have T-Mobile with Nokia 6301 and it just worked when I selected T-Mobile Web and plugged it in and selected PC Suite on phone. Don't actually need PC Suite or any software.

---

