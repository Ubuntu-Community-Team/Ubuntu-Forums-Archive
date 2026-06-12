---
title: "No spdif audio, hdmi audio is ok"
date: 2009-07-30
forum: Mythbuntu
---

### Post by telko on 2009-07-30
Hello.

I´ve got a problem with the sound in Mythbuntu. I´m using the Mother board Zotac Mini-ITX nVidia 9300. I can play audio through hdmi, but I´m not able of playing audio through spdif (neither coaxial nor optical)

Any ideas about what can I try?

The output of aplay is:

propietario@propietario-desktop:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****

card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]

  Subdevices: 1/1

  Subdevice #0: subdevice #0


propietario@propietario-desktop:~$ aplay -L

hdmi:CARD=NVidia

    HDA NVidia, NVIDIA HDMI

    HDMI Audio Output

null

    Discard all samples (playback) or generate zero samples (capture)



I think that the point is why I cannot see other sound devices.

[SOLVED]
The problem was on the BIOS configuration. In "Integrated peripherials->HD Audio" I had "Internal codecs". When I chose "Internal + External codecs". I was able to see many other devices in the aplay output.

Now, I can chose SPDIF of HDMI when I want each one. By the moment, I think both cannot be used simultaneously.

---

### Post by kingsleyben on 2009-07-30
Same problem.  XFX nForce 680i LT SLI Motherboard.  Optical doesn't work.  :confused:

---

### Post by trevs.bronco on 2009-08-01
Hi Telko,
 
I don't want to hijack your thread, but I am using the mother board as you and have been unable to get the HDMI sound working. or any sound for that matter. Would you be able to tell me how you got the HDMI sound working in my thread [here]("http://ubuntuforums.org/showthread.php?t=1219646")
 
Your help, or anyones, would be greatly appreciated.
 
Trev

---

### Post by telko on 2009-08-02
Hi Trev.

I got the PC preconfigured so I don´t really know what exactly must be done to configure the sound through HDMI. Seeing the output of aplay I guess there is a way to redirect all the sound to HDMI. I supose that your output of aplay is different. Could you show it?

I´m trying to discover what configuration was done to change it when I want the sound through the SPDIF. May be with your help, as you have the same motherboard, we both can get what we want.

Let me know if you get something or if you want me to show you some configuration files. I´m quite new in linux so I´m a bit lost.

---

