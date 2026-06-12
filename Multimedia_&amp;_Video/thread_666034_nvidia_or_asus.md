---
title: "nvidia or asus"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by bkelly on 2008-01-12
I just received my computer from Eracks. It is running Ubunto 7.10, Gutsy I believe.  The video display is larger than the screen and the entire screen scrolls when I put the cursor at an edge of the screen.  Reducing the resolution does not resolve the problem.

My documentation does not say what model card is installed and the card does not have a model number on it.  After some searching I ran the command:
   lspci -n | grep 0300 
and get the following output:
01:00.0 0300: 10de:01d3 (rev a1)

The mother board has a build in video adapter and it has the ASUS card installed.  I am using the two video ports on the ASUS with a dual monitors.  The graphics adapter on the motherboard has not connector installed.  The ASUS board has the following numbers on the component side:

EN7200GS-CSIC7A8074-02268-CICJ8K-A41-BKA41

and on the flip side I find:

EN7200GS/HTD/256M/A(C381/LP)
7AC0A1540206
N1319
D33005

As usual, digit 1 and lower case letter L may be interchanged and sometimes digit 0 and letter O (oh).

When I log on as root and try to select a driver, the options for ASUS do not match (or come close) to any of the numbers I find on the board.  The ASUS web site was of no help.

Is ASUS associated with NVIDIA?

What model video board is this and what driver should I select?

Thank you

---

### Post by tgalati4 on 2008-01-13
Post the output of:

>lspci -vv

and 

>lsmod

To get more information on your hardware, try 

>sudo lshw

ASUS makes motherboards (and PC's).  nVidia makes chipsets, including high-performance graphics cards and motherboard chipsets, but not complete motherboards (that I am aware of).  They are separate companies.

---

### Post by bkelly on 2008-01-13
hello tgalati4,
Thanks for taking the time to respond.

The video card does have ASUS written on it in upper case letters.  When I select Systems | Administration | Screens and Graphics, I get the video setup window.  When I select the tab Graphics Card, the field for Driver contains nvidia.  When I click on that field, it opens and if I select driver by model and pick ASUS, I find six models, none of which look anything like GeForce73000.  There are a bunch of options under nvidia.  I have plenty of things to learn and will wait for another response before making changes.

 When I entered lspci w it told me invalid option.  I did see a -v option so ran that.  Here is the section for the video adapter:

01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8250
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

&&&&&&&&&&&&&&&&&
Here is the lsmod output.  

sysadmin@DESQ:~$ 
sysadmin@DESQ:~$ lsmod
Module                  Size  Used by
ipv6                  317192  14 
af_packet              28172  2 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
cpufreq_conservative     9608  0 
cpufreq_userspace       6048  0 
cpufreq_stats           8160  0 
cpufreq_ondemand       10896  0 
freq_table              6464  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       3072  0 
container               6400  0 
dock                   12264  0 
video                  21140  0 
sbs                    21520  0 
button                 10400  0 
ac                      7304  0 
battery                12424  0 
lp                     15048  0 
snd_hda_intel         337192  1 
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             41896  1 
snd                    69288  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
parport                44172  3 ppdev,lp,parport_pc
pcspkr                  4608  0 
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
psmouse                45596  0 
serio_raw               9092  0 
nvidia               7013492  34 
i2c_core               30208  1 nvidia
sis190                 25092  0 
mii                     7424  1 sis190
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
evdev                  13056  3 
ext3                  146576  2 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sd_mod                 32512  5 
sg                     41384  0 
sr_mod                 19876  0 
cdrom                  41768  1 sr_mod
sata_sis               11524  3 
floppy                 69608  0 
ehci_hcd               40076  0 
ohci_hcd               25092  0 
usbcore               161584  3 ehci_hcd,ohci_hcd
pata_sis               18564  1 sata_sis
ata_generic             9988  0 
libata                138928  3 sata_sis,pata_sis,ata_generic
scsi_mod              172856  4 sd_mod,sg,sr_mod,libata
thermal                16528  0 
processor              36232  1 thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor

&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&
The output from sudo lshw is a bit long but here is the section for video:

      *-display
                description: VGA compatible controller
                product: G72 [GeForce 7300 SE]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia

Thanks again for taking the time to respond.

---

### Post by bkelly on 2008-01-13
As I continue searching, articles and posts seem to assume that the correct driver is already available.  I don't see any information on how to find and download the right driver.  I found a utility to install the right driver, but it asked me for the install disk.

My system was delivered without disks so I am downloading Ubuntu 7.10 and will burn to a disk.  I "assume" that when I run the install procedure, it will be able to go to the CD and find the driver.   But what happens when that driver is not on the disk?

When delivered, my system worked with dual monitors. (the second was an extension, not a mirror.  Both are Hanns-G with 1280 x 1024 resolution)  Now that I have messed with it, the two monitors mirror each other.  When I use sysadmin or root and adjust the selection under Systems | Administration, my selections now are ignored.

Just to make it easy, the video board seems to be made by ASUS with nvidia chip set for GeForce 7300 SE.

thanks for listening.

---

### Post by FlyingIsFun1217 on 2008-01-13
> **bkelly said:**
> 01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1) (prog-if 00 [VGA])

That says it all. Your running with a GeForce 7300 SE chipset (which is different than the physical card you might see; the card is a board with the chipset on it).

For hardware acceleration, you need the nvidia driver. The easiest way to pick it would be the restricted driver manager (System menu), but I would just reconfigure the xserver:

> 
sudo dpkg-reconfigure xserver-xorg


And choose the nvidia driver when you get that screen.

Personally, I haven't had much luck with Nvidia and Gutsy (7.10). Right now I'm actually downloading mint just to get it to work (well, other reasons too).

FlyingIsFun1217

---

### Post by tgalati4 on 2008-01-13
Also, try running envy to see if it can pick up a newer/better video driver directly from the nVidia repository/website.  I'm not sure if they can improve performance of a 7300 chipset as that is an older architecture.

lspci -vv is actually dash VEE VEE.  It looks like a W.

Sounds like you have some things to experiment with.

---

### Post by bkelly on 2008-01-13
I followed the advice of FlyingIsFun1217 but my system continues to fuss at me.  It keeps resetting the resolution to 800 x600 and the two monitors mirror instead of extend.  I downloaded an install image, burned the disk, and will now run the utility called Envy I found on this site to configure my system. (When first attempted it asked for the install disk, which I did not have.)

I will see what happens with that.  Further advice is solicited and will be welcome.

---

### Post by FlyingIsFun1217 on 2008-01-13
Best of luck using Envy. It makes it easy, but for some reason, Gutsy just doesn't want to play nice with Nvidia.

If all else fails, a fresh install of Feisty (or in my case, linuxmint, which is based off of feisty, with parts of gutsy) will let you use the Nvidia driver with a steady resolution by using just the restricted drivers manager.

FlyingIsFun1217

---

### Post by bkelly on 2008-01-25
After a significant delay on my part, Eracks gave me a quick response and my dual monitors are running.  Here is their procedure with elaborations from me. (i.e. any errors are mine, not theirs)

This procedured worked for me to set up a dual monitor using a graphics 
card by ASUS with nvidia GeForce chips.

Go to the System -> Administration -> Restricted Drivers
Click on the tab "Graphics Card"
In the driver field, select "nvidia"
There is an "nv" but pick the nvidia.
Select the Screen tab and Screen 1.
Pick the model LCD and resolution.  I use Hanns-G monitors which are not listed.  
My selection was "LCD Panel 1280x1204"
Set the resolution as appropriate.
Select Screen 2 and repeat for the second monitor.

After this, I did not just log off as instructed, I rebooted.
My system reverted to a very low graphics mode with nothing on the screen.
When I held the cursor against the edge of a screen, the entire screen
would scroll.  I had to scroll around to find the log in prompt.

After logging back in bring up the command window with ALT-F2.
I selected the Run in terminal option and entered 
	nvidia-settings

The program started and brought up a window.
In the NVIDIA X Server Settings, on the left, I selected 
	X Server Display Configuration
In the Layout field, select the monitors one at a time.
For each monitor, in the Display field, set the resolution.
Just to be certain, reboot and you should be good.

---

