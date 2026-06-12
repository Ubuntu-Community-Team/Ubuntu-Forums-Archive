---
title: "Can't enable Xinerama / extended screen help!"
date: 2011-08-26
forum: Multimedia Software
---

### Post by teh'p3nsi0n3r on 2011-08-26
Excuse my short post and lack of details, posting this from my phone as I currently only have the use of one arm.

I have done a fresh install of ubuntu 11.04.

Everything is fine, Ubuntu seemed to be using the opensource ati drivers upon first boot.
Then prompted that I install the ati catalyst control center/drivers from additional drivers which I did.

Again smooth sailing untill I decided to enable my HD tv (hdmi) as my secondary screen. This again worked fine cloned. But I could not enable extended. The option is available but requires xinerama to be enabled. 

After restarting I could not login. Read up on this and others have has this issue with different cards. 
I proceeded to login to ubuntu (no effects) session and then swtiched off xinerama. (this did work in this session). The issue is getting it to work with unity. Logged back into unity now but I don't know how I can enable dual screens in extended mode. There are recomendations on other threads advising to use the open source drivers. But these don't work correctly. 

The card I am using is an ASUS EAH5570. This I believe has the radeon 5570 chip.

Any help would be greatly apreciated. :)

---

### Post by BicyclerBoy on 2011-08-26
I have never used ATI graphics adaptor..but

Catalyst 10.7 and later has eyefinity support.
Switching to (from ?) clone mode by pressing Fn+F4
I would not think extended desktop would be called xinerama, but it could be.

From nVidia point-of-view..
Xinerama can mean (2) distinct things: Xorg xinerama extension & the video driver xinerama extension.

I'm not running any multi-monitor setup on 11.04 or unity because it all seems a complete mess.
I should add that Unity3d is excellent on a netbook.

---

### Post by teh'p3nsi0n3r on 2011-08-26
Hi BicyclerBoy,

i see what your saying. So i have included a few screenshots.
Do i need to upgrade the catalyst control center/drivers?.

Xinerama from following threads and info on the net needs to be ticked a enable an extended desktop. (Screenshot attached.)

This is what's causing the problem.

---

### Post by BicyclerBoy on 2011-08-27
Remember I have never seen this tool before but..
I think the ATI logo splashed everywhere suggests this could be an old catalyst control centre & driver. I see the number 8.84 listed.

AMD Catalyst 10.7 landed in July2010.

The thought of installing AMD/ATI drivers fills me with fear & trepidation.

---

