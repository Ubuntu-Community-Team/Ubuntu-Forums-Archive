---
title: "NVidia Drivers issues on Ubuntu 9.04 wont work..."
date: 2009-08-04
forum: Multimedia Software
---

### Post by Valek on 2009-08-04
I HAVE THE SAME PROBLEM, AND AM STARTING TO GIVE UP HOPE... Ive TRIED EVERYTHING, I VE READ LIKE 100 WEBPAGES, FORUMS, TILL I SAW THIS POST, AND PISSES ME OFF MORE, JUST TO READ, THAT OTHER PEOPLE HAVE THE SAME PROBLEM.

ILL JUST STATE THE INCONVENIENCES I FOUND:
[SIZE=2]
Just when I installed UBUNTU 9.04 and updated, when I restarted, it just appeared a freakin small windows (just after the grub, etc) that stated:
[/SIZE]

[LIST]
[*][SIZE=2][COLOR=Blue]Failed to initialize the Nvidia graphics device PCI 1:0:0[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Blue]Please see the common problems section in the READ me for...[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Blue]Failed to initialice the Nvidia graphics device [/COLOR][/SIZE]
[*][SIZE=2][COLOR=Blue]EE server found, but none have a usable configuration[/COLOR][/SIZE]
[/LIST]

Now after this appears it keeps on coming more NEWS! ....
Then i can see this next options:


[LIST]
[*]  [SIZE=2][COLOR=Blue]Run ubuntu in low graphics mode[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Blue]  Reconfigure Graphics[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Blue]  Troubleshott the error[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Blue]  Exti to console[/COLOR][/SIZE]
[/LIST]

No matter what option i choose i have to restart, except for the last one "Exist to Console" that jumps me to a black login scree, that I do not know how to get out, I would appeared to be a big terminal black screen. After this I pressed shut down button, to restart my PC. 

HP Pavilion Media Center m8120n TVTuner
WIn Vista Home Premium (in the other hard drive)
3G RAM
QUAD Core 
[COLOR=Blue]**128  MB GFOrce 7350 LE TurboCache Card**
[/COLOR]
Know after I restart, now I finally get Ubuntu to appear, but IF want to use [COLOR=Blue]**EXTRA**[/COLOR] **[COLOR=Blue]VISUAL EFFECTS[/COLOR]** it would tell me:  Desktop Efects COULD NOT BE ENABLED.

THIS IS MY MAJOR PROBLEM I COULD NOT USE ALL THE COOL STUFF ABOUT UBUNTU @%#$%$. 

[FONT=Tahoma][SIZE=2][COLOR=Blue]To solve this problem is that maybe I dont have the correct drivers... but Ive tried em all!!
If i go to system--> administration ---> hardware drives
I can see:
NVIDIA ACCELERATED GRAPHICS DRIVER v180, v96, v173. It would say that the v180 is the recommended, but down that window, tells me am using another version of this driver. Now if i activate this driver, tells me to restart. I restart and i still get the same @#$$@! problem; about the choices of runing in lower graphical mode, etc. [/COLOR][/SIZE][/FONT]

Now another anomaly I see is that when I try to go to the famous X-SERVER SETTINGS it shows a message: 
"[SIZE=2][COLOR=Blue]YOU DO NOT APPEAR TO BE USING THE NVIDIA X DRIVER. PLEASE EDIT YOUR X CONFIGURATION FILE (just run 'nvidia-xconfig' as root, and restart X server. [/COLOR][/SIZE]

After i see this i got to terminal and type as sudo (root) 
$ sudo nvidia-xconfig 


[IMG]http://ubuntuforums.org/home/rocknrolla/Screenshot.png[/IMG]

If the image cannot be seen, well it shows:

[SIZE=2][COLOR=Red]Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
[/COLOR][/SIZE]

[SIZE=2]Now i guess this xorg.conf fiel is important. From what i read some ppl say that i have to edit some parts of it (nv for nvidia and other stuff), or some file i have to edit
Then i go again to the terminal and now i type:[/SIZE]

  sudo nano /etc/X11/xorg.con

[SIZE=2]So i can see this file, as the image shows next:[/SIZE]
[IMG]http://ubuntuforums.org/home/rocknrolla/Screenshot2.png[/IMG]
[IMG]http://ubuntuforums.org/home/rocknrolla/screenshot3.png[/IMG]

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



[SIZE=3][COLOR=Blue]KNOW I DONT UNDERSTAND ALL THAT..... so....

COULD SOMEONE EXPLAIN ME WHAT TO DO SO I CAN RESOLVE THIS PROBLEM!!!
I WANNA SEE THE CUBE!!!! 

PLEASE HELP!!!!!!!!!!!!!!!!!
[/COLOR][/SIZE]
PD: Cause am losing on hope...to fix this...

---

### Post by dal on 2009-08-04
Had the same problem, apparently on my machine it was caused by me attempting to install a new nvidia driver package from nvidia.com (the .run file) without first uninstalling the ubuntu-managed nvidia packages. If this isn't relevant to your situation, I'd suggest just trying to completely uninstall the nvidia drivers and then reinstall them. If it is, you'll probably want to look at files like /usr/lib/libGL.so.*, /usr/lib/libGLcore.so.*, /usr/lib/libGLU.so.* etc and make sure those symlinks all point towards the same nvidia driver version (in my case I had some pointing to libGL.so.180.60, libGLU.so.185.14 etc).

---

### Post by Trophy on 2009-08-04
Do you have another slot to plug your video card into?

I am a total noob but check this

   [FONT=&quot]check the following file:[/FONT]
  [FONT=&quot]            Sudo pico [/FONT][FONT=&quot]/var/log/Xorg.0.log[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Look for entries like the following:
(EE) No devices detected.[/FONT]

If they are there then

   [FONT=&quot]Get information on the hardware on your system (make a note of this)[/FONT]
  [FONT=&quot]sudo lshw -businfo | grep -i display[/FONT]
  
   [FONT=&quot]you need to explicitly add the PCI bus ID to your /etc/X11/xorg.conf file:

sudo pico /etc/X11/xorg.conf. 
 
 [/FONT]
  [FONT=&quot]Find the line that says Section "Device", Insert a new line that says [/FONT]
  [FONT=&quot]BusID "PCIxxxx", where xxxx is the PCI address displayed by lshw command.

Save the file. If you had to restart into recovery mode, type reboot[/FONT]

---

### Post by dal on 2009-08-04
"Failed to initialize the Nvidia graphics device PCI 1:0:0"

If the Xorg log has a PCI address listed for it (1:0:0), then the card is being detected, the problem is between it and X, in the driver.

I'd wager either that the OP did the same stupid thing I did in trying to install a nvidia.com .run driver file over the top of the existing .deb install, and ended up with symlinks pointing to files from either driver version - or that the distro upgrade process tried to install another version of the nvidia driver over the top of the old one.

Using the --list option on a nvidia driver package reveals this list of pertinent files:

./usr/lib/libGLcore.so.185.18.14                                        
./usr/lib/libGL.so.185.18.14
./usr/lib/libnvidia-tls.so.185.18.14                                    
./usr/lib/tls/libnvidia-tls.so.185.18.14                                
./usr/lib/libnvidia-cfg.so.185.18.14                                    
./usr/lib/libcuda.so.185.18.14                                          
./usr/lib/libvdpau.so.185.18.14                                         
./usr/lib/libvdpau_nvidia.so.185.18.14                                  
./usr/lib/libvdpau_trace.so.185.18.14                                   
./usr/X11R6/lib/modules/extensions/libglx.so.185.18.14                  
./usr/X11R6/lib/modules/libnvidia-wfb.so.185.18.14                      
./usr/X11R6/lib/libXvMCNVIDIA.so.185.18.14   

These files aren't used directly, rather the system accesses similarly named symbolic links - for instance instead of using the file libGL.so.185.18.14, the system uses file libGL.so.1 which is a symlink pointing to libGL.so.185.18.14 - but if all the other so.1 files point towards their 185.18.14 equivalents, but libGL.so.1 points to say libGL.so.190.60.11 you're gonna have problems pretty similar to what the OP has run into. Checking that all the symlinks for the files listed above point to the same version files and that version is the same as the nvidia driver version reported by nvidia-settings in X (which should still run even under low graphics mode) would hopefully fix his issue.

Having said that I've often found that the more exclamation marks used in someone's post, the less chance there is of them following it up, so we may never know <shrug>

---

### Post by Valek on 2009-08-05
If the Xorg log has a PCI address listed for it (1:0:0), then the card is being detected, the problem is between it and X, in the driver.

I'd wager either that the OP did the same stupid thing I did in trying to install a nvidia.com .run driver file over the top of the existing .deb install, and ended up with symlinks pointing to files from either driver version - or that the distro upgrade process tried to install another version of the nvidia driver over the top of the old one.

Using the --list option on a nvidia driver package reveals this list of pertinent files:

./usr/lib/libGLcore.so.185.18.14                                        
./usr/lib/libGL.so.185.18.14
./usr/lib/libnvidia-tls.so.185.18.14                                    
./usr/lib/tls/libnvidia-tls.so.185.18.14                                
./usr/lib/libnvidia-cfg.so.185.18.14                                    
./usr/lib/libcuda.so.185.18.14                                          
./usr/lib/libvdpau.so.185.18.14                                         
./usr/lib/libvdpau_nvidia.so.185.18.14                                  
./usr/lib/libvdpau_trace.so.185.18.14                                   
./usr/X11R6/lib/modules/extensions/libglx.so.185.18.14                  
./usr/X11R6/lib/modules/libnvidia-wfb.so.185.18.14                      
./usr/X11R6/lib/libXvMCNVIDIA.so.185.18.14   

These files aren't used directly, rather the system accesses similarly named symbolic links - for instance instead of using the file libGL.so.185.18.14, the system uses file libGL.so.1 which is a symlink pointing to libGL.so.185.18.14 - but if all the other so.1 files point towards their 185.18.14 equivalents, but libGL.so.1 points to say libGL.so.190.60.11 you're gonna have problems pretty similar to what the OP has run into. Checking that all the symlinks for the files listed above point to the same version files and that version is the same as the nvidia driver version reported by nvidia-settings in X (which should still run even under low graphics mode) would hopefully fix his issue.

Having said that I've often found that the more exclamation marks used in someone's post, the less chance there is of them following it up, so we may never know <shrug>


I[SIZE=2][COLOR=Blue]'VE CHECKED IF I HAVE THOSE FILES... BUT SOME ARE MISSING?? IS THAT A PROBLEM???
I SEARCHED FOR ./usr/lib/libnvidia-cfg.so.180.44 (in my case am using that version of 180.44) Somehow i cant upgrade to 185. Ive downloaded and when i try to install, it tells me that 1st i have to exit X-server or the X-setting... I do not know how to do that...last time i tried, it logged me out to the black screen "login". 

BACK TO THE PROBLEM I ALSO CANT FIND THE NEXT FILES U POSTED I SUPPOSED TO HAVE POINTING TO THE DRIVER AM USING... :

./usr/X11R6/lib/modules/extensions/libglx.so.185.18.14                  
 ./usr/X11R6/lib/modules/libnvidia-wfb.so.185.18.14                      
 ./usr/X11R6/lib/libXvMCNVIDIA.so.185.18.14   

Apparently I do not have that directory, when I get to the X11R6, it only appears 
/usr/X11R6/bin. Inside this folder /bin theres a bunch of files: executables, Link to Perl Script and shell script files. 

WHAT DO I DO NEXT??
[/COLOR][/SIZE]

---

### Post by Valek on 2009-08-05
**e: NVidia Drivers issues on Ubuntu 9.04 wont work...** 			 			 			 		   		 		 		Had the same problem, apparently on my machine it was caused by me attempting to install a new nvidia driver package from nvidia.com (the .run file) without first uninstalling the ubuntu-managed nvidia packages. If this isn't relevant to your situation, I'd suggest just trying to completely uninstall the nvidia drivers and then reinstall them. If it is, you'll probably want to look at files like /usr/lib/libGL.so.*, /usr/lib/libGLcore.so.*, /usr/lib/libGLU.so.* etc and make sure those symlinks all point towards the same nvidia driver version (in my case I had some pointing to libGL.so.180.60, libGLU.so.185.14 etc).

DAL:
About checking those 3 files, am missing /usr/lib/libGLU.so it appears to be libGLU.so.1 that points to or its target link is: libGLU.so.1.3.070300. 

The other 2 files do point to my present driver (i think thats the driver am using.. i do not know also how to check which  drivers am using, i downloaded some utility called sysinfo, to check that)
v180.44

---

### Post by Valek on 2009-08-05
What do u mean by entries. I just found a line similar to that:
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

---

### Post by dal on 2009-08-06
Ah, my bad, the 180 series differs from the 185 one on those three files.

libnvidia-wfb isn't one you have to worry about, it appears to have been added in 185 and isn't present in 180.

libXvMCnvidia is in /usr/lib for the 180 series rather than /usr/X11R6/whatever

libglx however is in /usr/lib/xorg/modules/extensions (although my system also has a symlink in /usr/lib/xorg/modules/ )

as far as .so and .so.1 goes, most of the links should end in .so.1, on my system the only ones that end in .so are the libvdpau* files (although libvdpau has a .so symlink as well, which points to the so.1 file, which then points to the actual .180.60 file).

libGLU.so.1 pointing to 1.3.070300 is what is on my system as well, so that should be fine.

hadn't heard of sysinfo before but it seems to work ok on my system, reports the right nvidia driver version. whether it operates with a non-functioning nvidia driver installed I don't know though.

If you can't find one of these files that are pointing to the wrong version, or sysinfo tells you you have a version other than 180.44 installed your best bet would be to remove the drivers entirely and reinstall them. To do this, type "apt-get remove --purge nvidia-180-kernel-source nvidia-180-libvdpau nvidia-180-modaliases nvidia-common nvidia-glx-180 nvidia-settings" at a commandline, then the same thing again but with no --purge and with remove replaced by install. You may need to close down X and log in at the black screen before doing this.

If you want to install the drivers you downloaded from the nvidia site (I REALLY don't recommend this at it means each time your kernel is upgraded you get dropped to the black screen commandline login and have to reinstall the driver again before being able to use X again), do the same thing up to the apt-get remove command, but then type "dkms remove nvidia". After this find the NVIDIA-whatever.run driver file you downloaded from the site and type sudo sh /path/to/location/NVIDIA-driverversionnumber.run (once you've reached the NVIDIA bit you can press tab and it should fill the rest in for you). I.e. if you saved it to your desktop type sudo sh /home/yourname/Desktop/NVIDIA-etc. ***BUT*** I really don't recommend this as it means everytime a new kernel version is available for your system and you upgrade you'll have to repeat the sudo sh NVIDIA step again, and then you'd have to either reboot or type sudo telinit 1 and choose "resume" from the menu it shows you.

---

### Post by dal on 2009-08-06
As far as the Xorg.log entries, I don't think that applies to your case. Trophy was thinking maybe X was not able to see the video card at all, which would result in that error message he mentioned ((EE) No devices detected) - but I think the fact that you get the error message "Failed to initialize the Nvidia graphics device PCI 1:0:0" and "EE server found, but none have a usable configuration" preclude that possibility - as far as I can tell X can see the graphics card and knows it's PCI address, but the driver isn't working :(

---

