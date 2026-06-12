---
title: "New Edgy Install - No Sound"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by faedrake on 2006-11-10
I just finished a fresh install of Ubuntu Edgy server, and then I used apt-get to install the Ubuntu desktop.  A post I had read somewhere said this was the best way to proceed if I wanted both server and gui.  But, I have no sound.

I'm a 99% linux newbie.  I had Dapper installed before (same method, installed lamp server then apt-get desktop), and the sound was not on by default.  I managed to get it to work with a single command that contained alsa. Of course that was months ago and I don't have the command any longer, nor can I find it again.

aplay -l gives me:

aplay: device_list:222: no soundcards found...

lspci -v gives me:

> 00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 23)
        Flags: bus master, medium devsel, latency 64
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at eddff000 (32-bit, prefetchable) [size=4K]
        I/O ports at dc00 [disabled] [size=4]
        Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: ede00000-efefffff
        Prefetchable memory behind bridge: d5b00000-ddcfffff

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 1b)
        Subsystem: VIA Technologies, Inc. VT82C686/A PCI to ISA Bridge
        Flags: bus master, stepping, medium devsel, latency 0

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Flags: bus master, medium devsel, latency 32
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 0e) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at d400 [size=32]
        Capabilities: <access denied>

00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 0e) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at d800 [size=32]
        Capabilities: <access denied>

00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 20)
        Flags: medium devsel

00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at d000 [size=256]
        Memory at efffff00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:05.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Memory at ddc80000 (32-bit, prefetchable) [size=512K]
        Expansion ROM at efef0000 [disabled] [size=64K]
        Capabilities: <access denied>


I checked, and I should be using the sbawe driver.

When I tried sudo modprobe snd-sbawe I get a Segmentation fault and the following text:

> Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000019] Oops: 0000 [#1]

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000023] SMP 

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000122] CPU:    0

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000152] EIP is at kref_get+0x6/0x40

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000161] eax: 07400022   ebx: 07400022   ecx: dad945e0   edx: 00000000

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000171] esi: dad942e0   edi: 00000000   ebp: 00000002   esp: d47ade1c

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000178] ds: 007b   es: 007b   ss: 0068

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000187] Process modprobe (pid: 5025, threadinfo=d47ac000 task=d8534ab0)

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000193] Stack: 00000081 00000081 00002a18 00000008 0740000a c01dfedf dad94360 c02455be 

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000212]        c0245a3c 00000014 dad94360 c037d714 dad945e0 dad942e8 ffffffea 00000001 

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000231]        dad942e0 dad942e0 fffffff4 dad945e0 00000002 c0245dad d47adea0 d47adea0 

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000249] Call Trace:

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000264]  <c01dfedf> kobject_get+0xf/0x20  <c02455be> class_device_get+0xe/0x20

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000295]  <c0245a3c> class_device_add+0x5c/0x330  <c0245dad> class_device_create+0x8d/0xc0

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000343]  <e0b902fb> snd_register_device+0xcb/0x100 [snd]  <e0a8e14b> alsa_timer_init+0x14b/0x1fc [snd_timer]

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000449]  <c013bb28> sys_init_module+0x148/0x19c0  <c0166990> __kmalloc+0x0/0x70

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000563]  <c0102f8b> sysenter_past_esp+0x54/0x75 

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000601] Code: 08 35 00 00 00 c7 44 24 04 5b af 2f c0 c7 04 24 23 f5 2e c0 e8 fc 16 f4 ff e8 57 3c f2 ff eb 80 90 8d 74 26 00 53 89 c3 83 ec 10 <8b> 00 85 c0 74 08 90 ff 03 83 c4 10 5b c3 c7 44 24 0c f9 18 2e 

Message from syslogd@alcove at Fri Nov 10 12:53:48 2006 ...
alcove kernel: [  557.000675] EIP: [kref_get+6/64] kref_get+0x6/0x40 SS:ESP 0068:d47ade1c


Edit: now when I try sudo modprobe snd-sbawe the terminal remains blank, there is no response and the command prompt does not come back unless I close and reopen the terminal window.

Initially sbawe was not listed under modprobe, so I tried to install it under the directions I read in the Sound Problems Guide.  

First, when I tried sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source

I got this error:
E: Couldn't find package module-assistant

When I tried again without module-assistant (because it said it was optional) I got this error:
E: Couldn't find package alsa-source

So, I proceeded to download and compile the drivers from the alsa project.  All of these steps went fine, and it ended saying it installed successfully.  I have rebooted.  However I still have no sound and still get the above errors.

Now I'm totally lost and would appreciate any help anyone has to offer.

---

### Post by faedrake on 2006-11-11
Well, I figured out that I didn't have the universal packages installed. (DUH)

So I tried doing that, but it wouldn't complete the package install through the graphical module assistant. 

I do see a bios message when I boot up saying something about not having a terminating line in PnP.  I guess I'll look into that too.

I'm considering going back to Dapper though...  ](*,) Sound worked under Dapper without nearly as much of a headache.  I had moved to Edgy hoping it would be easier to get 3D acceleration going on my Geforce3 Nvidia card.  I broke the gui trying to get it to work under Dapper.

---

### Post by OwenA on 2006-11-11
I can understand! They make it sound so easy, but it is not even close to being easy. I have been on this ubuntu pc for over 5 hours and not even close to figuring out what is going on. Been reading and on thier IRC channel. 

THey need to have someone rewrite the manuals and do it so it makes sense for those who are having issues. 

On the Forums there are 20 different answers to the same question but in different threads. THey should include a button on the bottom that says did this work..yes or no. If enough people click yes it stays and if No then that post is deleted because it was useless!

---

