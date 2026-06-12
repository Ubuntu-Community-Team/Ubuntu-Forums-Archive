---
title: "NVIDIA driver suddenly started causing black screen from GDM"
date: 2008-07-24
forum: Multimedia Software
---

### Post by remu on 2008-07-24
Hello Everyone,

I've been using envyng-gtk for a while now to install the drivers for my nvidia card. It was working fine and everything, compiz worked, games worked and everything. However, recently after a boot, I was greeted with a black screen and the sound that plays when the GDM gets displayed. But the screen was all black. I switched to a console (which I could see) and ran envyng in terminal mode, and re-installed the nvidia driver and then restarted my laptop. 

After the restart, I encountered the same problem. So I went back into the terminal and un-installed the nvidia driver through envyng, restarted, and the GDM showed up perfectly with the vesa drivers. I was able to log in and everything. Then using envyng-gtk I installed the latest nvidia drivers again, rebooted, same problem. So I un-installed it once more, and logged in with the vesa drivers, from which I'm currently typing this post.

I normally have compiz turned off, don't know if that would make a difference or not. Also, there hasn't been an update of the driver since it was working fine (like an hour ago) and now.

Any help would be greatly appreciated, sorry for being a little long winded.

---

### Post by NT4usB on 2008-07-24
Did you grab the latest Envy? I've been bit when a kernel upgrade jacks nvidia and I ran the installer I had. Alberto updates these all the time so might check for a new one.
[http://albertomilone.com/envyngfaq.html](http://albertomilone.com/envyngfaq.html)

---

### Post by remu on 2008-07-24
I am running envyng 1.1.1, I believe thats the latest.

---

### Post by tseliot on 2008-07-25
post the output of this command:
sudo aptitude search linux

---

### Post by remu on 2008-07-25
Here you go:

```
v   base-config-skolelinux          -                                           
v   cfengine-skolelinux             -                                           
p   circuslinux                     - The clowns are trying to pop balloons to s
p   circuslinux-data                - data files for circuslinux                
p   doc-linux-de                    - Linux HOWTOs in German                    
p   doc-linux-fr-html               - Linux docs in French: HOWTOs, MetaFAQs in 
p   doc-linux-fr-text               - Linux docs in French: HOWTOs, MetaFAQs in 
p   doc-linux-hr                    - Documentation in Croatian / dokumentacija 
p   doc-linux-html                  - Linux HOWTOs and FAQs in HTML format      
p   doc-linux-html-pt               - Linux HOWTOs in Portuguese (html format). 
p   doc-linux-it                    - Linux HOWTOs in Italian - HTML version    
p   doc-linux-it-text               - Linux HOWTOs in Italian - ASCII version   
p   doc-linux-ja-html               - Linux HOWTOs and FAQs in Japanese (HTML fo
p   doc-linux-ja-text               - Linux HOWTOs and FAQs in Japanese (TEXT fo
p   doc-linux-nl-html               - Dutch Linux HOWTOs, mini-HOWTOs, and FAQs 
p   doc-linux-nl-text               - Dutch Linux HOWTOs, mini-HOWTOs, and FAQs 
p   doc-linux-nonfree-html          - Linux HOWTOs in HTML format (non-free)    
p   doc-linux-nonfree-text          - Linux HOWTOs in ASCII format (non-free)   
p   doc-linux-pl                    - Linux docs in Polish: HOWTO - ascii versio
p   doc-linux-pl-html               - Linux docs in Polish: HOWTO - html version
p   doc-linux-text                  - Linux HOWTOs and FAQs in ASCII format     
p   doc-linux-text-pt               - Linux HOWTOs in Portuguese (text format). 
p   focalinux-html                  - A full GNU/Linux Portuguese guide (html fo
p   focalinux-text                  - A full GNU/Linux Portuguese guide (text fo
p   fwbuilder-linux                 - Firewall Builder policy compiler(s) for Li
p   grub-linuxbios                  - GRand Unified Bootloader, version 2 (Linux
p   lcd4linux                       - Grabs information and displays it on an ex
p   libaltlinuxhyph-dev             - ALTLinux hyphenation library development f
p   libcorelinux-dev                - Foundation Classes, Design Patterns, IPC a
p   libcorelinux-doc                - Foundation Classes, Design Patterns, IPC a
p   libcorelinux-examples           - Foundation Classes, Design Patterns, IPC a
p   libcorelinuxc2a                 - Foundation Classes, Design Patterns, IPC a
p   liblinux-inotify2-perl          - scalable directory/file change notificatio
p   liblinux-kernelsort-perl        - Perl module for sorting Linux Kernel versi
p   liblinux-lvm-perl               - Perl extension for accessing Logical Volum
v   libselinux-dev                  -                                           
i   libselinux1                     - SELinux policy enforcement, run-time libra
p   libselinux1-dbg                 - SELinux policy enforcement, run-time debug
p   libselinux1-dev                 - SELinux policy enforcement, development fi
p   linux                           - Generic complete Linux kernel.            
p   linux-amd64-generic             - Upgrade dummy package. Can be removed     
p   linux-amd64-k8                  - Upgrade dummy package. Can be removed     
p   linux-amd64-server              - Upgrade dummy package. Can be removed     
p   linux-amd64-xeon                - Upgrade dummy package. Can be removed     
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-2.6.24- - Ubuntu supplied Linux modules for version 
p   linux-backports-modules-hardy   - Generic Linux backported drivers.         
p   linux-backports-modules-hardy-g - Backported drivers for generic kernel imag
p   linux-backports-modules-hardy-o - Backported drivers for openvz kernel image
p   linux-backports-modules-hardy-r - Backported drivers for rt kernel image    
p   linux-backports-modules-hardy-s - Backported drivers for server kernel image
p   linux-backports-modules-hardy-x - Backported drivers for xen kernel image   
v   linux-boot-loader               -                                           
v   linux-debug                     -                                           
p   linux-doc                       - Linux kernel documentation                
v   linux-doc-2.6                   -                                           
p   linux-doc-2.6.24                - Linux kernel specific documentation for ve
i   linux-generic                   - Complete Generic Linux kernel             
v   linux-gnu                       -                                           
v   linux-headers                   -                                           
v   linux-headers-2.6               -                                           
p   linux-headers-2.6.24-16         - Header files related to Linux kernel versi
p   linux-headers-2.6.24-16-generic - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-16-openvz  - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-16-rt      - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-16-server  - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-16-xen     - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-18         - Header files related to Linux kernel versi
p   linux-headers-2.6.24-18-generic - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-18-openvz  - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-18-rt      - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-18-server  - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-18-xen     - Linux kernel headers for version 2.6.24 on
i A linux-headers-2.6.24-19         - Header files related to Linux kernel versi
i A linux-headers-2.6.24-19-generic - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-19-openvz  - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-19-rt      - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-19-server  - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-19-xen     - Linux kernel headers for version 2.6.24 on
p   linux-headers-amd64-generic     - Upgrade dummy package. Can be removed     
p   linux-headers-amd64-k8          - Upgrade dummy package. Can be removed     
p   linux-headers-amd64-server      - Upgrade dummy package. Can be removed     
p   linux-headers-amd64-xeon        - Upgrade dummy package. Can be removed     
i   linux-headers-generic           - Generic Linux kernel headers              
v   linux-headers-lbm               -                                           
v   linux-headers-lbm-2.6           -                                           
p   linux-headers-lbm-2.6.24-16-gen - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-16-ope - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-16-rt  - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-16-ser - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-16-xen - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-18-gen - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-18-ope - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-18-rt  - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-18-ser - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-18-xen - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-19-gen - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-19-ope - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-19-rt  - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-19-ser - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-19-xen - Header files related to linux-backports-mo
v   linux-headers-lum               -                                           
v   linux-headers-lum-2.6           -                                           
p   linux-headers-lum-2.6.24-16-gen - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-16-ope - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-16-rt  - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-16-ser - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-16-xen - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-18-gen - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-18-ope - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-18-rt  - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-18-ser - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-18-xen - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-19-gen - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-19-ope - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-19-rt  - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-19-ser - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-19-xen - Header files related to linux-ubuntu-modul
p   linux-headers-openvz            - openvz Linux kernel headers               
p   linux-headers-rt                - rt Linux kernel headers                   
p   linux-headers-server            - Linux kernel headers on Server Equipment. 
p   linux-headers-xen               - xen Linux kernel headers                  
p   linux-image                     - Generic Linux kernel image.               
v   linux-image-2.6                 -                                           
p   linux-image-2.6.24-16-generic   - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-16-openvz    - Linux kernel image for version 2.6.24 on O
p   linux-image-2.6.24-16-rt        - Linux kernel image for version 2.6.24 on I
p   linux-image-2.6.24-16-server    - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-16-xen       - Linux kernel image for version 2.6.24 on T
p   linux-image-2.6.24-18-generic   - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-18-openvz    - Linux kernel image for version 2.6.24 on O
p   linux-image-2.6.24-18-rt        - Linux kernel image for version 2.6.24 on I
p   linux-image-2.6.24-18-server    - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-18-xen       - Linux kernel image for version 2.6.24 on T
i   linux-image-2.6.24-19-generic   - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-19-openvz    - Linux kernel image for version 2.6.24 on O
p   linux-image-2.6.24-19-rt        - Linux kernel image for version 2.6.24 on I
p   linux-image-2.6.24-19-server    - Linux kernel image for version 2.6.24 on x
p   linux-image-2.6.24-19-xen       - Linux kernel image for version 2.6.24 on T
p   linux-image-amd64-generic       - Upgrade dummy package. Can be removed     
p   linux-image-amd64-k8            - Upgrade dummy package. Can be removed     
p   linux-image-amd64-server        - Upgrade dummy package. Can be removed     
p   linux-image-amd64-xeon          - Upgrade dummy package. Can be removed     
p   linux-image-debug-2.6.24-16-gen - Linux kernel debug image for version 2.6.2
p   linux-image-debug-2.6.24-16-ser - Linux kernel debug image for version 2.6.2
p   linux-image-debug-2.6.24-18-gen - Linux kernel debug image for version 2.6.2
p   linux-image-debug-2.6.24-18-ser - Linux kernel debug image for version 2.6.2
p   linux-image-debug-2.6.24-19-gen - Linux kernel debug image for version 2.6.2
p   linux-image-debug-2.6.24-19-ser - Linux kernel debug image for version 2.6.2
p   linux-image-debug-generic       - Linux kernel debug image for generic kerne
p   linux-image-debug-server        - Linux kernel debug image for server kernel
i   linux-image-generic             - Generic Linux kernel image                
p   linux-image-openvz              - Real time Linux kernel image              
p   linux-image-rt                  - Real time Linux kernel image              
p   linux-image-server              - Linux kernel image on Server Equipment.   
p   linux-image-xen                 - Real time Linux kernel image              
v   linux-initramfs-tool            -                                           
p   linux-kernel-devel              - Linux kernel hacking dependencies         
v   linux-kernel-headers            -                                           
v   linux-kernel-log-daemon         -                                           
i A linux-libc-dev                  - Linux Kernel Headers for development      
p   linux-libertine                 - The Linux Libertine family of free fonts  
p   linux-openvz                    - Complete openvz Linux kernel              
p   linux-patch-aufs                - Kernel patches for aufs                   
p   linux-patch-evms                - Enterprise Volume Management System (kerne
p   linux-patch-lustre              - Linux kernel patch for the Lustre Filesyst
p   linux-patch-openswan            - IPSEC Linux kernel support for Openswan   
p   linux-restricted-modules        - Generic Linux restricted modules.         
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on x86/x86_6
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on OpenVZ Vi
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on x86/x86_6
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on x86/x86_6
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on Xen      
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on x86/x86_6
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on OpenVZ Vi
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on x86/x86_6
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on x86/x86_6
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on Xen      
i   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on x86/x86_6
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on OpenVZ Vi
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on x86/x86_6
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on x86/x86_6
p   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on Xen      
p   linux-restricted-modules-amd64- - Upgrade dummy package. Can be removed     
p   linux-restricted-modules-amd64- - Upgrade dummy package. Can be removed     
p   linux-restricted-modules-amd64- - Upgrade dummy package. Can be removed     
i A linux-restricted-modules-common - Non-free Linux 2.6.24 modules helper scrip
i   linux-restricted-modules-generi - Restricted Linux modules for generic kerne
p   linux-restricted-modules-openvz - Restricted Linux modules for openvz kernel
p   linux-restricted-modules-rt     - Restricted Linux modules for rt kernels   
p   linux-restricted-modules-server - Restricted Linux modules for server kernel
p   linux-restricted-modules-xen    - Restricted Linux modules for xen kernels  
p   linux-rt                        - Complete rt Linux kernel                  
v   linux-security                  -                                           
p   linux-server                    - Complete Linux kernel on Server Equipment.
i   linux-sound-base                - base package for ALSA and OSS sound system
p   linux-source                    - Linux kernel source with Ubuntu patches   
v   linux-source-2.6                -                                           
p   linux-source-2.6.24             - Linux kernel source for version 2.6.24 wit
p   linux-ubuntu-modules-2.6.24-16- - Ubuntu supplied Linux modules for version 
p   linux-ubuntu-modules-2.6.24-16- - Ubuntu supplied Linux modules for version 
p   linux-ubuntu-modules-2.6.24-16- - Ubuntu supplied Linux modules for version 
p   linux-ubuntu-modules-2.6.24-16- - Ubuntu supplied Linux modules for version 
p   linux-ubuntu-modules-2.6.24-16- - Ubuntu supplied Linux modules for version 
p   linux-ubuntu-modules-2.6.24-18- - Ubuntu supplied Linux modules for version 
p   linux-ubuntu-modules-2.6.24-18- - Ubuntu supplied Linux modules for version 
p   linux-ubuntu-modules-2.6.24-18- - Ubuntu supplied Linux modules for version 
p   linux-ubuntu-modules-2.6.24-18- - Ubuntu supplied Linux modules for version 
p   linux-ubuntu-modules-2.6.24-18- - Ubuntu supplied Linux modules for version 
i   linux-ubuntu-modules-2.6.24-19- - Ubuntu supplied Linux modules for version 
p   linux-ubuntu-modules-2.6.24-19- - Ubuntu supplied Linux modules for version 
p   linux-ubuntu-modules-2.6.24-19- - Ubuntu supplied Linux modules for version 
p   linux-ubuntu-modules-2.6.24-19- - Ubuntu supplied Linux modules for version 
p   linux-ubuntu-modules-2.6.24-19- - Ubuntu supplied Linux modules for version 
p   linux-wlan-ng                   - utilities for wireless prism2 cards       
p   linux-wlan-ng-doc               - documentation for wlan-ng                 
p   linux-wlan-ng-firmware          - firmware files used by the linux-wlan-ng d
p   linux-wlan-ng-source            - linux-wlan-ng driver                      
p   linux-xen                       - Complete xen Linux kernel                 
v   linux32                         -                                           
p   linuxdcpp                       - Port of the Windows file-sharing program, 
p   linuxdcpp0.691                  - Port of the Windows file-sharing program D
v   linuxdoc-sgml                   -                                           
p   linuxdoc-tools                  - convert LinuxDoc SGML source into other fo
p   linuxdoc-tools-info             - Info output facility of LinuxDoc-Tools    
p   linuxdoc-tools-latex            - LaTeX/PS/PDF output facility of LinuxDoc-T
p   linuxdoc-tools-text             - Text output facility of LinuxDoc-Tools    
p   linuxfacile                     - An Italian manual for newbies             
p   linuxinfo                       - Displays extended system information      
p   linuxlogo                       - Color ANSI System Logo                    
p   linuxprinting.org-ppds          - OpenPrinting printer support - PostScript 
p   linuxprinting.org-ppds-extra    - OpenPrinting printer support - PostScript 
p   linuxtrade                      - A real-time stock market tracker and news 
p   linuxvnc                        - VNC server to allow remote access to a tty
v   locale-config-skolelinux        -                                           
p   mplinuxman                      - an mp3 player manager for mpman F50/F60   
v   not+gnu-linux                   -                                           
v   not+gnueabi-linux               -                                           
v   not+gnulp-linux                 -                                           
v   not+linux-gnueabi               -                                           
v   not+linux-gnulp                 -                                           
p   pptp-linux                      - Point-to-Point Tunneling Protocol (PPTP) C
p   python-selinux                  - Python bindings to SELinux shared librarie
p   python-selinux-dbg              - Python bindings to SELinux shared librarie
v   python2.4-selinux               -                                           
v   python2.5-selinux               -                                           
p   selflinux                       - A collection of German documents about Lin
p   selflinux-pdf                   - PDF version of the selflinux docs         
p   selinux                         - Security-Enhanced Linux runtime support   
p   selinux-basics                  - transitional package to smooth renaming to
p   selinux-doc                     - documentation for Security-Enhanced Linux 
v   selinux-policy                  -                                           
v   selinux-policy-cups             -                                           
p   selinux-policy-dummy            - Empty Security-Enhanced Linux policy (dumm
p   selinux-policy-refpolicy        - Security-Enhanced Linux Reference Policy B
p   selinux-policy-refpolicy-cups   - Security-Enhanced Linux Reference Policy C
p   selinux-policy-refpolicy-dev    - Security-Enhanced Linux Reference Policy D
p   selinux-policy-refpolicy-doc    - Security-Enhanced Linux Reference Policy D
p   selinux-policy-refpolicy-unconf - Security-Enhanced Linux Reference Policy U
v   selinux-policy-unconfined       -                                           
p   selinux-utils                   - SELinux utility programs                  
p   selinux-utils-dbg               - SELinux utility programs                  
p   syslinux                        - Bootloader for Linux/i386 using MS-DOS flo
v   ttf-linux-libertine             -                                           
p   user-mode-linux                 - User-mode Linux (kernel)                  
p   user-mode-linux-doc             - User-mode Linux (Documentation)           
i   util-linux                      - Miscellaneous system utilities            
i   util-linux-locales              - Locales files for util-linux              
v   x86-64-linux-gnu                - 
```

---

### Post by remu on 2008-07-27
bump

---

### Post by remu on 2008-07-28
Okay, I think this may be a hardware issue possibly. Because the video causes the same problem in Vista, but works in Vista's safemode. So I guess I'll be sending the laptop back to hp to get it looked at. Thanks for all your help anyways guys!

---

