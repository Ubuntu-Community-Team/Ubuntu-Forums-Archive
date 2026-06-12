---
title: "Recommendations on motherboard"
date: 2008-04-24
forum: Mythbuntu
---

### Post by jhfry on 2008-04-24
Ok... it's the dreaded impossible hardware question... but I will try to keep my requirements as specific as possible to make it easier.

Basically I am trying to build a low cost myth frontend, possibly diskless, that will work flawlessly with mythbuntu.  Here are my desires, and requirements, order doesn't dictate level of preference, only the order I thought of things:

Requirements:
1. Small form factor, no larger than mini atx
2. Onboard audio with digital output (preferably optical, but coaxial is ok)
3. Onboard GBit NIC that must be capable of booting from the network via PXE
4. Headers for front panel USB
5. Onboard DVI ouput video with a decent chipset
6. Case fan headers and thermal sensors that will adjust the case fan speed when necessary for the onboard video and chipset.
7. All components MUST be fully supported in mythbuntu with minimal and widely published post install configuration.


Preferences:
1. Nvidia video, unless you have a good reason why your suggestion is better, and your certain I will have no issues with it.
2. A design that will allow for a single fan system, IE heatpipes that put all the heat near the processor to be ducted out with a single large fan.
3. TPM support (just in case it comes in handy in the next few years)
4. Support for HDCP (again just in case)
5. Uses low cost commodity RAM, no need for special expensive modules.
6. Support for passing SPDIF audio through the DVI connector; DVI+SPDIF -> HDMI.
7. On board support for HDCP audio (again just in case).

Essentially I want a Mythbuntu system on a single board.  I don't want to have to purchase any additional components (other than the obvious cpu, ram, ps, case) and still get excellent HD playback.

Please do not post your ideas or thoughts... I need actual experience here, preferably with Mythbuntu 8.04.  I am perfectly capable of locating boards with these features, I want to KNOW before I buy it that it will work!

I realize that I am asking a lot, but surely there is a board that comes close to reaching my goals.  I am open to solutions that require the purchase of an additional component or two, only if they are low cost and the board meets the rest of the requirements and many of the desired features.

I am confident that if any good answers are given, it will help reduce the endless "what should I buy" questions that always plague mythtv discussions.

Again, please don't send comments, just hard experiences... if someone suggests something that you KNOW won't work as advertised, please say so... but only if you KNOW they are wrong.

Thanks, and sorry for sounding so harsh... I'm just tired of reading page after page of conflicting suggestions and vagueness... I want to know what worked effortlessly for you, as I am sure others would like to know as well.

Once I make a purchase and test it, I will post my setup process in detail so  others can easily replicate it to get a functional frontend... as my thanks for any assistance I receive.

Thanks again!

---

### Post by Trollslayer on 2008-05-06
DVI doesn't have the signals for audio, you have to use HDMI or separate audio.
I have an Abit IF90 which is Intel/ATI based, Muthbuntu 7.10 (MythTV 0.20), supports HDCP.
The only thing is HDMI audio isn't working yet (generally, not ATI  or m/b specific).
TPM? Nope, not got it and don't plan to get it.
Is the PXE boot for diskless operation? Nice idea

---

### Post by Trollslayer on 2008-05-23
> **Trollslayer said:**
> DVI doesn't have the signals for audio, you have to use HDMI or separate audio.
I have an Abit IF90 which is Intel/ATI based, Muthbuntu 7.10 (MythTV 0.20), supports HDCP.
The only thing is HDMI audio isn't working yet (generally, not ATI  or m/b specific).
TPM? Nope, not got it and don't plan to get it.
Is the PXE boot for diskless operation? Nice idea

Update - HDMI audio is working (under 8.04, yet to test under 7.10), installed a simple app. from Synaptic called the default sound card sound selector

---

