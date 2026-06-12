---
title: "Audio over HDMI, home theatre does'nt work, TV works!"
date: 2010-01-20
forum: Mythbuntu
---

### Post by solo1minuto on 2010-01-20
Hi,
I have configured without particulars problems audio over hdmi, simply changing audio settings in myth frontend.
The HDMI cable is connected to an home theatre (sony STR KG700), and another cable connects the home theatre with the TV.
Now, audio and video on the TV works, but the STR KG700 doesn't play sound. I played it around for 2-3 days with myth options and alsa tools... can someone help me, please?

---

### Post by sk8er3810 on 2010-01-20
When looking to upgrade my receiver to HDMI, I read that most receivers simply had a "pass-through" for HDMI.  That seems kind of pointless to me if it passes both AUDIO and VIDEO to the TV and doesn't pull out the AUDIO portion.  I can't confirm that this is what is meant by "pass-through" but this could be the case.  Can anyone with a HDMI receiver confirm this?

---

### Post by SiHa on 2010-01-20
I did do a quick Google on this receiver and, it seemed to suggest that the only audio inputs were coax / SPDIF.

It may be to do with [[COLOR="Blue"]_HDCP_[/COLOR]](http://en.wikipedia.org/wiki/High-bandwidth_Digital_Content_Protection). Could be that the amp is only a repeater device for HD content. 

Although, for a MythTV output I'd be surprised. Just a thought though.

---

### Post by ian dobson on 2010-01-20
Hi,

Check what formats your reciever supports (DTS,AC3 PCM). A friend had the same problem with his windows HTPC. I think he just setup the system to send PCM and the reciever was happy.

Regards
Ian Dobson

---

### Post by Neon Dusk on 2010-01-20
According to the specs it's a HDMI switch which means it doesn't process the HDMI audio or video it just passes it straight to the HDMI out)

(HDMI repeater in an amp specs indicates that it can process the audio. Another indication is if the amp supports Dolby Digital Plus or Dolby TruHD as these can only be sent over HDMI)

If you want the Sony STR KG700 to process the audio you'll need to use the Optical/Coax S/PDIF input.

---

