---
title: "syncml-plugin-installation"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by ashishchandna on 2011-01-05
[SIZE=3][FONT=Arial]Hi all,[/FONT][/SIZE]
[SIZE=3][FONT=Arial]currently I have installed libsyncml but when I am trying to install syncml plugins(opensync-plugin-evolution and opensync-plugin-file) I am getting following errors:[/FONT][/SIZE]
 
[FONT=Arial][SIZE=2][FONT=Arial]-- Evolution Data Server 1.2 used.[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial]-- checking for one of the modules 'libopensync;>=0.39'[/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=2][FONT=Arial]CMake Error at cmake/modules/FindPkgConfig.cmake:357 (message):[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial]None of the required 'libopensync;>=0.39' found[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial]Call Stack (most recent call first):[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial]cmake/modules/FindOpenSync.cmake:27 (PKG_SEARCH_MODULE)[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial]CMakeLists.txt:11 (FIND_PACKAGE)[/FONT][/SIZE][/FONT]
 
 
[FONT=Arial][SIZE=2][FONT=Arial]CMake Error at cmake/modules/FindOpenSync.cmake:46 (MESSAGE):[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial]OpenSync cmake modules not found. Have you installed opensync core or did[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial]you set your PKG_CONFIG_PATH if installing in a non system directory ?[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial]Call Stack (most recent call first):[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2][FONT=Arial]CMakeLists.txt:11 (FIND_PACKAGE)[/FONT][/SIZE][/FONT]
 
 
[FONT=Wingdings][SIZE=2][FONT=Wingdings]n[/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2][FONT=Arial]Configuring incomplete, errors occurred![/FONT][/SIZE][/FONT]
 
[FONT=Arial][SIZE=3][FONT=Arial]How I can use syncml with bluez to synchronize my phone and desktop or how I can integrate syncml with bluez?[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=3][FONT=Arial]Which packages and application should be required?[/FONT][/SIZE][/FONT]

---

