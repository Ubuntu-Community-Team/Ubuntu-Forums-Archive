---
title: "Sending and receiving SMS with Ubuntu 9.10"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by Sven6210 on 2010-02-15
I have the UMTS Stick Huawei E160 with a prepaid SIM card from tchibo/O2 in Germany. The prepaid SIM allows daily flat-rates at a reasonable price however I need to send and receive a SMS (*short message service*) in order to book the daily flat-rate.

I have tried the following programs already:

1. umtsmon (in different vrsions incuding the O2 version). Unfortunately I was not able to send or receive SMS with umtsmon

2. Wammu (intalled trough the repositories); I can read the SMS from the SIM card however I get an error message when sending a SMS and the program fails.

I guess there must be other Ubuntu users that use their UMTS stick to send an receive SMS. What is your solution and ho o you do it? I am even open for any solution. So far I have to use a Windows machine or but the SIM in my mobile phone in order to book the daily flat-rate. I am sure there are better solutions.

Thank you for your help

Sven

---

### Post by iponeverything on 2010-02-15
you can do sms through gmail and google voice.

---

### Post by Whoopie on 2010-02-15
The [_wader_]("http://www.wader-project.org") project has support for SMS, but I've never tested it.

---

### Post by Chrissss on 2010-02-15
> **iponeverything said:**
> you can do sms through gmail and google voice.

Not in Germany... In Germany SMS are a valuable good. The telcos charge you usually ~20 euro cent (about 0.27 u.s. cent) for one sms ;) It's not possible to send SMS via Gmail in Germany.

---

### Post by Sven6210 on 2010-02-16
Well, it's not only the fact that SMS do cost money in Germany. I need to send an SMS from the SIM number in order to book the daily flatrate. So even though it would be possible to use gmail I do not have Internet (and therefore gmail) if I do not send an SMS before.

I tried 'Wader GTK 0.3.6.4' and it looks very well apart from sending and receiving SMS. And that is actually what I am really looking for.

Thank you for your help however I still need to wait for further feedback. I am surprised how difficult it is receiving and sending SMS through a UMTS stick. I alwys thought it should be rather simple.

---

### Post by Whoopie on 2010-02-16
It's documented here:

[http://docs.wader-project.org/user/tutorial.html#sending-a-sms](http://docs.wader-project.org/user/tutorial.html#sending-a-sms)
[http://docs.wader-project.org/user/tutorial.html#receiving-sms](http://docs.wader-project.org/user/tutorial.html#receiving-sms)

---

### Post by spazlon on 2010-02-16
I have the same modem for my 3G internet here in Kuwait. I was able to send and receive SMS with it using Gammu. The only problem I had was that I could not send/receive SMS while I was connected to the internet.

Check out this site, it might help you out. [http://cakesms.blogspot.com/](http://cakesms.blogspot.com/)

I got all my information by googling "Ubuntu SMS Gateway".

---

### Post by Sven6210 on 2010-02-20
Dear Whoopie,

I am able to send SMS however 'Wader' doesn't show me any SMS received. I actually got the information that an SMS was received but unfortunately is can't be shown. The Inbox is always completely empfty. But I can see the contacts saved on the SIM. Really strange to me.

Dear Spazlon,

What is the syntax with 'Gammu' in order to receive and send SMS? I would be grateful if you could send me an example.

Thank you for your help

Sven

---

### Post by Sven6210 on 2010-03-27
I found the solution how to send and receive SMS with the Huawei E160 under Ubuntu 9.10 (and 10.04 beta1) - I use gammu in order to do so.

1. use synatics to install gammu

2. in the terminal window run:

gammu-config

Make the following settings:
Port: (/dev/ttyUSB1)
Connection: (at115200)
Model: ()
Synchronize time: (yes)
Log file: ()
Log format: (nothing)
Gammu localisation: ()

Save the file

3, in the terminal window run:

gammu --identify

This should show that gammu found the Huawei E160. If not there is a problem with the setting above.

Now you can use gammu to send and receive SMS.


**Sending an SMS**
In order to send an SMS enter the following command in the terminal  window:

echo 'Here is the text of your SMS' | gammu sendsms TEXT +1234567890

where +1234567890 is the telephone number


**Reading SMS**
In order to read all SMS on your E160 and the SIM card enter in the  terminal window:

gammu --getallsms


For further details of how to use gammu see:
[http://www.gammu.org/wiki/index.php?title=Gammu:Reference_manual](http://www.gammu.org/wiki/index.php?title=Gammu:Reference_manual)

---

### Post by bushguy43 on 2010-04-07
> **Sven6210 said:**
> I found the solution how to send and receive SMS with the Huawei E160 under Ubuntu 9.10 (and 10.04 beta1) - I use gammu in order to do so.
...


Well I guess if you like the idea of sitting in a Coffee Shop typing command line stuff, then it's solved, but for me command line for something so basic, is a thing of the last century. 

There must be millions of people who use Netbooks and laptops with usb modems. 

I never used to think of Mobile Partner as a great piece of software until I tried to get my Netbook going on Ubuntu. In order to get my E180 USB Modem doing everything that it was capable of doing, (like SIM settings, SMS and records of SMS's) I need several pieces of software, including one for which I have to remember command line syntax. 

I eventually got my HP1001TU  mini working on home wifi (after a command line installation of the wireless card), only to find that it didn't recognise other wifi systems. 

This is an area that seriously needs to be sorted out. I wonder how many people have given up in disgust and gone back to Windows because of this?

---

### Post by alexfish on 2010-04-07
> **bushguy43 said:**
> Well I guess if you like the idea of sitting in a Coffee Shop typing command line stuff, then it's solved, but for me command line for something so basic, is a thing of the last century. 

There must be millions of people who use Netbooks and laptops with usb modems. 

I never used to think of Mobile Partner as a great piece of software until I tried to get my Netbook going on Ubuntu. In order to get my E180 USB Modem doing everything that it was capable of doing, (like SIM settings, SMS and records of SMS's) I need several pieces of software, including one for which I have to remember command line syntax. 

I eventually got my HP1001TU  mini working on home wifi (after a command line installation of the wireless card), only to find that it didn't recognise other wifi systems. 

This is an area that seriously needs to be sorted out. I wonder how many people have given up in disgust and gone back to Windows because of this?


Hi 

You are correct in your statement

However most of this needs to be sorted out By the ISP's and manufactures and not linux

one company via Beta Vine are working towards this aspect with VMC

most of these problems occur when the ISP's over write the firmware and then lock the devices to suit windows, but not all window's , a lot of these devices require firmware updates to work in the windows 7, and to which only to gain a further market share by pandering to microsoft

if the same effort was put into the linux side by these isp's and manufactures then we would heading on a level platform

added one write up of one specific modem

[http://en.wikipedia.org/wiki/Huawei_E220](http://en.wikipedia.org/wiki/Huawei_E220)

---

### Post by pdc on 2010-04-07
hi bushguy;

mate:

gammu is the command-line stuff

[http://www.gammu.org/wiki/index.php?title=Welcome_to_Gammu.org](http://www.gammu.org/wiki/index.php?title=Welcome_to_Gammu.org)

for guys like yourself with better things to do in their day, there is wammu

[http://wammu.eu/](http://wammu.eu/)

wammu is the graphical front-end; so you just click the buttons and fire off texts to your heart's content ...

here are some screen-shots

[http://wammu.eu/screenshots/](http://wammu.eu/screenshots/)

you can even change the colours if the bright Queensland sun is just too much;

---

### Post by bushguy43 on 2010-04-09
> **pdc said:**
> hi bushguy;

mate:

gammu is the command-line stuff

[http://www.gammu.org/wiki/index.php?title=Welcome_to_Gammu.org](http://www.gammu.org/wiki/index.php?title=Welcome_to_Gammu.org)

for guys like yourself with better things to do in their day, there is wammu

[http://wammu.eu/](http://wammu.eu/)

wammu is the graphical front-end; so you just click the buttons and fire off texts to your heart's content ...

here are some screen-shots

[http://wammu.eu/screenshots/](http://wammu.eu/screenshots/)

you can even change the colours if the bright Queensland sun is just too much;

It would be great if I could even get it to recognise my E180. I even tried command line with Gammu and it doesn't find it. Wammu finds the E180 (it produces it on a list) but when I select it, it says "Device not found". That's the same whether or not it's connected to the network. 

It connects ok, but I have the same problem as Sven. I need to access the SMS's in order to recharge my credit etc.  

I realise that it's not the fault of Linux or Ubuntu. The ISP has nothing to do with it. For one thing, I use an unlocked modem. I have been using Mobile Partner on Windows, which I installed myself. That's supplied by Hua Wei.  There is just nothing available right now to get my Netbook fully functional on Ubuntu using Mobile Broadband, and from what I see, nothing on Lucid either. 

My only option is to use my wife's netbook (which is still on Windows) to recharge and just forget about my 500 free sms's.

My other computers are all on Ubuntu, and  I love it. It's a pity that it's just this one issue that prevents me from going 100% Ubuntu.

---

### Post by pdc on 2010-04-09
the nearest package has probably been VMC by vodafone;

[https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

their developers have worked hard to craft packages for differing linux distros;

I think they were pulling their hair out by mid 2009; and said they were not supporting ubuntu; it is about 1MB to download; and I am told it is happy with providers other than vodafone: the programme does not discriminate;

they suggest installing 3 packages; 
ozerocdoff to flip option modems
usb_modeswitch to flip most other modems; .. then ..
their vmc package

I installed it on our Xandros EEE and it worked well then; I (and the initial Eee) have moved on, and I ain't tried vmc recently; it does allow sending and receiving of txts

Liam Green-Hughes has written a blog

[http://www.greenhughes.com/content/vodafone-mobile-connect-ubuntu-netbooks](http://www.greenhughes.com/content/vodafone-mobile-connect-ubuntu-netbooks)

[http://www.betavine.net/bvportal/resources/datacards/netbooks/eeepc](http://www.betavine.net/bvportal/resources/datacards/netbooks/eeepc)

Liam comments

> *Despite its name, you don't have to be a Vodafone customer to use it, in fact I've been testing it out with my 3 UK account*. 

---

### Post by Sven6210 on 2010-04-22
I have also tried 'wammu', the graphical version for 'gammu'. Well, in the end I was able to send an SMS but it was much slower and less reliable. Actually I send my SMS twice because I first through it did not work.

With 'gammu' in the command line it works much better, at least I get a direct feedback whether it worked or not. And I receive the SMS much faster on my mobile phone.

Summary:
I prefer using 'gammu' when sending or receiving SMS

And no, I do not mind using the command line when sitting in a coffee bar. The command line might not be as fancy as a GUI tool (or an iphone) - but who cares? And for 5 seconds I feel like an IT pro, being independent grom GUIs ;)

---

### Post by sgurminder on 2010-09-22
> **Sven6210 said:**
> I found the solution how to send and receive SMS with the Huawei E160 under Ubuntu 9.10 (and 10.04 beta1) - I use gammu in order to do so.

1. use synatics to install gammu

2. in the terminal window run:

gammu-config

Make the following settings:
Port: (/dev/ttyUSB1)
Connection: (at115200)
Model: ()
Synchronize time: (yes)
Log file: ()
Log format: (nothing)
Gammu localisation: ()

Save the file

3, in the terminal window run:

gammu --identify

This should show that gammu found the Huawei E160. If not there is a problem with the setting above.

Now you can use gammu to send and receive SMS.


**Sending an SMS**
In order to send an SMS enter the following command in the terminal  window:

echo 'Here is the text of your SMS' | gammu sendsms TEXT +1234567890

where +1234567890 is the telephone number


**Reading SMS**
In order to read all SMS on your E160 and the SIM card enter in the  terminal window:

gammu --getallsms


For further details of how to use gammu see:
[http://www.gammu.org/wiki/index.php?title=Gammu:Reference_manual](http://www.gammu.org/wiki/index.php?title=Gammu:Reference_manual)
=================================

Thanks a lot. It works like breeze !

-Gurminder:KS

---

### Post by pjrodz on 2010-10-11
> **sgurminder said:**
> =================================

Thanks a lot. It works like breeze !

-Gurminder:KS

thanks guys! it worked for me too! :)

---

### Post by Sven6210 on 2010-12-12
Good to see that there are some more Ubuntu users not minding to use the command line ;)

Actually I admit that I bought a new device, the Huawei E5830 which is a 3G modem combined with a WiFi hub. This way I can connect several laptops with the WiFi hib and they share one 3G connection. And that device even has an web-based admin tool to send and receive SMS. A great solution, especially for Linux users as you do not need to worry about compatibility at all as long as WiFi works.

Best regards

Sven

---

