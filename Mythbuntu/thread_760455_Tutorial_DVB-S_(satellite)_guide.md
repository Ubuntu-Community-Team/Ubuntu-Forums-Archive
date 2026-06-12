---
title: "Tutorial: DVB-S (satellite) guide"
date: 2008-04-20
forum: Mythbuntu
---

### Post by DutchLoki on 2008-04-20
Hi, I'm considering writing a complete how to guide for MythTV DVB-S (satellite). I've googled some and looked at most of the official mythTV and dedicated places for a guide about this, but found nothing good. would it be helpful for current and future users if I write one?

This will be a walk through/ how to guide that everyone can follow (no linux experience required) that includes mounting the dish to using it, configuring the satellite card, getting all available channels, using payTV channels, basicly all the works for MythTV and DVB-s.

Some topics that will be covered: 
- Hardware choise
- List of compatible cards with matrix to findout which functions are supported with that card
- Channellistings (manual and online listings)
- Diseq usage 
- Cams (payTV)
- etc.

Also (for this purpose) I was hoping everyone could mention the sites they know about the subject. This way I can save some time by including some existing texts (of cource with credits where they belong).

Thanks in advance for any suggestion you have.



Edit: Tutorial completed - see one of my posts in this thread for the url.

---

### Post by DutchLoki on 2008-04-20
Questions:
1)	what's the best place to put such a guide?
2)	Which sites do you know about this subject?

---

### Post by wildchild on 2008-04-20
> **DutchLoki said:**
> Questions:
2)	Which sites do you know about this subject?
DVBN has a quite good tutorial with pictures how to setup mythtv with a dvb-s card. Also there's some stuff how to get cccam softcam to work with mythtv.

---

### Post by superm1 on 2008-04-20
Put this guide on a wiki, hopefully on help.ubuntu.com or wiki.mythtv.org.  When you are done with the page, link to it from this thread.

---

### Post by DutchLoki on 2008-04-20
> **wildchild said:**
> DVBN has a quite good tutorial with pictures how to setup mythtv with a dvb-s card. Also there's some stuff how to get cccam softcam to work with mythtv.

Do you have an URL for me? I can not find the right page :confused:

---

### Post by superm1 on 2008-04-20
To do it on help.ubuntu.com,

just make a url like this:

[https://help.ubuntu.com/community/MythTV_BLAH](https://help.ubuntu.com/community/MythTV_BLAH)

and then edit it.  Creates the page for you

---

### Post by DutchLoki on 2008-04-20
> **superm1 said:**
> To do it on help.ubuntu.com,

just make a url like this:

[https://help.ubuntu.com/community/MythTV_BLAH](https://help.ubuntu.com/community/MythTV_BLAH)

and then edit it.  Creates the page for you


Thanks, didn't know it was that simple. Need to work more with wiki I see.

---

### Post by DutchLoki on 2008-04-21
Anyone else with ideas about a MythTV sattelite setup guide? 

Questions:
1) what's the best place to put such a guide?
2) Which sites do you know about this subject?
3) what subjects need to be covered?

---

### Post by hllywood14 on 2008-04-21
I would be very interested in such a guide....i think it will be a great addition to the forums and show members other cheaper ways to use there systems from everything to desktop use to media server..A great idea..hope to be reading it soon

---

### Post by DutchLoki on 2008-04-25
I'm working on it. Hardware compatibility seems the biggest problem. it's difficult to point people to the right site about choosing compatible hardware. 

For the rest, i think it's covering most stuff now. Also going to ask the Mythbuntu team to include it in the official site.

---

### Post by hllywood14 on 2008-04-25
can't wait to see the outcome...please let us know where to find it..

---

### Post by DutchLoki on 2008-04-26
> **DutchLoki said:**
> I'm working on it. Hardware compatibility seems the biggest problem. it's difficult to point people to the right site about choosing compatible hardware. 

For the rest, i think it's covering most stuff now. Also going to ask the Mythbuntu team to include it in the official site.


Paused working on the tutorial, my (only)dvb card has left this world... I'm about to order two new ones soon. First I will do some reading about using dvb-s with multiple lnb's or using diseqc for positioning my dish. (read: I wanna know what I can do in mythtv with this). 

anyone suggestions or more information/links about diseq, multiple lnb's etc?

---

### Post by hllywood14 on 2008-05-10
what kind of information are you looking for? send me a pm and I think I can help you find a few things you my be looking for..of course this is outside of the myth software..mainly hardware information i can provide.

---

### Post by Trollslayer on 2008-05-11
> **DutchLoki said:**
> I'm working on it. Hardware compatibility seems the biggest problem. it's difficult to point people to the right site about choosing compatible hardware. 

For the rest, i think it's covering most stuff now. Also going to ask the Mythbuntu team to include it in the official site.

Edit: solved.

Agreed, one problem with hardware is chip manufacturers won't release data sheets so others can write linux drivers. :(

---

### Post by DutchLoki on 2008-05-29
> **hllywood14 said:**
> what kind of information are you looking for? send me a pm and I think I can help you find a few things you my be looking for..of course this is outside of the myth software..mainly hardware information i can provide.

Thanks hllywood14, but I manage. I've done some work on it, but needs to take some screenshots with it in version 8.04, which I needs to install on my system first. HOPEFULLY this weekend. 

I think the manual is fine now.

---

### Post by drifting on 2008-06-24
I await with baited breath, two Hauppauge Nova-S sitting here waiting for your guide :-)

Regards
Paul.

---

### Post by DutchLoki on 2008-07-04
> **drifting said:**
> I await with baited breath, two Hauppauge Nova-S sitting here waiting for your guide :-)

Regards
Paul.

See my reply to your PM. Hope this solved it.

---

### Post by DutchLoki on 2008-08-29
You can find a first version of the DVB-S (satellite) guide on the link below. Next week i'll add an example setup from begin to end and more information about gathering channel data and settings. 

I think its important to have a good manual and documentation to get a larger end-user and developer-base, the more people use MythTV and help maintain the code and skins the longer the project will grow and stay alive.
 
Also a wiki based MythTV-manual is the way to go to get maximum help from us users(although this always seems a little disappointing).

Wiki-based manual (feel free to contribute): 
[http://www.mythtv.org/wiki/index.php/User_Manual](http://www.mythtv.org/wiki/index.php/User_Manual)

Let me know if you have any suggestions or edit the manual yourself (thats why its wiki based). 


Post scriptum, 
If anyone from the MythBuntu community would like to add this guide to the official manual, its fine by me (I noticed this topic was missing in the official guide).

---

### Post by bone2006 on 2008-08-29
I'm using GeniaTech DVB-S PCI Card and pretty happy with it.   I'd recommend it for a few reasons, it's pretty inexpensive, but if you have a small tiny case for your HTPC needs then the bigger cards won't fit into the case.   I have a microATX case that almost all cards won't fit into the case, the case is about the size of a DVD player.  I went to built on video card, so that I could get everything put in a little box....
The bracket around the GeniaTech DVB-S PCI Card had to be removed to fit into the low profile case.

The card is supported out of the box on mythbuntu 8.04 original kernel.  You can pick one up for 40-50 bucks.

TWINHAN DVB-S cards are another popular DVB-S card, but those are just too big to fit into my case.

---

### Post by DutchLoki on 2008-09-04
> **bone2006 said:**
> I'm using GeniaTech DVB-S PCI Card and pretty happy with it.   I'd recommend it for a few reasons, it's pretty inexpensive, but if you have a small tiny case for your HTPC needs then the bigger cards won't fit into the case.   I have a microATX case that almost all cards won't fit into the case, the case is about the size of a DVD player.  I went to built on video card, so that I could get everything put in a little box....
The bracket around the GeniaTech DVB-S PCI Card had to be removed to fit into the low profile case.

The card is supported out of the box on mythbuntu 8.04 original kernel.  You can pick one up for 40-50 bucks.

TWINHAN DVB-S cards are another popular DVB-S card, but those are just too big to fit into my case.

Thanks for the suggestions. I personally like the technotrend budget cards, which are cheap and well supported under linux and mythtv. i will take a look at them.

---

### Post by DutchLoki on 2008-10-03
Updated the DVB-S (satellite) guide on the MythTV wiki. 

[http://www.mythtv.org/wiki/index.php/User_Manual:Setting_up_DVB-S_for_satellite](http://www.mythtv.org/wiki/index.php/User_Manual:Setting_up_DVB-S_for_satellite)


Any comments or suggestions are welcome.

---

### Post by chene on 2008-10-07
> **DutchLoki said:**
> Updated the DVB-S (satellite) guide on the MythTV wiki. 

[http://www.mythtv.org/wiki/index.php/User_Manual:Setting_up_DVB-S_for_satellite](http://www.mythtv.org/wiki/index.php/User_Manual:Setting_up_DVB-S_for_satellite)


Any comments or suggestions are welcome.

would adding a section for, or a link to, setting up encrypted channels be appropriate?

---

### Post by laga on 2008-10-08
> **chene said:**
> would adding a section for, or a link to, setting up encrypted channels be appropriate?


Using a hardware CAM + CI: yes
Using a softCAM: no

---

### Post by DutchLoki on 2008-10-10
> **chene said:**
> would adding a section for, or a link to, setting up encrypted channels be appropriate?

Yes it would, i'll add it as soon i've time for it (ofcourse anyone reading this can add it as well, its wiki based).

Cheers, loki

> **laga said:**
> Using a hardware CAM + CI: yes
Using a softCAM: no

Don't do that... making any mentioning about encrypted television an topic about softcams. It sounds like a phobia.

---

### Post by laga on 2008-10-11
Hi,

I'm afraid there's a misunderstanding :)

I'm not condemning the use of encrypted channels. As I said, there are ways to watch them legally. These usually involve monthly payments to get a subscription card. Of course, softcams can be used with a subscription card. But that's a grey area.

Here are the rules for the #mythtv-users IRC channel regarding softcams: [http://www.mythtv.org/wiki/index.php/IRC#Softcam](http://www.mythtv.org/wiki/index.php/IRC#Softcam)

I'd be very surprised if that didn't apply to your DVB-S guide as it resides in the official MythTV wiki :)

---

### Post by DutchLoki on 2008-10-11
> **laga said:**
> Hi,

I'm afraid there's a misunderstanding :)

I'm not condemning the use of encrypted channels. As I said, there are ways to watch them legally. These usually involve monthly payments to get a subscription card. Of course, softcams can be used with a subscription card. But that's a grey area.

Here are the rules for the #mythtv-users IRC channel regarding softcams: [http://www.mythtv.org/wiki/index.php/IRC#Softcam](http://www.mythtv.org/wiki/index.php/IRC#Softcam)

I'd be very surprised if that didn't apply to your DVB-S guide as it resides in the official MythTV wiki :)

I know about those rules, i'm following them for some time now ;) I meant that every time someone asks a questions about encrypted channels, someone needs to start about not to talk about softcams. Please juist hold the horses untill someone does talk about it... 

by the way thanks for clarifying your point.

---

### Post by Tony1977 on 2009-01-09
Hi guys.

new to the board but hopefully here to stay... :D

Just tryng to get a how to guide on how to set up my mythbuntu 8.10 with my hauppauge HD Sat card really.
Will look into the DVB-S Route,but i dont know if there's something avaliable for DVBS2 Cards...

Thanks for good work.

Tony

---

