---
title: "Display adjustment, brightness, FX5200 dual head"
date: 2010-01-23
forum: Mythbuntu
---

### Post by extra300 on 2010-01-23
[FONT=Arial]Hi[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]Im having difficulty adjusting brightness and contrast on my dual head display's projector output. The video card is an fx5200, with an LCD monitor connected to its VGA output, and a projector connected to its DVI output. It is running the restricted Nvidia driver (173x I think it is- whatever is current for the 5200). The system runs well in all respects except for low brightness in video display; the menus are fine. [/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]When I configure X Server as TwinView, I get 2 separate screens (0/1) in the nvidia control panel. With that, I can adjust the brightness of either/both displays using the Nvidia control sliders. However, I am not able to get MythTV to see the second (projector) screen. It seems in order to have that happen, I have to enable Xinerama. When that is enabled, I no longer have independent control of the 2 displays, and the Nvidia control panel will only impact the LCD display.[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]I have disabled Composite in the xorg.conf file. Doing that allows the ‘F’ key within the Mythtv player to display the Brightness and Contrast controls on the projector’s screen. However, modifying these settings has no impact on the display. Im unclear as to why this fails.[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]Am I missing something here? Do I have to convolute things such that the projector is the primary display in TwinView? I would prefer to retain the LCD as the primary interface to the PC. Is there a way to cause Myth to load/display by default on the projector output, such that if I disable Xinerama I have hardware-level control over brightness/contrast?[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]I was not able to find any reference to a native player control that would allow me to adjust these 2 parameters- which seems strange; VLC has it.[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]Any help is appreciated-[/FONT]
[FONT=Arial]Regards[/FONT]

---

