---
title: "NOVA-T 500 (dvb_usb_dib0700) Driver Issues - And Nvidia 7800GTX issues"
date: 2009-01-06
forum: Mythbuntu
---

### Post by gneville on 2009-01-06
Hello All,

I have been using a 8500GT graphics card and deceied to upgrade to a nvidia 7800GTX as it was spare. Everytime I put the Nvidia card in it stops the NOVA-T working correctly. I then decied this time to reinstall the dvb_usb_dib0700 drivers using the MythTV Wiki page:

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

However it doesn't work :(

The most I can get is :

[   83.968369] dib0700: loaded with support for 8 different device-types
[   83.968393] usbcore: registered new interface driver dvb_usb_dib0700

I also tried a number of Nvidia drivers just to make sure.

I then took out the card and have now gone back to the original card (8500GT) However to find that again the NOVA-T 500 has stopped working.

So I'm in a bit of a mess, I have tried the method on the Wiki a few times no luck, I have read a few forum with people downloading a .deb for the linux-restricted-modules and taking the firmware file : dvb-usb-dib0700-1.10.fw out of it and placing it in /lib/firmware/<build>

gneville@gneville-mythtv:~$ uname -a
Linux gneville-mythtv 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

These are the current places where 

dvb-usb-dib0700-1.10.fw
or
dvb-usb-dib0700-1.20.fw

Are on the system:


gneville@gneville-mythtv:/lib/firmware/2.6.24-22-generic$ locate dvb-usb-dib0700-1.10.fw
/home/gneville/dvb-usb-dib0700-1.10.fw
/home/gneville/linux/lib/firmware/2.6.24-19-386/dvb-usb-dib0700-1.10.fw
/lib/firmware/dvb-usb-dib0700-1.10.fw
/lib/firmware/2.6.24-22-generic/dvb-usb-dib0700-1.10.fw

gneville@gneville-mythtv:/lib/firmware/2.6.24-22-generic$ locate dvb-usb-dib0700-1.20.fw
/home/gneville/dvb-usb-dib0700-1.20.fw
/lib/firmware/dvb-usb-dib0700-1.20.fw
/lib/firmware/2.6.24-22-generic/dvb-usb-dib0700-1.20.fw


Please can any one help? I Got no TV at the moment :(

Thanks

---

### Post by gneville on 2009-01-06
Oh also I see this in the dmesg output, not sure it its trying to load the wrong things?

[   60.946020] lirc_pvr150: no version for "lirc_unregister_plugin" found: kernel tainted.
[   60.946113] lirc_pvr150: disagrees about version of symbol ivtv_reset_ir_gpio
[   60.946115] lirc_pvr150: Unknown symbol ivtv_reset_ir_gpio

---

### Post by Neon Dusk on 2009-01-06
does 'dmesg | grep dvb-usb' return anything else or lsusb?

---

### Post by Archmage on 2009-01-07
I find this card also a pain in the ...

For me the card only works if I:

shutdown the system completly, wait 10 seconds, start the system, remove delete the turners in MythTV, shutdown the system competly, wait 10 seconds, start the system, add the turners in MythTV, scan for new channels.

If this wont work I have to retry. After the maximum of three retrys it should working.

---

### Post by gneville on 2009-01-07
Hmmm,

I will try this out, but im not sure it will work as I think the problem I have is with the drivers itself rather than within MythTV.

Ubuntu isn't registering the Card and it should show up in dmesg first before MythTV can detect and use it.

---

### Post by gneville on 2009-01-07
> **Neon Dusk said:**
> does 'dmesg | grep dvb-usb' return anything else or lsusb?

Hi Neon Dusk.

gneville@gneville-mythtv:~$ dmesg | grep dvb-usb
gneville@gneville-mythtv:~$

gneville@gneville-mythtv:~$ lsusb
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 045e:0719 Microsoft Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
gneville@gneville-mythtv:~$

Thats All I Get.....Any Idea?

---

### Post by gneville on 2009-01-07
Hmmmm,

Very Odd, I have just installed Mythbuntu 8.10 onto another harddrive which was working in this machine and run that just using the same hardware.

That Too doesn't detect it, 

gneville@gneville-mythtv:~$ dmesg | grep dvb-usb
gneville@gneville-mythtv:~$ lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 04b4:0101 Cypress Semiconductor Corp. Keyboard/Hub
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 045e:0719 Microsoft Corp.
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
gneville@gneville-mythtv:~$
gneville@gneville-mythtv:~$ dmesg | grep dvb


Maybe I've got a problem with the actual card now?

---

### Post by gneville on 2009-01-07
You gotta Love It.

Changed the PCI slot the Card was in and now starts to work! Grrr!

gneville@gneville-mythtv:~$ dmesg | grep dvb-usb
[   35.372531] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   35.539654] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   36.241374] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   36.241413] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   36.964205] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   37.521216] dvb-usb: schedule remote query interval to 50 msecs.
[   37.521221] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
gneville@gneville-mythtv:~$ lsusb
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 002: ID 2040:9950 Hauppauge
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 04b4:0101 Cypress Semiconductor Corp.
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:0719 Microsoft Corp.
Bus 001 Device 001: ID 0000:0000
gneville@gneville-mythtv:~$

---

### Post by gneville on 2009-01-07
Going back to My Main Harddrive now though, its not working on 8.04 :(

gneville@gneville-mythtv:~$ dmesg | grep -i dvb
[   44.632363] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   44.688102] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   45.389797] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   45.389826] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   45.390191] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   45.499281] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   46.039793] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   46.039986] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   46.045160] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   46.533373] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb3/3-1/input/input7
[   46.565751] dvb-usb: schedule remote query interval to 50 msecs.
[   46.565756] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   46.565953] usbcore: registered new interface driver dvb_usb_dib0700
[   71.459961] Modules linked in: powernow_k8 cpufreq_userspace cpufreq_powersave cpufreq_conservative cpufreq_ondemand cpufreq_stats freq_table video output sbs sbshc container dock battery ipv6 iptable_filter ip_tables x_tables nls_cp437 cifs ac parport_pc lp parport uinput mt2060 af_packet dvb_usb_dib0700 dib7000p dib7000m dvb_usb dvb_core nvidia(P) dib3000mc dibx000_common dib0070 joydev agpgart snd_hda_intel i2c_core snd_pcm_oss snd_mixer_oss wmi_acer snd_pcm snd_page_alloc snd_hwdep snd_seq_dummy psmouse serio_raw snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device button shpchp snd k8temp pci_hotplug soundcore evdev pcspkr ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_amd ide_disk pata_acpi ahci usbhid hid ata_generic floppy libata forcedeth uhci_hcd hpt366 ide_core scsi_mod ohci_hcd ehci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   71.460004] EIP is at dvb_frontend_open+0x67/0x240 [dvb_core]
[   71.460032]  [<f8b906c9>] dvb_device_open+0xc9/0x150 [dvb_core]
[   71.460040]  [<f8b90600>] dvb_device_open+0x0/0x150 [dvb_core]
[   71.460105] EIP: [<f8b96977>] dvb_frontend_open+0x67/0x240 [dvb_core] SS:ESP 0068:f7261e98


It finds it, but can't use the card.

root@gneville-mythtv:/home/gneville# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > /root/.tzap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy



gneville@gneville-mythtv:~$ tail -50 /var/log/mythtv/mythbackend.log
2009-01-07 20:15:57.033 DVBChan(1:0) Error: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2009-01-07 20:15:57.039 New DB connection, total: 3
2009-01-07 20:15:57.040 Connected to database 'mythconverg' at host: localhost
2009-01-07 20:15:57.042 mythbackend: Problem with capture cards: Card 1failed init
2009-01-07 20:15:57.046 DVBChan(3:1) Error: Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2009-01-07 20:15:57.058 mythbackend: Problem with capture cards: Card 3failed init

---

### Post by gneville on 2009-01-07
No process seems to be using the card either:

root@gneville-mythtv:/home/gneville#
root@gneville-mythtv:/home/gneville# lsof /dev/dvb/adapter0/frontend0
root@gneville-mythtv:/home/gneville#

---

### Post by Neon Dusk on 2009-01-07
> **gneville said:**
> 

...
It finds it, but can't use the card.

root@gneville-mythtv:/home/gneville# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > /root/.tzap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy
...

Is the mythbackend stopped when you try the scan? (sudo /etc/init.d/mythtv-backend stop)

---

### Post by gneville on 2009-01-08
Managed to fix it by again reinstalling v4l-dvb and downloading the firmware again!

I have not got it working with the 7800GTX card YAY!

---

