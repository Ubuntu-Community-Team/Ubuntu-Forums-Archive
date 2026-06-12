---
title: "I cannot make work Airlink Golden 150  AWLL5077 in Ubuntu 9.10"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by cavalgar69 on 2010-09-30
I recently purchased this wireless adapter and tried to make work with ndiswrapper but I had no success so far. Could anyonoe give me a hand?
Many thanks

---

### Post by chili555 on 2010-09-30
I believe this is a r8192s_usb chipset. Please open Applications > Accessories > Terminal and do:```
lsusb
```Is the usb.id 0BDA:8171? If so, the driver is already built in to your kernel:```
$ modinfo r8192s_usb | grep 8171
alias:          usb:v[COLOR="Red"]0BDA[/COLOR]p[COLOR="Red"]8171[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```If it is not loading correctly, please do:```
sudo modprobe r8192s_usb
dmesg | grep 819
iwconfig
```Post the result and we'll try to see why it's not working.

---

### Post by cavalgar69 on 2010-09-30
First of all, Thank you for your help, chili555.
I'm going to post you the results:.
carlos@carlos1-desktop:~$ [COLOR=Blue]lsusb[/COLOR]
[COLOR=Red][SIZE=3]Bus 001 Device 008: ID 0bda:8171 Realtek Semiconductor Corp.[/SIZE] [/COLOR]
Bus 001 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


carlos@carlos1-desktop:~$ $ [COLOR=Blue]modinfo r8192s_usb | grep 8171[/COLOR]
$: command not found

carlos@carlos1-desktop:~$ [COLOR=Blue]alias:          usb:v0BDAp8171d*dc*dsc*dp*ic*isc*ip*[/COLOR]
alias:: command not found

[COLOR=Blue]carlos@carlos1-desktop:~$ sudo modprobe r8192s_usb[/COLOR]
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

carlos@carlos1-desktop:~$[COLOR=Blue] dmesg | grep 819[/COLOR]
[    0.000000] ACPI: SLIC 000000003fec8195 00176 (v01 HPQOEM SLIC-BPC 00000001      00000000)
[    0.918819] Bluetooth: RFCOMM ver 1.11
[   21.157833] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   21.164093] Linux kernel driver for RTL8192 based WLAN cards
[   21.164134] usbcore: registered new interface driver rtl819xU
[18191.740045] usb 1-5: new high speed USB device using ehci_hcd and address 8
[18191.895304] usb 1-5: configuration #1 chosen from 1 choice

carlos@carlos1-desktop:~$ [COLOR=Blue]iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

And after doing all this still does not work.

---

### Post by chili555 on 2010-09-30
> And after doing all this still does not work.We haven't done any work at all. We're still running diagnostics to find out what's going wrong. I'd like to see your whole *dmesg* file. Please run these commands and transfer the file on a USB drive or otherwise so it can be posted here as an attachment to your reply. Use the little paperclip icon to add an attachment.```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```Please attach *dmesg.zip* to your reply.

---

### Post by cavalgar69 on 2010-09-30
Sorry if I look impatience. It is just the product of my ignorance

I send you attached the dmesg.zip.
... and thanks again

---

### Post by chili555 on 2010-09-30
On boot, the correct driver is loaded; however, an interface, wlan0 is not created. So far, I do not know why.

Do you have the package *linux-firmware* installed? ```
sudo aptitude search linux-firmware
```Does this yield **i** for installed?

Do you have an internet connection through your ethernet cable? Is the result the same if you reboot without the ethernet connected?

If you have an ethernet connection, please do:```
sudo apt-get install linux-firmware
```Thanks.

---

### Post by cavalgar69 on 2010-09-30
Hi again.
I don't know if I understood you well. This is what I did

This is the result with the ethernet cable



carlos@carlos1-desktop:~$ [COLOR=Blue]sudo aptitude search linux-firmware[/COLOR]
[sudo] password for carlos: 
i   linux-firmware                  - Firmware for Linux kernel drivers         
p   linux-firmware-nonfree          - Non-free firmware for Linux kernel drivers


carlos@carlos1-desktop:~$ [COLOR=Blue]sudo aptitude search linux-firmware i[/COLOR]

p   xcolmix                         - an RGB colour mixer                       
p   xdaliclock                      - Melting digital clock                     
p   xdemineur                       - Yet another minesweeper for X             
p   xdeview                         - Smart multi-file multi-part decoder (X11 G
i   xdg-user-dirs                   - tool to manage well known user directories
i   xdg-user-dirs-gtk               - tool to manage well known user directories
i   xdg-utils                       - desktop integration utilities from freedes
p   xdiskusage                      - Displays a graphic of your disk usage with
p   xdvik-ja                        - Japanized DVI Previewer for the X Window S
p   xeji                            - Yet Another Follow the Mouse X demo       
p   xemacs21-bin                    - highly customizable text editor -- support
v   xen-hypervisor                  -                                           
p   xen-hypervisor-3.3              - The Xen Hypervisor for i386 and amd64.    
v   xen-hypervisor-amd64            -                                           
v   xen-hypervisor-i386             -                                           
v   xen-utils                       -                                           
p   xen-utils-3.3                   - XEN administrative tools                  
p   xenomai-doc                     - Xenomai documentation                     
p   xenomai-runtime                 - Xenomai runtime utilities                 
p   xevil                           - A violent side-scrolling game for X       
v   xf86-input-tslib                -                                           
v   xf86-video-driver-riva128       -                                           
p   xfce4-appfinder                 - Application finder for the Xfce4 Desktop E
p   xfce4-battery-plugin            - battery monitor plugin for the Xfce4 panel
p   xfce4-cddrive-plugin            - CD-Rom drive management plugin for the Xfc
p   xfce4-cellmodem-plugin          - cellular modem plugin for the Xfce4 panel 
p   xfce4-clipman-plugin            - clipboard history plugin for the Xfce4 pan
p   xfce4-cpu-freq-plugin           - display the CPU informations in the Xfce p
p   xfce4-cpufreq-plugin            - cpufreq information plugin for the Xfce4 p
p   xfce4-cpugraph-plugin           - CPU load graph plugin for the Xfce4 panel 
p   xfce4-datetime-plugin           - date and time plugin for the Xfce4 panel  
p   xfce4-dict                      - Dictionary plugin for Xfce4 panel         
p   xfce4-diskperf-plugin           - disk performance display plugin for the Xf
p   xfce4-eyes-plugin               - eyes plugin for the Xfce4 panel           
p   xfce4-fsguard-plugin            - filesystem monitor plugin for the Xfce4 pa
p   xfce4-genmon-plugin             - Generic Monitor for the Xfce4 panel       
p   xfce4-goodies                   - enhancements for the Xfce4 Desktop Environ
p   xfce4-governor-plugin           - governor plugin for the Xfce4 panel       
p   xfce4-icon-theme                - Xfce Standard icon theme                  
p   xfce4-linelight-plugin          - Search plugin for Xfce panel              
p   xfce4-mailwatch-plugin          - mail watcher plugin for the Xfce4 panel   
p   xfce4-messenger-plugin          - Dbus messages plugin for xfce4-panel      
p   xfce4-mixer                     - Xfce mixer application                    
p   xfce4-mount-plugin              - mount plugin for the Xfce4 panel          
p   xfce4-mpc-plugin                - Xfce panel plugin which serves as client f
p   xfce4-netload-plugin            - network load monitor plugin for the Xfce4 
p   xfce4-notes-plugin              - Notes plugin for the Xfce4 desktop        
p   xfce4-notifyd                   - simple, visually-appealing notification da
p   xfce4-places-plugin             - quick access to folders, documents and rem
p   xfce4-power-manager-plugins     - power manager plugins for Xfce panel      
p   xfce4-quicklauncher-plugin      - rapid launcher plugin for the Xfce4 panel 
p   xfce4-radio-plugin              - v4l radio control plugin for the Xfce4 pan
p   xfce4-screenshooter-plugin      - transitional dummy package for xfce4-scree
p   xfce4-sensors-plugin            - hardware sensors plugin for the Xfce4 pane
p   xfce4-session                   - Xfce4 Session Manager                     
p   xfce4-settings                  - graphical application for managing Xfce se
p   xfce4-smartbookmark-plugin      - search the web via the Xfce4 panel        
p   xfce4-smartpm-plugin            - Smart Package Manager plugin for xfce4-pan
p   xfce4-systemload-plugin         - system load monitor plugin for the Xfce4 p
p   xfce4-terminal                  - Xfce terminal emulator                    
p   xfce4-time-out-plugin           - time out plugin for the Xfce4 panel       
p   xfce4-timer-plugin              - timer plugin for Xfce panel               
p   xfce4-utils                     - Various tools for Xfce                    
p   xfce4-verve-plugin              - Verve (command line) plugin for Xfce 4.4 p
p   xfce4-volstatus-icon            - xfce systray icon for ejecting removable v
p   xfce4-wavelan-plugin            - wavelan status plugin for the Xfce4 panel 
p   xfce4-weather-plugin            - weather information plugin for the Xfce4 p
p   xfce4-wmdock-plugin             - Compatibility layer for running WindowMake
p   xfce4-xfapplet-plugin           - Gnome applets plugin for Xfce panel       
p   xfce4-xkb-plugin                - xkb layout switch plugin for the Xfce4 pan
p   xfig                            - Facility for Interactive Generation of fig
p   xfig-doc                        - XFig on-line documentation and examples   
p   xfig-libs                       - XFig image libraries and examples         
p   xfingerd                        - BSD-like finger daemon with qmail support 
p   xfireworks                      - Fireworks in your root window             
p   xfishtank                       - turns your X root into an aquarium        
p   xflip                           - programs to mirror-image or melt your disp
p   xfmedia                         - Xfce media player                         
p   xfmedia-dbg                     - Xfce media player, debugging symbols      
p   xfmedia-dev                     - The Xfmedia development files             
p   xfmedia-remote-plugin           - Xfmedia Remote control plugin             
v   xfntbig5p-cmex24m               -                                           
i   xfonts-100dpi                   - 100 dpi fonts for X                       
p   xfonts-100dpi-transcoded        - 100 dpi fonts for X (transcoded from ISO 1
i   xfonts-75dpi                    - 75 dpi fonts for X                        
p   xfonts-75dpi-transcoded         - 75 dpi fonts for X (transcoded from ISO 10
v   xfonts-arphic-bkai00mp          -                                           
v   xfonts-arphic-bsmi00lp          -                                           
v   xfonts-arphic-gbsn00lp          -                                           
v   xfonts-arphic-gkai00mp          -                                           
p   xfonts-bitmap-mule              - fonts of BITMAP-MULE for X                
p   xfonts-biznet-100dpi            - 100 dpi BIZNET ISO-8859-2 fonts for X serv
p   xfonts-biznet-75dpi             - 75 dpi BIZNET ISO-8859-2 fonts for X serve
p   xfonts-biznet-base              - Standard BIZNET ISO-8859-2 fonts for X ser
p   xfonts-bolkhov-75dpi            - 75 dpi Unicode Cyrillic fonts for X (Cyr-R
p   xfonts-bolkhov-cp1251-75dpi     - 75 dpi CP1251 encoded Cyrillic fonts for X
p   xfonts-bolkhov-cp1251-misc      - Character-cell CP1251 encoded Cyrillic fon
p   xfonts-bolkhov-isocyr-75dpi     - 75 dpi ISO 8859-5 encoded Cyrillic fonts f
p   xfonts-bolkhov-isocyr-misc      - Character-cell ISO-8859-5 encoded Cyrillic
p   xfonts-bolkhov-koi8r-75dpi      - 75 dpi KOI8-R encoded Cyrillic fonts for X
p   xfonts-bolkhov-koi8r-misc       - Character-cell KOI8-R encoded Cyrillic fon
p   xfonts-bolkhov-koi8u-75dpi      - 75 dpi KOI8-U encoded Cyrillic fonts for X
p   xfonts-bolkhov-koi8u-misc       - Character-cell KOI8-U encoded Cyrillic fon
p   xfonts-bolkhov-misc             - Character-cell Unicode Cyrillic fonts for 
p   xfonts-cmex-big5p               - Big5+ Chinese Mingti bitmap font (by CMEX 
p   xfonts-cronyx-100dpi            - 100 dpi Unicode Cyrillic fonts for X (Cron
p   xfonts-cronyx-75dpi             - 75 dpi Unicode Cyrillic fonts for X (Crony
p   xfonts-cronyx-cp1251-100dpi     - 100 dpi CP1251 encoded Cyrillic fonts for 
p   xfonts-cronyx-cp1251-75dpi      - 75 dpi CP1251 encoded Cyrillic fonts for X
p   xfonts-cronyx-cp1251-misc       - Character-cell CP1251 encoded Cyrillic fon
p   xfonts-cronyx-isocyr-100dpi     - 100 dpi ISO 8859-5 encoded Cyrillic fonts 
p   xfonts-cronyx-isocyr-75dpi      - 75 dpi ISO 8859-5 encoded Cyrillic fonts f
p   xfonts-cronyx-isocyr-misc       - Character-cell ISO-8859-5 encoded Cyrillic
p   xfonts-cronyx-koi8r-100dpi      - 100 dpi KOI8-R encoded Cyrillic fonts for 
p   xfonts-cronyx-koi8r-75dpi       - 75 dpi KOI8-R encoded Cyrillic fonts for X
p   xfonts-cronyx-koi8r-misc        - Character-cell KOI8-R encoded Cyrillic fon
p   xfonts-cronyx-koi8u-100dpi      - 100 dpi KOI8-U encoded Cyrillic fonts for 
p   xfonts-cronyx-koi8u-75dpi       - 75 dpi KOI8-U encoded Cyrillic fonts for X
p   xfonts-cronyx-koi8u-misc        - Character-cell KOI8-U encoded Cyrillic fon
p   xfonts-cronyx-misc              - Character-cell Unicode Cyrillic fonts for 
p   xfonts-cyrillic                 - Cyrillic fonts for X                      
p   xfonts-efont-unicode            - /efont/ Unicode fonts for X which cover va
p   xfonts-efont-unicode-ib         - /efont/ Unicode fonts for X (italic and bo
i   xfonts-encodings                - Encodings for X.Org fonts                 
p   xfonts-intl-arabic              - International fonts for X -- Arabic       
p   xfonts-intl-asian               - International fonts for X -- Asian        
p   xfonts-intl-chinese             - International fonts for X -- Chinese      
p   xfonts-intl-chinese-big         - International fonts for X -- Chinese big  
p   xfonts-intl-european            - International fonts for X -- European     
p   xfonts-intl-japanese            - International fonts for X -- Japanese     
p   xfonts-intl-japanese-big        - International fonts for X -- Japanese big 
p   xfonts-intl-phonetic            - International fonts for X -- Phonetic Alph
p   xfonts-jisx0213                 - JIS X 0213 Japanese Kanji bitmap fonts for
p   xfonts-knickers                 - Knickers font for X                       
p   xfonts-marumoji                 - Roundish fonts (marumoji fonts) for X     
p   xfonts-shinonome                - Various 12,14,16 dot Japanese Kanji, iso88
p   xfonts-terminus                 - Fixed-width fonts for fast reading        
p   xfonts-terminus-dos             - Fixed-width fonts for DOS encodings       
p   xfonts-terminus-oblique         - Oblique version of the Terminus font      
p   xfonts-thai                     - A collection of Thai fonts for X          
p   xfonts-thai-etl                 - Thai etl fonts for X                      
p   xfonts-thai-manop               - Dr.Manop Wongsaisuwan's bitmap fonts for X
p   xfonts-thai-nectec              - Thai fixed fonts for X from Nectec        
p   xfonts-thai-poonlap             - Poonlap Veerathanabutr bitmap fonts for X 
p   xfonts-thai-vor                 - Voradesh Yenbut bitmap fonts for X        
p   xfonts-tipa                     - X11 PostScript Type 1 font for the Phoneti
p   xfonts-unifont                  - PCF (bitmap) version of the GNU Unifont   
i   xfonts-utils                    - X Window System font utility programs     
p   xfonts-x3270-misc               - Font files for the x3270(1) IBM 3270 emula
p   xfprint4                        - Printer GUI for Xfce4                     
p   xfractint                       - UNIX-based fractal generator              
v   xfree86-driver-synaptics        -                                           
p   xfrisk                          - Server and X11 client for playing risk wit
p   xfslibs-dev                     - XFS filesystem-specific static libraries a
p   xfswitch-plugin                 - fast user switching plugin for the Xfce pa
p   xgdvi                           - a TeX DVI previewer for X, with a nice GTK
p   xgnokii                         - Datasuite for mobile phone management (X i
p   xgridfit                        - a program for gridfitting, or "hinting," T
p   xgridfit-doc                    - Documentation for xgridfit                
p   xicc                            - set the ICC colour profile for an X displa
v   ximian-connector                -                                           
v   ximian-setup-tools              -                                           
p   xindy                           - index generator for structured documents l
p   xindy-rules                     - rule files for xindy                      
p   xine-console                    - the xine video player, user interface     
p   xine-dbg                        - the xine video player, debug symbols      
p   xine-plugin                     - xine-based media player plugin for Mozilla
i A xine-ui                         - the xine video player, user interface     
p   xineliboutput-fbfe              - Remote Framebuffer frontend for vdr-plugin
p   xineliboutput-sxfe              - Remote X-Server frontend for vdr-plugin-xi
p   xinetd                          - replacement for inetd with many enhancemen
i   xinit                           - X server initialisation tool              
i   xinput                          - Runtime configuration and test of XInput d
p   xinv3d                          - 3D space invaders for X                   
p   xiphos                          - environment for Bible reading, study, and 
p   xiphos-data                     - data files for Xiphos Bible study software
p   xipmsg                          - A pop up style message communication softw
p   xiterm                          - internationalized terminal emulator for X 
p   xiterm+thai                     - X terminal program with Thai languague sup
p   xjdic                           - Japanese-English dictionary search program
p   xjig                            - An X11 jigsaw puzzle                      
p   xlassie                         - Dockable mail notifier w/ message count & 
p   xlbiff                          - X Literate Biff. Displays From and Subject
p   xli                             - command line tool for viewing images in X1
p   xlibmesa-gl                     - transitional package for Debian etch      
p   xlibmesa-gl-dev                 - transitional package for Debian etch      
p   xlibmesa-glu                    - transitional package for Debian etch      
v   xlibmesa-glu-dev                -                                           
v   xlibosmesa-dev                  -                                           
p   xloadimage                      - Graphics file viewer under X11            
p   xmail                           - advanced, fast and reliable ESMTP/POP3 mai
p   xmail-doc                       - documentation for xmail                   
p   xmaxima                         - A computer algebra system -- x interface  
p   xmille                          - The classic game of Mille Bournes         
p   xmix                            - X11-based interface to the Linux sound dri
v   xml-i18n-tools                  -                                           
p   xml-resume-library              - A set of tools for writing a resume in XML
p   xml-rpc-api2cpp                 - Generate C++ wrapper classes for XML-RPC s
p   xml-rpc-api2txt                 - Dump an XML-RPC API as a text file        
p   xml-twig-tools                  - Command line tools for processing XML docu
p   xmldiff                         - tree to tree correction between xml docume
p   xmldiff-xmlrev                  - xmldiff output formatter                  
p   xmlindent                       - XML stream reformatter                    
p   xmltooling-schemas              - XML schemas for XMLTooling                
p   xmltv-gui                       - Graphical user interface related to the XM
p   xmltv-util                      - Utilities related to the XMLTV file format
p   xmms2-client-avahi              - XMMS2 - avahi client                      
p   xmms2-client-cli                - XMMS2 - cli client                        
p   xmms2-client-medialib-updater   - XMMS2 - medialib-updater client           
p   xmms2-client-nycli              - XMMS2 - new cli client                    
p   xmms2-client-vis                - XMMS2 - visualization clients             
p   xmms2-icon                      - XMMS2 - icon package                      
p   xmms2-plugin-airplay            - XMMS2 - airplay output plug-in            
p   xmms2-plugin-all                - XMMS2 - all plug-ins                      
p   xmms2-plugin-alsa               - XMMS2 - ALSA output                       
p   xmms2-plugin-ao                 - XMMS2 - libao output plug-in              
p   xmms2-plugin-apefile            - XMMS2 - Monkey's Audio decoder plug-in    
p   xmms2-plugin-asf                - XMMS2 - ASF plug-in                       
p   xmms2-plugin-asx                - XMMS2 - ASX playlist plug-in              
p   xmms2-plugin-avcodec            - XMMS2 - avcodec decoder                   
p   xmms2-plugin-cdda               - XMMS2 - CDDA plug-in                      
p   xmms2-plugin-cue                - XMMS2 - CUE playlist plug-in              
p   xmms2-plugin-curl               - XMMS2 - curl transport for HTTP           
p   xmms2-plugin-daap               - XMMS2 - daap plug-in                      
p   xmms2-plugin-faad               - XMMS2 - faad decoder                      
p   xmms2-plugin-flac               - XMMS2 - FLAC decoder                      
p   xmms2-plugin-flv                - XMMS2 - Flash Video plug-in               
p   xmms2-plugin-gme                - XMMS2 - gme plug-in                       
p   xmms2-plugin-gvfs               - XMMS2 - gvfs plug-in                      
p   xmms2-plugin-html               - XMMS2 - HTML playlist plug-in             
p   xmms2-plugin-ices               - XMMS2 - Ogg streaming output              
p   xmms2-plugin-icymetaint         - XMMS2 - shoutcast metadata plug-in        
p   xmms2-plugin-id3v2              - XMMS2 - ID3v2 plug-in                     
p   xmms2-plugin-jack               - XMMS2 - JACK output                       
p   xmms2-plugin-karaoke            - XMMS2 - karaoke plug-in                   
p   xmms2-plugin-m3u                - XMMS2 - M3U playlist plug-in              
p   xmms2-plugin-mad                - XMMS2 - libmad based mp3 decoder          
p   xmms2-plugin-mms                - XMMS2 - MMS transport                     
p   xmms2-plugin-modplug            - XMMS2 - modplug decoder                   
p   xmms2-plugin-mp4                - XMMS2 - MPEG-4 plug-in                    
p   xmms2-plugin-mpg123             - XMMS2 - libmpg123 based mp3 decoder       
p   xmms2-plugin-musepack           - XMMS2 - mpc decoder                       
p   xmms2-plugin-normalize          - XMMS2 - Normalize plug-in                 
p   xmms2-plugin-ofa                - XMMS2 - Open Fingerprint Architecture plug
p   xmms2-plugin-oss                - XMMS2 - OSS output                        
p   xmms2-plugin-pls                - XMMS2 - PLS playlist plug-in              
p   xmms2-plugin-pulse              - XMMS2 - PulseAudio output plug-in         
p   xmms2-plugin-rss                - XMMS2 - RSS podcast plug-in               
p   xmms2-plugin-sid                - XMMS2 - libsidplay2 based decoder         
p   xmms2-plugin-smb                - XMMS2 - Samba transport                   
p   xmms2-plugin-speex              - XMMS2 - Speex decoder                     
p   xmms2-plugin-tta                - XMMS2 - TTA decoder plug-in               
p   xmms2-plugin-vocoder            - XMMS2 - vocoder plug-in                   
p   xmms2-plugin-vorbis             - XMMS2 - vorbis decoder                    
p   xmms2-plugin-wavpack            - XMMS2 - WavPack decoder plug-in           
p   xmms2-plugin-wma                - XMMS2 - wma decoder                       
p   xmms2-plugin-xml                - XMMS2 - XML plug-in                       
p   xmms2-plugin-xspf               - XMMS2 - XSPF playist plug-in              
p   xmountains                      - Fractal landscape generator for X         
p   xmp-audacious                   - An XMP plugin for Audacious               
p   xmpi                            - a graphical user interface for MPI program
p   xnecview                        - NEC structure and gain pattern viewer     
p   xnetcardconfig                  - A simple network card configuration wizard
p   xoids                           - Asteroids game with powerups and color gra
p   xonix                           - Carve up the screen whilst dodging monster
v   xorg-build-macros               -                                           
p   xorg-driver-fglrx               - Video driver for the ATI graphics accelera
p   xorg-driver-fglrx-dev           - Video driver for the ATI graphics accelera
v   xorg-driver-synaptics           -                                           
p   xorg-options-editor-gtk         - Editor for xorg.conf files                
p   xorriso                         - command line iso9660+RR manipulation tool 
p   xosd-bin                        - X On-Screen Display library - binary files
p   xosview                         - X based system monitor                    
p   xpaint                          - simple paint program for X                
p   xpdf-chinese-simplified         - Portable Document Format (PDF) suite -- si
p   xpdf-chinese-traditional        - Portable Document Format (PDF) suite -- tr
p   xpdf-utils                      - Portable Document Format (PDF) suite -- ut
p   xpenguins                       - little penguins walk on your windows      
p   xpenguins-applet                - GNOME2 panel applet implementation of xpen
p   xpilot-extra                    - Maps, utilities and configs for XPilot    
p   xpilot-ng                       - Multi-player tactical game for X (NG versi
p   xpilot-ng-client-sdl            - Client for XPilot NG                      
p   xpilot-ng-client-x11            - Client for XPilot NG                      
p   xpilot-ng-common                - Common files for XPilot NG                
p   xpilot-ng-server                - Server for hosting XPilot NG games        
p   xpilot-ng-utils                 - Utilities for XPilot NG                   
p   xplanet-images                  - imagery for xplanet                       
p   xpm2wico                        - An Xpm to Windows .ico converter          
p   xpmutils                        - X11 pixmap utilities                      
p   xpostit                         - simple postit program on X with I18N suppo
p   xprint-utils                    - utilities for Xprint, the X11 print system
p   xprintidle                      - Small utility that prints user's idle time
p   xprintmon                       - graphical print queue monitor for lprng   
p   xqilla                          - XQuery and XPath 2.0 command line interpre
p   xringd                          - extended ring daemon - monitor phone rings
v   xserver-xorg-input-4            -                                           
p   xserver-xorg-input-acecad       - X.Org X server -- AceCad input driver     
p   xserver-xorg-input-aiptek       - X.Org X server -- Aiptek input driver     
i   xserver-xorg-input-all          - the X.Org X server -- input driver metapac
p   xserver-xorg-input-elographics  - X.Org X server -- ELOGraphics input driver
i   xserver-xorg-input-evdev        - X.Org X server -- evdev input driver      
p   xserver-xorg-input-evtouch      - Touchscreen-Driver for X.Org/XFree86 serve
p   xserver-xorg-input-fpit         - X.Org X server -- FPIT input driver       
p   xserver-xorg-input-joystick     - X.Org X server -- joystick input driver   
p   xserver-xorg-input-kbd          - X.Org X server -- keyboard input driver   
i   xserver-xorg-input-mouse        - X.Org X server -- mouse input driver      
p   xserver-xorg-input-mutouch      - X.Org X server -- muTouch input driver    
p   xserver-xorg-input-penmount     - X.Org X server -- Penmount input driver   
i   xserver-xorg-input-synaptics    - Synaptics TouchPad driver for X.Org server
p   xserver-xorg-input-tslib        - tslib touchscreen driver for X.Org/XFree86
i   xserver-xorg-input-vmmouse      - X.Org X server -- VMMouse input driver to 
p   xserver-xorg-input-void         - X.Org X server -- void input driver       
i   xserver-xorg-input-wacom        - X.Org X server -- Wacom input driver      
v   xserver-xorg-video-5            -                                           
i   xserver-xorg-video-all          - the X.Org X server -- output driver metapa
i   xserver-xorg-video-apm          - X.Org X server -- APM display driver      
i   xserver-xorg-video-ark          - X.Org X server -- ark display driver      
i   xserver-xorg-video-ati          - X.Org X server -- ATI display driver wrapp
p   xserver-xorg-video-ati-dbg      - X.Org X server -- ATI display driver wrapp
i   xserver-xorg-video-chips        - X.Org X server -- Chips display driver    
i   xserver-xorg-video-cirrus       - X.Org X server -- Cirrus display driver   
p   xserver-xorg-video-dummy        - X.Org X server -- dummy display driver    
i   xserver-xorg-video-fbdev        - X.Org X server -- fbdev display driver    
p   xserver-xorg-video-glint        - X.Org X server -- Glint display driver    
i   xserver-xorg-video-i128         - X.Org X server -- i128 display driver     
p   xserver-xorg-video-i740         - X.Org X server -- i740 display driver     
i   xserver-xorg-video-intel        - X.Org X server -- Intel i8xx, i9xx display
p   xserver-xorg-video-intel-dbg    - X.Org X server -- Intel i8xx, i9xx display
p   xserver-xorg-video-ivtv         - X.Org X server -- IVTV display driver     
p   xserver-xorg-video-ivtv-dbg     - X.Org X server -- IVTV display driver (deb
i   xserver-xorg-video-mach64       - X.Org X server -- ATI Mach64 display drive
p   xserver-xorg-video-mach64-dbg   - X.Org X server -- ATI display driver (debu
i   xserver-xorg-video-mga          - X.Org X server -- MGA display driver      
i   xserver-xorg-video-neomagic     - X.Org X server -- Neomagic display driver 
p   xserver-xorg-video-nouveau      - X.Org X server -- Nouveau display driver (
i   xserver-xorg-video-nv           - X.Org X server -- NV display driver       
i   xserver-xorg-video-openchrome   - X.Org X server -- VIA display driver      
i   xserver-xorg-video-r128         - X.Org X server -- ATI r128 display driver 
p   xserver-xorg-video-r128-dbg     - X.Org X server -- ATI r128 display driver 
i   xserver-xorg-video-radeon       - X.Org X server -- ATI Radeon display drive
p   xserver-xorg-video-radeon-dbg   - X.Org X server -- ATI Radeon display drive
p   xserver-xorg-video-radeonhd     - X.Org X server -- AMD/ATI r5xx, r6xx displ
p   xserver-xorg-video-radeonhd-dbg - X.Org X server -- AMD/ATI r5xx, r6xx displ
i   xserver-xorg-video-rendition    - X.Org X server -- Rendition display driver
i   xserver-xorg-video-s3           - X.Org X server -- legacy S3 display driver
i   xserver-xorg-video-s3virge      - X.Org X server -- S3 ViRGE display driver 
i   xserver-xorg-video-savage       - X.Org X server -- Savage display driver   
i   xserver-xorg-video-siliconmotio - X.Org X server -- SiliconMotion display dr
i   xserver-xorg-video-sis          - X.Org X server -- SiS display driver      
i   xserver-xorg-video-sisusb       - X.Org X server -- SiS USB display driver  
i   xserver-xorg-video-tdfx         - X.Org X server -- tdfx display driver     
i   xserver-xorg-video-trident      - X.Org X server -- Trident display driver  
i   xserver-xorg-video-tseng        - X.Org X server -- Tseng display driver    
i   xserver-xorg-video-v4l          - X.Org X server -- Video 4 Linux display dr
i   xserver-xorg-video-vesa         - X.Org X server -- VESA display driver     
p   xserver-xorg-video-via          - X.Org X server -- VIA display driver (dumm
i   xserver-xorg-video-vmware       - X.Org X server -- VMware display driver   
i   xserver-xorg-video-voodoo       - X.Org X server -- Voodoo display driver   
p   xsettings-kde                   - XSettings daemon for KDE                  
p   xshisen                         - Shisen-sho puzzle game for X11            
p   xshogi                          - An X Window System Japanese Chess (Shogi) 
p   xsidplay                        - Music player for tunes from C64           
p   xsoldier                        - shoot 'em up game with the "not shooting" 
p   xstarfish                       - X wallpaper generator                     
p   xsynth-dssi                     - classic-analog (VCOs-VCF-VCA) style softwa
p   xsysinfo                        - display some Linux kernel parameters in gr
p   xtail                           - like "tail -f", but works on truncated fil
p   xtide                           - provides tide and current predictions     
p   xtide-coastline                 - coastline data for xtide                  
p   xtide-data                      - Harmonics data for xtide                  
p   xtide-data-nonfree              - Harmonics data for xtide (Canada, Netherla
p   xtightvncviewer                 - virtual network computing client software 
p   xtoolwait                       - Allows to start X applications serially   
p   xtradius                        - Free radius server implementation         
p   xtris                           - client-server multiplayer X tetris        
p   xttitle                         - Changes X terminal emulator window titles 
p   xtux-client                     - arcade game featuring Free Software mascot
p   xubuntu-default-settings        - default settings for Xubuntu              
p   xubuntu-restricted-extras       - Commonly used restricted packages         
p   xul-ext-all-in-one-sidebar      - A sidebar extension for Iceweasel/Firefox 
v   xul-ext-bindwood                -                                           
p   xul-ext-firebug                 - web development plugin for Firefox        
v   xul-ext-prism                   -                                           
v   xul-ext-speeddial               -                                           
p   xul-ext-ubuntu-it-menu          - Firefox extension for a quick browse of Ub
p   xulrunner-1.9.1-testsuite       - Test Suite from XULRunner 1.9.1           
p   xulrunner-1.9.1-testsuite-dev   - Test Suite development files for XULRunner
p   xulrunner-1.9.2-testsuite       - Test Suite from XULRunner 1.9.2           
p   xulrunner-1.9.2-testsuite-dev   - Test Suite development files for XULRunner
p   xutils                          - X Window System utility programs metapacka
p   xutils-dev                      - X Window System utility programs for devel
p   xvid4conf                       - creates XviD configuration files          
p   xvidcap                         - Screen video capture for X                
p   xvidenc                         - shell script to encode DVDs to Xvid       
p   xvier                           - a "Four in a row" game                    
p   xview-clients                   - XView client programs                     
p   xview-examples                  - XView contrib programs                    
p   xviewg                          - XView shared libraries                    
p   xviewg-dev                      - XView development tools                   
p   xvile                           - VI Like Emacs - vi work-alike (X11)       
p   xvnc4viewer                     - Virtual network computing client software 
p   xwelltris                       - 3D Tetris like popular game similar to Wel
p   xwit                            - a collection of simple routines to call so
p   xwrits                          - reminds you to take a break from typing   
p   xxdiff                          - graphical file/directory comparison and me
p   xxdiff-scripts                  - graphical file/directory comparison and me
p   xymon-client                    - client for the Xymon network monitor      
p   xz-utils                        - high compression-ratio compressor         
p   xzip                            - Interpreter of Infocom-format story-files 
p   yabasic                         - Yet Another BASIC interpreter             
p   yacpi                           - ncurses based acpi monitor for text mode  
p   yagiuda                         - software to analyse performance of Yagi-Ud
p   yaird                           - Yet Another mkInitRD                      
v   yale-viewer                     -                                           
p   yamdi                           - a utility for adding metadata to flash vid
p   yapps2-runtime                  - Yet Another Python Parser System          
p   yardradius                      - YARD Radius Authorization and Accounting S
p   yasnippet                       - A template system for Emacs               
p   yaws-mail                       - Webmail application for Yaws web server   
p   yaws-wiki                       - Wiki application for Yaws web server      
p   yaz-icu                         - command line utility for ICU utilities of 
p   yaz-illclient                   - utility for ISO ILL of YAZ                
p   ydpdict                         - interface for Collins and Langenscheidt di
p   yersinia                        - Network vulnerabilities check software    
p   yics                            - Yahoo! Chess client for use with FICS inte
p   yiff-server                     - Y Sound Server                            
p   yiyantang                       - Terminal-based Chinese automatic encoding 
p   yokadi                          - command line TODO list tool               
p   yorick                          - interpreted language and scientific graphi
p   yorick-cubeview                 - a 3D FITS data viewer specialized in spect
p   yorick-curses                   - interface to the (n)curses library for the
p   yorick-data                     - interpreted library for the Yorick languag
p   yorick-dev                      - development files for the Yorick interpret
p   yorick-doc                      - documentation for the Yorick interpreted l
p   yorick-gl                       - OpenGL 3D graphics support for the Yorick 
p   yorick-hdf5                     - Hierarchical Data Format 5 interface for t
p   yorick-imutil                   - fast image manipulation routines for the Y
p   yorick-ml4                      - Matlab file format support for the Yorick 
p   yorick-soy                      - sparse matrix operations for the Yorick la
p   yorick-spydr                    - FITS image display and simple analysis    
p   yorick-yao                      - a Yorick-based adaptive optics system simu
p   yorick-yeti                     - utility plugin for the Yorick language    
p   yorick-yeti-fftw                - FFT plugin for the Yorick language        
p   yorick-yeti-gsl                 - GSL special functions plugin for the Yoric
p   yorick-yeti-regex               - POSIX regular expressions for the Yorick l
p   yorick-yeti-tiff                - TIFF image format input for the Yorick lan
p   yorick-yutils                   - various utilities for the Yorick language 
p   yorick-z                        - zlib, jpeg and png support for the Yorick 
p   ypsilon                         - R6RS Scheme implementation with concurrent
p   yudit                           - Unicode text editor (arch-dependent binari
p   yudit-common                    - Unicode text editor (arch-independent file
p   yudit-doc                       - Unicode text editor (Documentation)       
p   z8530-utils2                    - Utilities for Z8530 based HDLC cards for A
p   z88dk-bin                       - executable files for z88dk                
p   zabbix-agent                    - network monitoring solution - agent       
p   zabbix-frontend-php             - network monitoring solution - PHP front-en
p   zabbix-proxy-mysql              - network monitoring solution - proxy (using
p   zabbix-proxy-pgsql              - network monitoring solution - proxy (using
p   zabbix-server-mysql             - network monitoring solution - server (usin
p   zabbix-server-pgsql             - network monitoring solution - server (usin
p   zanshin                         - Todo List Manager                         
p   zapping                         - television viewer for the GNOME environmen
v   zcode-interpreter               -                                           
p   zeitgeist-core                  - activity logging service                  
p   zekr-quran-translations-en      - Zekr Quran English translations           
p   zend-framework-bin              - a simple, straightforward, open-source sof
i   zenity                          - Display graphical dialog boxes from shell 
p   zephyr-clients                  - Project Athena's notification service - cl
v   zeroc-ice                       -                                           
p   zeroc-ice-manual                - Ice documentation in pdf                  
p   zeroc-ice33                     - Internet Communications Engine            
p   zeroc-icee                      - Embedded edition of the ZeroC Ice         
p   zeroinstall-injector            - run programs by URL                       
p   zile                            - very small Emacs-subset editor            
p   zim                             - graphical text editor based on wiki techno
p   zimpl                           - mathematical modeling language for optimiz
p   zinnia-utils                    - utils for the zinnia library              
i   zip                             - Archiver for .zip files                   
p   zipcmp                          - compare contents of zip archives          
p   zipmerge                        - merge zip archives                        
p   zipper.app                      - Tool for inspecting the contents of a comp
p   ziproxy                         - compressing HTTP proxy server             
p   zivot                           - the game of life, simple console version  
p   zlib-bin                        - compression library - sample programs     
p   zlib-gst                        - Zlib bindings for GNU Smalltalk           
i   zlib1g                          - compression library - runtime             
p   zlib1g-dbg                      - compression library - development         
idA zlib1g-dev                      - compression library - development         
p   zlibc                           - An on-fly auto-uncompressing C library    
p   znc-webadmin                    - an advanced IRC bouncer (webadmin module) 
p   zoidberg                        - modular Perl shell                        
p   zonecheck-cgi                   - A DNS configuration checker, Web interface
p   zoneminder                      - Linux video camera security and surveillan
p   zope-atextensions               - Extensions to Archetypes in Zope          
p   zope-cmfbibliographyat          - A Bibliography management product for Zope
p   zope-cookiecrumbler             - Use cookies even when folder doesn't suppo
v   zope-docfindereverywhere        -                                           
p   zope-docfindertab               - Find documentation for a Zope product usin
p   zope-externaleditor             - Zope External Editor                      
p   zope-ldapmultiplugins           - LDAP plugin for Zope/Plone                
p   zope-linguaplone                - multilingual and translation solution for 
p   zope-maildrophost               - send mails from within Zope through a mail
p   zope-scriptablefields           - Zope tool bundle for working with componen
p   zope-textindexng3               - full text index for Zope objects          
p   zope-textindexng3-lib           - full text index for Zope objects          
p   zope-tinytableplus              - Present tabular data in Zope              
p   zope-zwiki                      - WikiWikiWeb implementation for Zope       
p   zopeedit                        - Helper Application for Zope External Edito
p   zsh-static                      - A shell with lots of features (static link
p   zvbi                            - Vertical Blanking Interval (VBI) utilities
p   zziplib-bin                     - library providing read access on ZIP-archi


And this is the result after reboot without the ethernet cable


carlos@carlos1-desktop:~$ [COLOR=Blue]sudo aptitude search linux-firmware[/COLOR]
[sudo] password for carlos: 
i   linux-firmware                  - Firmware for Linux kernel drivers         
p   linux-firmware-nonfree          - Non-free firmware for Linux kernel drivers
carlos@carlos1-desktop:~$ [COLOR=Blue]sudo aptitude search linux-firmware i[/COLOR]


p   xcolmix                         - an RGB colour mixer                       
p   xdaliclock                      - Melting digital clock                     
p   xdemineur                       - Yet another minesweeper for X             
p   xdeview                         - Smart multi-file multi-part decoder (X11 G
i   xdg-user-dirs                   - tool to manage well known user directories
i   xdg-user-dirs-gtk               - tool to manage well known user directories
i   xdg-utils                       - desktop integration utilities from freedes
p   xdiskusage                      - Displays a graphic of your disk usage with
p   xdvik-ja                        - Japanized DVI Previewer for the X Window S
p   xeji                            - Yet Another Follow the Mouse X demo       
p   xemacs21-bin                    - highly customizable text editor -- support
v   xen-hypervisor                  -                                           
p   xen-hypervisor-3.3              - The Xen Hypervisor for i386 and amd64.    
v   xen-hypervisor-amd64            -                                           
v   xen-hypervisor-i386             -                                           
v   xen-utils                       -                                           
p   xen-utils-3.3                   - XEN administrative tools                  
p   xenomai-doc                     - Xenomai documentation                     
p   xenomai-runtime                 - Xenomai runtime utilities                 
p   xevil                           - A violent side-scrolling game for X       
v   xf86-input-tslib                -                                           
v   xf86-video-driver-riva128       -                                           
p   xfce4-appfinder                 - Application finder for the Xfce4 Desktop E
p   xfce4-battery-plugin            - battery monitor plugin for the Xfce4 panel
p   xfce4-cddrive-plugin            - CD-Rom drive management plugin for the Xfc
p   xfce4-cellmodem-plugin          - cellular modem plugin for the Xfce4 panel 
p   xfce4-clipman-plugin            - clipboard history plugin for the Xfce4 pan
p   xfce4-cpu-freq-plugin           - display the CPU informations in the Xfce p
p   xfce4-cpufreq-plugin            - cpufreq information plugin for the Xfce4 p
p   xfce4-cpugraph-plugin           - CPU load graph plugin for the Xfce4 panel 
p   xfce4-datetime-plugin           - date and time plugin for the Xfce4 panel  
p   xfce4-dict                      - Dictionary plugin for Xfce4 panel         
p   xfce4-diskperf-plugin           - disk performance display plugin for the Xf
p   xfce4-eyes-plugin               - eyes plugin for the Xfce4 panel           
p   xfce4-fsguard-plugin            - filesystem monitor plugin for the Xfce4 pa
p   xfce4-genmon-plugin             - Generic Monitor for the Xfce4 panel       
p   xfce4-goodies                   - enhancements for the Xfce4 Desktop Environ
p   xfce4-governor-plugin           - governor plugin for the Xfce4 panel       
p   xfce4-icon-theme                - Xfce Standard icon theme                  
p   xfce4-linelight-plugin          - Search plugin for Xfce panel              
p   xfce4-mailwatch-plugin          - mail watcher plugin for the Xfce4 panel   
p   xfce4-messenger-plugin          - Dbus messages plugin for xfce4-panel      
p   xfce4-mixer                     - Xfce mixer application                    
p   xfce4-mount-plugin              - mount plugin for the Xfce4 panel          
p   xfce4-mpc-plugin                - Xfce panel plugin which serves as client f
p   xfce4-netload-plugin            - network load monitor plugin for the Xfce4 
p   xfce4-notes-plugin              - Notes plugin for the Xfce4 desktop        
p   xfce4-notifyd                   - simple, visually-appealing notification da
p   xfce4-places-plugin             - quick access to folders, documents and rem
p   xfce4-power-manager-plugins     - power manager plugins for Xfce panel      
p   xfce4-quicklauncher-plugin      - rapid launcher plugin for the Xfce4 panel 
p   xfce4-radio-plugin              - v4l radio control plugin for the Xfce4 pan
p   xfce4-screenshooter-plugin      - transitional dummy package for xfce4-scree
p   xfce4-sensors-plugin            - hardware sensors plugin for the Xfce4 pane
p   xfce4-session                   - Xfce4 Session Manager                     
p   xfce4-settings                  - graphical application for managing Xfce se
p   xfce4-smartbookmark-plugin      - search the web via the Xfce4 panel        
p   xfce4-smartpm-plugin            - Smart Package Manager plugin for xfce4-pan
p   xfce4-systemload-plugin         - system load monitor plugin for the Xfce4 p
p   xfce4-terminal                  - Xfce terminal emulator                    
p   xfce4-time-out-plugin           - time out plugin for the Xfce4 panel       
p   xfce4-timer-plugin              - timer plugin for Xfce panel               
p   xfce4-utils                     - Various tools for Xfce                    
p   xfce4-verve-plugin              - Verve (command line) plugin for Xfce 4.4 p
p   xfce4-volstatus-icon            - xfce systray icon for ejecting removable v
p   xfce4-wavelan-plugin            - wavelan status plugin for the Xfce4 panel 
p   xfce4-weather-plugin            - weather information plugin for the Xfce4 p
p   xfce4-wmdock-plugin             - Compatibility layer for running WindowMake
p   xfce4-xfapplet-plugin           - Gnome applets plugin for Xfce panel       
p   xfce4-xkb-plugin                - xkb layout switch plugin for the Xfce4 pan
p   xfig                            - Facility for Interactive Generation of fig
p   xfig-doc                        - XFig on-line documentation and examples   
p   xfig-libs                       - XFig image libraries and examples         
p   xfingerd                        - BSD-like finger daemon with qmail support 
p   xfireworks                      - Fireworks in your root window             
p   xfishtank                       - turns your X root into an aquarium        
p   xflip                           - programs to mirror-image or melt your disp
p   xfmedia                         - Xfce media player                         
p   xfmedia-dbg                     - Xfce media player, debugging symbols      
p   xfmedia-dev                     - The Xfmedia development files             
p   xfmedia-remote-plugin           - Xfmedia Remote control plugin             
v   xfntbig5p-cmex24m               -                                           
i   xfonts-100dpi                   - 100 dpi fonts for X                       
p   xfonts-100dpi-transcoded        - 100 dpi fonts for X (transcoded from ISO 1
i   xfonts-75dpi                    - 75 dpi fonts for X                        
p   xfonts-75dpi-transcoded         - 75 dpi fonts for X (transcoded from ISO 10
v   xfonts-arphic-bkai00mp          -                                           
v   xfonts-arphic-bsmi00lp          -                                           
v   xfonts-arphic-gbsn00lp          -                                           
v   xfonts-arphic-gkai00mp          -                                           
p   xfonts-bitmap-mule              - fonts of BITMAP-MULE for X                
p   xfonts-biznet-100dpi            - 100 dpi BIZNET ISO-8859-2 fonts for X serv
p   xfonts-biznet-75dpi             - 75 dpi BIZNET ISO-8859-2 fonts for X serve
p   xfonts-biznet-base              - Standard BIZNET ISO-8859-2 fonts for X ser
p   xfonts-bolkhov-75dpi            - 75 dpi Unicode Cyrillic fonts for X (Cyr-R
p   xfonts-bolkhov-cp1251-75dpi     - 75 dpi CP1251 encoded Cyrillic fonts for X
p   xfonts-bolkhov-cp1251-misc      - Character-cell CP1251 encoded Cyrillic fon
p   xfonts-bolkhov-isocyr-75dpi     - 75 dpi ISO 8859-5 encoded Cyrillic fonts f
p   xfonts-bolkhov-isocyr-misc      - Character-cell ISO-8859-5 encoded Cyrillic
p   xfonts-bolkhov-koi8r-75dpi      - 75 dpi KOI8-R encoded Cyrillic fonts for X
p   xfonts-bolkhov-koi8r-misc       - Character-cell KOI8-R encoded Cyrillic fon
p   xfonts-bolkhov-koi8u-75dpi      - 75 dpi KOI8-U encoded Cyrillic fonts for X
p   xfonts-bolkhov-koi8u-misc       - Character-cell KOI8-U encoded Cyrillic fon
p   xfonts-bolkhov-misc             - Character-cell Unicode Cyrillic fonts for 
p   xfonts-cmex-big5p               - Big5+ Chinese Mingti bitmap font (by CMEX 
p   xfonts-cronyx-100dpi            - 100 dpi Unicode Cyrillic fonts for X (Cron
p   xfonts-cronyx-75dpi             - 75 dpi Unicode Cyrillic fonts for X (Crony
p   xfonts-cronyx-cp1251-100dpi     - 100 dpi CP1251 encoded Cyrillic fonts for 
p   xfonts-cronyx-cp1251-75dpi      - 75 dpi CP1251 encoded Cyrillic fonts for X
p   xfonts-cronyx-cp1251-misc       - Character-cell CP1251 encoded Cyrillic fon
p   xfonts-cronyx-isocyr-100dpi     - 100 dpi ISO 8859-5 encoded Cyrillic fonts 
p   xfonts-cronyx-isocyr-75dpi      - 75 dpi ISO 8859-5 encoded Cyrillic fonts f
p   xfonts-cronyx-isocyr-misc       - Character-cell ISO-8859-5 encoded Cyrillic
p   xfonts-cronyx-koi8r-100dpi      - 100 dpi KOI8-R encoded Cyrillic fonts for 
p   xfonts-cronyx-koi8r-75dpi       - 75 dpi KOI8-R encoded Cyrillic fonts for X
p   xfonts-cronyx-koi8r-misc        - Character-cell KOI8-R encoded Cyrillic fon
p   xfonts-cronyx-koi8u-100dpi      - 100 dpi KOI8-U encoded Cyrillic fonts for 
p   xfonts-cronyx-koi8u-75dpi       - 75 dpi KOI8-U encoded Cyrillic fonts for X
p   xfonts-cronyx-koi8u-misc        - Character-cell KOI8-U encoded Cyrillic fon
p   xfonts-cronyx-misc              - Character-cell Unicode Cyrillic fonts for 
p   xfonts-cyrillic                 - Cyrillic fonts for X                      
p   xfonts-efont-unicode            - /efont/ Unicode fonts for X which cover va
p   xfonts-efont-unicode-ib         - /efont/ Unicode fonts for X (italic and bo
i   xfonts-encodings                - Encodings for X.Org fonts                 
p   xfonts-intl-arabic              - International fonts for X -- Arabic       
p   xfonts-intl-asian               - International fonts for X -- Asian        
p   xfonts-intl-chinese             - International fonts for X -- Chinese      
p   xfonts-intl-chinese-big         - International fonts for X -- Chinese big  
p   xfonts-intl-european            - International fonts for X -- European     
p   xfonts-intl-japanese            - International fonts for X -- Japanese     
p   xfonts-intl-japanese-big        - International fonts for X -- Japanese big 
p   xfonts-intl-phonetic            - International fonts for X -- Phonetic Alph
p   xfonts-jisx0213                 - JIS X 0213 Japanese Kanji bitmap fonts for
p   xfonts-knickers                 - Knickers font for X                       
p   xfonts-marumoji                 - Roundish fonts (marumoji fonts) for X     
p   xfonts-shinonome                - Various 12,14,16 dot Japanese Kanji, iso88
p   xfonts-terminus                 - Fixed-width fonts for fast reading        
p   xfonts-terminus-dos             - Fixed-width fonts for DOS encodings       
p   xfonts-terminus-oblique         - Oblique version of the Terminus font      
p   xfonts-thai                     - A collection of Thai fonts for X          
p   xfonts-thai-etl                 - Thai etl fonts for X                      
p   xfonts-thai-manop               - Dr.Manop Wongsaisuwan's bitmap fonts for X
p   xfonts-thai-nectec              - Thai fixed fonts for X from Nectec        
p   xfonts-thai-poonlap             - Poonlap Veerathanabutr bitmap fonts for X 
p   xfonts-thai-vor                 - Voradesh Yenbut bitmap fonts for X        
p   xfonts-tipa                     - X11 PostScript Type 1 font for the Phoneti
p   xfonts-unifont                  - PCF (bitmap) version of the GNU Unifont   
i   xfonts-utils                    - X Window System font utility programs     
p   xfonts-x3270-misc               - Font files for the x3270(1) IBM 3270 emula
p   xfprint4                        - Printer GUI for Xfce4                     
p   xfractint                       - UNIX-based fractal generator              
v   xfree86-driver-synaptics        -                                           
p   xfrisk                          - Server and X11 client for playing risk wit
p   xfslibs-dev                     - XFS filesystem-specific static libraries a
p   xfswitch-plugin                 - fast user switching plugin for the Xfce pa
p   xgdvi                           - a TeX DVI previewer for X, with a nice GTK
p   xgnokii                         - Datasuite for mobile phone management (X i
p   xgridfit                        - a program for gridfitting, or "hinting," T
p   xgridfit-doc                    - Documentation for xgridfit                
p   xicc                            - set the ICC colour profile for an X displa
v   ximian-connector                -                                           
v   ximian-setup-tools              -                                           
p   xindy                           - index generator for structured documents l
p   xindy-rules                     - rule files for xindy                      
p   xine-console                    - the xine video player, user interface     
p   xine-dbg                        - the xine video player, debug symbols      
p   xine-plugin                     - xine-based media player plugin for Mozilla
i A xine-ui                         - the xine video player, user interface     
p   xineliboutput-fbfe              - Remote Framebuffer frontend for vdr-plugin
p   xineliboutput-sxfe              - Remote X-Server frontend for vdr-plugin-xi
p   xinetd                          - replacement for inetd with many enhancemen
i   xinit                           - X server initialisation tool              
i   xinput                          - Runtime configuration and test of XInput d
p   xinv3d                          - 3D space invaders for X                   
p   xiphos                          - environment for Bible reading, study, and 
p   xiphos-data                     - data files for Xiphos Bible study software
p   xipmsg                          - A pop up style message communication softw
p   xiterm                          - internationalized terminal emulator for X 
p   xiterm+thai                     - X terminal program with Thai languague sup
p   xjdic                           - Japanese-English dictionary search program
p   xjig                            - An X11 jigsaw puzzle                      
p   xlassie                         - Dockable mail notifier w/ message count & 
p   xlbiff                          - X Literate Biff. Displays From and Subject
p   xli                             - command line tool for viewing images in X1
p   xlibmesa-gl                     - transitional package for Debian etch      
p   xlibmesa-gl-dev                 - transitional package for Debian etch      
p   xlibmesa-glu                    - transitional package for Debian etch      
v   xlibmesa-glu-dev                -                                           
v   xlibosmesa-dev                  -                                           
p   xloadimage                      - Graphics file viewer under X11            
p   xmail                           - advanced, fast and reliable ESMTP/POP3 mai
p   xmail-doc                       - documentation for xmail                   
p   xmaxima                         - A computer algebra system -- x interface  
p   xmille                          - The classic game of Mille Bournes         
p   xmix                            - X11-based interface to the Linux sound dri
v   xml-i18n-tools                  -                                           
p   xml-resume-library              - A set of tools for writing a resume in XML
p   xml-rpc-api2cpp                 - Generate C++ wrapper classes for XML-RPC s
p   xml-rpc-api2txt                 - Dump an XML-RPC API as a text file        
p   xml-twig-tools                  - Command line tools for processing XML docu
p   xmldiff                         - tree to tree correction between xml docume
p   xmldiff-xmlrev                  - xmldiff output formatter                  
p   xmlindent                       - XML stream reformatter                    
p   xmltooling-schemas              - XML schemas for XMLTooling                
p   xmltv-gui                       - Graphical user interface related to the XM
p   xmltv-util                      - Utilities related to the XMLTV file format
p   xmms2-client-avahi              - XMMS2 - avahi client                      
p   xmms2-client-cli                - XMMS2 - cli client                        
p   xmms2-client-medialib-updater   - XMMS2 - medialib-updater client           
p   xmms2-client-nycli              - XMMS2 - new cli client                    
p   xmms2-client-vis                - XMMS2 - visualization clients             
p   xmms2-icon                      - XMMS2 - icon package                      
p   xmms2-plugin-airplay            - XMMS2 - airplay output plug-in            
p   xmms2-plugin-all                - XMMS2 - all plug-ins                      
p   xmms2-plugin-alsa               - XMMS2 - ALSA output                       
p   xmms2-plugin-ao                 - XMMS2 - libao output plug-in              
p   xmms2-plugin-apefile            - XMMS2 - Monkey's Audio decoder plug-in    
p   xmms2-plugin-asf                - XMMS2 - ASF plug-in                       
p   xmms2-plugin-asx                - XMMS2 - ASX playlist plug-in              
p   xmms2-plugin-avcodec            - XMMS2 - avcodec decoder                   
p   xmms2-plugin-cdda               - XMMS2 - CDDA plug-in                      
p   xmms2-plugin-cue                - XMMS2 - CUE playlist plug-in              
p   xmms2-plugin-curl               - XMMS2 - curl transport for HTTP           
p   xmms2-plugin-daap               - XMMS2 - daap plug-in                      
p   xmms2-plugin-faad               - XMMS2 - faad decoder                      
p   xmms2-plugin-flac               - XMMS2 - FLAC decoder                      
p   xmms2-plugin-flv                - XMMS2 - Flash Video plug-in               
p   xmms2-plugin-gme                - XMMS2 - gme plug-in                       
p   xmms2-plugin-gvfs               - XMMS2 - gvfs plug-in                      
p   xmms2-plugin-html               - XMMS2 - HTML playlist plug-in             
p   xmms2-plugin-ices               - XMMS2 - Ogg streaming output              
p   xmms2-plugin-icymetaint         - XMMS2 - shoutcast metadata plug-in        
p   xmms2-plugin-id3v2              - XMMS2 - ID3v2 plug-in                     
p   xmms2-plugin-jack               - XMMS2 - JACK output                       
p   xmms2-plugin-karaoke            - XMMS2 - karaoke plug-in                   
p   xmms2-plugin-m3u                - XMMS2 - M3U playlist plug-in              
p   xmms2-plugin-mad                - XMMS2 - libmad based mp3 decoder          
p   xmms2-plugin-mms                - XMMS2 - MMS transport                     
p   xmms2-plugin-modplug            - XMMS2 - modplug decoder                   
p   xmms2-plugin-mp4                - XMMS2 - MPEG-4 plug-in                    
p   xmms2-plugin-mpg123             - XMMS2 - libmpg123 based mp3 decoder       
p   xmms2-plugin-musepack           - XMMS2 - mpc decoder                       
p   xmms2-plugin-normalize          - XMMS2 - Normalize plug-in                 
p   xmms2-plugin-ofa                - XMMS2 - Open Fingerprint Architecture plug
p   xmms2-plugin-oss                - XMMS2 - OSS output                        
p   xmms2-plugin-pls                - XMMS2 - PLS playlist plug-in              
p   xmms2-plugin-pulse              - XMMS2 - PulseAudio output plug-in         
p   xmms2-plugin-rss                - XMMS2 - RSS podcast plug-in               
p   xmms2-plugin-sid                - XMMS2 - libsidplay2 based decoder         
p   xmms2-plugin-smb                - XMMS2 - Samba transport                   
p   xmms2-plugin-speex              - XMMS2 - Speex decoder                     
p   xmms2-plugin-tta                - XMMS2 - TTA decoder plug-in               
p   xmms2-plugin-vocoder            - XMMS2 - vocoder plug-in                   
p   xmms2-plugin-vorbis             - XMMS2 - vorbis decoder                    
p   xmms2-plugin-wavpack            - XMMS2 - WavPack decoder plug-in           
p   xmms2-plugin-wma                - XMMS2 - wma decoder                       
p   xmms2-plugin-xml                - XMMS2 - XML plug-in                       
p   xmms2-plugin-xspf               - XMMS2 - XSPF playist plug-in              
p   xmountains                      - Fractal landscape generator for X         
p   xmp-audacious                   - An XMP plugin for Audacious               
p   xmpi                            - a graphical user interface for MPI program
p   xnecview                        - NEC structure and gain pattern viewer     
p   xnetcardconfig                  - A simple network card configuration wizard
p   xoids                           - Asteroids game with powerups and color gra
p   xonix                           - Carve up the screen whilst dodging monster
v   xorg-build-macros               -                                           
p   xorg-driver-fglrx               - Video driver for the ATI graphics accelera
p   xorg-driver-fglrx-dev           - Video driver for the ATI graphics accelera
v   xorg-driver-synaptics           -                                           
p   xorg-options-editor-gtk         - Editor for xorg.conf files                
p   xorriso                         - command line iso9660+RR manipulation tool 
p   xosd-bin                        - X On-Screen Display library - binary files
p   xosview                         - X based system monitor                    
p   xpaint                          - simple paint program for X                
p   xpdf-chinese-simplified         - Portable Document Format (PDF) suite -- si
p   xpdf-chinese-traditional        - Portable Document Format (PDF) suite -- tr
p   xpdf-utils                      - Portable Document Format (PDF) suite -- ut
p   xpenguins                       - little penguins walk on your windows      
p   xpenguins-applet                - GNOME2 panel applet implementation of xpen
p   xpilot-extra                    - Maps, utilities and configs for XPilot    
p   xpilot-ng                       - Multi-player tactical game for X (NG versi
p   xpilot-ng-client-sdl            - Client for XPilot NG                      
p   xpilot-ng-client-x11            - Client for XPilot NG                      
p   xpilot-ng-common                - Common files for XPilot NG                
p   xpilot-ng-server                - Server for hosting XPilot NG games        
p   xpilot-ng-utils                 - Utilities for XPilot NG                   
p   xplanet-images                  - imagery for xplanet                       
p   xpm2wico                        - An Xpm to Windows .ico converter          
p   xpmutils                        - X11 pixmap utilities                      
p   xpostit                         - simple postit program on X with I18N suppo
p   xprint-utils                    - utilities for Xprint, the X11 print system
p   xprintidle                      - Small utility that prints user's idle time
p   xprintmon                       - graphical print queue monitor for lprng   
p   xqilla                          - XQuery and XPath 2.0 command line interpre
p   xringd                          - extended ring daemon - monitor phone rings
v   xserver-xorg-input-4            -                                           
p   xserver-xorg-input-acecad       - X.Org X server -- AceCad input driver     
p   xserver-xorg-input-aiptek       - X.Org X server -- Aiptek input driver     
i   xserver-xorg-input-all          - the X.Org X server -- input driver metapac
p   xserver-xorg-input-elographics  - X.Org X server -- ELOGraphics input driver
i   xserver-xorg-input-evdev        - X.Org X server -- evdev input driver      
p   xserver-xorg-input-evtouch      - Touchscreen-Driver for X.Org/XFree86 serve
p   xserver-xorg-input-fpit         - X.Org X server -- FPIT input driver       
p   xserver-xorg-input-joystick     - X.Org X server -- joystick input driver   
p   xserver-xorg-input-kbd          - X.Org X server -- keyboard input driver   
i   xserver-xorg-input-mouse        - X.Org X server -- mouse input driver      
p   xserver-xorg-input-mutouch      - X.Org X server -- muTouch input driver    
p   xserver-xorg-input-penmount     - X.Org X server -- Penmount input driver   
i   xserver-xorg-input-synaptics    - Synaptics TouchPad driver for X.Org server
p   xserver-xorg-input-tslib        - tslib touchscreen driver for X.Org/XFree86
i   xserver-xorg-input-vmmouse      - X.Org X server -- VMMouse input driver to 
p   xserver-xorg-input-void         - X.Org X server -- void input driver       
i   xserver-xorg-input-wacom        - X.Org X server -- Wacom input driver      
v   xserver-xorg-video-5            -                                           
i   xserver-xorg-video-all          - the X.Org X server -- output driver metapa
i   xserver-xorg-video-apm          - X.Org X server -- APM display driver      
i   xserver-xorg-video-ark          - X.Org X server -- ark display driver      
i   xserver-xorg-video-ati          - X.Org X server -- ATI display driver wrapp
p   xserver-xorg-video-ati-dbg      - X.Org X server -- ATI display driver wrapp
i   xserver-xorg-video-chips        - X.Org X server -- Chips display driver    
i   xserver-xorg-video-cirrus       - X.Org X server -- Cirrus display driver   
p   xserver-xorg-video-dummy        - X.Org X server -- dummy display driver    
i   xserver-xorg-video-fbdev        - X.Org X server -- fbdev display driver    
p   xserver-xorg-video-glint        - X.Org X server -- Glint display driver    
i   xserver-xorg-video-i128         - X.Org X server -- i128 display driver     
p   xserver-xorg-video-i740         - X.Org X server -- i740 display driver     
i   xserver-xorg-video-intel        - X.Org X server -- Intel i8xx, i9xx display
p   xserver-xorg-video-intel-dbg    - X.Org X server -- Intel i8xx, i9xx display
p   xserver-xorg-video-ivtv         - X.Org X server -- IVTV display driver     
p   xserver-xorg-video-ivtv-dbg     - X.Org X server -- IVTV display driver (deb
i   xserver-xorg-video-mach64       - X.Org X server -- ATI Mach64 display drive
p   xserver-xorg-video-mach64-dbg   - X.Org X server -- ATI display driver (debu
i   xserver-xorg-video-mga          - X.Org X server -- MGA display driver      
i   xserver-xorg-video-neomagic     - X.Org X server -- Neomagic display driver 
p   xserver-xorg-video-nouveau      - X.Org X server -- Nouveau display driver (
i   xserver-xorg-video-nv           - X.Org X server -- NV display driver       
i   xserver-xorg-video-openchrome   - X.Org X server -- VIA display driver      
i   xserver-xorg-video-r128         - X.Org X server -- ATI r128 display driver 
p   xserver-xorg-video-r128-dbg     - X.Org X server -- ATI r128 display driver 
i   xserver-xorg-video-radeon       - X.Org X server -- ATI Radeon display drive
p   xserver-xorg-video-radeon-dbg   - X.Org X server -- ATI Radeon display drive
p   xserver-xorg-video-radeonhd     - X.Org X server -- AMD/ATI r5xx, r6xx displ
p   xserver-xorg-video-radeonhd-dbg - X.Org X server -- AMD/ATI r5xx, r6xx displ
i   xserver-xorg-video-rendition    - X.Org X server -- Rendition display driver
i   xserver-xorg-video-s3           - X.Org X server -- legacy S3 display driver
i   xserver-xorg-video-s3virge      - X.Org X server -- S3 ViRGE display driver 
i   xserver-xorg-video-savage       - X.Org X server -- Savage display driver   
i   xserver-xorg-video-siliconmotio - X.Org X server -- SiliconMotion display dr
i   xserver-xorg-video-sis          - X.Org X server -- SiS display driver      
i   xserver-xorg-video-sisusb       - X.Org X server -- SiS USB display driver  
i   xserver-xorg-video-tdfx         - X.Org X server -- tdfx display driver     
i   xserver-xorg-video-trident      - X.Org X server -- Trident display driver  
i   xserver-xorg-video-tseng        - X.Org X server -- Tseng display driver    
i   xserver-xorg-video-v4l          - X.Org X server -- Video 4 Linux display dr
i   xserver-xorg-video-vesa         - X.Org X server -- VESA display driver     
p   xserver-xorg-video-via          - X.Org X server -- VIA display driver (dumm
i   xserver-xorg-video-vmware       - X.Org X server -- VMware display driver   
i   xserver-xorg-video-voodoo       - X.Org X server -- Voodoo display driver   
p   xsettings-kde                   - XSettings daemon for KDE                  
p   xshisen                         - Shisen-sho puzzle game for X11            
p   xshogi                          - An X Window System Japanese Chess (Shogi) 
p   xsidplay                        - Music player for tunes from C64           
p   xsoldier                        - shoot 'em up game with the "not shooting" 
p   xstarfish                       - X wallpaper generator                     
p   xsynth-dssi                     - classic-analog (VCOs-VCF-VCA) style softwa
p   xsysinfo                        - display some Linux kernel parameters in gr
p   xtail                           - like "tail -f", but works on truncated fil
p   xtide                           - provides tide and current predictions     
p   xtide-coastline                 - coastline data for xtide                  
p   xtide-data                      - Harmonics data for xtide                  
p   xtide-data-nonfree              - Harmonics data for xtide (Canada, Netherla
p   xtightvncviewer                 - virtual network computing client software 
p   xtoolwait                       - Allows to start X applications serially   
p   xtradius                        - Free radius server implementation         
p   xtris                           - client-server multiplayer X tetris        
p   xttitle                         - Changes X terminal emulator window titles 
p   xtux-client                     - arcade game featuring Free Software mascot
p   xubuntu-default-settings        - default settings for Xubuntu              
p   xubuntu-restricted-extras       - Commonly used restricted packages         
p   xul-ext-all-in-one-sidebar      - A sidebar extension for Iceweasel/Firefox 
v   xul-ext-bindwood                -                                           
p   xul-ext-firebug                 - web development plugin for Firefox        
v   xul-ext-prism                   -                                           
v   xul-ext-speeddial               -                                           
p   xul-ext-ubuntu-it-menu          - Firefox extension for a quick browse of Ub
p   xulrunner-1.9.1-testsuite       - Test Suite from XULRunner 1.9.1           
p   xulrunner-1.9.1-testsuite-dev   - Test Suite development files for XULRunner
p   xulrunner-1.9.2-testsuite       - Test Suite from XULRunner 1.9.2           
p   xulrunner-1.9.2-testsuite-dev   - Test Suite development files for XULRunner
p   xutils                          - X Window System utility programs metapacka
p   xutils-dev                      - X Window System utility programs for devel
p   xvid4conf                       - creates XviD configuration files          
p   xvidcap                         - Screen video capture for X                
p   xvidenc                         - shell script to encode DVDs to Xvid       
p   xvier                           - a "Four in a row" game                    
p   xview-clients                   - XView client programs                     
p   xview-examples                  - XView contrib programs                    
p   xviewg                          - XView shared libraries                    
p   xviewg-dev                      - XView development tools                   
p   xvile                           - VI Like Emacs - vi work-alike (X11)       
p   xvnc4viewer                     - Virtual network computing client software 
p   xwelltris                       - 3D Tetris like popular game similar to Wel
p   xwit                            - a collection of simple routines to call so
p   xwrits                          - reminds you to take a break from typing   
p   xxdiff                          - graphical file/directory comparison and me
p   xxdiff-scripts                  - graphical file/directory comparison and me
p   xymon-client                    - client for the Xymon network monitor      
p   xz-utils                        - high compression-ratio compressor         
p   xzip                            - Interpreter of Infocom-format story-files 
p   yabasic                         - Yet Another BASIC interpreter             
p   yacpi                           - ncurses based acpi monitor for text mode  
p   yagiuda                         - software to analyse performance of Yagi-Ud
p   yaird                           - Yet Another mkInitRD                      
v   yale-viewer                     -                                           
p   yamdi                           - a utility for adding metadata to flash vid
p   yapps2-runtime                  - Yet Another Python Parser System          
p   yardradius                      - YARD Radius Authorization and Accounting S
p   yasnippet                       - A template system for Emacs               
p   yaws-mail                       - Webmail application for Yaws web server   
p   yaws-wiki                       - Wiki application for Yaws web server      
p   yaz-icu                         - command line utility for ICU utilities of 
p   yaz-illclient                   - utility for ISO ILL of YAZ                
p   ydpdict                         - interface for Collins and Langenscheidt di
p   yersinia                        - Network vulnerabilities check software    
p   yics                            - Yahoo! Chess client for use with FICS inte
p   yiff-server                     - Y Sound Server                            
p   yiyantang                       - Terminal-based Chinese automatic encoding 
p   yokadi                          - command line TODO list tool               
p   yorick                          - interpreted language and scientific graphi
p   yorick-cubeview                 - a 3D FITS data viewer specialized in spect
p   yorick-curses                   - interface to the (n)curses library for the
p   yorick-data                     - interpreted library for the Yorick languag
p   yorick-dev                      - development files for the Yorick interpret
p   yorick-doc                      - documentation for the Yorick interpreted l
p   yorick-gl                       - OpenGL 3D graphics support for the Yorick 
p   yorick-hdf5                     - Hierarchical Data Format 5 interface for t
p   yorick-imutil                   - fast image manipulation routines for the Y
p   yorick-ml4                      - Matlab file format support for the Yorick 
p   yorick-soy                      - sparse matrix operations for the Yorick la
p   yorick-spydr                    - FITS image display and simple analysis    
p   yorick-yao                      - a Yorick-based adaptive optics system simu
p   yorick-yeti                     - utility plugin for the Yorick language    
p   yorick-yeti-fftw                - FFT plugin for the Yorick language        
p   yorick-yeti-gsl                 - GSL special functions plugin for the Yoric
p   yorick-yeti-regex               - POSIX regular expressions for the Yorick l
p   yorick-yeti-tiff                - TIFF image format input for the Yorick lan
p   yorick-yutils                   - various utilities for the Yorick language 
p   yorick-z                        - zlib, jpeg and png support for the Yorick 
p   ypsilon                         - R6RS Scheme implementation with concurrent
p   yudit                           - Unicode text editor (arch-dependent binari
p   yudit-common                    - Unicode text editor (arch-independent file
p   yudit-doc                       - Unicode text editor (Documentation)       
p   z8530-utils2                    - Utilities for Z8530 based HDLC cards for A
p   z88dk-bin                       - executable files for z88dk                
p   zabbix-agent                    - network monitoring solution - agent       
p   zabbix-frontend-php             - network monitoring solution - PHP front-en
p   zabbix-proxy-mysql              - network monitoring solution - proxy (using
p   zabbix-proxy-pgsql              - network monitoring solution - proxy (using
p   zabbix-server-mysql             - network monitoring solution - server (usin
p   zabbix-server-pgsql             - network monitoring solution - server (usin
p   zanshin                         - Todo List Manager                         
p   zapping                         - television viewer for the GNOME environmen
v   zcode-interpreter               -                                           
p   zeitgeist-core                  - activity logging service                  
p   zekr-quran-translations-en      - Zekr Quran English translations           
p   zend-framework-bin              - a simple, straightforward, open-source sof
i   zenity                          - Display graphical dialog boxes from shell 
p   zephyr-clients                  - Project Athena's notification service - cl
v   zeroc-ice                       -                                           
p   zeroc-ice-manual                - Ice documentation in pdf                  
p   zeroc-ice33                     - Internet Communications Engine            
p   zeroc-icee                      - Embedded edition of the ZeroC Ice         
p   zeroinstall-injector            - run programs by URL                       
p   zile                            - very small Emacs-subset editor            
p   zim                             - graphical text editor based on wiki techno
p   zimpl                           - mathematical modeling language for optimiz
p   zinnia-utils                    - utils for the zinnia library              
i   zip                             - Archiver for .zip files                   
p   zipcmp                          - compare contents of zip archives          
p   zipmerge                        - merge zip archives                        
p   zipper.app                      - Tool for inspecting the contents of a comp
p   ziproxy                         - compressing HTTP proxy server             
p   zivot                           - the game of life, simple console version  
p   zlib-bin                        - compression library - sample programs     
p   zlib-gst                        - Zlib bindings for GNU Smalltalk           
i   zlib1g                          - compression library - runtime             
p   zlib1g-dbg                      - compression library - development         
idA zlib1g-dev                      - compression library - development         
p   zlibc                           - An on-fly auto-uncompressing C library    
p   znc-webadmin                    - an advanced IRC bouncer (webadmin module) 
p   zoidberg                        - modular Perl shell                        
p   zonecheck-cgi                   - A DNS configuration checker, Web interface
p   zoneminder                      - Linux video camera security and surveillan
p   zope-atextensions               - Extensions to Archetypes in Zope          
p   zope-cmfbibliographyat          - A Bibliography management product for Zope
p   zope-cookiecrumbler             - Use cookies even when folder doesn't suppo
v   zope-docfindereverywhere        -                                           
p   zope-docfindertab               - Find documentation for a Zope product usin
p   zope-externaleditor             - Zope External Editor                      
p   zope-ldapmultiplugins           - LDAP plugin for Zope/Plone                
p   zope-linguaplone                - multilingual and translation solution for 
p   zope-maildrophost               - send mails from within Zope through a mail
p   zope-scriptablefields           - Zope tool bundle for working with componen
p   zope-textindexng3               - full text index for Zope objects          
p   zope-textindexng3-lib           - full text index for Zope objects          
p   zope-tinytableplus              - Present tabular data in Zope              
p   zope-zwiki                      - WikiWikiWeb implementation for Zope       
p   zopeedit                        - Helper Application for Zope External Edito
p   zsh-static                      - A shell with lots of features (static link
p   zvbi                            - Vertical Blanking Interval (VBI) utilities
p   zziplib-bin                     - library providing read access on ZIP-archi
carlos@carlos1-desktop:~$ 

And then I typed this with the ethernet connection on

carlos@carlos1-desktop:~$ [COLOR=Blue]sudo apt-get install linux-firmware[/COLOR]
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
[COLOR=Red]linux-firmware ya está en su versión más reciente.
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  libssl-dev zlib1g-dev[/COLOR]
Utilice «apt-get autoremove» para eliminarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 2 no actualizados.
carlos@carlos1-desktop:~$ 

I translate the result for you
[COLOR=Red]Linux-firmware is already the most recent version
The next packages were  automatically installed and they are not necesary 
[/COLOR][COLOR=Red]  libssl-dev zlib1g-dev
Use «apt-get autoremove» to eliminate them[/COLOR]

---

### Post by chili555 on 2010-09-30
> arlos@carlos1-desktop:~$ sudo aptitude search linux-firmware
[sudo] password for carlos:
[COLOR="Red"]**i** linux-firmware[/COLOR] - Firmware for Linux kernel drivers
p linux-firmware-nonfree - Non-free firmware for Linux kernel driversThere is the answer; the **i** indicates **installed**.

It also indicates that firmware is not the problem.

Please detach the ethernet cable and reboot. Run these commands:```
iwconfig
dmesg | grep r819
```Post the result and let's see if the wireless springs to life.

---

### Post by cavalgar69 on 2010-09-30
These are the results:

carlos@carlos1-desktop:~$ [COLOR=Blue]iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.


carlos@carlos1-desktop:~$ [COLOR=Blue]dmesg | grep r819iww[/COLOR]
carlos@carlos1-desktop:~$

After that nothing has happened.

---

### Post by ANew on 2010-09-30
It works with differernt driver 8712u.ko

[http://ubuntuforums.org/showthread.php?t=1555203](http://ubuntuforums.org/showthread.php?t=1555203)

---

### Post by chili555 on 2010-09-30
> carlos@carlos1-desktop:~$ dmesg | grep r819iww
carlos@carlos1-desktop:~$The command is actually:```
dmesg | grep r819
```Please redo.

---

### Post by cavalgar69 on 2010-09-30
With the ethernet cable unplugged I did this

carlos@carlos1-desktop:~$ [COLOR=Blue]iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

carlos@carlos1-desktop:~$[COLOR=Blue] dmesg | grep r819[/COLOR]
[   21.806326] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[ 4497.981493] Modules linked in: ndiswrapper(+) nls_iso8859_1 nls_cp437 isofs vfat fat udf crc_itu_t binfmt_misc nfsd exportfs nfs lockd nfs_acl auth_rpcgss snd_hda_codec_realtek r8192s_usb(C) ieee80211_rsl(C) sunrpc ieee80211_crypt_ccmp(C) ieee80211_crypt_tkip(C) ieee80211_crypt_wep(C) ieee80211_crypt(C) ppdev snd_hda_intel snd_hda_codec snd_hwdep amd64_edac_mod parport_pc psmouse serio_raw lp parport snd_pcm_oss snd_mixer_oss edac_core snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device i2c_piix4 snd soundcore snd_page_alloc k8temp iptable_filter ip_tables x_tables nvidia(P) dm_raid45 xor usb_storage usbhid tg3 floppy

carlos@carlos1-desktop:~$[COLOR=Blue] iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

carlos@carlos1-desktop:~$

---

### Post by chili555 on 2010-09-30
> Modules linked in: ndiswrapperI wonder if ndiswrapper is fighting us. Please do:```
ndiswrapper -l
```Whatever driver you find, net8192su perhaps, use in the next command:```
sudo ndiswrapper -e net8192su   <==or whatever you found
```Now do:```
sudo rmmod -f ndiswrapper
sudo rmmod -f r8192s_usb
sudo modprobe r8192s_usb
iwconfig
```Let me know the result.

---

### Post by cavalgar69 on 2010-09-30
Here we go
carlos@carlos1-desktop:~$ [COLOR=Blue]ndiswrapper -l[/COLOR]
net8192su : driver installed

carlos@carlos1-desktop:~$ [COLOR=Blue]sudo ndiswrapper -e net8192su[/COLOR]
[sudo] password for carlos: 

carlos@carlos1-desktop:~$ [COLOR=Blue]sudo rmmod -f ndiswrapper[/COLOR]

carlos@carlos1-desktop:~$ [COLOR=Blue]sudo rmmod -f r8192s_usb[/COLOR]

carlos@carlos1-desktop:~$ [COLOR=Blue]sudo modprobe r8192s_usb[/COLOR]
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

carlos@carlos1-desktop:~$ [COLOR=Blue]iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

carlos@carlos1-desktop:~$

---

### Post by chili555 on 2010-09-30
I will have to check back tomorrow. See you then.

---

### Post by cavalgar69 on 2010-09-30
Many thanks for your help.
See you tomorrow

---

### Post by cavalgar69 on 2010-10-01
I have been doing some research and I found this. Do you think that can be useful? 
PD I'm aware that this is for Ubuntu 10.04


[http://webcache.googleusercontent.com/search?q=cache:xVXfOLTe7OsJ:mnshankar.wordpress.com/2010/05/08/ubuntu-10-04-lucid-lynx-on-my-optiplex-gx260/+make+work+r8192s_usb+ubuntu+9.10&cd=7&hl=es&ct=clnk&gl=es&client=firefox-a](http://webcache.googleusercontent.com/search?q=cache:xVXfOLTe7OsJ:mnshankar.wordpress.com/2010/05/08/ubuntu-10-04-lucid-lynx-on-my-optiplex-gx260/+make+work+r8192s_usb+ubuntu+9.10&cd=7&hl=es&ct=clnk&gl=es&client=firefox-a)

Richard Keefer says:		 		 		[ 			May 28, 2010 at 12:11 pm]("http://mnshankar.wordpress.com/2010/05/08/ubuntu-10-04-lucid-lynx-on-my-optiplex-gx260/#comment-115")		
  		On the Realtek wifi, I found this didn’t **work**, and that nothing would **make** the driver supplied with 10.04 **work**. Instead, I downloaded RTLl8192SU_usb_linux_v2.6.0006.20100511.zip directly from Realtek (extract, **make**, sudo su, **make** install, sudo modprobe 8712u, **make**  clean, sudo gedit “8712u” into listing of /etc/modules). Best to  copy  rtl8192sfw from /lib/firmware/RTL8192SE, since this is a later version  (80976 vs. 68368 B of download you list). Some have suggested  blacklisting of native drivers, or hobbling them  (i.e. sudo mv **r8192s_usb**.ko  **r8192s_usb**.ko.bak  in /lib/modules/2.6.32-21-generic/kernel/drivers/staging/rtl8192su/),  since the native driver interferes with the Realtek one.  This seems to  give a stable result. Hope this helps.
 
  		 			[URL="http://mnshankar.wordpress.com/2010/05/08/ubuntu-10-04-lucid-lynx-on-my-optiplex-gx260/?replytocom=115#respond"]
[/URL]

---

### Post by cavalgar69 on 2010-10-01
Sorry I put the wrong link
I think this is the right one

[http://mnshankar.wordpress.com/2010/05/08/ubuntu-10-04-lucid-lynx-on-my-optiplex-gx260/](http://mnshankar.wordpress.com/2010/05/08/ubuntu-10-04-lucid-lynx-on-my-optiplex-gx260/)

---

### Post by chili555 on 2010-10-01
It's certainly worth a try. Do you feel like you can proceed or would you prefer detailed instructions? In order to build the module, you will first need to install *build-essential* and *linux-headers-generic.*

---

### Post by cavalgar69 on 2010-10-01
If you don't mind I would rather to have some guidance, because I am kind of a rookie in Ubuntu. 
Thanks

---

### Post by cavalgar69 on 2010-10-01
Ther is something else. I couldn't find  RTLl8192SU_usb_linux_v2.6.0006.20100511.zip at the Realtek web nor anywhere else on the Internet.

---

### Post by cavalgar69 on 2010-10-01
I checked in    	> System > Administration >Synaptic and I have  *build-essential (v 11.4)* and [I]linux-headers-generic (v 2.6.31.22.35) already installed
[/I]

---

### Post by chili555 on 2010-10-01
> **cavalgar69 said:**
> Sorry I put the wrong link
I think this is the right one

[http://mnshankar.wordpress.com/2010/05/08/ubuntu-10-04-lucid-lynx-on-my-optiplex-gx260/](http://mnshankar.wordpress.com/2010/05/08/ubuntu-10-04-lucid-lynx-on-my-optiplex-gx260/)This link says you do ***not*** have to compile a driver from Realtek. It says:> After some research, I realized that the drivers to run this are already present (I did NOT have to download, and compile the drivers from realtek).. All that is missing is the “firmware”. Click here to download this. Extract it and place it in the /lib/firmware/RTL8192SU directory like so :

    /lib/firmware/RTL8192SU/rtl8192sfw.bin

(If the RTL8192SU directory does not exist, go ahead and create it)

Now, if you insert your mini USB, it should detect the wireless signals around. Please go ahead and download the file he refers to; by default, downloads go to your desktop.

Right-click the file and select 'Extract here.' You will have a file called *rtl8192sfw.bin*. First we will create a folder for it in the correct place. Open a terminal and do:```
sudo mkdir /lib/firmware/RTL8192SU
```Now we will copy the file from your desktop to the new correct folder:```
sudo cp Desktop/rtl8192sfw.bin /lib/firmware/RTL8192SU
```Now, we will make sure it is readable and has the correct owner:```
sudo chmod 644 /lib/firmware/RTL8192SU/*
sudo chown root:root /lib/firmware/RTL8192SU/*
```The wildcard * means perform the change to everything in the folder.

You can check your work with:```
ls -al /lib/firmware/RTL8192SU
```If you have done the steps correctly, it will read:> drwxr-xr-x  2 root root  4096 2010-10-01 20:18 .
drwxr-xr-x 62 root root 20480 2010-10-01 20:17 ..
-rw-r--r--  1 root root 68368 2010-10-01 20:18 rtl8192sfw.bin

Reboot without the ethernet cable and post:```
dmesg | grep r819
iwconfig
```Thanks.

---

### Post by cavalgar69 on 2010-10-01
Hi again. Somehow I already had /lib/firmware/RTL8192SU created and  within it was the file rtl8192sfw.bin so I skiped the two first actions 

Then I did as you said this.


carlos@carlos1-desktop:~$ [COLOR=Blue]sudo chmod 644 /lib/firmware/RTL8192SU/*[/COLOR]

carlos@carlos1-desktop:~$ [COLOR=Blue]sudo chown root:root /lib/firmware/RTL8192SU/*[/COLOR]

carlos@carlos1-desktop:~$ [COLOR=Blue]ls -al /lib/firmware/RTL8192SU[/COLOR]
total 84
drwxr-xr-x  2 root root  4096 2010-10-01 19:10 .
drwxr-xr-x 12 root root 12288 2010-09-30 07:46 ..
-rw-r--r--  1 root root 68368 2010-10-01 19:21 rtl8192sfw.bin
carlos@carlos1-desktop:~$ 

I reboot with the ethernet cable unplugged and did this

carlos@carlos1-desktop:~$ [COLOR=Blue]dmesg | grep r819[/COLOR]
[   21.720129] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.

carlos@carlos1-desktop:~$ [COLOR=Blue]iwconfig[/COLOR]

lo        no wireless extensions.

eth0      no wireless extensions.

carlos@carlos1-desktop:~$

---

### Post by blazemore on 2010-10-05
Try this:
```

echo 'install r8192s_usb modprobe --ignore-install r8192s_usb ; /bin/echo "0bda 8171" > /sys/bus/usb/drivers/rtl819xU/new_id' | sudo tee /etc/modprobe.d/r8192s_usb.conf
sudo ln -s /lib/firmware/RTL8192SE /lib/firmware/RTL8192SU
sudo modprobe -rf r8192s_usb
sudo modprobe r8192s_usb

```

---

