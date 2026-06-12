---
title: "sound mapping? sound only comes through subwoofer - 2.1 Surround"
date: 2014-06-16
forum: Multimedia Software
---

### Post by Austin_Moore on 2014-06-16
Hey guys, I will explain my scenario below and hope someone can help. 

I installed Ubuntu 14.04 LTS and everything works great after drivers are loaded. Upon going to play audio I noticed the sound was muddy and discovered all of the sound appears to be channeled through only the subwoofer/LFE of my 2.1 Surround speaker setup. The laptop is an Alienware 18, and I found an excerpt on the internet of someone with the same problem in a bug report but with no resolution. The other thing I notice is there is only one "speaker" bar in Alsamixer. When I viewed instructions from other people they showed multiple controls in Alsamixer. So everything is being mixed through the subwoofer as far as I can tell. I am trying to get the accurate mapping solution to fix this so sound can be channeled to all of the proper speakers. Right now it seems very generic and even in Pulseaudio the 'subwoofer' slider is greyed out so it obviously thinks this is a one output setup or something. This is the best I can tell to what is going on. When I do the speaker test, I get 'front-left', 'front-right' and 'center' with sound but each of those still plays through the subwoofer while displaying 'front-left', 'front-right' ...etc. 

So far I have discovered there are settings in daemon.conf in pulse and something about .asoundrc however I am not sure how to edit this. When I try to make a new .asoundrc file it says a file already contained in that location. I put it in my home directory. Does anyone have a fix or channel mapping solution for 2.1 surround? I found one package from diwic/surround21 but it didnt fix the problem on its own so i think there must be some way to map the channels properly. Does anyone know where to do this?

Any information or links are helpful.

---

