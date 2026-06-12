---
title: "How to use SPDIF output from Santa Cruz sound card with Kubuntu"
date: 2012-05-24
forum: Multimedia Software
---

### Post by RudyG on 2012-05-24
Well after some trial and error (actually lots of error) I finally got this to work today and wanted to post the details in case there are others that want to accomplish the same thing. I'm running Kubuntu 12.04 Precise.
Before this I used the analog output (speakers) on this card into my receiver, with a cable that has RCA connectors on one side and a 1/8" connector on the other.
Reading the Santa Cruz documentation reveals that the SPDIF connection requires the exact same cable. The 1/8" connector needs to be plugged into the VersaJack which is the yellow colored connector. This causes the RCA connector to carry two separate digital streams. The Red RCA connector will carry the AC3 stream and the White Connector will carry the PCM stream. Again in the Santa Cruz documentation they advise the users to use the Red Connector, however, for me only the White connector works, maybe because the standard audio sources don't decode any sort of AC3. Perhaps the Red Connector will work with a DVD or Blu Ray.
Anyway, once plugged in, select the source on your receiver into which you plugged the white connector into.
Next step calls for going to your mixer and making sure that the DAC volume is not muted and is all the way up and also that the IEC958 is not muted. I had to add the IEC958 control to my mixer (See Settings Menu)

To test the setup go to Settings->System Settings->Multimedia Once there click on the Phonon tab. There you'll see a bunch of Audio Playback devices. The ones that worked for me were the "hw:0,0" and "default" along with a few others.
Interestingly no devices marked with IEC958 worked.:confused: 

No Matter. I'm a very very happy camper as the sound improvement is tremendous. The analog output produced a very noisy and sometimes distorted sound at many of the frequencies.

HTH
Rudy

---

