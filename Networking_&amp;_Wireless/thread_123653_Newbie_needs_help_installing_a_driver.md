---
title: "Newbie needs help installing a driver"
date: 2006-01-30
forum: Networking &amp; Wireless
---

### Post by djgenesis on 2006-01-30
I have a Safecom USB 11Mb wireless ethernet adapter (Model SWLUS-1100) and i am trying to install the driver i got for it, from 
```
http://sourceforge.net/project/showfiles.php?group_id=59001
```

I am RTFM but it says 
> 
To configure your kernel build options, in the kernel source directory
(most probably /usr/src/linux-2.x.x), do a `make menuconfig` under console
or `make xconfig' under X environment. 
I have no directory like this and i am a bit scared to mess with the kernel.... 
Inside the direcoty of the driver i downloaded, there are the files
```

genesis@ubuntuj:~/Desktop/atmelwlandriver$ ls -a
.   CHANGES  Makefile             Makefile.kernelv2.6  patch   scripts
..  COPYING  Makefile.kernelv2.4  man                  README  src

``` 
I am trying to run Makefile with sudo ./Makefile but 
> 
sudo: Makefile: command not found

How can i install the module ? :-k

---

### Post by Sutekh on 2006-01-30
[QUOTE=djgenesis]I have a Safecom USB 11Mb wireless ethernet adapter (Model SWLUS-1100) and i am trying to install 

the driver i got for it[/QUOTE]
Are you relying on the wireless adapter for internet when you are using Ubuntu?  Is there anyway you can access the internet *while* you are using Ubuntu?  This will make things *alot* easier.
[QUOTE=djgenesis]
I have no directory like this and i am a bit scared to mess with the kernel.... 
[/QUOTE]
Don't worry you wont be messing with the kernel, but you will need to download the *kernel headers*.

To start you will need to identify the kernel verion you currently use.
```
uname -r
```
will achieve this.  You should get something like
```
2.6.12-10-386
```
This will mean you will need a package called linux-headers-2.6.12-10-386.

You have two ways of getting it.  First (and most easiest) you can use 'apt-get'. But you will need some sort of internet connection *inside* Ubuntu, I don't know if this is achievable for you yet.  If you do have a connection, any connection
```
sudo apt-get install linux-headers-2.6.12-10-386
```
will download and automatically extract the kernel headers for you.

The second way, and I'm afraid more difficult way, will be to download the package yourself from [packages.ubuntu.com](packages.ubuntu.com)

This is a link to 'linux-headers-2.6.12-10-386', but you may need different, depending on the output of 'uname -r' (but -10-386 is prob the most common)
[http://packages.ubuntu.com/breezy/devel/linux-headers-2.6.12-10-386](http://packages.ubuntu.com/breezy/devel/linux-headers-2.6.12-10-386)

Once you downlaod the file (a .deb), you will have to copy it over to your Ubuntu installation.

If you put the file in the /var/cache/apt/archives folder you should be able to install it using the 'apt-get' command above.

[QUOTE=djgenesis]
Inside the direcoty of the driver i downloaded, there are the files
```

genesis@ubuntuj:~/Desktop/atmelwlandriver$ ls -a
.   CHANGES  Makefile             Makefile.kernelv2.6  patch   scripts
..  COPYING  Makefile.kernelv2.4  man                  README  src

``` 
I am trying to run Makefile with sudo ./Makefile but 


How can i install the module ? :-k[/QUOTE]
To solve this you will need to install the 'build-essential' packges, that will install the necessary components to build source code.
Fortunately build-essential is on the install CD
```
sudo apt-get install build-essential
```
will do the trick.

As for the makefile command, what does the README say?

Good Luck.

---

### Post by djgenesis on 2006-02-01
[QUOTE=Sutekh]Are you relying on the wireless adapter for internet when you are using Ubuntu?  Is there anyway you can access the internet *while* you are using Ubuntu?  This will make things *alot* easier.
No, i  have a wired ethernet as well which i am using to access the net.
[/QUOTE]


> To start you will need to identify the kernel verion you currently use.
```
uname -r
```
My kernel version is 2.6.10-5-386 and i have downloaded the headers through apt-get
I have also installed the essentials with apt-get.

> As for the makefile command, what does the README say?

[SIZE="5"]**PART 1**[/SIZE]

It says

> STEP I: Kernel compilation
--------------------------------------------------------------------------------
NOTICE: Sometimes, you may not have to build your kernel manually. This happens
when you are so lucky that your precompiled kernel which your distribution uses
fullfills all the requirements mentioned below. However, in any case you still
have to obtain the kernel sources that correspond to your running kernel, and
put them in the right place.

To configure your kernel build options, in the kernel source directory
(most probably /usr/src/linux-2.x.x), do a `make menuconfig` under console
or `make xconfig' under X environment. (If no such dir exists, this means that
you have no kernel sources, and you have to install them)

The following parameters must be configured, in order for the driver to work:
- Loadable Module Support -> Enable (Module unloading is also recommended)
- Processor types and features -> Symmetric Multiprocessing Support - Disabled
- Device Drivers -> Networking Support -> Wireless LAN (non-hamradio)
        No further specific drivers need to be selected there.
- (PCMCIA only) Bus Options -> PCMCIA/CardBus support -> yenta-compatible.
        Select this only if you prefer to use internal card services
	Otherwise, When you build the external package pcmcia_cs,select i82365.
	You may have to edit /etc/sysconfig/pcmcia, filling the `PCIC=' field,
	with `i82365' or `yenta_socket', according to your selection.
- (USB only) The appropriate host controller interface has to be selected. 
	If unsure, select both ehci, ohci and alternate-uhci and you'll 
	later determine which one is actually used.
- (USB for 2.5 and 2.6) In order to make the driver work for 2.6 kernels,
	you have to download and install the reset-usb kernel patch.
	To make things easier, we provide a link to download the patch from 
	(atmelwlandriver.sourceforge.net/downloads.html).
	Gzip -d it, Copy the ungzipped file to /usr/src/linux-2.6.x and run:
	#patch -bf -p1 < patch_atmel_reset
	This keeps backups of the updated files, in case something goes wrong.
	After the patch has been applied, rebuild your kernel.


To find out if your kernel (custom or not) has these parameters configured as 
required, view the file /usr/src/<Your Running Kernel>/.config and check if the
following lines are the same. 
(they wont be found together, you have to search for each one of them)

CONFIG_MODULES=y
CONFIG_MODULE_UNLOAD=y 		# recommended
# CONFIG_SMP is not set
CONFIG_NET_RADIO=y		# to enable wireless extensions
CONFIG_NET_WIRELESS=y

CONFIG_PCMCIA=m			# mandatory for pcmcia
CONFIG_YENTA=m			# if not using external cs
CONFIG_CARDBUS=m

CONFIG_USB=y			# mandatory for usb
CONFIG_USB_EHCI_HCD=m		# `=m' to all 3 HCI's is the least risky option
CONFIG_USB_OHCI_HCD=m		# therefore `=y' is not recommended.
CONFIG_USB_UHCI_UHCI_ALT=m	# you only need to select the one that suits you
				# but selecting all of them won't do any harm

---

### Post by djgenesis on 2006-02-01
[SIZE="5"]**Part 2**[/SIZE]

> 

WARNING: There are serious conflicts when our driver tries to cooperate with 
usb-uhci, that can lead to a crash. Using uhci (instead of usb-uhci)
is higly recommended. So, if your system starts with usb-uhci loaded 
(you can see this with lsmod), rmmod it and manually load uhci.o (or uhci-hcd.ko
for 2.5+ kernels). In kernel Configuration, select as module only the alternate
UHCI driver if your bus is of that type.


Some further info for linux newbies:
After having finished with kernel tweaking, do `make bzImage', `make modules'
and `make modules_install'.
(For 2.4.x kernels, `make dep' must be run after exiting `make config')
The kernel image shall reside in ./arch/i386/boot/bzImage and should be copied
to /boot directory. For GRUB, just adding a section (in /boot/grub/menu.lst)
containing the new kernel image, is enough to activate the newly compiled kernel
and to be able to load it when booting.

Fedora Core 2 Specific Tips:
Although there is already a precompiled kernel that meets the requirements, you
are strongly recommended to build your own. Having acquired the kernel sources,
do as usual a `make menuconfig', then just save and exit. You need not change
anything. Go on with the kernel building process, as described above in this 
chapter.
Having compiled and installed the atmelwlandriver, you are also suggested to 
disable the script /etc/sysconfig/network-scripts/ifup-wireless . You can do so
by commenting all it's lines. 



STEP II: Building the Driver Modules
--------------------------------------------------------------------------------
Unpack the tarball (tar jxvf) and change dir to atmelwlandriver.

There are 2 variations of Makefile architectures at the moment, depending on
which kernel version you intend to build the drivers. One for 2.6.x kernels and
one for 2.4.x and below.
In each case, make sure that you run every following command as superuser.

i) Building for 2.4.x Kernels

# make config
( `#' represents the superuser's prompt, whereas `$' is a normal user's one.
Either way, you don't have to type it :-)
A number of yes/no questions shall be asked, such as:
1. Build all
2. Set extra module version information
3. Build Debug version
4. Build USB Drivers
	a) Build USB 503A RFMD Driver
	b) Build USB RFMD 505 Driver
	c) Build USB RFMD 505+2958 Driver
	d) Build USB RFMD 505A Driver
5. Build PCMCIA Drivers
	a) Build PCMCIA rfmd Driver
	b) Build PCMCIA 3COM Driver
	c) Build PCMCIA rfmd revision d Driver
	d) Build PCMCIA rfmd revision e Driver
	e) Build PCMCIA 504 Driver
	f) Build PCMCIA 504+2958 Driver
	g) Build PCMCIA 504A+2958 Driver
6. Build miniPCI Driver
7. Build applications
        a) Build console-application (lvnet)
        b) Build X Windows application (winter)
8. Build Firmware Upgrade Tools

You have to find and select your device chipset amongst them. If you are unsure
about your device id, select and build every device of the corresponding bus 
(pci, pcmcia or usb) and you will find out which one is actually used when you
insert the device, by watching console output or the file /var/log/messages.
Except from specific chipset selection options, there are also some preferences
that apply to whatever driver you build. In each one of them, just pressing
enter means answering "no", which is usually safer. Furthermore, answering "yes"
to 2 is highly discouraged, unless you really know why you need that. It is also
recommended when trying the drivers for the first time, to build them in debug
mode (which means answering "yes" to 3), so as to determine easier whatever
malfunction is responsible for a potential error. Be prepared, however, for a
great console output. (this can be ceased by `echo 0 > /proc/sys/kernel/printk`)
The two applications accompanying the drivers are `lvnet' and `winter' and are
suited for console and X respectively. lvnet requires ncurses, while winter is a
wxWidgets app, therefore it needs wxGTX-4.2 or greater. Both must be run as root.

Having finished with the selections, order the building with
# make all
and finally run
# make install
This will copy the modules to a directory inside:
/lib/modules/<Your Running Kernel>/kernel/drivers/ , depending on the selected
bus, and shall report to module-init-tools about their existence, so that 
modprobe can find and load them, resolving their dependencies.


ii) Building for 2.6.x Kernels

# make 
This will display all the available build options:

Pick one of the following targets for KERNELS 2.X.X:
make clean	- remove all directories of object files
make device buildonly=argument 
		- where device = usb or pcmcia, argument = debug or release
make lvnet	- compile lvnet utility
make winter 	- compile winter utility 
make world	- compile all modules with debug and release information
make install	- install modules and programs
							
example:
# make pcmcia buildonly=debug 
Builds every pcmcia module with debug information 

It is generally recommended when trying the drivers for the first time, 
to build them in debug mode, so as to determine easier whatever
can be responsible for a potential error. Be prepared, however, for a
great console output. (this can be ceased by `echo 0 >/proc/sys/kernel/printk')
The two applications accompanying the drivers are `lvnet' and `winter' and are
suited for console and X respectively. lvnet requires ncurses, while winter is a
wxWidgets app, therefore it needs wxGTX-4.2 or greater.Both must be run as root.

Having finished with building procedure, run:
# make install
This will copy the modules to a directory inside:
/lib/modules/<Your Running Kernel>/kernel/drivers/ , depending on the selected
bus. Finally, run, as prompted:
# depmod -aeq
which shall report to modprobe about the modules' existence, so that it
can find and load them, resolving their dependencies.



---

### Post by djgenesis on 2006-02-01
The other part is for loading the module, which i think i know how to do, and enabling the wireless network card etc which i think i also know how to do ... 


Thanks for you help..

---

