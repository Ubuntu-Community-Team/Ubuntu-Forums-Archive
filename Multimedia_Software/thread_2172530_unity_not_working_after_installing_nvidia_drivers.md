---
title: "unity not working after installing nvidia drivers"
date: 2013-09-05
forum: Multimedia Software
---

### Post by rookiewannacookie on 2013-09-05
hello all,

let me start by saying that im new to ubuntu well... linux period. i installed ubuntu 13.04 (raring ringtail) installed java and some other meaningless files for android development. desided i wanted better graphics and dual monitors so i inserted the nvidia geforce 5500 fx graphics card into the computer and turned it on. at first everything was ok i had my main monitor (call it monitor1) working and the display settings recognized both monitors but would only show picture on monitor1 so i figured drivers where required. this is where things get all botched up... not knowing what im doing i did a little googling and found a guide to help me install nvidia drivers. well first i didnt know i couldnt do it from a terminal, secondly i wasnt even sure of which drivers i needed as im used to being on windows and using the cd that came with the card to install the drivers. i digress, installed the nvidia-currents drivers rebooted and unity was gone (top and side bar), desktop would boot normally but im presented with nothing but the wallpaper and my screen resolution was set (stuck) at 640x480 so i uninstalled the drivers (i think) and install nvidia 304.** but that didnt fix anything so i uninstalled them(again i think) and found that i require nvidia 174.14.** for my particular graphics card, installed them and somehow or another got my screen resolution to go back to normal but i still dont have unity and monitor2 is still not recognized...

would like to figure this out as im tired of windows and need linux to develop for android but with all that i've been through with this thing already im starting to get discouraged and thinking about going back to windows. any and all help is appreciated.

---

### Post by buzzingrobot on 2013-09-05
Can't tell you how to fix things since it's not clear what you've done, but...


The recommended, and easiest, way to install proprietary drivers, like the Nvidia drivers, on Ubuntu, is via "Additional Drivers". This is available on a tab in the Software Sources app. Tap the Windows key, start typing "Software Sources" and you'll see the icon displayed.


This should list a number of drivers that can work for your card. Select one and it will be installed.


In general, many traditional ways of doing things in Windows do not transfer to Linux. Two different systems, etc. A visit to ubuntu.com and a look at some of the basic docs is helpful.

---

### Post by rookiewannacookie on 2013-09-05
> **buzzingrobot said:**
> Can't tell you how to fix things since it's not clear what you've done, but...


The recommended, and easiest, way to install proprietary drivers, like the Nvidia drivers, on Ubuntu, is via "Additional Drivers". This is available on a tab in the Software Sources app. Tap the Windows key, start typing "Software Sources" and you'll see the icon displayed.


This should list a number of drivers that can work for your card. Select one and it will be installed.


In general, many traditional ways of doing things in Windows do not transfer to Linux. Two different systems, etc. A visit to ubuntu.com and a look at some of the basic docs is helpful.

cant really tell you what all i've done as i myself dont even know TBH, but i can tell you i tryed the "Additional Drivers" thing and the list was blank, so i started using the terminal to manually install the drivers using the guide here [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html) as i stated before this is where everything got messed up as i didnt realize i had to do this using a console and not on the terminal. tryed things like compiz (unity plugin was not selected but selecting it has had no effect. when i try to open the nvidia server settings window i only get matched with "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." tryed running the command

sudo nvidia-xconfig

as it says to do but that just returns some minor info about it backing up the file "xorg.conf" to "xorg.conf.old" or something like that.

---

### Post by buzzingrobot on 2013-09-05
> **rookiewannacookie said:**
> .... i tryed the "Additional Drivers" thing and the list was blank, so i started using the terminal to manually install the drivers using the guide here [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html) as i stated before this is where everything got messed up as i didnt realize i had to do this using a console and not on the terminal. tryed things like compiz (unity plugin was not selected but selecting it has had no effect. when i try to open the nvidia server settings window i only get matched with "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." tryed running the command

sudo nvidia-xconfig

as it says to do but that just returns some minor info about it backing up the file "xorg.conf" to "xorg.conf.old" or something like that.

Well, that's odd. In laptops with two video cards -- onboard Intel and an Nvidia or AMD card -- the Nvidia or AMD won't be detected if it's disabled in BIOS. 

I've used Dedoimedo's guide successfully.  Everything he suggests should work equally in a terminal window or on a console. 

You saw the correct response from nvidia-xconfig.  it creates the xorg.conf file the Nvdia driver needs.  If one already exists, it creates a backup and then creates a new one. Reboot and you *should* be using the driver. 

(One issue I have seen with Nvidia installs on a number of distributions is that the xorg.conf file may not be created.  The user will reboot and the system will appear broken.  So, I routinely run nvdia-xconfig myself, just to be sure.)

One tell-tale signal that an Ubuntu machine is on an Nvidia driver is that the pretty Plymouth boot screens go away.  You typically see the purplish Ubuntu backdrop with the release name and version in the center.

Just to cover the perfectly obvious, you are certain the card is correctly seated?  I have an Nvidia card that refused to work unless it was installed "just so". Took hours to figure that out.

---

### Post by rookiewannacookie on 2013-09-05
> **buzzingrobot said:**
> Well, that's odd. In laptops with two video cards -- onboard Intel and an Nvidia or AMD card -- the Nvidia or AMD won't be detected if it's disabled in BIOS. 

I've used Dedoimedo's guide successfully.  Everything he suggests should work equally in a terminal window or on a console. 

You saw the correct response from nvidia-xconfig.  it creates the xorg.conf file the Nvdia driver needs.  If one already exists, it creates a backup and then creates a new one. Reboot and you *should* be using the driver. 

One tell-tale signal that an Ubuntu machine is on an Nvidia driver is that the pretty Plymouth boot screens go away.  You typically see the purplish Ubuntu backdrop with the release name and version in the center.

Just to cover the perfectly obvious, you are certain the card is correctly seated?  I have an Nvidia card that refused to work unless it was installed "just so". Took hours to figure that out.


when it boots it shows the word *ubuntu* with 5 dots in the center. and yeah i double checked to make sure the card was seated. could it be that the onboard intel drivers somehow got removed? 
```
$ lspci -nn | grep -i vga

00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)
03:01.0 VGA compatible controller [0300]: NVIDIA Corporation NV34 [GeForce FX 5500] [10de:0326] (rev a1)
```

```
$ sudo lshw -C display

  *-display               
       description: Display controller
       product: 82915G/GV/910GL Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:dff80000-dfffffff ioport:ecd8(size=8) memory:b0000000-bfffffff memory:dff40000-dff7ffff
  *-display
       description: VGA compatible controller
       product: NV34 [GeForce FX 5500]
       vendor: NVIDIA Corporation
       physical id: 1
       bus info: pci@0000:03:01.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=64 maxlatency=1 mingnt=5
       resources: irq:17 memory:de000000-deffffff memory:c0000000-cfffffff memory:dfc00000-dfc1ffff
```

just some commands i found not sure if it helps or not...

---

### Post by buzzingrobot on 2013-09-05
They show the machine knows about the Nvidia card and the Intel card. They don't show which one it wants to use.   

"lsmod" will list the modules the kernel is using. I'm on a ThinkPad using the onboard Intel and it includes this: "video    19390  1 i915"

I have the Nvida card disabled in BIOS and lspci and lshw don't see it.

I'm not certain, but the presence of the Nvidia xorg.conf may prevent the Intel from being used.  Perhaps someone else can chip in here.




On a laptop, I'd disable the Intel, reboot, and see what happens. Does your BIOS offer that? 

What happens after the boot display with the 5 dots?  The dots should be sequentially changing color, and then you should boot into Unity.

---

### Post by rookiewannacookie on 2013-09-05
> **buzzingrobot said:**
> They show the machine knows about the Nvidia card and the Intel card. They don't show which one it wants to use.   

"lsmod" will list the modules the kernel is using. I'm on a ThinkPad using the onboard Intel and it includes this: "video    19390  1 i915"

I have the Nvida card disabled in BIOS and lspci and lshw don't see it.

I'm not certain, but the presence of the Nvidia xorg.conf may prevent the Intel from being used.  Perhaps someone else can chip in here.




On a laptop, I'd disable the Intel, reboot, and see what happens. Does your BIOS offer that? 

What happens after the boot display with the 5 dots?  The dots should be sequentially changing color, and then you should boot into Unity.

yes and no my BIOS offers which card i want to use at post boot at one point it would only boot loop when i tryed to use the nvidia card (probably due to the lack of drivers) havent tryed it as of yet will do when i reboot though and post results.

as for the boot screen yes they change color as if it was loading then it boots to the desktop-environment (unity) but with only the wallpaper as stated before, no side or topbar.

```
$lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39211  1 
snd_hda_codec_idt      63896  1 
gpio_ich               13236  0 
snd_hda_intel          38307  6 
snd_hda_codec         117617  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
dcdbas                 14021  0 
nvidia               7108000  0 
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
i915                  535505  2 
snd_seq_midi_event     14475  1 snd_seq_midi
parport_pc             27504  0 
microcode              18286  0 
video                  18894  1 i915
ppdev                  12817  0 
snd_rawmidi            25114  1 snd_seq_midi
drm_kms_helper         47545  1 i915
bnep                   17669  2 
rfcomm                 37420  12 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
drm                   228489  3 i915,drm_kms_helper
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
btusb                  17986  0 
binfmt_misc            17260  1 
snd_timer              24411  2 snd_pcm,snd_seq
psmouse                81065  0 
lpc_ich                16925  0 
mac_hid                13037  0 
serio_raw              13031  0 
i2c_algo_bit           13197  1 i915
bluetooth             202109  22 bnep,btusb,rfcomm
ext2                   63166  1 
snd                    56485  21 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
usb_storage            47684  0 
e100                   35903  0 
floppy                 55441  0 

```

heres that. will post results of reboot.

---

### Post by rookiewannacookie on 2013-09-05
reboot still yields a nice big bowl of bootloops. never goes past post boot.

---

### Post by buzzingrobot on 2013-09-05
> **rookiewannacookie said:**
> .

as for the boot screen yes they change color as if it was loading then it boots to the desktop-environment (unity) but with only the wallpaper as stated before, no side or topbar. 

lsmod is showing both the nvidia and intel modules are loading.  Since you got as far as you did,  one of the drivers is working. Here, "sudo lshw -c video" produces output that includes "configuration: driver =i915 latency=0" which tells me that it is using the i915 driver for the Intel, as it should be since the Nvida is disabled.

If the same command shows your machine is using the Intel, then I will guess that you need to disable the Intel and enable the Nvidia in BIOS.

My suspicion, though, is that you are using the Nvdia.

I once had the same problem with the Unity Launcher and top panel seemingly being pushed off screen. I searched for and found several "fixes" but they all involved deleting and re-installing many core packages.  I couldn't make it work.  In the end, the quickest and easiest route was just reinstalling.

I'm not a gamer. I have no issues using the Intel for videos, Flash, etc.  But, I don't use an external monitor with my laptop.  I believe the Intel can't support an external display.

When I have installed the Nvidia driver, I installed it with the Intel driver active.  I rebooted, enteedr the BIOS, disabled the Intel and enabled the Nvidia, continued the boot, and all was well.

---

### Post by rookiewannacookie on 2013-09-05
> **buzzingrobot said:**
> lsmod is showing both the nvidia and intel modules are loading.  Since you got as far as you did,  one of the drivers is working. Here, "sudo lshw -c video" produces output that includes "configuration: driver =i915 latency=0" which tells me that it is using the i915 driver for the Intel, as it should be since the Nvida is disabled.

If the same command shows your machine is using the Intel, then I will guess that you need to disable the Intel and enable the Nvidia in BIOS.

My suspicion, though, is that you are using the Nvdia.

I once had the same problem with the Unity Launcher and top panel seemingly being pushed off screen. I searched for and found several "fixes" but they all involved deleting and re-installing many core packages.  I couldn't make it work.  In the end, the quickest and easiest route was just reinstalling.

I'm not a gamer. I have no issues using the Intel for videos, Flash, etc.  But, I don't use an external monitor with my laptop.  I believe the Intel can't support an external display.

When I have installed the Nvidia driver, I installed it with the Intel driver active.  I rebooted, enteedr the BIOS, disabled the Intel and enabled the Nvidia, continued the boot, and all was well.


well i got unity back by removing any and all things dealing with Nvidia. that command you gave me returned these values

```
 $ sudo lshw -c video
  *-display                      description: VGA compatible controller
       product: 82915G/GV/910GL Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:dff80000-dfffffff ioport:ecd8(size=8) memory:b0000000-bfffffff memory:dff40000-dff7ffff
  *-display
       description: VGA compatible controller
       product: NV34 [GeForce FX 5500]
       vendor: NVIDIA Corporation
       physical id: 1
       bus info: pci@0000:03:01.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=64 maxlatency=1 mingnt=5
       resources: irq:17 memory:de000000-deffffff memory:c0000000-cfffffff memory:dfc00000-dfc1ffff

```

gonna try and see if i can find the correct drivers for Nvidia now... read somewhere that the GeForce FX5500 needs the 173 legacy drivers which im assuming is diff then the 173 drivers i installed.

i dont game on my pc either its way to slow for the "now a day" games mostly use it for movies which is why i need the nvidia graphics card it has the s-video support that my tv takes. trying to get into android development also which is the whole reason im even bothering with this instead of just reverting back to win7.

imma go ahead and say thanks for all your help thus far hopefully i will get it working tomorrow if not tonight.

---

### Post by rookiewannacookie on 2013-09-06
ok so i installed Synaptic PM and found the drivers installed them did the "nvidia-xconfig" command and rebooted set BIOS to run on the nvidia graphics card and proceeded to boot into buntu where i was met with a black screen after 10 mins of waiting i figured it wasnt going anywhere so i rebooted again put it back to run on the Intel card and once again im faced with no unity...

not really sure where to go from here anymore as it seems my efforts keep bringing me back to unity and my second monitor not working.

---

### Post by rookiewannacookie on 2013-09-06
found acouple of posts saying install and open compiz and enable unity that way but when i do it says it needs to enable OpenGL also so i click to enable it but after a brief second and some screen flashing it unchecks itself along with unity and anything else that needs OpenGL...

---

### Post by buzzingrobot on 2013-09-06
Good luck.  I took a quick look around and it seems the FX5500 is an older card that's an issue for many folks. Hope the legacy driver will do the trick.

---

### Post by rookiewannacookie on 2013-09-06
> **buzzingrobot said:**
> Good luck.  I took a quick look around and it seems the FX5500 is an older card that's an issue for many folks. Hope the legacy driver will do the trick.


good morning friend =)

im sad to report that again it didnt work with synaptic however the packages in there had no mention of "legacy" anywhere just said nvidia-173 so i think i still got the same package as from the apt-get repo. desided im giving it one more day then imma say forget it and go back to winblows7.



p.s. not really sure why linux has to be so difficult in the installing of hardware\software when on windows i woulda had it done 3 days ago. simple plug in and go... but hey i guess if it doesnt take effort its not worth using huh?!? ;-)

---

### Post by buzzingrobot on 2013-09-06
Well, it usually is easy to install. There are complicating issues here:

1.  Your card is a bit on the old side. I'm not sure of the state of its Linux support. Or, if Unity can run on it.
2.  No one knows what's in Nvidia's drivers because they don't release the code.  So, Linux developers are working against unknowns.  If Nvidia changes something, Linux developers only see the release notes, they don't know what the code does.  More than once, things have gone awry. (Nvidia drivers did not work on one of my machines for an entire kernel series.) Presumably, financial arrangements allow MS and Nvidia to share relevant code.
3.  There is an open source driver for Nvidia, Nouveau.  It's based on reverse-engineering. Can't match Nvidia on speed and 3D but it's fine for routine work.
4.  All installs, even in Windows, assume a base system.  If you altered your system in those initial efforts and didn't roll it back, problems aren't surprising.
5.  I suspect your problem with the incorrect display of Unity may not be a driver issue.  One of your cards is working, otherwise you'd see a black screen, but you're seeing a broken Unity screen. A reinstall is the best way to get to a clean slate and try again.

---

### Post by rookiewannacookie on 2013-09-06
a fresh install of ubuntu is out of the question for me. if i dont get it working tonight im going back to windows, already spent too much time just trying to get the system set up for android development and really discouraged about using linux altogether...

---

### Post by buzzingrobot on 2013-09-06
No problem.  I spent days trying to get font rendering in Windows 7 or Windows 8 to look something less than awful on this ThinkPad. (I'd promised to help a Windows-bound friend do some basic labor with several thousand photos.) Multiple installs, etc., etc. Nothing worked, so I stopped trying.

---

### Post by rookiewannacookie on 2013-09-06
> **buzzingrobot said:**
> No problem.  I spent days trying to get font rendering in Windows 7 or Windows 8 to look something less than awful on this ThinkPad. (I'd promised to help a Windows-bound friend do some basic labor with several thousand photos.) Multiple installs, etc., etc. Nothing worked, so I stopped trying.

ok so with all that ive been through i think i've narrowed it down to an issue with OpenGL not loading in compiz. been searching to find a fix but to no avail so far most everything just says reinstall compiz or reformat and the first options havent worked so far...

---

### Post by rookiewannacookie on 2013-09-06
ok so i deff think i found the issue now!!! 

the following showed me that things may still have been botched while trying to install nvidia

```
~$ dpkg -l | grep nvidiaii  nvidia-173                                173.14.37-0ubuntu1                                                     i386         NVIDIA binary Xorg driver, kernel module and VDPAU library


```

is what it shows now that i've removed all things dealing with Nvidia 304 seems i was still getting the Nvidia-304 settings found the correct settings menu i need gonna install them and see where it leads me.

---

### Post by buzzingrobot on 2013-09-06
Right, I found out the hard way that the "nvidia-settings" package needs to match the installed driver. 

Besides the failure to run nvidia-xconfig I mentioned earlier, I've also run across installs that install the Nvidia Settings icon (it's the Nvidia control panel) but don't install the actual package. So, you click and nothing happens.

---

### Post by rookiewannacookie on 2013-09-06
> **buzzingrobot said:**
> Right, I found out the hard way that the "nvidia-settings" package needs to match the installed driver. 

Besides the failure to run nvidia-xconfig I mentioned earlier, I've also run across installs that install the Nvidia Settings icon (it's the Nvidia control panel) but don't install the actual package. So, you click and nothing happens.


ok so i have spent the last however long its been since my last post installing EVERY...SINGLE...PACKAGE dealing with nvidia-173 and the likes of and this is still not working... so im frustrated im tired and im going back to good ol' reliable windows7... i thank you for your help and wish the best of luck to anyone else who stumbles apon this thread in there quest to get the Nvidia GeForce FX 5500 drivers to work... so long crapbuntu i learned alittle bit of nothing from you... ;-)

---

### Post by buzzingrobot on 2013-09-07
Funny how different folks have different experiences.  I've ever had real problems with Nvidia on a number of Linux machines. But, last month I spent hours and hours trying to get Windows to look less than horrific and couldn't.  People on the Windows sites kept telling me I was wrong, that I couldn't be seeing what I was seeing.  So, I spent 15 minutes and put Ubuntu on the machine. Kinda ticked, tho, that I have about $400 in Windows install DVD's sitting on a shelf.

---

### Post by Bucky Ball on 2013-09-07
Enough said. Goodbye and good luck.

*Thread moved to **Multimedia & Video*** and shortly after *** Thread Closed.***

---

