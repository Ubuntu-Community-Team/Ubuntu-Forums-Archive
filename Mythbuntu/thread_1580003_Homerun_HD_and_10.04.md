---
title: "Homerun HD and 10.04"
date: 2010-09-22
forum: Mythbuntu
---

### Post by moseleyb on 2010-09-22
Hi Folks,

Trying to set up my Homerun HD with 10.04. When I scan the channels I get strong signal overall at the top of the screen but the channels  each "atsc time out"  implying  that they are not receiving anything. Is there a simple setting that I am forgetting? I know that the HHD works. I watched TV with it over the wireless network last night.  Any simple suggestions for a begininer?

Does anyone have instructions for setting up HHD with 10.04? Silicon Dust hasn't seemed to have posted any yet. 

Thanks!

---

### Post by AKADAP on 2010-09-24
Do you have the HDHomeRun connected via cable or antenna?
Have you tried the hdhomerun_config_gui tool? See if you can tune the channels with that.

---

### Post by AKADAP on 2010-09-24
*

---

### Post by dcosler on 2010-09-29
> **moseleyb said:**
> Hi Folks,

Trying to set up my Homerun HD with 10.04. When I scan the channels I get strong signal overall at the top of the screen but the channels  each "atsc time out"  implying  that they are not receiving anything. Is there a simple setting that I am forgetting? I know that the HHD works. I watched TV with it over the wireless network last night.  Any simple suggestions for a begininer?

Does anyone have instructions for setting up HHD with 10.04? Silicon Dust hasn't seemed to have posted any yet. 

Thanks!

moseleyb,
I would just like to echo your questions about the HDHR, MythTV, and Ubuntu 10.04.  I too am trying to get everything configured correctly, and all the configuration is borderline ridiculous.  My HDHR obviously has no issues delivering a stream, why must I jump through a thousand MythTV screens and settings just to record the stream?  Makes no sense.

Furthermore, why can't I tell MythTV to ONLY show the channels that my HDHR can tune??  What is the point of a "channel scan" when I've already got a "Digital Cable.xml" file from my HDHR?  I'm baffled.

I know there is a decent piece of software behind all the MythTV screens...  and I know that somehow, I'll be able to tell it to record TV using the stream from my HDHR.  But..  I'm not holding my breath.  :(

Anybody??  Help?  There has to be hundreds of you guys out there running Lucid/MythTV/HDHR setups with success.  Care to comment?

Thanks,
Don

---

### Post by grandpaken on 2010-09-29
Have you looked over this page?

[http://www.mythtv.org/wiki/Silicondust_HDHomeRun](http://www.mythtv.org/wiki/Silicondust_HDHomeRun)

 I'm not using QAM so I can't help with specifics but your scan will find tons of QAM channels but most will be encrypted.

---

### Post by Brynwood on 2010-09-29
You mention a strong signal. Are you using the HD Homerun Config GUI? (It's in the Multimedia menu in Mythbuntu.) How are the signal Quality and Symbol Quality? 
 
Having a strong signal but a poor signal quality indicates the signal is too strong. Try reducing the signal strength and see if that helps. Radio Shack used to sell an antenna/cable signal attenuator. I can't find it on their web site now. They might have discontinued it. 
 
Even running the signal through a 4-way splitter should reduce it by 6 dB - enough to see a diference. 
 
If the tuner is being overloaded, reducing the signal will keep the signal strength high, and the signal quality will go up. Your channel scan should start producing results.

---

