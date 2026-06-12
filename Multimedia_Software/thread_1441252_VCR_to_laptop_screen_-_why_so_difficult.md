---
title: "VCR to laptop screen - why so difficult?"
date: 2010-03-28
forum: Multimedia Software
---

### Post by mango42 on 2010-03-28
In my search for information (*any information!*), I have noticed quite a few very short-lived threads, with a predominance of zero responses on this forum, where people are basically asking how to watch their old VHS tapes on their laptop monitors.

A simple enough request, I would have thought? Yet there seems to be something of a brick wall on this subject.

My route so far:-

VCR SCART out to SCART to S-Video & RCA adaptor;

S-Video in to my laptop (so I assume its nVidia 7900 card is handling this socket?!) but where to go from there? With the sublime optimism born of some years most enjoyable use of Ubuntu, I fired up Totem expecting to see the VHS tape playing in its window. Hey ho, guess that was just too optimistic, not to mention naive? ;)

I have sped-read the MythTV page but nowhere does it seem to mention VCR-S-Video-laptop screen.

Any and all suggestions gratefully received...

---

### Post by mango42 on 2010-03-29
Bump.

Perhaps nobody watches video tapes anymore? I'm really quite puzzled by the silence on this - have I missed something utterly fundamental?

---

### Post by lavinog on 2010-03-29
> **mango42 said:**
> Bump.

Perhaps nobody watches video tapes anymore? I'm really quite puzzled by the silence on this - have I missed something utterly fundamental?

Keep in mind SCART is not used everywhere.
What is your laptop model?
Does the video in work with anything else?
Are you using the proprietary nvidia drivers?

---

### Post by lisati on 2010-03-29
Another possibility is that not many people have used S-video as an input source on their computers. On my laptop, the S-video port is output only. These days I rarely use the capture card installed on my main desktop (it has S-video), and I don't think I've actually used it with Ubuntu.

---

### Post by lavinog on 2010-03-29
> **lisati said:**
> Another possibility is that not many people have used S-video as an input source on their computers. On my laptop, the S-video port is output only. These days I rarely use the capture card installed on my main desktop (it has S-video), and I don't think I've actually used it with Ubuntu.

I agree.

It might be a lost cause.  Recently nVidia announced that they will no longer support the open source drivers...so if the feature doesn't work in the proprietary driver, you only option is to beg for them to add it.
Can't you watch your VHS tapes on a TV? Are you looking to capture them?

---

### Post by mango42 on 2010-03-30
Many thanks for the responses.

> **lavinog said:**
> I agree.

It might be a lost cause.  Recently nVidia announced that they will no longer support the open source drivers...so if the feature doesn't work in the proprietary driver, you only option is to beg for them to add it.
Can't you watch your VHS tapes on a TV? Are you looking to capture them?

Um, I don't have a TV - never have. That's why I was eventually hoping to back up these old tapes (for my partner, who owns the tapes, an 'heirloom' from her mother, as is the VCR) onto DVD.

> Does the video in work with anything else? - fine on a friend's old TV screen, SCART to SCART.

Right now, just getting them to *play* on a laptop screen would be an achievement and I still don't understand why this is an unresolved issue.

The laptop, an Alienware m9700, comes equipped with two S-Video sockets, one in, one out. Yet I have drawn a complete blank on finding *any* software that recognises these ports, even in Windows. My nVidia drivers are up to date; Alienware is being its usual helpful self (ie: silence!)

What's going on here? Has this whole issue been 'Geffen'd or something?

---

### Post by rhy7s on 2010-03-30
Does your Alienware have a TV tuner? If not, the video-in may be a dummy port. Search around for linux compatible video capture devices.

---

### Post by lavinog on 2010-03-30
There might be an issue with the video formats.  I am assuming your vcr outputs in PAL...where did you buy this laptop...could it be that it only accepts NTSC?

Can you post the output of lspci?

I tried searching for you model, I found some references that claim the s-video in exists, but I couldn't find anything about it being used.  I would think it could be a handy feature to be able to capture video with a laptop...something for the manufacture to brag about, but the don't...hmmm.

---

### Post by lavinog on 2010-03-30
found something on dell's website:
[http://4help.alienware.com/cgi-bin/alienware.cfg/php/enduser/std_adp.php?p_faqid=5128&p_created=1152217327&p_sid=ovD*v9Yj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PTI6MiZwX3Jvd19jbnQ9NjAsNjAmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3NjZl9mYXFzKmM9JnBfcGFnZT00JnBfc2VhcmNoX3RleHQ9bTk3MDA*&p_li=&p_topview=1](http://4help.alienware.com/cgi-bin/alienware.cfg/php/enduser/std_adp.php?p_faqid=5128&p_created=1152217327&p_sid=ovD*v9Yj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PTI6MiZwX3Jvd19jbnQ9NjAsNjAmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3NjZl9mYXFzKmM9JnBfcGFnZT00JnBfc2VhcmNoX3RleHQ9bTk3MDA*&p_li=&p_topview=1)
it is for NTSC only though, I didn't see anything for PAL tuner cards.

---

### Post by mango42 on 2010-03-30
It's encouraging to find that there *is* an app, albeit in Windows, from which one can select S-Video as input!

Mine's a European Alien, so if it has a Tuner card it'll no doubt be PAL, as is the VCR.

Thanks indeed for the pointers - I'll keep digging and next time I fire up the Alien (presently net-less in Linux) I'll copy the **lspci** output across.

All this just to get a digital monitor to read an old analogue signal! ](*,)

Is this progress or just a new subtle twist on the Emperor's New Clothes?

---

### Post by KirbySmith on 2010-05-02
My nVidia card (BFG 7800 GT) has an s-video connector, and a clot of cable adapters that allows one to connect an s-video source to the card.  This usually works in windows, now abandoned by me.  I believe that the nVidia WDM windows software provides the capability for players such as Media Player Classic to view the video.  I have a VCR to provide the turner function and source the s-video.

With Ubuntu 9.10, the media players I've tried so far don't see the video.  And to add insult to injury, the motherboard sound line-in connectors don't connect to the sound output, in spite of endless alsa hacking.

Why use the computer as a TV? was asked.  Because if one is watching TV in the US, there are approximately 18 minutes per hour of commercials during which web searches, mail reading or other tasks can be performed.

My hope, for which I am presently searching this forum, is to find a Linux compatible auxiliary video card that can take s-video and audio in and make them visible to a media player.  Failing that, I would want a Linux compatible TV card that will accept analog channel 3 from my cable-company-provided digital-to-analog adapter.

kirby

---

### Post by mango42 on 2010-05-10
I would be very interested in what you find **KirbySmith** as we have very similar video cards. So far I've drawn a blank, much to my non-computerate partner's disgust ;-)

---

### Post by KirbySmith on 2010-05-17
This may take awhile because I have little time to research it.  What I've read so far is not too promising, or maybe I should write not to clear about suitability/compatibility.  

As an alternative, I found a modestly-priced Samsung combo LCD TV and monitor (2333HD)  at Staples that might avoid the entire nightmare of TV within the PC.  On-line reviews are mixed but mostly more positive than negative.  It is just not clear to me what different nightmare awaits driving this monitor with my video card (starting with getting ubuntu 9.10 to boot to a readable screen).

kirby

---

