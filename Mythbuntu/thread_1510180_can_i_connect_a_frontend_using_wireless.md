---
title: "can i connect a frontend using wireless?"
date: 2010-06-15
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-06-15
Hey;

I have been running a combined front end and backend for a while and am pretty pleased with the setup. I am now in a position to add another frontend, but was wondering if wireless gives sufficient connection speed to allow myth to work well?  If not then i guess i can look at running a cat 5 cable to the machine in question and then to my switch, but that will be a lower WAF and lots more work for me!

Thanks

---

### Post by klc5555 on 2010-06-15
I use wireless to connect a motley array of older Thinkpads as remote frontends. It generally works fine.

Even Wireless "B" can do SD satisfactorily.

Wireless "G" has no trouble with SD and analog.

Wireless "N" can do HD content pretty well on my one Thinkpad whose graphics chip can handle it.

This is all subject to the occasional flakiness that wireless is more prone to than is ethernet. So, for example, I never watch livetv over wireless, because a moment of glitchiness may cause the backend to decide the session is over, and shut off the tuner. Or, when shutting off a livetv session from a wireless frontend, sometimes the backend fails to get the memo and the runaway tuner will continue to run a livetv session until the backend is restarted. 

For these reasons, I use Mythtv from wireless frontends strictly in its DVR function; for this it works perfectly.

---

### Post by My Name on 2010-06-16
I think the big trick is to get the wireless to connect before mythtv is started, otherwise you may need to restart the frontends.

---

### Post by williammanda on 2010-06-16
Wireless has been brought up many times here and very few have had good success with it. I am one of the many that has limited success which translates into a very inconsistent frontend. Many factors come into play when using wireless so what JimBob does that works my not work for you. Until wireless gets to the level of wired then you will probably only get sub par results. Search the mythbuntu forums for the details of past success and failures.

---

### Post by geekyhawkes on 2010-06-16
Thanks, it sounds like it will be worth the effort of chasing an ethernet wire down to the new front end.  Best get my DIY up to scratch!

---

### Post by laffinet on 2010-06-16
Alternative to running a CAT cable is Ethernet-over-power. More expensive, but no cable running.

Had a higher WAF in my house so I ended up doing that.

I've got a couple of [these ]("http://www.netcomm.com.au/netcomm-products/ethernet-over-power/np201av")and they work really well (need the occasional reset). No problems with HD at all.

BTW You can pick them up for much less than what that page suggests. For comparison, I paid $139

---

### Post by Chris Musampa on 2010-06-17
I use wireless g for two laptop frontends (both Kubuntu 9.10) without problems.  With both these machines (both Atheros wireless chipsets, one 5000 the other 9000 I think) network manager gives frequently dropped connections whereas for some reason wicd has them both rock solid with better signal strength reported and zero drop outs, obviously that would make a huge difference.

---

### Post by Tteddo on 2010-06-19
> **Chris Musampa said:**
> I use wireless g for two laptop frontends (both Kubuntu 9.10) without problems.  With both these machines (both Atheros wireless chipsets, one 5000 the other 9000 I think) network manager gives frequently dropped connections whereas for some reason wicd has them both rock solid with better signal strength reported and zero drop outs, obviously that would make a huge difference.

I'll second this. Up until 10.04 my laptop was really flaky running the frontend until I put wicd on it. Then it worked passable. 10.04 fixed all that though (Acer Aspire 5050).

---

### Post by nickrout on 2010-06-19
if you can run a wire forget powerline and wireless.

---

