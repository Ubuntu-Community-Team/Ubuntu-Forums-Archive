---
title: "Error when I switch between my Tivo and my HTPC"
date: 2013-10-03
forum: Multimedia Software
---

### Post by necbot on 2013-10-03
[COLOR=#000000][FONT=Arial]**BACKGROUND INFO**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
I built a HTPC using an Intel motherboard, my specs are&#8230;.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Intel DH77DF Motherboard[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Intel G1620 Celeron[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]2 GB Corsair DDR3-1333[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]1 TB Western Digital hard drive[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]My tv is a Samsung LN40C630[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]This box is running Ubuntu 13.04 on it but I also tested running [/FONT][/COLOR][COLOR=#000000][FONT=Arial]OpenELEC 3.2.1 32 bit[/FONT][/COLOR][COLOR=#000000][FONT=Arial] on it.  This computer is connected to my TV through an HDMI cable (HDMI port 2 of my TV).  Also connected to my TV is my Tivo through an HDMI cable (HDMI port 1 of my TV).  [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]**THE PROBLEM**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]When I turn on my HTPC I sometimes leave it on and switch my TV source to my Tivo so I can watch TV for a while.  The problem is that after I&#8217;m done watching my Tivo, when I switch back to my HTPC (HDMI port 2) the screen goes black and then shows static.  This pattern of static and then black repeats every three seconds or so.  It looks like the TV is trying to connect to the HTPC but that it can&#8217;t.  This does not always happen, it happens maybe 20% of the time.  I can almost always fix this by switching the TV back to my Tivo (HDMI port 1) and then back to my HTPC (HDMI port 2) AGAIN.  However, this does not always work.  Another tactic is to unplug the HDMI cable coming from the HTPC and plug it back in.  None of these are real solutions though.  I did some troubleshooting and there is what I found&#8230;[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]**TROUBLESHOOTING**[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]_It is not the HDMI cable or HDMI ports on the TV_[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I plugged my HTPC into the HDMI port normally used by the Tivo (HDMI port 1) using the Tivo HDMI cable.  Then I plugged the Tivo into HDMI port 2 using the HTPC HDMI cable.  The same problem occurred, the HTPC would periodically show repeating patterns of static and black.  I also have a PS3 plugged into HDMI port 3 of the TV.  Swapping the cables and ports between the PS3 and the HTPC still results in the HTPC displaying repeating patterns of black and static.  I&#8217;ve owned the Tivo and PS3 for several years now, I switch back and forth between them all the time and I have never seen this problem with either.  It is clearly not the cables or the HDMI ports on my TV.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]_The HDMI port on the HTPC motherboard is not the problem_[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have a DVI to HDMI adapter.  The motherboard has a DVI port.  I connected the DVI to HDMI adapter to my motherboards DVI connector connected my HTPC to the TV using an HDMI cable.  So now the picture is coming out of the DVI connector on the HTPC and going through the DVI to HDMI adapter and then to the HDMI cable that is connected to the TV.  I tested all HDMI ports and the error still occurs.  So now I know that even the source leaving the HTPC through the DVI output can trigger this behavior.[/FONT][/COLOR]  In addition, I was at my local electronics store and picked us an Asrock H77M-ITX motherboard.  The error occurs on this motherboard too.  It is clearly not an issue with the motherboard.

[COLOR=#000000][FONT=Arial]_Adjusting sleep timeout, screensaver settings, XBMC skins does not fix the issue_[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I tried changing the skin on XBMC, turning off screensavers and screen timeout on OpenELEC and Ubuntu.  The same error still occurs.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]_TV and Motherboard BIOS are probably not the issue_[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Changing the TV BIOS is not an option because my TV is on the latest firmware.  I cannot downgrade because there is no lesser version of firmware available on the Samsung site for this TV.  The motherboard BIOS is not the issue.  I went to the Intel site and flashed the latest version of their BIOS (version 110) and the issue still occurs.  Then I downgraded to the oldest version of their BIOS (version 69) and the issue still occurs.  Oddly enough, when I load up Intel VisualBIOS the issue NEVER OCCURS.  I can switch back and forth between the Tivo and the HTPC without any problem.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]_Issue only occurs when running a Linux OS._[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I tried various builds of Ubuntu 13.04 and 12.04.  I also tried various build of OpenELEC, from 3.2.1 to  1.0.2.  All of these OS&#8217;s showed this error. I installed Windows 7 Home Edition and everything worked perfectly.  I was never able to trigger this error using windows.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]_The error is HDMI/DVI related, VGA works fine_[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have a DVI to VGA adapter and my TV has an VGA port. I connected my HTPC to my TV&#8217;s VGA port using a VGA cable and I did not see this patterns of black/static. No matter how many times I switched between my Tivo and HTPC I could not trigger it, regardless of whether I was running Windows or a Linux distro.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]**SUMMARY**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So to recap&#8230;.  The HDMI cables are fine.  The HDMI ports on my TV and Motherboard are fine.  The error does not occur when I&#8217;m running the motherboard&#8217;s Visual BIOS or Windows.  The error occurs when I&#8217;m running a Linux distro.  The error is HDMI/DVI related.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I&#8217;ve done all the tests I can to pinpoint exactly what the issue is.  Based on this, it seems to be a Linux issue.  Something with Xorg maybe?  I have no idea where to go from here.  HELP![/FONT][/COLOR]

---

### Post by oldos2er on 2013-10-03
Moved to Multimedia & Video.

---

### Post by necbot on 2013-10-04
Okay, I even tried another motherboard, an Asrock H77M-ITX, and the issue still occurs.  This must be a linux driver issue of some type.

---

### Post by necbot on 2013-10-06
Okay, I'm throwing in the towel on this.  It's clear that whatever the issue is that it won't be solved with a simple fix.  I'm convinced it's an HDMI handshake issue related to xserver, but I'm reluctant to blame xserver because the xserver log shows NO errors when this behavior occurs.  I tried updating to the latest xserver using xorg-edgers ppa and the error still occurs.  My final question is....

Where do I submit a bug report?  On launchpad?  Or is there a bug tracking system used by the xserver developers?  Anyone?

---

