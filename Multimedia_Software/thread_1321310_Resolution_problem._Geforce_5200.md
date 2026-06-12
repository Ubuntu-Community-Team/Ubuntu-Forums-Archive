---
title: "Resolution problem. Geforce 5200"
date: 2009-11-09
forum: Multimedia Software
---

### Post by russellpoovey on 2009-11-09
I cannot get a resolution bigger than 800x600 and when I try to egit xorg.conf there is no option to add resolutions I have searched everywhere with no luck. If anyone has any ideas on how to help just tell me what info you need and I will post it. I desire a 1920x1200 resolution to got nicely on my 26in monitor. And the nvidia settings nor the native display settings detect my monitor. It is a new VGA cable. I just can't get it higher than 800x600. Running 9.10

---

### Post by RedSingularity on 2009-11-09
Post your xorg file.

---

### Post by russellpoovey on 2009-11-09
Section "Screen"
    Identifier    "Configured Screen Device"
    DefaultDepth    24
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
EndSection


thats it.

---

### Post by russellpoovey on 2009-11-09
Section "Screen"
    Identifier    "Configured Screen Device"
    DefaultDepth    24
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
EndSection



thats it.

---

### Post by RedSingularity on 2009-11-09
```
Add these lines to "screen" part--------------

Section "Screen"
              Identifier    "Configured Screen Device"
              DefaultDepth    24
              SubSection "Display"
                           Depth                      24
                           Modes                    "1920x1200"
EndSection
```

---

### Post by russellpoovey on 2009-11-10
Added and now Ubuntu isn't loading after a restart so I could restart my X.

---

### Post by RedSingularity on 2009-11-10
Are you loading to a text boot?

---

### Post by RedSingularity on 2009-11-10
If you are booting into a text prompt run this command to reconfigure your X server.

sudo dpkg-reconfigure -phigh xserver-xorg

When done reboot.

---

### Post by russellpoovey on 2009-11-10
Done. Any other suggestions? I have been trying things for a week now. Eyes are starting to only see giant pixelated objects. :)

---

### Post by gradinaruvasile on 2009-11-10
In a terminal type: 

sudo nvidia-xconfig
reboot

Maybe helps... It worked on 9.04. I am not sure about 9.10.

---

### Post by RedSingularity on 2009-11-10
Are you sure your monitor is capable of that resolution?

---

### Post by russellpoovey on 2009-11-10
yes... i run it in windows xp pro that high with no problem...

---

### Post by RedSingularity on 2009-11-10
And you do have the drivers correct?

---

### Post by russellpoovey on 2009-11-10
yes they are saying that they are completely up-to-date... 173.14.something. or something like that.

---

### Post by RedSingularity on 2009-11-10
Those are actually pretty old.  190.xx is the current stable.

---

### Post by russellpoovey on 2009-11-10
well i will try and load those from nvidia.com i tried that yesterday but it wouldnt install so i just figured "o well"

---

### Post by russellpoovey on 2009-11-10
it says that my driver versions 173.14.20 are the most up-to-date ones... are there any third party drivers you know of? i was unable to locate any.

---

### Post by RedSingularity on 2009-11-10
Here is how you can upgrade.

1)  Add this to your sources list.  (System>Admin>Software sorces>Third party sources)
[FONT=monospace]
[/FONT]deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main 

2)  Right click this key and "save link as" to your desktop or something easy.

[KEY]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x1DABDBB4CEC06767")

3)  Go to the authentication tab and "import key file".  Select your file you just saved.  

4)  Close the window and open a terminal.  Do "sudo apt-get update".

5)  Then "sudo apt-get install nvidia-glx-190"

6)  Restart

---

### Post by nikhilbhardwaj on 2009-11-10
> **RedSingularity said:**
> Those are actually pretty old.  190.xx is the current stable.

no no no
173.19.xx
are the correct drivers for his card
the new ones don't support te older cards

the drivers are up to date

---

### Post by gradinaruvasile on 2009-11-10
> **RedSingularity said:**
> Here is how you can upgrade.

1)  Add this to your sources list.  (System>Admin>Software sorces>Third party sources)
[FONT=monospace]
[/FONT]deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main 

2)  Right click this key and "save link as" to your desktop or something easy.

[KEY](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x1DABDBB4CEC06767)

3)  Go to the authentication tab and "import key file".  Select your file you just saved.  

4)  Close the window and open a terminal.  Do "sudo apt-get update".

5)  Then "sudo apt-get install nvidia-glx-190"

I dont think thats a good idea. 
The 5200 its an old card. The 173 series drivers are for that class. The newer drivers support newer cards and have some features that might not work on older cards.
Thats why Nvidia supports 3 generations of drivers (170,90 and 190).

---

### Post by RedSingularity on 2009-11-10
> **nikhilbhardwaj said:**
> no no no
173.19.xx
are the correct drivers for his card
the new ones don't support te older cards

the drivers are up to date


Really?  News to me :)

I should have double checked

---

### Post by nikhilbhardwaj on 2009-11-10
```

Section "Module"
    Disable "dri"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux           
    Load "extmod"                          
    Load "glx" # 3D layer                  
EndSection                                 

Section "Monitor"
    Identifier "monitor1"
    VendorName "Plug'n Play"
    ModelName "S/T 57/56E/V"
    HorizSync 30-55         
    VertRefresh 50-120      
                            
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync               
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630                                                 
                                                             
    # 768x576 @ 100 Hz, 61.6 kHz hsync                       
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616                                                 
EndSection                                                   

Section "Device"
    Identifier "device1"
    VendorName "nVidia Corporation"
    BoardName "NVIDIA GeForce FX series"
    Driver "nvidia"                     
    Option "DPMS"                       
    Option "DynamicTwinView" "false"    
    Option "AddARGBGLXVisuals"          
EndSection                              

Section "Screen"
    Identifier "screen1"
    Device "device1"    
    Monitor "monitor1"  
    DefaultColorDepth 24
                        
    Subsection "Display"
        Depth 8         
        Modes "1024x768" "800x600" "640x480" "480x360" "320x240"                                                          
    EndSubsection                                            
                                                             
    Subsection "Display"                                     
        Depth 16                                             
        Modes "1024x768" "800x600" "640x480" "480x360" "320x240"
    EndSubsection

    Subsection "Display"
        Depth 24
        Modes "1024x768" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    Screen "screen1"
EndSection

```

i have a similar graphics card geforce fx5500
so have a look at my configuration

just add the mode you want to the list

and after restarting X
you can use xrandr
or nvidia-settings to change your resolution

i repeat
donot install the 190.something series
it's not for your card

---

### Post by nikhilbhardwaj on 2009-11-10
> **RedSingularity said:**
> Really?  News to me :)

I should have double checked

you can try downloading the drivers from nvidia's website
specify the card as geforce 5 fx series 

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) 

the current version is 

**173.14.20 **

---

### Post by nikhilbhardwaj on 2009-11-10
**Version:**

**185.18.36 **











[URL="http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run&lang=us&type=GeForce"]
[/URL]



Supported products



[IMG]http://www.nvidia.com/content/EMEAI/_new_drivers_download/download_page/images/nav_tab_on.jpg[/IMG] 
[LIST]
[*]Fixed a bug that caused  kernel panics when starting X on some mobile GPUs.
[*]Fixed an interaction problem between VDPAU and PowerMizer when using VDPAU solely as a display mechanism, and not to decode video streams. The GPU performance level should now be raised, if required, in this scenario.
[*]Fixed VDPAU to avoid "display preemption" in some cases where a VdpOutputSurface is deleted while it is still active (either queued or visible) in a VdpPresentationQueue. In particular, this can occur in MPlayer when using the "-fs" option, and could completely prevent VDPAU from operating successfully, depending on the exact timing conditions.
[/LIST]
 
     Note that many Linux distributions provide their own  packages of the   NVIDIA Linux  Graphics Driver in the distribution's native package   management  format.  This may interact better with  the rest of your   distribution's framework, and you may want to use this rather than   NVIDIA's  official package.
 Also note  that SuSE users should read the SuSE NVIDIA Installer   [ HOWTO]("http://www.suse.de/%7Esndirsch/nvidia-installer-HOWTO.html") before downloading the driver.
 Installation  instructions: Once you have downloaded the driver,   change to the  directory containing the driver package and install the driver by  running, as root, sh  ./NVIDIA-Linux-x86-185.18.36-pkg1.run
 One of the  last installation steps will offer to update your   X  configuration file.  Either accept that  offer, edit your X   configuration  file manually so that the NVIDIA X driver will be used, or run nvidia-xconfig
 See the  [README]("http://us.download.nvidia.com/XFree86/Linux-x86/185.18.36/README/index.html") for more detailed instructions.
  
**GeForce 200 series:**
GTX 260, GTS 250, GTX 280, GTX 285, GTX 295

**GeForce 100 series:**
GT 150, GT 120, GT 140, G 100, GT 130

**GeForce 9 series:**
9600 GSO, 9500 GS, 9300 GE, 9300 GS, 9400, 9200, 9500 GT, 9300, 9300 SE, 9400 GT, 9600 GT, 9600 GS, 9800 GT, 9800 GX2, 9600 GSO 512, 9800 GTX/GTX+

**GeForce 9M series:**
9650M GT, 9600M GT, 9800M GT, 9800M GTS, 9650M GS, 9600M GS, 9200M GS, 9500M G, 9500M GS, 9800M GS, 9700M GT, 9300M G, 9800M GTX, 9300M GS, 9700M GTS

**GeForce 8 series:**
8800 Ultra, 8800 GTX, 8300, 8600 GTS, 8400 GS, 8800 GT, 8800 GTS 512, 8200, 8100 / nForce 720a, 8500 GT, 8800 GTS, 8300 GS, 8800 GS, 8600 GS, 8200 / nForce 730a, 8400 SE, 8400, 8600 GT

**GeForce 8M series:**
8400M GS, 8400M GT, 8600M GT, 8700M GT, 8800M GS, 8800M GTX, 8400M G

**GeForce 7 series:**
7025 / NVIDIA nForce 630a, 7300 LE, 7050 / NVIDIA nForce 610i, 7300 GT, 7350 LE, 7050 PV / NVIDIA nForce 630a, 7900 GT/GTO, 7900 GTX, 7150 / NVIDIA nForce 630i, 7950 GX2, 7900 GS, 7800 SLI, 7650 GS, 7050 / NVIDIA nForce 630i, 7100 GS, 7300 GS, 7600 GS, 7300 SE / 7200 GS, 7100 / NVIDIA nForce 630i, 7800 GS, 7800 GTX, 7100 / NVIDIA nForce 620i, 7600 LE, 7500 LE, 7950 GT, 7550 LE, 7600 GT

**GeForce Go 7 series:**
Go 7950 GTX, Go 7900 GTX, Go 7900 GS, Go 7800 GTX

**GeForce 6 series:**
6800, 6500, 6150 LE, 6600 LE, 6800 XT, 6200, 6800 GS, 6100 nForce 405, 6800 GS/XT, 6150LE / Quadro NVS 210S, 6100, 6150, 6200 LE, 6200 A-LE, 6600 VE, 6200 TurboCache, 6600 GT, 6100 nForce 400, 6800 GT, 6150SE nForce 430, 6250, 6610 XL, 6200SE TurboCache, 6800 Ultra, 6800 XE, 6800 LE, 6600, 6700 XL, 6100 nForce 420

**Quadro FX series:**
FX 3800, FX 570, FX 370, FX 5500, FX 4500 X2, FX 550, FX 580, FX 1800, FX 1700, FX 1500, FX 3700, FX 4600, FX 5600, FX 3450, FX 1400, FX 540, FX 4700 X2, CX, FX 4800, FX 4000, FX 560, FX 370 Low Profile, FX 350, FX 4500, FX 3500, FX 3400/4400, FX 5800, FX 380

**Quadro FX Notebook series:**
FX 1700M, FX 1600M, FX 3600M, FX 570M, FX 2700M, FX 370M, FX 360M

**Quadro NVS series:**
NVS 450, NVS 295, NVS 290, NVS 210, NVS 420, NVS 280, NVS 285, NVS 440

**Quadro Plex series:**
D Series, Model IV, Model II

**Quadro G-Sync series:**
G-Sync II, G-Sync I

**Quadro SDI series:**
Quadro SDI

**ION series:**
ION

**GPU Computing Processor series:**
Tesla C1060

---

### Post by russellpoovey on 2009-11-10
I'm sorry but I do not have any of that code... No Modes to add into. so i would not know where to start to add nor where to place it in my code.

---

### Post by Cool G5 on 2009-11-10
Maybe [this]("http://sathyasays.com/2009/11/10/fix-for-ubuntu-and-other-suitable-os-hanging-during-boot-with-nvidia-geforce-fx-5200-and-other-suitable-cards/") can help.

---

### Post by RedSingularity on 2009-11-10
> **Cool G5 said:**
> Maybe [this]("http://sathyasays.com/2009/11/10/fix-for-ubuntu-and-other-suitable-os-hanging-during-boot-with-nvidia-geforce-fx-5200-and-other-suitable-cards/") can help.


I dont believe he was having a problem with it freezing up though.

---

### Post by nikhilbhardwaj on 2009-11-10
unless you have some exotic hardware

nvidia-xconfig should generate a config file in that format

is nvidia-xconfig installed

it has been mentioned earlier
you should try that again

otherwise backup your xorg.conf file
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bakup

and then reconfigure your x server
so that you can atleast get X to start

---

### Post by russellpoovey on 2009-11-10
> **nikhilbhardwaj said:**
> unless you have some exotic hardware

nvidia-xconfig should generate a config file in that format

is nvidia-xconfig installed

it has been mentioned earlier
you should try that again

otherwise backup your xorg.conf file
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bakup

and then reconfigure your x server
so that you can atleast get X to start

yes nvidia-xconfig is installed. and i posted earlier what all it generates inside my xorg.conf file... thats it. those 6 or so lines of code... nothing else.

---

### Post by nikhilbhardwaj on 2009-11-10
> **russellpoovey said:**
> yes nvidia-xconfig is installed. and i posted earlier what all it generates inside my xorg.conf file... thats it. those 6 or so lines of code... nothing else.

in that case try to copy my xorg.conf
its not the best way but it may just work out
backup your xorg.conf
and replace it with the on i've posted

let us know if that helps

---

### Post by russellpoovey on 2009-11-10
> **nikhilbhardwaj said:**
> unless you have some exotic hardware

nvidia-xconfig should generate a config file in that format

is nvidia-xconfig installed

it has been mentioned earlier
you should try that again

otherwise backup your xorg.conf file
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bakup

and then reconfigure your x server
so that you can atleast get X to start


but just incase i did it incorrectly tell me how... 

i was under root
and typed nvidia-xconfig. like it said. when i first loaded the nvidia program and got this error "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

---

### Post by nikhilbhardwaj on 2009-11-10
> **russellpoovey said:**
> but just incase i did it incorrectly tell me how... 

i was under root
and typed nvidia-xconfig. like it said. when i first loaded the nvidia program and got this error "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

how did you get under root??
ubuntu has the root account disabled by default

did you start in the recovery mode or something??

---

### Post by russellpoovey on 2009-11-10
> **nikhilbhardwaj said:**
> how did you get under root??
ubuntu has the root account disabled by default

did you start in the recovery mode or something??


in terminal just typed 

sudo bash

then

cd /etc/X11

then

sudo gedit xorg.conf 

to edit my file.

---

### Post by russellpoovey on 2009-11-10
> **nikhilbhardwaj said:**
> in that case try to copy my xorg.conf
its not the best way but it may just work out
backup your xorg.conf
and replace it with the on i've posted

let us know if that helps

after i copied your code into mine... it worked... im now viewing at 1024x768!!!! which is better than nothing... i tried adding 1920x1200 into the modes... and restarting but that didnt add that option to my resolutions... any ideas?

---

### Post by nikhilbhardwaj on 2009-11-10
sorry
had to go

if you add 1920x1200 before 1024x768 in all the modes
then on restarting the X sever
the changes should take place

otherwise after adding
start 
sudo nvidia-settings
see if the resolution is shown
if it is merge the settings into xorg.conf

also you could try
xrandr -s 1920x1200

---

### Post by fatalbert on 2009-11-10
> **russellpoovey said:**
> after i copied your code into mine... it worked... im now viewing at 1024x768!!!! which is better than nothing... i tried adding 1920x1200 into the modes... and restarting but that didnt add that option to my resolutions... any ideas?


I copied the code as well and it worked!! I was ready to give up hope. This was done on Nvidia 6150 le - 9.10 karmic. Thank you!!!

---

