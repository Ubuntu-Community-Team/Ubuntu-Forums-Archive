---
title: "Screen size adjustment Nvidia 6200FX"
date: 2008-09-10
forum: Mythbuntu
---

### Post by Ronno6 on 2008-09-10
How do I fine tune the display image size on the Mythbuntu 8.04.1 desktop? My card is Nvidia 6200FX AGP, set to 1280 X 720, with the Mythbuntu settings manager set to DEFAULT. I am connected to an Akai LCT32Z5TAP 32" LCD TV via component inputs. Resolution of the TV is 1280 X 720 in the component input mode. 
Problem is that desktop images extend off the screen, both horizontally and vertically. If this is also apparent in Mythbuntu TV display I can't say for sure, but, as the situation exists when Mythbuntu is not running, I believe it to be either a video card adjustment or an Ubuntu adjustment. I'm sure it is a simple fix, I just don't know which one.
Thanks in advance,

---

### Post by SiHa on 2008-09-10
Hi Ronno,

Do you have nvidia-settings installed? ```
sudo apt-get install nvidia-setings
```

There should be a slider in one of the menus to adjust the overscan. This will effect all output to the TV. This is only enabled for analogue outputs, so I think it'll be OK for the component, but not sure as I've only used it with composite / S-Video.

Also, see my post here: [http://ubuntuforums.org/showthread.php?t=915367](http://ubuntuforums.org/showthread.php?t=915367) for details of the MythTV screen setup wizard. This is only for Myth though, you will still lose the edges of the normal desktop.

---

### Post by Ronno6 on 2008-09-10
Yes, the Nvidia settings program is installed. That's where the 1280 X 760 setting is located. The settings for video in Mythbuntu are set at "Default". The only sliders I see in Mythbuntu ate for RGB, and the Nvidia settings have sliders for "Antialiasing" and"Anisotropic" override settings. I'll have to research that. But I have not been able to locate overscan settings except in Mythbuntu backend setup (or frontend, I can't remember which.)

---

### Post by SiHa on 2008-09-10
Sorry. Perhaps the 6x series don't support it. I've got a 7200, and that has overscan options, but they're not there on the 5200. I'd assumed that it was becuase one's driving an analogue (composite) and the other digital (DVI) output. I guess the 5x & 6x chipsets don't have this feature.
In Mythfrontend, go to (From memory) Setup -> TV Playback -> Screen Setup Wizard. That should take you to a screen where you can drag the corners into the visible area. Once you've done that select Menu -> Save and Exit.

---

### Post by Ronno6 on 2008-09-10
That adjusted the image when Mythbuntu frontend is open, but did not affect the desktop when the frontend is closed. 
Not there yet.

---

### Post by SiHa on 2008-09-10
That's right it's Myth only. I only use my frontend for MythTV, so just put up with the lost bits. I just wave the mouse up to the top left corner until the program opens.

For the desktop, if you can't resolve the issue, you could always go to settings > Workspaces and Margins, and set no-go areas for new windows. I think the top panel can be resized and moved as well.

---

### Post by Ronno6 on 2008-09-10
I can resize the task bar, but cannot seem to move it. 
When I installed Mythbuntu I selected the TV out option, and am using the YPbPr outputs. Does this have any relevance ? Does Mythbuntu/Ubuntu recognize devices connected to the YPbPr outputs the same way they would recognize monitors connected to VGA ??

I attempted to adjust the pan settings but could not seem to get the revised setting to take effect.Once again, Nvidia settings show 1280X720, which is listed as the native resolution of my TV when using YPbPr inputs.

The TV does not have any adjustment for size like you would see in a monitor.

---

### Post by SiHa on 2008-09-11
I think The PC will detect the TV using component (It does on mine, using composite anyhow), but only that it it connected. It won't be able to get the EDID info though.
Although 1280x720 is the native resolution for your TV, that is for a digital input, you are driving via an analogue input, so 'resolution' is irrelevant, really. The TV will always overscan - scale up the input slightly so that the ragged edges are off the screen.
IMHO, I think this is probably something you might have to live with, unless you can find out how to get into the service menu for your TV and switch off the overscan.

---

### Post by Ronno6 on 2008-09-11
Ahhhhhhhhhh. Well, thanks for the clear explanation. At least now I understand the problem. As TV functions are the main goals of this setup, maybe I'll have to live with it as you say. Unless anybody comes up with a solution...................

Thank you again.

---

