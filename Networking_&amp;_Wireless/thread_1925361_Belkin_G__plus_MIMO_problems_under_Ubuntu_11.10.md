---
title: "Belkin G  plus MIMO problems under Ubuntu 11.10"
date: 2012-02-14
forum: Networking &amp; Wireless
---

### Post by glubbler on 2012-02-14
I'm trying to connect to my WPA2 network using an external Belkin G  plus MIMO (ver. Nr. 4000) under Ubuntu 11.10. I'm hot having an any luck. The device seems to crash either immediately upon bootup or after approx. 30 seconds of holding the connection. The same device works falwlessly under Windows 7 on the same computer. Does anyone know a solution?

The following might be useful information:

> 

iwconfig
lo        
no wireless extensions.

eth0      
no wireless extensions.

iwlist wlan0 scan
wlan0     
Interface doesn't support scanning.


lsusb
Bus
001 Device 001: ID 1d6b:0002 Linux Foundation 
2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 
2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 
1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 
1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 
1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 
1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 
1.1 root hub
Bus 001 Device 005: ID 046d:0991 Logitech, Inc. QuickCam Pro for Notebooks
Bus 
003 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)
Bus 003 Device 
003: ID 03f0:2611 Hewlett-Packard OfficeJet 7100 series
Bus 002 Device 
002: ID 1bcf:0c31 Sunplus Innovation Technology Inc. 

ls mod
ls: 
lsmod
Module                  
Size  Used by
nls_utf8               
12493  1 
isofs                  
39549  1 
usb_storage            
44173  1 
uas                    
17699  0 
uvcvideo               
67271  0 
snd_usb_audio         
100880  0 
videodev               
85626  1 uvcvideo
snd_usbmidi_lib        
24558  1 snd_usb_audio
usbhid                 
41905  0 
hid                    
77367  1 usbhid
arc4                   
12473  0 
rt73usb                
27029  0 
crc_itu_t              
12627  1 rt73usb
rt2x00usb              
20092  1 rt73usb
rt2x00lib              
48114  2 rt73usb,rt2x00usb
mac80211              
272785  2 rt2x00usb,rt2x00lib
cfg80211              
172392  2 rt2x00lib,mac80211
rfcomm                 
38408  0 
bnep                   
17923  2 
bluetooth             
148839  10 rfcomm,bnep
parport_pc             
32114  0 
ppdev                  
12849  0 
vesafb                 
13489  1 
binfmt_misc            
17292  1 
snd_hda_codec_hdmi     
31426  4 
nvidia              
10390874  30 
snd_hda_codec_realtek   
254125  1 
snd_hda_intel          
24262  3 
snd_hda_codec          
91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              
13276  2 snd_usb_audio,snd_hda_codec
snd_seq_midi           
13132  0 
snd_rawmidi            
25241  2 snd_usbmidi_lib,snd_seq_midi
snd_pcm                
80468  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     
14475  1 snd_seq_midi
snd_seq                
51567  2 snd_seq_midi,snd_seq_midi_event
k10temp                
12990  0 
snd_timer              
28932  2 snd_pcm,snd_seq
snd_seq_device         
14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    
18744  0 
sp5100_tco             
13495  0 
snd                    
55902  18 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
i2c_piix4              
13093  0 
soundcore              
12600  1 snd
snd_page_alloc         
14115  2 snd_hda_intel,snd_pcm
ati_agp                
13242  0 
lp                     
17455  0 
parport                
40930  3 parport_pc,ppdev,lp
floppy                 
60310  0 
pata_atiixp            
12967  0 
ahci                   
21634  3 
libahci                
25727  1 ahci
r8169                  
43104  0 



---

