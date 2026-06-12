---
title: "Samsung N210 wireless! How to make it work?"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by olig1905 on 2010-06-02
Ok, i have just bought a samsung N210 and new before it even arrived that i wasn't going to be using windows 7 on it. So when it did arrive and i used windows 7 for about 5 minutes i was absolutely certain that it was crap ahahaha. I have now got ubuntu 10.4 netbook remix.

Couple of issues but the main one being :

Wireless wont work!

i have already searched the forums for an answer and not found one im satisfied with. I know how to use ndiswrapper and can't make it work. (just says invalid driver).

Another forum member suggested an email address of realtek and they send you a driver with instructions. 

So i tried this and i got the driver with a really vague set of instructions. I think i deciphered them enough to give it a try and when i typed make i just got a whole lot of instructions.

this is the set of instructions
```

[FONT=Arial Unicode MS][SIZE=1][COLOR=navy][COLOR=navy][FONT=&quot] [/FONT][/COLOR][/COLOR][/SIZE][/FONT]
  [FONT=Arial Unicode MS][SIZE=1][COLOR=navy][COLOR=navy][FONT=&quot]Just kindly remind, please install by the below steps.[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
  [FONT=Arial Unicode MS][SIZE=1][COLOR=navy][COLOR=navy][FONT=&quot]The following is the installing steps:[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
  [FONT=Arial Unicode MS][SIZE=1][COLOR=navy][COLOR=navy][FONT=&quot]1. Change to the driver directory[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
  [FONT=Arial Unicode MS][SIZE=1][COLOR=navy][COLOR=navy][FONT=&quot]2. sudo su[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
  [FONT=Arial Unicode MS][SIZE=1][COLOR=navy][COLOR=navy][FONT=&quot]3. make[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
  [FONT=Arial Unicode MS][SIZE=1][COLOR=navy][COLOR=navy][FONT=&quot]4. make install[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
  [FONT=Arial Unicode MS][SIZE=1][COLOR=navy][COLOR=navy][FONT=&quot]5.reboot[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
  [FONT=Arial Unicode MS][SIZE=1][COLOR=navy][COLOR=navy][FONT=&quot]6. ./wlan0up or ./wlan1u[/FONT][/COLOR][/COLOR][/SIZE][/FONT]

```

Also this is the output of:

lspci -nn | grep Network
sudo lshw -C network

```

oli@oli-netbook:~/rtl8192e_linux_2.6.0014.0401.2010$ lspci -nn | grep Network
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)
oli@oli-netbook:~/rtl8192e_linux_2.6.0014.0401.2010$ sudo lshw -C network
[sudo] password for oli: 
  *-network DISABLED      
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:b9:e0:eb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 00:24:54:43:9f:2b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.2.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f0200000-f0203fff ioport:3000(size=256)


```

I hope this is enough information for someone to help me. If anything else is needed to help please let me know.

Also im not exactly experienced so any help could it pleases be given in the simplest of terms to save me posting again and being like what does that mean. 

Thanks 
Oli

---

### Post by olig1905 on 2010-06-02
also the error i recieve when i try to "make":

```

root@oli-netbook:/home/oli/rtl8192e_linux_2.6.0014.0401.2010# make
/usr/src/linux-headers-2.6.32-22-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.32-22-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
/usr/src/linux-headers-2.6.32-22-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
  CC [M]  /home/oli/rtl8192e_linux_2.6.0014.0401.2010/HAL/rtl8192/rtl_core.o
/bin/sh: gcc: not found
make[2]: *** [/home/oli/rtl8192e_linux_2.6.0014.0401.2010/HAL/rtl8192/rtl_core.o] Error 127
make[1]: *** [_module_/home/oli/rtl8192e_linux_2.6.0014.0401.2010/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [all] Error 2

```

---

### Post by olig1905 on 2010-06-02
Also considering it is a NETbook it isnt exactly useful sitting here next to my router with ethernet cable. 

really really do need to get this wireless working

---

### Post by olig1905 on 2010-06-02
situation has now progressed yet worstened!

i have tried to use chili555's solution using the new driver i downloaded ([http://ubuntuforums.org/showthread.php?t=1391750](http://ubuntuforums.org/showthread.php?t=1391750))
> 
Open a terminal and do: 	Code:
 	sudo apt-get install linux-headers-`uname -r` build-essential 
Those little tick marks are on my US keyboard along with ~.

By default, in Firefox, downloads go to the Desktop. Right-click the  .tar.gz file and select 'Extract here.' A folder will be created called  'rtl8192e-blah-blah' Open a terminal and do: 	Code:
 	cd Desktop/rtl8 
Press the Tab key and the rest will be filled in for you. Press  Enter. Then do: 	Code:
 	make
sudo su
make install
modprobe r8192e-pci
iwconfig 
Do you now have a wireless interface? Can you click Network  Manager and connect?

Please post back any difficulties or errors.



The result of this is i could not get the modprobe to work, i cannot remember seeing any errors in the make install or make command. I have restarted my computer and now have no sign of ubuntu recognising my wireless. (Before it said i had wireless but i couldnt do anything with it)

---

### Post by chili555 on 2010-06-02
What do you mean, you could not get modprobe to work? Did it just come back to the terminal prompt? That means the command was accepted and executed without error.

What does this say?```
lsmod | grep 819
iwconfig
dmesg | grep 819
```Thanks.

---

### Post by olig1905 on 2010-06-02
i have not got time to reply now. I am going out for the evening, thanks for your response and i have juat reinstalled Ubuntu and was going to restart from scratch so if it still does not work i will post my errors i get at modprobe and my results of that code ^^^^


thankyou for your reply

---

### Post by olig1905 on 2010-06-02
ok with my new install i am again stuck at the point of the make command!
here is my output:
```

http://ubuntuforums.org/showthread.php?t=1499820

```

also output of 
lsmod | grep 819
iwconfig
dmesg | grep 819

```

oli@oli-laptop:~/rtl8192e_linux_2.6.0014.0401.2010$ lsmod | grep 819
r8192_pci             243127  0 
oli@oli-laptop:~/rtl8192e_linux_2.6.0014.0401.2010$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

oli@oli-laptop:~/rtl8192e_linux_2.6.0014.0401.2010$ dmesg | grep 819
[   12.480732] r8192_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   12.639734] Linux kernel driver for RTL8192 based WLAN cards
[   12.639827] rtl819xE 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.639843] rtl819xE 0000:05:00.0: setting latency timer to 64
[   12.681943] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
[   15.098881] rtl819xE: PlatformInitFirmware()==>
[   15.099811] rtl819xE 0000:05:00.0: firmware: requesting RTL8192E/boot.img
[   15.130040] rtl819xE:request firmware fail!
[   15.130051] rtl819xE:ERR in init_firmware()
[   15.130061] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[   15.848199]   domain 1: span 0-1 level MC

```

Look forward to your reply if you can help 
so i can finally get this thing working how it should be!

---

### Post by olig1905 on 2010-06-02
first code box is meant to say:

```

oli@oli-laptop:~/rtl8192e_linux_2.6.0014.0401.2010$ make
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
/usr/src/linux-headers-2.6.32-21-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
  CC [M]  /home/oli/rtl8192e_linux_2.6.0014.0401.2010/HAL/rtl8192/rtl_core.o
/bin/sh: gcc: not found
make[2]: *** [/home/oli/rtl8192e_linux_2.6.0014.0401.2010/HAL/rtl8192/rtl_core.o] Error 127
make[1]: *** [_module_/home/oli/rtl8192e_linux_2.6.0014.0401.2010/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [all] Error 2

```

---

### Post by olig1905 on 2010-06-02
just had an idea of running all the updates then trying... may be usefull i dont know? However i have left those running and will post the results of trying again after them in the morning

---

### Post by chili555 on 2010-06-02
> [   15.098881] rtl819xE: PlatformInitFirmware()==>
[   15.099811] rtl819xE 0000:05:00.0: [COLOR="Red"]firmware: requesting RTL8192E/boot.img[/COLOR]
[   15.130040] rtl819xE:request firmware fail!
[   15.130051] rtl819xE:ERR in init_firmware()
[   15.130061] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
It wants firmware and then it will work. I am googling now.

---

### Post by chili555 on 2010-06-02
In the package you downloaded, rtl8192e_linux_2.6.0014.0401.2010, is there any firmware file or package? Tell me what you have and maybe we can place it in the proper place and get you going.

---

### Post by olig1905 on 2010-06-03
I do have a firmware folder it is in the main driver folder along with a folder called HAL and rtlib, then all the other files

---

### Post by olig1905 on 2010-06-03
somehow i missed your previous reply showing what firmware it wanted.... iv seen that file in the firmware folder!

---

### Post by olig1905 on 2010-06-03
sorry for the silly ammount of short replys but surely if i could make and make install it would install the firmware and id have the firmware. right now i can't make the make command work

---

### Post by olig1905 on 2010-06-03
Ok im an idiot, the reason make wasnt working is because i forgot to get the linux headers.

I have now installed the driver and the hardware devices thing in the systems folder confirms this by saying ( Enabled but not in use) see attached image.

so presumeably the modprobe line is what will make it useable. Here is the error message i recieved.

```

root@oli-laptop:/home/oli/rtl8192e_linux_2.6.0014.0401.2010# modprobe r8192e-pci
FATAL: Error inserting r8192e_pci (/lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/r8192e_pci.ko): No such device

```

also  new results of

lsmod | grep 819
iwconfig

dmesg | grep 819
```

root@oli-laptop:/home/oli/rtl8192e_linux_2.6.0014.0401.2010# lsmod | grep 819
r8192_pci             243127  0 
root@oli-laptop:/home/oli/rtl8192e_linux_2.6.0014.0401.2010# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

root@oli-laptop:/home/oli/rtl8192e_linux_2.6.0014.0401.2010# dmesg | grep 819
[    9.985402] r8192_pci: module is from the staging directory, the quality is unknown, you have been warned.
[    9.998545] Linux kernel driver for RTL8192 based WLAN cards
[    9.998631] rtl819xE 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.998646] rtl819xE 0000:05:00.0: setting latency timer to 64
[   18.282914] rtl819xE: PlatformInitFirmware()==>
[   18.282949] rtl819xE 0000:05:00.0: firmware: requesting RTL8192E/boot.img
[   18.371495] rtl819xE:request firmware fail!
[   18.371503] rtl819xE:ERR in init_firmware()
[   18.371510] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[   23.208199]   domain 1: span 0-1 level MC
[11775.888201] rtl819xE 0000:05:00.0: PCI INT A disabled
[11776.638095] rtl819xE 0000:05:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[11776.638129] rtl819xE 0000:05:00.0: restoring config space at offset 0x5 (was 0x0, writing 0xf0100000)
[11776.638142] rtl819xE 0000:05:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x2001)
[11776.638155] rtl819xE 0000:05:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[11776.638170] rtl819xE 0000:05:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x40100103)
[11776.748198] [drm] Big FIFO is enabled
[11776.772818] rtl819xE 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[11776.772831] rtl819xE 0000:05:00.0: setting latency timer to 64
[12387.269322] Linux kernel driver for RTL8192 based WLAN cards
[12387.269367] proc_dir_entry 'net/rtl819xE' already registered
[12387.269372] Modules linked in: r8192e_pci(+) binfmt_misc rfcomm sco bridge stp bnep l2cap ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss fbcon snd_mixer_oss snd_pcm tileblit snd_seq_dummy font bitblit softcursor snd_seq_oss vga16fb snd_seq_midi vgastate joydev snd_rawmidi snd_seq_midi_event i915 snd_seq snd_timer snd_seq_device drm_kms_helper intel_agp snd drm btusb soundcore agpgart i2c_algo_bit psmouse uvcvideo r8192_pci(C) videodev snd_page_alloc video serio_raw v4l1_compat bluetooth output lp parport sky2 ahci
[12387.269608]  [<fcd8b309>] rtl8192_proc_module_init+0x29/0x40 [r8192e_pci]
[12387.269638]  [<fcdd40f3>] rtl8192_pci_module_init+0xf3/0x117 [r8192e_pci]
[12387.269680]  [<fcdd4000>] ? rtl8192_pci_module_init+0x0/0x117 [r8192e_pci]
[12387.269727] Error: Driver 'rtl819xE' is already registered, aborting...
[12412.733525] Modules linked in: r8192e_pci(+) binfmt_misc rfcomm sco bridge stp bnep l2cap ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss fbcon snd_mixer_oss snd_pcm tileblit snd_seq_dummy font bitblit softcursor snd_seq_oss vga16fb snd_seq_midi vgastate joydev snd_rawmidi snd_seq_midi_event i915 snd_seq snd_timer snd_seq_device drm_kms_helper intel_agp snd drm btusb soundcore agpgart i2c_algo_bit psmouse uvcvideo r8192_pci(C) videodev snd_page_alloc video serio_raw v4l1_compat bluetooth output lp parport sky2 ahci
[12412.733757]  [<fcf3613c>] rtllib_init+0x25/0x90 [r8192e_pci]
[12412.733784]  [<fcf3600c>] rtl8192_pci_module_init+0xc/0x117 [r8192e_pci]
[12412.733827]  [<fcf36000>] ? rtl8192_pci_module_init+0x0/0x117 [r8192e_pci]
[12412.733905] Linux kernel driver for RTL8192 based WLAN cards
[12412.733946] proc_dir_entry 'net/rtl819xE' already registered
[12412.733950] Modules linked in: r8192e_pci(+) binfmt_misc rfcomm sco bridge stp bnep l2cap ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss fbcon snd_mixer_oss snd_pcm tileblit snd_seq_dummy font bitblit softcursor snd_seq_oss vga16fb snd_seq_midi vgastate joydev snd_rawmidi snd_seq_midi_event i915 snd_seq snd_timer snd_seq_device drm_kms_helper intel_agp snd drm btusb soundcore agpgart i2c_algo_bit psmouse uvcvideo r8192_pci(C) videodev snd_page_alloc video serio_raw v4l1_compat bluetooth output lp parport sky2 ahci
[12412.734173]  [<fceed309>] rtl8192_proc_module_init+0x29/0x40 [r8192e_pci]
[12412.734203]  [<fcf360f3>] rtl8192_pci_module_init+0xf3/0x117 [r8192e_pci]
[12412.734245]  [<fcf36000>] ? rtl8192_pci_module_init+0x0/0x117 [r8192e_pci]
[12412.734291] Error: Driver 'rtl819xE' is already registered, aborting...
[12603.290679] Modules linked in: r8192e_pci(+) binfmt_misc rfcomm sco bridge stp bnep l2cap ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss fbcon snd_mixer_oss snd_pcm tileblit snd_seq_dummy font bitblit softcursor snd_seq_oss vga16fb snd_seq_midi vgastate joydev snd_rawmidi snd_seq_midi_event i915 snd_seq snd_timer snd_seq_device drm_kms_helper intel_agp snd drm btusb soundcore agpgart i2c_algo_bit psmouse uvcvideo r8192_pci(C) videodev snd_page_alloc video serio_raw v4l1_compat bluetooth output lp parport sky2 ahci
[12603.290907]  [<fd62013c>] rtllib_init+0x25/0x90 [r8192e_pci]
[12603.290938]  [<fd62000c>] rtl8192_pci_module_init+0xc/0x117 [r8192e_pci]
[12603.290981]  [<fd620000>] ? rtl8192_pci_module_init+0x0/0x117 [r8192e_pci]
[12603.291054] Linux kernel driver for RTL8192 based WLAN cards
[12603.291095] proc_dir_entry 'net/rtl819xE' already registered
[12603.291101] Modules linked in: r8192e_pci(+) binfmt_misc rfcomm sco bridge stp bnep l2cap ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss fbcon snd_mixer_oss snd_pcm tileblit snd_seq_dummy font bitblit softcursor snd_seq_oss vga16fb snd_seq_midi vgastate joydev snd_rawmidi snd_seq_midi_event i915 snd_seq snd_timer snd_seq_device drm_kms_helper intel_agp snd drm btusb soundcore agpgart i2c_algo_bit psmouse uvcvideo r8192_pci(C) videodev snd_page_alloc video serio_raw v4l1_compat bluetooth output lp parport sky2 ahci
[12603.291323]  [<fd5d7309>] rtl8192_proc_module_init+0x29/0x40 [r8192e_pci]
[12603.291353]  [<fd6200f3>] rtl8192_pci_module_init+0xf3/0x117 [r8192e_pci]
[12603.291395]  [<fd620000>] ? rtl8192_pci_module_init+0x0/0x117 [r8192e_pci]
[12603.291445] Error: Driver 'rtl819xE' is already registered, aborting...
[12727.492980] Modules linked in: r8192e_pci(+) binfmt_misc rfcomm sco bridge stp bnep l2cap ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss fbcon snd_mixer_oss snd_pcm tileblit snd_seq_dummy font bitblit softcursor snd_seq_oss vga16fb snd_seq_midi vgastate joydev snd_rawmidi snd_seq_midi_event i915 snd_seq snd_timer snd_seq_device drm_kms_helper intel_agp snd drm btusb soundcore agpgart i2c_algo_bit psmouse uvcvideo r8192_pci(C) videodev snd_page_alloc video serio_raw v4l1_compat bluetooth output lp parport sky2 ahci
[12727.493208]  [<fd87a13c>] rtllib_init+0x25/0x90 [r8192e_pci]
[12727.493235]  [<fd87a00c>] rtl8192_pci_module_init+0xc/0x117 [r8192e_pci]
[12727.493277]  [<fd87a000>] ? rtl8192_pci_module_init+0x0/0x117 [r8192e_pci]
[12727.493355] Linux kernel driver for RTL8192 based WLAN cards
[12727.493395] proc_dir_entry 'net/rtl819xE' already registered
[12727.493399] Modules linked in: r8192e_pci(+) binfmt_misc rfcomm sco bridge stp bnep l2cap ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss fbcon snd_mixer_oss snd_pcm tileblit snd_seq_dummy font bitblit softcursor snd_seq_oss vga16fb snd_seq_midi vgastate joydev snd_rawmidi snd_seq_midi_event i915 snd_seq snd_timer snd_seq_device drm_kms_helper intel_agp snd drm btusb soundcore agpgart i2c_algo_bit psmouse uvcvideo r8192_pci(C) videodev snd_page_alloc video serio_raw v4l1_compat bluetooth output lp parport sky2 ahci
[12727.493621]  [<fd831309>] rtl8192_proc_module_init+0x29/0x40 [r8192e_pci]
[12727.493651]  [<fd87a0f3>] rtl8192_pci_module_init+0xf3/0x117 [r8192e_pci]
[12727.493693]  [<fd87a000>] ? rtl8192_pci_module_init+0x0/0x117 [r8192e_pci]
[12727.493739] Error: Driver 'rtl819xE' is already registered, aborting...

```

---

### Post by olig1905 on 2010-06-03
i just restarted and it worked dont know why ahah! Thankyou chili555 for your help it was your guide on the other thread that ultimately got this task done

---

### Post by jadencore on 2010-06-10
Hi all, Im extremely new to ubuntu and would greatly appreciate any help with the wireless problem. 
I have tried following this thread as well as a few others but so far (probably due to not understanding instructions) i havent been able to get wifi working.

Im using a Samsung R420 with a  10.04

lspci -nn | grep Network
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)

sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:54:8f:d8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:2000(size=256) memory:f6000000-f6003fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:ea:88:66
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:fa000000-fa003fff ioport:4000(size=256)

Thanks for the help!

---

### Post by olig1905 on 2010-06-10
right.,,, it looks as though you have the same wireless thingymaboob as me.

have you emailed realtek for the driver? IF YOU HAVE THEN CONTINUE!

if not then email [email]wlanfae@realtek.com[/email] and ask for the rtl8192 linux driver.

they should repsond within 5 minutes.

Download the driver and extract it to a location your happy with.
**NOTE** ignore the instructions they give you i couldnt make them work.

Firstly update linux headers.... connect to internet using ethernet(hassle i know but necessary)

```
sudo apt-get install linux-headers-`uname -r` build-essential
```

open a terminal and cd to the location so for example in downloads

```
cd /home/oli/rtl8192e_linux_2.6.0014.0401.2010/ (replace oli with your username)
```

now you just have to install it

```
make
sudo su
make install
modprobe r8192e-pci
iwconfig
```

**NOTE** dont worry if the modprobe produces errors because mine does and my wireless still works

Restart your computer and your wireless should work..

Credit should go to chili555 for this!!!

---

### Post by jadencore on 2010-06-16
Thanks man internet works fine now

---

### Post by jadencore on 2010-06-17
Hi again, unfortunately the fix worked for about 1 day now my internet is highly erratic, it keeps disconnecting and is unable to reconnect for long periods of time. 

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:54:8f:d8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE driverversion=0014.0401.2010 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:2000(size=256) memory:f6000000-f6003fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:ea:88:66
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fa000000-fa003fff ioport:4000(size=256)

Sorry to be back so quick and thanks in advance for the help.

---

### Post by jadencore on 2010-06-17
I realised I wasnt very descriptive in the last post, basically after i installed the realtek driver i was able to connect to the internet. But after I shutdown and rebooted I couldn't reconnect. I can still see the available wireless networks but when it askes for network authentification required and I enter the password the entire window freezes. The network connections under preferences also hangs on start up.

This is annoying as I am back to where i was a week ago. Thanks for the help!

---

### Post by eccs on 2010-06-18
> **olig1905 said:**
>  ...and your wireless should work. 

Thanks -

I also have a SAMSUNG N210 that, similarly, was initially affected by non-compliant wireless, but the issues are completely rectified by your excellent step-by-step fix.

It is possibly of interest to those who e-mail REALTEK at a busy moment (I assume this is probably an affect of the time difference between the UK and the USA!) and cannot access the RLT8192E immediately that a seemingly up to date edition is available with a little googling of:

```
ubuntu / samsung N210 wireless driver
```For me, this was the 5th or so link.

---

### Post by olig1905 on 2010-06-23
good im glad other people have now found doing this easier.. i do not take any credit however all i did was copy and paste haha

---

### Post by afroldy on 2010-07-21
Hello chaps.

I bought a Samsung n210 yesterday, installed ubuntu netbook remix on it and now I'm absolutely tearing my hair out trying to get the wireless to work. I emailed realtek asking for the driver a few hours ago and have received no reply yet, possibly because of time differences I suppose (I'm in the UK). 

Anyway, I managed what appears to be the most recent version of the driver, downloaded it and followed the instructions given:

1. Change to the driver directory
  2. sudo su
  3. make
  4. make install
  5.reboot
  6. ./wlan0up or ./wlan1u

Step 6 is where things go awry. When I type this command into the terminal I get the response:

insmod: can't read 'r8192e_pci.ko': No such file or directory


And it's not wrong, no such file appears to exist anywhere in the folder.
Can anyone give me an idea of what I'm doing wrong? One thing I should mention is that I haven't updated the 'linux headers' as advised to by the original poster. I haven't access to a wired connection so it's impossible to connect the netbook to the internet. I tried downloading the headers from the ubuntu website onto my other, working, laptop, and transferring them via a USB stick, but when I tried to install them ubuntu claimed that they were an older version that what already exists on the system. 

So can my missing out of this step be the problem, or not? 

Thanks in advance, and sorry for the long post!

---

### Post by siennalizard on 2010-07-27
Many thanks for the clear instructions.

For those of you who aren't prepared to wait for Realtek to either e-mail out drivers or update their site, you'll find the file you need here (in the first post):

[http://ubuntuforums.org/showthread.php?t=1460038](http://ubuntuforums.org/showthread.php?t=1460038)


Thanks again: my wireless is working.

---

### Post by justkillingtime on 2010-08-31
realtek do answer really quickly ... had a problem with my n130 but the driver compiled ok ... once i figured it out if your really noobish u can extract to your home and when u type sudo su u literally need to follow the instructions no finding ur directory u extracted too but im a king noob at the moment soo

---

