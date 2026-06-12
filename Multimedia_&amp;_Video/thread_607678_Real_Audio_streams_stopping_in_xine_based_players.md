---
title: "Real Audio streams stopping in xine based players"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by tom17 on 2007-11-09
Hi,

I am trying to play BBC Radio 1 through Amarok but am having 2 issues.

1. The sound is occasionaly garbled. I can live with this for now as it is irrelevant as long as the following remains a problem.

2. It will only play the stream for 90 seconds and then it just stops!

Originally I thought this was a broken stream so tried it in another player (MPlayer) and it worked fine. It also works fine in the web-based player (Which I think used the MPLayer plugin, not sure).
Here is the stream if you wish to try... rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/radio1/live/r1_dsat_g2.ra?BBC-UID=54a753630f9549592a0e46a430605979190ea109f02001a4c47f08b15cbaac8d_n&SSO2-UID=

Then I thought I should check if it is an Amarok issue or an underlying issue so I installed gxine and sure enough, after 1m30s the stream stopped.

I have looked around for this but have not found anyone with the same problem and to be honest I am a bit stumped.

I have Ubuntu 7.10, upgraded from Feisty. It was a good few weeks ago when i first tried it and I think I had to install the win32 codecs to get RA working at all but I cannot remember now. Could it be some time limited version of the codecs that "only play the first 90 seconds" or something like that?

I am not by my home pc right now but if there is anything I need to check in order to help diagnose this prob, I can do so tonight.

I realise i could just play it in MPLayer, but I wanted it integrated into my 'Amarok Experience'.

Any ideas? Cheers.

---

### Post by tom17 on 2007-11-09
What, no ideas? Is there nothing I can check? :-(

---

### Post by pillyb on 2008-02-01
Hi.
I experience exactly the same as you describe. It happens regardless of whether I use xine or realplayer. Very puzzling. Did you ever get this sorted out?
Thanks.

---

### Post by subitul on 2008-02-23
Same here... Although RealPlayer is working perfectly, it's just Xine which stops so it's nothing wrong with the stream. Oh, and does anyone anyone have some hints into embedding RealPlayer into Konqueror so that I can use BBC iPlayer properly?

---

### Post by wolfen69 on 2008-02-23
open synaptic and remove totem and everything with totem in the name.(totem has been known to conflict with streaming media) then install mozilla-mplayer. vlc is a good replacement for totem.

---

