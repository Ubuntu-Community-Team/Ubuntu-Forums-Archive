---
title: "Intel e1000 NIC Not Recognized"
date: 2006-01-19
forum: Networking &amp; Wireless
---

### Post by j2fraser on 2006-01-19
Hi, I'm wondering if anybody here can help me out. I have a Dell Dimension 9150 with an Intel Pro Gigabit NIC on-board (e1000). Kubuntu would not recognize the NIC when it installed and I can't seem to get Kubuntu to recognize it. 

I ran 'sudo lshw -C network' (which I saw in a different sub-forum) and here is the output I got:

    *-network UNCLAIMED
    description: Ethernet controller
    product: Intel Corporation
    vendor: Intel Corporation
    physical id: 0
    bus info: pci@04:00.0
    version: 01
    width: 32 bits
    clock: 33MHz
    capabilities: bus_master cap_list
    resources: iomemory:ef7e0000-ef7fffff iomemory:ef800000-efbfffff ioport:cce0-ccff irq:10

'mii-tool eth0' gave me an error message saying that there was no ethernet card.

Seems to me that the card is being seen on a physical level, but there is some obstacle somewhere else. I ran 'lsmod | grep e1000' and got silence. 'ifconfig' shows only the local connection. 

I even tried to compile the driver myself, since I had seen here ([http://blog.dataloss.nl/perma/ubuntu-510-breezy-on-dell-dimension-9150/]("http://blog.dataloss.nl/perma/ubuntu-510-breezy-on-dell-dimension-9150/")) that the e1000 driver that came with Breezy is outdated. I downloaded the Intel driver stuff (in WinXP), copied to a FAT32 partition, untarred it, cd'd to the source directory and tried compiling it using 'make install', but I got a bunch of syntax errors (nb: had already run 'apt-get install build-essential'). Could the reason it won't compile be because I am running Kubuntu AMD64?

Help! As I'm sure many people will be able to see, I have just enough knowledge to get myself into real trouble -- I am out of my league here folks!

Any help / suggestions would be greatly appreciated.

Thanks!

---

### Post by tijs on 2006-02-13
I have the same problem and I'm very dissapointed Ubuntu doesn't work with my brand new Dell Dimension 9150... :( 

Is there any developer who can help us out?

---

### Post by mips on 2006-02-13
From a terminal try **sudo modprobe e1000** and see what happens.

---

### Post by lost_in_nz on 2006-02-15
The syntax errors are probably due to GCC4 (At least they were for me).
Here is what I did:

Install binutils:
sudo apt-get install binutils

Install GCC-3.4:
sudo dpkg - I cpp-3.4_3.4.4-6ubuntu8_i386.deb GCC-3.4_3.4.4-6ubuntu8_i386.deb GCC-3.4-base_3.4.4-6ubuntu8_i386.deb

Download the e1000 driver, untar etc..

Make kernel module: (in the intel src dir)
sudo make install

sudo modprobe e1000

Hope this helps.

---

### Post by mips on 2006-02-15
Thanks for that. I'm sure there are few people here that would benefit.

Any posibility of breaking the procedure down into command line steps seeing some people might have limited experience in building kernel modules.

Might wanna consider a HOWTO for the customization & tricks forum ?

---

### Post by lost_in_nz on 2006-02-15
This exists, I found the information in the french wiki:
[http://wiki.ubuntu-fr.org/materiel/e1000](http://wiki.ubuntu-fr.org/materiel/e1000)

If you dont understand french, the google translator might help out... it is mostly the links and commands that are of interest though.

---

### Post by mips on 2006-02-15
Thanks! As you said the commands are the most important.

Anybody care to translate the wiki to Anglais ???

---

### Post by mips on 2006-02-16
[http://www.ubuntuforums.org/showthread.php?p=741687](http://www.ubuntuforums.org/showthread.php?p=741687)

Thanks to ubuntulifestyle for the french to english tranlation of the wiki page.

---

### Post by j2fraser on 2006-03-03
Thanks (belatedly) for the help. The above worked, at least so far as getting my system to see my NIC. There was some wrangling for configuratrion info (which is available at [http://www.ubuntuforums.org/showthread.php?t=69539&highlight=e1000]("http://www.ubuntuforums.org/showthread.php?t=69539&highlight=e1000")), but I eventually got the thing up and running. SWEET!

---

### Post by j2fraser on 2006-03-13
OK, now more bummer e1000 problems (seriously considering a new NIC here people!:-? ). I ran an *apt-get update* and then an *apt-get upgrade* (I'm trying to upgrade to KDE 3.5.1, but that is a whole other nightmare...). Apt-get told me it was installing 2.6.12-10-amd64-generic. It retrieved and configured some files. On reboot, GRUB showed me some new 2.6.12-10 kernel entries, the first of which booted by default; **however**, now my onboard NIC will not work. Figuring (like the true newb that I am) that this was a problem calling for me to recompile the driver under the new kernel, I tried to do that with a *make install*; however, I got a bunch of pointer errors and the compile bombed with "*cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode*" at the end. Oddly, I can still access my NIC if I boot using the 2.6.10-9-amd64-generic option from GRUB. Is this a bug in the new kernel release or a conflict between the new kernel and the e1000 driver and, if so, is anybody else having the same problem or, even better, does anybody know how to fix it?

Any help / guidance would be appreciated!

---

### Post by lost_in_nz on 2006-03-14
You are correct, as the upgrade installed a newer version of the kernel, you must recompile the driver (for this new kernel). I have done this on my 9150 over a dozen times now, without a hitch.

My suggestion would be to go over the steps again carefully one by one, it would probably be quicker than trying to trackdown what is wrong (sounds like kernel headers / src are not available, not sure though). It wont break anything repeating the steps, I.e. installing gcc 3.4 etc.

It is a hassle, but dont waste you money on a new nic ;)

---

### Post by Freewheelin Franklyn on 2006-03-14
I'm getting the same problem. I got the NIC working and then it stopped when I update the Kernel. I followed the steps exactly as I did before. When I run the make install command I get the message "cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode" 

I'm running kernel version 2.6.12-10-686

Any ideas guys?

---

### Post by lost_in_nz on 2006-03-15
If this was done in the same way as the other chap, I.e. update, upgrade of whole system, it may have messed up (upgraded) the gcc3.x stuff that is required to compile the e1000 driver. Check what version of the compiler is installed, and make sure it still matches the instructions.

---

### Post by Freewheelin Franklyn on 2006-03-15
i'm sure I have the correct complier installed

The output I get when I run the make install command is:

make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
# remove all old versions of the driver
find /lib/modules/2.6.12-10-686 -name e1000.ko -exec rm -f {} \; || true
find /lib/modules/2.6.12-10-686 -name e1000.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000.ko /lib/modules/2.6.12-10-686/kernel/drivers/net/e1000/e 1000.ko
/sbin/depmod -a || true
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
man:
cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.

Don't know if this indicates what is causing the problem.

---

### Post by j2fraser on 2006-03-18
I tried re-installing gcc-3.4 (which seemed to go fine) and then re-compiling the driver, but I ran into the identical error  set out in the posting above. Any luck Franklyn?:???: 

PS. On the bright side, I did get KDE 3.5.1 working!

---

### Post by p47 on 2006-03-20
Hello Everybody !!!
I was readed the post and I have the same problem...

I have dimension 9150 too 
Do you resolved your problems with the NIC ?

---

### Post by lost_in_nz on 2006-03-20
An alternative to all these shenanigans could be to install the latest stable version of the kernel. The latest version has much better support for the e1000 card, and just seems to work as it should (I.e. no need to compile a driver).

The sound card also seems to be better supported in later versions of the kernel (2.6.15.x at least), and it fixes the problem of the harddrive light staying on all the time for the 9150.

There are plenty of good guides around (google) if you decide to go this way.
You will also need to re-install the ati fglrx driver again (if that is what you are using).

---

### Post by p47 on 2006-03-20
Thank's 
Sorry ! Which version of kernel do you have ?
I don't know how compile the kernel...
apt can install me that kernel ?

---

### Post by p47 on 2006-03-21
Hello again **lost_in_nz**

**Somebody HELP ME PLEASE !**
Do you have some tutorial about the compile or install the new kernel like 2.6.15.x ?
Because I'm the new user in ubuntu and linux and I don't understans as I want...
Thank's a lot !
Regards .

---

### Post by postbus24 on 2006-03-30
[QUOTE=j2fraser]I tried re-installing gcc-3.4 (which seemed to go fine) and then re-compiling the driver, but I ran into the identical error  set out in the posting above. Any luck Franklyn?:???: 

PS. On the bright side, I did get KDE 3.5.1 working![/QUOTE]

dont you have to activate GCC-3.4 ?
I tought it was something like this:
> 
export CC=gcc-3.4

---

### Post by mgw24 on 2008-03-16
This is what I get:

mweeks@nas:~/e1000-7.6.15.4/src$ sudo make install
make -C /lib/modules/2.6.22-14-server/build SUBDIRS=/home/user/e1000-7.6.15.4/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-server'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-server'
# remove all old versions of the driver
find /lib/modules/2.6.22-14-server -name e1000.ko -exec rm -f {} \; || true
find /lib/modules/2.6.22-14-server -name e1000.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000.ko /lib/modules/2.6.22-14-server/kernel/drivers/net/e1000/e1000.ko
/sbin/depmod -a || true
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
man: 
cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.

---

