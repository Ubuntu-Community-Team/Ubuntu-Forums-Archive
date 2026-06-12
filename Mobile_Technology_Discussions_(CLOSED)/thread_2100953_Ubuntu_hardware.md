---
title: "Ubuntu hardware"
date: 2013-01-03
forum: Mobile Technology Discussions (CLOSED)
---

### Post by jech on 2013-01-03
Hi,

I'd like to discuss with you the HW choices for mobile Ubuntu devices. Just recently I purchased Rikomagic MK802 IIIS Android mini PC. It has an alpha support of booting Ubuntu. It would be absolutely great if this device could run Ubuntu TV, which was announced a year ago. Unfortunately AFAIK there is still no device officially supported which can run Ubuntu TV.

I'm wondering why there is this lack of HW running Ubuntu. I would like to see a tablet with Ubuntu, a USB mini PC running Ubuntu TV, something like Asus PadPhone running Ubuntu Phone or an ARM notebook (like Samsung Chromebook with Ubuntu).

I see a lot of opportunities where Ubuntu would fit perfectly. Unfortunately there are no real products. I'm wondering why. What is the main problem? GPU and other HW drivers? The HW makers are afraid of innovative things? At least in China it doesn't look so to me...

Do you know any interesting devices which can run Ubuntu?

---

### Post by Transhumanist on 2013-01-03
The reason is that most of the devices you list - actually, all of them - run on ARM chips.

While Ubuntu supports ARM architectures, unfortunately ARM devices have a lot of locked-down, proprietary peripherals. For instance, the GPU, 3G, Wireless radio, etc will rarely (if ever) be easy to access.

The point I am trying to make is that without these proprietary drivers, installing Ubuntu on these ARM devices will leave you with a slow, buggy, half-working mess.

Ubuntu doesn't want to tarnish their name like that, so they're trying desperately hard to get hardware manufacturers on board before they unleash their software on the public. Hence their repeated attempts to woo OEMs and ODMs.

Although apparently Ubuntu runs fairly well on the Nexus 7 and the Samsung Chromebooks.

---

### Post by jech on 2013-01-03
I know about these problems with HW and closed source drivers. But Android (with Linux kernel) was able to get these drivers for a very wide range of devices. Why Ubuntu couldn't?

And it doesn' concern only ARM devices. I have a MID (UMPC or a very small tablet as people would call it today) Viliv S5 with Intel Atom. I would like to use Ubuntu on it, but there are also problems with HW drivers. Many things also still don't work in Ubuntu on Nexus 7.

I think that cooperation with OEMs and ODMs is something that Ubuntu should concentrate on. I hope this will significantly improve now when Ubuntu for Phones was announced. It is quite useless if you have a great SW but no HW to run it on.

---

### Post by whatthefunk on 2013-01-03
> **jech said:**
> I know about these problems with HW and closed source drivers. But Android (with Linux kernel) was able to get these drivers for a very wide range of devices. Why Ubuntu couldn't?

Google is a huge multi billion dollar company.  Canonical, which owns Ubuntu, isnt.  If you have an extra few billion laying around Im sure Canonical would love a donation so that they have some extra weight to throw around when talking with hardware makers.

---

### Post by jech on 2013-01-04
whatthefunk> You shouldn't have to pay to any HW maker to use your OS/SW, which makes his product more attractive to customers. But if it isn't true, then this world is getting really weired.

I still own a pretty old Chinese device SmartQ V5. It runs a modified version of Ubuntu with LXDE. They even modified the OS and VLC to use HW video decoders. All HW is working - WiFi, BT, touchscreen etc.

---

### Post by grahammechanical on 2013-01-05
> But Android (with Linux kernel) was able to get these drivers for a very wide range of devices. Why Ubuntu couldn't?

Can you buy an Android OS and install it on a variety of mobile devices? That I think is the difference. People expect to download Ubuntu and install it on everything that has ever been sold. That, I would say is expecting too much.

Ubuntu phone, TV, tablet, multi mobile devices are all intended to be versions of the OS pre-installed on devices by OEMs. At the moment any kernel images of Ubuntu available for installation are for testing purposes.

Canonical invites OEMs as partners to bring Ubuntu to these devices. Ubuntu offers to make it easy and cheap for OEMs to put Ubuntu on any hardware that they choose to put on the market. They will even provide a Ubuntu kernel so the OEM can have their own User Interface if they desire or a modified Ubuntu User Interface based upon the OEM's design. If they so wish.

Oh, by the way, the Ubuntu phone OS uses Android drivers. Ubuntu TV is not a television receiving OS. It is an interface for OEMs to use on their smart TVs.

Regards.

---

