---
title: "AMD/ATI Mobility 5470 HD and the hybrid graphics"
date: 2014-07-16
forum: Multimedia Software
---

### Post by patrick-kl on 2014-07-16
[COLOR=#000000][FONT=sans-serif]I've got a [/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]"HP G62-b25SG" notebook with hybrid graphics and my graphics hardware configuration looks like:
[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]**lspci -nnk | grep "VGA\|'Kern'\|3D\|Display" -A2**[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]```
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:143a]
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470] [1002:68e0] (rev ff)
    Kernel driver in use: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series] [1002:aa68] (rev ff)
```

[B]xrandr --prop
[/B]```
[COLOR=#000000]Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
[/COLOR]LVDS1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
    _MUTTER_PRESENTATION_OUTPUT: 0 
    EDID: 
        00ffffffffffff0006afec2200000000
        01130103802213780ac8959e57549226
        0f505400000001010101010101010101
        010101010101121b5642500026302018
        340058c1100000180000000f00000000
        00000000000000000020000000fe0041
        554f0a202020202020202020000000fe
        004231353658573032205632200a00c0
    BACKLIGHT: 10 
        range: (0, 10)
    Backlight: 10 
        range: (0, 10)
    scaling mode: Full aspect 
        supported: None, Full, Center, Full aspect
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
[COLOR=#000000]VIRTUAL1 disconnected (normal left inverted right x axis y axis)[/COLOR]
```

I've been trying for some time to activate my graphics card or in addition the switching between the two cards (but that last point is trival for me).
At the time, only the integrated Intel HD graphics chip is working.
I already tried to change in xorg.con the used card in the Screen1 section to Card1 (radeon oss driver), but after a reboot the gui doesn't response at all, so I had to go to the console (Ctrl + Alt + F1) and revert the config again. The proprietary driver doesn't work either, it doesn't detect my graphics hardware (I think it's not supported), after a reboot I got directly to the console (tty1).

Maybe you could help me to get my discrete AMD graphics card to work.

---

### Post by at_first_light on 2014-07-18
It sounds like you have an Intel integrated adapter + an ATI dedicated adapter? I'm not familiar with Intel graphics, but you said they are already working. Assuming your card is supported you will need install fglrx-updates using apt-get, and initialize it to get the ATI card working. I'm not sure if they can both be enabled at the same time like AMD + ATI graphics adapters can be, so attempting to might disable the Intel graphics.

**_Steps:_**
1. Install Drivers.
```

sudo apt-get install fglrx-updates

```

2. Initialize the adapter.
```

sudo aticonfig --initial

```

3. Reboot, and then open the Catalyst Control Center to change desired graphics settings for your ATI adapter.

**_Sources: _**
- [http://postbin.per.red/pages/article31/page.php](http://postbin.per.red/pages/article31/page.php)
- [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by QIII on 2014-07-18
Installing the fglrx driver will only make things worse.  Given that you have an HD 5xxx series and an Intel GPU, it is virtually assured that you have a muxed (multiplexed) arrangement which will NOT work with the fglrx driver.

Your best bet would be to use the default open source Radeon driver, which is installed when you install Ubuntu, and vga_switcheroo.  I'm on my cell phone right now and can't give you a link, but there is a page in either the community or official documentation that explains vga_switcheroo.

---

### Post by at_first_light on 2014-07-19
You may find this posting on AskUbuntu.com about systems with Intel & ATI graphics to be helpful as it has some good looking answers that even talk about how to switch back and forth between adapters. [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work)

---

### Post by QIII on 2014-07-19
Of note:  The OP in that AU thread has an HD 6xxxM ATI GPU.  Those who are complaining that the methods do not work properly have HD 5xxx cards.

Again:  It is nearly certain that an HD 5xxx ATI GPU in a hybrid machine is muxed.  Those methods will almost certainly *not* work because they will only work with muxless systems.

Following those instructions (some of which use deprecated commands, by the way) will more than likely cause the OP's machine to become unusable and require some work in recovery mode to correct the problems.

I have some expertise in this subject -- and have even written large portions of some of the URLs given by posters there.

patrick-kl:  It is my well-informed recommendation that you do not attempt to follow the instructions in that AU thread.  Instead, please see [this]("https://help.ubuntu.com/community/HybridGraphics").

---

