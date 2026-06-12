---
title: "Guide setup with schedules direct"
date: 2008-09-18
forum: Mythbuntu
---

### Post by iitywygms on 2008-09-18
I finally have mythbuntu running.  Everything is good except my guide data.
I have a subscription with schedules direct.  Problem is that only a few channels are showing up with information.  The rest are unknown with no data.
Can someone explain the correct way to set up the channel guide or point me in the direction of a how to?
Sorry for such a newb question but I can't find the answer.

Thanks

---

### Post by klc5555 on 2008-09-18
This information should be obtained automatically from your cable provider, but often this doesn't happen So, first, you'll need to identify your unknown stations by watching them.

Then, log on to Schedules direct and retrieve the  xmltvid number for each of these "unknown" stations that you have identified. Plug the xmltvid number for each of these stations into its correct slot, along with a channel assignment and a unique "call sign" (which can be made up, as long as it's unique for each station). You can also name each station.

This info can be entered via the backend, in the channel editor, which is something of a pain, or via the frontend, by hitting the "e" shortcut as you watch each channel. Sometime therafter, mythfilldatabase needs to be run, and the channel data should start filling in appropriately.

Remember that by default, mythfilldatabase only updates "tomorrow" and fourteen days out, so if you run just the default mythfilldatabase, don't be surprised that you have no schedules information for "today". It should be in place for "tomorrow". If you run mythfilldatabase "by hand", as a user job, you can use the --refresh-all switch to fill in all the data for your newly entered channels all at once.

Cheers! :)

---

### Post by iitywygms on 2008-09-18
Thankyou.  That is exactly what I needed to know.  I will do that tonight.
One other question.  I have another tv that is hooked up straight to cable.  It gets all the same stations my hdhomerun gets.  Why does it have all the correct  information for each channel displayed on the screen but myth does not?

---

### Post by klc5555 on 2008-09-18
> **iitywygms said:**
> 
One other question.  I have another tv that is hooked up straight to cable.  It gets all the same stations my hdhomerun gets.  Why does it have all the correct  information for each channel displayed on the screen but myth does not?

Not sure. The information is supposed to get pulled in when you set    up the backend to retrieve the EIT data. I think. But from a practical standpoint, in various installations I've only ever gotten a very few channels which were identified and updated automatically at the first running of mythfilldatabase. For me the overwhelming majority have had to be identified and have their data entered in manually before appearing and updating properly in the schedules.

All the best!

---

### Post by newlinux on 2008-09-18
Are you tuning QAM (cable) or OTA channels with your HD Homerun? If it is QAM then the channel information comes from PSIP, and maybe your TV does a better job of parsing that information than myth/HD Homerun. In my case, it sometimes depends on when I scan. My cable provider has screwed up the PSIP information on more than one occasion, but it only matters if I scan when it is screwed up. A couple of channels they broke a year ago and they don't transmit the PSIP correctly anymore. But they did a year ago...

As for entering channel info, I find mythweb to be a good alternative as well. It has a channel editor screen in the configuration area.

---

### Post by Eric Boring on 2008-09-19
Just a quick note:
Editing the channel id info is infinitely easier in Mythweb, if you happen to have that installed already. Go to Settings > TV > Channel Info.

---

