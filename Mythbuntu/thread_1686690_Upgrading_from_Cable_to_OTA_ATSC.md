---
title: "Upgrading from Cable to OTA ATSC"
date: 2011-02-12
forum: Mythbuntu
---

### Post by crbnrod on 2011-02-12
Hi, I have a mythtv system that's been going for about three years:

ASUS Pundit P1-AH2 (NVIDIA 6150)
Athlon 64X2 3800+
Hauppauge PVR 500
1GB RAM

Working great with unencrypted cable, however now that most everything's been encrypted, I'm transitioning to OTA and will be looking to upgrade/replace the old box (I have an add'l one running on an antenna in another room).

I have already in my posession a Hauppage 950Q, which will handle OTA (now that I think of it, I think the terms I'm supposed to use are QAM and ATSC. So I'm switching to ATSC), but I think it offloads the decoding onto the CPU, which if memory serves the PVR 500 did it on the card. Which might be bad.

Anyway, long post finally coming to an end here - Let's say I open up the system above and stick in a video card that's somewhere in the NVIDIA 8000 series or higher, maybe another GB of RAM, and try the 950Q tv tuner. What are my odds on smoothly and painlessly watching HD ATSC broadcasts? 

Another option would be to try the Hauppauge HVR-1600 instead of the 950Q, but the HVR-1600 looks like a pretty big card to fit inside that little Pundit, especially alongside a new video card.

Thanks for any opinions, or even if you just want to tell me I'm crazy for even thinking about trying this.

---

### Post by newlinux on 2011-02-12
> **crbnrod said:**
> Hi, I have a mythtv system that's been going for about three years:

ASUS Pundit P1-AH2 (NVIDIA 6150)
Athlon 64X2 3800+
Hauppauge PVR 500
1GB RAM

Working great with unencrypted cable, however now that most everything's been encrypted, I'm transitioning to OTA and will be looking to upgrade/replace the old box (I have an add'l one running on an antenna in another room).

I have already in my posession a Hauppage 950Q, which will handle OTA (now that I think of it, I think the terms I'm supposed to use are QAM and ATSC. So I'm switching to ATSC), but I think it offloads the decoding onto the CPU, which if memory serves the PVR 500 did it on the card. Which might be bad.

Anyway, long post finally coming to an end here - Let's say I open up the system above and stick in a video card that's somewhere in the NVIDIA 8000 series or higher, maybe another GB of RAM, and try the 950Q tv tuner. What are my odds on smoothly and painlessly watching HD ATSC broadcasts? 

Another option would be to try the Hauppauge HVR-1600 instead of the 950Q, but the HVR-1600 looks like a pretty big card to fit inside that little Pundit, especially alongside a new video card.

Thanks for any opinions, or even if you just want to tell me I'm crazy for even thinking about trying this.

I have a Pundit P1-AH1 still going strong :)

Decoding is done by GPU and CPU when a signal is displayed on a monitor. Encoding is done by some tuner cards and CPU when you are capturing a signal. Digital ATSC signals do not need to be decoded, they are simply captured (as are digital QAM signals) and thus recording will take little CPU. PVR-500 encodes analog signals on the card, but if you're not recording analog, you don't need encoding on the card.

In other words, your tuner choice should for recording digital signals will no have no impact on your CPU - all the signals no matter which card you use will have to be decoded using either your CPU or your GPU, not your tuner card.

Any nvidia VDPAU capable card should have no problem decoding any HD signals from OTA/ATSC (720p/1080i mpeg-2).  An X2 3800 would have no problem decoding HD signals from OTA/ATSC either. I have one it has performed fine with for years and doesn't need VDPAU to play back any of my ATSC or QAM recordings (but I do have a VDPAU capable card in it to help playback higher bitrate h.264 HD content).

My Pundit has an X2 4200 and has no problems decoding HD mpeg-2 content either (nor most h.264 content that I throw at it - though on the lower bitrate side for HD) - and that's with the onboard nvidia 6150.

---

### Post by newlinux on 2011-02-12
also, if the P1-AH2 is like the P1-AH1 (IRIC, the only real difference is the AH2 uses an AM2 socket and the AH1 uses 939 socket) you only have PCI slots available which will limit your VDPAU GPU choices. Also my pundit only has a 250W PSU, which may also limit your GPU choices.

---

### Post by crbnrod on 2011-02-13
Thanks for the response.

So I hooked up the 950Q with the crappy little antenna it came with, and sure enough, the system is able to handle the OTA HD, even 1080i. Kind of a surprise since I just built a second box in the fall for OTA and I tried I think three separate video card options. 
Which, as you point out, is a good thing, since the Pundit is pretty limited based on PSU and expansion ports.

---

