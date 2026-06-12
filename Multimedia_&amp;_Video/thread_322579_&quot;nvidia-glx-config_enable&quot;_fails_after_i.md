---
title: "&quot;nvidia-glx-config enable&quot; fails after installing nvidia-glx"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by dishbert on 2006-12-20
i used Synaptic to install nvidia-glx, the installation was successfull and came with a new kernel image as well.  But when I try:

chris@downstairs:~$ sudo nvidia-glx-config enable

I get this:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

But my xorg.conf has no line with nv.  I think this is the line where it is supposed to appear:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"VX2025wm"
	Option		"DPMS"

I've searched the forums but I don't seem to be able to find an answer on how to proceed.
Should I change "vesa" to nvidia?  Or try the md5sum command?

(I see I should change my signature block to identify my new FX6200 card).

---

### Post by mid_night gypsy on 2006-12-20
dishbert,
 Yes,You do need to change Driver "vesa" to Driver "nvidia" and then reboot.
                                                                                                                           good luck,gypsy

---

### Post by dishbert on 2006-12-20
gypsy, thanks for trying to help, but that turned out to be a BAD suggestion.

X failed on reboot, and I had to use a live CD to get back into xorg.conf to change it back.

---

### Post by Cariboo1938 on 2006-12-20
> **dishbert said:**
> gypsy, thanks for trying to help, but that turned out to be a BAD suggestion.
X failed on reboot, and I had to use a live CD to get back into xorg.conf to change it back.
Hi,
I'm sitting in the same boat...since more than a week I try.... always with the same result: xserver failes to start after installing nvidia driver. 
I'm desperately waiting for some suggestions which work.

---

### Post by dishbert on 2006-12-20
Maybe it's because we're both in BC?

Did you use Synaptic to install nvidia-glx?  If so, did it come with a new kernel image, as mine did?  

I somehow think that's where mine started to go so very very wrong.  A new kernel was installed at the top of my GRUB logon screen, pointing to the new kernel, but X fails with either the new one 2.6.15.27, or the original 2.6.15.23.

---

### Post by Cariboo1938 on 2006-12-21
> **dishbert said:**
> Maybe it's because we're both in BC?
Did you use Synaptic to install nvidia-glx?  If so, did it come with a new kernel image, as mine did?  
...... Hello BC,
No, I didn't yet. I'm not sure if there is any working solution available right now. I checked [HERE]("http://www.ubuntuforums.org/showthread.php?t=322476&highlight=NVIDIA") and got even more confused. I didn't get any useful answer to my questions at [THIS ]("http://www.ubuntuforums.org/showthread.php?t=318206&highlight=NVIDIA")forum yet! Maybe I have to wait...for a miracle! BTW my kernel is 2.6.17-10-generic.
Cheers
Cariboo

---

### Post by dishbert on 2006-12-21
Well I'm leaving tomorrow for the Island for a few weeks, so I think I'll put this project off until the new year anyway.

Happy Holidays Cariboo

---

### Post by Cariboo1938 on 2006-12-21
> **dishbert said:**
>  
Happy Holidays CaribooSame to You! Maybe I can offer you the solution when you are back!!!
Cheers:D

---

