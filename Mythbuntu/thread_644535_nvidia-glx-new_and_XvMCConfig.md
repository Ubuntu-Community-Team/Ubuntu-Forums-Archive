---
title: "nvidia-glx-new and XvMCConfig"
date: 2007-12-19
forum: Mythbuntu
---

### Post by faginbagin on 2007-12-19
I just set up a myth box following the instructions for a combined backend, frontend and desktop as described at:
[https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop)

I used the MCC to install the nvidia proprietary drivers and was wondering why it didn't change /etc/X11/XvMCConfig to use nvidia's shared library as described in mythtv.org documentation.

MCC seems to be taking care of so many details automatically (things that I had to do by hand when I was using debian etch), that I'm wondering if maybe changing XvMCConfig is a step that should not be done (although I did it under debian etch).

My card has a GeForce 7300 LE GPU which supports MPEG-2 decoding.

So, should I or shouldn't I change XvMCConfig so it contains:
libXvMCNVIDIA_dynamic.so.1
replacing:
libXvMC.so.1

And, if I should make this change to take advantage of MPEG-2 decoding on my card, is there some reason why mythbuntu didn't do it for me? Maybe because not all nvidia cards work with the library?

TIA

---

### Post by superm1 on 2007-12-19
There is a lot of confusion whether that step is actually necessary.

Can you try it without modifying the XvMCConfig?  See if you get the b/w OSD.  If you don't, then we'll get a bug filed and get this fixed for hardy.

---

### Post by faginbagin on 2007-12-19
I think I've tested it, although I'm a bit confused about the B/W part of it. I assume you mean black & white.

With the original library, doing  some channel up/down's while watching live tv, I see the same OSD that I see with the nvidia library. Both configurations' OSD is in red & blue, not B&W. Is this what you wanted me to test?

This is different from the OSD I saw under debian etch and I don't recall making a change that might account for the difference. Perhaps something mythbuntu did, e.g. a different skin/theme (I would like to know)?

Do I need to change something with mythtv-setup or with mythfrontend's Setup to verify whether the library affects functionality? Or, am I not doing the right test? So far, I don't see a difference. Oh, and I haven't looked at any logs, either.

---

### Post by superm1 on 2007-12-19
> **faginbagin said:**
> I think I've tested it, although I'm a bit confused about the B/W part of it. I assume you mean black & white.

With the original library, doing  some channel up/down's while watching live tv, I see the same OSD that I see with the nvidia library. Both configurations' OSD is in red & blue, not B&W. Is this what you wanted me to test?

This is different from the OSD I saw under debian etch and I don't recall making a change that might account for the difference. Perhaps something mythbuntu did, e.g. a different skin/theme (I would like to know)?

Do I need to change something with mythtv-setup or with mythfrontend's Setup to verify whether the library affects functionality? Or, am I not doing the right test? So far, I don't see a difference. Oh, and I haven't looked at any logs, either.
Well the easiest way to tell whether XvMC was working is by the OSD.  If it is black and white rather than the normal red and blue, then XvMC is on.

There are two areas that might affect XvMC, inside the frontend's appearance section, and that config file.  If you don't modify the config file, but do turn on that appearance section, see what happens.

---

### Post by faginbagin on 2007-12-19
Oops, I had forgotten to change the Preferred MPEG2 Decoder in TV Settings -> Playback to Standard XvMC. When I made that change, then using the nvidia library did change the OSD display to B&W.

One odd thing:
I decided to compare mythfrontend's CPU usage with the different libraries and was surprised to find that, when watching the same recording,  it used 3% more CPU with the nvidia library than without it. I would have expected its CPU usage to be lower if the nvidia GPU is doing the decoding.

I guess I'm beginning to question whether I'm really taking advantage of hardware decoding.

I should mention that while I was monitoring mythfrontend's CPU usage, mythbackend was recoding and mythcommflag was using more CPU than anything else. So I think I will repeat the test when nothing is being recorded and see if that makes a difference.

Another thing that surprised me was, when I hit pause, mythfrontend continued to use the CPU. I would have thought it would go quiet, waiting for input from me. Are you familiar with mythfrontend's internals? Enough to know why it's still using CPU while paused?

Thanks for your help and interest.

---

### Post by superm1 on 2007-12-19
> **faginbagin said:**
> Oops, I had forgotten to change the Preferred MPEG2 Decoder in TV Settings -> Playback to Standard XvMC. When I made that change, then using the nvidia library did change the OSD display to B&W.


Okay so to verify, /etc/X11/XvMCConfig has the old default in it, and b/w OSD works, correct?

> 

One odd thing:
I decided to compare mythfrontend's CPU usage with the different libraries and was surprised to find that, when watching the same recording,  it used 3% more CPU with the nvidia library than without it. I would have expected its CPU usage to be lower if the nvidia GPU is doing the decoding.

I guess I'm beginning to question whether I'm really taking advantage of hardware decoding.

I should mention that while I was monitoring mythfrontend's CPU usage, mythbackend was recoding and mythcommflag was using more CPU than anything else. So I think I will repeat the test when nothing is being recorded and see if that makes a difference.

Another thing that surprised me was, when I hit pause, mythfrontend continued to use the CPU. I would have thought it would go quiet, waiting for input from me. Are you familiar with mythfrontend's internals? Enough to know why it's still using CPU while paused?

Thanks for your help and interest.

You will have adjust the syncing method (open GL,rtc,or such), and you will need to adjust whether it syncs on vblank to play with these settings.

---

### Post by faginbagin on 2007-12-19
> **superm1 said:**
> Okay so to verify, /etc/X11/XvMCConfig has the old default in it, and b/w OSD works, correct?.

No, I only get B&W OSD with the nvidia library, not with the default library. I get red & blue OSD with the default library.

> **superm1 said:**
> You will have adjust the syncing method (open GL,rtc,or such), and you will need to adjust whether it syncs on vblank to play with these settings.

Well, I tried "Enable OpenGL vertical sync for timing" back when I was using debian etch and I think it caused my system to lock up. I was using the same nvidia driver, direct from nvidia, not the ubuntu packages. Maybe with ubuntu gutsy's newer kernel and who knows what else, it will be stable. In any event, I'd want to do a backup before mucking with it or other options.

When you say "rtc" are you referring to "realtime priority threads", also on the same TV Settings -> Playback screen? According to the onscreen help, that setting only makes a difference if mythfrontend has root privileges. Perhaps you're referring to some of the options that can be set in nvidia-settings? Something to do with Real Time Clock? I don't remember seeing anything about that in nvidia-settings or in nvidia's README, but then I'm sure I'm suffering from information overload. Can you be a little more specific?

Would any of these options affect CPU usage while mythfrontend is paused?

The info that's available on the web could use some work. When I don't understand something, I do my best to learn (e.g. google, the various wikis, etc). When I can't find anything telling me why I should do something, I tend to be gun shy, especially since things like my experiment with OpenGL vsync have just caused me more problems than theyve solved. I really wish there were a guide that said, if you have an nvidia card with hardware decoding, you need to do a thru z, with explanations, or at least references to sources that explain why it's important. MythTV is an example of a really cool app that has a dizzying array of config options and insufficient info explaining why I should care about many (if not most) of these options. I know I'm whining. After I've gotten my feet wet with mythtv, and I'm confident that I've got a stable system that's taking full advantage of my h/w, maybe then I'll try to share what I've learned by adding to one or more wikis.

---

