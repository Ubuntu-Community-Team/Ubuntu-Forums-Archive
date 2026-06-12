---
title: "Deconflicting analog and digital recordings on the HVR-2250"
date: 2011-05-04
forum: Mythbuntu
---

### Post by johnlatz on 2011-05-04
I have a problem that cropped up this week immediately after upgrading to Mythbuntu 11.04.

First - my config:
Recently upgraded to mythbuntu 11.04
MythTV Version   : v0.24-250-g56c54fa
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.0

single frontend/backend system
HVR-1600 card, on which the mechanical connection for the digital side is broken, so effectively analog only
HVR-2250 card

I upgraded to 11.04 specifically to get the 2.6.38 kernel and with it the SAA7164 driver in order to enable the analog recording capability of the HVR-2250.  When I did, my backend started crashing.  

I seem to have spotted a problem - when I schedule recordings, sometimes Myth decides to record two analog recordings (using the single HVR-1600 channel, and one of the two HVR-2250 channels) along with two digital recordings (attempting to use two of the HVR-2250 channels).  The problem is, with the HVR-2250, you can only use two channels total - and in this case myth is trying to use three (one analog, two digital).

So my question is - how do I make MythTV recognize that if "digital-1" is being utilized, "analog-1" is not a valid option?

John Latz

---

### Post by LowSky on 2011-05-05
Easy fix.. open the backend, and go to channel editor. Change the name of the channel slightly

for instance: If the channels names are the same like WNBC, then mark one NBC-Analog, the other NBC-HD. The data will still pull correctly as it is a number with schedulesdirect.org. Then from the frontend edit the recording option for which tuner or channel you wish to use for the recording.

---

### Post by johnlatz on 2011-05-06
Sorry, you misunderstood.

(First - I have small children who have no clue what a TV commercial or scheduled broadcasting is thanks to MythTV.  Second - I pay $20/month for basic cable, for which I get a slew of analog channels plus the digital and HD channels of local broadcast market stations).

At 9AM, the machine is set up to record Dora the Explorer on Nick (analog), Mickey Mouse Clubhouse on Disney (analog), and Sesame Street on PBS (digital).  Three distinct and totally separate channels.  Nick is set to be recorded via the HVR-1600, Disney is set to be recorded via the HVR-2250 channel 1 [Analog-1], and the PBS is set to be recorded via the HVR-2250 channel 1 [Digital-1].  The problem is that the HVR-2250 can/should only be able to record analog or digital from channel 1 at the given time, apparently there is some sort of conflict initiated by this condition.

If I notice this going on, I can manually override and either force the offending recording to an alternate card channel, or failing that cancel the offending recording.  When I don't, bad things happen.


So my question is - how do I clue in MythTV that Analog-1 and Digital-1 should be considered the same recording device, and thus cannot be used at the same time?

---

### Post by LowSky on 2011-05-07
Ah, ok... 

because the analog drivers are not perfect, you end up losing a digial tuner, something I dont think you might like.

So in thebackend the 2250 has two digital tuners and two analog tuners. but in reality it has two tuners that can either do digital or analog. In Windows you can use all 4 at once and there is not problem. in Linux you can't because of poor driver support. So you can only use analog on one tuner and digital on the other.

So the fix is go into the backend and only apply one digital tuner.. and the apply one analog tuner of the other tuner... basically if you use video0  (analog) you cant use dvb/adapter0, but you can use /dvb/adapter1 (if this makes sense).

---

### Post by tgm4883 on 2011-05-07
> **LowSky said:**
> Ah, ok... 

because the analog drivers are not perfect, you end up losing a digial tuner, something I dont think you might like.

So in thebackend the 2250 has two digital tuners and two analog tuners. but in reality it has two tuners that can either do digital or analog. In Windows you can use all 4 at once and there is not problem. in Linux you can't because of poor driver support. So you can only use analog on one tuner and digital on the other.

So the fix is go into the backend and only apply one digital tuner.. and the apply one analog tuner of the other tuner... basically if you use video0  (analog) you cant use dvb/adapter0, but you can use /dvb/adapter1 (if this makes sense).

I'd have to dig deeper into it, but I believe there is a better fix than that. The issue with the fix you propose is that you can only record a single digital recording, even if you aren't recording an analog recording. My understanding of this situation is that if one wanted, they could record 2 digital recordings if the analog side wasn't being used.

IIRC, the correct fix is something similar to tuner groups. Basically you set the card up in mythtv so that 2 tuners belong to the same group, and mythtv knows that only a one of those tuners can be used at a time.

:EDIT:

It's called an input group, and is discussed a bit here [http://www.mythtv.org/docs/mythtv-HOWTO-12.html](http://www.mythtv.org/docs/mythtv-HOWTO-12.html)

> 
Input 1 and input 2 receive content from the same set top box and the channels can not be tuned independently. Therefore only one of these two inputs should be used at any given time. The solution is to create an "Input Group" with mythtv-setup in "Input connections". Including these two inputs in the same Input Group will tell the scheduler that these are mutually exclusive and may not record at the same time. Inputs 2 and 3 are automatically mutually exclusive because they are on the same card so there is no need to create an Input Group for these inputs.


---

### Post by johnlatz on 2011-05-07
Sweet - The link seems to explain exactly my issue and the solution, I'll have to try it later this weekend.  Thanks TGM.

I'll mark this solved when I get it working

---

### Post by gedakc on 2011-05-20
Hi johnlatz,

I am experiencing a similar problem with a dual digital, dual analog HVR-2250 card.  I have tried a variety of combinations of input group names but so far have been unsuccessful in properly setting up the card so that only two inputs (either digital or analog or a combination) can be used at one time.

Would you be able to reply here with the names you used for "Input group 1" and "Input group 2" for your digital and analog tuner?

---

