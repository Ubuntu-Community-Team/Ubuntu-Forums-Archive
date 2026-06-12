---
title: "Basic system design question"
date: 2007-12-17
forum: Mythbuntu
---

### Post by RustyWyatt on 2007-12-17
Hi Folks,

I am a relatively new and VERY happy user of Ubuntu! I currently use my T60 with 7.10 as my main pc, via a wireless network with a 500 gb NAS and network printer.  My NAS currently provides support for media streaming and I currently use this feature for music (MP3).

I am going to use my old Win desktop (2.4 Ghtz) as a media server for music and videos. I have an extensive collection of VCR tapes that I want to preserve and I might as well spool all of my DVDs on to the media server also.  I have no interest in TV at this time! It seems to me like MythTV is the best option for my project.

My questions are:

1) Can I configure MythTV for music and video support now and add TV later if I wish, without having to completely reinstall MythTV?

2) Given the forced move to digital TV in a year or so, if I have to buy TV cards now, can I provide for future digital TV in my hardware decisions today?

3) Do you have any additional suggestions for my proposed project?

All comments GREATLY appreciated!

Thanks,
Tom

---

### Post by milhouse on 2007-12-17
> 2) Given the forced move to digital TV in a year or so, if I have to buy TV cards now, can I provide for future digital TV in my hardware decisions today?

Yes.  But exactly what you pick will depend.

If you have cable this isn't an issue as the switch only affects OTA broadcasts and cable providers will continue to provide an analog signal.    So you could go with an analog tuner.

If you pick up your TV OTA and want to "future proof" then you'll need a dual analog/digital tuner.  There are at least a few dual digital/analog tuners out there.  The HD Homerun and DViCO FusionHDTV are both built around the same chip and "mostly" work (some people say they have both analog/digital working well, some don't).  I have the latter running on mythbuntu 7.1  and it was quirky handling the analog audio.  I have cable though, so I had the option of not using the analog tuner so this wasn't a bit deal.  If I was picking up TV OTA though, this would have been a big problem.

If you have digital cable with a cable box and get "premium" content then the best choice would depend on your STB and it's outputs.  In this case you would probably have many options (firewire, component video, analog), but you could always use an analog tuner.

-r

---

### Post by newlinux on 2007-12-18
1. Yes, you will have to add and configure the tuner card later.
2. Just as a point of clarification, the HD Homerun does not do analog tuning. Ones that do both that I have used are:

Dvico Fusion 5 lite
Kworld ATSC 110/115
pchdtv 5500

Audio on analog was a bit buggy on all of them. If I were you, if all you want is analog now I'd be a dedicated analog card with a hardware encoder (none of the dual analog/digital cards that I know of do hardware encoding) and then buy a digital card when you want to use it. Especially if you are planning on capturing cable.

3. Read all the documentation before proceeding. Make sure Myth is what you want and allot enough time for mistakes in the install. Make sure your hardware is likely to work.

---

