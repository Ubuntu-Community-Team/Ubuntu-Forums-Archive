---
title: "HD-PVR times out with AC3 audio (in fixes23893)"
date: 2010-04-07
forum: Mythbuntu
---

### Post by trevmar on 2010-04-07
Been struggling to get my HD-PVR fully functional with Mythbuntu fixes23893. 

Problem is that the HD-PVR takes a long time when changing channels, and that time varies depending on video and audio data encoding of the source (DCX3200 cable box). A timeout often kicks in when changing channels, giving an error message on the frontend screen **"irrecoverable recorder error."** 

I have to put a delay in the channel change script of at least 3.8 seconds. Otherwise, the Hauppauge HD-PVR AC3 audio locks-up/goes-away/whatever. But when I put in this delay the frontend doesn't wait long enough for the channel to change, hence the 'irrecoverable' error message.

I downloaded the source, and thanks to help from the thread at:
[http://ubuntuforums.org/showthread.php?t=835529](http://ubuntuforums.org/showthread.php?t=835529)
I was able to build a modified package. I even managed to sign it :)

I went through the .cpp files trying to find the HD-PVR channel change timeout. I found a variable in videosource.cpp which appeared to be a likely candidate:
 
            case CardUtil:: DVBS2:
            cardtype->setValue("DVB-S2");
            cardname->setValue(frontend_name);
            signal_timeout->setValue(13000); //was 7000
            channel_timeout->setValue(16000);
            break;

and so I changed signal_timeout and channel timeout, without any apparent benefit. So I went looking for the HDPVR 'case' statement, I couldn't find it :(

Could somebody point me to the appropriate timeout variable to change, so that I can rebuild my dpkg and get a usable Mythbuntu?

The backend changes channels and records them OK, with the 30 seconds extra I give it before the recording starts :) Typically the channel change takes just over 7 seconds. That is enough to seriously upset the frontend... Although it is hardly "irrecoverable," as selecting OK on the remote starts up the LiveTV again...

---

### Post by tgm4883 on 2010-09-29
> **trevmar said:**
> Been struggling to get my HD-PVR fully functional with Mythbuntu fixes23893. 

Problem is that the HD-PVR takes a long time when changing channels, and that time varies depending on video and audio data encoding of the source (DCX3200 cable box). A timeout often kicks in when changing channels, giving an error message on the frontend screen **"irrecoverable recorder error."** 

I have to put a delay in the channel change script of at least 3.8 seconds. Otherwise, the Hauppauge HD-PVR AC3 audio locks-up/goes-away/whatever. But when I put in this delay the frontend doesn't wait long enough for the channel to change, hence the 'irrecoverable' error message.

I downloaded the source, and thanks to help from the thread at:
[http://ubuntuforums.org/showthread.php?t=835529](http://ubuntuforums.org/showthread.php?t=835529)
I was able to build a modified package. I even managed to sign it :)

I went through the .cpp files trying to find the HD-PVR channel change timeout. I found a variable in videosource.cpp which appeared to be a likely candidate:
 
            case CardUtil:: DVBS2:
            cardtype->setValue("DVB-S2");
            cardname->setValue(frontend_name);
            signal_timeout->setValue(13000); //was 7000
            channel_timeout->setValue(16000);
            break;

and so I changed signal_timeout and channel timeout, without any apparent benefit. So I went looking for the HDPVR 'case' statement, I couldn't find it :(

Could somebody point me to the appropriate timeout variable to change, so that I can rebuild my dpkg and get a usable Mythbuntu?

The backend changes channels and records them OK, with the 30 seconds extra I give it before the recording starts :) Typically the channel change takes just over 7 seconds. That is enough to seriously upset the frontend... Although it is hardly "irrecoverable," as selecting OK on the remote starts up the LiveTV again...

Did you ever resolve this? I have an HDPVR now and am having a similar issue (Are you using digital audio?)

---

### Post by trevmar on 2010-09-29
No, I never resolved it. Haven't had time. 

As a result of this problem, which just got worse two weekly 'fixes' ago, we are not using the MythTV system much any more, being forced to watch directly from the set top box.

The new changes in 'fixes' mean that the HD-PVR will fail to get audio, and then stay without audio until a hardware reset. 

Yes, I know it is probably the HD-PVR's fault, and probably my own fault for not having time to debug and fix the problem. I just don't see how imposing a guilt trip on me (see the other thread I posted here trying to resolve this topic) is supposed to help others struggling with their HD-PVR MythTV

---

### Post by trevmar on 2010-09-29
.
I just installed fixes 26437, and we are back to relative stability again, I think. The frontend still times out with an "irrecoverable error" when I select an AC3 audio channel instead of a PCM DTV channel, but if I just escape the error message everything now works OK the second time around.

Having said that, there is something I need to track down -- to figure out why my HD 1080i channels no longer show up full screen on my HDMI TV (fed HDMI from my frontend). Sigh...
.

---

### Post by tgm4883 on 2010-09-29
> **trevmar said:**
> .
I just installed fixes 26437, and we are back to relative stability again, I think. The frontend still times out with an "irrecoverable error" when I select an AC3 audio channel instead of a PCM DTV channel, but if I just escape the error message everything now works OK the second time around.

Having said that, there is something I need to track down -- to figure out why my HD 1080i channels no longer show up full screen on my HDMI TV (fed HDMI from my frontend). Sigh...
.

Ok. I've just decided to use my red/white composite for audio since I don't have surround sound. Seems to be working good here

---

### Post by trevmar on 2010-09-29
That's the clever thing to do. It is switching back and forth from AC3 which seems to cause the most problems. I use the TOS-link optical feed from the Motorola set-top box.

---

