---
title: "Share Audio device on Lucid"
date: 2010-06-08
forum: Multimedia Software
---

### Post by pmbsa on 2010-06-08
Hi, is there a way to share an audio device between something like XBMC and squeezeslave on ubuntu. I have not had a problem on windows and mac before so this is new to me but it appears that if I have squeezeslave running that ubuntu has no access to the sound card.

I have a Zotac mag ION chipset. if that makes any difference to the equation.
thanks
paul

---

### Post by pmbsa on 2010-06-10
surely there are other people about who have done this already? I cant believe its not possible to share the audio devices across applications?

I have tried running squeezeslave using aoss as well, I real in a few places that that was the way to go but that didnt seem to help me at all.

thanks
Paul

---

### Post by Breambutt on 2010-06-10
Even if the people around here helpful, they might be busy and not feel like studying XBMC and SqueezeSlave on your behalf. I've never heard of either one, so "sharing an audio device across applications" just seems a little... vague. 

I can put my butt on stake that there's at least a workaround or even better way to accomplish the same thing, but I'm not exactly sure of what's going on here. Are you trying to control a "multimedia center" on/from Ubuntu remotely with Squeeze, locally or what?

And what's the actual error message, could it be the device is just busy (in use) instead of not having access to it at all?

---

### Post by pmbsa on 2010-06-11
Hi, the situation is reasonably simple to explain.

I have a Zotac Mag (ION Based machine) which I use primary as a media centre pc running XBMC (which is just media centre software like Mythtv etc). Squeezeslave is a software based client which allows you to turn your Linux, Mac or windows based machine into a zone on a squeezeserver network. It is a simple command line utility that can be run as a deamon and then be controlled by the various methods used to control devices on a squeezenetwork. 

I am running stock standard lucid and I have my sound setting left as the default installation setting (analog duplex). I have an spdif cable connected to my digital amp. Everything works perfectly as far as the normal operation goes, sound is working without a problem and the digital signal is being passed through to my SPDIF when applicable. 
However, as soon as I run squeezeslave the sound device then becomes unavailable to all other applications. Most of them will simply hang or provide an error saying that the sound device is not available. Soon as I stop Squeezeslave there is no problem again. I read on a few Myth sites that running the deamon under aoss stops this from happening but I suspect its more complicated then that since it did nothing to resolve my issue.

---

