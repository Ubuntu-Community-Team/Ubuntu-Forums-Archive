---
title: "Is GT 240 supported in mythbuntu"
date: 2010-03-26
forum: Mythbuntu
---

### Post by rramesh on 2010-03-26
I have stutter problem with my 9400 GT and want to buy a GT 240 with GDDR5. Currently there is one on sale for $65 after rebate.  However, I am worried about getting it to work in my mythbuntu box. 

I have a standard 9.10 installation with proprietary nvidia drivers. I notice that driver version is some 18x... I am told that I need version 195x to get GT 240 working.  What do I have to do to get this version. Is there a tutorial of some sort for this/ My google search does not come up with any instructions. I  only get general description of capabilities nothing about getting driver/installation.  I am a debian user and have started using mythbuntu only a month ago. So I am a bit less educated in the workings of a ubuntu releases. 

Ramesh

---

### Post by novellahub on 2010-03-26
For the Nvidia Driver, you can use the Mythtbuntu auto-build (Install the newer Nvidia driver in synaptic after you add the repo):

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

Follow these instructions here for upgrading and patching ALSA if you plan on using HDMI audio:

[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

---

### Post by rramesh on 2010-03-26
Thanks. I will try the auto build. I am only interested in video and will use exisitng motherboard autio.
I am connecting audio to receiver that does not have a hdmi input.

Ramesh

---

### Post by gordintoronto on 2010-03-26
It's quite possible that the stutter is due to delays elsewhere, and has nothing to do with your video card.

---

### Post by rramesh on 2010-03-26
It is entirely possible that the bottleneck is elsewhere especially because it has an old MB (nvidia 6100 + AMD 939 2G) with 1.5G sata.  Since the stutter is occasional when I am not doing anything on the machine and 9400GT is limited in VDPAU, I like to begin there.

That said, I am interested in understanding your thoughts. Can you give me some pointers that I can experiment with? BTW, I have turned of all freq scaling stuff that is supposed drop bus speeds. Load on the 
machine is usually less than 30%. So, I doubted video. Besides, increasing vdpaubuffersize to 32 did improve, but could not make the stutter go away.

Ramesh

---

### Post by gordintoronto on 2010-03-26
Are backend and frontend on the same machine?  If not, something as simple as another person on the network running a bittorent download could cause stuttering.

Likewise, there are background processes in Ubuntu which might be responsible.

---

### Post by rramesh on 2010-03-27
I fired off a tail -f /var/log/mythtv/mythfrontend.log and started 
watching TV. Each time it stuttered, I noticed that mythweather process 
would spawn something that will get weather data. I suspect this is the 
problem for my stutter. This explains why my stutter would be very  
periodic and would go away when I wait for a while (pause). It is too 
much of a coincidence for video to have tough to render passages at such 
regularity.  I have turned off mythweather. So far (about 30min) no stutter. So this
looks like it. 

Ramesh

---

### Post by gordintoronto on 2010-03-28
Excellent!  You should mark this thread as "solved" using the "thread tools" at the top of the page.

---

