---
title: "[SOLVED] Not Getting Output On Tv"
date: 2008-07-13
forum: Multimedia Software
---

### Post by greatboss on 2008-07-13
Hi All Experts

I am on ubuntu 8.04 Hardy with 2.6.22-14-server.

I have a  ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
graphics card and S-Video cable plugged in from the laptop to the TV. After following all the posts previously written, I still am unable to get the laptop output on to the TV [ Bush ].

I am using the following file and face the following issues.

1. If I keep the line Option "TVOutput" "NTSC", the laptop screen flickers but nothing happens on the TV.

2. atitvout detect did show that the TV was connected via the S-Video but the Xorg went down on boot up and the text screen was displayed ONLY on the laptop and nothing on the TV.

3. When I run atitvout auto I get the following with 800X600 resolution:-

VBE call failed.
Maybe this command is not supported by your graphics adapter?
Did your parameters (if you specified some) really make sense?
Please try all other available commands before complaining!
VBE call failed.
Maybe this command is not supported by your graphics adapter?
Did your parameters (if you specified some) really make sense?
Please try all other available commands before complaining!

Can anybody help me since I am a die-hard Ubuntu fan and have to prove to my wife that Windows has gone for GOOD.

Please find attached the xorg file that I am currently using.
PLEASE DONOT DIRECT ME TO ANY TUTORIALS SINCE I HAVE FOLLOWED THEM about 20 times to no effect, though this should not be treated as a brash statement from my side.

---

### Post by markbuntu on 2008-07-13
Which driver are you using for your video card?

---

### Post by greatboss on 2008-07-14
Hi

I am using the GATOS 6.6.3 after patching it as indicated in the posts that I have gone through.

Just to confirm, could you advise on how I can verify it and suggest if thats the correct version that I have tried.

---

### Post by greatboss on 2008-07-15
Hi

CAN ANYBODY GUIDE ME PLEASE ???:(

---

### Post by greatboss on 2008-08-19
Hi

The problem got solved after a lot of trying and then simply activating the vesa driver once upgrade to 8.04.1 was done.

At least I have seen some output on TV and can switch back and forth between laptop and tv.

Closing this post.

> **greatboss said:**
> Hi

CAN ANYBODY GUIDE ME PLEASE ???:(

---

