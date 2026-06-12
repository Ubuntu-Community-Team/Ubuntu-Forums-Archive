---
title: "3D effects, desktops lost"
date: 2013-12-06
forum: Multimedia Software
---

### Post by isagarran2 on 2013-12-06
Hello, 
I'm totally lost and I need some help. My computer is no longer working correctly after I installed nvidia-current package and another one using Synaptic. After multiple reboot, I am able to connect to the computer and to have a correct definition of my desktop.
But I lost multiple things :
- Windows are sticked to the edge of the desktop
- I have four desktops using the icon on the launcher (on the left). Before I had eight desktops and I was able to select them on the right side of each desktop.
-  In system => apparence => behaviour tab, there is no possiblity to check "enable desktops". This option doesn't exist
- In system => details => graphic card, I have "experience" and "standard"
- In the summary there is no longere anything written for my graphic card.
I'm using virtualbox and the VMs can no longer start with messages "VM was configured to use 3D acceleration but the 3D support for the host doesn't working properly ..."
I have Ubuntu 12.04
> sudo -u lspci -vnn | egrep "VGA|3D|Display" gives
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09) (prog-if 00 [VGA controller])
I'm totally stuck I would appreciate any help.
regards.
JP

---

### Post by isagarran2 on 2013-12-06
I add this command also
> sudo lshw -C display
  *-display               
       description: VGA compatible controller
       produit: 2nd Generation Core Processor Family Integrated Graphics Controller
       fabriquant: Intel Corporation
       identifiant matériel: 2
       information bus: pci@0000:00:02.0
       version: 09
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       ressources: irq:50 mémoire:f0000000-f03fffff mémoire:e0000000-efffffff portE/S:5000(taille=64)

---

### Post by deadflowr on 2013-12-06
Remove all packages for the nvidia-current.

You are NOT using an nvidia card, so those drivers do you no use.
If you generated an xorg file, then remove that also.

---

### Post by isagarran2 on 2013-12-06
OK, I am going to try. What I saw also is a new process (using top). It's named unity-2D-shell. I am not used to seeing it.
Thanks for your quick reply. I let it know immediatly about the test.
regards.jp

---

### Post by isagarran2 on 2013-12-06
I removed nvidia-current but the behavior is the same. 
In fact I have two processes : unity-2D-panel and unity-2D-shell that are running. Due to their name it seems that I can't activate 3D effects. Perhaps the problem came from that.
Could you tell me how to solve it ?
regards.jps

---

### Post by isagarran2 on 2013-12-06
I ran also 
> /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0".
Error: GLX is not available on the system
So Unity 3D shouldn't be able to run however I had before these problem 3D capabilities. I don't understand. Perhaps. I set Unity instead on anther desktop. It's quite stange.
Let me know if you can help me,
regards.jps

---

### Post by deadflowr on 2013-12-06
Did you reboot?

---

### Post by isagarran2 on 2013-12-07
Yes I did it after rmoval of the nvidia-current package.
regards.jp

---

### Post by deadflowr on 2013-12-07
This might help
[http://askubuntu.com/questions/80914/how-reinstall-the-default-graphics-drivers](http://askubuntu.com/questions/80914/how-reinstall-the-default-graphics-drivers)

---

### Post by isagarran2 on 2013-12-07
Hello,
Thanks for your reply. It seems to match but I have some difficulties to apply it. I ran the command and I got errors because package not found. It should be easy to remove this error but I don't know the command.
Here is the command and the results :
   > sudo lshw -c video 

    *-display                
        description: VGA compatible controller 
        produit: 2nd Generation Core Processor Family Integrated Graphics Controller 
        fabriquant: Intel Corporation 
        identifiant matériel: 2 
        information bus: pci@0000:00:02.0 
        version: 09 
        bits: 64 bits 
        horloge: 33MHz 
        fonctionnalités: msi pm vga_controller bus_master cap_list rom 
        configuration: driver=i915 latency=0 
        ressources: irq:50 mémoire:f0000000-f03fffff mémoire:e0000000-efffffff portE/S:5000(taille=64) 
  
 and
> lspci -n 

 00:00.0 0600: 8086:0104 (rev 09) 
 00:02.0 0300: 8086:0126 (rev 09) 
 00:16.0 0780: 8086:1c3a (rev 04) 
 00:16.3 0700: 8086:1c3d (rev 04) 
 00:19.0 0200: 8086:1502 (rev 04) 
 00:1a.0 0c03: 8086:1c2d (rev 04) 
 00:1b.0 0403: 8086:1c20 (rev 04) 
 00:1c.0 0604: 8086:1c10 (rev b4) 
 00:1c.1 0604: 8086:1c12 (rev b4) 
 00:1c.3 0604: 8086:1c16 (rev b4) 
 00:1c.4 0604: 8086:1c18 (rev b4) 
 00:1c.6 0604: 8086:1c1c (rev b4) 
 00:1d.0 0c03: 8086:1c26 (rev 04) 
 00:1f.0 0601: 8086:1c4f (rev 04) 
 00:1f.2 0106: 8086:1c03 (rev 04) 
 00:1f.3 0c05: 8086:1c22 (rev 04) 
 03:00.0 0280: 8086:0085 (rev 34) 
 0d:00.0 0880: 1180:e822 (rev 08) 
 0d:00.3 0c00: 1180:e832 (rev 04) 
 0e:00.0 0c03: 1033:0194 (rev 04)

Then they told me to run this commands :
   
> sudo apt-get purge nvidia-*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf

There, I got errors :
> sudo apt-get purge nvidia-*
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Note : sélection de nvidia-180-libvdpau-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-173-updates pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-185-libvdpau-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-glx-173-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-persistenced pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-current pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-libvdpau-ia32 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-cuda-debugger pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-libvdpau1 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-glx-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-glx-185-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-173 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-304 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-96-updates-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-319 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-settings-updates pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-settings-304-updates pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-libopencl1-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-settings pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-185-libvdpau pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-libopencl1 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-185-kernel-source pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-vdpau-driver pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-96-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-opencl-profiler pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-cg-toolkit pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-96 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-libvdpau1-ia32 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-glx-96-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-173-updates-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-96-updates pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-experimental-304 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-experimental-310 pour l'expression rationnelle « nvidia-* »
Note : sélection de libkwinactivenvidiahack4 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-glx-173 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-glx-180 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-glx-185 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-prime pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-180-modaliases pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-cuda-profiler pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-current-updates pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-kernel-common pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-opencl-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-current-updates-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de libkwinnvidiahack4 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-opencl-icd pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-libvdpau pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-304-updates-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-319-updates pour l'expression rationnelle « nvidia-* »
Note : sélection de boinc-nvidia-cuda pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-current-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-compute-profiler pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-glx-96 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-experimental-304-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-settings-304 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-settings-319 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-glx-180-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-va-driver pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-current-modaliases pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-173-modaliases pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-185-modaliases pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-319-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-texture-tools pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-304-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-common pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-tegra pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-96-kernel-source pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-settings-319-updates pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-cuda-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-cuda-doc pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-173-kernel-source pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-cuda-gdb pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-304-updates pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-experimental-310-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-180-kernel-source pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-cuda-toolkit pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-libvdpau-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de libgl1-nvidia-alternatives pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-96-modaliases pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-glx pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-settings-experimental-304 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-settings-experimental-310 pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-173-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-319-updates-dev pour l'expression rationnelle « nvidia-* »
Note : sélection de nvidia-180-libvdpau pour l'expression rationnelle « nvidia-* »
Note : sélection de « libnvtt-bin » au lieu de « nvidia-texture-tools »
Note : sélection de « vdpau-va-driver » au lieu de « nvidia-va-driver »
Le paquet nvidia-96-updates n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-96-updates-dev n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-cg-toolkit n'est pas installé, et ne peut donc être supprimé
Le paquet libkwinactivenvidiahack4 n'est pas installé, et ne peut donc être supprimé
Le paquet libkwinnvidiahack4 n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-prime n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-settings n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-settings-304-updates n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-settings-319 n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-settings-319-updates n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-settings-experimental-304 n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-settings-experimental-310 n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-settings-updates n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-173 n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-173-dev n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-173-updates n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-173-updates-dev n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-304-dev n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-304-updates n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-304-updates-dev n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-319 n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-319-dev n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-319-updates n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-319-updates-dev n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-96 n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-96-dev n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-current n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-current-dev n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-current-updates n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-current-updates-dev n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-experimental-304 n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-experimental-304-dev n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-experimental-310 n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-experimental-310-dev n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-compute-profiler n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-cuda-dev n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-cuda-doc n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-cuda-gdb n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-cuda-toolkit n'est pas installé, et ne peut donc être supprimé
Le paquet nvidia-opencl-dev n'est pas installé, et ne peut donc être supprimé
Le paquet boinc-nvidia-cuda n'est pas installé, et ne peut donc être supprimé
Les paquets suivants seront ENLEVÉS :
  nvidia-304* nvidia-common* nvidia-settings-304* ubuntu-desktop*
0 mis à jour, 0 nouvellement installés, 4 à enlever et 0 non mis à jour.
Après cette opération, 114 Mo d'espace disque seront libérés.
Souhaitez-vous continuer [O/n] ? o
(Lecture de la base de données... 634797 fichiers et répertoires déjà installés.)
Suppression de nvidia-304 ...
Removing all DKMS Modules
Done.
update-alternatives: utilisation de « /usr/lib/i386-linux-gnu/mesa/ld.so.conf » pour fournir « /etc/ld.so.conf.d/i386-linux-gnu_GL.conf » (i386-linux-gnu_gl_conf) en mode automatique.
INFO:Disable nvidia-304
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
update-initramfs: deferring update (trigger activated)
Purge des fichiers de configuration de nvidia-304 ...
update-initramfs: deferring update (trigger activated)
Suppression de ubuntu-desktop ...
Suppression de nvidia-common ...
Purge des fichiers de configuration de nvidia-common ...
Suppression de nvidia-settings-304 ...
Purge des fichiers de configuration de nvidia-settings-304 ...
Traitement des actions différées (« triggers ») pour « bamfdaemon »...
Rebuilding /usr/share/applications/bamf.index...
Traitement des actions différées (« triggers ») pour « libc-bin »...
ldconfig deferred processing now taking place
Traitement des actions différées (« triggers ») pour « desktop-file-utils »...
Traitement des actions différées (« triggers ») pour « gnome-menus »...
Traitement des actions différées (« triggers ») pour « man-db »...
Traitement des actions différées (« triggers ») pour « initramfs-tools »...
update-initramfs: Generating /boot/initrd.img-3.2.0-53-generic-pae
Traitement des actions différées (« triggers ») pour « ureadahead »...
ureadahead will be reprofiled on next reboot
[B]N: « 20auto-upgrades.ucf-old » dans le répertoire « /etc/apt/apt.conf.d/ » a été ignoré car il utilise une extension non valable
N: « 50unattended-upgrades.distrib » dans le répertoire « /etc/apt/apt.conf.d/ » a été ignoré car il utilise une extension non valable[/B]

I don't know if the two last lines are notification or errors but the next command doesn't work at all !

>  sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
[sudo] password for jps: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
La réinstallation de libgl1-mesa-dri est impossible, il ne peut pas être téléchargé.
La réinstallation de libgl1-mesa-glx est impossible, il ne peut pas être téléchargé.
La réinstallation de xserver-xorg-video-intel est impossible, il ne peut pas être téléchargé.
Le paquet suivant a été installé automatiquement et n'est plus nécessaire :
  screen-resolution-extra
Veuillez utiliser « apt-get autoremove » pour les supprimer.
0 mis à jour, 0 nouvellement installés, 1 réinstallés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 1 676 ko dans les archives.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? o
[B]Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise-updates/main xserver-xorg-core i386 2:1.11.4-0ubuntu10.13
  404  Not Found
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main xserver-xorg-core i386 2:1.11.4-0ubuntu10.13
  404  Not Found [IP : 91.189.92.190 80][/B]
Impossible de récupérer [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.11.4-0ubuntu10.13_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.11.4-0ubuntu10.13_i386.deb)  404  Not Found [IP : 91.189.92.190 80]
N: « 20auto-upgrades.ucf-old » dans le répertoire « /etc/apt/apt.conf.d/ » a été ignoré car il utilise une extension non valable
N: « 50unattended-upgrades.distrib » dans le répertoire « /etc/apt/apt.conf.d/ » a été ignoré car il utilise une extension non valable
**E: Impossible de récupérer quelques archives, peut-être devrez-vous lancer apt-get update ou essayer avec --fix-missing ?**

Could you tell me what's wrong ?
Thank you for your patience.
regards.jp

---

### Post by isagarran2 on 2013-12-07
Oups ... I try sudo apt-get update before running the last command ans this command works succesfully.
I'll let you know if all these commands solve the problem

---

### Post by isagarran2 on 2013-12-07
Hello,
I ran apt-get upgrade and the commands ran succesfully. I reboot.
unity-2D-xxx proceses are no longer there. Instead, I have compiz running.
Fron my starting point
- Windows are sticked to the edge of the desktop                                                                                                                                                                    ===> that's work fine.
- I have four desktops using the icon on the launcher (on the left).  Before I had eight desktops and I was able to select them on the right  side of each desktop.      ==> eight desktops but I can't select them on the right side of the desktop
-  In system => apparence => behaviour tab, there is no possiblity to check "enable desktops". This option doesn't exist                                                              ==> always the same
- In system => details => graphic card, I have "experience" and "standard"                                                                                                                               ==> Intel® Sandybridge Mobile x86/MMX/SSE2   experience standard
In compiz, there is no 3D effects (compiz => effects )
It seems that I got my old desktop except 3D functionalities.
It seems better but it is not the end .could you help me to activate 3D effects ?
regards.jp
- In the summary there is no longere anything written for my graphic card.

---

### Post by deadflowr on 2013-12-07
firstly, let's make sure everything is up to snuff.
Run the 
```
/usr/lib/nux/unity_support_test -p
```
command again, and make sure the output looks like this
> Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes




Then, if successful, install the program compizconfig-settings-manager.
When that is installed open it and go to the side section preferences
inside this is a button for reset the defaults, click on it and compiz will reset the default layout.
While it resets the default,, the screen will seem to go crazy, this is normal and may take sometime.
Do not do anything while this happens. Doing something might cause even more harm.
Let the program re-adjust itself.
When it finally stops, you should have a blank screen with just the wallpaper(no launcher or panel)
Now you need to activate the unity plugin.
Go to the Section in the compizconfig-settings-mamnager called Desktop and find the plugin for Unity or unity-shell, or Ubuntu-unity and click on it.
Then in the side pane of the unity plugin is an enable button, click on it and then follow the questions.
the question are usually about setting keybinding and normally you can just select the default options, which will be highlighted.
When all the questions are done, compiz and unity will be back to the default settings as they were before.

Good Luck.

---

### Post by isagarran2 on 2013-12-07
I was about to have something working. I tried the reset button and I got nothing. I can no longer view windows. I reboot and I have no launcher , icon for power and so on. I have only icons on the desktop.
Is there a way to recover from this situation ?
help please. 
regards. jp

---

### Post by deadflowr on 2013-12-07
Please give us a break down of what you had done.
What programs were you running when the windows disappeared.

But from the sound of it, did you run the reset to defaults?
And then closed the compizconfig-settings-manager window?

Then the fix for that would be to click
ctrl + alt + T
This will open a terminal window, but it won't have a title bar or open,close buttons.
when the terminal window opens, type
```
ccsm
```
This is the command to run the settings manager.
Then follow the above post to re-enable the unity plugin.

---

### Post by isagarran2 on 2013-12-07
Hello,
Thank you very much. I'm really happy and I appreciated greatly your support.
I recover all the fucntionalities except the number of desktop. I had eight desktops and now I have only four desktops.
I don't know how to configure it. 
If you could tell me how to get them, it would be really nice :)
Thanks again.
jp

---

### Post by isagarran2 on 2013-12-07
Hello,
Finaly, I was able to define the eight desktops
This post can be closed. As I'm quite new, let me know how to do it.
Thank you very much for your help.
jp

---

### Post by deadflowr on 2013-12-07
Somewhat congratulations!
Only forum staff can close threads, however you can mark a thread as solved by clicking on the thread tools section of in the thread.
(Me thinks)

Personally, I would give it a little time to make sure that the issue is truly solved and that nothing new creeps up.
Sometimes people mark their thread's as solved and then the problem happens again shortly there after.

But, you know where to go at least when the problems do happen.:P

---

