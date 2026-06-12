---
title: "help with ndiswrapper problem please"
date: 2005-02-24
forum: Networking &amp; Wireless
---

### Post by mike_c on 2005-02-24
This is driving me NUTS.  I've literally spent days now trying to get my wireless NIC working.  The card is a Netgear wg311v2.  I have followed the instructions on the Ubuntu ndiswrapper howto.  I have tried using the houseofcraig acx100_howto, all to no avail.  I have recompiled ndiswrapper, both the 1.0 version on sourceforge and the newer pre-release version.   I don't know what else to try and I'm afraid I've munged things up so badly that I'll never get it working.  Starting over from a clean install is likewise undesirable, because I've spent so many days setting this machine up and would have to repeat it all.

Presently, modprobe ndiswrapper returns:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-3-386/misc/ndiswrapper.ko): Operation not permitted

I am issuing the command as root.  Several days ago, when I first started this nightmare, ndiswrapper loaded properly, but then there was a driver problem.  I've since found a solution to that problem (I think) but now cannot get the module to load.  I need help from someone who can walk me through fixing this.  I am not a linux newbe, but I'm in over my head right now.

xoxo
Mike C.

---

### Post by acascianelli on 2005-02-24
[QUOTE=mike_c]This is driving me NUTS.  I've literally spent days now trying to get my wireless NIC working.  The card is a Netgear wg311v2.  I have followed the instructions on the Ubuntu ndiswrapper howto.  I have tried using the houseofcraig acx100_howto, all to no avail.  I have recompiled ndiswrapper, both the 1.0 version on sourceforge and the newer pre-release version.   I don't know what else to try and I'm afraid I've munged things up so badly that I'll never get it working.  Starting over from a clean install is likewise undesirable, because I've spent so many days setting this machine up and would have to repeat it all.

Presently, modprobe ndiswrapper returns:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-3-386/misc/ndiswrapper.ko): Operation not permitted

I am issuing the command as root.  Several days ago, when I first started this nightmare, ndiswrapper loaded properly, but then there was a driver problem.  I've since found a solution to that problem (I think) but now cannot get the module to load.  I need help from someone who can walk me through fixing this.  I am not a linux newbe, but I'm in over my head right now.

xoxo
Mike C.[/QUOTE]
 su to root and then do the modprobe.

---

### Post by mike_c on 2005-02-24
[QUOTE=acascianelli]su to root and then do the modprobe.[/QUOTE]

I'm already root.  That's the problem.   ](*,) 

root@music-box:/home/music # whoami
root

root@music-box:/home/music # modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-3-386/misc/ndiswrapper.ko): Operation not permitted

xoxo
Mike C.

---

### Post by fizgig on 2005-02-24
Perhaps the module you're trying to insert doesn't match the kernel you have installed...

If you got ndiswrapper from the repository, why not remove it and compile it yourself.  (Download from [here](http://sourceforge.net/projects/ndiswrapper/) )

That's how I used to do it and it was easy.   This will make sure it matches the kernel.

---

### Post by mike_c on 2005-02-25
[QUOTE=fizgig]Perhaps the module you're trying to insert doesn't match the kernel you have installed...

If you got ndiswrapper from the repository, why not remove it and compile it yourself.  (Download from [here](http://sourceforge.net/projects/ndiswrapper/) )

That's how I used to do it and it was easy.   This will make sure it matches the kernel.[/QUOTE]

Thanks, but I tried that-- this IS a freshly compiled ndiswrapper.  Make distclean, make, and make install all completed without a hitch.

---

### Post by Joe on 2005-02-25
I've got the exact same problem.

[QUOTE=mike_c]Thanks, but I tried that-- this IS a freshly compiled ndiswrapper.  Make distclean, make, and make install all completed without a hitch.[/QUOTE]

---

### Post by bobmitch on 2005-02-25
I have the same network card, but I`m running on hoary (array 4 dvd weekly image) - and it works without requiring ndiswrapper.

Saying that, when I was on warty, I never had the problem you guys are experiencing with ndiswrapper.

You may want to do a:  ndiswrapper -m   (I think from memory) to create the modprobe definition automatically, then retry the modprobe.

Rgds,
mitch

---

### Post by Mastor on 2005-02-25
maybe the gcc version must be the same of the kernel...
the basic kernel uses gcc-3.3.5 and you have to compile ndiswrapper with gcc-3.3.5

(try to see the log of ndiswrapper-buginfo)

---

### Post by present on 2005-02-27
acx111:  i get a ndiswrapper error in dmesg that complains: check utils version mismatch.  could ndiswrapper and ndiswrapper-utils be different version?  i downloaded the bz2 files (tried 2 versions) straight from sf.  or perhaps more likely to me, ndiswrapper and ndiswrapper-utils are each referencing the ubuntu headers differently and ubuntu does not have consistent naming (perhaps one returns 2.6.8.1-3-386 while the other returns 2.6.8.1, or some other variant).

i have used a regular "make, make install" of version 0.10 and RC version. same error.

how do i compile gcc 3.3.5 without a compiler? lol... this is getting rather time consuming on an old stinkpad 300mhz...  if there are possible app inconsistencies if the kernel is compiled with a different release than apps, wouldn't it make sense to package the same compiler with the distro that the kernel was compiled with?  i mean it is not very functional to have a compiler packaged that will not compile usable binaries right?

hmm, just a thought...

---

### Post by lao_V on 2005-02-28
I have a USR Wireless card which apparently uses that same chipset (TI - acx 111) as the netgear one. 

After trying ndiswrapper and many other solutions for hours and hours, I tried linuxant drivers ([here)]("http://www.linuxant.com/driverloader/wlan/full/archive/driverloader-2.24/driverloader_2.24_i386.deb") which worked perfectly!! You might want to try that The instructions  can be found [here]("http://www.linuxant.com/driverloader/wlan/install.php") (look at Method B for deb)

---

### Post by present on 2005-02-28
i'll give it a shot.

does it supports WEP?

---

### Post by lao_V on 2005-02-28
Yup, upto 256 I think. It also supports 64-bit machines (if you have 64-bit proprietery drivers!!)

---

### Post by present on 2005-02-28
woot sounds cool!

i couldn't get ubuntu to detect my card tho :S

lspci or ... (the ctl cmd that prints nic volteage), both commands didn't work.

i'm just finishing a slack install, if it doesn't work i'll try damn small linux again.  it detected my card under lspci and the voltage command, but the linux drivers didn't support WEP and ndiswrapper didn't install properly-probably the modified, small form factor gcc packages.

guess that would make it a "non-ubuntu" issue, but i'll post my results here in case it can help someone.

---

