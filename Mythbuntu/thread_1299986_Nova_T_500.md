---
title: "Nova T 500"
date: 2009-10-24
forum: Mythbuntu
---

### Post by dualboot on 2009-10-24
I'm working well with a version 8 set up, but have not so far had any success with 9.04 or 9.10beta/RC.  I am having graphics problems, but also tuners dying, and this second problem is concerning me most.  Reading around I'm seeing comment that make me wonder if anyone has the NOVA-T 500 working properly with version 9.anything of Mythbuntu.  At best it seems that people have to regularly power their machines right down and wait a few minutes.

Can anyone post if they are working OK with version 9 ?

---

### Post by AJ1000 on 2009-10-24
I have got it working upgrading from 8.10 to 9.04 (when 9.04 was released) and now to 9.10 (using the ubuntu desktop rather than kde or xfce one). I know solutions to most issues. I am trying to build a clean 9.10 version which again works apart from an extra session which has appeared as I am using the ubuntu desktop.

What problems are you having? If you wish you can email me directly if required.

---

### Post by dualboot on 2009-10-24
I've spent the last few days reading up on things, and checking them against my working set-up.

Hearing that you have got thing working have motivated me to have another go, so I've just put the new hard drive back in, looked in dmesg, and the first thing I've noticed is the driver is dvb-usb-dib700-1.20.fw

I've seen several people say to stick with 1.10 - what are you using ? I assume this came from the 'restricted drivers' choice (or are firmware and drivers different things ?)

---

### Post by AJ1000 on 2009-10-24
No need the 9.10 firmware works for me, it was needed to be changed in 9.04.

 I have an nvidia 5200 so I am using the restricted drivers as well.

Are you doing an upgrade or clean install?

---

### Post by dualboot on 2009-10-24
clean install (swapping hard drive) of the release candidate.  So you reckon the 1.20 firmware isn't a problem ?  I've also notice that there's no options file in /etc/modprob.d/ - do you have one - to set the lna ?

---

### Post by Zeedok on 2009-10-24
> **AJ1000 said:**
> I have got it working upgrading from 8.10 to 9.04 (when 9.04 was released) and now to 9.10 (using the ubuntu desktop rather than kde or xfce one). I know solutions to most issues.

I love your confidence because I need help and am getting desperate. I am using the (Hauppauge Nova-T-500 MCE Dual DVBT SD/HD tuner) on a mythbuntu 9.10RC clean install.  I am having problems locking on to some channels.  The signal information listed at the bottom of the screen indicates Signal stength 99%, but the BE is at the maximum >65k.  This is the exact hardware setup that was tuning fine with 9.04 yesterday.  I have tried enabling the LNA with the suggestions [you gave in another thread]("http://ubuntuforums.org/showthread.php?t=1294971") but it is still not working.

Any suggestions??

Thanks

---

### Post by AJ1000 on 2009-10-24
Yes you need to add the options.conf file to force activation of the amplifier in the nova t. I am assuming you know how to do this. If not let me know.

---

### Post by AJ1000 on 2009-10-24
Zeedok,

Check out here:

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

especially the 

'Testing The DVB Card' section

Hope it helps. I have had nova t 500 working for a week now on 9.10, and have gone through the pain you are experiencing, so I understand your frustration.

AJ1000

---

### Post by Zeedok on 2009-10-24
I've had alook at the thread - once I drilled down to the details regarding my card [I found this]("http://www.mythtv.org/wiki/Index.php/Hauppauge_WinTV_Nova-T_500_PCI"), which obviously wasn't much help.

EDIT: Sorry, didn't see your direction to the testing the card section, will have a look now.

Thanks

---

### Post by Zeedok on 2009-10-24
I starte following the guide.  I ran dvdscan, but it just said "Could not start the frontend"

Any ideas?

I think the guide suggests that I may have the older chipset, but the link just goes back to the empty wiki page . . .

---

### Post by AJ1000 on 2009-10-24
I am using the older chipset. See the guiguy thread for the last entry I posted on page 2

or search google for

mythtv pci nova t 500

---

### Post by Zeedok on 2009-10-24
OK, so after some difficulties I have managed to get the "testing your dvb cards" section to work.

I *think* I have been able to get a lock on one of the troublesome channels using tzap.
I have two transmitters near me, but when I run dvbscan/scan pointed at one of them I generate following channels.conf

```
ABC HDTV:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2314:0:544
ABC1:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:545
ABC2:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2307:2308:546
ABC1:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:547
ABC3:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:548
ABC DiG Radio:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:0:2317:550
ABC DiG Jazz:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:0:2318:551
7 Digital:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:513:514:1312
7 Digital 1:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:513:514:1313
7 Digital 2:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:545:546:1314
7 Digital 3:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:513:514:1315
7 HD Digital:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:577:0:1316
NINE DIGITAL:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:519:720:1057
NINE HD:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:0:1058
GO!:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:517:700:1059
```

Which lists some, but not all all my available channels.  It does pick up NINE DIGITAL, which is the one station I can't get a reliable lock on.

Not sure where to go next.

---

### Post by AJ1000 on 2009-10-25
Since you have two transmitters near you ... try to see which is the best for channels. I am in the UK, so I can not comment on the channels you found.

Things to do:

Run the following

1) dmesg|grep -i dvb 

Check your nova t is in a warm state.

2) mythtv-setup [this is a condensed version]

Select capture cards > (New capture card)

Change card type to DVB DTV capture card

The device number should automatically be filled in to the default which is adapter0.

Select Finish and then go back to the main menu.

Select Video Sources > (New Video Source)

Type in a source name e.g. TunerOne

Select the listings grabber (I use EIT)

Select Finish and then go back to the main menu.

Select Input Connections > DVB: ... (DVBInput) -> (None)

Select the Video Source which was previously defined as TunerOne

Select scan for channels [and do the screens shown ... this should have found the channels]

Select Next and Finish until you go back to the sub menu screen which should now say DVB: ... (DVBInput) -> (TunerOne)

Go back to the main menu and then leave mythtv-setup. 

Make sure you run mythfilldatabase if it has not already been done.

Reboot

Mythfrontend should now be able to see TV.

Note: A similar procedure to the above can be done for tuner 2, but in the capture cards section select DVB Device number adapter1 rather than adapter0.

---

### Post by Zeedok on 2009-10-25
Thanks for your suggestions. I have set-up the sources, inputs and channels before, so I know the procedure.  I have checked, and my card is using the up to date firmware and is in the warm state.  I've also cold rebooted.  No luck.

Since this was a clean install - and I initially had everything working fine on 9.04 (I later stuffed up lirc, hence the clean install), I just reinstalled 9.04.  The tuner still has some difficulty picking up all the channels, but manages (with the LNA enabled) to lock them all.

My conclusion then is that something has changed from 9.04-9.10 which has caused problems (for my setup anyway).  I'm not sure if I have a weak signal (it is amplified as I am in an apartment) or what, but 9.04 is a better bet for me at the moment.

Are all cards this troublesome (the tuner in my TV is perfect)?  I think if there was a gui manual channel editor - ie where you could enter in the transport and just scan for that channel - that would be helpful.

---

### Post by AJ1000 on 2009-10-26
Have you tried stopping the 'Mythbuntu back end' and using MeTV or Kaffeine instead?

With Kaffeine you specify the transmitter.

---

### Post by bruk on 2009-10-26
I can't say I've had any *more* problems with my Nova-T in 9.04 than with my previous 8.10 setup. That's not to say there aren't some problems straight out of the box that need fixing. The one that I think you're experiencing is some iffy i2c usb shenanigans, where one of the tuners turns off, pretty much crapping all over myth and requiring a reboot. I stumbled across the actual fix somewhere purely by accident, despite searching umpteen forums...

You have to make two changes in myth setup, for both of your tuners (the nova-t is a dual tuner, so you should have two). On both tuners change the query interval to 150 ms/msecs/milliseconds. And on your second tuner, turn off the eit scan.

Without these tweaks, my myth box needed rebooting every eight hours or so. With them it's pretty much rock solid, although it may miss a recording once in a blue moon.

HTH

---

### Post by Zeedok on 2009-10-26
> **AJ1000 said:**
> Have you tried stopping the 'Mythbuntu back end' and using MeTV or Kaffeine instead?

With Kaffeine you specify the transmitter.

I tried Kaffeine - it seemed to pick up the transmitters and channels, but didn't quite work for some reason.  At that point I got impatient and did a reinstallation.  In a month or two I might try upgrading to 9.10 to see if things go more smoothly (after I clone current setup that is . . .)

---

### Post by Zeedok on 2009-10-26
> **bruk said:**
> I can't say I've had any *more* problems with my Nova-T in 9.04 than with my previous 8.10 setup. That's not to say there aren't some problems straight out of the box that need fixing. The one that I think you're experiencing is some iffy i2c usb shenanigans, where one of the tuners turns off, pretty much crapping all over myth and requiring a reboot. I stumbled across the actual fix somewhere purely by accident, despite searching umpteen forums...

You have to make two changes in myth setup, for both of your tuners (the nova-t is a dual tuner, so you should have two). On both tuners change the query interval to 150 ms/msecs/milliseconds. And on your second tuner, turn off the eit scan.

Without these tweaks, my myth box needed rebooting every eight hours or so. With them it's pretty much rock solid, although it may miss a recording once in a blue moon.

HTH

I'm not sure what the issue was.  I have no problems with 9.04 - in fact I have since reverted to it - but some amplifier or tuner setting was clearly mucked up in 9.10RC.  I'm hoping that after a month or so any kinks in 9.10 with be ironed out and I can upgrade without problems . . .

---

