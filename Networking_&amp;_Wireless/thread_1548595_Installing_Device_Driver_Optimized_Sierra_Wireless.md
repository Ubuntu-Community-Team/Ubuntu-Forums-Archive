---
title: "Installing Device Driver Optimized Sierra Wireless U 306 on Karmic(9.10)"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by w4w4n on 2010-08-08
;)
When i reached on google and find out at ["]Sierra Official Websites]("https://sierrawireless.custhelp.com/app/answers/detail/a_id/641/session/L3NpZC81c2xvT1k2aw%3D%3D#[3)
it just says simply ways,
1. Download the drivers that available according to your kernel machines (on my machines, I use 2.6.31 kernel version) at [_Sierra Wireless Customer Help_]("https://sierrawireless.custhelp.com/app/answers/detail/a_id/500/session/L3NpZC81c2xvT1k2aw%3D%3D") 
you can determine type of your kernel by typing " uname -r " in terminal
after finished, put it into new folder and extract its contents,
2. open terminal, "cd" to your directory that contains extracted files, compile the kernel drivers using "sudo make"
3. be sure no erors message while compiling, and if if finish compile, type "sudo make install" to install the compiled files
4. If there is no erors message detected, you can type "sudo dmesg | tail" to ensure that its have been work on your kernel

On my machine, here some capture if successfully installed

[ATTACH]165884[/ATTACH]

[ATTACH]165885[/ATTACH]
;)

if you have more knowledge about the syntax of the command line, you can try to activate the AT commands to increase the stability of your modem in this links [_Configuring GSM AT Commands_]("https://sierrawireless.custhelp.com/app/answers/detail/a_id/500/session/L3NpZC81c2xvT1k2aw%3D%3D#GSM/UMTS_AT_Commands") 

if still confused about this post, you can follow this information 
["]_here_]("https://sierrawireless.custhelp.com/app/answers/detail/a_id/641/session/L3NpZC81c2xvT1k2aw%3D%3D#[3)

---

