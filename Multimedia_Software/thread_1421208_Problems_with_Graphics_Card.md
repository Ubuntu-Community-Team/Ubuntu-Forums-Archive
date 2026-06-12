---
title: "Problems with Graphics Card"
date: 2010-03-03
forum: Multimedia Software
---

### Post by TheFlyingTangler on 2010-03-03
Hey guys, I've been googling this problem and have tried some of the fixes I've found but nothing seems to be working for me. I'm very new to Ubuntu (second day running it) so be gentle!

I got WoW installed and am running it through Wine1.2. When I go to open the game, my screen looks like this: [IMG]http://img.photobucket.com/albums/v119/BurningHadouken/Screenshot.png[/IMG] 

I tried doing a gedit of my WTF configuration to set the gxApi to OpenGL. I've also tried running in windowed, starting it up from terminal with the -d3d command, and combinations of all 3 of those, all of which was to no avail.

The driver on AMD's site for my video card (RV535 [Radeon X1650 Series]) seemed like it'd be the best solution, but upon attempts to install it, it informs me that I'm not running a supported version.

The following is what I see when I run it via Terminal
> archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:powrprof:DllMain (0x7dd40000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7dd40000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed90,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ec60,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f294,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f56c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f568,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f55c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f66c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x139068) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x39f124,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x39def0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df18,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmAssociateContextEx (0x30024, (nil), 16): stub
X Error of failed request:  GLXBadContextTag
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  144 ()
  Serial number of failed request:  68037
  Current serial number in output stream:  68245


I'm using Ubuntu 10.4 (or whatever the newest Distro is)

Thanks for any help.

---

### Post by Mark Phelps on 2010-03-05
Your card has no ATI drivers that will work in Ubuntu versions newer than 8.04.  ATI dropped Linux support for your card a long time ago.

You are relegated to using the open source drivers now.

---

### Post by TheFlyingTangler on 2010-03-05
Ugggh stupid ATI.

Thanks for the help!

---

### Post by TheFlyingTangler on 2010-03-05
I followed the instructions for the open source driver located here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Everything was fine until it got to the Configuring X.org part. When I ran either command, the vim or the nano, I simply got a blank page. Is there a method to search and locate the sections it tells you to edit, or do I have to build them from the ground up? If I have to build them, how would I go about doing that?

Sorry for all the questions, I'm just excited about learning all the intricacies of ubuntu and also at the prospect of getting this all to work. Thanks for any information.

---

