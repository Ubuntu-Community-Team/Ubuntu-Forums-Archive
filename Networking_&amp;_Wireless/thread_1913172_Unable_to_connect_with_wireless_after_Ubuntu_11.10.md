---
title: "Unable to connect with wireless after Ubuntu 11.10 upload also affecting W7 install"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by souprgrover on 2012-01-22
I am new to Ubuntu/Linux so will need fairly simple instructions for my problem, but here it goes:

I have a Compal FL92 (bought via Micro Express) which I recently decided to do a clean install on.  I installed my W7 x64 into one partition and left a smaller ~60 gb partition for installing Ubuntu.  I got the W7 installed and working great with one caveat: my blue tooth adapter didn't work on W7, actually it never has and was is not even recognized.  Worked fine in XP. It was not a big deal as i don't own any blue tooth devices.  After I installed W7 I decided to install Ubuntu 11.10 via the wubi installer.  I figured that way if it didn't work properly I could uninstall it easy, although looking back i should have just ran it from a USB or CD instead. So after initial Ubuntu install it rebooted and started some coding (see attachments) and then booted into the desktop.  The first thing I noticed was the blue tooth icon in the top right was there and my blue tooth was working, although would not connect to my phone (phone said unsupported). Then it asked for my wireless passkey which I obliged. Acts like it is connecting, but then just brings up the window asking for the passkey again. This happens about 3 times and it then says "wireless disconnected" and goes away for about 5 minutes and the passkey window comes back up.  Wired connection works fine. 

Well after this happened I rebooted into my W7 partition and first off the blue tooth is recognized right away and the drivers are automatically installed which was new.  The big problem is now my wireless on my windows side will not connect either.  Asks for my password then after 10-15 seconds puts up a error that "cannot connect to the network" and gives troubleshoot options/link none of which has done any good.  Tried uninstalling Ubuntu and using W7 system restore with not change.  

So it seems to me that Ubuntu installed a new firmware on both my blue tooth, my wireless card, or both without asking which has now disrupted my wireless card from working either because of a conflict between the two or incompatibility.  I have included some terminal command outputs that I saw in other threads:

>                                    lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11abgn  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
 

 tracy@ubuntu:~$ lspci | grep -i net  
 04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)  
 0c:00.0 Network controller: Intel Corporation WiFi Link 5100  
 

 iwlagn 0000:0c:00.0: fail to flush all tx fifo queues
 

 [   48.427116] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:  
 [   48.427119] iwlagn: Copyright(c) 2003-2011 Intel Corporation  
 [   48.427233] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [   48.427273] iwlagn 0000:0c:00.0: setting latency timer to 64  
 [   48.427331] iwlagn 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54  
 [   48.452105] iwlagn 0000:0c:00.0: device EEPROM VER=0x11f, CALIB=0x4  
 [   48.452107] iwlagn 0000:0c:00.0: Device SKU: 0Xb  
 [   48.452115] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels  
 [   48.452251] iwlagn 0000:0c:00.0: irq 48 for MSI/MSI-X  
 [   49.765204] iwlagn 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692  
 [  947.452313] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [  958.408343] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [ 2198.388064] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [ 2756.168177] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [ 4409.444091] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [ 7142.312386] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [ 7197.836082] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [ 7682.396128] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [ 9098.104048] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [11558.104050] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [15098.216064] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [15109.168061] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [15322.029783] iwlagn 0000:0c:00.0: PCI INT A disabled  
 [15411.119253] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:  
 [15411.119256] iwlagn: Copyright(c) 2003-2011 Intel Corporation  
 [15411.119369] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [15411.119412] iwlagn 0000:0c:00.0: setting latency timer to 64  
 [15411.119473] iwlagn 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54  
 [15411.144879] iwlagn 0000:0c:00.0: device EEPROM VER=0x11f, CALIB=0x4  
 [15411.144881] iwlagn 0000:0c:00.0: Device SKU: 0Xb  
 [15411.144915] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels  
 [15411.145905] iwlagn 0000:0c:00.0: irq 48 for MSI/MSI-X  
 [15411.149304] iwlagn 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692  
 [15622.404048] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [15642.368300] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [15671.244293] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [16858.376031] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [16878.368095] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [18640.184050] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues  
 [18669.164034] iwlagn 0000:0c:00.0: fail to flush all tx fifo queues
 

 Module                  Size  Used by  
 bnep                   18436  2  
 rfcomm                 47946  8  
 parport_pc             36962  0  
 ppdev                  17113  0  
 lp                     17799  0  
 parport                46562  3 parport_pc,ppdev,lp  
 binfmt_misc            17540  1  
 vesafb                 13809  1  
 arc4                   12529  2  
 snd_hda_codec_si3054    13008  1  
 snd_hda_codec_realtek   330769  1  
 joydev                 17693  0  
 snd_hda_intel          33390  4  
 snd_hda_codec         104802  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep              13668  1 snd_hda_codec  
 snd_pcm                96714  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec  
 snd_seq_midi           13324  0  
 usbhid                 47198  0  
 nvidia               8107305  37  
 hid                    95463  1 usbhid  
 snd_rawmidi            30547  1 snd_seq_midi  
 uvcvideo               72711  0  
 videodev               92992  1 uvcvideo  
 r592                   18144  0  
 v4l2_compat_ioctl32    17083  1 videodev  
 snd_seq_midi_event     14899  1 snd_seq_midi  
 btusb                  18600  2  
 memstick               16569  1 r592  
 compal_laptop          20011  0  
 snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event  
 bluetooth             166112  23 bnep,rfcomm,btusb  
 psmouse                73882  0  
 serio_raw              13166  0  
 snd_timer              29991  2 snd_pcm,snd_seq  
 ir_lirc_codec          12898  0  
 lirc_dev               19204  1 ir_lirc_codec  
 snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq  
 ir_sony_decoder        12549  0  
 iwlagn                314213  0  
 mac80211              462092  1 iwlagn  
 ir_jvc_decoder         12546  0  
 ir_rc6_decoder         12546  0  
 ir_rc5_decoder         12546  0  
 rc_rc6_mce             12502  0  
 ir_nec_decoder         12546  0  
 cfg80211              199587  2 iwlagn,mac80211  
 ene_ir                 22796  0  
 snd                    68266  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 video                  19412  0  
 rc_core                26963  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir 
 wmi                    19256  0  
 soundcore              12680  1 snd  
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm  
 firewire_ohci          40722  0  
 firewire_core          63626  1 firewire_ohci  
 sdhci_pci              14032  0  
 sdhci                  32166  1 sdhci_pci  
 crc_itu_t              12707  1 firewire_core  
 tg3                   147729  0  
 ahci                   26002  1  
 libahci                26861  1 ahci  
 

 0: compal-wifi: Wireless LAN  
     Soft blocked: no  
     Hard blocked: no  
 1: hci0: Bluetooth  
     Soft blocked: no  
     Hard blocked: no  
 2: compal-bluetooth: Bluetooth  
     Soft blocked: no  
     Hard blocked: no  
 3: phy0: Wireless LAN  
     Soft blocked: no  
     Hard blocked: no  
  

Any help for this problem would be greatly appreciated as it is limiting the use of my laptop which I use for work.

thanks in advance.

---

### Post by davethewave83 on 2012-01-22
That's strange that it would have affected your W7 wireless, Linux does not install new firmware to the hardware on it's own. The best I could assume is that you are too far from the router, or the router needs to be reset because something confused it. 

It could be an incompatibility between the type of encryption used, and the type you selected in the OS (WEP/WPA/WPA2) 

you want to make sure you select the same one that is being used in the router as the one you are using in the OS. WPA2 is considered more secure than WEP, If you use WPA2 don't use Enterprise, use personal. 

try cycling the router, unplug it for about 1 minute + and then plug it back in, let it all re-connect and see if the Windows7 Wireless has issues still. 

if it does, check the wireless security and verify it is WPA2, maybe create a new password and then try again. 

Wireless always gives me trouble too. It's a blessing when it behaves.

don't worry about the booting up messages, that's just the boot loader showing that it found your linux kernel and noticed your windows7 installation (skipped it) and is loading. the UUID=6a3cb6af-c28b-4f53-b467-9d9e7ec80763 is the unique identifier for your hard drive which helps the OS distinguish it from other drives that may be present. It's like a finger print sort of for the hard drive.

---

### Post by souprgrover on 2012-01-25
My laptop is all of 12 in from the router so i know its not distance.  I have tried resetting the router and changing all the security settings to no avail. Same with the settings on my wireless adapter.  I still think it has to due something with the blue tooth suddenly activated.  I do know that although the blue tooth is now active I am unable to connect to it on either Ubuntu or W7, at least with my phone.  

Also what does this error mean?  

>  iwlagn 0000:0c:00.0: fail to flush all tx fifo queuesDoes this have something to do with my problem?

---

