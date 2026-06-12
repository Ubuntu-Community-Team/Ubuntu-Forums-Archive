---
title: "Can only boot into safe graphics mode [cant install nivida driver onto 7.10]"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by mrdaniel on 2007-10-20
When I boot onto the ubuntu 7.10 CD, the menu pops up, if I select install ubuntu, some white texts is printed on the screen, then the ubuntu logo pops up, then it goes black forever. Now when I choose safe graphics mode on the boot up menu, then I get to the GUI ubuntu everything looks good. now I need to install the Nivida driver, so i go to the "Restricted Driver Manager" and check the little box next to the nividia driver, it downloads the proper software or driver then it asks me to restart the computer, i do so and then get back into the safe graphics mode and nothing changes everything is the exact same in the restricted driver manager, it still asks me to restart the computer after i check the box again, same thing over and over. The whole screen stays black, when i choose to install ubuntu without safe graphics mode after the ubuntu logo shows itself. I tryed all verisons and i try the alternate cd [NOT LIVECD] and the screen just stays black and flicker different colors. It screen goes black when you see the big "ubuntu" logo and the little organe loading bar going side to side, it stays black after that loading screen.

Here are my specs:

Microprocessor   	1.8 GHz AMD Turion™ 64 X2 Dual-Core Mobile Technology TL-56
Microprocessor Cache 	2 X 512KB L2 Cache
Memory 	2048MB DDR2 System Memory (2 Dimm)
Memory Max 	2048MB
Video Graphics 	NVIDIA GeForce Go 6150 (UMA)
Video Memory 	up to 128MB (shared)
Hard Drive 	120GB 5400RPM (SATA)
Multimedia Drive 	LightScribe SuperMulti 8X DVD±RW with Double Layer Support
Display 	17.0” WXGA+ High-Definition BrightView Widescreen Display (1440 x 900)
Fax/Modem 	High speed 56k modem
Network Card 	Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
Wireless Connectivity 	802.11b/g WLAN
HP Features 	HP Imprint finish & HP Pavilion WebCam with Integrated Microphone
Sound 	Altec Lansing
Keyboard 	Notebook keyboard with scroll bar and integrated numeric keypad

2 Quick Launch Buttons (HP Quick Play Menu and DVD buttons)
Pointing Device 	Touch Pad with On/Off button and dedicated vertical Scroll Up/Down pad
PC Card Slots 	

    * 1 ExpressCard/54 Slot (also supports ExpressCard/34)

External Ports 	

    * 5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards
    * 4 Universal Serial Bus (USB) 2.0
    * 2 Headphone out - 1 w/SPDIF Digital Audio & 1 stereo
    * 1 microphone-in
    * 1 VGA (15-pin)
    * 1 TV-Out (S-video)
    * 1 RJ-11 (modem)
    * 1 RJ -45 (LAN)
    * 1 notebook expansion port 3
    * 1 IEEE 1394 Firewire (4-pin)
    * 1 Consumer IR

Dimensions 	15.16" (L) x 11.65" (W) x 1.57" (H)
Weight 	7.8lbs
Security 	

    * Kensington® MicroSaver lock slot
    * Power-on password
    * Accepts 3rd party security lock devices

Power 	

    * 90W AC adapter
    * 8-cell Lithium-Ion Battery

---

### Post by froy02 on 2007-10-20
Go to synaptics package manager and install the Nvidia driver for your card. Choose the one for your card Nvidia-glx, Nvidia-glx-legacy or Nvidia-glx-new.  Do not try to install Nvidia-setting or Nvidia-xconfig.  One of them crashed my installation but I haven't had time to experiment which one.

By the way make sure you remove the ones you do not want use while installing the one you need.

---

### Post by mrdaniel on 2007-10-22
> **froy02 said:**
> Go to synaptics package manager and install the Nvidia driver for your card. Choose the one for your card Nvidia-glx, Nvidia-glx-legacy or Nvidia-glx-new.  Do not try to install Nvidia-setting or Nvidia-xconfig.  One of them crashed my installation but I haven't had time to experiment which one.

By the way make sure you remove the ones you do not want use while installing the one you need.

Should i do this in safe graphics mode? Will it ask me to reboot or do I start the  installation process right away? Where do i download the driver?

---

### Post by Endolith on 2007-10-22
I have a GeForce FX Go5200.  It worked perfectly in Fiesty, but when I upgraded, it stopped working and only does low-res mode.  I try to change it in the settings but it goes back to vesa when I open it again.

---

### Post by mrdaniel on 2007-10-22
I will try that tonight, did you have to do a alternate install or just a liveCD will work?

---

### Post by dabl on 2007-10-22
Or, you could download and install the Envy installer, and let it do the work for you:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

:guitar:

---

### Post by BoomShaka on 2007-10-22
Sorry, but from my understanding you said you where booting from the CD.
Meaning you didn't actually install the OS... as far as I am aware when you run Ubuntu from the CD changes you make are not written to a hard disk... therefore installing new drivers may work for that "session", but when you reboot you will simply be starting from scratch since the drivers you downloaded (and settings you set) were not saved.

Or am I mis-interpreting something here?

---

### Post by mrdaniel on 2007-10-22
> **BoomShaka said:**
> Sorry, but from my understanding you said you where booting from the CD.
Meaning you didn't actually install the OS... as far as I am aware when you run Ubuntu from the CD changes you make are not written to a hard disk... therefore installing new drivers may work for that "session", but when you reboot you will simply be starting from scratch since the drivers you downloaded (and settings you set) were not saved.

Or am I mis-interpreting something here?

No you are correct.

---

### Post by mrdaniel on 2007-10-22
> **dabl said:**
> Or, you could download and install the Envy installer, and let it do the work for you:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

:guitar:

Do I do this with a LiveCD? I having a hard time understanding how to install Envy. If I download the program "Envy" where do I put it, burn it to a CD maybe, or just download it while I an installing?

---

### Post by Endolith on 2007-10-22
> **Endolith said:**
> I have a GeForce FX Go5200.  It worked perfectly in Fiesty, but when I upgraded, it stopped working and only does low-res mode.  I try to change it in the settings but it goes back to vesa when I open it again.

I solved my own problem.  I simply wasn't running the latest kernel because the boot loader was on another partition.  As soon  as I used the latest kernel my display worked.  (Fonts are too small, though...)

Oh.  I also restored an old version of xorg.conf (stored at xorg.conf.1).  But the configurator program seems to be working along with it, too, and remembering the settings.

---

### Post by mrdaniel on 2007-10-22
> **Endolith said:**
> I solved my own problem.  I simply wasn't running the latest kernel because the boot loader was on another partition.  As soon  as I used the latest kernel my display worked.  (Fonts are too small, though...)

Oh.  I also restored an old version of xorg.conf (stored at xorg.conf.1).  But the configurator program seems to be working along with it, too, and remembering the settings.

Didn't work for me, I think all I need to do is to just install Envy, which I do not know how to do. Is there a complete tutorial for noobs? Possibly a video?

---

### Post by Endolith on 2007-10-22
> **mrdaniel said:**
> Didn't work for me, I think all I need to do is to just install Envy, which I do not know how to do. Is there a complete tutorial for noobs? Possibly a video?

I don't even know what Envy is.

---

### Post by BoomShaka on 2007-10-23
mrdaniel: boot into safe graphics mode and do the full install. Once that is done, boot into 7.10 and then download and install envy (or download the drivers yourself).
I had this same problem, once I had installed gutsy, I simply installed the latest drivers for my nvidia card.

I don't believe that installing Envy BEFORE the actual OS install will work.

---

### Post by mrdaniel on 2007-10-23
> **BoomShaka said:**
> mrdaniel: boot into safe graphics mode and do the full install. Once that is done, boot into 7.10 and then download and install envy (or download the drivers yourself).
I had this same problem, once I had installed gutsy, I simply installed the latest drivers for my nvidia card.

I don't believe that installing Envy BEFORE the actual OS install will work.

I can only install from safe graphics mode right? Because I installed the Gusty Non-LiveCD and when it installs and boots, the ubuntu logo pops up and disapars and the screen stays black forever. I never tryed to install from safe graphics mode, I will try tonight. Thanks. Let me know if there is anypoint in try to install it from safe graphics mode cause it does work when I install it from the alternate non-livecd. Thanks Again.

---

### Post by mrdaniel on 2007-10-29
What should I do?

---

### Post by Therion on 2007-10-29
**If You Have Gutsy Installed on Your Hard Drive:**

Boot your PC.
From the GRUB menu hit "Escape".
Select "**Recovery Mode**" (you'll wind up at a system prompt).
From the system prompt:
```
 nano /boot/grub/menu.lst
```
Scroll down to the bottom of the page using the arrow key, past all the # signs until you come to the first line that starts with Kernel.  This will be a long line of code that runs off the end of your display.  Use the arrow keys to scroll to the end of that line where you'll find where it says **-ro -splash -quiet**
Remove the word splash.
Ctrl+X to save, confirm the overwrite and reboot.

When you reboot you will NOT get a splash-screen but will go straight to your desktop where you should get prompted about installing the Restricted Driver for your video card.  Install it, and from there you should be good to go.



**If You Don't Yet Have Gutsy Installed on Your Hard Drive:**

Boot from the LiveCD.
At the splash-screen use F6.
Find the Kernel line as mentioned above and remove "splash".  It will the second line or so of code in this instance.
This will allow you to get to your desktop where you can do the full installation of Gutsy to your hard drive.
After it's installed to your hard drive, see the first set of instructions because you're going to have to RE-edit menu.lst once you're no longer booting from the LiveCD.

---

### Post by THEBIGEYE on 2007-10-29
i have the same problem but i have installed by network i downloaded the live cd but it wont boot i get an I/O error i have tried envy repos and binary from nvidias site still no joy have to run in safe mode all the time but my xorg shows i have more resolutions avallible

---

