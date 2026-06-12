---
title: "failed to get i915 symbols, graphics turbo disabled error on boot"
date: 2010-10-12
forum: Multimedia Software
---

### Post by LaMooNa on 2010-10-12
I have Toshiba Satellite L650 with ATI Radeon HD 5600 Series. I new with ubuntu and I have the new release 10.10
can anybody help me please :)

---

### Post by delang on 2010-10-12
hi,
im also have the same error message after upgrading from lucid. im on lenovo g460 nvidia geforce 310m

---

### Post by KoSa333 on 2010-10-16
Hi, the same here. I guess it must be a problem with the Intel Core i (M) CPU (i have i540M in my notebook). It has an integrated GPU which gets disabled I think. Anyway, I have nvidia 330M GPU which works just fine.

---

### Post by LaMooNa on 2010-10-16
yes I think so, I have core i5 430M which has the same HD GPU & have Radeon 5650 HD works fine.
So, this is a bug in ubuntu, they should solve it

---

### Post by Chris1274 on 2010-10-19
I get the same error message, only I don't have a discrete graphics card, only the integrated card. So it's not disabling the integrated graphics, otherwise I'd have none. I have an Intel i3.

---

### Post by umbeebmu on 2010-10-19
same message with i5 M450 + ATI Mobility Radeon HD 5000 Series, Ubuntu 10.10.

System seems to run ok but once in a while the screen freeze (including the mouse pointer) and I can only poweroff/on to recover.

Can this be the cause?
(I am seriously considering to go back to windows after many years of Ubuntu because of this!!)

---

### Post by bpickel on 2010-10-21
This is certainly due to the integrated graphics chip. Under Windows the Intel chip can run graphics while the graphic accelerator cores can be used for co-processing. Nvidia calls its technology CUDA.  These GPUs are "Massively Parallel Processor Cores". The have been in use by large enterprise and  for scientific research and are now making it mainstream as Windows 7 and Snow Leopard support CUDA natively. That coupled with the fact that it is a feature of NVIDIA's latest business and workstation oriented GPUs such as the Quadro. If you will notice late model Dells can EFI boot and now have LatitudeON which is a small Linux installation that runs on a low power integrated circuit and boots instantly allowing, web browsing, email and media playback. 

Change is upon us my friends, but don't worry, the Linux Kernel with catch up and then expand far beyond the features that will be supported on proprietary platforms. 

Who thought we would see BIOS go to that big bottom desk drawer in the sky. (You know the drawer full of crap you keep because your afraid you might need that someday.....)

---

### Post by system_e4 on 2010-10-22
Well the same here. I have Dell Inspiron i5 2.27 with ATI Mobility Radeon HD 4300 Series 512 MB 

The same problem just upgraded to Ubuntu 10.10 

Hope they will solve this bug :)

---

### Post by Aitaix on 2010-10-24
same problem!

---

### Post by tomko222 on 2010-10-24
Same problem in Toshiba Satellite L650-11F (intel i5 cpu and ati radeon hd 5650 graphics) in Kubuntu 10.10.

---

### Post by fjasper on 2010-10-27
Same issue, on Dell Latitude E4310 i5 540M.
Ubuntu works, but the screen momentarily goes black for a split second and then back to normal, up to a dozen times per minute.

---

### Post by alex- on 2010-10-28
Same probmlem here:
CPU: Intel(R) Core(TM) i3 CPU M 350
Graphic chip: ATI

---

### Post by danieltcv on 2010-10-29
Same with Acer 5745g (core i5, nvidia gt330m).
Didn't have the problem with lucid (kernel 2.6.32), started after upgrading to maverick (2.6.35).
Not too big problem, but graphics are slighltly less performable.

---

### Post by phz_swe on 2010-10-29
> **danieltcv said:**
> Same with Acer 5745g (core i5, nvidia gt330m).
Didn't have the problem with lucid (kernel 2.6.32), started after upgrading to maverick (2.6.35).
Not too big problem, but graphics are slighltly less performable.

Same exact computer, same error message during startup since Maverick. Well, not really, since I always run graphics in "Discrete" mode (setting in the BIOS setup) using only the Nvidia circuit, so I don't think there is a performance hit (since the Intel circuit should be disabled (? don't exactly know what "Discrete" does on the hardware level) anyway. There would potentially be a performance boost if I could run the graphics in "Switchable" mode and thus use the i915 chip for co-processing, but as I said I don't really know what "Discrete" and "Switchable" _really_ does.

I used kernel 2.6.35-15 before the upgrade to Maverick, and I haven't seen the error message at startup before what I can recall. Maverick came with 2.6.35-22, so I guess something changed there.

Not a bigger problem than that it is annoying to see during startup.

---

### Post by mpanch13114@gmail.com on 2010-11-03
I got the same problem. How to fix this problem?

---

### Post by tibbyyo on 2010-11-04
Now that we've established that a few people have it, does anyone out there have any suggestions as to how to fix it? I can tell that my graphics are definitely not being accelerated since I got that error (from upgrading to Ubuntu 10.10).

---

### Post by bogdan_e on 2010-11-09
> **fjasper said:**
> Same issue, on Dell Latitude E4310 i5 540M.
Ubuntu works, but the screen momentarily goes black for a split second and then back to normal, up to a dozen times per minute.

Any solution?
I also have screen flickers (after I upgraded from 10.04 to 10.10) and some log or error messages after the 'failed to get i915 ...'  (before the login screen to appear).

Thank you!

---

### Post by fjasper on 2010-11-10
I haven't found a solution, but I haven't searched for one.  I had to wipe the hard drive on my E4310, and start over, and since I have to have a couple of windows applications (one for school and one for working on my car), I didn't put Linux back on it for now.
 
That said, has anyone tried retrograding to an earlier kernel that worked?  I don't feel like I need the latest and greatest, and I like the idea of keeping my personal stuff in a different partition, and different OS than my work stuff, but the flickering made me think I might be torturing the video system.
 
If it helps to explain the problem to those much smarter than me, the flicker appears to be the same as the one that occurs when windows completes its startup ritual.  There's a momentary flicker that appears at the end of the startup sequence, after the desktop image has loaded when I start (but not when I resume) W7/32.
 
FWIW, when I was dual-booting Windows 7/32 with Ubuntu (10.04 or 10.10-I tried both), if I restarted from u10 into W7, I would occasionally get the "momentary black screen" issue in windows.  Sequence:  Cold boot.  Boot menu.  Select Ubuntu.  Run ubuntu for a while, with the screen flicker issue.  Restart.  Select Windows 7 (32 bit) at the boot menu.  Run W7(32).  Flicker issue present while in W7(32) OS.  Perform shutdown.  Cold boot.  Select W7.  Run W7 with no flickering issue.
 
I don't know if the 32-bit thing makes a difference or not, but I mention it b/c it seems like the less-common version of W7.  I don't know why Dell put the 32-bit version on this machine, it has a Core i5 540 M processor.
 
I have to admit that I'm pretty much a passive Ubuntu user, since fixing it is way above my competence level, so I wouldn't even know where to start, except maybe trying an older version of Ubuntu.

---

### Post by onetanzania on 2010-11-12
same with me i have Dell latitude E5510

---

### Post by Darkhorse85 on 2010-11-13
i have the same problem! It just gives the error message on boot, but my graphics is not disabled. Acer 4741 core i3 laptop with onboard graphics. Its slows down my boot time...:eek:

---

### Post by RedBluespot on 2010-11-16
I've got the same problem. I got an **Asus U35JC**.
This is what it says for a split second when I log in.

[I][   14.510607] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   14.792778] nouveau 0000:01:00.0: Invalid ROM contents
[   14.859203] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid
[   14.884188] [drm] nouveau 0000:01:00.0: 0xDD22: Failed parsing init table opcode: INIT_ZM_I2C_BYTE -6[/I]

Then it resumes as normal.
It's annoying and is slowing down my boot time.

---

### Post by dentharg on 2010-11-17
Same on Dell latitude e6410 (intel only). Screen flickers and then boot normally.

---

### Post by x201r on 2010-11-18
Same problem here on EliteBook 2540p i5-540M

Curiously, I also have a Lenovo x201 with i5-560M and I don't have the same problem.. weird.

---

### Post by TheRue on 2010-11-19
Hm I have the same problem and I have asked multi time's over about it since it is not showing my splash screen cause of this,so I take it there is no fix for this or the wmid problem as well,so I guess we all sit back and wait till they iron it out.

---

### Post by ricomoss on 2010-11-19
Add me to the list of affected individuals.

Dell Latitude E5410 with 160GB HDD, 2GB RAM and Intel Core i5-520M(2.4GHz).

I had serious lag issues during install and haven't yet been able to boot.  I'm looking for an older version of Kubuntu until they can fix the problem.

---

### Post by depeha on 2010-11-19
I´ve got same problem on my HP Pavilion DV6-3040ec. It has i5 M450 CPU - Intel integrated graphics + ATI Radeon HD 5650. 

I´m using intel graphics, because ati drivers don´t support switcheroo and kwin effects. But with intel graphics comes another problem. Few minutes after boot whole system freezes.

---

### Post by artemhp on 2010-11-21
Have the same problem Asus K42F

---

### Post by nonabhai on 2010-11-21
Same problem with Dell inspiron i5

---

### Post by clifhanger_uk on 2010-11-22
I also experience this error msg when starting Ubuntu 10.10
How can I check if my graphics are accelerated? (whatever that means?):-?

Latitude E6410

---

### Post by birdmanuk on 2010-11-24
Same problem for me on my Vaio VPCEB1Z0E with a ati radeon 5000 graphics.

I have upgraded from 10.04, which had the ATI Catalyst driver installed (preferred this driver to the standard Ubuntu one as all my brightness keys and battery lasted longer)

On the upgraded 10.10 system, I have uninstalled all of the fglrx packages and I guess I still have the catalyst driver installed, not sure how to remove it.??

---

### Post by phaed on 2010-11-24
Ditto on Toshiba Satellite L550.

**$ lspci | grep VGA**
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

**$ dmesg | grep intel**
[    0.704086] intel_idle: MWAIT substates: 0x1120
[    0.704088] intel_idle: v0.4 model 0x25
[    0.704089] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.716071] ACPI: acpi_idle yielding to intel_idle
[   11.223186] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   11.223215] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   11.223401] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   11.241027] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
[   11.251001] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[   11.252519] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   11.333164] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   12.312057] fb0: inteldrmfb frame buffer device

---

### Post by wechselbalg on 2010-11-26
Same for me: ThinkPad X201s with Intel i540M HD

---

### Post by clockworkpc on 2010-11-28
Same here, Dell Inspiron 1564.
Although my installation is currently Linux Mint 10 -- I'm switching to Maverick soon -- but I suspect that it'll be the same there too.
Have the ATI drivers installed.

---

### Post by birdmanuk on 2010-12-04
Any fix?

---

### Post by n5xmt on 2010-12-06
Same here...
HP Elitebook 8440P

lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GT218 [NVS 3100M] (rev a2)

dmesg | grep intel
[    1.094841] intel_idle: MWAIT substates: 0x1120
[    1.094842] intel_idle: v0.4 model 0x25
[    1.094843] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.095813] ACPI: acpi_idle yielding to intel_idle
[   10.462063] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   10.462091] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   10.462182] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   10.462329] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
[   12.619228] hda_intel: Disable MSI for Nvidia chipset
[   37.224968] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

---

### Post by jjozeh on 2010-12-06
Same problem


~$  lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]


~$ dmesg | grep intel
[    1.443681] intel_idle: MWAIT substates: 0x1120
[    1.443683] intel_idle: v0.4 model 0x25
[    1.443684] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.460002] ACPI: acpi_idle yielding to intel_idle
[   11.558237] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   11.558261] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   11.558415] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   49.174167] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

---

### Post by fjasper on 2010-12-07
[FONT=System]So, does anyone tracking this forum know how to turn this into an official bug report? It seems like a fairly repeatable problem, like someone who knows about these things might be able to code a fix for it.[/FONT]
[FONT=System][/FONT] 
[FONT=System]Maybe it would be useful to put together a poll to try to spot trends. Which processor, video card, release (10.04, 10.10, or both), etc. I could try to make some stuff up, but it's likely I'd miss the point and muddy the issue. Anyone want to give it a shot?[/FONT]

---

### Post by hawthornso23 on 2010-12-07
There is already an official bug report on this issue. The problem is the lack of a driver for intel integrated graphics. We can't fix it as Intel hasn't provided a driver, or information that would allow people to write their own driver. 

Basically new Intel CPU chips come with a GPU (graphics processor) actually on the chip. This is the way the world is going. It will eventually allow the CPU to use the power of the GPU (and vice versa) to speed up certain calculations. Linux doesn't support this yet, but it will come. 

If you have a graphics card then this takes over from the onchip graphics after bootup and your graphics quality will not be effected (except perhaps during bootup).  If you don't have any other kind of graphics however, then you have a problem.

Anyway that is the situation. There is already a bug report filed, but really nobody except Intel can do anything about it at this point. Try complaining to them about the lack of a linux driver.

By the way - I have this issue in my Dell Latitude E6510.

---

### Post by nadoudidou on 2010-12-07
so while it gets an official fix, is there any workaround to this ?

---

### Post by Paivalhao on 2010-12-08
> **jjozeh said:**
> Same problem


~$  lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]


~$ dmesg | grep intel
[    1.443681] intel_idle: MWAIT substates: 0x1120
[    1.443683] intel_idle: v0.4 model 0x25
[    1.443684] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.460002] ACPI: acpi_idle yielding to intel_idle
[   11.558237] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   11.558261] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   11.558415] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   49.174167] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

Same here. Toshiba L635-10U

Can it be done something to pass this while w8 for official solution?

---

### Post by tomtom12 on 2010-12-09
Same problem with Samsung Q330 (core i3 / Nvidia 350M )

10.10 installed quick; then enabled suggested hardware driver for Nvidia ... and never got to start again, without removing /etc/X11/xorg.conf

Can not disable integrated Intel graphics as BIOS does not show graphic card selection option... What to ?? :(

---

### Post by Opperkip on 2010-12-09
I don't think it helps when we all say we have the same problem.
I think the only people who sould post after me should provide a possible solution or workaround.
so as the last person. My laptop HP touchsmart tm-2000ed has the same problem.

---

### Post by fjasper on 2010-12-09
[http://intellinuxgraphics.org/2010Q3.html](http://intellinuxgraphics.org/2010Q3.html)
Maybe helpful?

---

### Post by feuxfollets on 2010-12-09
So if the intel integrated graphics doesn't work then what graphics is my computer using exactly?

I have an envy 14 with i5, intel HD, and radeon 5650. The radeon card does not have a driver that works well (fglrx doesn't support dual gpus and the open source one doesn't work well, in fact performs worse than the intel). So I turn off the radeon with a startup script.

However according to the post earlier the intel doesn't have a driver, so then what the heck is my computer running from?

---

### Post by umbeebmu on 2010-12-09
Hi,
[FONT="Courier New"]02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
Linux 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux[/FONT]

I get the same message as anybody else, but with the additional side effect that Ubuntu freezes very often.

This is very likely in the first minutes (2 to 10) of usage, but if I manage to survive after this time usually does not happens anymore.
It could freeze while moving a window, scrolling something, opening a menu, or even while doing absolutely nothing.

This is a blocking problem for me (I'm using W7 most of the time now :( )
**Anyone knows a workaround for the freezing issue? **
Or any suggestion on **how can I debug this further?**
I intentionally bought this new laptop with an extra vido card to avoid troubles with the internal intel controller... but it didn't help.
Last point: in my BIOS I cannot disable/configure anything about the Radeon

---

### Post by PhaMenThaR on 2010-12-12
need help :confused:
[IMG]http://i56.tinypic.com/9av1xx.jpg[/IMG]
my netbook acer 4740G nVidia GEFORCE 310M CUDA 512Mb
some body give me solution ;)

---

### Post by umbeebmu on 2010-12-13
last night happened again, and today I looked carefully at every single logfile (gnome-system-log) but I could not find a single hint of what happened at the time of the freezing.
I'll keep checking in case I see any recurrent pattern....

---

### Post by umbeebmu on 2010-12-13
Sorry to say this, but after 5 happy years of Ubuntu I'm going to use windows from now on, because of this problem!

---

### Post by fjasper on 2010-12-14
I don't usually go to conspiracy theories, but does it seem suspicious that when the GPU came onboard, (making it harder to change your graphics system) it got harder for anyone except windows (and mac, I guess) to use it? I'm using W7 exclusively on my new laptop because of this, but instead of switching to windows forever, I'm planning to make sure every computer I buy in the future includes support for Linux. If it's not Linux compatible, as evidenced by good results from regular users, I won't consider it.
 
I bought this laptop (Dell E4310) planning to put Ubuntu on it, but it doesn't work. Yet. So I'll use the backup OS (W7) until it gets sorted out, and be more careful in the future to avoid any computer that doesn't work with Linux right out of the box.
 
If it becomes a factor for buyers like us, any chip mfr that doesn't support Linux will lose some sales, and will have to make a business decision as to whether it's prudent to ignore a market segment in order to reduce costs.
 
All right, I'll stop ranting about it. Hopefully it gets taken care of soon. Still, it seems a little suspicious.

---

### Post by flusheDData on 2010-12-17
The same problem on my Dell 1558 (Studio 15)

---

### Post by patrickwilken on 2010-12-17
Same problem on my Samsung RF-510.

---

### Post by tomtom12 on 2010-12-18
With Ubuntu 10.10: Same on my Samsung Q330 (Nvidia Optimus). But Bios does not have option to disable one or the other, so both kept running -> laptop became lapHOT

Changed it for an HP DM4 1160  because of that (too bad Nvidia - you are loosing customers). Everything runs out of the box - great. Even Compiz advanced effects...but... during start up I get the same error - briefly... Please note:  this DM4 1160 does *not* have any discrete graphics , just the intel core i5 integrated

---

### Post by obi22 on 2010-12-27
Hi there all you guys that cannot run your laptops!

Did you try to look at bios for graphic settings something like: Discreet/Switchable ?

For now switchable doesn't work for me, but discreet does, I'm on Acer 5745G, i5, nVidia 330m.

---

### Post by n5xmt on 2010-12-27
> **obi22 said:**
> Hi there all you guys that cannot run your laptops!

Did you try to look at bios for graphic settings something like: Discreet/Switchable ?

For now switchable doesn't work for me, but discreet does, I'm on Acer 5745G, i5, nVidia 330m.

Mine runs, but I always get this message on start up.
the other issue I have is if I close the lid, upon opening, I have to do Ctrl-Alt-F1, then Ctrl-Alt-F7 to get the display back... wasn't an issue under 10.04...

---

### Post by daragon on 2010-12-27
I had the issue too,but i found a method to forbiden it

> sudo gedit /etc/modprobe.d/blacklist.confadd 
> blacklist intel_ipsthat will work

---

### Post by andys42 on 2010-12-29
I had a similar problem with my Thinkpad Edge 11. It has an Intel i3 and only has the integrated graphics on the CPU.

Using the 2.6.36-24 kernel image the output from the intel_ips module in dmesg was:
```

[    6.864987] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 11, expected 18)
[    6.865045] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    6.865316] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[    6.916727] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535

```I found what appears to be a fix to the overall problem but you still get the error on bootup. Run the following:

Removing the intel_ips module and inserting it again with:
```

modprobe -r intel_ips
modprobe intel_ips

```gave this output from intel_ips in dmesg:
```

[   82.337585] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 11, expected 18)
[   82.340231] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535

```If you care, this is how I found this. It'll involve looking through chunks of C in the kernel source:
The problem was with the intel_ips kernel module, so I got the kernel source, found the code for the module ("find ./ -name intel_ips*" in the root of the kernel source found the file) which was src/linux-2.6.36.2/drivers/platform/x86/intel_ips.c

In there the error from the module could only come from this code:
```

        if (!ips_get_i915_syms(ips)) {
                dev_err(&dev->dev, "failed to get i915 symbols, graphics turbo disabled\n");

```And the function it runs starts with

```

static bool ips_get_i915_syms(struct ips_driver *ips)
{
        ips->read_mch_val = symbol_get(i915_read_mch_val);

```And the symbols it gets are in the i915 driver. Unfortunately until that module is loaded into the kernel the IPS driver can't get the i915 symbols and so throws the error. There isn't a dependency set within the intel_ips module for the i915 module so it always gives off an error. I tried changing options in grub to get the i915 module loaded first but the intel_ips module always seems to be loaded first. The only way I found was to wait until linux had fully booted and then remove the module and reload it. Incidentally, this also fixed a problem where the intel_ips module was giving out errors like this:

```

[   67.047376] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   72.039844] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded

```It looks as though not being able to figure out the details of the GPU meant the IPS module meant it couldn't figure out the thermal/power budgets and kept using too much power.

---

### Post by Danny830x on 2011-01-06
I also have this problem. Dell Inspiron n7010. I have received the error since install, but was always able to boot up until now.

Now the error message shows, then I get a scaled down purple Ubuntu screen followed by a terminal like screen which asks for login/pass. I can't use the sudo gedit screen as I get a WARNING: graphics disabled error.

Is there any fix to at least get me back up and running?

---

### Post by tomtom12 on 2011-01-08
@Andys42...interesting... Could this also be reason why my HP DM4 does not show remaining battery?  It always shows:

*Laptop battery (estimating....)*

---

### Post by dondamyani on 2011-01-11
> **daragon said:**
> I had the issue too,but i found a method to forbiden it

     Quote:
                                                 sudo gedit /etc/modprobe.d/blacklist.conf                                 
add 
     Quote:
                                                 blacklist intel_ips                                 
that will work

that worked for me too :D

---

### Post by tomtom12 on 2011-01-13
Well... it will hide the warning... but does it mean we do not have optimal graphics?

---

### Post by raif1 on 2011-01-13
What I did.

As the previous post, in /etc/modprobe.d/blacklist.conf, add the line "blacklist intel_ips"

and edit /etc/rc.local , just before line exit 0, add the line "modprobe intel_ips".

When I reboot, the message about turbo graphics disabled was gone, and when I do lsmod | grep intel_ips, the module intel_ips is loaded.

So, the question remains, does this mean the turbo graphics is enabled ?

---

### Post by greybot on 2011-01-14
I have a core i3 processor in my laptop and also get this message. According to the spec of the processor it doesn't support turbo mode, whereas the i5 and i7 do, which would warrant the warning that it isn't enabled. However some people on here are encountering the error with i5 processors, which means this still needs fixing.

---

### Post by ivt13 on 2011-01-16
Long time reader, first time poster.

I'm using a Lenovo X201 w/ Core i5, Ubuntu 10.10

Initially I was running 10.04 and did the upgrade. That gave me the problem described in this thread. I also could not have any "eye candy."

What I did was I reinstalled 10.10 completely (reformat etc) and now I have all the visual effects enabled. I still get that error message sometimes, but its not such a big problem anymore.

 I hope that helps.

---

### Post by greybot on 2011-01-21
Can anyone confirm if this bug is still present with first version of 2.6.38 kernel?

---

### Post by nils-79 on 2011-01-28
Hi,
 
there are a plenty of other problems related to this intel graphic card.
One of those is - for example - a bug in the linux kernel which makes
dual head impossible. I tried different versions of the linux kernel 2.6.37 (even
in the rc state) to get dual head working. 
 
It sounds strange but after installing the latest stable kernel 2.6.37 
booting into X is sometimes possible, sometimes not. In the worst case
I have to reboot my machine several times until the X server is displayed.
 
However, after installing the latest stable kernel the error message 
(failed to get ...) still exists. Anyway, the dual head problem is solved
and I'm now going to install the latest GIT kernel on my laptop.
 
As far as I know they implemented some changes in the 2.6.38 kernel
related to this graphic chipset. Due to a slow internet link,
dowloading the kernel sources will take a while :-) 
 
I'll post my results on here.  Let's pray that some of these bugs are fixed ... ... , 
it's so time consuming to troubleshoot these kind of problems. 

Nils

---

### Post by nils-79 on 2011-01-28
I compiled the new 2.6.38 rc2 kernel .... and .... problem does still exist.
It seems some drivers from intel are missing to enable graphic turbo.
 
However ... it seems the x-server is more stable while running the new kernel.
I booted several times and no problems regarding performance or stability 
could be detected.

---

### Post by JeanVW14 on 2011-01-31
+1 for the prob.. Had to reinstall to get 3d graphics enabled and it's working now, but still have the 'i915' and 'turbo failed' at boot, which is in oversized crappy plaintext (?!?)

Is this just a 'hurry up and wait' for the kernel to fix it?

---

### Post by ralzes on 2011-02-03
i was cheking this post and it seems to be post along time ago... is already a solution for this problem? i install kubuntu 10.10 and delete all trace of windows... tried to enter by doing the nomodeset but i can´t change the blacklist thing... i´m noob on al this thing, can anyone explain to me how can i do that without seen anithing more than the root? help please! (sorry i´m not an english natural speaker.. =S)

---

### Post by kongstad on 2011-02-03
@ralzes:

Open a terminal and type this:

[FONT="System"]sudo sh -c "echo blacklist intel_ips >>  /etc/modprobe.d/blacklist.conf"
[/FONT]
You will be asked for your password, enter it, and you have fixed the blacklist file

The sudo command executes the following shell with root permissions.

This should remove the error on startup.

If you want more control then use this command:

[FONT="System"]gksudo gedit /etc/modprobe.d/blacklist.conf [/FONT]

This opens the file in the text editor with root permissions.

Then add 
[FONT="System"]blacklist intel_ips[/FONT]
tot he end of the file

---

### Post by wujastyk on 2011-02-04
But does blacklisting intel_ips allow Turbo mode.  I think not.  Nor does the i915 graphics driver seem to work.  The blacklisting of intel_ips avoids the error message, but doesn't solve the problem.

Or am I wrong?

Dominik

---

### Post by ralzes on 2011-02-04
thanks ill check it now... i hope can boot after that

---

### Post by ralzes on 2011-02-04
ok i should post all my problem... i installed with no apci option kubuntu 10.10, after i had win 7, kubuntu installed succesfully and then restart, but when it was starting show this problem... failed to get i915... so i read that i can enter kubuntu by doing in the start some changes linux /boot/vmlinuz... ro quiet splash to linux /boot/vmlinuz... ro nomodeset quiet splash... kubuntu load but no graphical enviroment... so there i am, i see everything like a console, i logged in and i tried sudo sh -c "echo blacklist intel_ips >> /etc/modeprobe.h/blacklist.conf" and i got this error sh: cannot create /etc/modeprobe/blacklis.conf : directory nonexistent i tried to rewrite it i thought i wrote it wrong, so i wrote it whitout space before the sh... sh-c"... and i get this sh: illegal option h... i couldn't put it onto black list =(.... (sorry again for the bad engish)

---

### Post by danadn on 2011-02-05
Blacklisting it don't solve the problem, it hides it.

My laptop still gets high temperatures, with windows 7 that doesn't happens

---

### Post by wujastyk on 2011-02-08
I've just successfully compiled and booted kernle 2.6.38-rc4.  I was disappointed that the intel_ips / i915 symbols error message still appears at boot time.

HP Elitebook 8740w.  Still can't run compiz.  :-(

Dominik

---

### Post by vigyani on 2011-02-09
Hi

I have an Acer Aspire 4740 (Intel Core i3 & running Ubuntu 10.10 Linux 2.6.35-26-generic #46-Ubuntu SMP i686 GNU/Linux, suffer the same problem.

---

### Post by ralzes on 2011-02-09
i get bored of this problem... i installed fedora 14 with kde... and it is not what it can be... but it works...
thanks :)

---

### Post by 25an on 2011-02-17
I managed to get it work by applying the patch that can be found at
[http://lists.freedesktop.org/archives/intel-gfx/2010-December/009017.html](http://lists.freedesktop.org/archives/intel-gfx/2010-December/009017.html) and then following the steps in [http://blog.avirtualhome.com/2010/11/06/how-to-compile-a-ubuntu-10-10-maverick-kernel/](http://blog.avirtualhome.com/2010/11/06/how-to-compile-a-ubuntu-10-10-maverick-kernel/) before starting the build of the kernel apply the patch and then build the kernel install the deb files and thats it. I am running this on KUbuntu 10.10 on a DELL Latitude E5510 and the kernel that I patched was Ubuntu-2.6.35-25.44 from the ubuntu git repository. So in the manual above when running the command git tag -l | sort -V I checked out the tag Ubuntu-2.6.35-25.44. 

My dmesg after the fix:
$ dmesg | grep intel
[ 0.000000] Linux version 2.6.35-25-intelgt (root@LJPC) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #44 SMP Thu Feb 17 12:59:58 CET 2011 (Ubuntu 2.6.35-25.44-intelgt 2.6.35.10)
[ 0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-intelgt root=UUID=a56802c9-18ce-455f-8db7-014779c24a21 ro crashkernel=384M-2G:64M,2G-:128M
[ 0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-intelgt root=UUID=a56802c9-18ce-455f-8db7-014779c24a21 ro crashkernel=384M-2G:64M,2G-:128M
[ 0.902666] intel_idle: MWAIT substates: 0x1120
[ 0.902668] intel_idle: v0.4 model 0x25
[ 0.902668] intel_idle: lapic_timer_reliable_states 0xffffffff
[ 0.905086] ACPI: acpi_idle yielding to intel_idle
[ 11.259910] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[ 11.260910] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[ 11.365005] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[ 11.365042] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[ 11.365063] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 11.365225] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[ 11.424083] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
[ 13.019027] fb0: inteldrmfb frame buffer device
[ 18.324616] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
$ dmesg | grep ips
[ 11.259910] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[ 11.365042] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[ 11.365063] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 11.365225] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[ 11.424083] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
[ 18.324616] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo

I noticed that the start up time might be just a tiny bit longer.

---

### Post by Iljusin on 2011-02-18
Great, but a bit difficult for me ;) Has your Ubuntu better graphics performance?

---

### Post by UprightMan on 2011-02-19
Apologies for what is probably an obvious question (I'm still learning the Linux ropes at the moment), but how do I apply the patch that 25an has shown us?

That error message each boot-up is eating away at my sanity and I'd very much like to correct it haha.

---

### Post by de_Selby on 2011-02-20
Thanks for that 25an! I've compiled a new kernel and it's working perfectly.

I've uploaded a deb of the kernel for anyone else to download so they don't have to go through the effort of compiling. The link is below:

[http://www.4shared.com/file/HiJd6rdx/linux-image-2635-28-generic_26.html](http://www.4shared.com/file/HiJd6rdx/linux-image-2635-28-generic_26.html)

I haven't used 4shared before, hopefully they don't have a limit on the no of downloads.

---

### Post by klarkent on 2011-02-20
> **de_Selby said:**
> Thanks for that 25an! I've compiled a new kernel and it's working perfectly.

I've uploaded a deb of the kernel for anyone else to download so they don't have to go through the effort of compiling. The link is below:

[http://www.4shared.com/file/HiJd6rdx/linux-image-2635-28-generic_26.html](http://www.4shared.com/file/HiJd6rdx/linux-image-2635-28-generic_26.html)

I haven't used 4shared before, hopefully they don't have a limit on the no of downloads.

Same message on K52JB notebook :'( even after installing your .deb kernel

---

### Post by de_Selby on 2011-02-20
Yeah you'll still get the initial message, but the driver gets re-attached - that's what the patch does

if you do dmesg | grep "intel ips" with the kernel i've compiled you'll see something like this:


```
peter@deSelby:~$ dmesg | grep "intel ips"
[   17.456759] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   17.456787] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   17.456956] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   17.491721] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   22.678855] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
```

If you see the last line in your output you're good, it got re-enabled.

---

### Post by visonwei on 2011-02-22
> **de_Selby said:**
> Thanks for that 25an! I've compiled a new kernel and it's working perfectly.

I've uploaded a deb of the kernel for anyone else to download so they don't have to go through the effort of compiling. The link is below:

[http://www.4shared.com/file/HiJd6rdx/linux-image-2635-28-generic_26.html](http://www.4shared.com/file/HiJd6rdx/linux-image-2635-28-generic_26.html)

I haven't used 4shared before, hopefully they don't have a limit on the no of downloads.

Could you plz help to make a package for i386 if it's possible,I have tried to compile it by myself, it seemed generating some errors.

---

### Post by Jeanke on 2011-02-24
Thanks 25an and de_Selby!
New patched kernel as provided by de_Selby works fine for me!

---

### Post by de_Selby on 2011-02-24
> **visonwei said:**
> Could you plz help to make a package for i386 if it's possible,I have tried to compile it by myself, it seemed generating some errors.

well first you have to make sure you have all the development packages installed, so do this:

```
sudo apt-get install fakeroot build-essential crash kexec-tools makedumpfile kernel-wedge
sudo apt-get build-dep linux
sudo apt-get install git-core libncurses5 libncurses5-dev libelf-dev asciidoc binutils-dev
```

Then you want to download the kernel source, so make a temporary directory open a terminal there and do the following:
```
sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)
```
then you'll have to apply the patch given in 25an's link, so paste the following into a file called intel_patch
```

---
 drivers/gpu/drm/i915/i915_dma.c  |   23 +++++++++++++++++++++++
 drivers/platform/x86/intel_ips.c |   36 +++++++++++++++++++++++++++++++++---
 drivers/platform/x86/intel_ips.h |   21 +++++++++++++++++++++
 3 files changed, 77 insertions(+), 3 deletions(-)
 create mode 100644 drivers/platform/x86/intel_ips.h

diff --git a/drivers/gpu/drm/i915/i915_dma.c b/drivers/gpu/drm/i915/i915_dma.c
index 18746e6..8cb7f93 100644
--- a/drivers/gpu/drm/i915/i915_dma.c
+++ b/drivers/gpu/drm/i915/i915_dma.c
@@ -34,6 +34,7 @@
 #include "i915_drm.h"
 #include "i915_drv.h"
 #include "i915_trace.h"
+#include "../../../platform/x86/intel_ips.h"
 #include <linux/pci.h>
 #include <linux/vgaarb.h>
 #include <linux/acpi.h>
@@ -1834,6 +1835,26 @@ out_unlock:
 EXPORT_SYMBOL_GPL(i915_gpu_turbo_disable);
 
 /**
+ * Tells the intel_ips driver that the i915 driver is now loaded, if
+ * IPS got loaded first.
+ *
+ * This awkward dance is so that neither module has to depend on the
+ * other in order for IPS to do the appropriate communication of
+ * GPU turbo limits to i915.
+ */
+static void
+ips_ping_for_i915_load(void)
+{
+	void (*link)(void);
+
+	link = symbol_get(ips_link_to_i915_driver);
+	if (link) {
+		link();
+		symbol_put(ips_link_to_i915_driver);
+	}
+}
+
+/**
  * i915_driver_load - setup chip and create an initial config
  * @dev: DRM device
  * @flags: startup flags
@@ -2019,6 +2040,8 @@ int i915_driver_load(struct drm_device *dev, unsigned long flags)
 	dev_priv->mchdev_lock = &mchdev_lock;
 	spin_unlock(&mchdev_lock);
 
+	ips_ping_for_i915_load();
+
 	return 0;
 
 out_gem_unload:
diff --git a/drivers/platform/x86/intel_ips.c b/drivers/platform/x86/intel_ips.c
index aa5f9b6..a8d21ee 100644
--- a/drivers/platform/x86/intel_ips.c
+++ b/drivers/platform/x86/intel_ips.c
@@ -75,6 +75,7 @@
 #include <drm/i915_drm.h>
 #include <asm/msr.h>
 #include <asm/processor.h>
+#include "intel_ips.h"
 
 #define PCI_DEVICE_ID_INTEL_THERMAL_SENSOR 0x3b32
 
@@ -245,6 +246,7 @@
 #define thm_writel(off, val) writel((val), ips->regmap + (off))
 
 static const int IPS_ADJUST_PERIOD = 5000; /* ms */
+static bool late_i915_load = false;
 
 /* For initial average collection */
 static const int IPS_SAMPLE_PERIOD = 200; /* ms */
@@ -339,6 +341,9 @@ struct ips_driver {
 	u64 orig_turbo_ratios;
 };
 
+static bool
+ips_gpu_turbo_enabled(struct ips_driver *ips);
+
 /**
  * ips_cpu_busy - is CPU busy?
  * @ips: IPS driver struct
@@ -517,7 +522,7 @@ static void ips_disable_cpu_turbo(struct ips_driver *ips)
  */
 static bool ips_gpu_busy(struct ips_driver *ips)
 {
-	if (!ips->gpu_turbo_enabled)
+	if (!ips_gpu_turbo_enabled(ips))
 		return false;
 
 	return ips->gpu_busy();
@@ -532,7 +537,7 @@ static bool ips_gpu_busy(struct ips_driver *ips)
  */
 static void ips_gpu_raise(struct ips_driver *ips)
 {
-	if (!ips->gpu_turbo_enabled)
+	if (!ips_gpu_turbo_enabled(ips))
 		return;
 
 	if (!ips->gpu_raise())
@@ -549,7 +554,7 @@ static void ips_gpu_raise(struct ips_driver *ips)
  */
 static void ips_gpu_lower(struct ips_driver *ips)
 {
-	if (!ips->gpu_turbo_enabled)
+	if (!ips_gpu_turbo_enabled(ips))
 		return;
 
 	if (!ips->gpu_lower())
@@ -1454,6 +1459,31 @@ out_err:
 	return false;
 }
 
+static bool
+ips_gpu_turbo_enabled(struct ips_driver *ips)
+{
+	if (!ips->gpu_busy && late_i915_load) {
+		if (ips_get_i915_syms(ips)) {
+			dev_info(&ips->dev->dev,
+				 "i915 driver attached, reenabling gpu turbo\n");
+			ips->gpu_turbo_enabled = !(thm_readl(THM_HTS) & HTS_GTD_DIS);
+		}
+	}
+
+	return ips->gpu_turbo_enabled;
+}
+
+void
+ips_link_to_i915_driver()
+{
+	/* We can't cleanly get at the various ips_driver structs from
+	 * this caller (the i915 driver), so just set a flag saying
+	 * that it's time to try getting the symbols again.
+	 */
+	late_i915_load = true;
+}
+EXPORT_SYMBOL_GPL(ips_link_to_i915_driver);
+
 static DEFINE_PCI_DEVICE_TABLE(ips_id_table) = {
 	{ PCI_DEVICE(PCI_VENDOR_ID_INTEL,
 		     PCI_DEVICE_ID_INTEL_THERMAL_SENSOR), },
diff --git a/drivers/platform/x86/intel_ips.h b/drivers/platform/x86/intel_ips.h
new file mode 100644
index 0000000..73299be
--- /dev/null
+++ b/drivers/platform/x86/intel_ips.h
@@ -0,0 +1,21 @@
+/*
+ * Copyright (c) 2010 Intel Corporation
+ *
+ * This program is free software; you can redistribute it and/or modify it
+ * under the terms and conditions of the GNU General Public License,
+ * version 2, as published by the Free Software Foundation.
+ *
+ * This program is distributed in the hope it will be useful, but WITHOUT
+ * ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
+ * FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for
+ * more details.
+ *
+ * You should have received a copy of the GNU General Public License along with
+ * this program; if not, write to the Free Software Foundation, Inc.,
+ * 51 Franklin St - Fifth Floor, Boston, MA 02110-1301 USA.
+ *
+ * The full GNU General Public License is included in this distribution in
+ * the file called "COPYING".
+ */
+
+void ips_link_to_i915_driver(void);
--

```
save that file in the kernel source directory, and in a terminal there do:
```
cat intel_patch | patch -p1 --dry-run
```

This tests to see whether the patch can be applied ok, look at the output from it, it should return a status for each of the 'Hunks' of the patch - you want these to all say Ok (no failures) **. If that runs ok, then you can actually apply the patch - ie execute the command above without the --dry-run bit.

Then you can go on to build the kernel, just run

```
fakeroot debian/rules clean
AUTOBUILD=1 fakeroot debian/rules binary-debs
```

That'll take a while, but it should compete successfully and you'll be left with a deb to install.



** if there are some failures with the patching you can open the patch file and figure out which ones failed and just edit the file yourself. the format is pretty self explanatory, and the only two files being patched are "drivers/platform/x86/intel_ips.c" and "drivers/platform/x86/intel_ips.h"

---

### Post by x_lk on 2011-02-25
[SIZE=4]**This method is obsolete. See [post 94]("http://ubuntuforums.org/showpost.php?p=10502147&postcount=94") for a better (and simpler) solution.**
[/SIZE] 
I came here initially for the solution. Since there wasn't an easy one, I ended up trying to solve it myself... anyway, guess I was lucky, I found the fix :) It works for my laptop (ACER-1830T). Here's how I got rid of this annoying message (BTW, it did not seem to create any harm for me, other than showing this ugly error during boot)

You need to do this as root,

```

sudo -s
echo "i915" >> /etc/initramfs-tools/modules
update-initramfs -k all -u
reboot

```

---

### Post by de_Selby on 2011-02-25
> **x_lk said:**
> I came here initially for the solution. Since there wasn't an easy one, I ended up trying to solve it myself... anyway, guess I was lucky, I found the fix :) It works for my laptop (ACER-1830T). Here's how I got rid of this annoying message (BTW, it did not seem to create any harm for me, other than showing this ugly error during boot)

You need to do this as root,

```

sudo -s
echo "i915" >> /etc/initramfs-tools/modules
update-initramfs -k all -u
reboot

```

That doesn't solve anything, it just stops the message appearing

---

### Post by x_lk on 2011-02-25
> **de_Selby said:**
> That doesn't solve anything, it just stops the message appearing
Let me explain how it worked. I think many of us already agreed that the root cause of the issue is i915 driver was not loaded when intel_ips driver needs it. In other word, module i915 must be inserted into kernel before intel_ips module. The kernel patch solution modifies driver code, so that initialization order does not matter any more. However, for the rest of us not wanting to rebuild kernel, forcing i915 to be loaded before intel_ips is a more elegant solution, IMO. Using following command line I found that intel_ips module is not included in initramfs,
```

lsinitramfs /boot/initrd.img-2.6.35-25-generic | grep intel_ips
```
So making i915 module into initramfs will most likely fix the issue, because this way, it can be loaded at a much earlier stage. After making change to my initramfs, kernel log shows that kernel does load i915 module much earlier than intel_ips now. And, as expected, intel_ips does not complain about not being able to find i915 any more.
```

dmesg | grep i915
[    1.785142] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.785150] i915 0000:00:02.0: setting latency timer to 64 tr
[    1.845774] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    2.850377] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
dmesg | grep 'intel ips'
[    8.846831] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 11, expected 18)
[    8.846880] intel ips 0000:00:1f.6: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    8.910249] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
```

---

### Post by wujastyk on 2011-02-26
> **x_lk said:**
> I came here initially for the solution. Since there wasn't an easy one, I ended up trying to solve it myself... anyway, guess I was lucky, I found the fix :) It works for my laptop (ACER-1830T). Here's how I got rid of this annoying message (BTW, it did not seem to create any harm for me, other than showing this ugly error during boot)

You need to do this as root,

```

sudo -s
echo "i915" >> /etc/initramfs-tools/modules
update-initramfs -k all -u
reboot

```


Seemed like a good idea, but when I rebooted I got an error message - first thing - saying that the system couldn't find i915.ko.  I've checked, and it *is* in my system (/lib/modules/2.6.35-27-generic-pae/kernel/drivers/gpu/drm/i915/i915.ko).

```

$ dmesg | grep i915
[    3.919543] [drm:i915_init] *ERROR* drm/i915 can't work without intel_agp module!
[   20.816634] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
$ dmesg | grep intel_ips
<i.e., blank>

```
Have drawn a blank at this point.
Dominik

---

### Post by renep1977 on 2011-02-26
I am very new at linux & Ubuntu.
I have installed the Ubuntu 10.10 x64. 
After installing the[SIZE=1] linux-image-2.6.35-28-generic_2.6.35-28.48_amd64, Gnome fails to start, only in revovery mode i can enter.
Any ideas???

[/SIZE]

---

### Post by de_Selby on 2011-02-26
> **x_lk said:**
> Let me explain how it worked. I think many of us already agreed that the root cause of the issue is i915 driver was not loaded when intel_ips driver needs it. In other word, module i915 must be inserted into kernel before intel_ips module. The kernel patch solution modifies driver code, so that initialization order does not matter any more. However, for the rest of us not wanting to rebuild kernel, forcing i915 to be loaded before intel_ips is a more elegant solution, IMO. Using following command line I found that intel_ips module is not included in initramfs,
```

lsinitramfs /boot/initrd.img-2.6.35-25-generic | grep intel_ips
```
So making i915 module into initramfs will most likely fix the issue, because this way, it can be loaded at a much earlier stage. After making change to my initramfs, kernel log shows that kernel does load i915 module much earlier than intel_ips now. And, as expected, intel_ips does not complain about not being able to find i915 any more.
```

dmesg | grep i915
[    1.785142] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.785150] i915 0000:00:02.0: setting latency timer to 64 tr
[    1.845774] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    2.850377] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
dmesg | grep 'intel ips'
[    8.846831] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 11, expected 18)
[    8.846880] intel ips 0000:00:1f.6: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    8.910249] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
```

ah ok, sorry, i thought at first you were just blacklisting, that is a much nicer solution!

well, i've built the kernel now anyway.

---

### Post by x_lk on 2011-02-27
> **wujastyk said:**
> Seemed like a good idea, but when I rebooted I got an error message - first thing - saying that the system couldn't find i915.ko.  I've checked, and it *is* in my system (/lib/modules/2.6.35-27-generic-pae/kernel/drivers/gpu/drm/i915/i915.ko).

```

$ dmesg | grep i915
[    3.919543] [drm:i915_init] *ERROR* drm/i915 can't work without intel_agp module!
[   20.816634] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
$ dmesg | grep intel_ips
<i.e., blank>

```Have drawn a blank at this point.
Dominik
You may try adding intel_agp into /etc/initramfs-tools/modules - it needs to appear before i915. Then update your initramfs and reboot. However, this is rather strange, because intel_agp module is included in the initramfs in my Ubuntu 10.10 system. Maybe X64 kernel and PAE kernel are quite different...I'm not sure.

---

### Post by UprightMan on 2011-02-27
> **x_lk said:**
> You may try adding intel_agp into /etc/initramfs-tools/modules - it needs to appear before i915. Then update your initramfs and reboot. However, this is rather strange, because intel_agp module is included in thne initramfs in my Ubuntu 10.10 system. Maybe X64 kernel and PAE kernel are quite different...I'm not sure.

I find myself getting exactly the same error as wujastyk; adding intel_agp before i915 doesn't seem to be fixing the problem as well.

As of yet, I haven't had any epiphanies...but I'm still fairly new to all this so I'm still relying heavily on you guys for help.

---

### Post by x_lk on 2011-02-27
> **UprightMan said:**
> I find myself getting exactly the same error as wujastyk; adding intel_agp before i915 doesn't seem to be fixing the problem as well.

As of yet, I haven't had any epiphanies...but I'm still fairly new to all this so I'm still relying heavily on you guys for help.My guess is that your laptop is one of those with dual-GPU support, and BIOS sets default GPU to be the non-Intel one, which caused intel_agp and i915 failed to load.
After spending some time with modprobe man pages, I believe the following fix should work for all systems, with single or dual GPU. But again, I don't have a dual-GPU laptop, so please feedback if it works on such a system or not.

If you've updated your initramfs with i915 module, undo those changes by removing i915 from /etc/initramfs-tools/modules, and rerun 'update-initramfs -k all -u'.

Run following command,

```

sudo echo "softdep intel_ips pre: i915" > /etc/modprobe.d/intel-ips-dep-i915.conf

```Then reboot.

The 'softdep' option tells modprobe that intel_ips module has a soft dependency on i915, meaning intel_ips can be loaded without i915, but will only provide limited functionality. With this option, modprobe will always try to load i915 before inserting intel_ips.

---

### Post by wujastyk on 2011-02-27
Sadly, no luck.  Tried your approach, but got this: 

[   21.441263] [drm:i915_init] *ERROR* drm/i915 can't work without intel_agp module!
[   21.472914] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled

as the first message after booting.

I'm on a HP Elitebook 8740w, running Ubuntu Linux 2.6.35-27-generic-pae

Best,
Dominik

---

### Post by x_lk on 2011-02-27
> **wujastyk said:**
> Sadly, no luck.  Tried your approach, but got this: 

[   21.441263] [drm:i915_init] *ERROR* drm/i915 can't work without intel_agp module!
[   21.472914] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled

as the first message after booting.

I'm on a HP Elitebook 8740w, running Ubuntu Linux 2.6.35-27-generic-pae

Best,
DominikDoes your laptop come with any intel integrated graphics chip? If not, I guess you don't need the fix at all.

---

### Post by Osanya on 2011-02-27
> **de_Selby said:**
> Thanks for that 25an! I've compiled a new kernel and it's working perfectly.

I've uploaded a deb of the kernel for anyone else to download so they don't have to go through the effort of compiling. The link is below:

[http://www.4shared.com/file/HiJd6rdx/linux-image-2635-28-generic_26.html](http://www.4shared.com/file/HiJd6rdx/linux-image-2635-28-generic_26.html)

I haven't used 4shared before, hopefully they don't have a limit on the no of downloads.

I don't have much to add.  I just thought I'd mention that I'm suffering the same problem on a Dell inspiron 15r, and the Kernel uploaded above doesn't fix any problems for me.

---

### Post by amirstep on 2011-02-28
Same problem on Dell Latitude E6510 with NVIDIA NVS 3100M card running ubuntu 10.10.  Computer gets quite warm with graphics-intensive programs.  I've been following this thread for the last week or so.  I tried the initrampfs approach but no dice.  I downloaded patched/compiled kernel by de_Selby and it crashed and I couldn't reinstall the generic kernel.  Re-installed ubuntu 10.10 from CD.  Noobie so no suggestions.

---

### Post by vigyani on 2011-02-28
> **x_lk said:**
> My guess is that your laptop is one of those with dual-GPU support, and BIOS sets default GPU to be the non-Intel one, which caused intel_agp and i915 failed to load.
After spending some time with modprobe man pages, I believe the following fix should work for all systems, with single or dual GPU. But again, I don't have a dual-GPU laptop, so please feedback if it works on such a system or not.

If you've updated your initramfs with i915 module, undo those changes by removing i915 from /etc/initramfs-tools/modules, and rerun 'update-initramfs -k all -u'.

Run following command,

```

sudo echo "softdep intel_ips pre: i915" > /etc/modprobe.d/intel-ips-dep-i915.conf

```Then reboot.

The 'softdep' option tells modprobe that intel_ips module has a soft dependency on i915, meaning intel_ips can be loaded without i915, but will only provide limited functionality. With this option, modprobe will always try to load i915 before inserting intel_ips.

Hi

I have an Acer Aspire 4740 and running Ubuntu 10.10, I had the same problem and used the solution suggested in the post quoted above.

It no longer suffers from the problem.

Anyway I have update Kernel to Linux 2.6.37-020637-generic #201101050908 SMP, to take care of another problem related to repeated messages "intel ips 0000:00:1f.6: MCP power or thermal limit exceeded" from 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

thanks a lot.
regards

---

### Post by candrewswpi on 2011-03-01
Please note that this issue can be found in Launchpad at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/724569](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/724569)

---

### Post by UprightMan on 2011-03-02
> **x_lk said:**
> My guess is that your laptop is one of those with dual-GPU support, and BIOS sets default GPU to be the non-Intel one, which caused intel_agp and i915 failed to load.
After spending some time with modprobe man pages, I believe the following fix should work for all systems, with single or dual GPU. But again, I don't have a dual-GPU laptop, so please feedback if it works on such a system or not.

If you've updated your initramfs with i915 module, undo those changes by removing i915 from /etc/initramfs-tools/modules, and rerun 'update-initramfs -k all -u'.

Run following command,

```

sudo echo "softdep intel_ips pre: i915" > /etc/modprobe.d/intel-ips-dep-i915.conf

```Then reboot.

The 'softdep' option tells modprobe that intel_ips module has a soft dependency on i915, meaning intel_ips can be loaded without i915, but will only provide limited functionality. With this option, modprobe will always try to load i915 before inserting intel_ips.

Hmm, this file doesn't even exist on my system...

And also, after getting the 2.6.35-27-generic-pae kernel, it would seem that system isn't able to detect any graphics card at all...

---

### Post by amirstep on 2011-03-02
> **UprightMan said:**
> Hmm, this file doesn't even exist on my system...

And also, after getting the 2.6.35-27-generic-pae kernel, it would seem that system isn't able to detect any graphics card at all...

Ditto.  File doesn't exist on my system either. Dell Latitude E6510 with NVIDIA 3100 NVS, ubuntu 10.10.

---

### Post by x_lk on 2011-03-03
> **UprightMan said:**
> Hmm, this file doesn't even exist on my system...

And also, after getting the 2.6.35-27-generic-pae kernel, it would seem that system isn't able to detect any graphics card at all...Yes, the file does not exist on normal ubuntu. The command I gave is supposed to create the file. Sorry, can't help with PAE kernels, I don't use them.

---

### Post by UprightMan on 2011-03-03
That's alright then, I'll just stick with the .25 one, which seems to be the most stable for me, not including the graphics bug.

---

### Post by benju on 2011-03-05
Ditto on the issue
laptop hp dm4-1165dx ( i5, integrated crappics card :x ) please somebody tell me how to fix this issue ( my particular problem I get a green hue in the monitor throught the HDMI output, VGA works well )

---

### Post by macflav on 2011-03-13
> **x_lk said:**
> Yes, the file does not exist on normal ubuntu. The command I gave is supposed to create the file. Sorry, can't help with PAE kernels, I don't use them.

Ok, the file doesn't exist on my system either, and apparently I'm not able to create it. When I run the command line ([FONT=Courier New]sudo echo "softdep intel_ips pre: i915" > /etc/modprobe.d/intel-ips-dep-i915.conf[/FONT]) I get this:

[FONT=Courier New]bash: /etc/modprobe.d/intel-ips-dep-i915.conf: Permission denied[/FONT]

I'm not even prompted for the password, which is very weird!

---

### Post by ht1979 on 2011-03-19
I failed also to create the file with the orig command. I made it work so that I created the (empty) file with vi and then applied the command again.
After restart I got an additional error: ERROR* drm/i915 can't work without intel_agp module!

I have a Lenovo W510 with nVIDIA Quadro FX 880M running on 64bit 10.10[FONT=Verdana][/FONT]

---

### Post by macflav on 2011-03-20
Right, I managed to create the file somewhere else then move it there  with "sudo mv (...)". Now I get the same additional error  ([drm:i915_init] *ERROR* drm/i915 can't work without intel_agp module!)

LG R590 (core i5) with nVIDIA GeForce GT 335M, 64bit 10.10

---

### Post by Flaqs on 2011-03-20
Hello Guys!!!

Unfortunately I have the same problem with my Maverick. Lastly, I've installed it within Windows 7 using WUBI. Everything was prefect untill I've tried to boot it for the first time. Then this error occured. I have a HP Pavillion dv7-4020 with i5 450M CPU and AMD HD5650 graphic card. I've tried to install ATI drivers and hoped that it will help. Obviously it didn't. 
Before Ubuntu I tried with Kubuntu 10.04 and 10.10 and it was even worse. After the blue booting screen showed up, my screen turned black and stayed that way. It's better with Ubuntu but still not to good. The only way I managed to force system to run was as follows:
1. I run it in recovery mode
2. I chose something like "customize graphic settings" or "run in safe graphic mode" (I don't remember how it was named and also I'm using version with polish language)
3. Then I chose option to restart x.org server

After that I am able to use my Ubuntu normally, but cannot switch on any graphic special effects.

I hope it will be fixed in Natty.

Best regards,
Flaqs

---

### Post by mahaganapati on 2011-03-23
I have the same problem in Kubuntu Maveric. I can boot Kde, though. I have tried running the softdep fix mentioned above, but it doesn't seem to do anything apart from removing the error message. Framerate is the same as without the fix. Is the fix even meant to actually activate the turbo or just to give the unfortunate, who booted at a text prompt, the opportunity to boot into the Gui?

---

### Post by Magnificent 7 on 2011-03-26
Shiny New Tecra M11-130 with i5-520M with Intel QM57 Express Chipset with Intel Graphics Media Accelerator HD. Quite a good lappy under Ubuntu, but has some stability issues, i.e. the random freezing reported at the start of this and other very similar threads, requiring a power cycle.

As the graphics seemed to be working, it was almost as an afterthought that I followed up the i915 error message on bootup. That error and one other, that appeared after the latest (2011/3/26) batch of updates, seems to have been solved by

> **x_lk said:**
> Run following command,

```

sudo echo "softdep intel_ips pre: i915" > /etc/modprobe.d/intel-ips-dep-i915.conf

```Then reboot.

The 'softdep' option tells modprobe that intel_ips module has a soft dependency on i915, meaning intel_ips can be loaded without i915, but will only provide limited functionality. With this option, modprobe will always try to load i915 before inserting intel_ips.

from post 94 above.

I had been toying with the idea of starting a Tecra M11 thread asking for reports on the type of stability issues I'd been experiencing, but will hang fire for a few days to see whether this solves the random freezing issues.

Thanks, x_lk :)

______________________________________

By the way, being a relative n00b myself, I sympathise with the posters above who reported that 'intel-ips-dep-i915.conf' doesn't exist. It doesn't, until x_lk's command is executed (this is the '>' = "create, if doesn't exist", versus '>>' = "append text to end of file"). To create the file in /etc/modprobe.d you'll need privileges above sudo level. Just type

```
sudo su -
```

then type the password of the user you are currently in. You'll then be presented with the 'root' prompt, with a '#' at the end instead of the usual '$'. Be afraid.

Type

```
echo "softdep intel_ips pre: i915" > /etc/modprobe.d/intel-ips-dep-i915.conf
```

i.e. without the 'sudo' prefix. Once that's executed, type 'exit' and press return. Start breathing again.

---

### Post by macflav on 2011-03-27
> **Magnificent 7 said:**
> By the way, being a relative n00b myself, I sympathise with the posters above who reported that 'intel-ips-dep-i915.conf' doesn't exist. It doesn't, until x_lk's command is executed (this is the '>' = "create, if doesn't exist", versus '>>' = "append text to end of file"). To create the file in /etc/modprobe.d you'll need privileges above sudo level. Just type

```
sudo su -
```then type the password of the user you are currently in. You'll then be presented with the 'root' prompt, with a '#' at the end instead of the usual '$'. Be afraid.

Type

```
echo "softdep intel_ips pre: i915" > /etc/modprobe.d/intel-ips-dep-i915.conf
```i.e. without the 'sudo' prefix. Once that's executed, type 'exit' and press return. Start breathing again.


Thanks for that. I always wondered what ever happened to good old "su" (I assumed Ubuntu replaced it with "sudo").

On another note, and back to the i915 issue: shortly after installing Ubuntu (10.10) and updating it, I installed StartUp-Manager to do a little tweaking with Grub. I can't be 100% sure, but I think [COLOR=Red]I didn't have the "turbo disabled" message before that (see update below)[/COLOR]. [COLOR=Red]Ever since I used StartUp-Manager (see update#2)[/COLOR] I don't get the usplash in my monitor's native resolution (1600x900) either -- it shows in 640x480, even if I set vga=799 and GRUB_GFXMODE=1600x900. I've tried reinstalling Grub, but nothing changes. I don't want to reinstall the whole system, so I put up with the bootup lag, the annoying error message and the lack of the beautiful usplash I liked so much.

--- UPDATE ---
Reinstalled Ubuntu (I had to be sure!). The error was there from the start, so please forget I even said that! No regrets, at least I got my nice usplash back [COLOR=Red](I'll never try StartUp-Manager again) (see update#2)[/COLOR].

The only "solution" for me this far is blacklisting intel-ips, but I still get the lag before the splash.

--- UPDATE#2 ---
Sorry for blaming StartUp-Manager. Apparently the splash resolution issue happens after I activate the NVIDIA additional driver. Funny, one would expect video to work *better* with a specific drive rather than a generic one. But I digress...

---

### Post by wujastyk on 2011-03-27
> **x_lk said:**
> Does your laptop come with any intel integrated graphics chip? If not, I guess you don't need the fix at all.


Yes, there is an intel integrated graphics chip.

Dominik

---

### Post by tintinux on 2011-03-28
@de_Selby :

Thanks for your step by step instructions to recompile the kernel.
There is one error for the first patch. I made the update manually.

I managed to compile the new i386 kernel, but this changes nothing. 
Graphics are not activated 9 times over 10 with my HP 8440p / Nvidia 3100
I pray for this issue solved in Natty, otherwise I must either return to Windows or throw my new laptop away...

Thanks for your help !

Tintinux

---

### Post by sdemmitt on 2011-03-29
This fixed it for me.

Only for 64 bit, I repeat 64 bit users only 

It's a modified kernel designed to take advantage of dual core cpus and above. As well as the performance boost, it seems to have fixed the i915 error on boot.

Worked for me but results could vary. Needs testing.

Here is the link

[http://duopetalflower.blogspot.com/2011/03/custom-kernel-26381-ubuntu-amd64.html](http://duopetalflower.blogspot.com/2011/03/custom-kernel-26381-ubuntu-amd64.html)


**Edit**
One issue I found is there doesn't seem to be support for vga switcheroo with this kernel, so it uses considerably more battery power on hybrid graphics systems.

---

### Post by tintinux on 2011-03-29
.

---

### Post by mahaganapati on 2011-03-29
> **sdemmitt said:**
> This fixed it for me.

Only for 64 bit, I repeat 64 bit users only 

It's a modified kernel designed to take advantage of dual core cpus and above. As well as the performance boost, it seems to have fixed the i915 error on boot.

Worked for me but results could vary. Needs testing.

Here is the link

[http://duopetalflower.blogspot.com/2011/03/custom-kernel-26381-ubuntu-amd64.html](http://duopetalflower.blogspot.com/2011/03/custom-kernel-26381-ubuntu-amd64.html)


**Edit**
One issue I found is there doesn't seem to be support for vga switcheroo with this kernel, so it uses considerably more battery power on hybrid graphics systems.

Thank you! This seems to have fixed it for me as well.

---

### Post by yakshbuntu on 2011-03-29
> **sdemmitt said:**
> This fixed it for me.

Only for 64 bit, I repeat 64 bit users only 

It's a modified kernel designed to take advantage of dual core cpus and above. As well as the performance boost, it seems to have fixed the i915 error on boot.

Worked for me but results could vary. Needs testing.

Here is the link

[http://duopetalflower.blogspot.com/2011/03/custom-kernel-26381-ubuntu-amd64.html](http://duopetalflower.blogspot.com/2011/03/custom-kernel-26381-ubuntu-amd64.html)


**Edit**
One issue I found is there doesn't seem to be support for vga switcheroo with this kernel, so it uses considerably more battery power on hybrid graphics systems.

Hi, I built 2.6.38.2 with core2 optimizations with vga_switcheroo and have posted a blog about it here, [http://duopetalflower.blogspot.com/2011/03/custom-kernel-26382-ubuntu-amd64_30.html](http://duopetalflower.blogspot.com/2011/03/custom-kernel-26382-ubuntu-amd64_30.html)

---

### Post by Magnificent 7 on 2011-03-30
> **Magnificent 7 said:**
> I had been toying with the idea of starting a Tecra M11 thread asking for reports on the type of stability issues I'd been experiencing, but will hang fire for a few days to see whether this solves the random freezing issues.

Another lockup today, just after the first resume of the morning. X seemed to try to keep its head above water for a couple of seconds, with the briefest flash of a login screen before descending into The Eternal Blackness with Mouse Pointer. This may have been cruft leftover in the screen buffer after a resolution switch, tho. Not sure whether this maps onto the i915/proprietary/unavailable drivers issue under discussion here.

Curiously, the 'Ubuntu' splash, which had been reduced to an odd-looking top left (640x480?) representation after the softdep fix, returned to full widescreen after this morning's reboot.

Off to start a Tecra M11 stability thread. Thanks for the i915 tip anyway.

---

### Post by carld on 2011-04-02
Is there a bug filed for this? 
Maybe I missed it --- I ran a few searches on [https://bugs.launchpad.net](https://bugs.launchpad.net) with no relevant hits.

---

### Post by macflav on 2011-04-02
> **carld said:**
> Is there a bug filed for this? 
Maybe I missed it --- I ran a few searches on [https://bugs.launchpad.net](https://bugs.launchpad.net) with no relevant hits.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/724569](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/724569)

---

### Post by tarek89 on 2011-04-07
Same problem for me on my Vaio ATI RADEON

---

### Post by Osanya on 2011-04-07
Same problem, none of the above kernels or suggestions fix the problem.  In fact, I can't even boot the last kernel posted.

---

### Post by mahotsava on 2011-04-10
Same problem on Vaio Ati Radeon VPCEA43 with i5. With Mint 10 Julia.

---

### Post by CatmanTiger on 2011-04-21
Hi! I also had the same problem.  But now no error massage after doing correction according to this link:D

[http://linux-software-news-tutorials.blogspot.com/2011/02/fix-bug-failed-to-get-i915-symbols-boot.html](http://linux-software-news-tutorials.blogspot.com/2011/02/fix-bug-failed-to-get-i915-symbols-boot.html)

---

### Post by mexicanseaf00d on 2011-04-21
> **x_lk said:**
> 
Run following command,

```

sudo echo "softdep intel_ips pre: i915" > /etc/modprobe.d/intel-ips-dep-i915.conf

```Then reboot.


Hi, I just wanted to say that this actually works for me! 
HP dv7 notebook with intel i5/ATI 5650 gfxcards
ubuntu 10.10 standard kernel, 
xorg-intel driver 2:2.13.901-2ubuntu2-xup-maverick (from x-swat update ppa, but IIRC I updated AFTER using the above patch)

+ no error messages in dmesg
+ reduced "flickering" when using the FN+brightness keys
+ downside: occasional failure to boot (gets stuck with blinking cursor or straight to commandline instead GDM)

This patch combined with vgaswitcheroo (switch dedicated gfx off for more powersaving) makes me quite happy with my notebook ;)

---

### Post by monteagus on 2011-04-27
mexicanseaf00d
whats going to happen if i run that comand...i mean what changes are going to take place?

---

### Post by mexicanseaf00d on 2011-04-28
quoting the OP of this tip:

> The 'softdep' option tells modprobe that intel_ips module has a soft dependency on i915, meaning intel_ips can be loaded without i915, but will only provide limited functionality. With this option, modprobe will always try to load i915 before inserting intel_ips.


also, if you see someone quoting another posting, theres a little icon next to the quote - it leads to the original message :KS

---

### Post by 135798642 on 2011-04-30
sudo echo "softdep intel_ips pre: i915" > /etc/modprobe.d/intel-ips-dep-i915.conf

not work on my laptop Acer 4745G IntelHD-HD5470 :(

---

### Post by zwigno on 2011-05-27
Use this command instead.  Otherwise your redirect still runs as your user and not root.

```
sudo su -c 'echo "softdep intel_ips pre: i915" >> /etc/modprobe.d/intel-ips-dep-i915.conf'
```

---

### Post by ankit28595 on 2011-06-14
Try this

Open the terminal and type:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Now, at the end of file, type:

```
 blacklist intel_ips 
```

This worked for me!

---

### Post by nbubis on 2011-06-19
Blacklisting only helps if you don't want to use the card together with the nvidia card (say with bumblebee). Any solutions?

---

### Post by Knightsfoil on 2011-07-22
how can I undo this?

```
sudo su -c 'echo "softdep intel_ips pre: i915" >> /etc/modprobe.d/intel-ips-dep-i915.conf'
```I tried it on Asus X52J with Radeon HD 6370 M and it did not resolve and made things worse....:confused:

---

### Post by macflav on 2011-07-23
Knightsfoil, did the file exist already, or did you create it?

If you created a new file (most likely), you can just delete it:
```
sudo rm /etc/modprobe.d/intel-ips-dep-i915.conf
```If you appended that line to the file that already existed, you could edit the file, delete that line (softdep intel_ips pre: i915) and save it.
```
sudo gedit /etc/modprobe.d/intel-ips-dep-i915.conf
```

---

### Post by Knightsfoil on 2011-07-23
thanks macflav! The file only had 1 line in it. I deleted it with your help, and now I'm back to normal. :D  I'll just have to wait for the next release and hope 11.11 bug fix will get turbo graphics working!

---

### Post by OpenKOJU on 2011-08-11
Same problem in HP-Pavilion g6-1037 tx 
i5 480M and ATI Radeon 6470 graphics 
also ubuntu 11.04 don't work in my laptop

---

### Post by gufide on 2011-08-28
Same problem on 11.04. If you can't boot on live cd, try nomodeset, it worked for me

---

### Post by loudog23 on 2011-09-30
Hi Guys,
First time i got stuck on this, i re-installed from scratch..
See signature for machine description

Second time, a week after installation, it crashed again but all my devellopement tools were alredy installed and everything so i tried a few things and here what worked for me.

THe result seems very heiratic (randow ) but here the procedure i've done..I'm gaming once i a while so i have a win7 partition:
1. rebooted in win7,
2. ran a dxdiag (dunno if this as anything to do but i was trying to kick on the graphics turbo in anyway)
3. restarted the machine (not shutdown + power-on)
4. after the grub menu i filled my keyboard buffer with CTRL-C and Ctrl-Z alternatively
5. Boom i was in ubuntu again

6. i did this ->
> [http://linux-software-news-tutorials...bols-boot.html](http://linux-software-news-tutorials...bols-boot.html)

6.1 edit the blacklist conf file
Code:
```

sudo gedit /etc/modprobe.d/blacklist.conf
```

6.2Add this to the end of the file, save and restart:
Code:```


 blacklist intel_ips
```

7. rebooted and voila!


My question is: Does that procedure will redure graphics performance? my 1st guess would be yes but i NEED my linux so i can live with the fall back for now.


hope this helps someone!
cheers everyone!

PS: This was originaly posted at [http://ubuntuforums.org/showthread.php?p=11299851#post11299851](http://ubuntuforums.org/showthread.php?p=11299851#post11299851)

---

### Post by cdysthe on 2011-11-27
Hi,

I see there's two workarounds for this problem. One is blacklisting, the other is this:


sudo su -c 'echo "softdep intel_ips pre: i915" >> /etc/modprobe.d/intel-ips-dep-i915.conf'


Both work for me, but I've stuck with the second quoted above. 

My question is whether one or both of these solutions are simply removing the error message or is one or both are actually correcting the error. Anyone know?

My laptop (Asus U43) has an i5 processor with Intel GMA 940 graphics.

---

### Post by muddpup64 on 2011-12-10
I have the same problem!

I run a Lenovo T410 with a "Intel Processor Integrated Graphics Controller" and a 3i processor. I, like many other, receive an error message upon boot. Though I still have the ability to boot  there is a definite graphics problem.

My question is does any know if Intel is planing on fixing the problem with a new driver or if this is a Gnome problem and should consult them?


Oh, and I am planing on updated to 11.10 if that helps, thanks.

---

### Post by Stratosmacker on 2012-05-02
Has this issue been resolved in a way that is reliable? I have the same issue and there doesn't seem to be a sure fire solution or definite cause for this.

Thanks,
Jesse

---

### Post by Supratimn on 2012-12-04
Same problem in DELL N4010. I'm using Ubuntu 12.04 (precise pangolin)

---

### Post by i915resolu on 2012-12-27
[SIZE=3]Hello,

[SIZE=3]i have an acer 5733 and have the same problem
[SIZE=3]core i3-[/SIZE]370M :Intel HD graphics running ubuntu 12.04 64bits

Solved as this :

[SIZE=3]install t[SIZE=3]he xserver-xorg-video-intel-dbg  [SIZE=3]with [/SIZE]synaptic

[SIZE=3]and [SIZE=3]now no fuc.......k [SIZE=3]"failled to find i915 symbol"

[SIZE=3]i hope that help you. ):P[/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by rocco2 on 2013-09-06
I have started to get this problem on my Dell E6510 with ubuntu 12.04 64 Bit starting with Kernel 3.2.0.-52.78, in 3.2.0.-53.81 it is still there. Seems like the system is booting and performing worse than before. With the old kernel the error is not there. Have a very bad feeling about automatical updates right now since I need to rely on the laptop. Could somebody plz comment on this issue.

---

### Post by macflav on 2013-11-19
I found this very helpful: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Adding '[COLOR=#000000]*GRUB_GFXPAYLOAD_LINUX=text*[/COLOR]' and '[COLOR=#000000]i915modeset=0[/COLOR]' seemed to fix it for me.

---

