---
title: "Wifi on HP 6000"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by johkep on 2012-05-24
Good day,
A quick search turned up only four threads related to my issue, none of which were similar to my issue.  In short, wifi that works on my hp 6000 with maverick meerkat just fine does not work when I try to upgrade to a later version.

I have tried fresh installing 11.04 and 11.10.  Both load the same broadcom sta wireless driver that 10.10 loads but for some reason it does not allow wireless internet.  So I reinstalled 10.10, got the wireless going as usual and then tried doing an upgrade of my existing system figuring the working settings and configuration under 10.10 will somehow magically transfer to 11.10.  No such luck.  

I am a former mac os x 10.5 user and have limited windows experience.  I have no fear of getting in the terminal and typing like a fiend but I would like to have some idea of what I am doing first.  Any help is appreciated.  Thank you...

---

### Post by chili555 on 2012-05-24
Let's start by identifying your wireless card. Please open the terminal and run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by johkep on 2012-05-24
Thank you Chili555  Here is my terminal data...

jon@jon-HP-Pavilion-dv6000-RP297UA-ABA:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

FWIW, the 0280 that is in the brackets did come up as a red font in the terminal screen.  Not sure if that is of consequence or not but I figured I should at least mention it.

Again, thank you for your help...

---

### Post by chili555 on 2012-05-24
You need some firmware. If you have an ethernet connection, please do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -r b43
sudo modprobe b43
```Detach the ethernet and your wireless should be working.

---

### Post by johkep on 2012-05-25
Thank you for the instructions on the firmware update.  Given that I am currently running 10.10 with wifi without issue, will this firmware update upset that compatibility?  Should I do the 11.10 install again and then do the firmware update or am I safe to do it now running 10.10?  Thanks in advance for your help...

---

### Post by chili555 on 2012-05-25
It's all up to you. If you are comfortable, stick with 10.10. If I were going to update, I'd go for the latest, 12.04. If your card is working well, that means you have the firmware in 10.10. It will be located in /lib/firmware/b43. You could copy the entire folder to a USB key and then transfer it to your newer install when done.

There is no need to run the firmware commands if your wireless is running now.

---

### Post by johkep on 2012-05-25
Thanks for the feedback.  First off, yes, I would like to upgrade to 12.04.  Wifi works fine under 10.04/10.10 using the broadcom sta wireless driver.  Under 11.04/11.10/12.04 the driver is still loaded during installation but the wifi never starts working.  I even tried just upgrading from 10.10 to 11.10 to see if that would help and it did not.  Your recommendation to update the firmware would make sense with the wifi not working on the new OS.  Since I am currently on 10.10, should I update now or wait for to run it after I install the newer OS?  Also, would the firmware update disrupt my current configuration from working?  Sorry to be a pain about this, just trying to understand.  Again, thank you so much for your time, advice, and most of all, your patience.

---

### Post by chili555 on 2012-05-25
> Wifi works fine under 10.04/10.10 using the broadcom sta wireless driver. Are you sure? 14e4:4311 is a device that works well with b43, ssb and firmware and not well at all with STA. Let's check:```
sudo lshw -C network
```

---

### Post by johkep on 2012-05-25
Here is what came out...


jon@jon-HP-Pavilion-dv6000-RP297UA-ABA:~$ sudo lshw -C network
[sudo] password for jon: 
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:23:93:c5
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.103 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:ea:18:b1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)

---

### Post by chili555 on 2012-05-25
> *-network
description: Wireless interface
product: [COLOR="Red"]BCM4311 802.11b/g WLAN[/COLOR]
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth1
version: 01
serial: 00:1a:73:23:93:c5
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]driver=wl0[/COLOR] driverversion=5.60.48.36 ip=192.168.1.103 latency=0 multicast=yes wireless=IEEE 802.11bg
resources: irq:16 memory:d6000000-d6003fffOld Chili has a big bump on his head because he just fell out of his chair. Your case is one in a hundred.

When you update, hook up the ethernet temporarily and do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Detach the ethernet and enjoy your wireless. If it doesn't work, for some reason, try:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -r b43
sudo modprobe b43
```I shall be fascinated to hear the result!

I never fight momentum.

---

### Post by johkep on 2012-05-25
Thank you sir and will do.  I will PROBABLY do this tomorrow but I MAY wait until Monday.  You see the Grand Prix of Monte Carlo is simulcast by Sky Sports over the web and I have been kind of an F1 nut since the mid 60's.  Yep, I'm THAT old.  So Monday for certain, tomorrow maybe.  As soon as I do it I will certainly let you know.  Just curious, when you say one in a hundred, would you mind a brief description of what you are referring to that maybe even an old Mac user could understand?  Thank you sir!  :)

---

### Post by chili555 on 2012-05-25
I'll be watching Monaco, too. But then I'll follow up with the Indy 500 and the NASCAR's 600 miler; just 1400 miles of racing in one day. That's a lot of beer, potato chips, salsa, popcorn and peanuts!

You are one in a hundred because 99% of the Broadcom 4311s I ever see work with b43, ssb and firmware. Only yours, so far, does not, but works perfectly with the STA driver instead.

---

### Post by johkep on 2012-05-25
Same here.  But after Monaco is over I'll probably be doing the big upgrade.  I think Indy is on ABC and World 600 on Fox.  A big day for burning rubber and beer and chips!  I used to live in NC and went to Charlotte, Rockingham, and Darlington like all the time from about 1981-90.  Oh yeah, add a trip or two to Talladega in there as well.  Thanks again for your time, attention, and patience.  Probably turn up sometime Sunday afternoon...

---

### Post by johkep on 2012-05-28
Chili555, rub that spot on your head for good luck.  I upgraded to 12.04 and did the first instructions you mentioned.  No change, not even after a reboot.  Did the second one and Bingo!  We is talkin'!  You  rock dude, that is all I gotta say.  Now, if you don't care, could you give me in three or four sentences, using low grade geek speak, just what the hell I did and why it now works?  Thanks friend and if this is like ebay and there is a way I can give you a public kudo, you'll have to tell me how to do that as well.  But that is ok.  At least I have shown that I can follow instructions!  :D

---

### Post by chili555 on 2012-05-28
Awesome! Glad it's working.> Now, if you don't care, could you give me in three or four sentences, using low grade geek speak, just what the hell I did and why it now works? You didn't have bcmwl-kernel-source by  default, so trying to remove it did nothing. However, installing b43-fwcutter and firmware-b43-installer downloaded and installed the firmware that b43 needs to work properly.> a way I can give you a public kudo,You can use thread tools at the top and mark Solved. Please enjoy your Ubuntu experience!

---

### Post by allegrashelley on 2012-10-29
> **chili555 said:**
> Old Chili has a big bump on his head because he just fell out of his chair. Your case is one in a hundred.

When you update, hook up the ethernet temporarily and do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Detach the ethernet and enjoy your wireless. If it doesn't work, for some reason, try:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -r b43
sudo modprobe b43
```I shall be fascinated to hear the result!

I never fight momentum.



-----------------------------------------------------------
Dear Ubuntu Wisemen and Wisewomen::-({|=:redface:](*,)

Please accept my apologies for my ignorance & prepare yourselves for a truly inept Ubuntu user.  I've never been in a forum before, I am guessing at protocol--I hope that doesn't make me lazy--and I am one of those people who maybe shouldn't use Ubuntu due to lack of technical skill.  There is my apology/disclaimer, I hope someone is still reading along!

I am terribly worried that my excessive use of words will put people off--please stick with me! 

**PC**: HP Pavilion dv6000 (that identifies the first prob. right?)
**Major issue**: Wi-fi access is no good.
**WHY?**  From reading through the forums and blindly trying to fix the problem without help I have come up with ***some*** possible places to begin. 

1. Does the laptop recognize the wi-fi card.
   How do I find out if it recognizes the wi-fi card.
2. ARE there any wi-fi drivers installed? 
   I THINK broadcom is installed but alas I do not know what that
   means or how to determine if it is working or compatible or if 
   all my tweaking has caused some configuration "clashes". 
   How will I determine the answer to these questions and how 
   best to address them?
3. Could the Wi-fi recognition have been wiped out when Windows
   was wiped off the hard drive?  (I sort of wiped Windows by 
   happy accident.)  
4. When I run the "additional drivers" wizard I get only drivers
   for the Nvidia graphics card.  Is this "normal"?  Surely this indicates that broadcom is . . .
   well I saw it earlier today in among some files, but nothing when I search for additional drivers.
   If broadcom is present I installed it via-argh I can't remember what the other software service is
   called!  Its far too advanced for me to be using, I took a chance.  Really want to just start over
   but with expert help to guide me along!

I think that is a good place to start.  So-no windows on this machine but I do have Wine installed.  I just don't know a thing about unzipping and extracting and where to find zip files or the best utility for unzipping and extracting.  What I am saying is I am afraid I am going to have to be spoken to like a 10 year old.  I would have written 12 year old but I am sure that "in this day and age" (said the old person who has no business using Ubuntu) that a 12 year old knows how to extract and unzip files!  

Right then--any help--and DO be nice as I am very sensitive about my ignorance--it would just be SO nice to FIX something on the PC myself and learn how to use Linux a bit better.  The whole concept behind Ubuntu is brilliant.  I would like to make sure I know how to use it properly so I can encourage others to do the same!

Thanks so much for your help!
Oh--do I need to mention that this is an European PC in case the functions are diff. than other editions?  Well--it is European.;)

---

### Post by chili555 on 2012-10-29
> 1. Does the laptop recognize the wi-fi card.
How do I find out if it recognizes the wi-fi card.Let's ask the computer for a listing of PCI devices and filter them down to wireless network cards. Please open a terminal and run and post in your reply:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.> 2. ARE there any wi-fi drivers installed?
I THINK broadcom is installed but alas I do not know what that
means or how to determine if it is working or compatible or if
all my tweaking has caused some configuration "clashes". We'll figure that out after we know what card you have. It is, indeed, a common error; excusable in new users. That's why I live and breathe.> 3. Could the Wi-fi recognition have been wiped out when Windows
was wiped off the hard drive?Not very likely, but I never get over being shocked at what can happen. I'd say the chances a wipe also wiped wireless is 0.01%. > 4. When I run the "additional drivers" wizard I get only drivers
for the Nvidia graphics card. Is this "normal"?Sure, if you have already installed the wireless driver or none is available to download.> and DO be nice I will do the very best I can. I promise.

All of us were new at one time. Even me. I have turned my empathy knob up to eleven.

---

### Post by allegrashelley on 2012-10-29
> > **chili555 said:**
> Let's ask the computer for a listing of PCI devices and filter them down to wireless network cards. Please open a terminal and run and post in your reply:```
lspci -nn | grep 0280
```
[QUOTE]

Sorry for the double quote-I'm learning!  
-The above command produced another command line--meaning there was no output what so ever.

> The pipe symbol | is on the right side of my US keyboard on the same key with \.

 Now I did cut and paste as every time I've tried to use that silly pipe symbol-with ctrl, with shift, with alt, with alt gr or any combination there of-it doesn't appear.  I will go back and try again.  One does not learn whilst being led by the nose!

> We'll figure that out after we know what card you have. It is, indeed, a common error; excusable in new users.That's why I live and breathe.

Thank you, you are indeed a gentleman!  

 Not very likely, but I never get over being shocked at what can happen. I'd say the chances a wipe also wiped wireless is 0.01%.

> 4. When I run the "additional drivers" wizard I get only drivers
for the Nvidia graphics card. Is this "normal"?
 Sure, if you have already installed the wireless driver or none is available to download.

This "none is available to download" concerns me-unless it means a drive is already present.  However, the fact that nothing shows up when I run the command makes me worry even more. :confused:
I will do the very best I can. I promise.



> Quote:
and DO be nice
I will do the very best I can. I promise.

All of us were new at one time. Even me. I have turned my empathy knob up to eleven.[/QUOTE]

As I said, you are indeed a gentleman!  So - - - next step? Oh I do hope there is a next step!

---

### Post by chili555 on 2012-10-30
Let's dig deeper:> lspci -nnPost anything that may slightly resemble a network card. Also run:```
lsusb
lshw -C network
```> This "none is available to download" concerns me'Additional Drivers' only has drivers for a very few wireless cards. A great number of cards' drivers are all ready built in. No worries.

---

### Post by chili555 on 2012-10-30
> every time I've tried to use that silly pipe symbol-with ctrl, with shift, with alt, with alt gr or any combination there of-it doesn't appear.You don't need any of that. Just go over to the key with \ on it, press Shift and the key and it should appear. Please see attached.

As your computer is Euro, it may be in a different spot.

---

### Post by allegrashelley on 2012-10-30
> > **chili555 said:**
> Let's dig deeper:Post anything that may slightly resemble a network card.




**Result:** I may have repeated two lines, however I suspect you can find your way around without too much difficulty!

NVIDIA Corporation C51 Host Bridge [10de:02f0] (rev a2)

PCI bridge [0604]: NVIDIA Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: NVIDIA Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
VGA compatible controller [0300]: NVIDIA Corporation C51 [GeForce Go 6150] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: NVIDIA Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: NVIDIA Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: NVIDIA Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: NVIDIA Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB controller [0c03]: NVIDIA Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB controller [0c03]: NVIDIA Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: NVIDIA Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: NVIDIA Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: NVIDIA Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: NVIDIA Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]




[QUOTE] Also run:[CODE]lsusb

Well will you look at that-TWO partitions full of Ubuntu-there was a third as well-my mobile phone!  I left that bit out!:P

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



> lshw -C network
I think this is where we start to run into trouble, perhaps?
PCI (sysfs)

Yes-that is ALL there was to it!  There was no more information other than those 8 letters and two symbols.  There is simply nothing there!  Poof!  This is why I think there could be trouble!

And Chili-thank you once again for your help!  I did find that particular symbol we discussed-top right of keyboard next to the back space button on mine plus where you mentioned-worked fine yesterday-today, no luck!  Of course yesterday was actually 4 a.m.  - . . . Was glued to the telly & PC following the hurricane. Will check your instructions again. 

Cheers!:)

---

### Post by allegrashelley on 2012-10-30
> **chili555 said:**
> You don't need any of that. Just go over to the key with \ on it, press Shift and the key and it should appear. Please see attached.

As your computer is Euro, it may be in a different spot.
Right-I would post a pic of my keyboard to show you where the pipe symbol is but the PC does not recognize my phone properly.  Remember, I brought this PC back from the dead-the graphics card still sometimes freezes up, for lack of a better word.  In any case, top left of keyboard with the § and the ¦ and the ½ symbol-which actually doesn't work from that location! ;-) What a fascinating phenomenon is HP computing.  

Ta!

---

### Post by chili555 on 2012-10-30
> I think this is where we start to run into trouble, perhaps?
PCI (sysfs)It often takes a few moments. Please try again and wait...wait until it either coughs up something useful or comes back to the command prompt.

So far, we see nothing that is a wireless device. We *DO* see an ethernet device which uses the driver *forcedeth* (aka by Chili as 'Forced Death'):> NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)Therefor, *lshw* ought to produce a result.> Remember, I brought this PC back from the deadI wonder if the wireless device is still dead. So far, it has resisted all efforts to identify it.

---

### Post by allegrashelley on 2012-10-30
> > **chili555 said:**
> It often takes a few moments. Please try again and wait...wait until it either coughs up something useful or comes back to the command prompt.

Its always simply returned to the command prompt.  Quite rude I think!

[QUOTE](aka by Chili as 'Forced Death'):Therefor, *lshw* ought to produce a result.

I've given it the same name-works in code speak! 
If it SHOULD produce a result-then I am anxious to discover which or what result(s) we uncover.  How or what would cause it to disappear.:confused:  Thus my theory that it wiped with Windows.  I mean you never can tell with an HP what will be there one day to the next.  Sorry-I'm too chatty to be any good at forums!

> I wonder if the wireless device is still dead. So far, it has resisted all efforts to identify it.[/QUOTE]

Exactly!

---

### Post by chili555 on 2012-10-30
>  How or what would cause it to disappear. Electrical failure as a result of old age, I'd guess. Heat in laptops cooks, in particular, capacitors fairly regularly.

You could try a live CD of Ubuntu or any other Linux distribution to see if it's recognized elsewhere. You could look up the maintenance manual for your laptop on line and see if the wireless card is easily replaceable, as it is in both my Lenovos, and consult Ebay. Or you could find any of several inexpensive USB wireless devices by checking this forum for the many posts asking about 'works out of the box' wireless cards. 

If your laptop doesn't even know it has a wireless card, I don't think there is much else we can do.

Is there any option to enable/disable wireless in the BIOS?

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&lang=en&rule=4003&product=500515&docname=c00273322](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&lang=en&rule=4003&product=500515&docname=c00273322)

---

### Post by allegrashelley on 2012-10-30
Right-it was as bad as I feared then.  At least I know what to do next and that I can stop trying to find out what happened to the wifi driver. 

Thank you again for all your help-your empathy switch was on a good setting!  Have a lovely week!

---

