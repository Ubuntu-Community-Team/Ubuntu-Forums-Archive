---
title: "Ubuntu/Mythbuntu ATI 4350 HDMI audio problem - please help"
date: 2009-09-03
forum: Multimedia Software
---

### Post by scar1 on 2009-09-03
Hi all,

Can anyone please assist me with a small problem i have with the final setup of my HTPC with ATI 4350 512mb video card.

I have recently installed Mythbuntu 9.04 and all was running ok, however it was using the onboard graphics which only had a VGA interface. I decided to buy and install a ATI 4350 512mb as understood the video support under ubuntu was good.

After I installed card and also updated and installed the proprietary ATI drivers video is fantastic. I am currently using the HDMI interface to attached TV and I am unable to get sound output over HDMI cable.
I have read man threads to set this up some with success others with not, currently i am yet to get any sound. My system seems to recognise 2 audio outputs when i open Multimedia >> mixer;

HDA ATI HDMI (Alsa Mixer) >> Here I get a switches tab and can select controls and check the box for IEC958 but that is it. I do not get any other options.
ATI ATI R6xx HDMI (OSS Mixer) >> Here I get a playback tab, I have unmutted and under digital-1 I have put that right to the top.

Then in VLC and Mplayer I have tried to configure and tried various different option to try and get sound working however this is where i think im stuck. Can anyone please offer some advice....

I am new to unix/linux however learning fast.

Thanks
Steve

---

### Post by scar1 on 2009-09-03
ah ha - persistence is key!!!!

Ok I after all the reading I had done I went back to the first post i read on this ([http://antiflash.org/notes/computers/linux,_radeon_4350_and_hdmi/](http://antiflash.org/notes/computers/linux,_radeon_4350_and_hdmi/)). Now I understand the "aplay -l" output.

In the Mplayer and VLC configured the player to use alsa card hardware 0.3 and as if by magic I have sound!!!!

---

### Post by usererror on 2010-03-20
> **scar1 said:**
> ah ha - persistence is key!!!!

Ok I after all the reading I had done I went back to the first post i read on this ([http://antiflash.org/notes/computers/linux,_radeon_4350_and_hdmi/](http://antiflash.org/notes/computers/linux,_radeon_4350_and_hdmi/)). Now I understand the "aplay -l" output.

In the Mplayer and VLC configured the player to use alsa card hardware 0.3 and as if by magic I have sound!!!!

HA!  thank you for your post!  Just got my audio to work with VLC now too.

For anyone else who finds this, in VLC you have to go to:

Tools > Preferences.  At the lower left of Preferences screen under "Show Settings" choose ALL then Expand Audio >  Output Module > ALSA, in the Alsa Device Name choose the ATI hw0,3, which on mine had said "Defaualt".

After the switch audio works!!

---

### Post by hairy one on 2010-03-24
Hi scar1

If it is still working could you please add solved to the heading.

Not picking but when it comes up in search Solved means everything to some.

cheers for the info, setting up my own myth now with the same card.

cheers
hairy

---

### Post by scar1 on 2010-07-30
Sure - ill add to solved

---

