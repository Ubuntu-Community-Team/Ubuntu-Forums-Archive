---
title: "dual monitor Screen Resolutions  reverts to mirrored after reboot/logging-out"
date: 2008-12-17
forum: Multimedia Software
---

### Post by hanzj on 2008-12-17
Hi. 
Am using Ubuntu 8.10.

I have a video card that accepts 2 monitors. So I want to have a dual monitor setup, wherein, side-by-side, they act as one extra wide monitor.

My two CRT monitors are NEC MultiSync FP2141SB and AOC 9KLR. 


My video card:
>  ~$ lspci | grep -i vga
05:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)]According to the Net, my NEC MultiSync FP2141SB supports up to 2,048 x 1,536 resolution at 85 Hz. 



But in the "Monitor Resultion Settings" window, the max that the NEC monitor goes up to is 1680 x 1050 (16:10).

So, In System > Preferences > Screen Resolution, 
I remove the check box that is on "Mirrored Screens".

I then choose the ff: 
> AOC Intl 18": 1280 x 960 (4:3) at 60 Hz refresh
NEC 20": 1400 x 1050 (4:3) at 85 Hz refresh.I then hit the Apply button. Sometimes, it works, just right. 
But other times, I get a mirrored effect, with both monitors displaying the "AOC Intl 18" box on the upper left of each screen after I hit Apply and before clicking the Close button.
I don't know why it sometimes works and sometimes doesn't.

Also, even thought it's now working just fine now, after I reboot or log-out, the resolutions revert back to mirrored screens.

I don't know what's going on.

I have _not_ turned on hardware acceleration. I have not touched System > Administration > Hardware Drivers. In other words, I have NOT turned on ATI/AMD proprietary FGLRX graphics driver.



According to [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
> **Make** : ATI
    **Model** Radeon X850 XT 
    **Chipset/Driver**  [blank]
    **Auto-detected? **Yes 
    **2D**  Yes
    **3D **Yes 
    **Ubuntu Version**  Edgy & Dapper
    **Comments** if X server does not start with driver "Ati" (first boot) change it to "vesa" and then follow the instructions on wiki.cchtml.com
    **Last Updated** [blank]  

Below are outputs of what may be helpful info. If you need to know some more, please let me know.




To see the output of dmesg, pls see [http://paste.ubuntu.com/87354/](http://paste.ubuntu.com/87354/)
Output of lshw is at [http://paste.ubuntu.com/87356/](http://paste.ubuntu.com/87356/)
cat xorg.conf output is at [http://paste.ubuntu.com/87360/](http://paste.ubuntu.com/87360/)

---

