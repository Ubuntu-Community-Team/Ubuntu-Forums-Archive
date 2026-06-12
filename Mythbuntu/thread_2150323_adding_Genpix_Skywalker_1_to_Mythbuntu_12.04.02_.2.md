---
title: "adding Genpix Skywalker 1 to Mythbuntu 12.04.02 .26 not working"
date: 2013-05-31
forum: Mythbuntu
---

### Post by bhcv on 2013-05-31
I have mythbuntu 12.04.02 .26 working fine with HDhomeRun usb dual tuner. I tried adding a Genpix skywalker 1 to it and I would loose the ability to use my mouse and keyboard. Rebooting with the Skywalker unplugged fixes the mouse and keyboard. The Skywalker is fully functional running under DVB Dream on Windows 7. It took me 2 weeks to get the HDhomeRun working because I'm not familiar with linux at all. Instead of chancing ruining what I have, I got another hard drive and started from scratch ignoring the HDHomeruns. [COLOR=#000000][FONT=Verdana]My components are as follows:[/FONT][/COLOR]
[FONT=Verdana][SIZE=2][COLOR=#000000]BioStar TA785GE 128M Ver. 6.1 board with a AMD 955 Phenom II 3.2 4 core processor, 4 gig ddr2, 1.5 tb WD150earx. and a EVGA Geforce 9800 GTX+. The software updater says everything is up to date. After much research I saw somewhere that there may be a problem with AMD 7000 series usb chips, so I added a PCI usb card which has given me no more lockups.  After a fresh reboot "DMSEG" command towards the end shows my Skywalker initialized.[/COLOR][/SIZE][/FONT]
[FONT=arial]
16.556817] gp8psk: FPGA Version = 1[/FONT]
[FONT=arial]16.557166] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.[/FONT]
[FONT=arial]16.557385] DVB: registering new adapter (Genpix SkyWalker-1 DVB-S receiver)[/FONT]
[FONT=arial]16.558522] DVB: registering adapter 0 frontend 0 (Genpix DVB-S)...[/FONT]
[FONT=arial]16.560280] dvb-usb: Genpix SkyWalker-1 DVB-S receiver successfully initialized and connected.[/FONT]
[FONT=arial]16.560282] gp8psk: found Genpix USB device pID = 203 (hex)[/FONT]
[FONT=arial]16.560309] usbcore: registered new interface driver dvb_usb_gp8psk[/FONT]
[FONT=arial]16.595623] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory[/FONT]
[FONT=arial]16.595754] NFSD: starting 90-second grace period[/FONT]
[FONT=arial]16.616253] init: udev-fallback-graphics main process (1072) terminated with status 1[/FONT]
[FONT=arial]18.643741] r8169 0000:02:00.0: eth0: link up[/FONT]
[FONT=arial]18.644056] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready[/FONT]
[FONT=arial]18.679687] NVRM: GPU at 0000:01:00: GPU-bf2ea96b-b282-a697-3ef0-1c5d606aa0f0[/FONT]
[FONT=arial]22.789774] init: mythtv-backend main process (1748) terminated with status 1[/FONT]
[FONT=arial]22.789795] init: mythtv-backend main process ended, respawning[/FONT]
[FONT=arial]23.900156] init: mythtv-backend main process (2147) terminated with status 1[/FONT]
[FONT=arial]23.900178] init: mythtv-backend main process ended, respawning[/FONT]
[FONT=arial]24.044031] init: mythtv-backend main process (2367) terminated with status 1[/FONT]
[FONT=arial]24.044049] init: mythtv-backend respawning too fast, stopped[/FONT]
[FONT=arial]24.572925] audit_printk_skb: 48 callbacks suppressed[/FONT]
[FONT=arial]24.572929] type=1400 audit(1370025434.846:28): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=963 comm="cupsd" pid=963 comm="cupsd" capability=36  capname="block_suspend"
[/FONT]
[FONT=arial]bruce@MythBuntu1:~$ 

I'm not sure what the last line is referring to but I thought it my have something to do with "permissions", so I entered the following:
bruce@MythBuntu1:~$ sudo -s mythtv-setup
[sudo] password for bruce: 

My DVB card doesn't show up under capture devices. I can edit the location, but saw somewhere that it should propagate on it's own. 
Running DMSEG again shows the following lines added to the last entry from above

24.572929] type=1400 audit(1370025434.846:28): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=963 comm="cupsd" pid=963 comm="cupsd" capability=36  capname="block_suspend"


[  325.410271] type=1400 audit(1370025735.945:29): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=963 comm="cupsd" pid=963 comm="cupsd" capability=36  capname="block_suspend"
[  405.174401] gp8psk: FW Version = 2.13.1 (0x20d01)  Build 2010/03/12
[  405.175294] gp8psk: FPGA Version = 1
[  406.243895] gp8psk: FW Version = 2.13.1 (0x20d01)  Build 2010/03/12
[  406.244788] gp8psk: FPGA Version = 1
[  407.323862] gp8psk: FW Version = 2.13.1 (0x20d01)  Build 2010/03/12
[  407.324726] gp8psk: FPGA Version = 1
[  408.393231] gp8psk: FW Version = 2.13.1 (0x20d01)  Build 2010/03/12
[  408.394125] gp8psk: FPGA Version = 1
[  436.216439] gp8psk: FW Version = 2.13.1 (0x20d01)  Build 2010/03/12
[  436.217337] gp8psk: FPGA Version = 1
[  438.215354] gp8psk: usb in 137 operation failed.
[  440.209139] gp8psk: usb out operation failed.
[  442.202930] gp8psk: usb in 138 operation failed.
bruce@MythBuntu1:~$ 


[/FONT]
.
If anybody has any suggestions how to get this working I would really appreciated it

---

### Post by nickrout on 2013-06-01
I wasn't aware that HD Homerun came in a USB version??

What gave you the idea that the genpix worked in linux? Or with mythtv?

---

