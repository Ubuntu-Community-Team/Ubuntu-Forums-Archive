---
title: "S/PDIF on LogiLink USB Box"
date: 2010-10-15
forum: Multimedia Software
---

### Post by sir.hampster on 2010-10-15
Hello everyone,
I have bought a LogiLink 7.1 USB Box some weeks ago and wanted to use it to passthrough the audio from my movies directly to my new receiver via its S/PDIF.

Ubuntu detects this card as a "CM106 Like Sound Device" and gives multiple profile options in Pref>Sound>Hardware for this card.
However, there is no option for S/PDIF, and no matter which profile I choose, whether it's digital or analog and stereo or 5.1, my receiver always gets a stereo feed on the S/PDIF line. When playing media on vlc, movieplayer or kaffeine.

Someone in IRC said I should try alsamixer, but it reports "This sound device does not have any playback controls." for this card.

Please can anyone help me set up my VLC with this card so that I can play movies with surround? =)

Thanks in advance

---

### Post by sir.hampster on 2011-10-18
Hmm, I suppose after a year it is reasonable to be allowed to bump my own topic :D

Using 11.10 by now but still not being able to use a digital audio pass-through :(

---

### Post by aisyko on 2012-02-18
> **sir.hampster said:**
> Hmm, I suppose after a year it is reasonable to be allowed to bump my own topic :D

Using 11.10 by now but still not being able to use a digital audio pass-through :(

Is this this thing ?
[http://www.amazon.fr/gp/product/B0013BXFLG/ref=pd_lpo_k2_dp_sr_1/279-5758960-5034766?pf_rd_m=A1X6FK5RDHNB96&pf_rd_s=lpo-top-stripe&pf_rd_r=0RY47AGJXHC8FV8M9H1W&pf_rd_t=201&pf_rd_p=471061593&pf_rd_i=B002H3BSCM](http://www.amazon.fr/gp/product/B0013BXFLG/ref=pd_lpo_k2_dp_sr_1/279-5758960-5034766?pf_rd_m=A1X6FK5RDHNB96&pf_rd_s=lpo-top-stripe&pf_rd_r=0RY47AGJXHC8FV8M9H1W&pf_rd_t=201&pf_rd_p=471061593&pf_rd_i=B002H3BSCM)

Maybe i'll buy one...

---

### Post by sir.hampster on 2012-02-18
I have this one: [http://www.logilink.eu/showproduct/UA0099.htm](http://www.logilink.eu/showproduct/UA0099.htm)

but afaik there is still no development in a proper pulse driver. I managed to get s/pdif working with alsa, but it's not working that nice - like no integrated volumemixer like pulse has with the system.

---

