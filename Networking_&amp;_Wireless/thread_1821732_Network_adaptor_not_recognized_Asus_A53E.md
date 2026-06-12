---
title: "Network adaptor not recognized Asus A53E"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by kodb on 2011-08-09
I just purchased an Asus A53E from Newegg for the office.  Like all of my machines I now wipe Windows and install Ubuntu 10.04 LTS desktop.
Installation went no problem but no network adapter is recognized or active.
After searching I did a command line query and the output returned "Realtek 8176" but I am pretty much stuck on how to proceed.  Do I need to dl a driver or is there some other trick to make Ubuntu recognize this particular network controller?  
Thanks
Bob

---

### Post by wildmanne39 on 2011-08-09
Hi, run these commands in the terminal please:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by kodb on 2011-08-09
wildmanne39:
Thanks for the help.  I have to type in the responses because I have zero network on the notebook in question!
```
*-network UNCLAIMED
description: Network Controller
product: Realtek Semiconductor Co
physical id: 0
bus info: pci@000:02:00.0
version: 01
width: 64 bits
clock 33mhz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resource: ioport:c000(size=256) memory: dea0000-dea03fff
*-network UNCLAIMED
description: Ethernet controller
product: Atheros Communications
vendor: Atheros Comm
physical id: 0
bus info: pci@000:03:00.0
version c0
width: 64 bits
clock: 33 mhz
capabilities: pm msi pciexpress vpd bus_master cap_list
resources: memory:de000000-de03ffff ioport:b000(size=128)
```

```
 02:00.0 Network Controller [0280]: Realtek Semiconductor Co ltd.  Device [10ec:8176] (rev01)
```

```
lo        no wireless extensions.
```

```

```  no output in response to rfkill command

```

binfmt_misc     6587    1
ppdev              5259   0
psmouse          63245  0
uvcvideo          56990  0
fbcon               35102  71
tileblit              2031   1 fbcon
font                 7557  1 fbcon
bitblit               4707  1 fbcon
softcurosr         1189  1 bitblit
videodev          34361  1 uvcvideo
vga16fb           11385  1
vgastate          8961  1 vga16fb
video              13251  2 uvcvideo,videodev
output             1871  1  video
v4li_compat      13251  2 uvcvideo,videodev
serio_raw         3978   0
lp                    7028 0
parport            32635 2  ppdev,lp
ahci                 32008  3
```

whew! hope I didn't make any typo's
Thanks for your help!
Bob

---

### Post by wildmanne39 on 2011-08-09
Hi, I am sorry it has taken me so long to get back to you, I have been at the doctor's office all afternoon, I am running a high fever, so I may be slow in responding.

Here is a link to set up your wireless card.

You need to read the last three posts.

You will have to go to another thread and it has a download link, to get your driver.
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667)

You will need to have internet access then download the driver to a usb jump drive or cd, then transfer it to ubuntu.
Thank you

---

### Post by pdc on 2011-08-09
I see from post #10 here

[http://ubuntuforums.org/showthread.php?t=1608908](http://ubuntuforums.org/showthread.php?t=1608908)

that canucked pointed towards a ppa and gave some commands 

they may be helpful as it seemed to work for those posting back

---

### Post by kodb on 2011-08-11
Ok, thanks for the direction: I need to try to download that stuff and transfer via usb drive.
What about the wired ethernet adapter- is there any direction on how to get ubuntu to recognize/claim that adapter as well or will that occur when I load up the above noted drivers?
Bob

PS: I hope you are feeling better wildmanne39!

---

### Post by kodb on 2011-08-11
OK, found the solution for the wired card (Atheros 1083) here:
[HTML]http://ubuntuforums.org/showthread.php?t=1806056&highlight=atheros+1083[/HTML]You have to find the download link for the Atheros drivers as they have been moved following qualcomm's acquistion but I was able to link over eventually.

[http://ifile.it/cfzeko0/AR81Family-linux-v1.0.1.14.zip](http://ifile.it/cfzeko0/AR81Family-linux-v1.0.1.14.zip)

After you download the link there are errors when you try to decompress.  Do not use the Archive Manager!  Same problem in command line.   Instead:
1. Open the above file using the Archive Mounter.  Copy the folder to the  /home directory and then follow the directions in:

[http://tuxthink.blogspot.com/2010/08/enabling-atheros-ethernet-controller-on.html](http://tuxthink.blogspot.com/2010/08/enabling-atheros-ethernet-controller-on.html)

Still working on the wireless per above...
Bob

---

### Post by fvg007 on 2011-08-11
I am running windows 7 Pro 64bit as Host and running virtualBox - Ubuntu 11.04 here..My host machine is connected d-link 140 usb adapter.  In my virtualbox, ubuntu has no problem connected to internet.  Questions: I like to run feedingbottle to scan my network, but it wont able to find the network card.

Any one can help. Thank you in advance

---

### Post by kodb on 2011-08-14
ok, still no joy on the wireless despite following the directions above.
The wired is working great via the directions I listed above
Bob

---

### Post by wildmanne39 on 2013-02-08
Old thread closed.

---

