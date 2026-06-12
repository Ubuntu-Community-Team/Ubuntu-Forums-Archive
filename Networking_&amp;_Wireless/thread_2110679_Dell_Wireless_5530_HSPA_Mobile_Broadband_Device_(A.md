---
title: "Dell Wireless 5530 HSPA Mobile Broadband Device (AT&amp;T)"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by baddison1 on 2013-01-30
Hello to all. I am a very very new Ubuntu user. I have installed 12.04LTS on my Dell Latitude E4300. This laptop has an onboard AT&T (GSM) Mobile Broadband device. When I go to set up a Mobile Broadband connection, the system defaults to Dell Wireless 5530 HSPA Mobile Broadband Device. I am able to even see the IMEI number associated with the device. I have already called AT&T to test and verify that the card is active on their network. And it works in windows environment with AT&T Connection Manager software.
 
So, I guess you can imagine where I'm going with this...LOL! I cannot get this broadband card to work with Ubuntu. I have attached a terminal lspci -nn output. I don't even see the device in the output, but Ubuntu shows it there when I go to set it up. Does anyone have any ideas to get this mobile device t connect? Is it possible the drivers are not correct? Has anyone successfully gotten their onboard gsm card connected?
 
All suggestions and advice welcome. Thanks in advance.

---

### Post by Bucky Ball on 2013-01-30
Welcome to the forums. You have posted in the correct section but to improve your chances of getting help please use descriptive thread titles. This one is generic and gives no information about your actual problem. 

Example:

'Can't connect  AT&T (GSM) Mobile Broadband device'

... or something like it.

To improve your chances of help you can change the thread title by editing the first post and clicking 'Go Advanced.' Good luck.

---

### Post by baddison1 on 2013-01-30
> **Bucky Ball said:**
> Welcome to the forums. You have posted in the correct section but to improve your chances of getting help please use descriptive thread titles. This one is generic and gives no information about your actual problem. 
 
Example:
 
'Can't connect AT&T (GSM) Mobile Broadband device'
 
... or something like it.
 
To improve your chances of help you can change the thread title by editing the first post and clicking 'Go Advanced.' Good luck.
 
Thank you.....title changed.:)

---

### Post by Bucky Ball on 2013-01-30
All good. ;)

The new title is what people will see in the thread list, even though only the first post here shows it and the rest don't.

---

### Post by baddison1 on 2013-01-31
title change??? not seeing new title of this thread

---

### Post by mörgæs on 2013-01-31
Title must be changed for the thread, not for a single post. 
Done.

---

### Post by Bucky Ball on 2013-01-31
> **baddison1 said:**
> title change??? not seeing new title of this thread

The new title appears only on the first post and in the thread list which comes up in New Posts so all would-be helps see the new title, not the old. The rest of the posts in the thread retain the old title. 

The thread title can only be changed by editing the first post, not after that. You can go back and edit that, hit 'Go Advanced' and change it there to whatever you want, by the looks of it 'Can't connect AT&T (GSM) Mobile Broadband device'.

---

### Post by baddison1 on 2013-01-31
When I run the "ls -al..." command, this is the output I get:

bernadette@LatitudeE4300:~$ ls -al /dev/serial/by-id/*
lrwxrwxrwx 1 root root 13 Jan 31 08:19 /dev/serial/by-id/usb-Dell_Dell_Wireless_5530_HSPA_Mobile_Broadband_Minicard_Device_3541420206631770-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 Jan 31 08:19 /dev/serial/by-id/usb-Dell_Dell_Wireless_5530_HSPA_Mobile_Broadband_Minicard_Device_3541420206631770-if03 -> ../../ttyACM1
lrwxrwxrwx 1 root root 13 Jan 31 08:19 /dev/serial/by-id/usb-Dell_Dell_Wireless_5530_HSPA_Mobile_Broadband_Minicard_Device_3541420206631770-if09 -> ../../ttyACM2


Clearly the device is recognized by Ubuntu.  But why can I not connect successfully to the AT&T network?  I have already verified with AT&T that the device is active, and the IMEI # is correct.  Additionally, this works flawlessly in Windos OS.  Can someone point me in the right direction?

---

### Post by baddison1 on 2013-01-31
Just tried to run AT&T Communications Manager thru POL (play on linux).  Isnt that supposed to be the vehicle to run any windows program on linux???  Getting more and more confused here.....*sigh*

---

### Post by mörgæs on 2013-02-01
> **baddison1 said:**
> Just tried to run AT&T Communications Manager thru POL (play on linux).  Isnt that supposed to be the vehicle to run any windows program on linux?

No. It runs some Windows applications, and the same goes for Wine. 

My best unscientific and untested advice is to try a fresh install of the development version (13.04).

---

### Post by baddison1 on 2013-02-01
> **mörgæs said:**
> No. It runs some Windows applications, and the same goes for Wine. 
 
My best unscientific and untested advice is to try a fresh install of the development version (13.04).
 
Has there been documented success with 13.04 and dell 5530 mobile broadband device?
 
 
Additionally, is there a place to download linux-specific drivers for this card? Obviosly support.dell.com doesnt have them. :(

---

### Post by baddison1 on 2013-02-01
So, I ran the nm-tool command, and the first thing to pop up was the wwan0 Mobile Broadband card.  I noticed the driver associated with this card is called "cdc_ether".  If I could get real linux drivers for this device, the perhaps it might help.  I also downloaded wicd from the app store.  this lead to another dead end.




bernadette@LatitudeE4300:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wwan0 ----------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_ether
  State:             disconnected
  Default:           no

  Capabilities:

bernadette@LatitudeE4300:~$ exit

---

### Post by baddison1 on 2013-02-01
OK....so I did a "lsusb" command, and it turns out the Dell 5530 shows up as:
 
Bus 002 Device 002: ID 413c:8147 Dell Computer Corp. F3507g Mobile Broadband Module.
 
 
Isn't that the model number for the Ericsson WWAN Mobile Broadband card?????
 
stranger.....and stranger....
 
I don't think I've ever had such issues with windows OS .... at all.
 
Off I go to do more research.
 
I would love to use Ubuntu as a daily driver for some of my project managers....but most of their machines have this onboard Mobile Broadband card installed.  If they can't work remotely, then this is not even a possiblilty. 
 
@mörgæs : I looked into dev version 13.04, but since its not as stable, this would not be viable as a "daily driver" either.  Thanks much for you suggestion.  Please keep 'em coming!! I simply MUST resolve this issue.

---

### Post by bmork on 2013-02-01
> **baddison1 said:**
> So, I ran the nm-tool command, and the first thing to pop up was the wwan0 Mobile Broadband card.  I noticed the driver associated with this card is called "cdc_ether".  If I could get real linux drivers for this device, the perhaps it might help.

What makes you think "cdc_ether" isn't the real linux driver for this card? It is.

And the card is a Dell branded Ericsson card, yes.  And as you already found out, it is supported in NetworkManager/ModemManager.

---

### Post by baddison1 on 2013-02-01
> **bmork said:**
> What makes you think "cdc_ether" isn't the real linux driver for this card? It is.
 
And the card is a Dell branded Ericsson card, yes. And as you already found out, it is supported in NetworkManager/ModemManager.
 
sadly, instill cannot get this card to connect to AT&T. I believe I've tried all the recommendations on the forum.  Is there anyone here who is successfully using their Dell 5530 Mobile Broadband card with Ubuntu 12.04?  I wish I could find a step-by-step setup/guide  :(

---

### Post by mörgæs on 2013-02-02
> **baddison1 said:**
> 
 
@mörgæs : I looked into dev version 13.04, but since its not as stable, this would not be viable as a "daily driver" either.  Thanks much for you suggestion.  Please keep 'em coming!! I simply MUST resolve this issue.

You're welcome. My advice is still that you try 13.04. You need more testing and less investigation.

Until you try, you don't know how stable 13.04 is *on your hardware*. My 10.04 setup was installed at an early alpha stage and has been updated to today without major problems.

---

### Post by baddison1 on 2013-02-02
> **mörgæs said:**
> You're welcome. My advice is still that you try 13.04. You need more testing and less investigation.

Until you try, you don't know how stable 13.04 is *on your hardware*. My 10.04 setup was installed at an early alpha stage and has been updated to today without major problems.

you're correct! i'm headed over to 13.04 now....will keep you all posted ;)

---

### Post by Bucky Ball on 2013-02-02
I have no idea why installing a still testing, unreleased version is going to make any difference. But hey, why not? Expect unexpected breakages even if it does fix your wireless issue, and I see no reason it will.

---

### Post by baddison1 on 2013-02-02
> **Bucky Ball said:**
> I have no idea why installing a still testing, unreleased version is going to make any difference. But hey, why not? Expect unexpected breakages even if it does fix your wireless issue, and I see no reason it will.

Definitely what I was thinking...but its worth a shot.  I am really confused as to why all my searches do not turn up a working fix for this.  Is this such an oddity trying to get the Mobile Broadband card to work?

I've seen suggestions on rebuilding the kernel?!?!  what - I don't even know what that means...I'm so new to this.

I've seen suggestions on using wicd -didn't work.  I've seen suggestions on using gnome-ppp...couldn't even find a suitable download for that one.  
I will continue to search and test and investigate - it is absoultely crucial that I get this working.  I would love to be able to deply ubuntu on the laptops in our company, but they all have this mobile broadband card in them....about 40 laptops.  So this is a must for me.

I really appreciate all the replies, ideas and suggestions this far.  I am confident with all the knowledge in this community, I will get this working just fine.

---

### Post by Bucky Ball on 2013-02-02
If you are wanting to deploy Ubuntu in a production situation you definitely don't want 13.04. The LTS releases are designed for this very purpose (production machines and servers which need to be stable, reliably on and up for long periods).

12.04 LTS. I hope you can find a fix for this so you can deploy Ubuntu on those forty machines. Good luck.

---

### Post by baddison1 on 2013-02-03
HAving the same issue with 13.04 ,network manager sees mobile broadband device but I cannot connect. Is it possible to see the connection as it executes? Perhaps I can look at the connection script? or connection config ? Where do I pull this up?

---

### Post by Bucky Ball on 2013-02-03
Please post in the Ubuntu +1 forum about this:

[http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

It is not yet released and all posts concerning it go there, as this one probably will before long (the individual post with a little editing). That is where it belongs because those that are testing 13.04 and can help you hang out there.

---

### Post by baddison1 on 2013-02-03
> **Bucky Ball said:**
> Please post in the Ubuntu +1 forum about this:

[http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

It is not yet released and all posts concerning it go there, as this one probably will before long (the individual post with a little editing). That is where it belongs because those that are testing 13.04 and can help you hang out there.

Thanks Bucky.  I'm back.  13.04 was a no-go for me.  Formatted the entire harddrive, and reinstalled 12.04.  Starting from scratch all over again.  Gonna keep scouring these forums and the internet for a solution to this.  Still hoping that someone who has been successful in getting this to work , will see this post and help me out. 

Additionally, I've opened up a launchpad.net issue. 

There has GOT to be a solution for this.  Too many of us have mobile broadband cards in our systems....so....

I will keep you all posted on my progress.  If I solve this, I will definitely be very detailed in how I got it done.

**_QUESTION:_** how can I see what commands the modem is sending when trying to connect?  I'm thinking the solution may lie in configuring the right commands.

---

### Post by mörgæs on 2013-02-04
The development-part of the problem:
[http://ubuntuforums.org/showthread.php?t=2111658](http://ubuntuforums.org/showthread.php?t=2111658)

---

### Post by baddison1 on 2013-02-05
Launchpad.net bug report:
[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/1114575](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/1114575)

Please feel free to contibute anything you think may help.  There are multiple log files listed there as well.

Thanks in advance for everyone's support here!!

---

### Post by baddison1 on 2013-02-07
Totally solved!!!  Up and running...needed to physically connect the antennae to the modem on the hardware itself.  Go figure!!
 
 
[https://bugzilla.gnome.org/show_bug.cgi?id=693309](https://bugzilla.gnome.org/show_bug.cgi?id=693309)

---

