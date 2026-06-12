---
title: "Audio over HDMI as an option"
date: 2008-06-26
forum: Mythbuntu
---

### Post by Quentusrex on 2008-06-26
I'm trying to build my htpc and I really want to have audio over HDMI as an option. I also want to be able to use an integrated video card, so my question becomes which nvidia chipset supports audio over hdmi. And then which motherboard has this chipset and implements that feature properly?

Thanks.

---

### Post by netslacker on 2008-06-26
> **Quentusrex said:**
> I'm trying to build my htpc and I really want to have audio over HDMI as an option. I also want to be able to use an integrated video card, so my question becomes which nvidia chipset supports audio over hdmi. And then which motherboard has this chipset and implements that feature properly?

Thanks.

You should really search around for this info.  avsforum.com has some discussions and there are some here in ubuntuforums.org.

I've struggled w/ audio over hdmi w/ an IGP ATI HD 3200.  However, in my own looking it seems that audio over hdmi w/ nvidia isn't supported yet because the nvidia driver doesn't support it yet.  I believe they are coming out w/ support in the 177 (??) driver.  But, like I said, you have to do some searching as this is just what I recall for nvidia.

There are a few threads dealing w/ audio over hdmi and it is completely hit and miss.  I had it working w/ my ATI card but then had to go back to an nvidia card to get clean HD video. The general concensus that I have seen is to use DVI->HDMI cables and route the audio seperately to your TV or receiver (most go to a receiver).

---

### Post by Quentusrex on 2008-06-26
I think I've read the same thing. And the HD feature is why I want to use nvidia cards. Would the feature only be possible only with the nvidia driver? Or could this be done with something from alsa? So, if I really wanted this feature is there anything I could do to get it?

---

### Post by netslacker on 2008-06-26
> **Quentusrex said:**
> I think I've read the same thing. And the HD feature is why I want to use nvidia cards. Would the feature only be possible only with the nvidia driver? Or could this be done with something from alsa? So, if I really wanted this feature is there anything I could do to get it?

I think there are a number of factors that go into having audio over hdmi work.  With my ATI card, the ALSA drivers definitely made all the difference. For me, the HDMI Audio was detected as a separate audio card (card 1, vs. onboard that was card 0) and the HDMI was device 3.  So all I had to do was change the output in myth from ALSA:default to ALSA:hw:1,3 which seems to be the only way to make it work even with an ATI card.  However, even this method is not fool proof because it seems to reject any audio that isn't 48khz.  

I just think in general that audio over hdmi on linux isn't ready for primetime.  Maybe in a year, but not now.

btw, I have abandoned trying to get audio over hdmi to work since my new nvidia card only has DVI out. I'll try again w/ my IGP-ATI card once drivers have matured.

---

### Post by Trollslayer on 2008-07-02
> **netslacker said:**
> I think there are a number of factors that go into having audio over hdmi work.  With my ATI card, the ALSA drivers definitely made all the difference. For me, the HDMI Audio was detected as a separate audio card (card 1, vs. onboard that was card 0) and the HDMI was device 3.  So all I had to do was change the output in myth from ALSA:default to ALSA:hw:1,3 which seems to be the only way to make it work even with an ATI card.  However, even this method is not fool proof because it seems to reject any audio that isn't 48khz.  

I just think in general that audio over hdmi on linux isn't ready for primetime.  Maybe in a year, but not now.

btw, I have abandoned trying to get audio over hdmi to work since my new nvidia card only has DVI out. I'll try again w/ my IGP-ATI card once drivers have matured.

Similar experiences here plus problems with 5.1 sound support - I'm going for the Asus card which uses the C-Media CMI8788 chip as the ALSA driver for that seems to be in good shape.
Creative don't seem to be interested in supporting Linux development.

---

