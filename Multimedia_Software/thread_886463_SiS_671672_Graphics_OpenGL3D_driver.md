---
title: "SiS 671/672 Graphics: OpenGL/3D driver"
date: 2008-08-11
forum: Multimedia Software
---

### Post by rekado on 2008-08-11
related to:
[http://ubuntuforums.org/showthread.php?t=615094](http://ubuntuforums.org/showthread.php?t=615094)


I haven't heard of a single Linux user who would have installed the 3D drivers for the SiS 6717&72 Mirage 3 graphics chip.

Mr. Barros Lee of SiS in Taiwan wrote the 3D driver and internally released it, however, SiS refuses to publish the driver to end-users (that's us) but allegedly only gives it to mainboard manufacturers. I asked the manufacturer of my wife's laptop (Haier, a big Chinese consumer electronics comapny), but they didn't know of a driver for Linux. Mr. Lee is not allowed to release the driver himself; only a 2D driver can be sent to end-users which - in my case - performs pretty badly.

As there is no way of getting the driver at the moment and most probalby neither in the near future, I thought we should try to **build it ourselves**.

I've got no experience whatsoever in programming drivers, but I have been working as a software developer for a while now and am experienced in microcontroller programming. I don't know what is required to write a driver for the chip, but I would like to volunteer for working in a team of people who know more.

Is there anybody willing to participate? If you've got any information that could be helpful in the process please post it. If you've got a machine with this chip you could volunteer as a tester.

I don't know if anything usable will come out of this idea, but I really hope we will be able to solve this problem.

Rekado

---

### Post by soxs on 2008-08-11
Doing such a project requires _A_ _LOT_ of knowledge, though only a very minor minority suffers from the lack of a sis graphics driver.
I would suggest to:
A) start a petition
B) ask canonial to ask the guy who wrote the driver
BEFORE trying to rebuild it yourself, which will take plenty of tie and resources.. with variang success, not being guuarantied at all..

---

### Post by rekado on 2008-08-12
I once read that it's a myth that only rocket scientists can develop graphic drivers... but I sure agree with what you've said: it is a lot of work requiring a lot of knowledge.
From what I've learnt SiS would want a significant amount of money to be paid for the driver - would Canonical be likely to get this driver when it seems that not even the mainboard manufacturers (who should be able to get it) got it?
Should I just write an email to Canonical? I wish I could know how many Linux users actually would benefit from the driver.

---

### Post by soxs on 2008-08-12
I am not sure about what to do, but you might file a bugreport explaining what would be required to do... can't of anything else at the moment..

---

### Post by dub_u on 2008-08-12
> **rekado said:**
> I wish I could know how many Linux users actually would benefit from the driver.

Hi, I would be more than happy if this "mystery" 3D driver of Barros Lee's came out of the darkness and available for the public use.
And as far as I have checked this forum, there is quite a lot of people who would benefit from the driver.

---

### Post by rekado on 2008-08-13
Asking Canonical seems to be a bit difficult (I know, if that is considered difficult how should we start writing a driver on our own...) - there is no contact address that would seem appropriate for our request.

A bugreport would not help much, this is not even a feature request. Actually we would just like to have someone pay for getting the driver and including it in following Ubuntu versions.

Barros Lee said that he is not allowed to release any hardware specifications of the chip, so writing a driver could be even more difficult than it is already...

---

### Post by soxs on 2008-08-13
You may try the first address you can find for canoncial, you may get further info where to go...

---

### Post by dub_u on 2008-08-14
> **soxs said:**
> You may try the first address you can find for canoncial, you may get further info where to go...

I agree with rekado, reading the following @ canonicals contact page.

> Please try and find the right channel for your enquiry. We do try and respond to all requests but due to volume we can only reply to requests received in the correct relevant channels. All requests should be in English if possible.

And the only available email address is to webmaster :(

---

### Post by rekado on 2008-08-15
I indeed sent an email address to the webmaster - not with the actual request but with the request for the appropriate contact data. Isn't that (remotely) connected to the webpage if we can't find the proper communication channel...?
Hope to receive a reply.

On the other side I'm still working on getting the driver through manufacturers. I just wrote to Barros Lee again, telling him about the disappointing reply I received from the service guys at Clevo Germany (the Taiwanese service didn't reply, probably because they cannot read simplified characters that well...). He told me before that he is almost sure that Clevo has the driver. Here an excerpt of his mail:

&#25105;&#26377;&#25910;&#21040;Clevo &#23492;&#32102;&#25105;&#30340;&#20449;&#65292;&#25105;&#24050;&#32147;&#23559;&#20182;&#36681;&#23492;&#32102;&#25105;&#32769;&#38342;&#36319;&#30456;&#38364;&#30340;&#20154;&#65292;&#25818;&#35498;&#20182;&#20497;&#24050;&#32147;&#26377;&#35531;&#21488;&#21271;&#30340;Clevo &#36319;&#20182;&#20497;&#25509;&#35320;&#12290;

"I again *{maybe a typo in the original text}* received a mail sent by Clevo; I already forwarded it to my boss *{not sure about that passage}* and he said that he already asked Clevo Taipei (Taiwan HQ) to get in touch with them."


&#25105;&#20063;&#35258;&#24471;&#24456;&#35079;&#38620;&#65292;&#26126;&#26126;&#26159;&#24456;&#31777;&#21934;&#30340;&#20107;&#24773;&#65292;&#28858;&#20160;&#40636;&#25630;&#37027;&#40636;&#35079;&#38620;&#19968;&#23652;&#21448;&#19968;&#23652;&#12290;&#25105;&#19981;&#20171;&#24847;&#24171;&#24537;sis &#23492;driver &#32102;end user&#65292;&#21487;&#26159;sis &#23601;&#19981;&#35731;&#25105;&#20570;&#8230;

"I also feel it's somehow very complicated; actually it is such a simple thing, so why do they have to make it so complex with one layer and yet another layer... I wouldn't mind to help SiS to send out the driver to end-users but SiS just won't let me do it..."


This could mean that with some luck the driver is somewhere available through Clevo support if they manage to share their knowledge. I will send an email to Clevo Taipei once again, this time with traditional characters (can't even read them), and hope I can get a reply clearing things up a bit.

Please don't set your hopes high on this (but I sure do)...

---

### Post by dub_u on 2008-08-15
You're right, it is a website matter that there isn't any email for miscellaneous questions.


> Please don't set your hopes high on this (but I sure do)...

Can't help myself... I do to  :) 

Good work so far, Rekado

---

### Post by Jdm111 on 2008-08-15
I have the sis 650 and i cant use zattoo because of the lack of 3D driver.

---

### Post by gandaran on 2008-08-15
> **Jdm111 said:**
> I have the sis 650 and i cant use zattoo because of the lack of 3D driver.

I too have a IGP graphics SIS 650 and as far as I know it doesn't support 3D even on windows xp with windows sis drivers.

edit.
    I just visited zattoo.com and everything seams to work, except the player I'm still waiting to download as my location is not yet supported, there's nothing there to do with 3d graphics.

---

### Post by majeru on 2008-08-19
Hello,

I wanted to buy a Fujitsu siemens laptop with SiS mirage 3 chipset for my little brother but this forum made me think again and I'll choose something else...Screw them and their crappy hardware and missing Linux drivers!

Thanks!

---

### Post by rekado on 2008-08-26
Clevo support is annoying.

**_August 12_**
**Me:** asking for the driver, no matter in which form.

**Support:** "how about using google?" sends me a link to the vista drivers... "there are too many types of linux anyway, we can't support all of them..."

**Me:** "well...." ignoring the vista link, explaining some things related to Xorg. Asking them to maybe just contact Barros Lee for more info.

**Support:** no reply...

**_August 20_**
**Me:** "Hi, it's me again..." This is what Barros Lee wrote... Please contact Clevo Taipei as they supposedly have the driver.

**Support:** "So far we don't have any reply of SiS. But I also don't know whom to contact at Clevo Taipei."


**_August 21_**
**Me:** *(assuming that the support guy is Chinese)*Xu&#20808;&#29983;&#65306;&#24744;&#22909;&#65281;
&#24744;&#26159;&#20013;&#22269;&#20154;&#21527;&#65311; &#25105;&#19981;&#26159;&#25152;&#20197;&#25105;&#32473;Clevo&#21488;&#21271;&#20889;&#37038;&#20214;&#30340;&#35805;&#20182;&#20204;&#26377;&#21487;&#33021;&#30475;&#19981;&#25026;&#12290;&#20320;&#20204;&#20844;&#21496;&#32943;&#23450;&#26377;&#20182;&#20204;&#26381;&#21153;&#32852;&#31995;&#20449;&#24687;&#12290;&#35831;&#24110;&#25105;&#32473;&#20182;&#20204;&#20889;&#19968;&#23553;&#37038;&#20214;&#12290;
&#35874;&#20102;&#21834;&#65281;

**Support:** no reply...


-----

I'll try again...

---

### Post by soxs on 2008-08-26
Thx for your great effort to get over all that f***in support lines a linux driver.

---

### Post by rekado on 2008-08-27
Still no reply. So I wrote a trilingual mail to all support addresses listed at the Clevo website as below. My Chinese is no so great but I think it is necessary as Clevo as well as SiS are operating from China. 

<snip/>

---

### Post by dub_u on 2008-08-27
Thanks for trying so hard to solve this, as it seems, impossible mission.
I will recieve my Zepto Titan A15 this week, which is equiped with a SiS Mirage 3 graphic card... 

Since I found out the (in)compability issues **after** ordering the laptop I have already asked Zepto for the driver, and today I was told that they have been in contact with both SiS and the manufacturer of the motherboard used in that laptop without any results.

---

### Post by rekado on 2008-08-27
Hmm, sounds bad. I received a reply from the UK service center. They said they are only responsible for warranty issues and repair. Told me to contact the HQ of Clevo. But my hopes are not high to actually receive a statement from Clevo Taipei.

---

### Post by rekado on 2008-09-15
I've got a reply from Clevo (a customer of SiS or at least notebook manufacturer) now:

"Dear Sir

We regret to inform you that, we can not provide technical service to the end user.

If you have any problem, Please contact your vendor or his distributor to help you.

Thank you,"


They are cute, aren't they? SiS says: "contact our customer, i.e. the notebook manufacturer", the manufacturer (clevo) says: "contact the vendor", the vendor says... well, nothing. They don't know anything and just sell stuff...

So, who should I ask now?
The laptop that I bought for my wife is Haier A20 which is a rebranded Clevo M721 or so using chips by SiS. So when I see that right I need to ask Haier to give me driver, even though they told me they can't (this is where I asked in the first place). They just buy from Clevo and replace their logo.

According to SiS' process description Clevo needs to offer the driver. What a mess!

---

### Post by soxs on 2008-09-15
> **rekado said:**
> I've got a reply from Clevo (a customer of SiS or at least notebook manufacturer) now:

"Dear Sir

We regret to inform you that, we can not provide technical service to the end user.

If you have any problem, Please contact your vendor or his distributor to help you.

Thank you,"


They are cute, aren't they? SiS says: "contact our customer, i.e. the notebook manufacturer", the manufacturer (clevo) says: "contact the vendor", the vendor says... well, nothing. They don't know anything and just sell stuff...

So, who should I ask now?
The laptop that I bought for my wife is Haier A20 which is a rebranded Clevo M721 or so using chips by SiS. So when I see that right I need to ask Haier to give me driver, even though they told me they can't (this is where I asked in the first place). They just buy from Clevo and replace their logo.

According to SiS' process description Clevo needs to offer the driver. What a mess!

Well, as you explored any possible holes the driver could be hidden in, and .. well.. every hole was protected by either poisionous spieders and/or trolls, sell your laptop and get a new one... I don't see any other possibility atm. I am sorry.

---

### Post by Father D on 2008-09-16
Sitting here in 'Vesa 2D' land... waiting for the wonderful almighty Gods at Sis to graciously deliver a 3D driver from above, to us lowly Linux Lemmings .... ERRRRR NO! .. this piece of s**t Sis laptop will be flogged to a Windows sucking mug, and a Linux friendly replacement will be grabbed 

STUFF YOU SIS!

---

### Post by rekado on 2008-09-19
Hmm, actually I feel uncomfortable giving up and selling a nice new laptop for much less than I bought it. Is there any more idea what we could do to get the driver? You sure don't all own laptops manufactured by Clevo, right? Could you name your laptop and the possible manufacturer? When Clevo doesn't want to help out maybe others still would.

---

### Post by dub_u on 2008-09-19
As I have already written here, I own a Zepto Titan A15 and have been in contact with Zepto's customer service even before I got my laptop delivered. I then got a mail from that specific person at Zepto that has been in contact with both SiS and the manufacturer of the actual laptop regarding this matter. Unfortunately without any result. He did give a hint, though that there may be an integrated 3D OpenSuse driver that should work with this graphic card, but since I saw a post in a Suse forum refering to ubuntuforums.org as a solution to a related problem, I strongly doubt that.

Anyway, I have a greater problem right now. I am forced to run Gutsy on this laptop, since the wireless (an Intel (!) 4965) isn't working properly. I'm awaiting Intrepid to see whether this is solved in this release or not. 

This is rather "off-topic" but describes my main issues nowadays. :( (Hardy - No 3D, no wireless but sound | Gutsy - No 3D, but wireless, on the other hand no sound)

---

### Post by Dennis Schulmeister on 2008-09-22
Hi,

I didn't notice that the old thread has gone. So I wondered why I got no mail notifications anymore. ;)

Anway I just wanted to rephrase my offer to collect all available SiS drivers and information on my dedicated wiki page:

[http://ncc-1701a.homelinux.net/WikiBerd/?page=LinuxSis67x](http://ncc-1701a.homelinux.net/WikiBerd/?page=LinuxSis67x)

Just send it to "dennis*ncc-1701a.homelinux.net". Both - the wiki and the mail server - are running on my small home server which in contrast to free offerings like RapidShare doesn't use ambigous captchas. :) So please help me with my efforts to establish a central informwation pool for the SiS driver issue.

Dennis :guitar:

---

### Post by rekado on 2008-09-25
Got a reply from the offical Haier service:

&#23562;&#25964;&#30340;&#29992;&#25143;&#65306;
&#24744;&#22909;&#65281;&#26469;&#20989;&#25910;&#24713;&#65281;
&#38750;&#24120;&#24863;&#35874;&#24744;&#20449;&#20219;&#28023;&#23572;&#24182;&#36873;&#25321;&#20102;&#28023;&#23572;&#20135;&#21697;&#65281;&#30001;&#20110;A20&#31995;&#21015;&#30340;&#25152;&#26377;&#31508;&#35760;&#26412;&#27809;&#26377;&#39044;&#35013;Linux&#25805;
&#20316;&#31995;&#32479;&#30340;&#65292;&#22240;&#27492;&#65292;&#26080;&#27861;&#21521;&#24744;&#25552;&#20379;A20&#30340;linux&#31995;&#32479;&#30340;&#30456;&#20851;&#39537;&#21160;&#31243;&#24207;&#65292;&#22914;&#26524;&#24744;&#36824;&#26377;&#20160;&#20040;&#38382;
&#39064;&#38656;&#35201;&#21644;&#25105;&#20204;&#32852;&#31995;&#65292;&#35831;&#24744;&#21450;&#26102;&#25320;&#25171;&#65306;4006999999&#26381;&#21153;&#30005;&#35805;&#65292;&#25105;&#20204;&#20250;&#32473;&#24744;&#25552;&#20379;&#28385;&#24847;&#30340;&#26381;
&#21153;&#30340;&#65281;
&#31069;&#24744;&#65306;
  &#29983;&#27963;&#24841;&#24555;
&#28023;&#23572;&#30005;&#33041;&#39038;&#26381;&#37096;
2008&#24180;9&#26376;25&#26085;

Embedded in all the default sentences full of expressions of courtesy there is the message: "Our notebooks don't come with Linux pre-installed, hence we cannot help you to get the driver for Linux."

I'm tired.

---

### Post by Dennis Schulmeister on 2008-09-25
> **rekado said:**
> Got a reply from the offical Haier service:

&#23562;&#25964;&#30340;&#29992;&#25143;&#65306;
&#24744;&#22909;&#65281;&#26469;&#20989;&#25910;&#24713;&#65281;
&#38750;&#24120;&#24863;&#35874;&#24744;&#20449;&#20219;&#28023;&#23572;&#24182;&#36873;&#25321;&#20102;&#28023;&#23572;&#20135;&#21697;&#65281;&#30001;&#20110;A20&#31995;&#21015;&#30340;&#25152;&#26377;&#31508;&#35760;&#26412;&#27809;&#26377;&#39044;&#35013;Linux&#25805;
&#20316;&#31995;&#32479;&#30340;&#65292;&#22240;&#27492;&#65292;&#26080;&#27861;&#21521;&#24744;&#25552;&#20379;A20&#30340;linux&#31995;&#32479;&#30340;&#30456;&#20851;&#39537;&#21160;&#31243;&#24207;&#65292;&#22914;&#26524;&#24744;&#36824;&#26377;&#20160;&#20040;&#38382;
&#39064;&#38656;&#35201;&#21644;&#25105;&#20204;&#32852;&#31995;&#65292;&#35831;&#24744;&#21450;&#26102;&#25320;&#25171;&#65306;4006999999&#26381;&#21153;&#30005;&#35805;&#65292;&#25105;&#20204;&#20250;&#32473;&#24744;&#25552;&#20379;&#28385;&#24847;&#30340;&#26381;
&#21153;&#30340;&#65281;
&#31069;&#24744;&#65306;
  &#29983;&#27963;&#24841;&#24555;
&#28023;&#23572;&#30005;&#33041;&#39038;&#26381;&#37096;
2008&#24180;9&#26376;25&#26085;

Embedded in all the default sentences full of expressions of courtesy there is the message: "Our notebooks don't come with Linux pre-installed, hence we cannot help you to get the driver for Linux."

I'm tired.
It's a pity really. Thanks for trying, though.

Dennis

---

### Post by pikmaster on 2008-09-26
> **Dennis Schulmeister said:**
> 
I didn't notice that the old thread has gone. So I wondered why I got no mail notifications anymore. ;)
Anway I just wanted to rephrase my offer to collect all available SiS drivers and information on my dedicated wiki page:


Dennis

Thanks to your page I was able to solve the problem with my Packard Bell Easynote MX37-T-003 laptop with SIS Mirage 3+ (SiS M672 chipset) video card.
When trying to use those 2D drivers from Barros Lee, I had mixed-up colors (some users called them "negative"). The fix was to insert the following line in your **/etc/X11/xorg.conf** file:
```
Option "useROMData " "False"
```

Pictures of the problem and the config files can be found on this web page [http://superpikmaster.googlepages.com/sis]("http://superpikmaster.googlepages.com/sis"). The old thread is now closed for new posting, so I wanted to share my experience here.

Now I am looking to enable DRI for this driver, as I still get this error
```

drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
```

Thanks.

---

### Post by spoons on 2008-09-26
Couldn't you create like a petition site and link all the linux dstro forums to it asking for them to bombard SiS with requests for drivers?

Good luck! :)

---

### Post by rekado on 2008-09-26
I'm tired, how about you organize it...? They certainly know my name already, anyway :-p

---

### Post by spoons on 2008-09-26
> **rekado said:**
> I'm tired, how about you organize it...? They certainly know my name already, anyway :-p

I don't think it would be my place considering I don't have an SiS chipset. Also if you started it, they'd be sitting there thinking "the linux is strong with this one". :D

---

### Post by rekado on 2008-09-26
haha! i wish they would think so. but i guess they rather think by themselves: "when will he ever learn...?"

once i recovered from the setbacks i will think about it again...

---

### Post by Master One on 2008-09-27
Even worse than not having the 3D driver, now the [**patched Winischhofer SiS Premium Driver**](http://ubuntuforums.org/showthread.php?t=463077) does not build any more with the latest xorg on Intrepid Ibex, please have a look [**here**](http://ubuntuforums.org/showthread.php?t=930930).

Since SiS is not going to give us the 3D driver, it is up to someone with the proper knowledge, to fix the patch for the 2D driver, otherwise it means going back to VESA on Intrepid Ibex (which is not an option, if running a 24" LCD with 1920x1200, like me).

---

### Post by rekado on 2008-09-29
Now that sounds bad. Unfortunately I've got no means to confirm it before the end of december (I'm here in Germany while my wife has to stay in China and her SiS notebook with her).
I wish we could get some information to add the 3D functionality to the existing (and possibly to be patched) 2D driver ourselves. Bad thing is: I really have no idea how drivers work, especially when there is no documentation of the hardware...

---

### Post by INAPPROPRIATE_USERNAME on 2008-10-24
Although I've been foolish enough to buy a laptop with Sis M672 graphics, I vote against anyone taking the time to write a 3d driver purely on the basis that this may encourage linux users to buy these products. I should have had the sense to check forums before buying and I've now made a point of ensuring that my company never buys anything containing SiS components.

---

### Post by rekado on 2008-10-24
Good point. I think this counts as a lesson learned for me too... As I delve into Blender I consider buying a new PC for rendering soon anyway, so we do not have to rely on the SiS laptop. Sad outcome. I will never understand how a company can be so stubborn...

I don't think it is worth spending so much time to reinvent a wheel that is locked up and probably will break after an update... I for my part will avoid anything labelled SiS now for practical reasons.

However, I want to thank Mr. Lee and Mr. Cheng from SiS Taiwan for their friendly support, all their work and their continuous responses to lots of emails from Linux users. So much energy bound by a company's rules - it's a shame!

---

### Post by Midnightsun on 2008-10-24
This is a great shame for me also :(  Having to use VESA in Intrepid is a royal pita.  So frustrating to have a company profit from us purchasing their hardware (albeit as part of a whole system) and then refusing to give us the software to allow us to use it properly.  Just wish I'd been using Linux before I bought the machine and I would have known to check compatibility first.

A petition to sign or something would be great.

---

### Post by uraker on 2008-10-31
Anyone knows about this satux drivers? Anyone tried?
[http://repos.satux.org.br/download/sis3d-driver-satux.deb](http://repos.satux.org.br/download/sis3d-driver-satux.deb)
I got the idea from: [http://ncc-1701a.homelinux.net/WikiBerd/index.php?page=LinuxSis67x](http://ncc-1701a.homelinux.net/WikiBerd/index.php?page=LinuxSis67x)

uraker

---

### Post by Dennis Schulmeister on 2008-10-31
> **uraker said:**
> Anyone knows about this satux drivers? Anyone tried?
[http://repos.satux.org.br/download/sis3d-driver-satux.deb](http://repos.satux.org.br/download/sis3d-driver-satux.deb)
I got the idea from: [http://ncc-1701a.homelinux.net/WikiBerd/index.php?page=LinuxSis67x](http://ncc-1701a.homelinux.net/WikiBerd/index.php?page=LinuxSis67x)

uraker
Hi uraker,

Manuel Dulcidio sent me the link to the Satux drivers last Sunday. Unfortunately I wasn't able to test because the laptop in question resides at my mother's. Besides I don't want to break her working system. :)

I wasn't able to gather much information from the satux page. It looks like a small Linux distribution created by a Portuguese developer team. There were some posts in the corresponding forum and from my limited language understanding I could gather that the driver is released as a beta driver for people to test. Unfortunately I couldn't detect any information about licensing and source code availability. Both are very important issues, IMHO.

Regards, Dennis

---

### Post by uraker on 2008-10-31
True. I can't even find "sis 672" in connection with that driver in their forum. (I even thought it is spanish, irgnorant as I am.)
Having 3d would be to good to be real. sis seams to hate linux and would do anything against it. Must be like that. Whats the point in not giving a driver? Obviously no manufacturer wants to buy it, so they are at a point where they mix up the money making part with the ruining their image part. Their cheap stuff is often selled without an OS so it should be important to give linux drivers. Man.

Sorry, I drifted away.

If anyone tried, please post it. Thanks!

---

### Post by jellfish on 2008-11-04
I can confirm that this SatuxSIS3d driver works on Kubuntu Hardy 7.04 i386 (X.org 7.2) with updated kernel 2.6.27.4. The driver causes some libGL warnings: "3D driver claims to not support visual 0x5a", but glgears now runs with 2777 frames in 5.0 seconds = 555.253 FPS. I will continue some testing... Would we really good to know if the source is somewhere available.

---

### Post by Master One on 2008-11-04
> **jellfish said:**
> I can confirm that this SatuxSIS3d driver works on Kubuntu Hardy 7.04 i386 (X.org 7.2) with updated kernel 2.6.27.4
Xorg 7.2? That does not make any sense. On one hand the missing sources, on the other hand, it will not work with Xorg 7.4 then. :(

---

### Post by jellfish on 2008-11-04
> **Master One said:**
> Xorg 7.2? That does not make any sense. On one hand the missing sources, on the other hand, it will not work with Xorg 7.4 then. :(

Uuups, what I wanted to say is that the driver works on Kubuntu *Feisty* 7.04 i386 (X.org 7.2) with updated kernel 2.6.27.4 [where the kernel update might not be necessary]. However, indeed, I did not get it working with Kubuntu 8.10 (X.org 7.4), also not forced by ignoreABI. 

I guess this binary driver is the 3d driver build by B. Lee for Ubuntu 7.04 (Satux 1.4?), see [http://barroslee.blogspot.com/2008/02/sis-linux-3d-driver-supported.html]("http://barroslee.blogspot.com/2008/02/sis-linux-3d-driver-supported.html").

I'm not very confident of having a satisfying solution for X on SIS 671 soon :(

---

### Post by rekado on 2008-11-04
> **jellfish said:**
> I can confirm that this SatuxSIS3d driver works on Kubuntu Hardy 7.04 i386 (X.org 7.2) with updated kernel 2.6.27.4. The driver causes some libGL warnings: "3D driver claims to not support visual 0x5a", but glgears now runs with 2777 frames in 5.0 seconds = 555.253 FPS. I will continue some testing... Would we really good to know if the source is somewhere available.

That sounds pretty good to me. I don't really care if it is 7.04 I have to install on my wife's laptop if the 3D graphics will work then.

Where does the driver actually come from? Didn't SiS only issue the driver to hardware manufacturers? If we could trace it back to its origin maybe we could get hold of the source code.

---

### Post by jellfish on 2008-11-04
I also have some better news. The SatuxSIS3D driver also works with kubuntu 8.04 with 

```
X -ignoreABI
``` 

in the .xserverrc. This might be a temporary solution for me.

---

### Post by rekado on 2008-11-04
Can't test this before the end of this year but I'm looking forward to trying this. Thanks!

---

### Post by jellfish on 2008-11-04
Another note: The binary driver as it is available at the moment appears to be very buggy (so it is offered as BETA). It seems to provide some basic 3d acceleration, but it crashes easily both on ubuntu 7.04 and 8.04, e.g. moving around the glxgears window may freeze your system. Let's hope these guys from Satux have the source code to be able to do bug fixing (and to compile a version for Xorg>7.3).

---

### Post by sailershen on 2008-11-09
> **rekado said:**
> Got a reply from the offical Haier service:

&#23562;&#25964;&#30340;&#29992;&#25143;&#65306;
&#24744;&#22909;&#65281;&#26469;&#20989;&#25910;&#24713;&#65281;
&#38750;&#24120;&#24863;&#35874;&#24744;&#20449;&#20219;&#28023;&#23572;&#24182;&#36873;&#25321;&#20102;&#28023;&#23572;&#20135;&#21697;&#65281;&#30001;&#20110;A20&#31995;&#21015;&#30340;&#25152;&#26377;&#31508;&#35760;&#26412;&#27809;&#26377;&#39044;&#35013;Linux&#25805;
&#20316;&#31995;&#32479;&#30340;&#65292;&#22240;&#27492;&#65292;&#26080;&#27861;&#21521;&#24744;&#25552;&#20379;A20&#30340;linux&#31995;&#32479;&#30340;&#30456;&#20851;&#39537;&#21160;&#31243;&#24207;&#65292;&#22914;&#26524;&#24744;&#36824;&#26377;&#20160;&#20040;&#38382;
&#39064;&#38656;&#35201;&#21644;&#25105;&#20204;&#32852;&#31995;&#65292;&#35831;&#24744;&#21450;&#26102;&#25320;&#25171;&#65306;4006999999&#26381;&#21153;&#30005;&#35805;&#65292;&#25105;&#20204;&#20250;&#32473;&#24744;&#25552;&#20379;&#28385;&#24847;&#30340;&#26381;
&#21153;&#30340;&#65281;
&#31069;&#24744;&#65306;
  &#29983;&#27963;&#24841;&#24555;
&#28023;&#23572;&#30005;&#33041;&#39038;&#26381;&#37096;
2008&#24180;9&#26376;25&#26085;

Embedded in all the default sentences full of expressions of courtesy there is the message: "Our notebooks don't come with Linux pre-installed, hence we cannot help you to get the driver for Linux."

I'm tired.

&#25105;&#29992;&#30340;&#26159;&#28023;&#23572;a680&#65292;&#20063;&#26159;sis 671/771&#26174;&#21345;&#65292;&#20351;&#29992;sis_vga_150508_ubuntu_8.04.tar.bz2&#21487;&#20197;&#19978;&#21040;1280*800&#65292;&#20294;&#26159;&#20250;&#33457;&#23631;&#65292;&#23631;&#24149;&#19978;&#25152;&#26377;&#30340;&#39068;&#33394;&#37117;&#33457;&#25481;&#20102;&#65292;&#26681;&#26412;&#30475;&#19981;&#28165;&#26970;&#12290;

I use Haier A680, sis 671/771. this is my xorg.conf:
```

Section "Files"
  FontPath     "/usr/share/fonts/misc:unscaled"
  FontPath     "/usr/share/fonts/local"
  FontPath     "/usr/share/fonts/75dpi:unscaled"
  FontPath     "/usr/share/fonts/100dpi:unscaled"
  FontPath     "/usr/share/fonts/Type1"
  FontPath     "/usr/share/fonts/URW"
  FontPath     "/usr/share/fonts/Speedo"
  FontPath     "/usr/share/fonts/PEX"
  FontPath     "/usr/share/fonts/cyrillic"
  FontPath     "/usr/share/fonts/latin2/misc:unscaled"
  FontPath     "/usr/share/fonts/latin2/75dpi:unscaled"
  FontPath     "/usr/share/fonts/latin2/100dpi:unscaled"
  FontPath     "/usr/share/fonts/latin2/Type1"
  FontPath     "/usr/share/fonts/latin7/75dpi:unscaled"
  FontPath     "/usr/share/fonts/baekmuk:unscaled"
  FontPath     "/usr/share/fonts/japanese:unscaled"
  FontPath     "/usr/share/fonts/kwintv"
  FontPath     "/usr/share/fonts/truetype"
  FontPath     "/usr/share/fonts/uni:unscaled"
  FontPath     "/usr/share/fonts/CID"
  FontPath     "/usr/share/fonts/ucs/misc:unscaled"
  FontPath     "/usr/share/fonts/ucs/75dpi:unscaled"
  FontPath     "/usr/share/fonts/ucs/100dpi:unscaled"
  FontPath     "/usr/share/fonts/hellas/misc:unscaled"
  FontPath     "/usr/share/fonts/hellas/75dpi:unscaled"
  FontPath     "/usr/share/fonts/hellas/100dpi:unscaled"
  FontPath     "/usr/share/fonts/hellas/Type1"
  FontPath     "/usr/share/fonts/misc/sgi:unscaled"
  FontPath     "/usr/share/fonts/xtest"
  FontPath     "/opt/kde3/share/fonts"
  InputDevices "/dev/gpmdata"
  InputDevices "/dev/input/mice"
EndSection

Section "ServerFlags"
  Option       "AllowMouseOpenFail" "on"
  Option       "ZapWarning" "on"
EndSection

Section "Module"
  Load         "freetype"
  Load         "type1"
  Load         "dbe"
  Load         "glx"
  Load         "extmod"
EndSection

Section "InputDevice"
  Driver       "kbd"
  Identifier   "Keyboard[0]"
  Option       "Protocol" "Standard"
  Option       "XkbLayout" "us"
  Option       "XkbModel" "microsoftpro"
  Option       "XkbRules" "xfree86"
EndSection


Section "InputDevice"
  Driver       "synaptics"
  Identifier   "Mouse[1]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Emulate3Buttons" "on"
  Option       "HorizScrollDelta" "0"
  Option       "InputFashion" "Mouse"
  Option       "Name" "Synaptics;Touchpad"
  Option       "Protocol" "explorerps/2"
  Option       "SHMConfig" "on"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[3]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "ImPS/2 Generic Wheel Mouse"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
  Option       "CalcAlgorithm" "XServerPool"
  DisplaySize  304 190
  HorizSync    30-50
  Identifier   "Monitor[0]"
  ModelName    "SAMSUNG LCD MONITOR"
  Option       "DPMS"
  Option       "PreferredMode" "1280x800"
  VendorName   "SEC"
  VertRefresh  50-60
  UseModes     "Modes[0]"
EndSection


Section "Modes"
  Identifier   "Modes[0]"
EndSection


Section "Screen"
  DefaultDepth 16
  SubSection "Display"
    Depth      15
    Modes      "1280x800" "1280x768" "1280x720" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1280x800" "1280x768" "1280x720" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1280x800" "1280x768" "1280x720" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1280x800" "1280x768" "1280x720" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection


Section "Device"
  BoardName    "Sis"
  Driver       "sis"
  Identifier   "Device[0]"
  Screen       0
  VendorName   "sis"
EndSection



Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  InputDevice  "Mouse[3]" "SendCoreEvents"
  Option       "Clone" "off"
  Option       "Xinerama" "off"
  Screen       "Screen[0]"
EndSection


Section "DRI"
    Group      "video"
    Mode       0660
EndSection

Section "Extensions"
EndSection

```

---

### Post by rekado on 2008-11-10
Could you provide a screenshot or a photo of your screen? I don't know what exaclty you mean with colors that are "hua diao le".

&#26377;&#21487;&#33021;&#36825;&#20010;&#39537;&#21160;&#21644;SiS 771&#19981;&#22909;&#29992;&#12290;Are you sure it is SiS 671/771?
(maybe the driver doesn't work with SiS 771)

---

### Post by Dennis Schulmeister on 2008-11-10
Could someone please translate all that Chinese? ;) I don't get a single word.

Best, Dennis

---

### Post by rekado on 2008-11-10
> **Dennis Schulmeister said:**
> Could someone please translate all that Chinese? ;) I don't get a single word.

(Actually, Chinese is a very simple language. No grammar to learn, I picked it up in half a year or so. But reading takes a bit longer...)


&#25105;&#29992;&#30340;&#26159;&#28023;&#23572;a680&#65292;&#20063;&#26159;sis 671/771&#26174;&#21345;&#65292;&#20351;&#29992;sis_vga_150508_ubuntu_8.04.tar.bz2&#21487;&#20197;&#19978;&#21040;1280 *800&#65292;&#20294;&#26159;&#20250;&#33457;&#23631;&#65292;&#23631;&#24149;&#19978;&#25152;&#26377;&#30340;&#39068;&#33394;&#37117;&#33457;&#25481;&#20102;&#65292;&#26681;&#26412;&#30475;&#19981;&#28165;&#26970;&#12290;

What I use is a Haier a680 [laptop], it's also an SiS 671/771 graphics card. Using [the driver from] sis_vga_150508_ubuntu_8.04.tar.bz I can go up to 1280*800, but it will become *washed out (not sure)*; on the screen all the colors appear *blurry (not sure)*, not clear at all.

---

### Post by Dennis Schulmeister on 2008-11-11
Thanks a lot. :)

---

### Post by sailershen on 2008-11-12
> **pikmaster said:**
> Dennis

Thanks to your page I was able to solve the problem with my Packard Bell Easynote MX37-T-003 laptop with SIS Mirage 3+ (SiS M672 chipset) video card.
When trying to use those 2D drivers from Barros Lee, I had mixed-up colors (some users called them "negative"). The fix was to insert the following line in your **/etc/X11/xorg.conf** file:
```
Option "useROMData " "False"
```

Pictures of the problem and the config files can be found on this web page [http://superpikmaster.googlepages.com/sis]("http://superpikmaster.googlepages.com/sis"). The old thread is now closed for new posting, so I wanted to share my experience here.

Now I am looking to enable DRI for this driver, as I still get this error
```

drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
```

Thanks.

It's useful for me!

---

### Post by dcardinale on 2008-11-20
please sign me up as one who would benefit from an improved driver. interstingly, the driver for the sis card in ubuntu 8.04 worked just wonderfully. why is that driver missing in 8.10? is there someone we can contact to get that driver back to fully functioning??
I am afraid I may have to jump ship an move to Mandriva who has a fully functioning driver for the SIS chipset.

Dan

---

### Post by dub_u on 2008-11-26
> I am afraid I may have to jump ship an move to Mandriva who has a fully functioning driver for the SIS chipset.

I am running Mandriva One 2009 since it was released and it solved both the graphics problems I had (2D anyway, no support for 3D here either) and my wireless issue. 
Out of the box support for 2D graphics, and after a firmware upgrade the Intel iwl4965AGN worked as well.

Yet I sometimes miss "my" Ubuntu. Luckily I have a dual boot with 7.10, and that has been useful, since the USB support is less OOB in Mandriva.
I couldn't connect my digital camera, but it was recognized from the start by Ubuntu.

Sorry for the off topic parts of this post, but I just wanted to clear out some details pro-mandriva and pro-ubuntu ;-)
Frustrating, though that I need them both to get (almost) full functionality.

I also tried to install the Satux driver in Ubuntu 7.10 but that only left me with a 800x600 resolution that I can't get rid of ](*,)
I am working on that.....

---

### Post by Alex_Gor on 2008-12-20
Hello! Please help me! :) I can not use Satux 3D SIS driver, after installation sis3d-driver-satux.deb I reload X (Ctrl-Alt-BackSpace) and X do not start! in X log I found "can't read /usr/lib/dri/sis315_dri.so"
i rename new file sis667_dri.so and X start! but in X log i found too many "3D driver claims to not support visual 0x5a" etc.. and opengl game (open arena for example) can not start. :( May be You know how install satux 3d driver correctly? I use Kubuntu 7.04 Hardy

---

### Post by Dennis Schulmeister on 2008-12-27
Hi friends,

I just want to let you know that I converted my ole wiki page to a full wiki on its own. Now the available information on the SiS vs. Linux community topic should be more accesible than before.

You can find the new wiki here: [http://ncc-1701a.homelinux.net/~linux-sis/](http://ncc-1701a.homelinux.net/~linux-sis/)

Please help me to keep it up to date and go on sending my new files and information as they arise. Many readers with similar problems are grateful.

Thanks a lot and have a happy new year,:popcorn:
Dennis

PS: Oh and please refrain from using dubious offers like RapidShare for offering driver files. Instead send the files to me and I'll make them availble on my web server in an instant. The advantage is that you don't get any ads and that users don't need to surpass ambiguous captchas just to get a single file. :)

---

### Post by Master One on 2008-12-28
That's great, Dennis.

I didn't follow that stuff for a while, because I'm now using the D201GLY2 on a 17" LCD temporarily with Debian Lenny, which means the old driver as compiled by myself still works.

Going for Ubuntu 8.10, what's the way to go now?

Is it xserver-video-sis671_ubuntu8.10-1_i386.deb or Satux SiS 3D drivers (i386)?

---

### Post by Dennis Schulmeister on 2008-12-28
> **Master One said:**
> Going for Ubuntu 8.10, what's the way to go now?

Is it xserver-video-sis671_ubuntu8.10-1_i386.deb or Satux SiS 3D drivers (i386)?

As I understand it that's the satux driver packaged as a handy deb file. Bar&#322;omiej Gerlich has done the work sent me a message. :)

Wait, the readme says it's the Winischoefer driver. Now I'm confused.

Dennis

---

### Post by Dennis Schulmeister on 2008-12-28
Ah, oj, should have read it better. This is the original message from Bar&#322;omiej:

>  Fedora Forum's user bahamot has done the pcistruct rework in
sisimedia driver, it works in Xserver>1.5 now. His source can be found at
[http://forums.fedoraforum.org/showthread.php?t=195483](http://forums.fedoraforum.org/showthread.php?t=195483) .

Third, I have packaged bahamot's modified driver, disabled some buggy
features and added a PCIID file, so now all that is needed to run the driver
in Ubuntu Intrepid Ibex is installing the deb package. No fiddling with
xorg.conf, compiling or copying required. My driver package and sisctrl
package can be found in this thread:
[http://ubuntuforums.org/showthread.php?p=6374259](http://ubuntuforums.org/showthread.php?p=6374259) .

So it's a patched version of the Winischoefer driver.

Dennis

---

### Post by zorglups on 2009-01-24
I'm running Hardy 8.04.1 (2.6.24-19-386) on my D201GLY2.
I still use the [driver compiled by Otto]("http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads"). I'm quite happy but Bluetooth is making my Mythbox to hang :(

This hang is solved in 2.6.15.

I tried the upgrade to Intrepid (using Xorg 7.4) but couldn't find any working driver.

Still seeking for a solution tonight I found this:
[http://www.freshports.org/x11-drivers/xf86-video-sis-intel/]("http://www.freshports.org/x11-drivers/xf86-video-sis-intel/")
[http://www.freebsd.org/cgi/cvsweb.cgi/ports/x11-drivers/xf86-video-sis-intel/xf86-video-sis-intel.tar.gz?tarball=1]("http://www.freebsd.org/cgi/cvsweb.cgi/ports/x11-drivers/xf86-video-sis-intel/xf86-video-sis-intel.tar.gz?tarball=1")

This sounds good:
> - Update X.org ports to 7.4+ (few ports are more recent than the katamari).

I will give it a try and keep you posted.

---

### Post by zorglups on 2009-01-24
Too bad. I did not catch this was for FreeBSD.
Anyhow, the change might help me apply the same changes on the driver provided by Intel.

If anyone has any experience with this, please let me know.

---

### Post by zorglups on 2009-01-24
Does anyone had any success running Intrepid on a D201GLY2 ?

If yes, which driver did you use ?

---

### Post by Dennis Schulmeister on 2009-01-25
I wonder if the driver can easily be installed on a Linux system since it comes in a FreeBSD package.

Looking at the make file it is not GNU make compatible. There's a BSD make in the Ubuntu/Debian repositories called pmake but it's actualy a netBSD make. As BSD makes each have their little differences I'm not sure whether it works.

Dennis

---

### Post by zorglups on 2009-01-25
Dennis,

Have you ever got report from someone running successfully one of the drivers hosted on your useful wiki on a **D201GLY2 with Intrepid**?

If yes, I will try a fresh install of Ubuntu.
If not I might go for Debian trial.

Best regards,

Pierre.

---

### Post by Dennis Schulmeister on 2009-01-25
> **zorglups said:**
> Dennis,

Have you ever got report from someone running successfully one of the drivers hosted on your useful wiki on a **D201GLY2 with Intrepid**?

If yes, I will try a fresh install of Ubuntu.
If not I might go for Debian trial.

Best regards,

Pierre.
Hi Pierre,

I think nobody ever explicitely mentioned this specific mainboard or the Mirage 1 chipset on it. So I can't tell if one of the drivers works.

I think the best shot would be the new official 2D SiS driver from Barros Lee. It's approved for Ubuntu 8.10. ([http://ncc-1701a.homelinux.net/~linux-sis/downloads/sis_vga_drv_161208-Ubuntu810.run](http://ncc-1701a.homelinux.net/~linux-sis/downloads/sis_vga_drv_161208-Ubuntu810.run))

Best, Dennis

---

### Post by Master One on 2009-01-26
What? Barros Lee is back?

Is this a binary driver (didn't inspect the .run file), and if yes, what about amd64?

---

### Post by Dennis Schulmeister on 2009-01-26
I'm not sure whether he's back or whether it's his final driver relase ... It's a binary driver and unfortunately no AMD64. :( As with nearly all proprietary binary packages!

Dennis

---

### Post by zorglups on 2009-01-29
> **Dennis Schulmeister said:**
> Hi Pierre,

I think nobody ever explicitely mentioned this specific mainboard or the Mirage 1 chipset on it. So I can't tell if one of the drivers works.

I think the best shot would be the new official 2D SiS driver from Barros Lee. It's approved for Ubuntu 8.10. ([http://ncc-1701a.homelinux.net/~linux-sis/downloads/sis_vga_drv_161208-Ubuntu810.run](http://ncc-1701a.homelinux.net/~linux-sis/downloads/sis_vga_drv_161208-Ubuntu810.run))

Best, Dennis

I probably did something wrong...
Here are my steps.

I had everything fine under Ubuntu 8.04 with the driver compiled by Otto.

I did a do-release-upgrade to upgrade from hardy to intrepid.
For sure the display was showing the well known vertical noise.

I then did:
sudo /etc/init.d/gdm stop
cd /tmp
wget [http://ncc-1701a.homelinux.net/~linux-sis/downloads/sis_vga_drv_161208-Ubuntu810.run](http://ncc-1701a.homelinux.net/~linux-sis/downloads/sis_vga_drv_161208-Ubuntu810.run)
chmod 755 sis_vga_drv_161208-Ubuntu810.run
sudo ./sis_vga_drv_161208-Ubuntu810.run

I then rebooted my system but X failed to start and started in safe mode.

Did I do anything wrong ?
Is there some left-over fron the previously installed Otto's driver ?
Would anyone propose me a working Xorg.conf I could start with ?

Thanks a lot in advance,

Pierre

---

### Post by zorglups on 2009-02-02
Despite my efforts in running Intrepid (Xorg 7.4) on my Intel D201GLY2 with his crap SiS chipset, I miserably failed. :(:(:(

I had to upgrade my system anyhow to solve kernel freeze (due to bluetooth bug).

Here is what I finally did:
1) Upgraded my system from Hardy to Intrepid.
2) Downgraded Xorg to 7.3 following this guide: [http://dailyvim.blogspot.com/2008/12/ubuntu-downgrading-xorg.html](http://dailyvim.blogspot.com/2008/12/ubuntu-downgrading-xorg.html)

I now have Intrepid running fine with the Otto's compiled driver.

Thanks to Denis to maintain his Wiki. It is always useful.

I will maybe try in the future to downgrade to Xorg 7.2 and install the Satux driver. I still have plenty of other things to solve first but will update this threads with my findings.

Best regards,

Pierre.

---

### Post by Solarium on 2009-02-02
> **zorglups said:**
> 
I will maybe try in the future to downgrade to Xorg 7.2 and install the Satux driver. 


Hmm, to my understading using the satux driver in 8.10 was a problem because of the kernel and not Xorg version ? Have i got it complitly wrong ?:confused:

---

### Post by zorglups on 2009-02-02
> **Solarium said:**
> Hmm, to my understading using the satux driver in 8.10 was a problem because of the kernel and not Xorg version ? Have i got it complitly wrong ?:confused:

I sincerely don't know. Hopefully someone else might shed some light.

Pierre

---

### Post by dc740 on 2009-02-03
jellfish would you be so kind of telling us how did you get the Satux 3D drivers working? I tried adding those lines to .serverrc but it doesn't work for me.I also tried copying only the needed files.I mean sis_drv.*from the deb package. but it doesn't work

tell me. if you have to install kubuntu all over again. what would you do?

thanks for your time

---

### Post by dc740 on 2009-02-05
OK, Satux 3D drivers + KUbuntu work. to make the drivers load under kubuntu 8.04 you have to add this lines to /etc/X11/xorg.conf

Section "ServerFlags"
 Option "IgnoreABI" "true"
EndSection
 
now you can use it without problems. the question is... satux driver has 3D acceleration... but it's based on an GPL license .... isn't sis violating some terms?

Look what I found on /var/log/Xorg.0.log

> (II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
        SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
        SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
        SIS[M]661[F|M]X/[M]741[GX]/[M]760[GX]/[M]761[GX]/662, SIS340,
        [M]670/[M]770[GX], [M]671/[M]771[GX]
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
        Volari V3XT/V5/V8/Duo (XG40/XG42)
(II) Primary Device is: PCI 01:00:0
(--) Chipset [M]671/[M]771[GX] found
(II) resource ranges after xf86ClaimFixedResources() call:
bla bla bla
(II) Setting vga for screen 0.
(II) SIS(0): SiS driver (2006/10/17-1, compiled for X.org 7.1.1.0)
(II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(0): *** See [http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml)
(II) SIS(0): *** for documentation, updates and a Premium Version.
(II) SIS(0): RandR rotation support not available in this version.
(II) SIS(0): Dynamic modelist support not available in this version.
(II) SIS(0): Screen growing support not available in this version.
(II) SIS(0): Advanced Xv video blitter not available in this version.
(II) SIS(0): Advanced MergedFB support not available in this version.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0x9000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(**) SIS(0): Depth 24, (--) framebuffer bpp 32
(==) SIS(0): RGB weight 888
(==) SIS(0): Default visual is TrueColor
(--) SIS(0): Video BIOS version "3.74.03a" found (new SiS data layout)
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Color HW cursor is enabled
(II) SIS(0): Using VRAM command queue, size 512k
(==) SIS(0): Hotkey display switching is enabled
(==) SIS(0): SiSCtrl utility interface is disabled
(II) SIS(0): For information on SiSCtrl, see
                [http://www.winischhofer.at/linuxsispart1.shtml#sisctrl](http://www.winischhofer.at/linuxsispart1.shtml#sisctrl)

I have no idea about the licenses but shouldn't they give the source code with the binaries that where written using Thomas Winischhofer as the base code? aren't they violating the GPL terms?
just asking. I repeat: I have no idea about this

Second question:
I installed the drivers. made them work... but DRI is still not present... the logs show that it tries to load but it fails. any suggestion?

this is the error:
> drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
(EE) [drm] drmOpen failed.
(EE) SIS(0): [dri] DRIScreenInit failed. Disabling the DRI.
(II) SIS(0): Framebuffer from (0,0) to (1279,4094)
(II) SIS(0): Using XFree86 Acceleration Architecture (XAA)



thanks for your time people!

---

### Post by wargoth on 2009-02-06
I asked Barros Lee to send me SiS driver for Ubuntu 8.10 x64. He answered that they don't have 64bit driver for this version. Sad.

P.S. He attached a driver for Ubuntu 8.10 x32: **[sis_vga_drv_161208-Ubuntu810.run]("http://narod.ru/disk/5515834000/sis_vga_drv_161208-Ubuntu810.run.html")**

Also Barros said:

> ...But recently, SiS don't allowed me to release 2d driver now...But I think they will release sis 2d driver source code soon....

---

### Post by dc740 on 2009-02-06
great!

Just another thing about KUbuntu and Satux 3D drivers:

A lot of people complained about problems with GTK applications using the sis3D drivers. Well I started to copy each file of the package one by one, and restarting the system each time to find out how could I get DRI enabled. I couldn't because changing from libdrm.so.2.3.0 to libdrm.so.2.0.0 hangs my system at startup when it tries to load DRI module.

the good new is that I found wich file was causing the segmentation faults that closed a lot of applications:
you should install the driver BUT before doing so make a backup of this files /usr/lib/libGL*
install the driver and the copy the backup files again to /usr/lib/
also make a backup of /usr/lib/libdrm* because I had problems trying to install this old files (and I think this files are the ones that make DRI work)

I CAN'T get DRI enabled. I would like to see someone's xorg.conf using the satux3D drivers because I can use the drivers but I don't have 3D acceleration and I really would like to fix it.


Good luck people. lets wait for a decent solution someday soon.

---

### Post by Solarium on 2009-02-07
Here's my xorg.conf using satux 1.8 with 3D driver that seems to be working

```
# xorg.conf (Xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands as root:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum
#   dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/share/fonts/X11/CID"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
EndSection
Section "Module"
	Load	"v4l"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"evdev"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"dri"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
	Load 	"synaptics"
EndSection


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
	Option		"XkbVariant"	"abnt2"
EndSection

Section "ServerFlags"
Option "AllowMouseOpenFail" "true"
EndSection 

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "auto-dev"
	Option "HorizScrollDelta" "0"
	Option "SHMConfig" "1"
EndSection

Section "Device"
	Identifier "Placa de Video"
	Driver "sis"
	#BusID "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-60
	VertRefresh	50-60
	Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Placa de Video"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
               Modes   "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
               Modes   "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
               Modes   "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
               Modes   "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
               Modes   "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
               Modes   "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice    "Synaptics Touchpad"
	Option "AllowMouseOpenFail" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by afeasfaerw23231233 on 2009-03-05
Hi, I bought my notebook last week and now I am regret that I did not to check the compatibility isuue with linux before. 

The notebook is made by HASEE (Chinese manufacturer) with the dang SiS 671MX chipsets. This notebook was come with Red Flag Linux Preinstalled but I did my own installation once I got it because I needed it dual-booting Win XP and UBUNTU. It didn't provide a recovery disk for the Red Flag OS. And I didn't know SiS 671MX has such a big problem in the linux graphic driver. Now it is running Ubuntu 8.10 32-bit (I didn't know the existence of this thread and I cannot find the driver for 64-bit, so I reinstall 32-bit to get the 2D driver work)

Perhaps I should send a request to the manufacturer for the 3D driver too, but I don't expect they would reply as their customer service is rubbish. Last week I request them an updated BIOS and Wireless driver for win xp and I have no reply until now. 

If I knew SiS doesn't provide linux driver I might choose another model...

---

### Post by zorglups on 2009-03-06
The Red Flag Linux 6.0 ISO is here:
[ftp://ftp.redflag-linux.com/pub/redflag/dt6sp1/SP1/redflag-6-sp1.iso](ftp://ftp.redflag-linux.com/pub/redflag/dt6sp1/SP1/redflag-6-sp1.iso)

We might look at it to see if it includes any interresting sis driver ???

---

### Post by afeasfaerw23231233 on 2009-03-06
Sorry that I didn't even check the pre-installed Red Flag linux. When I got it I just install xp and then ubuntu. This notebook didn't come with a recovery disk. The two cd come with it are MS drivers disk. I visit the hasee's site and cannot find a recovery disk for it. If it provides one I may try recovering the Red Flag on a USB drive to see if 3D works.

---

### Post by afeasfaerw23231233 on 2009-03-06
Some guys on the non official hasee support forum claim this iso support SiS chipsets
[ftp://fuwuzhan:fuwuzhan@ftp.hasee.com/iso/RedFlag6.0.08_u40si.iso](ftp://fuwuzhan:fuwuzhan@ftp.hasee.com/iso/RedFlag6.0.08_u40si.iso)


Don't know if it's ture or not.

---

### Post by afeasfaerw23231233 on 2009-03-06
I am downloading it. It needs around 24 hour for 6-10KB/s

---

### Post by nush on 2009-03-09
> **wargoth said:**
> I asked Barros Lee to send me SiS driver for Ubuntu 8.10 x64. He answered that they don't have 64bit driver for this version. Sad.

P.S. He attached a driver for Ubuntu 8.10 x32: **[sis_vga_drv_161208-Ubuntu810.run]("http://narod.ru/disk/5515834000/sis_vga_drv_161208-Ubuntu810.run.html")**

Also Barros said:

hi all
has this driver been tested yet and does it work, my acer is driving me mad
thanks nush

---

### Post by afeasfaerw23231233 on 2009-03-11
Yes, it works. I am using it and I am running Ubuntu 8.10 i686 and the kernel is 2.6.27-11.

---

### Post by nush on 2009-03-16
> **afeasfaerw23231233 said:**
> Yes, it works. I am using it and I am running Ubuntu 8.10 i686 and the kernel is 2.6.27-11.

hi 
were you able to activate desktop effects with this driver, also how do you open it and install it
thanks nush

---

### Post by afeasfaerw23231233 on 2009-03-16
I cannot get any desktop effects with this driver as it's for 2D only. 3D is not available. 
But at least I can get full 1280x800 resolution instead of 800x600 by this 2D driver. 
I install the driver following Dennis Schulmeister's site (see post #67).
Visit this page
[http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads](http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads)
download sis_vga_drv_161208-Ubuntu810.run, follow the instruction and it should work. 

Some previous posts mentioned the Satax driver may work on 3D. I don't know how to install it as I am just a newbie of linux.

---

### Post by nush on 2009-03-17
thanks, i will checkout the link

---

### Post by azedddine on 2009-03-17
hi every body

i'm using mandriva linux 2009, on a laptop, before i tried ubuntu 8.10 on my laptop with sis 672, but no 3D effect only 2D with the driver of barros lee,
with mandriva it work but hardly but it work and i can see 3d effect of desktop,compiz fusion work slowly, now i just want to  know, is it possible to convert "drivers" from .rpm to .deb with alien package?

---

### Post by dc740 on 2009-03-28
Ok, just a little update for those who still try:

How to make satux 3D driver work on kubuntu 8.04?
Add this lines to your xorg.conf:

Section "ServerFlags"
Option "IgnoreABI" "true"
EndSection

I also works for ubuntu 8.04 but you have to make a backup of some files before installing it (or you'll have GTK problems)
I don't remember which files should be backed up but I think they were:
libGLEW.so.1.5        libGL.so.1            libGLU.so.1
libGLEW.so.1.5.0      libGL.so.1.2          libGLU.so.1.3.070200
they are on /usr/lib


why? because the satux driver overwrittes them and that's what causing the GTK problems everyone complains about.
It's obvious but I have to say it:
Step 1: backups those files (also backup libdrm.so.2... I dont know but just in case)
Step 2: install satux driver and DON'T restart X server until you complete the steps
Step 3: restore your backup files to overwrite the files installed by the driver.

WARNING: I think that should work but DO NOT do it on your main rig and make sure you have a backup of everything (just in case something goes wrong). I did this a loooong time ago and it worked (I think I did it on KUbuntu 8.04) but I don't remember the exact steps.


A note on Ubuntu 8.10:

I don't know why but the latest sis_vga_drv_161208-Ubuntu810 driver HAS dri support

This is glxgears output:
glxgears 
1196 frames in 5.0 seconds = 239.040 FPS
1199 frames in 5.0 seconds = 239.681 FPS
1193 frames in 5.0 seconds = 238.556 FPS

And glxinfo:
 glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes        <-----------
server glx vendor string: SGI
server glx version string: 1.2


I whould like to see how is glxgears performing on Satux 1.8 to compare results


Good luck people!

---

### Post by sieben on 2009-03-29
Hallo dc740,

could you please post your xorg.conf from kubuntu 8.04 and satux3D/driver.
I tried to install this drivers for ubuntu 8.04 but nothing happens. How should the xorg look like with a working satux/driver

thank you

---

### Post by dc740 on 2009-04-01
I don't have the working xorg for KUbuntu. but this is my current xorg using the latest 32 bit Ubuntu 8.10 driver:

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "es"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "HorizEdgeScroll" "0"
EndSection

Section "Device"
	Identifier "sis67x"
	Boardname "Sis 672M"
	Busid "PCI:1:0:0"
	Driver "sis"
	Screen 0
EndSection

Section "Monitor"
	Identifier "Main LCD"
	Vendorname "Generic LCD Display"
	Modelname "LCD Panel 1280x800"
	Horizsync 31.5-50.0
	Vertrefresh 56.0 - 65.0
	modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	modeline "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync

	Gamma 1.0
	Option "DPMS"
EndSection

Section "Screen"
	Identifier "Main Screen"
	Monitor "Main LCD"
	Device "sis67x"
	Defaultdepth 24
	SubSection "Display"
	Depth 24
	Virtual 1280 800
	Modes "1280x800@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
	EndSubSection
EndSection
#secondary monitor:
Section "Device"
        Identifier "Secondary sis67x"
        Boardname "Sis 672M"
        Busid "PCI:1:0:0"
        Driver "sis"
        Screen 1
EndSection

Section "Monitor" #
        Identifier "Secondary Monitor"
        Gamma 1.0
EndSection


Section "Screen" 
        Identifier "Secondary Screen"
        Device "Secondary sis67x"
        Defaultdepth 24
        Monitor "Secondary Monitor"
EndSection

#main
Section "ServerLayout"
	Identifier "Singlehead Layout"
	Screen 0 "Main Screen" 0 0
	Inputdevice "Synaptics Touchpad"
EndSection

Section "ServerLayout"
        Identifier "Multihead Layout"
        Screen 0 "Main Screen" LeftOf "Secondary Screen"
        Screen 1 "Secondary Screen"
        #Inputdevice "Synaptics Touchpad"
EndSection


Section "Module"
	Load "glx"
	Load "GLcore"
	Load "v4l"
EndSection


Section "ServerFlags"
#Option "xinerama" "true"
Option "DefaultServerLayout" "Singlehead Layout"
EndSection


to make it work remember to add this option:

Option "IgnoreABI" "true"

On the server flags section. that whould be:
> Section "ServerFlags"
#Option "xinerama" "true"
Option "DefaultServerLayout" "Singlehead Layout"
Option "IgnoreABI" "true"
EndSection


I couldn't enable multiple monitors. I think I should use MergeFB instead of Xinerama. If ou can make it work then let me know. I think MergeFB is not enabled on the latest drivers anyway.

Good luck.

---

### Post by sieben on 2009-04-03
Hi dc740 again,

i have Ubuntu 8.04 too, but i'm not sure, if the satux driver is wotking in my system. How can I find out? 3d desktop effects dosnt work.

---

### Post by dc740 on 2009-04-03
3D effects won't work anyway. the driver is not optimized enough or it simply can't handle it. Why am I saying this? because WinXP performance is not good at all too. I don't think this card will be able to handle Compiz as some other low budget integrated cards do (like Intel X3100)

IMHO the 3D drivers running on satux 1.8 have a lot of problems running simple 3D games like Tux Racer so they will hardly run compiz (if they run it)

Anyway there are special instructions to make effects work (they cannot be enabled "out of the box"). 

You have to follow this steps:

Edit '/etc/X11/xorg.conf'. on the Device section add this line:

>     Option "AddARGBGLXVisuals" "True"

Example:
>     Section "Device"
    Identifier "Configured Video Device"
    Boardname "SIS driver"
    Busid "PCI:1:0:0"
    Driver "sis"
    Screen 0
    Option "AddARGBGLXVisuals" "True"
    EndSection


Reboot the system and open a console:
> 
    wget [http://blogage.de/files/4359/download](http://blogage.de/files/4359/download) -O compiz-check
    chmod +x compiz-check
    ./compiz-check


There will be a question about avoiding some whitelist checks. answer Yes

Once it finished open another console and type:
> sudo apt-get install xserver-xgl
sudo apt-get install compizconfig-settings-manager



Let us know how it works. To know if you have DRI enabled you have to do this:
> glxinfo | grep rendering

if it say yes... then you ahve the satux 3D driver fully enabled... 

To disable Compiz do this:
Open a console and type:

>     mkdir ~/.config/xserver-xgl
    echo "" > ~/.config/xserver-xgl/disable


Good Luck! Let us know about your progress

---

### Post by sieben on 2009-04-03
Thank you very much!

I'll try it next days.

---

### Post by sieben on 2009-04-06
It dosn't work that way.

direct rendering: No

and after all stept I had to run Gnome in safty-mode to deactivate compiz.

any idea?

---

### Post by dc740 on 2009-04-06
that's what I've been saying.

First:
you have no DRI, less performance. this happened to me before. I tried the satux 3D drivers on KUbuntu but i couldn't get DRI working.

Second:
whithout proper drivers. you won't be able to run compiz at a decent speed (or in this case, you cannot run compiz at all)

I don't think you will be able to run compiz at a decent speed. none of us has done it. and the ones that tried it (I'm included) got a horrible performance. I disabled it five minutes later.

Good luck. If you find something new about this card post it here, so we can try it too.

---

### Post by afeasfaerw23231233 on 2009-06-04
Hi, I'm using Ubuntu 9.04 SMP i686 and by following Dennis' site [here]("http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads") , downloaded the .deb and it works well. 

But when I tried getting the touchpad driver work from this guide [http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758) , after logout and login it said X has problem and the screen resolution drops to 640x480! It seems that the SiS driver has been overrided. I undo the setting in Xorg.conf and reboot, everything returns normal again. What's my problem and how can I get synaptic driver works?

Here's my original xorg.conf
```


Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection 
```

I follow the guide and install the synaptic driver, and added the following to xorg.conf:
```

Section "ServerLayout"
	Identifier	    "Default Layout"
        Screen              "Default Screen"
	InputDevice         "Generic Keyboard"
	InputDevice	    "Configured Mouse"
        InputDevice         "Synaptics Touchpad"
EndSection

Section "InputDevice"
          Identifier "Synaptics Touchpad"
          Driver "synaptics"
          Option "SendCoreEvents"          "True"
          Option "Protocol"                "auto-dev"
          Option "Device"                  "/dev/psaux"
          Option "SHMConfig"               "True"
          Option "LeftEdge"      	   "100"
	  Option "RightEdge"     	   "1100"
	  Option "TopEdge"       	   "50"
	  Option "BottomEdge"    	   "300"
	  Option "FingerLow"     	   "30"
	  Option "FingerHigh"    	   "40"
	  Option "MaxTapMove"              "100"
	  Option "TapButton1"    	   "1"
	  Option "TapButton2"    	   "3"
	  Option "TapButton3"    	   "2"
	  Option "MinSpeed"      	   "0.15"
	  Option "MaxSpeed"      	   "0.90"
	  Option "AccelFactor"   	   "0.10"
	  Option "VertScrollDelta"         "25"
	  Option "HorizScrollDelta"        "30"
EndSection

```
Here's the xorg.0.log when it failed
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux coppen-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun  3 21:01:41 2009
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	Undefined InputDevice "Generic Keyboard" referenced by ServerLayout "Default Layout".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log

```
It said "Fatal server error: no screens found"

What's wrong?
Many thanks!

EDIT: from the notes on this page [http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads](http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads) ```

The file /etc/X11/xorg.conf shouldn't contain any modifications. The default version provided by Canonical should do. 
```

---

### Post by Dennis Schulmeister on 2009-06-04
Hi,

the problem is that the synaptics tutorial has been written with an older Xorg version in mind. Old versions (until approx. 9 months ago) needed very detailed configuration in /etc/X11/xorg.conf. Newer version configure themselves automaticaly.

The problem in your case is that you stated a "server layout" in the configuration file, just like it was needed for older versions. This section tells the X server about the architecture of your machine: There's a keyboard, there's a mouse, there's one screen, ... It does so by refering to other sections in the file which have an "Identifier".

Now in your server layout you're referencing sections which used to exist but don't exist anymore:

```

	InputDevice         "Generic Keyboard"
	InputDevice	    "Configured Mouse"

```

You need to at least remove those two lines. I'm not sure though if that won't override auto configuration. Maybe you need to remove the complete "Server Layout" block:

```

Section "ServerLayout"
	Identifier	    "Default Layout"
        Screen              "Default Screen"
	InputDevice         "Generic Keyboard"
	InputDevice	    "Configured Mouse"
        InputDevice         "Synaptics Touchpad"
EndSection

```

BTW, the low resolution comes because the X server starts a fail-safe mode if it encounters trouble in its configuration. In that case all configuration is ignored, no auto-configuration is performed and only some generic, "almost always" working settings are chosen. Once you got your configuration file right it'll start in normal resolution again. :)

Best,
Dennis

PS: I'm glad the wiki is of help for you. :popcorn:

---

### Post by afeasfaerw23231233 on 2009-06-05
Thanks! It works!

By the way I want to ask if the SiS 671 driver is available for ubuntu 9.04 x64 too? I install the 32-bit Ubutnu because the driver is for i386 only. And is there a driver for 3D acceleration?

---

### Post by Master One on 2009-06-05
A crappy SiS graphics is a good reason to stick with 32bit, an we all wish there would be 3D support and a fully functional open source driver.

---

### Post by Dennis Schulmeister on 2009-06-05
A crapy SiS card would be a reason to trash the notebook and never ever buy anything SiS again. \\:D/

Best,
Dennis

---

### Post by afeasfaerw23231233 on 2009-06-05
Yes, SiS chipsets is a real crap. No matter it's in XP or UBUNTU the idle power consumption is no less than 23W even everything is off. There's been rumour that the SiSM671/672(DX) are actually desktop chipset SiS671/672(DX) by just adding an "M" for pretending to be a mobile chipsets. Thier mobile chipsets are notorious so they quit the market right after these products.

---

### Post by Roehrich on 2009-06-09
> **afeasfaerw23231233 said:**
> 
By the way I want to ask if the SiS 671 driver is available for ubuntu 9.04 x64 too? I install the 32-bit Ubutnu because the driver is for i386 only. And is there a driver for 3D acceleration?

There is no 3D driver, but for 9.04 x64 there is a driver - look here: [http://ubuntuforums.org/showpost.php?p=7133694&postcount=167](http://ubuntuforums.org/showpost.php?p=7133694&postcount=167)

---

### Post by Dennis Schulmeister on 2009-06-09
Hi,

thanks for the hint about the 9.04 x64 drivers. I'll immediately add it to my wiki as I got some requests about x64 drivers lately. :popcorn:

Best,
Dennis

---

### Post by afeasfaerw23231233 on 2009-06-10
Hi, according to this link [http://ubuntuforums.org/showpost.php?p=7133694&postcount=167](http://ubuntuforums.org/showpost.php?p=7133694&postcount=167)
it should be ```

Driver "sis671"
```
But in your wiki it is```
 
Driver "sis"
```

Thanks for your helpful wiki!

---

### Post by Dennis Schulmeister on 2009-06-11
> **afeasfaerw23231233 said:**
> Hi, according to this link [http://ubuntuforums.org/showpost.php?p=7133694&postcount=167](http://ubuntuforums.org/showpost.php?p=7133694&postcount=167)
it should be ```

Driver "sis671"
```
But in your wiki it is```
 
Driver "sis"
```

Thanks for your helpful wiki!

Got it. Thanks a lot. :p

Best,
Dennis

PS: I'm glad the wiki is of help. Seems like people are visiting it a lot since it went online half a year ago.

```

· Downloads 15407 hits
· Front Page 12316 hits
· Official Drivers 1681 hits
· Vesa Driver 1672 hits
· Sismedia Pc Linux Os 1077 hits
· Additional Parameters 705 hits
· False Colors 557 hits
· Flickering Text 525 hits

```

---

### Post by m4tic on 2009-06-14
I have 3D acceleration for sis741

---

### Post by alinef on 2009-06-14
> **m4tic said:**
> I have 3D acceleration for sis741
Do you have a working AIGLX? How did you manage it?

I've installed xorg-driver-sis671 deb from above, except for 3D accel, it seems to be working fine in my acer aspire 3000. But it's missing sis315_dri.so, the drm stuff...

---

### Post by skywriter on 2009-08-11
Gonna to write on the wall: "Think twice who do you pay your money and what for!" SiS are selfish assholes.

---

### Post by skywriter on 2009-08-12
> **dc740 said:**
> you have no DRI, less performance. this happened to me before. I tried the satux 3D drivers on KUbuntu but i couldn't get DRI working.

Can anysoul explain why Satux driver called "3D" if there is no DRI working? What about writing to [http://www.softwarefreedom.org](http://www.softwarefreedom.org) about GPL violation from SiS?

---

### Post by azedddine on 2009-08-31
why can't we use the sismedia driver used by mandriva linux, i tryed mandriva before and it was fine i can also get the compiz fusion effects,??

---

### Post by afeasfaerw23231233 on 2009-10-08
SiS741/661 is different from SiS 671/672. The IGP of SiS741 is named "Mirage" but that of 671/672 is "Mirage 3/3+". Mirage supports DX7 and Mirage 3/3+ supports DX9.

It seems that there are 4 generations of Mirage IGP, corresponding to different chipsets. 

You can have a look on SiS' site
[http://www.sis.com/products/product_000001.htm](http://www.sis.com/products/product_000001.htm)
[http://www.sis.com/products/product_000002.htm](http://www.sis.com/products/product_000002.htm)

---

### Post by azedddine on 2009-10-10
and what does it mean?

---

### Post by afeasfaerw23231233 on 2009-10-10
Oh, sorry. I was referring to m4tic's post. His chipset is 741 but not 671/672.

> **m4tic said:**
> I have 3D acceleration for sis741

---

### Post by andydch on 2009-10-21
is anybody have driver for karmic koala?

:)

---

### Post by azedddine on 2009-10-21
you can try this, it's in french, you have to install the old driver and change the Xorg file, as shown here:

[http://doc.ubuntu-fr.org/sis_771_671](http://doc.ubuntu-fr.org/sis_771_671)

---

### Post by Stuart P. Bentley on 2009-11-20
Shouldn't Dell be able to get these drivers? I'm using a Dell Inspiron 1000 with Ubuntu and a SiS graphics card; with Dell's support of Ubuntu, it seems they would provide this.

---

### Post by ajoliveira on 2009-11-23
Hi

> **andydch said:**
> is anybody have driver for karmic koala?

:)

Use the instructions I already provided [here]("http://ajoliveira.com/ajoliveira/uk/software/xorg.php") for 9.04, those will work for Karmic as well, you have there drivers for both 32 and 64 bit. Or use my new driver compiled for Koala 9.10 64-bit present on the same location.

Cheers

---

### Post by thetechnaddict on 2009-12-27
> **m4tic said:**
> I have 3D acceleration for sis741

Great, where did you get the driver? could you post a link?

I've got 2d to work in Karmic thanks to 

[http://ajoliveria/ajoliveira/uk/software/xorg/php](http://ajoliveria/ajoliveira/uk/software/xorg/php)

---

### Post by Geri_lgfx on 2010-09-15
So still no 3d with this beautifull gpus?

well, well. sad. 

i **MAYBEE** would be able to do a shareware 3d driver for these chips, if i would get a laptop with sis mirage 3 gpu and some data sheets with the registers and microcodes of this brutal ultra mega fast chip, **IF** the existing 2d drivers can accept incoming data from an external third party opengl driver, without magic.

---

### Post by azedddine on 2010-09-22
> **Geri_lgfx said:**
> So still no 3d with this beautifull gpus?

well, well. sad. 

i **MAYBEE** would be able to do a shareware 3d driver for these chips, if i would get a laptop with sis mirage 3 gpu and some data sheets with the registers and microcodes of this brutal ultra mega fast chip, **IF** the existing 2d drivers can accept incoming data from an external third party opengl driver, without magic.


hello,

that will be awsome, what are your requests? i'm ready to send to you all informations you want


thank you

---

### Post by kev.r.j on 2012-02-07
:KS:KS
> Originally posted by azedddine              
**Re: SiS 671/672 Graphics: OpenGL/3D driver**
         you can try this, it's in french, you have to install the old driver and change the Xorg file, as shown here:

[http://doc.ubuntu-fr.org/sis_771_671](http://doc.ubuntu-fr.org/sis_771_671)**Brilliant two minute solution.**
 I have a 1280 x 800 laptop with onboard sis mirage3 graphics chipset on Mint 12. 
This worked a treat after returning to this problem time after time and the solutions never quite going according to procedures described for modding Xorg.conf or xrandr methods etc, tried on Ubuntu, Suse, Xubuntu CentOS and Mint
The instructions are simple even if you can't read french as the code is in terminal english.
If you have a 1280x800 just follow all the command lines one by one untill you run the line ```
make install
``` restart.
et voila!  (Well,it did for me anyway)

If you have a 1366 x 768 screen just continue following the next 2 steps to define xorg.conf, although I can't vouch for this one

---

### Post by sideger on 2012-02-24
I have recently 11.10 on my laptop

after a hours of reinstalls and searching for solutions regarding 11.10 and sis671/771 i came across this thread

=D> thanks to kev.r.j for the post. i now have my desired 1368x768 resolution

---

