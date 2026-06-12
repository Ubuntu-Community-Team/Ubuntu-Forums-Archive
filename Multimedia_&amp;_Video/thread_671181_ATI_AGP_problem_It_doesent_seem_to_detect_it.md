---
title: "ATI AGP problem It doesent seem to detect it"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by Strike_105x on 2008-01-18
My problem is i installed the drivers liked it said in the how to (here is the link [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Verifying](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Verifying))  but when using fglrxinfo command it said meta drivers here is an example:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)


 tried a more complex comand and this is what i got:

$ less /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(EE) AIGLX: Screen 0 is not DRI capable
strike105x@strike105x-pc:~$

from what i understand it doesent detect my agp could someone help me pls i want to use the psx emulator but its going verry bad 

my specs Sempron 3000+ asrock nvidia 3 chipset 1GB DDR 80GB HDD ATI 9600 XT 256 DRR

Forgot to say this but could it be because i got AGP fastwrite enable ?

---

### Post by Strike_105x on 2008-01-20
Well like i said before my specs are Sempron 3000+, asrock K8Upgrade-NF3, ATI 9600XT 1GB DDR 400, 80 GB HDD SATA, 40 GB HDD Seagate IDE.
Solution to my video problem : None
i'm Righting this if someone with a similar configuration to mine know's whats w8ing for him.
I tried to: Upgrade & Downgrade the motherboard bios with all available bios versions at [www.asrock.com](www.asrock.com)
if did this using Kubuntu 7.10 & Kubuntu 6.06 LTS but it still didnt work also tried the fix mentioned in the wiki([http://wiki.cchtml.com/index.php/Troubleshooting#nForce_3_AGP_Issues](http://wiki.cchtml.com/index.php/Troubleshooting#nForce_3_AGP_Issues)) with kubuntu 6.06 LTS (with all versiones off bios and nothing).
Also i would like to mention everytime i tried a difrent version of bios i have done a clean reinstall of Kubuntu (both 7.10 & 6.06 LTS)

Now there are 2 possible fixes for this problem that i found:

1.buy a new NVIDIA VideoCard  (which i aint gona do since i like my ATI)
2.buy a new MotherBoard BUT NOT NFORCE3  (this il try to do today some asus or gigabyte with VIA chipset)

PS:sry for spelling errors

---

### Post by foyb on 2008-04-02
Hi guys,

got the same problem here...

with an k8upgrade-nf3 board with a radeon 9800 Pro

tried different tastes of ubuntu (7.10/8.04 beta) - all non working ...

the agp module loaded is amd64_agp; fglrx does not show any important errors in dmesg; xorg shows the could not acquire agp ... error.

it only works full featured (DRI working) when i first boot into windows XP, then reboot into the linux distro... which isn't an option because i want to use the computer as a mce (mythbuntu...)

not so nice effect on 8.04: having the fglrx driver enabled ubuntu thinks we have AIXGL or GLX and trys to load compiz, which only shows a blank (white) screen - you can only start working if you disable fglrx or kill compiz from within the console (sudo killall compiz.real)

currently trying other distros ... seems like the ubuntu-kernel does not recognise the agp bridge well ...

will post update soon (will try to upgrade/downgrade bios and try other distros as well)

---

### Post by foyb on 2008-04-02
hi, 

found this: [http://bugzilla.kernel.org/show_bug.cgi?id=6350](http://bugzilla.kernel.org/show_bug.cgi?id=6350)

looks like you will have to compile a new kernel if you REALLY want to keep your hardware (nforce3 250 + ati graphics card) and potentially will loose usb (see the last comments on the bug report)

i will try to compile kernel with the patch included in the bug report and post what happens ...

---

### Post by Herno on 2008-04-03
Hi, I have a MSI K7N2-Delta2 (32bit) with a Radeon 9600 and I have the same problem. Should I try the patch?

---

### Post by robert1968 on 2008-07-03
SOLUTION for ATI Radeon 9600 and FGLRX -AGP

Symptome: Installing fglrx on Ubuntu 8.04 based on officially suggested way ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) or from binary
but results always the same: 
-NO DRI and AGP and OpenGl vendor is always MESA!! and Google Earth crashed.

Error messages in Xorg.0.log:
(WW) fglrx(0): * DRI initialization failed!                  *
(EE) fglrx(0): [agp] unable to acquire AGP, error -1023
(EE) fglrx(0): cannot init AGP
fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.

The problem: 
AGP not detected in some Intel chipsets 

**Solution:**
See details is [http://openwetware.org/wiki/Computing/Linux/Ubuntu](http://openwetware.org/wiki/Computing/Linux/Ubuntu)
Main steps in my case:
        # rmmod i82875p_edac 
        # rmmod fglrx 
        # rmmod intel-agp 
        # rmmod agpgart 
        # modprobe agpgart 
        # modprobe intel-agp 
        # modprobe fglrx 
blacklist the modules e7xxx_edac -  add the following two lines at the beginning of /etc/modprobe.d/blacklist:
            blacklist i82875p_edac 
            blacklist edac_mc 

Now Mesa AGP DRI Google earth and suspend to RAM (s2ram) works fine. :)

---

