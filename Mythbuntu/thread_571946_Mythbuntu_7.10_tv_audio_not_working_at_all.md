---
title: "Mythbuntu 7.10 tv audio not working at all"
date: 2007-10-09
forum: Mythbuntu
---

### Post by phipman on 2007-10-09
I recently downloaded mythbuntu, set it up correctly, and *almost* everything works fine.

The audio on my computer speakers works, and plays music correctly when I insert a CD, but the problem is live TV. I have a non-split cable input and an Analog V4L capture card, in case that helps.

I have tried many different settings, but I just can't seem to get live tv audio.THe video part works fine, by the way. I get no audio driver errors or anything like that, and know that it isn't muted externally or by the | or \  mute command. If anyone could help, that would be great!

Thanks,
Phipman

---

### Post by superm1 on 2007-10-09
> **phipman said:**
> I recently downloaded mythbuntu, set it up correctly, and *almost* everything works fine.

The audio on my computer speakers works, and plays music correctly when I insert a CD, but the problem is live TV. I have a non-split cable input and an Analog V4L capture card, in case that helps.

I have tried many different settings, but I just can't seem to get live tv audio.THe video part works fine, by the way. I get no audio driver errors or anything like that, and know that it isn't muted externally or by the | or \  mute command. If anyone could help, that would be great!

Thanks,
Phipman

Typically these cards need an external cable running from the card to the line in on your audio card.  Do you have such cable ran?  If so, make sure that the capture volume is not muted.

---

### Post by phipman on 2007-10-09
It seems that my capture card (it is an internal card, by the way) has no audio outputs, only S-video, component, and analog inputs. The cable I am using is just a regular house cable tv line, so it goes into the analog cable input. My speakers are simply connected to the integrated speaker out port on my computer. I've tried the capture card on another computer (running Windows Media Center Edition), where the audio works during live tv with only one cable tv cable input.

Maybe downgrading from 7.10 will help?

---

### Post by superm1 on 2007-10-10
> **phipman said:**
> It seems that my capture card (it is an internal card, by the way) has no audio outputs, only S-video, component, and analog inputs. The cable I am using is just a regular house cable tv line, so it goes into the analog cable input. My speakers are simply connected to the integrated speaker out port on my computer. I've tried the capture card on another computer (running Windows Media Center Edition), where the audio works during live tv with only one cable tv cable input.

Maybe downgrading from 7.10 will help?
typically downgrading won't solve problems like this.

Checkout 'dmesg' and see if some information about errors loading a driver or unknown cards show up.  If not, then this is likely a configuration error in mythtv-setup.

---

### Post by dannyboy79 on 2007-10-10
within mythfrontend setup of livetv, what options are chosen for playback? alsa, oss or what? also, I noticed one time that my PCM volume within alsamixer was way low, I turned that up and then I had sound again within livetv. Check these few things. As superm1 says, check dmesg for any errors with ivtv.

---

