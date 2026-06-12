---
title: "Poor Performance of some TV channels in MTV"
date: 2013-02-10
forum: Mythbuntu
---

### Post by os2 on 2013-02-10
Running MTV 0.26.

I receive good reception of local DVB-T BBC channels. However they won't play well in Live-TV. I switched to Quick Tuning in the BE but the performance is blocky and broken up. 

I've tested the setup in VLC, Kaffeine, XBMC/TVHE and all work well, except MTV.

DVB Radio channels (ie, BBC Radio 1..4 etc) all also play well in MTV.

Any tips or further suggestions would be most appreciated.

---

### Post by AlecJ on 2013-02-10
> **os2 said:**
> Running MTV 0.26.

I receive good reception of local DVB-T BBC channels. However they won't play well in Live-TV. I switched to Quick Tuning in the BE but the performance is blocky and broken up. 

I've tested the setup in VLC, Kaffeine, XBMC/TVHE and all work well, except MTV.

DVB Radio channels (ie, BBC Radio 1..4 etc) all also play well in MTV.

Any tips or further suggestions would be most appreciated.

You don't say what your DVB-T card is or hardware, but it sounds to me like signal loss. As you tune to each channel you should see the signal strength.

---

### Post by os2 on 2013-02-10
It's just a standard USB DVB-T stick. I receive good reception ~65% Strength, ~75% SNR. Having tested with other apps there's no problem. It's only a problem with MTV.

---

### Post by PhilWig on 2013-02-11
AlecJ, I also suggested signal issues here:
[http://www.mythtvtalk.com/bad-performance-bbc-channels-mux-mythtv-16114/](http://www.mythtvtalk.com/bad-performance-bbc-channels-mux-mythtv-16114/)

There are suggestions there of overlapping transmissions and a very doubtful aerial configuration (sounded like two connected together??).  That 75% snr looks very poor however you interpret it.

The OP has firmly rejected suggestions of a poor signal but without information such as location, a description of his aerial setup or copies of logs I don’t see how anyone can progress it.

Phil

---

### Post by nickrout on 2013-02-11
Please note the software is mythtv not MTV. 

You provide no log files, or information about your system.

Does the system record then playback OK?

65% strength and 75% SNR is not a good signal.

---

### Post by os2 on 2013-02-12
> **PhilWig said:**
> AlecJ, I also suggested signal issues here:
[http://www.mythtvtalk.com/bad-performance-bbc-channels-mux-mythtv-16114/](http://www.mythtvtalk.com/bad-performance-bbc-channels-mux-mythtv-16114/)

There are suggestions there of overlapping transmissions and a very doubtful aerial configuration (sounded like two connected together??).  That 75% snr looks very poor however you interpret it.

The OP has firmly rejected suggestions of a poor signal but without information such as location, a description of his aerial setup or copies of logs I don&#8217;t see how anyone can progress it.

Phil

As iterated earlier, reception is good via the local transmitter. 
SNR reporting is open to interpretation based on hardware in view. Eg, one box reports the signal quality differently than another.

There is nothing to report in the logs and having considered and tried all possible options I failed to solve the problem.

> **nickrout said:**
> Please note the software is mythtv not MTV. 

You provide no log files, or information about your system.

Does the system record then playback OK?

65% strength and 75% SNR is not a good signal.

The problem I was having was on one MUX. It wouldn't record so testing was not viable. Other MUX played and recorded fine.

MTV is short for mythtv just as FE and BE seem to be short for mythfrontend and mythbackend in the myth nomenclature.

---

### Post by PhilWig on 2013-02-12
os2,

I don’t think you have tried all options.  You have not taken the option of interacting sensibly with readers here by providing information requested or giving consideration to the views given.

Consider this:
a)   3 people now have suggested signal problems.
b)   Googling suggests that a good aerial will give 21db snr.  That’s a signal better than 100 times noise level  [10*log(100)=20].  Compare your 75%. 
c)  Mythtv may be getting scheduling information from other multiplexes.
d)  Just maybe Mythtv is less tolerant of terrible signals because it doesn’t simply ignore them, error handling is resource intensive, it is more feature-rich than other products so is doing more anyway and you do not have enough power to handle that.

There is a lot of good will in this forum from people who are here voluntarily, who know a heck of a lot about Mythtv and are prepared to spend time helping strangers.  Your blocking responses of "it's not that" or simply ignoring requests for information because you think it irrelevant is just liable to alienate.  If you know all the answers then why are you asking?

This started as an interesting problem but it's not any more because we don’t have enough clues.   Sorry for the bluntness; I really hope you are not offended and I really hope that you solve your problem and tell us the solution.

Phil

---

### Post by os2 on 2013-02-12
> **PhilWig said:**
> os2,

I don’t think you have tried all options.  You have not taken the option of interacting sensibly with readers here by providing information requested or giving consideration to the views given.

Consider this:
a)   3 people now have suggested signal problems.
b)   Googling suggests that a good aerial will give 21db snr.  That’s a signal better than 100 times noise level  [10*log(100)=20].  Compare your 75%. 
c)  Mythtv may be getting scheduling information from other multiplexes.
d)  Just maybe Mythtv is less tolerant of terrible signals because it doesn’t simply ignore them, error handling is resource intensive, it is more feature-rich than other products so is doing more anyway and you do not have enough power to handle that.

There is a lot of good will in this forum from people who are here voluntarily, who know a heck of a lot about Mythtv and are prepared to spend time helping strangers.  Your blocking responses of "it's not that" or simply ignoring requests for information because you think it irrelevant is just liable to alienate.  If you know all the answers then why are you asking?

This started as an interesting problem but it's not any more because we don’t have enough clues.   Sorry for the bluntness; I really hope you are not offended and I really hope that you solve your problem and tell us the solution.

Phil

Phil,

Hold on there one moment!

"Interacting non-"Sensibly"? I have interacted with you and gave you the information you requested earlier in this thread which you yourself brought up into this forum:

[http://www.mythtvtalk.com/bad-performance-bbc-channels-mux-mythtv-16114/](http://www.mythtvtalk.com/bad-performance-bbc-channels-mux-mythtv-16114/)

What a funny thing to say. Let's cut the emotion out of this.

If there is useful information to report and to be gleamed from the logs it would be reported here. It's the only way to troubleshoot. The logs are absolutely clean so I have not posted any. Recordings on the respective MUX are also zero.

a, b)
On the face of it yes it would appear to be signal problem. But as I have already mentioned, having tested the signal using standard methods and otherwise, it is not the signal strength. The signal (SNR) has been tested with a 4dB strength which proves sufficient with the given hardware. Even so when you asked and I stated the SNR was ~75%, true that is really just an arbitrary figure without knowing the full strength. The problem of ascertaining relevant signal is further compounded by the sensitivity of hardware. Some hardware are better than others under the same conditions.

c)
I am testing one MUX at a time. It's impossible to read EPG data from anywhere else. 

d)
So I experienced. Which leads me on to consider hardware bandwidth issues.

Rest assured the solution will be posted/updated when it has been found. In the meantime suggestions/leads worth pursuing was all I'm asking.

---

### Post by nickrout on 2013-02-12
OS2 you are a pretty rude sort of guy, but people volunteering their help for free and out of the goodness of the hearts get used to your sort.

You still have not provided logs, or details of your tuner.

As far as signal is concerned, are you using splitters or other devices which might attenuate signal? If so try removing them and have as little signal loss as possible.

---

### Post by PhilWig on 2013-02-13
Thanks Nick!

os2:  you have now provided some very important and quality information.  Thank you.  If I've pushed calculator buttons right your snr of 4dB means that signal:noise is about 5:2.  Some might judge that your signal quality is terrible.  A wire coathanger should do better.  QED.

As for why it's so bad, well without further information that's difficult to say.  Investigation of where your signal comes from, what might degrade it, what sort of aerial you need, and what you have are all questions.  A postcode to signal predictor may be a start.

I think though that this exonerates Mythtv.

There is however a remaining Mythtv issue which you may wish to explore.   Your backend log should be full of error reports and if it's not then it's a serious bug.

In order to report it and be taken seriously I imagine you would either have to be a very well respected member of the community or have obtained supporting views through (say) a forum by publishing your logs.

Thread closed for now though I think.

Phil

---

### Post by PhilWig on 2013-02-13
os2:
You excluded this possibility early on but just humour us and try one last thing will you please?  
Delete all channels, all video sources and all capture cards in backend setup, then recreate them and re-scan.  Gary Parker has good pages on this process.

This explains why I suggest this:
[http://www.mythtvtalk.com/qam-mapping-issues-charter-16006/#post61382](http://www.mythtvtalk.com/qam-mapping-issues-charter-16006/#post61382)
Phil

---

