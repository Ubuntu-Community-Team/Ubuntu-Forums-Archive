---
title: "HDHomerun tuner"
date: 2011-07-31
forum: Mythbuntu
---

### Post by williammanda on 2011-07-31
I'm looking to change tuners. The HDHomerun dual tuner seems to be a good candidate. I'm looking for feedback from existing owners. Please state your pro's and con's.

---

### Post by uteck on 2011-07-31
I like it since it lets me record over-the-air digital and unencrypted cable at the same time.  Depending on the multuplexing, you can record 2 shows on each output for a total of 4 shows at once.
Being network attached gives you more options in placement.  I have my Myth-server in the basement, but the HDHomerun is on the second floor were the reception is better.  Otherwise I would have to run cable for the antanna.
I think the price is dropping now that newer cable-card tuners are coming out.  I saw Woot had them on sale not too long ago.

I have had some problems with the virtual tuners.  Sometimes when I tune to a channel it does not display anything.  I have to use the menu and switch to the other virtual tuner, then it works.  Currently I don't use it to record much since my over-the-air recpetion is not that good at my location, especially if the weather is bad.  
My cable has not converted over to all unencypted digital yet, so I only have the local channels avalible so far, so I do not use it that much so the multiple recordeing has not been tested much.  The few times I have used it worked, but channel flipping has casued problems.

I am happy with it, and will be even more happy when I get all the basic channels with it, but if it were not for my cable company not encrypting their basic digital signal I would only be using it as a backup tuner when I am recording something from the HD tuner box.

---

### Post by AKADAP on 2011-07-31
It is very easy to set up, and requires no drivers under Linux.
The manufacturer does a good job of supporting linux.

Some have reported that it is not the most sensitive tuner for OTA reception. I have not noticed this myself.

I have noticed that it is susceptible to being over-driven by nearby FM stations causing problems on VHF High TV stations. I fixed this with an FM Trap.

---

### Post by mathog on 2011-08-01
> **AKADAP said:**
> 
Some have reported that it is not the most sensitive tuner for OTA reception. I have not noticed this myself.


I have seen OTA channels that comes in better with the TV tuner than the HDHomerun.  However, this only happens when the OTA station is marginal on every tuner.  That is,  where the TV tuner is bad (breaks up once a minute) the HDHomerun may be horrible (breaks up every couple of seconds).  I have yet to find a channel that came in well (no break ups) on the TV that didn't also come in as well on the HDHomerun.

---

### Post by williammanda on 2011-08-04
Thanks for all the replies. I ended up buying the HDHomerun. I have a question concerning the use. I have multiple tuners: pcHDTV 5000, FusionHDTV5 RT Gold and HDHomerun. When selecting a tv station to view, on both the pcHDTV 5000 and FusionHDTV5 RT Gold, the signal gives me the actual strength of the signal ie 80% (this shows up right after selecting the channel). The HDHomerun says 50% for every station for both tuners. I have the latest firmware version 20110729. I didn't scan for channels since I already had that setup with the existing tuners. Also I used windows to setup the unit, which wasn't much (what source type - digital cable). Other than that it seems to work fine. Please advise.
Thanks

---

### Post by williammanda on 2011-08-04
I have searched the Silicondust site but can not find what the 2 LED's on the right of the unit (HDHR3) are for. Please advise.

---

### Post by uteck on 2011-08-05
> **williammanda said:**
> I have searched the Silicondust site but can not find what the 2 LED's on the right of the unit (HDHR3) are for. Please advise.
I think they indicate which tuner is in use.

---

### Post by williammanda on 2011-08-05
> **uteck said:**
> I think they indicate which tuner is in use.

Thank you! I also found this information from the SiliconDust forums.

---

### Post by mathog on 2011-08-05
> **williammanda said:**
> I have a question concerning the use. I have multiple tuners: pcHDTV 5000, FusionHDTV5 RT Gold and HDHomerun. When selecting a tv station to view, on both the pcHDTV 5000 and FusionHDTV5 RT Gold, the signal gives me the actual strength of the signal ie 80% (this shows up right after selecting the channel). The HDHomerun says 50% for every station for both tuners.

Is the antenna cable split symmetrically?

Do you have some reason to think that every tuner has the same value for the amount of power corresponding to 100%?

---

### Post by williammanda on 2011-08-05
> **mathog said:**
> Is the antenna cable split symmetrically?

There is no splitter.

> Do you have some reason to think that every tuner has the same value for the amount of power corresponding to 100%?

? amount of power? Signal percentage what we are talking about...the measure of the channel signal strength.
Please re-read my post....I explain that the other tuners reflect what the actual signal % is (this could be a number between 80 - 100) but the HDHomerun displays 50% for the signal on each channel. 50% is not displayable.

---

### Post by mathog on 2011-08-05
> **williammanda said:**
> There is no splitter.


How are you feeding the output from a single antenna into 4 tuners without a splitter?

---

### Post by williammanda on 2011-08-05
> **mathog said:**
> How are you feeding the output from a single antenna into 4 tuners without a splitter?

The HDHomerun is in a different room than the other tuners. I fail to see your logic in trying to answer my original question.

---

### Post by mathog on 2011-08-06
> **williammanda said:**
> The HDHomerun is in a different room than the other tuners. I fail to see your logic in trying to answer my original question.

We don't have a full description of your system. 

Assuming for the moment you have one HDTV source it probably comes into your house on a single coaxial cable.  You have 4 tuners.  In what manner is that cable attached to those tuners?  The amount of power that is sent into your house is finite.  Since one cannot attach a single coaxial cable directly to multiple tuners you must have some sort of cable splitter in place.  Most splitters try to send equal amounts of power to each output.  If you have a 2 way splitter at the first card, then a 2 way splitter at the second card, and finally a 2 way splitter feeding both of the HDHomeRun inputs, then each of the HDHomeRun tuners would be receiving 1/4 the power of the first video card, and 1/2 the power of the 2nd video card.  The sum of the power coming out of the split coax cannot exceed that going into your house - else the laws of thermodynamics are violated and you could build a perpetual motion machine out of split coaxial cables.  Since, at best, power is conserved, there is a limit to the number of times the coax signal can be split before one must employ an amplifier to boost its amplitude.

In my home we have 3 tuners in use (1 in the tv and 2 in the HDHomeRun) and these are fed from the single antenna feed by a 1:3 splitter, so they each receive an equal amount of signal power.

---

### Post by williammanda on 2011-08-06
> **mathog said:**
> We don't have a full description of your system. 

Assuming for the moment you have one HDTV source it probably comes into your house on a single coaxial cable.  You have 4 tuners.  In what manner is that cable attached to those tuners?  The amount of power that is sent into your house is finite.  Since one cannot attach a single coaxial cable directly to multiple tuners you must have some sort of cable splitter in place.  Most splitters try to send equal amounts of power to each output.  If you have a 2 way splitter at the first card, then a 2 way splitter at the second card, and finally a 2 way splitter feeding both of the HDHomeRun inputs, then each of the HDHomeRun tuners would be receiving 1/4 the power of the first video card, and 1/2 the power of the 2nd video card.  The sum of the power coming out of the split coax cannot exceed that going into your house - else the laws of thermodynamics are violated and you could build a perpetual motion machine out of split coaxial cables.  Since, at best, power is conserved, there is a limit to the number of times the coax signal can be split before one must employ an amplifier to boost its amplitude.

In my home we have 3 tuners in use (1 in the tv and 2 in the HDHomeRun) and these are fed from the single antenna feed by a 1:3 splitter, so they each receive an equal amount of signal power.

I'm sorry this has turned out this way. First, I'm an electrical engineer. Second, I understand very thoroughly the rule that power is a zero sum game and also that the cable company compensates for more than 1 tuner per home. Third, I supplied enough data up till this point that should have told you that the source signal coming to the HDHomerun tuner was sufficient. 

Lets layout the current situation again so there can not be any question.

Assumptions:
Cable company supplies a source signal that should take care of about four tuners on average per home.
Some tuners have a feedback mechanism ie signal %, that tells you the signal level.

Items use for testing:
pcHDTV 5500
FusionHDTV5 Gold RT
HDHomerun HDHR3-US
TV
Cable splitter

Test areas:
Location 1 - Mythbackend that has both the pcHDTV 5500 and FusionHDTV5 Gold RT. These are supplied the cable source via a splitter.
Location 2 - The TV or the HDHomerun are supplied by the cable source.

Test theory
Each tuner that has the capability of the signal source level feedback should reflect the current level for each station. Also the 80% level is the minimum for a valid picture.

History
After moving in I had the cable company validate the signal level at each outlet. Each outlet was at an acceptable level.

Test
I recorded the signal levels for HDTV and digital stations.

Location 1 - The HDTV stations ranged from 90 - 96 for both tuners and 80 - 87 for the digital stations.

Location 2 - This location only has one source, so only one device can be tested at a time. The TV reflected about the same results as location 1. The HDHomerun results were that there was a valid picture for every station but the signal% stayed at 50% for every station.

Conclusions
The source signal supplied by the cable company is very sufficient as shown by the results. One could expect that at least four tuners could be used in this current situation and still get acceptable results. All tuners displayed valid pictures for all stations. All tuners that were capable of reflecting the signal level worked except for the HDHomerun. Lastly, since the HDHomerun worked except for the signal% there must be a problem. Where that problem lies is still in question ie hardware or software. This is the question I am asking the forum.
Thanks

---

### Post by mathog on 2011-08-06
Ok, so there is a splitter somewhere in a wall or under the floor boards that sends the signal to your two coaxial cable locations.   Let's just consider location 2, a single coaxial cable outlet (right?).  When the TV is attached to it you see 90% signal strength and when the HDHomeRun is you see 50%.  Clearly the signal present there is the same so either the scales are not comparable or the HDHomeRun is losing signal somewhere or is just less sensitive.

Which HDHomeRun model do you have?  Mine has two tuners with two separate coaxial inputs.  The newer model has the same number of tuners but only a single coaxial input.  Therefore, the new model must have an internal splitter.  All else being equal, if the manufacturer didn't change the software between the models the same input to a separate input on the old model, when applied to the shared input on the new model, would result in half the power arriving at the tuner itself.  If you put a 1:2 splitter at location 2 and attach the TV to one side, and the HDHomeRun to the other, what do the TV and HDHomeRun show now?  If the signal strength meter is linear then it should be about 50% and 25%, but it is probably logarithmic, in which case you'll see something more like 85% and 45%.

---

### Post by williammanda on 2011-08-06
> **mathog said:**
> Ok, so there is a splitter somewhere in a wall or under the floor boards that sends the signal to your two coaxial cable locations.   Let's just consider location 2, a single coaxial cable outlet (right?).  When the TV is attached to it you see 90% signal strength and when the HDHomeRun is you see 50%.  Clearly the signal present there is the same so either the scales are not comparable or the HDHomeRun is losing signal somewhere or is just less sensitive.

Which HDHomeRun model do you have?  Mine has two tuners with two separate coaxial inputs.  The newer model has the same number of tuners but only a single coaxial input.  Therefore, the new model must have an internal splitter.  All else being equal, if the manufacturer didn't change the software between the models the same input to a separate input on the old model, when applied to the shared input on the new model, would result in half the power arriving at the tuner itself.  If you put a 1:2 splitter at location 2 and attach the TV to one side, and the HDHomeRun to the other, what do the TV and HDHomeRun show now?  If the signal strength meter is linear then it should be about 50% and 25%, but it is probably logarithmic, in which case you'll see something more like 85% and 45%.

If what you say is true then why do I get a signal level above 90% on the two tuners in location 1 on two different frontends working at the same time?

Again your logic and your lack of understanding are what is causing you to question something that is not valid. You obliviously don't have an electrical background or you wouldn't be making the statements that you have. I don't have the time or energy to keep answering you. Please let it go and move on. Thanks for your help!

---

### Post by nickrout on 2011-08-06
williammanda, clearly you are not getting understanding of your question here. Your question is why the hdhr appears to give the same signal strength no matter which channel, when other tuner give variable (and higher) results.

I understand the question but don't know the answer. However I suggest you might get more help on the muythtv users mailing list.

Another opportunity is to see if the windows client reports different figures, eliminating (or confirming) a bug in the linux driver, or myth's interpretation of the linux driver's reporting. 

Lastly you will no doubt have read that the hdhr's tuner is not as strong as some others. Whether that is affecting things is beyond my ken.

I am about to set mine when I get time, although mine is the dvb-t version.

---

### Post by uncle hammy on 2011-08-06
> **williammanda said:**
> If what you say is true then why do I get a signal level above 90% on the two tuners in location 1 on two different frontends working at the same time?

Again your logic and your lack of understanding are what is causing you to question something that is not valid. You obliviously don't have an electrical background or you wouldn't be making the statements that you have. I don't have the time or energy to keep answering you. Please let it go and move on. Thanks for your help!

You're being rather arrogant for someone who's wrong.  

A) A very simple and reasonable question was asked to try to gather information to help with your query and you treated the person TRYING TO HELP YOU like a twit.  Personally, I think you owe him / her an apology.

B) You said early on "There is no splitter", however you indicate two "Test" locations from one cable feed...not possible without a splitter...period.

C) The HDHomeRun 3 has two tuners and one input because it has an internal splitter.  So now at the very least, you've split a split signal (once to get from source to two locations, and then again at the HdHomeRun), which is far worse than splitting the source signal through a four or more way splitter.

D) You indicate your "test theory" and "history" about the cable company testing each outlet and it being acceptable.  Did you have them test test each side again after you split each outlet...because you have, as I just outlined for you.  I'm rather surprised a self described infallible electrical engineering god, who's clearly above the advice he's asking for would fall so easily into the "assumption trap".

E) You said "Also the 80% level is the minimum for a valid picture.".  That is false, signal strength is not nearly as important as people like to believe.  I have 3 HDHomeRun units and I have some channels that never get above 70% signal strength and routinely are in the 60ish range and the picture is flawless.  Signal and Symbol Quality are far more valuable a measurements.

However, to answer your question, HDHomeRuns tend to have a weaker tuner and you are trying to run them on a line that has been split at least once, then split again at the unit (as I thoroughly outlined).  They have also always been known to report a signal strength lower than other devices would and been a bit susceptible to not dealing well with "unclean" signals.  In fact, if you browse through the HDHomeRun firmware revision history, you'll see several times where they "improved signal strength reporting".  Cable troubleshooting 101 tells you to remove ALL splitters between the source and the tuner when working through weak / corrupt signals...which is what I am sure led to mathog's splitter query...though as an infallible electrical engineering god, I don't know why you would need to be told that.

I'd also be interested in having you run the HdHomeRun Config Gui, tune to a channel and report the the levels of all 3 measurements.  Though I probably wouldn't be inclined to offer much help with the way you've decided to treat "lesser" (apparently in your eyes) intellectuals.

---

### Post by williammanda on 2011-08-06
> **uncle hammy said:**
> You're being rather arrogant for someone who's wrong.

You might be putting foot in your mouth here! But I will let you do want you want!

> A) A very simple and reasonable question was asked to try to gather information to help with your query and you treated the person TRYING TO HELP YOU like a twit.  Personally, I think you owe him / her an apology.

B) You said early on "There is no splitter", however you indicate two "Test" locations from one cable feed...not possible without a splitter...period.

Generally speaking most cable tv installations in a home have a splitter from the main trunk into the house to supply multiple outlet throughout the home. Yes I agree with that argument. But the question "are you using a splitter" was answered as I was not using a splitter at the HDHomerun.

> C) The HDHomeRun 3 has two tuners and one input because it has an internal splitter.  So now at the very least, you've split a split signal (once to get from source to two locations, and then again at the HdHomeRun), which is far worse than splitting the source signal through a four or more way splitter.

Not sure why you had to state this since basic theory says that if you split a signal that the resulting two signals will not be as strong as the original.

> D) You indicate your "test theory" and "history" about the cable company testing each outlet and it being acceptable.  Did you have them test test each side again after you split each outlet...because you have, as I just outlined for you.  I'm rather surprised a self described infallible electrical engineering god, who's clearly above the advice he's asking for would fall so easily into the "assumption trap".

Yes the cable technician tested the one splitter signal after he installed it.

> E) You said "Also the 80% level is the minimum for a valid picture.".  That is false, signal strength is not nearly as important as people like to believe.  I have 3 HDHomeRun units and I have some channels that never get above 70% signal strength and routinely are in the 60ish range and the picture is flawless.  Signal and Symbol Quality are far more valuable a measurements.

80% is a rule of thumb as different tuners receive differently.

> However, to answer your question, HDHomeRuns tend to have a weaker tuner and you are trying to run them on a line that has been split at least once, then split again at the unit (as I thoroughly outlined).  They have also always been known to report a signal strength lower than other devices would and been a bit susceptible to not dealing well with "unclean" signals.  In fact, if you browse through the HDHomeRun firmware revision history, you'll see several times where they "improved signal strength reporting".  Cable troubleshooting 101 tells you to remove ALL splitters between the source and the tuner when working through weak / corrupt signals...which is what I am sure led to mathog's splitter query...though as an infallible electrical engineering god, I don't know why you would need to be told that.

I'd also be interested in having you run the HdHomeRun Config Gui, tune to a channel and report the the levels of all 3 measurements.  Though I probably wouldn't be inclined to offer much help with the way you've decided to treat "lesser" (apparently in your eyes) intellectuals.

Thank you for the last statement which shows me how well you read all the posts and still didn't get what the real question was. Please use this forum for expressing helpful ideas for the issue at hand and not a soapbox to hear yourself rant. I accept your apology for being for being inferior.

---

### Post by williammanda on 2011-08-06
> **nickrout said:**
> williammanda, clearly you are not getting understanding of your question here. Your question is why the hdhr appears to give the same signal strength no matter which channel, when other tuner give variable (and higher) results.

I understand the question but don't know the answer. However I suggest you might get more help on the muythtv users mailing list.

Another opportunity is to see if the windows client reports different figures, eliminating (or confirming) a bug in the linux driver, or myth's interpretation of the linux driver's reporting. 

Lastly you will no doubt have read that the hdhr's tuner is not as strong as some others. Whether that is affecting things is beyond my ken.

I am about to set mine when I get time, although mine is the dvb-t version.

Thanks for your reply. I will try the mythtv users and report back. One question concerning the windows gui...if I scan for channels...the HDHomerun will or will not retain this information? I want to make sure the scanning will not screw up the mythtv application.

---

### Post by uncle hammy on 2011-08-06
> **williammanda said:**
> Yes I agree with that argument. But the question "are you using a splitter" was answered as I was not using a splitter at the HDHomerun.

Yes, you are using a splitter at the HDHomeRun.  IT'S IN THE HDHOMERUN.  So, the question "Is there a splitter?...as in between the trunk and the HdHomeRun" (and there is, the one that allows you to have 4 locations) is VERY appropriate, because the HDHomeRun is also splitting.

> **williammanda said:**
> Not sure why you had to state this since basic theory says that if you split a signal that the resulting two signals will not be as strong as the original.

Mostly because not all splitters are created equal.  You "basic" theory is not so basic.  So the quality of the splitter you have installed before the HDHomeRun unit is of importance...hence mathog's original question.

If you were to submit a trouble ticket to SiliconDust, one of the very first things they will ask you to do is plug the HDHomeRun directly into the trunk to test, because they do not recommend any splitters between the trunk and the unit...and you my friend, have at least one.

Anyways, I'm not on a soapbox, I just don't like seeing arrogant you know whats talk down to people who simply trying to help them. 

Have fun with your problem, you clearly smarter than all of us and don't need any help from here to fix it.  If you think I'm on a soapbox, wait til you start treating the good folks on the mailing list like moronic little pleabs.

P.S.  Though you felt some "mine is bigger than yours" need to accuse mathog of not having any electrical experience, an Electrical Engineering degree is not required to troubleshoot this problem.

---

### Post by williammanda on 2011-08-06
> **uncle hammy said:**
> Yes, you are using a splitter at the HDHomeRun.  IT'S IN THE HDHOMERUN.  So, the question "Is there a splitter?...as in between the trunk and the HdHomeRun" (and there is, the one that allows you to have 4 locations) is VERY appropriate, because the HDHomeRun is also splitting.



Mostly because not all splitters are created equal.  SO the quality of the splitter you have installed before the HDHomeRun unit is of importance...hence mathog's original question.

If you were to submit a trouble ticket to SiliconDust, one of the very first things they will ask you to do is plug the HDHomeRun directly into the trunk to test, because they do not recommend any splitters between the trunk and the unit...and you my friend, have at least one.

Anyways, I'm not on a soapbox, I just don't like seeing arrogant you know whats talk down to people who simply trying to help them. 

Have fun with your problem, you clearly smarter than all of us and don't need any help from here to fix it.

P.S.  Though you felt some "mine is bigger than yours" need to accuse mathog of not having any electrical experience, an Electrical Engineering degree is not required to troubleshoot this problem.

Thanks again for your inferiority. Do you know what the original question is? When you want to genuinely help it would be appreciated. Until then expect the same as you give.

---

### Post by uncle hammy on 2011-08-06
> **williammanda said:**
> Thanks again for your inferiority. Do you know what the original question is? When you want to genuinely help it would be appreciated. Until then expect the same as you give.

Yes, the question is "my HDHomeRun only reports 50% signal strength on all channels when my other tuners report 80% or higher....why?" 

People have been trying to help you find an answer to it.  You just don't like their answers and have assumed they must understand not you.

You have been offered multiple possibilites...

1) HDHomeRuns have a weaker / more sensitive tuner than your other hardware.
2) HDhomeRuns have always had signal reporting issues where they tend to report a lower signal than they actually are receiving.
3) You have a splitter before the HDHomeRun, which, combined with the HDHomeRuns weaker / more senstivie tuner could be causing you an issue.
4) The splitter you have at location 1 may be of higher quality than the HDHomeRun's internal splitter which could be why the hardware at location 1 has less degradation.
5) You are comparing 2 different locations.  For all we know, location 1 has 10' of coax from the trunk to it and location 2 has 100' of coax from the trunk to it.  For all we know since the cable guy was there, mice have been chewing on the coax going to location 2...trust me, it happens.
6) You can't compare the signal strength the TV at location 2 to the HDHomeRun because the TV is an unsplit signal and the HDHomeRun has an internal splitter before each tuner.  A truer test would be to go wall plate -> coax -> splitter -> TV on one side of splitter if you want to compare them.

Have you actually tried moving the HDHomeRun and plugging it directly into the trunk to take your house splitter out of play?  Have you moved the HDHomeRun to location 1 to see what signal strengths it gets there?

You do understand that this is a forum, and all people can do is try to help you troubleshoot, correct?  Part of helping you troubleshoot is gathering information about your physical setup which is all mathog was trying to do before you IQ jumped him.  Especially because the nature of this issue is most likely due to your physical layout and probably has nothing at all to do with Mythbuntu.

---

### Post by williammanda on 2011-08-06
> **nickrout said:**
> I understand the question but don't know the answer. However I suggest you might get more help on the muythtv users mailing list.

I tried the irc channel and the only answer so far was to use ALT-F7 to see the current signal strength. I tried this while using the HDHomerun but each time it displays 100%. This could be accurate. I switched to a non HDHomerun tuner (pcHDTV 5500) and got the same signal% (97%) as when the station initially displayed the signal at 97% but I could see the signal% changing between 97 and 98.
I have previously posted the issue on SiliconDust forum as well.

---

### Post by williammanda on 2011-08-06
A quick note in using the ALT-F7:
When you use the ALT-F7 during live tv use...the video disappears or freezes but the video text information stays...the only way to get out of this state is to use the esc button.

---

### Post by williammanda on 2011-08-07
I tried the windows route but I didn't get any where. Can someone step me through how to scan and play back?

---

### Post by nickrout on 2011-08-07
> **williammanda said:**
> I tried the windows route but I didn't get any where. Can someone step me through how to scan and play back?

I guess you need to start here:

[http://www.silicondust.com/support/hdhomerun/instructions/](http://www.silicondust.com/support/hdhomerun/instructions/)

Why not simply post on the mythtv mailing list like I suggested?

Also step back a minute: do you get a poor picture on the hdhr? Or glitches in the recordings?

If not, what does it matter?

---

### Post by williammanda on 2011-08-07
Which one of the url's should I use?

---

### Post by mathog on 2011-08-07
> **uncle hammy said:**
> 
Especially because the nature of this issue is most likely due to your physical layout and probably has nothing at all to do with Mythbuntu.

+1

The OP wants to make sense of the signal strength readings on different devices, and the only way he's going to get to the bottom of that without specialized test equipment is to measure signal strength on each device while it is plugged into the same source, and then to repeat the measurements after a 1:N splitter.  A couple of data points should resolve most of his questions.  Of course, it can only provide information on the relative measurements, without a calibrated source the absolute meaning of the signal strength cannot be determined.  For all we know at this point the firmware release in his HDHomeRun is broken so that signal strength measurements from that device are meaningless.

---

### Post by nickrout on 2011-08-07
> **williammanda said:**
> Which one of the url's should I use?

I don't know, but I assume you are capable of reading through the docs and sorting that out for yourself. You did say at the beginning of the thread that you had set the device up with windows. in other words, work it out for yourself.

---

### Post by williammanda on 2011-08-07
Ok I got in touch with SiliconDust support via the irc. They say there is a bug with the latest release which is the problem I have described "shows signal 50% for every station upon initially selecting the station". Using ALT-F7 does reflect the actual signal% and also using this command will give the actual signal%:

hdhomerun_config ffffffff get /tuner0/status

tuner0 will be the current tuner being used.

---

### Post by uncle hammy on 2011-08-07
> **williammanda said:**
> Ok I got in touch with SiliconDust support via the irc. They say there is a bug with the latest release which is the problem I have described "shows signal 50% for every station upon initially selecting the station". Using ALT-F7 does reflect the actual signal% and also using this command will give the actual signal%:

hdhomerun_config ffffffff get /tuner0/status

tuner0 will be the current tuner being used.

[QUOTE=uncle hammy]They have also always been known to report a signal strength lower than other devices would and been a bit susceptible to not dealing well with "unclean" signals. In fact, if you browse through the HDHomeRun firmware revision history, you'll see several times where they "improved signal strength reporting".[/QUOTE]

[QUOTE=uncle hammy]2) HDhomeRuns have always had signal reporting issues where they tend to report a lower signal than they actually are receiving.[/QUOTE]

[QUOTE=williammanda]Thanks again for your inferiority. Do you know what the original question is? When you want to genuinely help it would be appreciated.[/QUOTE]

:roll:

---

### Post by nickrout on 2011-08-07
OK children keep it seemly or you'l go to your rooms and NO MYTHTV FOR A WEEK.

Anyway case closed, never was a mythtv problem.

---

### Post by mathog on 2011-08-08
> **mathog]For all we know at this point the firmware release in his HDHomeRun is broken so that signal strength measurements from that device are meaningless.[/QUOTE]

[QUOTE=williammanda said:**
> Ok I got in touch with SiliconDust support via the irc. They say there is a bug with the latest release which is the problem I have described "shows signal 50% for every station upon initially selecting the station". 

nuff said.

---

### Post by williammanda on 2011-08-12
> **nickrout said:**
> I don't know, but I assume you are capable of reading through the docs and sorting that out for yourself. You did say at the beginning of the thread that you had set the device up with windows. in other words, work it out for yourself.

Sorry I responded by accident to this post and I'm sorry

---

### Post by williammanda on 2011-08-12
Hopefully anyone that has followed this thread...

There was a manufacturer problem with using the HDHR3-US HDHomerun unit with MythTv. They are working on the bug of "shows signal 50% for every station upon initially selecting the station". I will report back when they make their changes.
Thanks

---

