---
title: "ZTE MF112 (3 Mobile Broadband) mounting as a CD"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by JBUK79 on 2010-07-10
Hi all,

I bought the MF112 mobile broadband dongle from 3 and I'm pleased to say it worked pretty much straight out of the box!

The only problem, well minor annoyance, is that as described here..

[http://ubuntuforums.org/showthread.php?t=1461523](http://ubuntuforums.org/showthread.php?t=1461523)

.. it detects as a CD drive which must be ejected before you can use it as a modem.

When running Windows it does the same, and autorun kicks in to install the 3 software, so it's clearly down to the on-board storage.

My question is this.. is there any way to stop it detecting as a CD drive?

My experience so far with Ubuntu tells me pretty much anything is possible with enough time and effort but I'm hoping I'm missing something and someone out there has a simple fix for this!

I've been using Ubuntu for over 3 years now but I still feel like a beginner sometimes when it's something I haven't come across before :) 

Edit: Just to add that the on-board storage it mounts is read-only.

Thanks & regards,

John

p.s.

A word of warning to anyone else thinking of buying this, you WILL need access to either a Windows/Mac machine, an equivalent VM, or a local 3 store to retrieve your 'My3' password (for top-ups etc) as it can only be retrieved by using the 3 software. A slight pain, but takes seconds ;)

---

### Post by ieee488 on 2010-07-10
see if usb-modeswitch will work for you

---

### Post by pdc on 2010-07-10
sorry to hear this is not working for you John;

my reading of this thread

[http://ubuntuforums.org/showthread.php?t=1461523](http://ubuntuforums.org/showthread.php?t=1461523)

was that usb_modeswitch maybe was not needed

what does 

> lsusb give you when you plug this device in?

I guess we are assuming you are running 10.04 but maybe

> **I've been using Ubuntu for over 3 years now**

an older version?

If your result gives you 

> 19d2:2000

GeorgeVita, a bit of a guru, would say to create a udev rule

(it works well for me with these ZTE devices)

> sudo gedit /etc/udev/rules.d/zte_eject.rules

that creates an empty file called zte_eject.rules

and into it paste

> SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule" 

Save. Close.

reboot; your modem should go red; blue; light disappear; red changes to blue as the device gets recognised and lsusb now should give you 

> 19d2:0031

---

### Post by JBUK79 on 2010-07-11
Thanks for the advice so far guys :)

> an older version?

The first version I used full time was 6.10, but running 10.04 now (fully updated).

lsusb gives me this prior to ejecting the 'cd-rom';

Device 006: ID 19d2:0103 ONDA Communication S.p.A. 

and this once it's ejected and the modem is functional;

Device 007: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636

so I'm guessing try the zte_eject.rules fix replacing 2000 for 0103? I'll try it a little later when I get the chance.

Thanks again :)

---

### Post by pdc on 2010-07-12
> so I'm guessing try the zte_eject.rules fix replacing 2000 for 0103?

Yes, indeed please;

when I look at the usb_modeswitch entry, that details the ID of your device it is indeed 0103 before switching!

We hope it goes well for you

---

### Post by JBUK79 on 2010-07-12
> **ieee488 said:**
> see if usb-modeswitch will work for you

Sorry I was in a rush yesterday and forgot to add that I had tried usb-modeswitch, but it made no difference at all.

Thanks anyway though.

> **pdc said:**
> Yes, indeed please;

when I look at the usb_modeswitch entry, that details the ID of your device it is indeed 0103 before switching!

We hope it goes well for you

Well I'm pleased to say that the zte_eject.rules fix has done the job, the 'cd-rom' still appears, BUT I can use the modem without ejecting it, so I'm happy with that :)

Interesting about the usb_modeswitch entry though, makes me wonder why that didn't work... shame I don't get time to tinker more these days. 

Anyway thanks for the help guys, especially pdc, hope I can return the favour one day :)

---

### Post by pdc on 2010-07-12
delighted to hear the "eject" rules works; enjoy!

(there is some way to mark the thread as SOLVED if you can find it: I have yet to discover how!!)

---

### Post by JBUK79 on 2010-07-12
> **pdc said:**
> delighted to hear the "eject" rules works; enjoy!

(there is some way to mark the thread as SOLVED if you can find it: I have yet to discover how!!)

Now that I can help you with! 

You click the 'Thread Tools' drop-down menu (red text, near top-right of screen), and select 'Mark this thread as solved', once that's done the option changes to 'mark this thread as unsolved' just in case you break it again ;)

---

### Post by t0p on 2010-07-28
> **JBUK79 said:**
> 
p.s.

A word of warning to anyone else thinking of buying this, you WILL need access to either a Windows/Mac machine, an equivalent VM, or a local 3 store to retrieve your 'My3' password (for top-ups etc) as it can only be retrieved by using the 3 software. A slight pain, but takes seconds ;)

Oh dear.  I was planning to buya ZTE MF112 dongle to use on 3 Mobile Broadband, but this p.s has worried me.  So I gotta double-check:

You say I'll need a Windows/Mac machine, an equivalent VM or a local 3 store to retrieve my "My3" password.  Now, I have access to Windows computer at the local community centre; but I'll be running as a bog-standard User, not an Administrator, so I won't be able to install any software: does that mean the community centre computers won't help?  I also have a virtual XP on VirtualBox (not VMWare).  Will that be okay?  Finally, there's a 3 store about 50 miles from where I currently live.  Will I be able to just walk in and tell them what I need to do?  Will they demand proof of ID or anything?  What precisely is it that I need them to do for me?

I need this info before I commit myself to buying the dongle.  Can anyone help?

---

### Post by pdc on 2010-07-28
in which country will you be logging on?

---

### Post by JBUK79 on 2010-07-31
> **t0p said:**
> Oh dear.  I was planning to buya ZTE MF112 dongle to use on 3 Mobile Broadband, but this p.s has worried me.  So I gotta double-check:

You say I'll need a Windows/Mac machine, an equivalent VM or a local 3 store to retrieve my "My3" password.  Now, I have access to Windows computer at the local community centre; but I'll be running as a bog-standard User, not an Administrator, so I won't be able to install any software: does that mean the community centre computers won't help?  I also have a virtual XP on VirtualBox (not VMWare).  Will that be okay?  Finally, there's a 3 store about 50 miles from where I currently live.  Will I be able to just walk in and tell them what I need to do?  Will they demand proof of ID or anything?  What precisely is it that I need them to do for me?

I need this info before I commit myself to buying the dongle.  Can anyone help?

Hi,

Sorry it took me a couple of days to reply, was away for a few days.

I'm afraid the community centre computer won't be any help, you actually have to install the 3 software (the password is retrieved as a text message) :( 

BUT there is seemingly another way, if you have or can borrow a 3 mobile (or at least one you can use on the 3 network) then apparently you can pop the SIM from the dongle into it and retrieve the text that way, I haven't tried it personally but I've heard a couple of people say it does work so worth a shot!

Hope that helps (please post back either way in case anyone else has the same issue!)

Regards,

John

---

### Post by pdc on 2010-07-31
this is all very strange; I get the sense in these last few posts that  ...... some folks are suggesting .... special software of some sort needs to be installed on any linux distro, before folks can use a 3 mobile broadband dongle to access the internet;

this would seem to be completely at odds with a variety of other posts on this forum (that I haven't the time to find and quote ..... )

that seem to suggest a variety of folks have had no problem accessing the 3 network in the UK and Ireland;

and folks report the same for the 3 network in Australia: a Huawei E160 modem works fine there; and one accesses one's 3 account via any old internet browser ......

..... which I have also done successfully .........

so if we get folks to make clear if this belief (that you need *special* software) is what they are trying to say is a fact ..

---

### Post by JBUK79 on 2010-08-01
> **pdc said:**
> this is all very strange; I get the sense in these last few posts that  ...... some folks are suggesting .... special software of some sort needs to be installed on any linux distro, before folks can use a 3 mobile broadband dongle to access the internet;

this would seem to be completely at odds with a variety of other posts on this forum (that I haven't the time to find and quote ..... )

that seem to suggest a variety of folks have had no problem accessing the 3 network in the UK and Ireland;

and folks report the same for the 3 network in Australia: a Huawei E160 modem works fine there; and one accesses one's 3 account via any old internet browser ......

..... which I have also done successfully .........

so if we get folks to make clear if this belief (that you need *special* software) is what they are trying to say is a fact ..

No offence but you seem to have misunderstood what we're talking about...

It's not that special software is required on *nix systems, it's that 3's software only works on Windows/Mac OS. 
To use the ['My3']("https://my3.three.co.uk/mylogin//login?service=https://my3.three.co.uk/myaccount/index.jsp") online services (check balance & usage, top-up, etc) you need a password which is sent as a text message, there's no way to send it to an alternate number or e-mail address, so hence you either need access to Windows/Mac OS to install the software, to visit a 3 store with the modem, or put the sim in a mobile phone that can connect to the 3 network to retrieve it.

Not having the password doesn't affect connecting to the internet, it just means you can't make use of the on-line services unless connected via the dongle, even then you still need the password for some things.

I'm not sure if this just a UK thing or not (I'm based in England) but it's certainly the case for myself and several other people I know who recently signed up.

Hope that cleared things up a little (and didn't confuse things further, lol)

John

---

### Post by alexfish on 2010-08-01
> **JBUK79 said:**
> No offence but you seem to have misunderstood what we're talking about...

It's not that special software is required on *nix systems, it's that 3's software only works on Windows/Mac OS. 
To use the ['My3']("https://my3.three.co.uk/mylogin//login?service=https://my3.three.co.uk/myaccount/index.jsp") online services (check balance & usage, top-up, etc) you need a password which is sent as a text message, there's no way to send it to an alternate number or e-mail address, so hence you either need access to Windows/Mac OS to install the software, to visit a 3 store with the modem, or put the sim in a mobile phone that can connect to the 3 network to retrieve it.

Not having the password doesn't affect connecting to the internet, it just means you can't make use of the on-line services unless connected via the dongle, even then you still need the password for some things.

I'm not sure if this just a UK thing or not (I'm based in England) but it's certainly the case for myself and several other people I know who recently signed up.

Hope that cleared things up a little (and didn't confuse things further, lol)

John

have you tried wammu

---

### Post by JBUK79 on 2010-08-01
> **alexfish said:**
> have you tried wammu

I'd forgotten about that app!

A friend of mine couldn't get it to work under 9.10, but I just installed it and tested under 10.04 and after running the manual configuration wizard it's working fine.

So ironically (considering the last few posts) you do need additional software to retrieve the text, but at least it's free and easy to use! :D

John

---

### Post by David_Eeee on 2010-08-04
I've just got an Mf112 with the hope of getting it working by Friday on an EeePc - I'll apologise to the thread now the EeePC is still on the original Xandros/Debian variant, but as this is the only current forum I could find that seems to have success with the MF112 under linux I hope you might have answers to a couple of questions :

1) Does anyone know if the MF112 is very different from MF6?? - as the eeePC forums have a fix for that which might work, if the modem driver is transferable. (Not as smooth as it seems to be for you with Xandros, I'll have to write my own udev rule for dismounting the CDROM and mounting the Modem without disabling automount for all other USB devices) Thankyou to the thread for answering my first query - the device numbers for the MF112 in pen drive and modem mode was eluding me this morning, and now I know to look for 0103 and 0031.

2) Otherwise my options are 
- get an unlocked E220 modem - which I'm assured works out of the box on the Eee
- load ubuntu on to the Eeee 901 (A silly question on this forum I know)
- get a linux MF112 modem driver and seehow I get on - I'm sure that at that level most of  the linux and some of the Mac bits are transferable - I've no interest in the My3 fancy stuff - just a basic connection to the net would do.

Incidentally I have had catastrophic problems in the past with the new wave of clever USB devices, that load virtual CDroms - In particular a portable harddrive that a client gave me some data on caused major problems on the XP laptop (major data loss and system crashes) while the Linux one was more robust but not unscathed, and I'm getting similar symptoms with the MF112 on Linux - on loading the USB automount is disabled until reboot - so a way of disabling all automatic CDrom imitators would be a very useful byproduct of this exercise.

David

---

### Post by pdc on 2010-08-05
if you wish to work on the Xandros Eee, liam green-hughes has written various things eg

[http://www.greenhughes.com/content/zte-mf627-easy-way](http://www.greenhughes.com/content/zte-mf627-easy-way)

........... I would have thought that the latest usb_modeswitch version on its own would do all this:

get it from here

[http://packages.debian.org/squeeze/usb-modeswitch](http://packages.debian.org/squeeze/usb-modeswitch)

go half-way down the page: version 1.1.3-1 and use the i386 

right-click on file as Liam shows at the top of another of his how-tos

[http://www.greenhughes.com/content/huawei-e169g-easy-way](http://www.greenhughes.com/content/huawei-e169g-easy-way)

and that should switch the device, and you should ...be able to configure

---

### Post by rickbeton on 2010-08-14
Thanks folks: the advice above worked for me.

I'll summarise what I did here for the benefit of others:

1. I purchased a '3' ZTE MF112 dongle

2. I plugged it in. **lsusb** gives 19d2:0103

3. 
* **sudo aptitude install usb-modeswitch**
* **sudo gedit /etc/udev/rules.d/zte_eject.rules**
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="0103", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"

4. reboot

5. **lsusb** gives 19d2:0031

6. Using NetworkManager > Edit Connections... > Mobile Broadband, I set up the dongle to access 3's network.

I can now connect whenever I plug in the dongle, provided there is good mobile coverage.

Rick

---

### Post by PaulW21781 on 2010-10-23
> **rickbeton said:**
> Thanks folks: the advice above worked for me.

I'll summarise what I did here for the benefit of others:

1. I purchased a '3' ZTE MF112 dongle

2. I plugged it in. **lsusb** gives 19d2:0103

3. 
* **sudo aptitude install usb-modeswitch**
* **sudo gedit /etc/udev/rules.d/zte_eject.rules**
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="0103", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"

4. reboot

5. **lsusb** gives 19d2:0031

6. Using NetworkManager > Edit Connections... > Mobile Broadband, I set up the dongle to access 3's network.

I can now connect whenever I plug in the dongle, provided there is good mobile coverage.

Rick

I found the above would also prevent me from mounting and using any inserted SDCard while using the stick.  A quick dirty fix (for me) was to use this line in the rule instead:

SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="0031", RUN+="/usr/bin/eject /dev/sr1", OPTIONS+="last_rule"

That way, instead of ejecting %k (which would be any inserted device on that interface) it will now only eject SR1 which relates to the CDDrive emulation, and leave the memory card access fine.

Not sure how SR1 will change with other devices plugged in using the SR tree, will need to see, but... it works for me, so thought I'd post up incase others want to use the stick for both storage and net access.

---

### Post by RussellEngland on 2010-10-25
Brilliant!!! Worked for me, many thanks

---

