---
title: "mobile broadband with ubuntu 10.04"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by Whitston on 2010-07-06
My netbook is running ubuntu 10.04.  I have tried an o2 MF100 dongle with no success (completed the network manager connection wizard, but no recognition of the dongle and no connection).

Sorry, but I am not able to follow some of the more technical suggestions on problem solving, so I intent to fix this by buying a dongle that works out of the box with 10.04.

If you have such a dongle, please give me the details!!!!

Jim Whitston

---

### Post by pdc on 2010-07-06
Jim;

can we get you to try one last thing?

can you copy and paste these commands into a terminal:

> lsusb

and 

> dmesg | grep tty      copy and paste the commands and then copy and paste back the results ........

if you DO NOT get a ttyUSB0 at least ........

go here

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

click on the 1.1.3-1 in the sid unstable list (unstable means latest and greatest)

when you get this package into your downloads folder, right click and install with what the system offers: gdebi installer;

usb_modeswitch should get it working for you ..........

all these modems can be got to work: you are in the UK? 

There is support here on the forum to help you;

---

### Post by Whitston on 2010-07-06
OK PDC, I will give it a go.  I am in the uk and I should perhaps say that this dongle (unlike most) does not have any credit loaded onto it.  You use it by going online and paying up front for a day, a week or a month.   I say this because that may make a difference.  I see from another post that the vodaphone dongle must be loaded from a windows/mac pc and then used on the ubuntu machine.

Last point.  When I type in the commands you have given me, should the dongle be connected?

Thanks

Jim

---

### Post by pdc on 2010-07-07
> I see from another post that the vodaphone dongle **must be loaded** from a windows/mac pc and then used on the ubuntu machine.

I don't think that is correct

> I am in the uk 

I used a Vodafone simcard in the UK recently; it worked well; I brought an unlocked Huawei modem and it ran well (on linux); having bought a Vodafone simcard; no windows in sight

> *When I type in the commands you have given me, should the dongle be connected*?

Yes indeed; both are asking questions about the modem

>  *this dongle (unlike most) does not have any credit loaded onto it. You use it by going online and paying up front for a day, a week or a month*

well hopefully the rules of that provider will allow connection to pay for the forthcoming use .........

---

### Post by Whitston on 2010-07-07
OK, here are the results I got from the terminal messages you gave me.

jim@jim-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c526 Logitech, Inc. MX Revolution Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 19d2:0017 ONDA Communication S.p.A. 
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 174f:1403 Syntek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

jim@jim-laptop:~$ dmesg l grep tty
Usage: dmesg [-c] [-n level] [-r] [-s bufsize]

Did not understand the part of your message which said if you do not get ttyUSBO, so have not gone to the web site you provided.  
My question over whether the dongle needed to be connected when I entered these questions in the Terminal shows just how little I understand about all this!

Thanks

Jim

---

### Post by pdc on 2010-07-07
Jim:

I think your modem should be ready to go;

here it is

> ID 19d2:0017 ONDA Communication S.p.A. 

and it is already switched as seen as modem 

copy and paste this command

> dmesg | grep tty 

the middle command is actually got from SHIFT-backspace so best to copy and paste the above 

If you get any ttyUSB0 results, follow this guide

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

on how to configure

HALF_WAY Down the page

CREATE A MOBILE BROADBAND CONNECTION ..........

---

### Post by Whitston on 2010-07-07
I copied and pasted the line you gave me, and this is what the Terminal came back with.

jim@jim-laptop:~$ dmesg | grep tty 
[    0.000000] console [tty0] enabled
[   25.941604] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[   25.941919] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[   25.942247] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
[   25.942558] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB3
[   32.790082] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[   32.790365] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[   32.790647] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[   32.790926] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
jim@jim-laptop:~$ 

I suppose that this is what you mean by "ttyUSB0" results.  I will have a go with the link you provided, but unless it is written for complete beginners, then I expect problems.  Will get back to you.

Thanks

Jim

---

### Post by Whitston on 2010-07-07
Hi PDC,
I went to the website and saw the Create a Mobile Broadband Connection.   This is what i did when i first got the dongle - I called it "completed the Network Manager connection wizard" in my first post.

When I completed this, the network manager filled in all the boxes for me, including the username, password and APN.

Despite all this, no connection is possible, and I have had no opportunity to load the o2 connection manager which comes (I think) in the dongle.

Anyway, I think I have bought the wrong item.  Others seem to have success with the Huawei models, and I think I should try one of those.

Don't like to give up, but I think that something that works out of the box is what I need.  Thanks for your help anyway, 

Jim

---

### Post by pdc on 2010-07-07
so you right click on network manager;

edit ..

mobile broadband ..

add ..

country . provider O2:

then when accepted LEFT-CLICK on network manager, and click on the O2 you have just entered ???????

I see the default one on network manager is contract: you aren't on prepay?

this site also lists apn settings

[http://www.filesaveas.com/gprs.html](http://www.filesaveas.com/gprs.html)

> Access point (contract): wap.o2.co.uk
Access point (PAYG): payandgo.o2.co.uk


> *and I have had no opportunity to load the o2 connection manager which comes (I think) in the dongle*.

You won't need that ...........

> *Anyway, I think I have bought the wrong item*.

... your modem is being recognised as a modem .......

---

### Post by ieee488 on 2010-07-07
> **Whitston said:**
> I have had no opportunity to load the o2 connection manager which comes (I think) in the dongle.


The connection manager is only useful for Windows.

---

### Post by Whitston on 2010-07-08
Thanks to PDC and 488.

I now realise that the manager that comes with the dongle is not needed on ubuntu.   Regarding the ubuntu network manager, I created an entry for o2 by following the prompts.  It was for payandgo.  The username was payandgo, the password was payandgo and the APN was payandgo.o2.co.uk, all entered automatically when I selected the o2 payandgo option.   Just in case there is not 3g signal at my house I took the computer into our local town where the phone shop assured me there was a 3g signal, and no change there.

I am grateful for the help you have provided and I now understand a little more about how it should work, but my original post was a request for a dongle that works with 10.04 without too much technical knowhow, so I intend to return the o2 to the shop and try a different model.  Thanks again.

Jim

Jim

---

### Post by pdc on 2010-07-09
well; keep in touch Jim and let us know how it goes;

........ sounds like ....... the USB dongle configured well ...

.... without too much effort?

.......so you can become a linux ambassador ???? !!!!!

---

### Post by Whitston on 2010-07-10
Hi PDC,

Perhaps I will be an ambassador now that I have mobile broadband.  Here is the story.  Gave up on o2 and on the advice of another guy bought T-Mobile usb 120.

Entered everything into the network manager, which gave me Username as User, Password as mms and APN as general.t-mobile.uk 

Tried to connect, but each time got a pop-up asking for a ZTE password (not keyring)

Entered all sorts of things, but no luck.

Then found a msg on the forums from little(underscore)penguin who said
Change User to user
Change Password to pass

I did this and am now online!

It is all black magic to me, but just in case someone else gets this problem I thought I would give you the details.  Going to lie down in a dark room now....

Jim

---

### Post by pdc on 2010-07-10
great work Jim; well done; enjoy

rest and celebrate your triumph!

when recuperated if you were to make a new post with (SOLVED) in the title line, 

just describe what you did for T-Mobile (UK?) and post it and then google can find it for others; useful for others following in your path

---

### Post by Whitston on 2010-07-10
When you say a new post, do you mean as a reply to this thread, or as a new thread???

Jim

---

### Post by pdc on 2010-07-10
sorry for the confusion

I meant a new thread

---

### Post by Whitston on 2010-07-11
OK.  Goodbye until my next crisis.

Jim

---

