---
title: "hdmi AC-3 audio broke after upgrading from 11.10 to 12.04.3"
date: 2013-10-31
forum: Multimedia Software
---

### Post by AdirondackJim on 2013-10-31
I just updated my MythBuntu 11.10 to 12.04.3.  Now, when I  try to play 5.1 content (ripped DVD), my TV (and receiver) plays a  "chattering" sound.  I check my receiver and the digital dolby light  isn't on--it's in PCM mode.  So, either the audio is getting sent as  AC-3, but the TV and receiver think it's PCM or the AC-3 audio got  converted to multichannel PCM and they can't handle it.


  My setup:  hdmi cable from htpc to TV.  TV has an s/pdif output to my  receiver.  I know TV sends AC-3 audio out correctly because I see  digital dolby light come on when I view a digital TV channel and PCM  come on when I view an old analog channel.


  I can connect s/pdif from my htpc to my receiver and the digital  dolby light comes on and it can decode the audio just fine.  It's just  not sending it right over hdmi.


  Now for some hints to the issue:  I noticed in MythTV audio setup  when I select alsa:hdmi.... the description only lists 2 channel PCM  audio capability.  speaker-test -Dhdmi:PCH -c6 errors about a bad  channel count (only -c2 works).  Finally, I tried vlc and it does the  same chattering sound.  These all make me think this isn't a MythTV  issue, it's something lower than that.


  

  Thanks much,



  Jim

---

