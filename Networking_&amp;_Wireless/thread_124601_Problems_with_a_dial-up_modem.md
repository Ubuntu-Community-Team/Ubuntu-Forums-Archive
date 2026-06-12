---
title: "Problems with a dial-up modem"
date: 2006-02-01
forum: Networking &amp; Wireless
---

### Post by Da Cosmonaut on 2006-02-01
I've been having trouble configuring my modem.
Could you help me?

It is a Lucent Win Modem connected to COM2, I'm using kernel 2.6.12-9-386 and I really need a step by step guide since I couldn't work out the wiki instructions neither hundreds of tutorials.

Tia

---

### Post by sunnypk on 2006-02-01
I am having the same problem guyz and my modem is lucent win as well :) can anyone in here help me i m also pretty new user to linux i've been trying to find the solution but every solution i get is too advanced for me and usually don't work... waiting for reply ...

---

### Post by realdog on 2006-02-01
Hi i have the same problem i need to connect to internet and my modem is lucent win modem, i run scanmodem and is tellin me that the modem has a supported Lucent/Agere DSP (digital signal processing) and
The modem will NOT function because of interrupt assignment: IRQ 255
 Possible corrections are:
   1) to access the  the boot up BIOS change to a non-PNP mode.
my question is how can i acces the bios of ubuntu?

---

### Post by eriefisher on 2006-02-02
To access to bios you need to reboot and when your machine starts press F1 or ESC or DEL or somthing. Most machines will tell you wich button to push to enter setup. The bios load before the operating system does.

eriefisher

---

### Post by hajk on 2006-02-02
The Lucent WinModem requires a special Debian driver package, available
from \url{http://linmodems.technion.ac.il/packages/ltmodem} for the
installed kernel version. (If such a package is not available, then the driver
source code must first be downloaded, compiled, and packaged.)

The package can then be installed with the command "sudo dpkg -i <package>.deb", where <package> is the name of the package downloaded. This provides the modules "ltserial" and "ltmodem", which can be loaded by using the command "sudo modprobe ltserial". Afterwards, they're loaded automatically at boot.

The "ppp0" interface can be configured in the Gnome network manager, System/Administration/Networking, in the usual manner: highlight the ppp0 interface and hit Properties, then fill in the connection data that you got from your ISP. For example, userID, telephone number, password, and (under Options) use of the providers nameservers and using the modem device as default gateway. The connection is made once the ppp0 interface is activated.

That's the way it works for me when I'm on the road and there's only a telephone line available.

---

### Post by realdog on 2006-02-02
Yes i did all of that i downloaded the .deb fille ltmodem-2.6.12-9-386_8.31b1_i386
i did
>  sudo dpkg -i ltmodem-2.6.12-9-386_8.31b1_i386

i make the 
> sudo mobprobe 

[IMG][[IMG]http://img141.imageshack.us/img141/2853/screenshot9zi.png[/IMG]](http://imageshack.us)[/IMG]

Where i make my mistake.

---

### Post by hajk on 2006-02-02
Your mistake was to mix all sorts of instructions from other sources...
With all those files you edited or added, the kernel is now getting conflicting information about these modules. Yet, the ltmodem package already takes care of everything for you, no need to edit anything. Your edit of /etc/udev/rules.d/10-local.rules is a case in point -- the ltmodem package had already put a file ltmodem.rules there, specifying the /dev/ttyLTM0 device (and /dev/modem a symlink to it).

So, this is what you should do:

1. roll back all those "sudo gedit.." and "echo" commands.
2. just to be sure, reconfigure the package with 
    "sudo dpkg-reconfigure ltmodem....deb"
3. followed by "sudo modprobe ltserial" 

and you're all set to start connecting. Now, don't mess with files in /etc/ppp/peers and /etc/network/interfaces either! Leave everything to the System/Administration/Networking setup, as I suggested in my earlier post.

Have fun!

P.S. You already found out that the module name is now "ltserial", no longer "lt_serial"...

---

### Post by realdog on 2006-02-04
i did fresh reinstall and nothing is the same problem
[IMG][[IMG]http://img425.imageshack.us/img425/3885/screenshot9kz.png[/IMG]](http://imageshack.us)[/IMG]
in attach the results of the scan modem 
what can i do?

---

### Post by hajk on 2006-02-04
The output of the scan says that there is an IRQ conflict, so that's what you should try and fix. During boot press F2 (or something like it, depends on your computer) and try to reassign the IRQ for your COM2 port, or disengage PnP, or whatever -- try and experiment a bit, and see if it works. Advice: make a note of the changes you make, you may have to undo them later...;) 

Good luck!

---

### Post by realdog on 2006-02-09
Well after a long research to try to change ythe bios settings os the conflict IRQ 255 i can't access this
 Right-Arrow to the "Advanced" page. Below the CPU Type/Speed/Cache entries is a line: "Installed O/S:" Three alternatives are offered: Win95, Win98/WinNT5.0, and Other. Choosing "Other" is the proper selection for Linux. Exit, saving the changes. Continue booting into Linux.
it seems to be a mystrery in my computer because didnt have this settings

Well i will be stuck in windows for a long period until this problem can be resolve in next the lauch of dapper drakrer i think:cry:

---

