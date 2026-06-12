---
title: "Vodafone USB dongle"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by autonomouse on 2009-02-05
Hi all,

I'm just writing this because I've had a hell of a time trying to get my new Vodafone Mobile Broadband Dongle thing working in Ubuntu 8.10. It's up and running now and it turned out to be very simple, so I thought I'd add it here in case anyone else is having similar problems.

For starters here's the basics: It's a Huawei K3565 dongle (also referred to as a E160X) with Vodafone (in the UK) on a pre-pay contract. I'm using Ubuntu 8.10 which is supposed to make it very simple by right clicking on the network manager applet and selecting 'Edit Connections', then choosing the 'Mobile Broadband' tab and clicking 'add'. For the most part it was simple (so Kudos to them for that), but the problem I had was that after I selected 'Vodafone (pre-pay)' from the list, it wouldn't connect, instead coming up with a box demanding the password. I searched the internet and some suggested putting 'web' or 'wap' in the password box, but also most seemed to say that you could put anything you wanted in there.

Eventually, I came across a forum which mentioned that the APN (currently set to 'pp.vodafone.co.uk') was wrong when you do this and instead it should be set to 'pp.internet'.

Lo-and-behold, it worked. I don't think the password matters, as I ended up having 'vodafone' in there, just 'cos it was the last thing I tried before finding this. Kinda lucky really as the one I had in there before was 'whythehellarentyouworkingyoulittledongling$£$@bag'.

Hope this helps someone - dunno who like seeing as though they can't get on the internet in the first place, but hey...

Autonomouse

---

### Post by dmizer on 2009-02-05
This may help? [http://ubuntuforums.org/showthread.php?t=858032](http://ubuntuforums.org/showthread.php?t=858032)

I do not have your modem, but I have seen lots of threads on the Huawei modem, so if that thread doesn't help you, you should be able to find one that does. I simply searched in google with the following search parameters:

Huawei howto site:ubuntuforums.org

the "site:ubuntuforums.org" restricts searches to ubuntuforums only.

---

### Post by Teucer on 2009-04-09
Just wanted to say "thanks" for this info. I was up and running in a couple of minutes with your advice. 

There are many posts out there saying that these dongles don't work - or take a huge amount of effort to get working. Matters aren't helped by Vodafone insisting it won't work either! 

From the various posts I've read it seems to be important that you register the dongle first on a Windoze machine to activate it? That's what I did anyway - after that I had no problems on Ubuntu 8.10 following your advice.

Thanks again.

Teucer

---

### Post by candlerb on 2009-04-16
Thank you - pp.internet is exactly what I needed to know. In my case I didn't have to configure it under Windows first. It's now running happily under Xubuntu 8.10.

This is the £39 Huawei dongle which comes with 1GB of credit. Also you get £10 back if you buy it through topcashback.com :-)

[Only problem now is working out how to register for top-ups online. I can create an account but it thinks I have a mobile rather than broadband and wants the phone number]

---

### Post by candlerb on 2009-04-16
Top-up problem solved.
* stick the SIM into a normal unlocked phone
* Dial *#100# to find out its PSTN number
* Enter this number in 'my account' 'register PAYG'
* Wait for the text message to arrive containing security code
* Enter this into web site (you have 20 minutes)
* Put the SIM back in the dongle

Incidentally, while the SIM is in the phone, you can also check credit using *#1345# - the web site shows the same amount.

---

### Post by Zimmer on 2009-07-03
My experience...
I found Vodafone Mobile Connect from Betavine...
Works ok so far...  

[https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

---

### Post by dgcarboni on 2009-10-25
Hi there,

This worked for be too. I tried a number of things, but the following seems to be what worked: (I'm using CrunchEEE on a 901 - CrunchBang / Ubuntu intrepid variant)

I'm not sure if these steps had an effect:
 - Install BetaVine package for ubuntu (I still can't get it to run though)
 - I then had to fix dependencies, which succeeded

The steps that got me working are:
 - Start up
 - Disable wireless (This helped prevent the system automaticallp connecting to my home wireless)
 - Plug in dongle
 - Prompt pops up to configure wireless broadband
 - Step through the dalogs to completion
 - Go to Edit Connections
 - Go to Mobile Broadband tab
 - Edit the connection
 - Set "APN" to pp.internet (as described above)
 - Click OK
 - If necessary, select the connection (In CrunchEEE, left-click the network icon in the taskbar and click on the connection you just edited)

To disconnect:
 - In CrunchEEE, I get a "disconnect" option in the network connections menu.
 - Give it a few seconds to do its stuff
 - Disconnect the dongle
 - Re-enable wireless
 - After 20-30 seconds it picks up my home wireless again

---

### Post by clarkkillick on 2010-04-18
Autonomouse's advice is basically right, but the APN may vary.  I've just got a friend's Huawei K3565 dongle connected to Vodafone Pay As You Go in Ubuntu 9.10.

The dongle connected OK in Windows.  In Ubuntu 9.10, the dongle was recognised by the Network Connection wizard, but didn't connect.

In Windows, I used the Vodafone software to find the settings; I had to look around a fair bit, and eventually found them in "Diagnostics", I think.

Back in Ubuntu 9.10, I edited the connection that the wizard had set up, and entered the settings I'd found in Windows, and the connection worked.  Experimentation showed that Username and Password didn't matter, but "Number" had to be *99# (as set by the wizard) and APN had to be PPBUNDLE.INTERNET

---

### Post by MishMich on 2010-06-11
Thanks for that, the last one cracked it for me also - Start up and go with pp.internet didn't work, so looked up the settings under windows, then in NBE 10.4 I put that in as plan unknown with ppbundle.internet, and user 'web', and it worked fine.  Works pretty fast on an Advent Wind with netbook ubuntu - even got a decent picture with streaming video from BBC iPlayer through it. 

Mish.

---

### Post by Jjude on 2010-06-15
Thanks Clarkkillick, ur post worked for me too after two days of trying.

---

### Post by startling on 2010-11-04
I have a Vodafone Huawei E160X and am running Ubuntu 10.04

I tried changing the APN to both pp.internet and ppbundle.internet and, just in case, tried it in uppercase as well. None worked.

I tried installing Betavine Connection Manager but that cannot connect either.

I'd really love to get this working so I don't have to use Windows.

---

### Post by startling on 2010-11-04
Having seen that usb-modeswitch seems to solve the problem for some people I installed it but it didn't work for me. Then I wondered, is usb-modeswitch running? A quick look in system monitor suggested not, so in a terminal I ran ```
usb_modeswitch
``` (note the underscore, rather than a dash) and I got the following error:
```
Error: Could not find file /etc/usb-modeswitch.conf
```

How should I resolve this error?

---

### Post by startling on 2010-11-04
After a lot of Googling I found this:

[http://www.sakis3g.org/]("http://www.sakis3g.org/")

It worked! Sakis Dimopoulos is a genius!

I must say I'm a bit surprised that Sakis, with a tweaked shell script, can get these dongles working but Ubuntu 10.04 cannot.

---

### Post by TNT1 on 2010-11-04
> **autonomouse said:**
> Hi all,

I'm just writing this because I've had a hell of a time trying to get my new Vodafone Mobile Broadband Dongle thing working in Ubuntu 8.10. 

Same dongle, 10.04, works otb.

---

### Post by jsampaio57 on 2010-11-16
Hi, if still interested, the vodaphone dongle, when connected to ubuntu, is seen as a flash storage because it comes with windows drivers onboard. You must install usb-modeswitch to turn of Zero-CD

cheers...

Jorge

---

### Post by jsampaio57 on 2010-11-16
This is a different question. I have a vodaphone dongle that was unlocked. Now I use it to access broadband from my notebook using Dodo. Does anybody know if, using the usb dongle and a regular mobile sim card on it, I can make a phone call using the notebook as a mobile phone (instead of using skype, and similar). That is, can the dongle and the mobile turn into a mobile phone?

Cheers...

Jorge

---

### Post by startling on 2010-11-16
Thanks for the reply Jorge. I tried installing usb-modeswitch but it still didn't work - and still doesn't!

---

### Post by alexfish on 2010-11-16
> **startling said:**
> Thanks for the reply Jorge. I tried installing usb-modeswitch but it still didn't work - and still doesn't!
Hi

try to get system back to normal

uninstall vmc , wadercore


then reinstall modem-manager

see what happens

install latest usb_modeswitch follow debian link at

at the [Debian Repository]("http://packages.debian.org/usb-modeswitch").

alexfish

---

