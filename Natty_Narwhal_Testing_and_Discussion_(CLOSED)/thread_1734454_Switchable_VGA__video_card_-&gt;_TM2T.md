---
title: "Switchable VGA / video card -&gt; TM2T"
date: 2011-04-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tembares on 2011-04-20
Thank you for reading my post.

For my information:
I red some posts about ATI graphic cards.
On my HP TM2T 2100 CTO Touchsmart I have 2 graphic cards: an Intel i915 and ATI HD5450.

All information about the ATI cards I red, can I switch graphics in Natty when the ATI problems are solved which I could not in Maverick?

Thank you in advance

---

### Post by dino99 on 2011-04-20
some help:

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

---

### Post by tembares on 2011-04-20
> **dino99 said:**
> some help:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

Thank you very much, very helpful.

I was on this page before and tried figuring that out.

The thing is that when fglrx or the ATI prop.driver is not installed I can use vgaswitchero and when it is installed/activated I cannot.

The first line of your suggested link to test if the kernel is compiled with vga_switcheroo **succeeded**:
[I]bla:~$ grep -i switcheroo /boot/config-2.6.*
CONFIG_VGA_SWITCHEROO=y[/I]

The next test to see if vga-switcheroo is enabled **failed**:
[I]bla:~$ sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch
ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory[/I]

To enable vga_switcheroo I had to add 'modeset=1' and/or NOT use 'nomodeset'.
The following source is from my grub.cfg:
[I]menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root f51f9d69-db23-4c63-a3e5-73dba0e1bbf7
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=f51f9d69-db23-4c63-a3e5-73dba0e1bbf7 ro   **modeset=1** quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}[/I]

Because I first started Ubuntu without 'modeset=1' and 'nomodeset' and vga_switcheroo was not enabled I added 'modeset=1' to GRUB to 'force' it.
It still is not enabled.

**Why is vga_switcheroo not enabled?**

I wrote the following earlier about this with some testing results, but until now I had no comments on that:
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
When I have NOT installed the prop. ATI driver I can use vgaswitcheroo/switch which is in /sys/kernel/debug/vgaswitcheroo/switch.
When I use vgaswitcheroo/switch I see my 2 cards (Intel i915 and ATI HD5450), but by switching to the ATI I come into textmode and nothing works anymore. In my opinion this is normal, because the driver's not installed.

So I installed the prop. ATI driver, but then vgaswitcheroo/switch is disappeared.

When I go to System->Preferences I see 2 ATI Catalyst Control Centers: administrator and w/o admin. When I choose one of them (does not matter which one I choose) I get this message:
****************************
[I]There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.[/I]
****************************

I removed xorg.conf and did 'sudo aticonfig --initial -f' after installation the prop. ATI driver.

[cut]

To continue the story and testing:
bla:~$ sudo aticonfig --initial=check
Check: No fglrx section.

bla:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 43 not upgraded.

It seems FGLRX is installed, SYSTEM/ADMINISTRATION/ADDITIONAL DRIVERS it is activated.

What is going on?

EDIT 2:
bla:~$ aticonfig --list-adapters
* 0. 01:00.0 ATI Mobility Radeon HD 5000 Series

* - Default adapter

So, this means I am working on the ATI card now?
Why is HDMI not working and why can't I switch to it?
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

I hope you can help me further.

---

