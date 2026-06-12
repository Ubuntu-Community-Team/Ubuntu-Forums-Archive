---
title: "No center channel in 5.1"
date: 2011-12-12
forum: Multimedia Software
---

### Post by isecore on 2011-12-12
Just earlier today my Soundblaster Audigy2 ZS which had been working perfectly for the last 6+ years decided to die on me. My computer locked up and upon reboot it was no longer listed in sound hardware and was not listed when doing lspci. So I yanked it out and accepted that I was confined to onboard audio.

Which seemingly works fine, albeit with one glaring annoyance: for some reason the center channel in 5.1 setting exists but provides no sound. It's as if it's permanently muted. At first I thought I had connected my speakers wrong, but in an analog 5.1 setup the LFE (the subwoofer) and center shares that plug, and the LFE rumbles just fine when performing a speakertest.

Any ideas on how to fix this?

lspci gives:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

and I know from the motherboard specifications that it's a Realtek ALC889 powering it.

UPDATE: Sorry, I'm an idiot. I should've checked alsamixer first, where it happily showed me the center channel is muted. Why does it do this? This would be extremely confusing for a newbie since there's zero GUI tools to figure these things out.

---

