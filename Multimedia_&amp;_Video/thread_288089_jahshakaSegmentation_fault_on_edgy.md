---
title: "jahshaka
Segmentation fault on edgy"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by stani on 2006-10-29
Hi,

Unfortunately there are not yet edgy repositories for jahshaka. When I install jahshaka from the dapper repositories and I try to run it on edgy, I get this error:

```
stani@blue:/home$ jahshaka --debug
[ i] Starting Jahshaka System Tracer
[*D]  Using Runtime Options : jahshaka.bin:--debug:
[ i] Initializing Preferences
[ i] Initialized Translator
[ i] Jah Constructor : Initializing Jahshaka
[ i] Checking and Restoring Prerences
[*D]  Checking for media path
[*D]  Home directory:/home/stani
[*D]  QT_VERSION_STR: 3.3.6
[*D]  Qt is up to date
[*D]  ANTE: the application base path is /usr/share/jahshaka/
[*D]  ANTE: the media path is /home/stani/jahstorage/
[*D]  Found media folder, using JahMediaPath
[*D]  POST: the application base path is /usr/share/jahshaka/
[*D]  POST: the media path is /home/stani/jahstorage/
[ i] Launching Startup Screen
[*D]  in restorestyle
[ i] Checking the OpenGL Extensions
[*D]  Vendor    :ATI Technologies Inc.
[*D]  Renderer  :Radeon X1300 Series Generic
[*D]  Version   :2.0.6011 (8.28.8)
[*D]  Glew Initialized
[*D]  Status: Using GLEW 1.3.4

[ i] Enabling OpenGL Extensions
[*D]  OpenGL 1.3 is supported!
[ i] ARB_fragment_program is supported.
[ i] GL_ARB_multisample is supported.
[ i] GL_EXT_fog_coord is supported.
[ i] We have opengl shader support
[ i] We have ARB gpu support
[ i] Launching Core Application
[ i] >Initializing Variables
Segmentation fault

```

Anyone knows how to run jahshaka on Edgy?

---

### Post by rudlavibizon on 2006-11-29
I seem to have the same problem 

```
rudlavibizon@rudlavibizon-linux:~$ jahshaka debug
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
[ i] Starting Jahshaka System Tracer
[*D]  Using Runtime Options : jahshaka.bin:debug:
[ i] Initializing Preferences
[ i] Initialized Translator
[ i] Jah Constructor : Initializing Jahshaka
[ i] Checking and Restoring Prerences
[*D]  Checking for media path
[*D]  Home directory:/home/rudlavibizon
[*D]  QT_VERSION_STR: 3.3.6
[*D]  Qt is up to date
[*D]  ANTE: the application base path is /usr/share/jahshaka/
[*D]  ANTE: the media path is /home/rudlavibizon/jahstorage/
[*D]  Found media folder, using JahMediaPath
[*D]  POST: the application base path is /usr/share/jahshaka/
[*D]  POST: the media path is /home/rudlavibizon/jahstorage/
[ i] Launching Startup Screen
[*D]  in restorestyle
[ i] Checking the OpenGL Extensions
[*D]  Vendor    :ATI Technologies Inc.
[*D]  Renderer  :Radeon X1300 Series Generic
[*D]  Version   :2.0.6119 (8.30.3)
[*D]  Glew Initialized
[*D]  Status: Using GLEW 1.3.4

[ i] Enabling OpenGL Extensions
[*D]  OpenGL 1.3 is supported!
[ i] ARB_fragment_program is supported.
[ i] GL_ARB_multisample is supported.
[ i] GL_EXT_fog_coord is supported.
[ i] We have opengl shader support
[ i] We have ARB gpu support
[ i] Launching Core Application
[ i] >Initializing Variables
Segmentation fault (core dumped
```)
](*,) ](*,) ](*,)

---

### Post by OrganicPanda on 2007-02-25
Hey, don't know if this has been fixed yet but there is a script on the jahshaka site that works for edgy x86, well for me anyway, script is: [jahshaka-dapper-x86.sh]("http://puzzle.dl.sourceforge.net/sourceforge/jahshaka/jahshaka-dapper-x86.sh") that makes everything all better, you run it with:

```

sudo /bin/bash jahshaka-dapper-x86.sh install

```

(Assuming you're in the same directory as it)

I selected all the options to be safe and after what seems like ages of a none-to helpful progress bar bouncing backwards and forwards it's all installed and working. it is run with:

```

jahshaka

```

It looks incredible, enjoi

---

### Post by theophiles on 2007-03-02
I ran that and it still did not function. I feel like I am in way over my head.:confused: 

clinebj@desktop:~$ jahshaka
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
libGL warning: 3D driver claims to not support visual 0x46
Segmentation fault (core dumped)
clinebj@desktop:~$ sudo /home/clinebj/Desktop/jahshaka-dapper-x86.sh install
Password:
sudo: /home/clinebj/Desktop/jahshaka-dapper-x86.sh: command not found
clinebj@desktop:~$ cd /home/clinebj/Desktop/
clinebj@desktop:~/Desktop$ sudo /bin/bash jahshaka-dapper-x86.sh install
jahshaka jahplayer jplayer
clinebj@desktop:~/Desktop$ jahshaka
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Themes::create: returning new SuperGStyle instance
libGL warning: 3D driver claims to not support visual 0x46

Segmentation fault (core dumped)
clinebj@desktop:~/Desktop$ 
clinebj@desktop:~/Desktop$ cd
clinebj@desktop:~$ jahshaka
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Themes::create: returning new SuperGStyle instance
libGL warning: 3D driver claims to not support visual 0x46
Segmentation fault (core dumped)
clinebj@desktop:~$

---

### Post by anv on 2007-03-03
I'm giving one positive report of installing Jahshaka through that script, I'm running Edgy and I managed to install it, I try to edit something...ok it is little buggy yet, didn't crash but some buttons acted little sticky.

---

### Post by anv on 2007-03-06
ok it didn't work so long quite unstable and crashy:confused:

---

