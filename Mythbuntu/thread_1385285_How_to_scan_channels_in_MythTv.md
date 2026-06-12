---
title: "How to scan channels in MythTv"
date: 2010-01-19
forum: Mythbuntu
---

### Post by oz238 on 2010-01-19
I have read some docs in internet. However it doesn't work. I have Mythbuntu 9.10 with 0.22 MythTv, and SkyStar 2 dvb-s card.

I can scan only one frequency but I have to enter it. Is there any way to scan all frequencies at once? I don't want to enter all of them from many satellites.

If frequency field is empty I have error message: "error parsing parameters".

---

### Post by cedyathome on 2010-01-19
I used this guide [http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php)  When you get to this commmande scan /usr/share/dvb/dvb-t/uk-WinterHill > /root/.tzap/channels.conf  You'll need to substitute uk-WinterHill with a file for your satellite stream. Look in /usr/share/dvb/dvb-s (I think)  Also, you will use szap instead of tzap with the channel.conf in a .tzap dir. See the --help.  All the best.

---

### Post by DominicF on 2010-01-19
Hi,

I need help too.  Just got a new dvb-s2 card tbs8920 today. Installed and seems to be working using mplayer and channels.conf file created with Scan.  I now try to import this into Mythtv backend setup using the import channels.conf file option.  After trail and error I'm getting closer... now with the conf file Myth starts to perform a scan but times out (I don't remember the exact message).  How do I get past this issue?

Any tips?  I tried increasing the timeout values.  What typically should they be for a dvb-s card?

I might try scanning a know transponder next tomorrow with the default time outs and delays.

---

### Post by oz238 on 2010-01-20
Thanks cedyathome. I think that unability to scan channels is a serious bug. Does any previous version work better? 

I noticed also that I have tv picture with top and bottom margins. I suppose, there is possible to change it with scalling but it strange that it doesn't feet in default way.

---

### Post by Flecko on 2010-01-21
Channel scanning in 9.10/0.22 is essentially broken. I would say don't even attempt it. I switched back to 9.04 because of this and several other reasons.

My thoughts on it are here: [9.04 Vs. 9.10]("http://bensdrivel.wordpress.com/2009/12/29/mythbuntu-9-04-vs-9-10/")

I hope that 10.04 holds better things for us Mythbuntu users.

Best of luck.

---

### Post by bcg30506 on 2010-01-22
> **Flecko said:**
> Channel scanning in 9.10/0.22 is essentially broken. I would say don't even attempt it. I switched back to 9.04 because of this and several other reasons.

My thoughts on it are here: [9.04 Vs. 9.10]("http://bensdrivel.wordpress.com/2009/12/29/mythbuntu-9-04-vs-9-10/")

I hope that 10.04 holds better things for us Mythbuntu users.

Best of luck.

Just read your blog.  Good writeup.  I tend to agree and am also staying on 9.04 with MythTV 0.21-fixes since it is basically stable and does all I need with the WAF being acceptably high.  9.10 just introduces way too many risks from what I've read and 0.22 of MythTV really just adds a new UI for my wife to learn and nothing else I don't already have (since I'm running VDPAU courtesy of avenard).

---

### Post by oz238 on 2010-01-27
Flecko, yes, you are right. The 9.10 is not even a beta!

---

### Post by singedwings on 2010-01-28
I have a Skystar2 and while I agree that the whole channel scanning and setup in 9.10 is a total parade ground poo, (look in a Roger's Profanisaurus for that one) I had major problems with 9.04. I could not watch livetv at all, only record and watch later.

OK I am not an expert, but if you make use of Parker1's excellent guide [http://parker1.co.uk/mythtv_freesat.php]("http://parker1.co.uk/mythtv_freesat.php") with 9.10 you will at least be able to watch livetv including bbchd and record manually after only a minor amount of hair pulling.

When the channel adding in the myth setup has conflicting channels add the first instance of each channel and cancel the rest. You will still end up with a load of channels that do not appear to work but you will get about 50 decent channels that work fine (on astra anyway). Good luck.

---

### Post by oz238 on 2010-01-28
> I noticed also that I have tv picture with top and bottom margins. I suppose, there is possible to change it with scalling but it strange that it doesn't feet in default way.

I fixed it with setting dpi value in /etc/X11/xorg.conf.

Finally, I changed to Mythbuntu 9.04. It was caused not only by channel scanning but by other problems, too. I have just started my adventure with Mythtv so I prefer to have one stable and functioning system. After a year of experience, (probably) I will change to something newer. My system is located on pendrive so having one functioning system and other experimental on second pendrive is a comfortable idea.

---

### Post by diskmaster23 on 2010-01-30
This should be a sticky for the forum and titled "Do not upgrade to 9.10".

---

