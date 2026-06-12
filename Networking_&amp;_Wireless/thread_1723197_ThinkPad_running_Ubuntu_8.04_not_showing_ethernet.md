---
title: "ThinkPad running Ubuntu 8.04 not showing ethernet?"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by Liberty101 on 2011-04-06
Hey everyone,

My professor gave me an older ThinkPad, i1161, because he wants me to learn linux. So far, I successfully downloaded Hardy Heron onto the computer, using the Alternate version. Everything works great, and I can log on, play games, go into word processor, the whole nine yards. Unfortunately, the computer won't connect to the ethernet cable that I have plugged in. I am not sure what I am doing wrong, but that is probably because I don't know where to begin.

I also get an error message during boot, it says "ACPI no DMI Bios year" then it says "ACPI=force is required to enable ACPI. I don't know what this means, but I fugured it might have something to do with the ethernet.

I am connecting through my University internet. Also, under Network Settings ->Connections, it only has one option, "Point to point connection" and it says "This network interface is not configured."
:confused:
Any help would be greatly appreciated.

---

### Post by Liberty101 on 2011-04-12
Can anyone please help?

---

### Post by chili555 on 2011-04-12
Please open a terminal and run and post:```
sudo lshw -C network
dmesg | grep -i error
```

---

### Post by Liberty101 on 2011-04-12
I am a noob when it comes to command prompts. Do you want me to run both lines at the same time? I tried to run "sudo lshw -C network" and nothing came up. When I tried to run "dmesg | grep -i error" nothing happens either. I am probably an idiot, but I wasn't sure how to put 2 command lines in at once, or if that is even possible. I get something when I just put "sudo lshw", would you like me to list all of that?

---

### Post by chili555 on 2011-04-12
They are two separate commands, to be run one at a time. The command sudo lshw -C network asks the system to list all of the hardware of the class 'network,' in other words, ethernet and wireless cards. Nothing is returned. Is the ethernet enabled in the computer's BIOS?

The other command asks if there are any errors in the boot up messages. There are none, but there may be warnings. Let's see:```
dmesg | grep -i warn
```Let's also see:```
lspci -nn | grep -i ethernet
```

---

### Post by Liberty101 on 2011-04-12
First off, thanks for helping me! 

I went into the BIOS to see if the ethernet was enabled (I don't have a wireless card) and I could not find where I could check to see the status of the ethernet. What would be the best way to check this? Am I looking in the wrong place? I just booted up, hit F1, and looked through all the menus...

Also, you mentioned boot errors, and I get this, "ACPI no DMI Bios year"  then it says "ACPI=force is required to enable ACPI."


Secondly, for the "dmesg | grep -i warn" and "lspci -nn | grep -1 ethernet" nothing came up either. Am I doing something wrong? I type it in, press enter, and then it just gives me a new command line header thing:

jacob@ubuntu:~$ dmesg | grep -i warn

and it just gives me 

jacob@ubuntu:~$ 

again?

Again, thanks so much for helping me, my fiancee's vista computer just crashed because winsxs took up all her disk space, so I am trying to surprise her with a working computer...

---

### Post by chili555 on 2011-04-13
> I went into the BIOS to see if the ethernet was enabled (I don't have a wireless card) and I could not find where I could check to see the status of the ethernet. What would be the best way to check this? Am I looking in the wrong place? I just booted up, hit F1, and looked through all the menus...That's about all you can do. If there is no menu item to enable or disable ethernet, then there is nothing in the BIOS that you can do.> Secondly, for the "dmesg | grep -i warn" and "lspci -nn | grep -1 ethernet" nothing came up either. Am I doing something wrong? I type it in, press enter, and then it just gives me a new command line header thing:When the command yields no text, it simply means, roughly, 'I've executed the command and this is what I found: nothing.' In your case, it means we find no errors or warnings in the boot messages.

Before we do exploratory surgery, let's check two other things. First, run and post:```
dmesg | grep -i acpi
```Next, go back in the BIOS and look for two things. First, see if there is any menu item to enable or disable ACPI. Enable it if not already.

Second, see if the is a menu item for IRQs. Please see attached. If there are selections available, use Auto or Auto Select. Be sure to save your changes (often with F10) before you proceed.

Now run:```
sudo lshw -C network
```Does the ethernet show up? If not, we have one more trick in our hat.> lspci -nn | grep -1 ethernetThat's an i not a 1. Eye not one.

---

### Post by psusi on 2011-04-13
Hardy is 3 years old now and depreciated.  You should install Lucid or Maverick instead.

---

### Post by Liberty101 on 2011-04-13
jacob@ubuntu:~$ dmesg | grep -i acpi
 [    0.000000]  BIOS-e820: 000000000bff0000 - 000000000bff8000 (ACPI data)
 [    0.000000]  BIOS-e820: 000000000bff8000 - 000000000c000000 (ACPI NVS)
 [    0.000000] ACPI: RSDP signature @ 0xC00FE030 checksum 0
 [    0.000000] ACPI: RSDP 000FE030, 0014 (r0 IBM   )
 [    0.000000] ACPI: RSDT 0BFF0000, 0030 (r1 IBM    ATLANTA         1 IBM         0)
 [    0.000000] ACPI: FACP 0BFF008C, 0074 (r1 IBM    ATLANTA         1 IBM         0)
 [    0.000000] ACPI: DSDT 0BFF0104, 2FED (r1    IBM ThinkPad     1000 MSFT  100000C)
 [    0.000000] ACPI: FACS 0BFF8000, 0040
 [    0.000000] ACPI: BOOT 0BFF0030, 0028 (r1 IBM    ATLANTA         1 IBM         0)
 [    0.000000] ACPI: DBGP 0BFF0058, 0034 (r1 IBM    ATLANTA         1 IBM         0)
 [    0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
 [    0.000000] ACPI: Disabling ACPI support
 [   32.685755] ACPI: Interpreter disabled.
 [   32.685950] pnp: PnP ACPI: disabled
 [   32.697612] PCI quirk: region f000-f03f claimed by PIIX4 ACPI
 [   38.119224] thermal: Unknown symbol acpi_processor_set_thermal_limit
 [   84.526844] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
 [   84.527276] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
 [   84.528379] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
 [   84.528994] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
 jacob@ubuntu:~$  
 

Here is this part, I will let you know what I find in the BIOS in a few minutes.

---

### Post by Liberty101 on 2011-04-13
In my BIOS, there is a section called "Onboard Devices Configuration." This is what is shows:

Parallel Port --------------[Enabled] (I can disable it also)
     Base Address---------Has multiple options; "3BCh", "378h", and "278h". It is 3BCh now.
     IRQ--------------------Has 2 options; "7" and "5", on "7" right now.
     Operation Mode------Has a few options; "ECP", "Standard", "Bi-directional", and "EPP"
     ECP DMA Channel---If the prior setting is on ECP, I have 2 options; "1" and "3". Currently set on Bi-directional, and has ECP DMA channel inactive.

I've got to go to Economics Class, but I will be back in a few hours. Thanks!

Ohh, and psusi, I tried Maverick, but the computer wouldn't boot it right. I tried like 4 different versions until I found this one that worked.

---

### Post by psusi on 2011-04-13
> **Liberty101 said:**
> 
Ohh, and psusi, I tried Maverick, but the computer wouldn't boot it right. I tried like 4 different versions until I found this one that worked.

How about Lucid?  You certainly don't want to be running an obsolete and unsupported release, so you need to try to get one of them running.

---

### Post by Liberty101 on 2011-04-13
I have not tried Lucid. I am willing to give it a shot though, what is the best route for me to take? I had to use the alternate download for 8.04, will the regular version work for lucid? Or is it just something that I will have to tinker with?

Which of the options from this link should I try? [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

Thanks

---

### Post by chili555 on 2011-04-13
Please do:```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
sudo gedit /boot/grub/menu.lst
```The file you are editing will look (very) roughly like this:> default 1

timeout 10

title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

To the top kernel line, please add as I have indicated:```
title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash [COLOR="Red"]acpi=force[/COLOR]
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```Don't worry if your lines are slightly different; you just need to add the acpi=force line to the latest kernel listing at the end of the correct line. If in doubt, stop and post back.

Proofread carefully, save and close gedit. Now reboot and run:```
sudo lshw -C network
```Any ethernet card showing?

---

### Post by Liberty101 on 2011-04-13
When I entered this line: 
```
sudo cp /boot/grub/menu.1st /boot/grub/menu.1st-backup
```
It said:
cp: cannot stat '/boot/grub/menu.1st' : No such file or directory

I then tried the gedit line and it pulled up a word processor type thing but it was blank and did not contain any lines like you mentioned. I think I can access that kernel by hitting esc when booting up, and I think that can take me to the kernel line. Not sure though.

I tried typing in "sudo lshw" and here is what I got. I figured it might give you more information.

```
jacob@ubuntu:~$ sudo lshw  
 ubuntu                     
     description: Computer  
     width: 32 bits  
   *-core  
        description: Motherboard  
        physical id: 0  
      *-memory  
           description: System memory  
           physical id: 0  
           size: 191MiB  
      *-cpu  
           product: Celeron (Coppermine) 
           vendor: Intel Corp.  
           physical id: 1  
           bus info: cpu@0  
           version: 6.8.3  
           size: 550MHz  
           width: 32 bits  
           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up  
         *-cache:0  
              description: L1 cache  
              physical id: 0  
              size: 32KiB  
         *-cache:1  
              description: L2 cache  
              physical id: 1  
              size: 128KiB  
      *-pci  
           description: Host bridge  
           product: 82440MX Host Bridge  
           vendor: Intel Corporation  
           physical id: 100  
           bus info: pci@0000:00:00.0  
           version: 01  
           width: 32 bits  
           clock: 33MHz  
           configuration: latency=64  
         *-multimedia  
              description: Multimedia audio controller  
              product: 82440MX AC'97 Audio Controller  
              vendor: Intel Corporation  
              physical id: 0.1  
              bus info: pci@0000:00:00.1 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master  
              configuration: driver=Intel ICH latency=0 module=snd_intel8x0  
         *-communication UNCLAIMED  
              description: Modem  
              product: 82440MX AC'97 Modem Controller  
              vendor: Intel Corporation  
              physical id: 0.2  
              bus info: pci@0000:00:00.2 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: generic  
              configuration: latency=0  
         *-display UNCLAIMED  
              description: VGA compatible controller  
              product: SM712 LynxEM+  
              vendor: Silicon Motion, Inc.  
              physical id: 2  
              bus info: pci@0000:00:02.0 
              version: a0  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pm vga_controller bus_master cap_list  
              configuration: latency=32  
         *-pcmcia  
              description: CardBus bridge  
              product: OZ6812 CardBus Controller  
              vendor: O2 Micro, Inc.  
              physical id: 3  
              bus info: pci@0000:00:03.0 
              version: 05  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pcmcia bus_master cap_list  
              configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket  
         *-isa  
              description: ISA bridge  
              product: 82440MX ISA Bridge  
              vendor: Intel Corporation  
              physical id: 7  
              bus info: pci@0000:00:07.0 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: isa bus_master  
              configuration: latency=0  
         *-ide  
              description: IDE interface 
              product: 82440MX EIDE Controller  
              vendor: Intel Corporation  
              physical id: 7.1  
              bus info: pci@0000:00:07.1 
              logical name: scsi0  
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: ide bus_master emulated  
              configuration: driver=ata_piix latency=32 module=ata_piix  
            *-disk  
                 description: ATA Disk  
                 product: HITACHI_DK23AA-6  
                 vendor: Hitachi  
                 physical id: 0.0.0  
                 bus info: scsi@0:0.0.0  
                 logical name: /dev/sda  
                 version: 00XE  
                 serial: G17221  
                 size: 5729MiB (6007MB)  
                 capabilities: partitioned partitioned:dos  
                 configuration: ansiversion=5 signature=90909090  
               *-volume:0  
                    description: EXT3 volume  
                    vendor: Linux  
                    physical id: 1  
                    bus info: scsi@0:0.0.0,1  
                    logical name: /dev/sda1  
                    logical name: /  
                    logical name: /dev/.static/dev  
                    version: 1.0  
                    serial: 40e23489-ab07-4b8e-986a-9d8e82c9a6cf  
                    size: 5428MiB  
                    capacity: 5428MiB  
                    capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized  
                    configuration: created=2011-04-06 06:26:19 filesystem=ext3 modified=2011-04-13 14:54:55 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2011-04-13 14:54:55 state=mounted  
               *-volume:1  
                    description: Extended partition  
                    physical id: 2  
                    bus info: scsi@0:0.0.0,2  
                    logical name: /dev/sda2  
                    size: 298MiB  
                    capacity: 298MiB  
                    capabilities: primary extended partitioned partitioned:extended  
                  *-logicalvolume  
                       description: Linux swap / Solaris partition  
                       physical id: 5  
                       logical name: /dev/sda5  
                       capacity: 298MiB  
                       capabilities: nofs  
            *-cdrom  
                 description: SCSI CD-ROM  
                 product: CD-224E  
                 vendor: TEAC  
                 physical id: 0.1.0  
                 bus info: scsi@0:0.1.0  
                 logical name: /dev/cdrom  
                 logical name: /dev/scd0 
                 logical name: /dev/sr0  
                 version: 1.6A  
                 serial: TEAC    CD-224E         1.6A  
                 capabilities: removable audio  
                 configuration: ansiversion=5 status=open  
         *-usb  
              description: USB Controller  
              product: 82440MX USB Universal Host Controller  
              vendor: Intel Corporation  
              physical id: 7.2  
              bus info: pci@0000:00:07.2 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: uhci bus_master  
              configuration: driver=uhci_hcd latency=32 module=uhci_hcd  
         *-bridge  
              description: Bridge  
              product: 82440MX Power Management Controller  
              vendor: Intel Corporation  
              physical id: 7.3  
              bus info: pci@0000:00:07.3 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bridge  
              configuration: driver=piix4_smbus latency=0 module=i2c_piix4  
 jacob@ubuntu:~$  

```

---

### Post by psusi on 2011-04-13
> **Liberty101 said:**
> I have not tried Lucid. I am willing to give it a shot though, what is the best route for me to take? I had to use the alternate download for 8.04, will the regular version work for lucid? Or is it just something that I will have to tinker with?

Which of the options from this link should I try? [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

Thanks

The desktop cd should work.

---

### Post by chili555 on 2011-04-13
> sudo cp /boot/grub/menu.1st /boot/grub/menu.[COLOR="Red"]1[/COLOR]st-backupIs that a one? It's supposed to be an ell. Sort of, 'menu list.' Please try again.

---

### Post by Liberty101 on 2011-04-13
Nope, nothing. I tried again using the "L" and it worked perfectly. Then I edited it, saved, rebooted, and tried the -C network line again and nothing came up.

Should I try to reinstall the entire operating system with the ethernet cable plugged in? I don't think I had it plugged in when I did my install. Could that have an effect?

---

### Post by chili555 on 2011-04-13
What does this tell us?```
dmesg | grep -i acpi
```

---

### Post by Liberty101 on 2011-04-13
```
jacob@ubuntu:~$ dmesg | grep -i acpi  
 [    0.000000]  BIOS-e820: 000000000bff0000 - 000000000bff8000 (ACPI data)  
 [    0.000000]  BIOS-e820: 000000000bff8000 - 000000000c000000 (ACPI NVS)  
 [    0.000000] ACPI: RSDP signature @ 0xC00FE030 checksum 0  
 [    0.000000] ACPI: RSDP 000FE030, 0014 (r0 IBM   )  
 [    0.000000] ACPI: RSDT 0BFF0000, 0030 (r1 IBM    ATLANTA         1 IBM         0)  
 [    0.000000] ACPI: FACP 0BFF008C, 0074 (r1 IBM    ATLANTA         1 IBM         0)  
 [    0.000000] ACPI: DSDT 0BFF0104, 2FED (r1    IBM ThinkPad     1000 MSFT  100000C)  
 [    0.000000] ACPI: FACS 0BFF8000, 0040  
 [    0.000000] ACPI: BOOT 0BFF0030, 0028 (r1 IBM    ATLANTA         1 IBM         0)  
 [    0.000000] ACPI: DBGP 0BFF0058, 0034 (r1 IBM    ATLANTA         1 IBM         0)  
 [    0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI  
 [    0.000000] ACPI: Disabling ACPI support  
 [   34.453189] ACPI: Interpreter disabled.  
 [   34.453383] pnp: PnP ACPI: disabled  
 [   34.465061] PCI quirk: region f000-f03f claimed by PIIX4 ACPI  
 [   39.910746] thermal: Unknown symbol acpi_processor_set_thermal_limit  
 [   88.974231] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm  
 [   88.974650] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance  
 [   88.975844] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance  
 [   88.976453] acpi_cpufreq: Unknown symbol acpi_processor_register_performance  
 jacob@ubuntu:~$  

```

---

### Post by chili555 on 2011-04-14
> Should I try to reinstall the entire operating system with the ethernet cable plugged in? I don't think I had it plugged in when I did my install. Could that have an effect?I doubt it has any effect. I have done many an install on many a computer without an ethernet cable; none has any difficulty recognizing the unused ethernet card.

You might try a later version as has been suggested. You can run the live CD and find out before you reinstall.

Is there any option in the BIOS for plug and play operating system (PnP)? Older computers often have better results with that option set to No.

I am out of suggestions.

---

### Post by chili555 on 2011-04-14
Let's double-check your amendments. Please post:```
cat /boot/grub/menu.lst
```

---

### Post by Liberty101 on 2011-05-02
jacob@ubuntu:~$ cat /boot/grub/menu.lst 
 # menu.lst - See: grub(8), info grub, update-grub(8)  
 #            grub-install(8), grub-floppy(8),  
 #            grub-md5-crypt, /usr/share/doc/grub  
 #            and /usr/share/doc/grub-doc/.  
 

 ## default num  
 # Set the default entry to the entry number NUM. Numbering starts from 0, and  
 # the entry number 0 is the default if the command is not used.  
 #  
 # You can specify 'saved' instead of a number. In this case, the default entry  
 # is the entry saved with the command 'savedefault'.  
 # WARNING: If you are using dmraid do not use 'savedefault' or your  
 # array will desync and will not let you boot your system.  
 default        0  
 

 ## timeout sec  
 # Set a timeout, in SEC seconds, before automatically booting the default entry  
 # (normally the first entry defined).  
 timeout        3  
 

 ## hiddenmenu  
 # Hides the menu by default (press ESC to see the menu)  
 hiddenmenu  
 

 # Pretty colours  
 #color cyan/blue white/blue  
 

 ## password ['--md5'] passwd  
 # If used in the first section of a menu file, disable all interactive editing  
 # control (menu entry editor and command-line)  and entries protected by the  
 # command 'lock'  
 # e.g. password topsecret  
 #      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/  
 # password topsecret  
 

 #  
 # examples  
 #  
 # title        Windows 95/98/NT/2000  
 # root        (hd0,0)  
 # makeactive  
 # chainloader    +1  
 #  
 # title        Linux  
 # root        (hd0,1)  
 # kernel    /vmlinuz root=/dev/hda2 ro  
 #  
 

 #  
 # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST  
 

 ### BEGIN AUTOMAGIC KERNELS LIST  
 ## lines between the AUTOMAGIC KERNELS LIST markers will be modified  
 ## by the debian update-grub script except for the default options below  
 

 ## DO NOT UNCOMMENT THEM, Just edit them to your needs  
 

 ## ## Start Default Options ##  
 ## default kernel options  
 ## default kernel options for automagic boot options  
 ## If you want special options for specific kernels use kopt_x_y_z  
 ## where x.y.z is kernel version. Minor versions can be omitted.  
 ## e.g. kopt=root=/dev/hda1 ro  
 ##      kopt_2_6_8=root=/dev/hdc1 ro  
 ##      kopt_2_6_8_2_686=root=/dev/hdc2 ro  
 # kopt=root=UUID=40e23489-ab07-4b8e-986a-9d8e82c9a6cf ro  
 

 ## Setup crashdump menu entries  
 ## e.g. crashdump=1  
 # crashdump=0  
 

 ## default grub root device  
 ## e.g. groot=(hd0,0)  
 # groot=(hd0,0)  
 

 ## should update-grub create alternative automagic boot options  
 ## e.g. alternative=true  
 ##      alternative=false  
 # alternative=true  
 

 ## should update-grub lock alternative automagic boot options  
 ## e.g. lockalternative=true  
 ##      lockalternative=false  
 # lockalternative=false  
 

 ## additional options to use with the default boot option, but not with the  
 ## alternatives  
 ## e.g. defoptions=vga=791 resume=/dev/hda5  
 # defoptions=quiet splash  
 

 ## should update-grub lock old automagic boot options  
 ## e.g. lockold=false  
 ##      lockold=true  
 # lockold=false  
 

 ## Xen hypervisor options to use with the default Xen boot option  
 # xenhopt=  
 

 ## Xen Linux kernel options to use with the default Xen boot option  
 # xenkopt=console=tty0  
 

 ## altoption boot targets option  
 ## multiple altoptions lines are allowed  
 ## e.g. altoptions=(extra menu suffix) extra boot options  
 ##      altoptions=(recovery) single  
 # altoptions=(recovery mode) single  
 

 ## controls how many kernels should be put into the menu.lst  
 ## only counts the first occurence of a kernel, not the  
 ## alternative kernel options  
 ## e.g. howmany=all  
 ##      howmany=7  
 # howmany=all  
 

 ## should update-grub create memtest86 boot option  
 ## e.g. memtest86=true  
 ##      memtest86=false  
 # memtest86=true  
 

 ## should update-grub adjust the value of the default booted system  
 ## can be true or false  
 # updatedefaultentry=false  
 

 ## should update-grub add savedefault to the default options  
 ## can be true or false  
 # savedefault=false  
 

 ## ## End Default Options ##  
 

 title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic  
 root        (hd0,0)  
 kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=40e23489-ab07-4b8e-986a-9d8e82c9a6cf ro quiet splash acpi=force  
 initrd        /boot/initrd.img-2.6.24-26-generic 
 quiet  
 

 title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)  
 root        (hd0,0)  
 kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=40e23489-ab07-4b8e-986a-9d8e82c9a6cf ro single  
 initrd        /boot/initrd.img-2.6.24-26-generic 
 

 title        Ubuntu 8.04.4 LTS, memtest86+  
 root        (hd0,0)  
 kernel        /boot/memtest86+.bin  
 quiet  
 

 ### END DEBIAN AUTOMAGIC KERNELS LIST

Sorry it took so long for me to respond, I went home for easter, then I forgot for a while...sorry!

---

### Post by Liberty101 on 2011-05-02
I also tried to install 10.04 LTS for the laptop, but all I am getting is what looks like the terminal screen. No desktop comes up or anything, just a black screen that looks like terminal....

---

### Post by chili555 on 2011-05-02
Your change looks exactly correct. If that didn't fix it, I really have no other ideas. Sorry.

---

### Post by Liberty101 on 2011-05-02
Thats alright. I just got a hold of a Belkin N150 USB wireless adapter that I am attempting to try and get going. How do I determine the chipset of the device? I've seen most people say it is a type of ralink...

---

### Post by chili555 on 2011-05-02
> **Liberty101 said:**
> Thats alright. I just got a hold of a Belkin N150 USB wireless adapter that I am attempting to try and get going. How do I determine the chipset of the device? I've seen most people say it is a type of ralink...In a terminal, run:```
lsusb
```Search this forum for the usb.id, a sequence like: 12ab:34cd or similar.

Post back if I can help.

---

