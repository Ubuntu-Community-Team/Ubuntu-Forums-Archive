---
title: "kdeTV issue on 9.10"
date: 2010-03-08
forum: Multimedia Software
---

### Post by axicos on 2010-03-08
Hello,

I have a problem with kdetv, which in the GUI - Video menu says: No devices found. I searched, read and still can't get the thing to work.

NOTE: tvtime and XawTV work properly. (no remote)

So a little info:

- the system is a fresh install of Kubuntu 9.10
- tv-tuner: Leadtek Winfast 2000XP Expert
- outputs:

cat /etc/issue
Ubuntu 9.10

cat /proc/version                                                      
Linux version 2.6.31-20-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010

kdetv --version
Qt: 3.3.8b
KDE: 3.5.10
kdetv: 0.8.9

- dmesg attached
- lsmod attached

- running kdetv with:
kdetv --sync                                                                               
kbuildsycoca running...                                                                                    
DCOP Cleaning up dead connections.                                                                         
Creating vbi proxy client, rev.                                                                            
$Id: proxy-client.c,v 1.18 2008/02/19 00:35:21 mschimek Exp $                                              
proxy_msg: connect: error 2, No such file or directory                                                     
Try to open V4L2 0.20 VBI device, libzvbi interface rev.                                                   
  $Id: io-v4l2.c,v 1.37 2008/02/19 00:35:20 mschimek Exp $                                                 
Opened /dev/vbi0                                                                                           
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: Try to open V4L2 2.6 VBI device, libzvbi interface rev.            
  $Id: io-v4l2k.c,v 1.49 2008/02/19 00:35:20 mschimek Exp $.                                               
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: Opened /dev/vbi0.                                                  
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: /dev/vbi0 (Leadtek Winfast 2000XP Expert) is a v4l2 vbi device,    
driver cx8800, version 0x00000007.                                                                         
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: Using streaming interface.                                         
libzvbi:io-v4l2k:v4l2_get_videostd: Current scanning system is 525.                                        
libzvbi:io-v4l2k:v4l2_update_services: Querying current vbi parameters...                                  
libzvbi:io-v4l2k:v4l2_update_services: ...success.                                                         
libzvbi:print_vfmt: VBI capture parameters supported:                                                      
libzvbi:print_vfmt: VBI capture parameters granted:                                                        
libzvbi:raw_decoder:vbi3_raw_decoder_add_services: No services to add.                                     
libzvbi:io-v4l2k:v4l2_update_services: Nyquist check passed.                                               
libzvbi:io-v4l2k:v4l2_update_services: Request decoding of services 0x60000c7f, strict level -1.           
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000001 (Teletext System B 625 Level 1.5) requires videostd_set 0x1, have 0x0.
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000003 (Teletext System B, 625) requires videostd_set 0x1, have 0x0.         
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000001 (Teletext System B 625 Level 1.5) requires videostd_set 0x1, have 0x0.
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000003 (Teletext System B, 625) requires videostd_set 0x1, have 0x0.         
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000004 (Video Program System) requires videostd_set 0x1, have 0x0.           
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000400 (Wide Screen Signalling 625) requires videostd_set 0x1, have 0x0.     
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000008 (Closed Caption 625, field 1) requires videostd_set 0x1, have 0x0.    
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000010 (Closed Caption 625, field 2) requires videostd_set 0x1, have 0x0.    
libzvbi:io-v4l2k:v4l2_update_services: Will capture services 0x00000060, added 0x60 commit=1.                                                   
libzvbi:io-v4l2k:v4l2_stream_alloc: Requesting 16 streaming i/o buffers.                                                                        
libzvbi:io-v4l2k:v4l2_stream_alloc: Mapping 16 streaming i/o buffers.                                                                           
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: Successfully opened /dev/vbi0 (Leadtek Winfast 2000XP Expert).   

ISN'T a real success for me...  :'(


On a related issue, i also can't get the remote to function properly.

Information on this:
- remote info: Winfast Y0400052
- evtest result attached
- dmesg and lsmod already mentioned 
- lirc-hardware.conf attached. Note that the event number does not change so at this time i have not set an explicit device.

So..... Any ideas? Does anyone use kdeTV  ;D

I even tried MythTV, but i can't scan for channels and only managed to manually input a channel (set freq manually), but that is not a workable solution. However that is another story, beside the point of this thread.

Thanks in advance!

---

### Post by axicos on 2010-03-08
No one? O gods of ubuntu and kdeTV reveal yourselves!

[-o<

---

