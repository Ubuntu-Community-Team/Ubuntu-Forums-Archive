---
title: "Emu-1820M &amp; Linux"
date: 2006-06-19
forum: Multimedia &amp; Video
---

### Post by dralaroc on 2006-06-19
Hey Guys/Gals,

Curiousity is getting the best of me.  I currently have my 1820M loaded on my windows machine, and everything is running pretty smooth.  My question is this, anyone running an Emu sound card on dapper/linux?   Or, should I wait for Edgy to come out?

Thanks

---

### Post by jonathantneal on 2006-06-20
I'm running the exact same card, friend!  I just did a search for EMU and found your post.  I haven't had any luck getting sound at all, but if anybody can get our cards working though, it's the people here.

EMU 1820(M) sound cards use a breakout box and software (only currently available for windows) which controls your inputs/outputs.  We need two things to get it working on Linux:

A. Drivers. (ubuntu detects the card and labels it 'E-MU 1212m [4001]')
B. The EMU graphical interface which I'm about to try in WINE.  Chances are it won't understand what my EMU card is through WINE though.  Then again, Linux can work magic sometimes.

---

### Post by jonathantneal on 2006-06-22
I emailed Customer Service regarding the issue and they have replied through two emails the following:

"We do not offer any linux drivers." (and) "There are no future plans to release any linux drivers."

I didn't cut any other text out of their reply, except the signature.

---

### Post by Orion Mayair on 2006-06-24
The 1820 or 1820M is NOT an Audio Card...:) 
It is Technically the BreakOut ( External ) Box that Plugs into an...
 EMU 1212m Which IS the Audio Card that Linux Detects and Installs a Driver For !

I'm Personally Sorry to Hear that EMU has NO Plans to Support the 1820M Extentions for Linux... For I currently have a Dual Boot - Windows XP / Linux Ubuntu setup... With Both the 1212m and 1820m ( Attached ):( 

If you buy and install the 1212m FIRST and then UpGrade to the 1820 or 1820m...
You will have a Internally Cabled ( Analog IN/OUT & Midi ) Panel...
( This means the stock installation of a 1212m uses TWO Slots in your computer )

When the EMU 1212 is used with the 1820... This Daughter Card is usually REMOVED because the EMU Mixer Application can NOT use the Analog IN/OUT & Midi Connections ONCE the 1820 is Plugged In... ( I think that's a design flaw but that was the Bottom Line when I last contacted the EMU Tech people )

This means that to make the 1212m Work with Linux... The 1820 would most linkly have to be Unplugged. ( The 1212m Main Card has only Digital Outputs ) So at this point you should be able to use it's DIGITAL PORTS...
If you need Analog Ins and Outs then that Daughter Card will have to be attached interally to the 1212m.

I took out the Daughter Card on my system so I'm going to PUT IT BACK IN ( I do Need the Analog Outputs for my Headphone amp ) and See if I can discover that the Linux Drivers are working.:mrgreen: 

NOTE : I believe the reason the 1820 is Dead in Linux is because it uses a Hardware Bootup Process... ( this is Nornally initiated before Windows Starts Up )

Onward & UoWard !

Orion \\:D/

---

### Post by dralaroc on 2006-07-07
Oh well thought I'd ask before I mess up my windows setup.  Johnathan, let me know how the wine route went for ya.

---

### Post by jcdutton on 2006-08-26
I am writing a Linux ALSA driver for the EMU 1212m and the EMU1820m.
Are people still interested?

---

### Post by dolson on 2006-08-26
I don't have that card, but i'm sure the others would appreciate it, and perhaps I'd look into getting the card if a driver was available. So i'd encourage you to go for it. The more devices supported by ALSA and linux in general, the better.

---

### Post by shanepardue on 2006-08-28
> **jcdutton said:**
> I am writing a Linux ALSA driver for the EMU 1212m and the EMU1820m.
Are people still interested?

i'm very interested!

---

### Post by floogy on 2006-08-29
According to the alsa matrix: Isn't there already some development ongoing on these cards? Are you that developer? If not, I think it would be helpful to joining things together?*

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)
> E-MU 1212m  	CA0102, FPGA  	Details (emu10k1)  	 [ANio] [RCAio] [TOSio] [ADTio]
Support arriving soon
E-MU 1820m 	CA0102, FPGA 	Details (emu10k1) 	[ANio] [RCAio] [TOSio] [ADTio]
Support arriving soon

*) Sorry for my probably strange english...

---

### Post by neufena on 2006-08-29
jcdutton, I'd be very interested in a driver, espesially if it'll work for the 0404. Let me know if I can be of any help testing.

Neufena

---

### Post by af4k on 2006-08-31
I would be very interested to know if the driver under development might also work with my EMU-0404 card!

Thanks for any help. Also - is there any good Linux software 
out for use with recording / MIDI or audio interfaces like these???

TIA - af4k

---

### Post by floogy on 2006-09-02
[http://alsa.opensrc.org/EMU+1212m](http://alsa.opensrc.org/EMU+1212m)
[http://alsa-project.org/~james/alsa-driver/emu1212m/](http://alsa-project.org/~james/alsa-driver/emu1212m/)

---

### Post by halfpower on 2006-09-13
> **jcdutton said:**
> I am writing a Linux ALSA driver for the EMU 1212m and the EMU1820m.
Are people still interested?

I am interested.  At the moment I have no sound at all on my Linux boot.

These people on these forum threads are also interested:

[Linux support for the new EMU cards??? ]("http://productionforums.com/viewtopic.php?highlight=linux&t=796&sid=2932d9449c759757d0858af649536d63")
[One more question related to Linux ]("http://productionforums.com/viewtopic.php?highlight=linux&t=4664&sid=2932d9449c759757d0858af649536d63")

---

### Post by maniqui on 2006-09-22
> I am writing a Linux ALSA driver for the EMU 1212m and the EMU1820m.
Are people still interested?

I'm interested in a Linux driver for the EMU 0404. 

Do you think your driver could work for my soundcard at least for listening my music when booting on linux? :)

Thanks in advance.

---

### Post by raintheory on 2006-10-16
Sorry for a late reply on this...   

Anyways I have the E-MU 1616m and am wondering if there is any hope for it in what you guys may (or may not) be working on.

Thanks

---

### Post by handy on 2006-10-17
I can't help wondering if there is some conection between the fact that **Creative** own **EMU** now, & there not being any intention for **Linux drivers**?

I really don't know how tight **M$** & **Creative** are.

It could just be that **Creative** are such a big corporation, that they don't think they need to bother with **Linux**.

---

### Post by Scio on 2006-11-03
I'm planning to buy EMU 0404, what is the driver situation for this card?

---

### Post by miquelmatas on 2006-11-05
Here's another EMU0404 user

---

### Post by berniefranks on 2006-11-14
Presently, I'm not running Linux on any of my computers, although I am very interested. One thing that's preventing me is I don't know if it'd be able to read my 1212M, so you can count me in on wanting drivers as well.

---

### Post by gadderbaum on 2007-01-22
> **jcdutton said:**
> I am writing a Linux ALSA driver for the EMU 1212m and the EMU1820m.
Are people still interested?

Hi, 

I have a 1820 too (great sound card btw) and I would be delighted about a driver! Otherwise I would have to install a second one to have sound avail on my Ubuntu System.

I hope someone can provide me a running driver soon :-)

---

### Post by tjlytle on 2007-02-02
I have the 1616m and would love to try running a portable studio using Ardour. I see there are some drives listed on the ALSA site, 1820 and 1212, any idea if those are compatible with the 1616? Or if drivers for the 1616 will be available?

---

### Post by sgx on 2007-02-03
> **tjlytle said:**
> I have the 1616m and would love to try running a portable studio using Ardour. I see there are some drives listed on the ALSA site, 1820 and 1212, any idea if those are compatible with the 1616? Or if drivers for the 1616 will be available?
EMU, the now emasculated s0ck-puppet of (Creative Labs Micro$oft Monopoly Soundcard Division) the REAL  parent company, can only release enough helpful info to to avoid being renowned as -total- jerks, but have wickedly donated the odd card, and limited specs, so that they can glibly joke about linux devs working unpaid past midnight to reverse engineer audio that will be 2 generations old, before its stable...but I personally won't  lose any sleep if Chinese and Russian street-vendors sell 1000 copies of fista, for every one that gets cashed out in the U.S. ...free capitalism being what it is...

But it won't hurt to try your card  with code made on other models, basic i/o is all that needed, Lee Revel may be
involved, google him for inside info, though you may have to grep a large mailinglist log file to get at the truth...

---

### Post by sudoreboot on 2007-02-04
I'm using Emu-1820 (not M). Is the fpga thing on the 1820M that much important for ALSA functionality?
I've downloaded and installed alsa-*-1.0.14rc1, and alsaconf recognized the PCI card as emu10k1. Still no sound. I have no experience with multiple cards (the other is an onboard Intel thing). I've tried to not-use onboard card by compiling the driver with enable card = emu10k1 only. But afterwards I couldn't get alsamixer to work, so this is not good.
Oh (I feel a bit n00by asking this, but I currently don't have the manual), I'm not sure that I've installed it properly: Just plugged the PCI card into mobo and connected it with some cat5 cable to the external unit. Should the PCI or external unit receive additional power from somewhere? At first cycle, I intend to use the external unit as a quality headphone-output only (either it will drive DT770-80 or I'll connect it to additional amp).

---

### Post by djsubject on 2007-02-05
the 1820 needs a power connector to be connected internally to the main card (same power connector as the floppy drive) this powers up the dock,

i have ubuntu 6.10 installed & its telling me my card is a 1212 not a 1820,

i'm new to linux & have 3 cards on my linux install

on board ac97 (working well)
RME Digi96 (can only get the test tone in the control panel for sounds to work)
E-MU 1820 (cant get a peep out of it)


Subz

---

### Post by deathmonkey on 2007-03-05
Hi all.  Just adding my name to the roster of people interested in an 1820M driver.

:)

---

### Post by rotylee on 2007-03-24
> **jcdutton said:**
> I am writing a Linux ALSA driver for the EMU 1212m and the EMU1820m.
Are people still interested?

I am in.

mine is also being found but not emitting any joy.

---

### Post by Bill_Gates on 2007-03-25
Hi, i'm getting sound with EMU1212 since alsa 1.0.14 rc but driver seems a little buggy. When you plays something at 44.100 or any rate, playback is too fast and crappy, 48khz is perfect. Please keep improving this driver because i'm tired of windows. Sorry about my bad english. Thanks. :guitar:

---

### Post by ubbsbm on 2007-04-06
another 1616m user here. i'd be happy just to get the cardbus working.

---

### Post by raintheory on 2007-04-08
I know I've already posted, but just wanted to post again to say that I would be willing to help any way that I can to get something working.

1616m user.

---

### Post by Bill_Gates on 2007-04-10
> **Bill_Gates said:**
> Hi, i'm getting sound with EMU1212 since alsa 1.0.14 rc but driver seems a little buggy. When you plays something at 44.100 or any rate, playback is too fast and crappy, 48khz is perfect. Please keep improving this driver because i'm tired of windows. Sorry about my bad english. Thanks. :guitar:

Finally working fine here. I run alsamixer and changed internal clock to 44.100 and flash player and another programs sounds good now.

---

### Post by carella on 2007-05-21
YA1820mU ;)!

that is to say "Yet Another 1820m User" so very interested in a driver for it !

Thank's all

---

### Post by aspie on 2007-06-01
Yet another 1820M user here :D

---

### Post by raintheory on 2007-06-01
With UbuntuStudio having been released, there *really* should be some work on this!  :)

---

### Post by noizehunter on 2007-06-05
I am also using 1820M, I have just moved from XP to kubuntu. I have my EMU sitting on the desk looking forlorn. On board sound is working ok for now, but i'd love to not have to sell this emu as the sound quality is excellent.

The thing is though, no one seems to be talking about the emulatorX sampler in this device. I think it's unlikely that we'll ever have an implementation in linux for that, and that was the main reason I bought the 1820m.

If you chaps make a driver work in linux, i'd be most appreciative, but my fireface 800 would love you even more!! and theoretically this could have a fully working driver.

Anyway, good work everyone, i'm loving (k)ubuntu. And i can't believe i didn't start using linux back when win 3.11 started hiding everything from me.

Cheers

---

### Post by agkbill on 2007-06-22
I am also a EMU 1820 user. Would be really great to get it working under ALSA, thought it would come in the 1.0.14 verson but it seems like that is not the case.

Would really love it!

Thank you,
/Christer
Sweden

---

### Post by kinglevel on 2007-09-10
Another swedish 1820 user here. 
I could pay for a 100% working driver. 

/Edde

---

### Post by capt scroggins on 2007-09-30
Another 0404 user here. I too would be willing to help/pay for working driver. Only thing holding me up from 100% switch.

---

### Post by raintheory on 2007-10-16
...ALSA v1.0.15 released today...

Hopefully this will get some of our interfaces working.  Personally, I think I'm waiting until the official Gutsy release of UbuntuStudio before I dive in and see what happens with my E-MU 1616m PCMCIA.

Best of luck to everyone with this!

---

### Post by Mr.Johnny on 2007-10-23
Anybody got a working E-Mu under Ubuntu? Mine is recognized with 1.015, but no sound.

---

### Post by aspie on 2007-10-31
I just upgraded to Gutsy and was hoping this would sort it out.  But the lights aren't on (on the dock).  In fact the 121m card seems to no longer be on the system.

I guess there is a lot some config to do, but what???

---

### Post by Bill_Gates on 2007-11-08
> **aspie said:**
> I just upgraded to Gutsy and was hoping this would sort it out.  But the lights aren't on (on the dock).  In fact the 121m card seems to no longer be on the system.

I guess there is a lot some config to do, but what???

Compile alsa-firmware package from alsa web.

---

### Post by aspie on 2007-11-09
Thanks for the pointer.  For some reason I didn't get notification of your post!  Luckily someone else posted too.

[http://ubuntuforums.org/showthread.php?t=598497]("http://ubuntuforums.org/showthread.php?t=598497")

---

### Post by cwschw on 2007-11-29
Hi, I'm new to Ubuntu (UbuntuStudio 7.10).I installed it on a ASUS P4P-800E Deluxe MB, P4 3.0E CPU, 2Gb Corsair DDR 800, EVGA NVIDIA 7800GS SC, and an Audigy2 Value sound card. Everything was great, but - I wanted to use a "better soundcard" (a couple I/O} for recording. After checking ASLA I found the E-MU 1212m listed as support arriving in 1.0.14.  As Ubuntu 7.10 (as well as Studio) include 1.0.14  I thought great I'll pick up an E-MU, out with the old - in with the new, and hit the ground running.  I ran into a wall. I get no GStreamer plugins/devices found, Device Mgr sees it as SB Audigy, E-MU 1010(which is right). So it's recognized as H/W but I guess the emu10K1/CGA0102 driver isn't functional in 1.0.14 yet?  I tried "sudo-ing out/in" alsa-sound-base etc. but that didn't help. I have some minor unix experiance from long ago (15+ yrs) so I'm kind of a novice.  Any help for me? Is it the driver for the 1212m (Version 1?, has firewire), or am I doing something wrong?

---

### Post by spacevoid8 on 2008-01-17
i have EMU 1616 PCI card with microdock..and i can`t get it working..it`s a *very* pity that there is no official drivers from EMU... :(

---

### Post by Hobnobb on 2008-01-24
emu cards are more supported since the latest alsa project release alsa-driver-1.0.16rc1 january 22 2008

See my other post on:
[http://ubuntuforums.org/showthread.php?t=518039&highlight=emu%200404](http://ubuntuforums.org/showthread.php?t=518039&highlight=emu%200404)
Good luck !

---

### Post by spacevoid8 on 2008-01-24
>Hobnobb

thanks! good news, i try to do my best;) 

i can wait switching to linux from shitty windows, last problem is a need for quality emu driver..

---

### Post by Funkstar De Luxe on 2008-04-18
> **jcdutton said:**
> I am writing a Linux ALSA driver for the EMU 1212m and the EMU1820m.
Are people still interested?

I registered here just to show how much interest I have.  I would be over the moon if you could get a good driver!

---

### Post by Phu_Bard on 2008-05-26
My brother and I are both trying to Escape the MS grip.

He's got 10+ years of unix\linux experienced and I'm new to it.
I have a 1212M & he'd consider it if the drivers were available.
I like the 1212M so much that I think I'll buy another 3 as backups at that price, you can't go wrong.

Please attach a double count to the numbers interested in the drivers for the EMU 1212M in ubuntu Studio64.

Cheers!

P.S.>>>
There is a good sized EMU product interface users forum at    
[http://www.productionforums.com](http://www.productionforums.com)

---

### Post by joeltw on 2008-07-01
Hello... I've just started a bounty for a complete driver for the EMU 1212m (thats the 1616 without the breakout).

I know playback works but if anyone wants a complete driver with all the I/O then please pledge what you can afford.

Bounties really do offer an incentive to developers so with a bit of luck we might get a driver out of this.

please visit [www.emubounty.co.nr]("http://www.emubounty.co.nr")

---

### Post by Mr.Johnny on 2008-07-01
Well... you could give all that money to eugene gavrilov, leader programmer of the wonderful kx drivers, I'm sure he'd do a fine job, besides, he is already working on a mac version of it.

---

### Post by fluteman on 2008-07-05
> **Funkstar De Luxe said:**
> I registered here just to show how much interest I have.  I would be over the moon if you could get a good driver!

I have an emu1820 and I'd love to have a reliable, functioning Linux / Ubuntu driver for it so I can ditch Win XP.  After reading all of the various posts across the web, it sounds like there are lots of folks who would help support this effort...

How can I help (not being a programmer)?

---

