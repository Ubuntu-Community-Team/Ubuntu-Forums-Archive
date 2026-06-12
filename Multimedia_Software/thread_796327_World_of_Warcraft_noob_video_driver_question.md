---
title: "World of Warcraft noob video driver question"
date: 2008-05-16
forum: Multimedia Software
---

### Post by eveningsparkle on 2008-05-16
Hi there! I *just* installed ubuntu two days ago and have been trying to install World of Warcraft ever since. I finally got it to work, except the fps is maybe 4 outside (20+ inside though,) which makes it unplayable. And now suddenly the icons aren't working in game.

The reason I'm posting it here instead of in a wine or gaming forum is because I'm 80% sure it has something to do with my drivers. From terminal I got this:

fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eccc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f57c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x37402b24) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7d0f84a4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x33d194,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d200,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub


I know it means something, but being so new, I have no idea what!

I have Mobile Intel(R) 915GM/GMS, 910GML Express Chipset family as a fake graphics/video card and just updated the driver from the directions at: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
I'm running Gutsy, and WoW worked fine for me on windows for a good two years, so I figure my hardware is fine, just a matter of finding the right driver. I've been searching google for days at this point-- please help! Thanks!

---

### Post by phoenix12345 on 2008-05-16
[http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/](http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/)

I hope this will help you.

---

### Post by eveningsparkle on 2008-05-16
> **phoenix12345 said:**
> [http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/](http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/)

I hope this will help you.


I tried following that one, but envy works with ATI and nvidia-- mine's intel so I am sort of out of luck. I followed the rest of the directions though, which is probably why it works except for the slow frame rate.

---

### Post by Rudedawg on 2008-05-16
I'm also having a similar problem. Almost. I haven't installed WOW yet, but I know that my frame rates are going to blow after inputting some of the rendering commands to check the settings (as listed on the wowwiki linux-wine page). I have the intel 960GL/965 intergrated video card chipset on my laptop. I can't even get the desktop effects to work past the basic settings. If anyone knows how to get the proper drivers installed for these cards, it would be GREATLY appriciated.

---

### Post by eveningsparkle on 2008-05-21
So I tried installing Direct X through wine and that made things show properly, at least. And with a fresh install of hardy I now have the coveted direct rendering: yes. Still slow outside, despite all the tweaks in the FAQs I've found online, and for some reason opengl makes different layers of graphics not align and makes the same unplayable-- I thought using opengl would make it run faster? 

Any thoughts? I could really use the help, I am running out of ideas. :(

---

