---
title: "pppoe verizon dsl &amp; different modem/routers"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by Larry B on 2009-06-26
A noob here so hide your face when you laugh (you don't want to make me cry) :)

Been doing a bunch of research trying to get a handle on networking and i think i may have learned just enough to be dangerous. I've seen several threads from folks with the same or similar probs as i had and wanted to offer help, but i'm not confident i have a good enough understanding of WHY what worked for me did so. Also there is the matter that what worked for me may not work for others. Tis better to offer no advice than bad advice. So, with this in mind i'd like to see if my "understanding" of things is correct.

Following is what i "THINK" i've learned. Please correct and/or comment at will...... (Also - this applies to hardwired DSL not (necessarily) to wireless hook ups.)

Verizon DSL requires PPPoE.

PPPoE is essentially the means by which one enters a username 
and password.

PPPoE can be "programed" or "saved" in the firmware of some dsl modems and/or routers and/or modem-router combos.

Many (perhaps all) Verizon supplied DSL modems (typically if not exclusively, Westell) come pre-configured to NOT work until "activated". Basically this means they are pre-configured to work with the installation CD and not much else until certain internal settings are adjusted.

On Win platforms this is accomplished by the Verizon install CD but can also be done by manual configuration.  The key phase being the insertion of the username & password.

On a Ubuntu platform it can be done by manual configuration but must be approached differently depending on whether you have an existing Verizon DSL account which make for a relatively easy manual configuration, or a new Verizon DSL account which makes for a more difficult manual configuration. This is because:
    if you already have an _existing_ account you can just use pppoeconf to enter the username and password (among other things)but,
    if it is a _new _account you need to do what Verizon calls "activating your new account" to ACQUIRE a username and password, which is essentially what the install CD helps you do.


Is the above pretty much correct? If so, then i will have just a couple more questions to confirm and i should be just about ready to tackle the importance of DHCP and it's relationship to PPPoE.

:popcorn:

---

### Post by superprash2003 on 2009-06-27
well i have no idea about how the verizon activation part works but the rest of it is absolutely correct!!

---

### Post by Larry B on 2009-06-29
Thanks for the reply Super. I needed the confidence builder. :p



I've seen several threads about folks with problems using Ubuntu with Verizon and i DO think the solution is often dependent on whether it's a new account or an existing one, or more precisely, if the modem has been #1) "activated" as Verizon calls it and/or #2) if it has been previously "activated" using someone elses username and password. 

Take a look, if you have time, at this:
[http://www.bensdrivel.com/?p=142](http://www.bensdrivel.com/?p=142)

The above is one of several tips i've found that let's you "activate" a Verizon/Westell modem without the Verizon/Windows install CD. However, i've seen reports from others, and can confirm myself; that the formal steps, the names of the various dialogue boxes and tabs you may encounter vary slightly from one party to another. 

Am i correct in my assumption that the url is to the modems firmware?  If so, then that would explain the variation people with different Westell models are encountering, no? And why it helps to know why you are doing what you are doing and to not just be doing it blindly.

Would i also be correct in assuming that not all modems need this kind of "activation"?  I ask this because my first install of Ubuntu (Dapper) was on a box using a Zoom X5 modem/router and pppoeconf was all that was needed to get it up and running. But with my next install (Jaunty i think) i was using a Verizon/Westell 6100 and pppoeconf could not get it up and running until AFTER i walked through steps similar to those described in the above link.

I'm reasoning that the thing pppoeconf does NOT - CAN NOT - accomplish on a new account (OR a new Verizon/Westell modem) is step seven from the above link:
"7. Click apply, and then back at the broadband connection screen, disconnect the "Auto registration" connection and then connect the new one you just made. Also, don't forget to make it default."

The upshot of all of this is that if my understanding of things is correct, then Verizon simply - and quite Unecessarily - makes you jump through hoops to use anything other than Windows or Macs.  

Once i feel i have a working comprehension of all of this i'll feel much better about helping other Verizon users on this and other forums, as well as installing Ubuntu on some friends and families boxes.  As it stands, i'm a bit hesitant - first rule being "first do no harm".  :)

---

### Post by superprash2003 on 2009-06-30
i dont think its accessing the modem's firmware but just the modem's settings.. well i really dont know what this "activation" is all about.. typically you just get a username/password from your ISP and enter it either in your modem or in ubuntu's pppoeconf and your on!!i guess this is only for verizon modems.. for other modems it should be the usual way!!

---

### Post by Larry B on 2009-07-07
> **superprash2003 said:**
> i dont think its accessing the modem's firmware but just the modem's settings.. well i really dont know what this "activation" is all about.. typically you just get a username/password from your ISP and enter it either in your modem or in ubuntu's pppoeconf and your on!!i guess this is only for verizon modems.. for other modems it should be the usual way!!

Super, after more playing around (and self education)i'm sure you are spot on - it's the settings, not the firmware.

The activation thingy is all about setting up a Verizon _account_. Verizon ONLY supports Win and Mac platforms. The menu driven (install shield whatever) Verizon Install CD comes with a Westell 6100 (in my region anyway) and the modem installation is inter weaved with the formal DSL _account_ activation. 

I've not tried, but i have a suspicion that you can't run the (CD)modem configuration program separately from _account _activation. This makes it difficult for us noobs to use Verizon with Ubuntu or any flavor..... 

The install CD does among other things, configure the modems settings - pppoe, Uname &Pword, etc.. One setting it apparently configures -- this is pure speculation on my part -- is that it sets up the modem to require a WAN miniport.  Perhaps to make it backward compatible with Win95/98/ME because they require a Wan miniport???, or maybe certain network cards require one ???????  I don't know, but i DO know that XP, does not inherently **require **one with either the Westell or the Zoom X5 modem on either a linksys network card or an embedded Realtek network interface if the modem is properly configured.

Of the two modems the Zoom is far easier to congigure. Once you access the settings pages Zoom even provides an auto detection routine. If auto detect runs successfully all you have to do is click a link marked pppoe and enter your Uname and Pword and you are done. The Wetell setup pages on the other hand, are ....... confusing to say the least. Whether this a feature of the Westell 6100 per se or only those made for, and pre-configured for, Verizon, i do not know. 

One thing i found confusing was this:
I had one Westell 6100 that was working fine on both WinXP and Ubuntu.  I swapped it out for a physically different one of the  same make and model (another one from Verizon even) and it would not work. No matter what addy you entered the browser always took you here: [http://192.168.1.1/verizon/redirect.htm\](http://192.168.1.1/verizon/redirect.htm\) 

(Interestingly enough if you just try to type this addy into a browser on a working connection you get a 404 error with a link to a page named "Diagnose". For an explanation of this addy see this link from post #3 [http://www.bensdrivel.com/?p=142](http://www.bensdrivel.com/?p=142) ). 

I wasn't aware of bens Drivel page when i tried to use another persons Westll so i don't know if making the changes he recommends would have fixed things or not. I suspect hey would have.

The upshot of all of this is that i think the Westells from Verizon come pre-confiured to this redirect page until an billing account is set up and then the CD changes the modems configuration. I also think that the changes made to the settings by the CD are such that the modem will only work with YOUR account. I think this is accomplished by storing a Uname and Pword in the modem **BUT** also requiring that Uname and Pword to match the one tied to the Wan miniport used by XP. 

I say this because once the Westell is set up and working, a reinstall of XP itself installs a Wan miniport PPPOE and ask you for your Uname and Pword.

I'm not certain of much of the above but i do know the following:

1) A Westell configured by the Verizon Install CD on an XP platform can not be made to work in Ubuntu simply by running pppoeconf. You must first follow the steps in Bens Drivel (above link). Once you've done that, you can then use pppoeconf.

2) Once you've successfully configured the Westell in Ubuntu, it will still work in XP with the added benefit that it will no longer require you to "connect" by clicking a "MyInternet" or "Verizon" or whatever you may have named it, Icon (the WAN miniport). You will be connected on boot up providing you told pppoeconf to configure your modem to be always on under Ubuntu).

3) A retail boxed Zoom X5 can be set up using just pppoeconf. At east if it is hooked up initially using the factory default settings. If it has been previously used and those settings changed......?  I don't know..... But a paper clip to the reset button should fix that. 


Now, assuming i've not completely blundered in the above, i have just one more (i hope)question and i think i'll be ready to post a help page for Verizon users wishing to run Ubuntu - either in an XP dual boot or Ubuntu solo and no matter if they are applyig for a new account or simply using an existing one.

First, on an XP system configured by the Verizon install CD,  you will find (at minimum) under "Network Connections" at least two entries. 

One will be "Local Area Connection" of type "Lan or high speed Internet" and will be associated with whatever network device you are using (one of mine is Marvel Yukon). The other one will be named whatever you named it on installation and will be of type "Broadband" and will be associated with "WAN Miniport (PPPOE)".  This is the icon you must click to get online in the default Verizon install under XP.

Am i corrected that this Wan miniport icon serves the same purpose as pon in Ubuntu?  If so, then the need to use the miniport in XP is based on the Verizon install CD configuration settings and NOT necessity! I say this because once configured to be always on in Ubuntu, the wan miniport is no longer needed in XP. This has been true for both the Westell 6100 and the Zoom X5.

---

### Post by Larry B on 2009-07-07
Super, i was so zoned out trying to compose the previous post i forgot to thank you. So thank you.  :lolflag:

---

### Post by superprash2003 on 2009-07-08
yes WAN miniport = pppoeconf . the redirection is i think because of a specific verizon firmware which has been installed on the modem..
  ideally if this is a DSL connection and you have the user account already and you know the vpi/vci values you could get it to work with any modem ..

---

