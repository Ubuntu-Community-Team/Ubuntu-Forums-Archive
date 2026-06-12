---
title: "Digital audio working but not analog"
date: 2008-01-17
forum: Mythbuntu
---

### Post by murchball on 2008-01-17
Hi all,

I'm having a strange audio issue with my frontend. It's an MSI MediaLive and I currently have the SPDIF out connected to my receiver. It works great when I'm watching digital TV OTA but when I try to watch any analog shows (Hauppauge pvr-500 from cable and PVR-150 capturing from my cable box) there is no audio at all. I've connected with other frontends and the audio works fine, so I know that the backend is recording fine. Does anyone know what I can do about this?

---

### Post by carolco on 2008-01-18
Hello,

I do not know the answer, But I would like to ask you another question because I am just going to purchase msi medialive.
Is it possible to send audio via optical SPDIF to the receiver and video via HDMI to Monitor at the same time from DVD or another digital source of movie?
Help please.
K

---

### Post by volkswagner on 2008-01-18
It may help to post your settings.

Here is what worked best for me using spdif out.  In myth audio settings I have output set to default, passthrough output device set to ALSA:iec958, enabled checkbox for  ac3 and dts passthrough and internal volume controls, mixer device set to default.

I followed these instructions and installed the items listed although most were already present.
 
Look here to see my asoundrc file [http://ubuntuforums.org/showthread.php?p=4136487#post4136487]("http://ubuntuforums.org/showthread.php?p=4136487#post4136487")



[http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly]("http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly")

This worked for tv from pvr150 and pvr350, DVD's and ripped FLAC music all via optical out.

---

### Post by murchball on 2008-01-18
Booya!

Thanks Volkswagner! I used 

```

pcm.!default {
type plug
slave {
rate 48000
pcm "spdif"
}
}
```

and it worked like a charm! 

Carolco, what you are talking about is exactly how I have it set up. Video is going through HDMI to my TV and audio is going to my receiver through SPDIF. I was planning on using component for video, but I never managed to get to work and HDMI works fine for me. The only issue I have with the Media live is that the IR receiver seems a little weak. Now that my audio issue is resolved, this is the next thing I need to resolve. Maybe moving it further from my TV will help...

---

### Post by volkswagner on 2008-01-19
Carolco,

You should have no problem selecting audio out via spdif and using HDMI for video only.
 
I have seen many posts with audio not working via HDMI.

---

### Post by carolco on 2008-01-20
Thank you very much.

Could you, please, tell me another potential problems/issues with msi medialive that should be considered before purchase, please?

I will use medialive for audio, video and internet, not TVcard.
I will connect audio via optic out to receiver and video via hdmi to LCD...

thanks a lot
K

---

### Post by murchball on 2008-02-27
Just an update, even though I am using SPDIF for audio, I discovered by accident that audio over HDMI is working.

---

