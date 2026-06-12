---
title: "Graphical issues in newly installed World of Warcraft. Screens attached"
date: 2009-07-28
forum: Multimedia Software
---

### Post by tesseract1 on 2009-07-28
I am having some graphical issues in World of Warcraft.  As you can see from what I've attached, I've highlighted the glitched graphics.
Items in my bags, spells on my bar, my portrait, my buffs, and items in my inventory are mostly glitched.

I am running:[INDENT]Ubuntu 9.04
wine-1.1.26.
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4850 X2
OpenGL version string: 1.4 (2.1.8787)
[/INDENT]

---

### Post by tesseract1 on 2009-07-29
Is there another forum I can go to where I might find help?

---

### Post by themusicalduck on 2009-07-29
Did you set Wow to run in opengl mode with the -opengl flag on the launcher? Also did you disable desktop effects before running it?

---

### Post by tesseract1 on 2009-07-30
Ok so I didn't know i had to turn off my desktop effects before playing games.

I use compiz and awn.  Is there some sort of way I can turn off Compiz but keep it's settings so I can turn it back on quickly whenever?  Like a light switch?

These are the graphical issues I get when I add -opengl to the launcher.  The previous issues go away, but this seems much worse.  

I haven't figured out how to disable Compiz yet.  So maybe if I do that things will be better?

---

### Post by xc3RnbFO8P on 2009-07-30
> I haven't figured out how to disable Compiz
System> Preferences> Appearance>  Visual Effects> none

---

### Post by themusicalduck on 2009-07-30
Before doing that, you need to install the package simple-ccsm. This means you can go back to any custom configuration for compiz you might have made.

```
sudo apt-get install simple-ccsm
```

and a 'Custom' option will appear on the visual effects page.

---

### Post by tesseract1 on 2009-08-01
With appearance effects to none I haven't seen any improvement. Actually it is worse, most things in WoW are upside down!

With appearance effects and with -opengl at the end of the path makes the graphics even worse,  They look like the second pair of screenshots I posted.


Here is my wine output when running WoW, there are some errors.  What are the fixme: mixer: ALSA errors about?  Also the fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #11:?  What are these?

```

k@asus:~$ wine "/media/disk/Program Files/World of Warcraft/Wow.exe"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
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
fixme:win:EnumDisplayDevicesW ((null),0,0x39edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f084,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f584,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f578,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5b8,0x00000000), stub!
err:d3d:CreateContext Requesting MultiSampleType=8
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1473d8) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x39f140,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x16d838,0x16d738): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x39deec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df24,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39debc,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x374041e4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:d3d_surface:surface_load_ds_location No up to date depth stencil location
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #7:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #11:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #15:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #20:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #30:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #32:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #34:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #36:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #40:
fixme:d3d_shader:print_glsl_info_log     Fragment shader was successfully compiled to run on hardware.


```

---

### Post by Doctor Debian on 2009-08-01
Try this with in opengl mode:

Open the registry editor (type regedit in terminal) and navigate to the following key

HKEY_CURRENT_USER\Software\Wine\

Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder.

Right-click on the wine folder and select [NEW] then [KEY]

Replace the text New Key #1 with OpenGL

Right-click in the right hand pane and select [NEW] then [String Value]

Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)

Then double click anywhere on the line, a dialog box will open.

In the value field type GL_ARB_vertex_buffer_object

Copied from WineHQ. Fixed the problem for my on my Acer laptop.

---

### Post by tesseract1 on 2009-08-01
> **Doctor Debian said:**
> Try this with in opengl mode:

Open the registry editor (type regedit in terminal) and navigate to the following key

HKEY_CURRENT_USER\Software\Wine\

Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder.

Right-click on the wine folder and select [NEW] then [KEY]

Replace the text New Key #1 with OpenGL

Right-click in the right hand pane and select [NEW] then [String Value]

Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)

Then double click anywhere on the line, a dialog box will open.

In the value field type GL_ARB_vertex_buffer_object

Copied from WineHQ. Fixed the problem for my on my Acer laptop.

This seems to have solved a lot of my graphical issues.  I still have some glitches however.  

All text in the game is gone.  Also my map is completely white. Could this be the issue?

```
failed to open Z:/media/disk/Program Files/World of Warcraft/Data/Interface/Icons
failed to open Z:/media/disk/Program Files/World of Warcraft/Interface/Icons

```

---

### Post by Doctor Debian on 2009-08-01
> **tesseract1 said:**
> This seems to have solved a lot of my graphical issues.  I still have some glitches however.  The text in the chat frame disappears and the text in the Blizzard user interface disappears.  Also my map is completely white.  Strange!

The reason your map is white is because of ATI not implementing pixelbuffers in their drivers. Everyone who uses fglrx on linux has that problem.

As for the text, make sure you have the msttcorefonts package installed. (Microsoft fonts)

---

### Post by Doctor Debian on 2009-08-01
> **tesseract1 said:**
> 
All text in the game is gone.  Also my map is completely white. Could this be the issue?

```
failed to open Z:/media/disk/Program Files/World of Warcraft/Data/Interface/Icons
failed to open Z:/media/disk/Program Files/World of Warcraft/Interface/Icons

```
No, that is the directory WoW uses when installing a custom addon icon set. Perfectly normal behavior.

I noticed that you are running WoW from an existing windows install- Copying the World of Warcraft folder to your .wine/drive_c/Program Files folder may fix your font issue, as there may be font permission issues with NTFS3G.

---

### Post by tesseract1 on 2009-08-01
The fonts are installed.

---

### Post by tesseract1 on 2009-08-01
Ok i'll try copying.

---

### Post by tesseract1 on 2009-08-01
Does anyone know what this is about?

```

fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer


```

Is it normal that WoW in Ubuntu has far less FPS than ran on Windows OS?

---

### Post by Doctor Debian on 2009-08-01
> **tesseract1 said:**
> Does anyone know what this is about?

```

fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer


```

Is it normal that WoW in Ubuntu has far less FPS than ran on Windows OS?

An answer to both:

The first one may be because of your sound settings in winecfg. Although it shouldn't interfere with WoW, for optimal performance, make sure ALSA is selected in the audio tab. The ATI drivers are currently quite lacking for Linux, thus causing the FPS drop experienced from Windows to Linux. Sorry for answering all the good questions :)

---

### Post by tesseract1 on 2009-08-01
It certainly is selected.

---

### Post by tesseract1 on 2009-08-01
So I copied WoW directory from my windows to my wine folder.  Wow starts fine, I get online, and the text is all there, then after about 10 seconds it all disappears. =/

Is ATI planning on improving their drivers for Linux? =/

---

### Post by Doctor Debian on 2009-08-01
> **tesseract1 said:**
> So I copied WoW directory from my windows to my wine folder.  Wow starts fine, I get online, and the text is all there, then after about 10 seconds it all disappears. =/

Is ATI planning on improving their drivers for Linux? =/

What is the error message when it crashes?

I don't know ATI/AMD's roadmap on their driver, but the open-source driver for radeonhd cards is progressing nicely.

---

### Post by tesseract1 on 2009-08-01
No error, no crashing, this is my most recent wine output in which all the text disappeared from the screen.

```

kevin@asus:~/.wine/drive_c/Program Files/WoW$ wine Wow.exe -opengl
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
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
fixme:win:EnumDisplayDevicesW ((null),0,0x39edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f084,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f584,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f578,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f140,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x144190,0x1440d8): stub
failed to open C:/Program Files/WoW/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x39deec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df24,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x374041e4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
failed to open C:/Program Files/WoW/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x39dae4,0x00000000), stub!
failed to open C:/Program Files/WoW/Data/Interface/Icons
failed to open C:/Program Files/WoW/Interface/Icons
fixme:win:EnumDisplayDevicesW ((null),0,0x39deb4,0x00000000), stub!

```

Would I be better off using the open-source driver?

---

### Post by Doctor Debian on 2009-08-01
> **tesseract1 said:**
> No error, no crashing, this is my most recent wine output in which all the text disappeared from the screen.

```

kevin@asus:~/.wine/drive_c/Program Files/WoW$ wine Wow.exe -opengl
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
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
fixme:win:EnumDisplayDevicesW ((null),0,0x39edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f084,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f584,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f578,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f140,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x144190,0x1440d8): stub
failed to open C:/Program Files/WoW/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x39deec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df24,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x374041e4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
failed to open C:/Program Files/WoW/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x39dae4,0x00000000), stub!
failed to open C:/Program Files/WoW/Data/Interface/Icons
failed to open C:/Program Files/WoW/Interface/Icons
fixme:win:EnumDisplayDevicesW ((null),0,0x39deb4,0x00000000), stub!

```

Would I be better off using the open-source driver?

No, as the open source driver for your card does not yet have full 3d support, and just achieved glxgears recently.

This _might_ fix the crashing, we'll see;

1. Open up regedit

2. Go to HKEY_CURRENT_USER\Software\Wine\

3. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder.

4. Right-click on the wine folder and select [NEW] then [KEY]

5. Replace the text New Key #1 with Direct3D

6. Right-click in the right hand pane and select [NEW] then [String Value]

7. Replace New Value #1 with OffscreenRenderingMode

8. Double click anywhere on the line, a dialog box will open.

9. In the value field type backbuffer

Close, start Wow, profit? :)

---

### Post by tesseract1 on 2009-08-01
> **Doctor Debian said:**
> No, as the open source driver for your card does not yet have full 3d support, and just achieved glxgears recently.

This _might_ fix the crashing, we'll see;

1. Open up regedit

2. Go to HKEY_CURRENT_USER\Software\Wine\

3. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder.

4. Right-click on the wine folder and select [NEW] then [KEY]

5. Replace the text New Key #1 with Direct3D

6. Right-click in the right hand pane and select [NEW] then [String Value]

7. Replace New Value #1 with OffscreenRenderingMode

8. Double click anywhere on the line, a dialog box will open.

9. In the value field type backbuffer

Close, start Wow, profit? :)

Followed this and it didn't fix the text disappearing.  I'll have to mess around with it some more and ask around too.  I'm going to bed for the night. Thanks for your time Doc!

---

### Post by Doctor Debian on 2009-08-01
> **tesseract1 said:**
> Followed this and it didn't fix the text disappearing.  I'll have to mess around with it some more and ask around too.  I'm going to bed for the night. Thanks for your time Doc!

No problem, glad to help :D

---

