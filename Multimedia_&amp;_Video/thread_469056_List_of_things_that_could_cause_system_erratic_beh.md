---
title: "List of things that could cause system erratic behavior- urrgh"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by heatpumpcontrol on 2007-06-09
Hi guys,

I've had feisty 7.04 now for about 2 months. I installed it on my new pc with a P5BVM-DO MB. I'm not at the pc right now so suggestions will have to be performed later next week. I've messed with the xorg.conf file settings thinking that might do it and I still can't get it to work correctly.

My Audio, Video, Mouse, window panning, you name it, acts erratic and jumpy and/or choppy. I have fixed my Nvidia video driver issue. I have an Nvidia PCIE 6500 256mb card. It is working fine I guess so I don't think it is the culprit. I have internal audio using ALSA drivers which sound great. I have a Logitech Wireless mouse/keyboard that function well. All these function well except that the behavior of the O/S is erratic as mentioned. I have two 320gig HDs in AHCI mode. On the IDE I have a 120gig (slave) in line with a Sony DVD-RW.

Does anyone have any suggestions or maybe a list of things that could cause this type of behavior. 

I have not messed with the BIOS yet, that will be next when I get home. I think I read somewhere to deactivate Shadowing so I'll have to check that. All inputs will be considered. The system does work smoothly under XP unfortunately.

Thanks in advance.

---

### Post by heatpumpcontrol on 2007-06-14
> **heatpumpcontrol said:**
> Hi guys,

I've had feisty 7.04 now for about 2 months. I installed it on my new pc with a P5BVM-DO MB. I'm not at the pc right now so suggestions will have to be performed later next week. I've messed with the xorg.conf file settings thinking that might do it and I still can't get it to work correctly.

My Audio, Video, Mouse, window panning, you name it, acts erratic and jumpy and/or choppy. I have fixed my Nvidia video driver issue. I have an Nvidia PCIE 6500 256mb card. It is working fine I guess so I don't think it is the culprit. I have internal audio using ALSA drivers which sound great. I have a Logitech Wireless mouse/keyboard that function well. All these function well except that the behavior of the O/S is erratic as mentioned. I have two 320gig HDs in AHCI mode. On the IDE I have a 120gig (slave) in line with a Sony DVD-RW.

Does anyone have any suggestions or maybe a list of things that could cause this type of behavior. 

I have not messed with the BIOS yet, that will be next when I get home. I think I read somewhere to deactivate Shadowing so I'll have to check that. All inputs will be considered. The system does work smoothly under XP unfortunately.

Thanks in advance.

OK, I've come to note the following:
My wife logged in to her account (after pc was in hibernate) and I noticed that everything was working smooth. Audio, Video, window panning, everything was smooth.  I went back into my account to see if it was OK on my account and it was, so obviously it's a setting conflict that corrects itself when placed in hibernate. What can I do? Could it be ACPI BIOS support? I will look into that.

---

### Post by heatpumpcontrol on 2007-06-14
hello anyone?

---

### Post by heatpumpcontrol on 2007-06-25
Never mind. I'll figure it out eventually.

---

