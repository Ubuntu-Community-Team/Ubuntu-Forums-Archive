---
title: "Natty fails to boot"
date: 2011-03-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by libihero on 2011-03-23
when i choose natty on grub, it will hang 4/5 times. i have to force a shutdown, and then choose natty again, over and over, until finally it decides to boot. how can i file a bug report for this?

---

### Post by wilee-nilee on 2011-03-24
post the output from this command in the terminal.
sudo fdisk -lu

---

### Post by libihero on 2011-03-24
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc515122e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   204802047   102400000    7  HPFS/NTFS
/dev/sda2       246360062   488392064   121016001+   5  Extended
/dev/sda3       204802048   246358015    20777984   83  Linux
/dev/sda5       478238985   488392064     5076540   82  Linux swap / Solaris
/dev/sda6       246360064   457369599   105504768   83  Linux
/dev/sda7       457371648   478220287    10424320   83  Linux

Partition table entries are not in disk order

```

---

### Post by wilee-nilee on 2011-03-24
Since Natty was installed last it has the boot control and is grub2.

You can move that control to the other Linux if it is grub2 as well.

From the distro in the terminal.
sudo grub-install /dev/sda
then
sudo update-grub

If your running burg sub burg where grub is.

To confirm if you running grub2=1.97 or beyond running the terminal.
sudo grub-install -v

Not sure if is is the fix maybe a update grub in Natty needs to be run.

---

### Post by libihero on 2011-03-24
i should do sudo grub-install /dev/sda*number*?

---

### Post by wilee-nilee on 2011-03-24
> **libihero said:**
> i should do sudo grub-install /dev/sda*number*?

In a stable install if you have one no number your putting grub in the mbr=sda.

It would help if you identified the linux partitions in the fdisk what is installed in each one.

---

### Post by libihero on 2011-04-02
i tried what you said but it didnt work :(

---

### Post by giant420 on 2011-04-02
I am having a pretty similar issue. I was running 10.10 with no problems, but once I updated to Natty Alpha 3 I began having problems with boot. I would say about 75% of the time it will boot to a solid black screen. Eventually if I continue to power off and restart it will boot. 

Here is the output of my fdisk -lu and grub-install -v


```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022f5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   231290879   115644416   83  Linux
/dev/sda2       231290880   234440703     1574912    5  Extended
/dev/sda5       231292928   234440703     1573888   82  Linux swap / Solaris
giant@T400:~$ sudo grub-install -v
grub-install (GRUB) 1.99~rc1-8ubuntu1

```

---

### Post by kansasnoob on 2011-04-02
If you remove the "quiet splash" from the boot parameter the text may give you a clue as to what's hanging, maybe :confused:

If you have more than one Ubuntu/grub installed you need to know which one is controlling boot. Then the easiest way is to just run:

```
sudo dpkg-reconfigure grub-pc
```

The debconf windows are easily navigated using Tab, Backspace, Enter and the spacebar.

---

### Post by giant420 on 2011-04-02
> **kansasnoob said:**
> If you remove the "quiet splash" from the boot parameter the text may give you a clue as to what's hanging, maybe :confused:

If you have more than one Ubuntu/grub installed you need to know which one is controlling boot. Then the easiest way is to just run:

```
sudo dpkg-reconfigure grub-pc
```

The debconf windows are easily navigated using Tab, Backspace, Enter and the spacebar.

Okay, after removing the "quiet splash" parameter I was able to see where it hangs. It definitely looks to be graphics related for me. It hangs at: 

[3.437157] fb1: VESA VGA frame buffer device

Even when it boots normally it seems to pause there for a second..

---

### Post by kansasnoob on 2011-04-02
What graphics card do you have? This command would provide specifics:

```
lspci | grep VGA
```

---

### Post by giant420 on 2011-04-02
I am using a lenovo t500 laptop with "switchable graphics", so there are technically two cards; an intel and an ATI. I am assuming that the switching doesnt work on linux (havent looked in to it), but I am hoping it knows to use the radeon over the intel. I had installed the ATI drivers at one point before I upgraded to natty.

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

```

---

### Post by kansasnoob on 2011-04-02
I have no idea how the "switching" works on that. It varies greatly based on hardware, etc. I do have a setup with VIA graphics that I added a really old PCI video card to and I had to fiddle around in the BIOS ............ something about "palette snoop" and then I had to choose which card to use.

It was very confusing to me but I tend to think you'd be better off with the Intel gpu if you can figure out how to switch which is used.

---

### Post by giant420 on 2011-04-02
> **kansasnoob said:**
> I have no idea how the "switching" works on that. It varies greatly based on hardware, etc. I do have a setup with VIA graphics that I added a really old PCI video card to and I had to fiddle around in the BIOS ............ something about "palette snoop" and then I had to choose which card to use.

It was very confusing to me but I tend to think you'd be better off with the Intel gpu if you can figure out how to switch which is used.

Aha, I think I may have fixed my problem. Your post lead me on a search which lead me to another thread (post # 3 [here]("http://ubuntuforums.org/showthread.php?t=1050142") for future reference) that said to disable OS detection for switchable graphics in the BIOS, and do all switching manually there. I set everything to use the PCIE graphics (ATI) and everything works 100%! I boot to the login screen in 15 seconds again. Thanks for the help! :guitar:

---

### Post by kansasnoob on 2011-04-02
Thanks for posting the fix you found :)

Too few people bother posting solutions they've found.

---

### Post by benjamimgois on 2011-04-02
I have exactly the same problem. My laptop has also 2 VGA:


> lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M93 [Mobility Radeon HD 4500 Series]


But the bios of my HP laptop do not have options to disable swtichable graphics. It used to work just fine on Maverick. Any clues ?

---

### Post by giant420 on 2011-04-02
> **benjamimgois said:**
> I have exactly the same problem. My laptop has also 2 VGA:

But the bios of my HP laptop do not have options to disable swtichable graphics. It used to work just fine on Maverick. Any clues ?

Hm, after a quick google search, it looks like many other people are complaining of the same thing. For the HP laptops, there is no way to disable the switchable graphics in the bios. They do provide a handy windows utility, but no Linux support. AFAIK there is no software solution available..

---

### Post by edster on 2011-04-06
Thanks for the pointers, I too was experiencing a failure to fully boot 4 out of 5 times on a lenovo T500.  Graphics cards:

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

removing 'quiet splash' would show

> udevd-work[77]: '/sbin/modprobe -bv pci:v00001002d00009591sv000017AAsd00002116bc03sc00i00' unexpected exit with status 0x0009
[...]
IP: [<f87cf7be>] drm_mode_connector_update_edid_property+0x5e/0x170[drm]

and trying 'rdblacklist=radeon' when booting would simply give me a crash screen at higher resolution...

Switching to discrete graphics / disabling 'switchable graphics' in the bios did the trick!

---

### Post by libihero on 2011-04-11
i cant switch the graphics on mine either... is there any way to file a bug for this or how is there already one?

---

### Post by Duncan Williams on 2011-04-11
I am new to ubuntu (3 weeks).
10.10 worked fine with my nvidia (geforce 5200 I think) 128mb video card.
After installing natty I get a black screen after clicking on ubuntu at boot. (it sounds like it has booted into ubuntu though.

If I use > recovery > use failsafe graphics for this session.
Everything works fine, Except say youtube videos seem a little shaky. My 24" monitor is correctly coming up at 1900 by 1080.

---

### Post by Duncan Williams on 2011-04-12
Well my boot problems must have been video card related as it boots now.
-------------
No proprietory drivers after last install of natty.
I was advised in additional drivers of:
experimental 3D support for NVIDIA cards.
This driver provides a highly experimental 3D acceleration for NVIDIA graphics cards, as a free alternative to the proprietary driver.
You need to restart your desktop session after installation.

Thats when my pc would boot to a blank screen in ubuntu mode.
(I used failsafe graphics mode to get into gnome)

After installing updates yesterday.
There were amongst the updates NVIDIA related and nouvea and experimental.

After a few reboots:
I am now booting straight into unity mode ubuntu with full support for my fx5200 card. and no noticeable problems.

The resolution is superb on my 24" monitor > the best it has been, photos are now clearer than any previous installation of either windows or ubuntu.
___________

---

### Post by libihero on 2011-04-17
bump... still having this problem... :(

---

### Post by ndstate on 2011-04-17
I can't even boot from the install disk with the Mobility Radeon HD 3400 Series graphics card.  Any ideas?

---

### Post by libihero on 2011-04-17
o btw my graphics card is ATI Radeon X1200

---

### Post by libihero on 2011-04-19
bump... 
filing a bug report anyways :) but lemme kno if someone figures this out

---

