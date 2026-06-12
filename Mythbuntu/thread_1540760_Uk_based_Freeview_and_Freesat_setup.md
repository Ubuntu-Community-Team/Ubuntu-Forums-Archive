---
title: "Uk based Freeview and Freesat setup"
date: 2010-07-28
forum: Mythbuntu
---

### Post by zoot149 on 2010-07-28
Hi.

I have been running Mythbuntu for a few months now as a test project building up to replacing Sky.  I have had a dual tuner DVB-T tuner up and running and happy with how that is set up.  I have always used EIT guide data for it.

Finding the picture quality seemed to be lower than what I wished for I have bought a NOVA-S2 to get the freesat channels, as well as the HD stuff and to give me a total of 3 tuners plus virtual to be able to never worry about conflicts again.

I have both cards installed alongside eachother but am struggling to get them set up so they work as I want them.  The freeview channels have their usual numbers but the freesat channels are all numbered 3000 and above.  I have both set up using EIT.

What I want to achieve is that if I choose to watch a channel, say BBC1 it will be numbered as channel 1 on both sources and whichever is free from recording will display it.  Similarly I want to set up recordings for series in such a way that I say record this show at any time on this channel and leave myth to decide which source to take it from.

I think to do this I need to use XMLTV as the guide data.  I am having no success setting this up.  To view the setup screen I have set myth to show the mouse pointer so I can scroll the screen using the sidebar...  I think i get through the whole setup process but when I run mythfilldatabase it fails.  Should I be choosing the channels I want individually or should I just get them all?

Cheers for any help.  I am a noob at linux really so if to help you need to see a logfile please point me to a guide as to how to display it on the forum.

zoot

---

### Post by bance on 2010-07-29
I would be interested in any replies to this thread,as I'm looking for a similar set up! 

Unfortunately I'm still trying to get my tuner cards working correctly, See[ this]("http://ubuntuforums.org/showthread.php?t=1537985") thread if anyone is interested.

Good luck, and I'm sorry I can't help just at the moment. I think the channel editor is probably the tool to use,
but I haven't quite got that far:(

---

### Post by xykevinr on 2010-07-29
Guys,

I think I have what you're asking for. I just did this in the last couple of weeks.

I'm in the UK, I have a DVB-T dual card and a single DVB-S card. I get all the free sky type channels (including the HD ones), and all the freeview channels.

I think to achieve what you want, you simply change the channel names and numbers to be the same for both channels.

I did this using mythweb (I'm not at home right now, so apologies for inaccuracies) If you look at the settings, database, channel info page. You'll get a list of all the channels you have, both DVB-T and DVT-S. Then, change the channel numbers and names to match. On mine it was something like

1 "BBC 1" on DVB-T
and
1052 "BBC One South" on DVB-S

Obviously consider the spacing etc - 'BBC 1' vs 'BBC1'.

Then, on mythweb, channel listings will only show one BBC1 channel. You can select a progam and myth will decide which tuner to choose.

Try reading this...

[http://www.mythtv.org/docs/mythtv-HOWTO-12.html#ss12.6](http://www.mythtv.org/docs/mythtv-HOWTO-12.html#ss12.6)

You dont need XMLTV at all for what I think you're asking, apologies if I've misunderstood.

Finally, I had some problems with some scheduled recordings being on the wrong channels - now all fixed - I'm not sure that mythweb database updates were all picked up at the same time. Suggest a restart of the backend... and trying out what I suggested on a single channel, with a bit of testing before going for everything.

Kev

---

### Post by Neon Dusk on 2010-07-29
There's a discussion about combined UK DVB-T & DVB-S set-ups [here](http://www.gossamer-threads.com/lists/mythtv/users/375444)

---

