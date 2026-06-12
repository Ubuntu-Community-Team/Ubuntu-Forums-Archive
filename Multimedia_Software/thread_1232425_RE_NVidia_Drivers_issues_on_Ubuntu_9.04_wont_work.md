---
title: "RE: NVidia Drivers issues on Ubuntu 9.04 wont work"
date: 2009-08-05
forum: Multimedia Software
---

### Post by Valek on 2009-08-05
**Re: NVidia Drivers issues on Ubuntu 9.04 wont work...** 			
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

WHAT DO I DO NEXT??[/COLOR][/SIZE]

---

