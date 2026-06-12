---
title: "Sound stopped working"
date: 2009-04-10
forum: Multimedia Software
---

### Post by tneva82 on 2009-04-10
Yesterday worked fine, today booted up and volume control has red X and no sound comes. Trying to open volume control gives me No volume control GStreamer plugins and/or devices found. What's up with this?

Didn't do anything for sounds yesterday. Only thing I did was installing whole bunch of security updates via Ubuntu's update tool. Could that have disabled it? If so how I could restore sound back?

---

### Post by utnubuuser on 2009-04-10
Hi - have you tried > sudo apt-get install --reinstall gstreamer

---

### Post by tneva82 on 2009-04-11
> **utnubuuser said:**
> Hi - have you tried

E: Couldn't find package gstreamer

Didn't work :(

I now used synaptic packet manager to find everything related to gstreamer and reinstalled all of them that were there. No change :(

---

### Post by stephen2365 on 2009-04-11
Same problem same result
User:~$ sudo apt-get install --reinstall gstreamer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer

HELP!!!!

---

### Post by wheezer on 2009-04-11
I am using 8.10 with a what I thought was a realtek basic sound card.

My sound will work fine after a reboot, but after a day or so, mysteriously just stops, system wide. I have no idea how to debug this. I get no visual indication that anything is wrong, except that audo speak symbol on Totem will be greyed out. 

What to do?

---

### Post by tneva82 on 2009-04-16
Nobody has any ideas? Rather annoying thing. Sound works fine on Windows but not on Ubuntu so atleast sound card is working.

Help!

---

### Post by wheezer on 2009-04-16
> **tneva82 said:**
> Nobody has any ideas? Rather annoying thing. Sound works fine on Windows but not on Ubuntu so atleast sound card is working.

Help!

Yeah, I was hoping for more response, myself. It's still doing it, even after reinstalling all the gstreamers.  Is there other stuff I might reinstall?

---

### Post by Daisuke_Aramaki on 2009-04-16
Try to setup alsamixer and call alsamixer from the command line and try to control the volume and see if it helps. If there is a systemwide sound failure, and some kernel updates were done, it could also be likely something messed with loading your sound module. Check alsamixer first, and then after boot, call dmesg in the command line and go through the boot log and see if snd_hda intel or something like that is loaded.

---

### Post by tneva82 on 2009-04-16
> **Daisuke_Aramaki said:**
> Try to setup alsamixer and call alsamixer from the command line and try to control the volume and see if it helps. If there is a systemwide sound failure, and some kernel updates were done, it could also be likely something messed with loading your sound module. Check alsamixer first, and then after boot, call dmesg in the command line and go through the boot log and see if snd_hda intel or something like that is loaded.

Not sure mixer helps. I tried aplay -l and it claims theres no sound card installed...Where that went? It did work long time and it works in windows.

Then I tried sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils (and reinstalling those) but didn't help either.

Bugger.

---

### Post by Daisuke_Aramaki on 2009-04-16
> **tneva82 said:**
> Not sure mixer helps. I tried aplay -l and it claims theres no sound card installed...Where that went? It did work long time and it works in windows.

Then I tried sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils (and reinstalling those) but didn't help either.

Bugger.

what did your dmesg say? Are you sure your sound module is being loaded at boot?

---

### Post by markbuntu on 2009-04-16
This problem is an ongoing bug in the snd-hda-intel alsa driver. If this happens to you you can reload alsa and pulseaudio and avoid having to reboot

```

killall pulseaudio

sudo alsa force-reload

pulseaudio -D

```

This is a temporary workaroumd. A more permanent fix can only come from driver/kernel updates.

---

### Post by Macintosh SE on 2009-04-16
If this is an update problem, you could just go into Synaptic and go to 'History' under the File menu. Find all the packages installed around the time you updated. Search them individually. When you find each one, select it and go to Package > Force Version. Set it to be the older version. Do this with EACH updated package. This is a crude workaround but should fix your problem if updates were the cause. I had to do this about a year ago to fix a similarly mysterious and sudden malfunction of my SETI@home BOINC program.

Also be aware that if you do this, the Update Manager is going to start bugging you to update the packages you just downgraded. If you downgrade all the updates and it fixes your problem, you should find each package that you downgraded and go to Package > Lock Version. This will prevent them from being updated in the future.

---

### Post by tneva82 on 2009-04-16
> **Daisuke_Aramaki said:**
>  and then after boot, call dmesg in the command line and go through the boot log and see if snd_hda intel or something like that is loaded.

a) alsamixer says no mixer elems found.

b) among dmesg following was printed. Guess something is messed up with sound card :-/

```
[   11.214688] phy0: hwaddr 00:1a:9f:91:bd:96, RTL8185vD + rtl8225z2                                                                                                               
[   11.381449] snd_hda_intel: disagrees about version of symbol snd_ctl_add_slave                                                                                                  
[   11.381452] snd_hda_intel: Unknown symbol snd_ctl_add_slave                                                                                                                     
[   11.381570] snd_hda_intel: disagrees about version of symbol snd_ctl_add                                                                                                        
[   11.381571] snd_hda_intel: Unknown symbol snd_ctl_add                                                                                                                           
[   11.381681] snd_hda_intel: disagrees about version of symbol snd_pcm_new                                                                                                        
[   11.381682] snd_hda_intel: Unknown symbol snd_pcm_new                                                                                                                           
[   11.381767] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates                                                                                             
[   11.381769] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates                                                                                                                
[   11.381867] snd_hda_intel: disagrees about version of symbol snd_card_register                                                                                                  
[   11.381869] snd_hda_intel: Unknown symbol snd_card_register                                                                                                                     
[   11.381933] snd_hda_intel: disagrees about version of symbol snd_card_free                                                                                                      
[   11.381935] snd_hda_intel: Unknown symbol snd_card_free                                                                                                                         
[   11.381998] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all                                                                              
[   11.382000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all                                                                                                 
[   11.382066] snd_hda_intel: disagrees about version of symbol snd_card_proc_new                                                                                                  
[   11.382067] snd_hda_intel: Unknown symbol snd_card_proc_new                                                                                                                     
[   11.382296] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id                                                                                                    
[   11.382298] snd_hda_intel: Unknown symbol snd_ctl_find_id                                                                                                                       
[   11.382360] snd_hda_intel: disagrees about version of symbol snd_pcm_set_sync                                                                                                   
[   11.382361] snd_hda_intel: Unknown symbol snd_pcm_set_sync                                                                                                                      
[   11.382522] snd_hda_intel: disagrees about version of symbol snd_ctl_new1                                                                                                       
[   11.382523] snd_hda_intel: Unknown symbol snd_ctl_new1                                                                                                                          
[   11.382688] snd_hda_intel: disagrees about version of symbol snd_component_add                                                                                                  
[   11.382689] snd_hda_intel: Unknown symbol snd_component_add                                                                                                                     
[   11.382758] snd_hda_intel: disagrees about version of symbol snd_ctl_make_virtual_master                                                                                        
[   11.382760] snd_hda_intel: Unknown symbol snd_ctl_make_virtual_master                                                                                                           
[   11.382967] snd_hda_intel: disagrees about version of symbol snd_card_new                                                                                                       
[   11.382969] snd_hda_intel: Unknown symbol snd_card_new                                                                                                                          
[   11.383104] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages                                                                                           
[   11.383106] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages                                                                                                              
[   11.383170] snd_hda_intel: disagrees about version of symbol snd_ctl_boolean_mono_info                                                                                          
[   11.383172] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info                                                                                                             
[   11.383260] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl                                                                                                  
[   11.383262] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl                                                                                                                     
[   11.383331] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages                                                                                             
[   11.383333] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages                                                                                                                
[   11.383436] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops                                                                                                    
[   11.383437] snd_hda_intel: Unknown symbol snd_pcm_set_ops                                                                                                                       
[   11.383516] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list                                                                                         
[   11.383518] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list                                                                                                            
[   11.383633] snd_hda_intel: disagrees about version of symbol snd_device_new                                                                                                     
[   11.383634] snd_hda_intel: Unknown symbol snd_device_new                                                                                                                        
[   11.383696] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_ops_page                                                                                             
[   11.383698] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page                                                                                                                
[   11.383797] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all                                                                                                
[   11.383799] snd_hda_intel: Unknown symbol snd_pcm_suspend_all                                                                                                                   
[   11.383896] snd_hda_intel: disagrees about version of symbol snd_card_disconnect                                                                                                
[   11.383898] snd_hda_intel: Unknown symbol snd_card_disconnect                                                                                                                   
[   11.383960] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer                                                                                      
[   11.383961] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer                                                                                                         
[   11.384340] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed                                                                                             
[   11.384342] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed                                                                                                                
[   11.384403] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step                                                                                         
[   11.384404] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step                                                                                                            
[   11.538169] snd_hda_intel: disagrees about version of symbol snd_ctl_add_slave                                                                                                  
[   11.538172] snd_hda_intel: Unknown symbol snd_ctl_add_slave                                                                                                                     
[   11.538291] snd_hda_intel: disagrees about version of symbol snd_ctl_add                                                                                                        
[   11.538293] snd_hda_intel: Unknown symbol snd_ctl_add                                                                                                                           
[   11.538403] snd_hda_intel: disagrees about version of symbol snd_pcm_new                                                                                                        
[   11.538405] snd_hda_intel: Unknown symbol snd_pcm_new                                                                                                                           
[   11.538490] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates                                                                                             
[   11.538492] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates                                                                                                                
[   11.538564] snd_hda_intel: disagrees about version of symbol snd_card_register                                                                                                  
[   11.538565] snd_hda_intel: Unknown symbol snd_card_register                                                                                                                     
[   11.538630] snd_hda_intel: disagrees about version of symbol snd_card_free                                                                                                      
[   11.538632] snd_hda_intel: Unknown symbol snd_card_free                                                                                                                         
[   11.538696] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all                                                                              
[   11.538698] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all                                                                                                 
[   11.538763] snd_hda_intel: disagrees about version of symbol snd_card_proc_new                                                                                                  
[   11.538765] snd_hda_intel: Unknown symbol snd_card_proc_new                                                                                                                     
[   11.538993] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id                                                                                                    
[   11.538995] snd_hda_intel: Unknown symbol snd_ctl_find_id                                                                                                                       
[   11.539058] snd_hda_intel: disagrees about version of symbol snd_pcm_set_sync                                                                                                   
[   11.539060] snd_hda_intel: Unknown symbol snd_pcm_set_sync                                                                                                                      
[   11.539220] snd_hda_intel: disagrees about version of symbol snd_ctl_new1                                                                                                       
[   11.539221] snd_hda_intel: Unknown symbol snd_ctl_new1                                                                                                                          
[   11.539385] snd_hda_intel: disagrees about version of symbol snd_component_add                                                                                                  
[   11.539387] snd_hda_intel: Unknown symbol snd_component_add                                                                                                                     
[   11.539456] snd_hda_intel: disagrees about version of symbol snd_ctl_make_virtual_master                                                                                        
[   11.539458] snd_hda_intel: Unknown symbol snd_ctl_make_virtual_master                                                                                                           
[   11.539542] snd_hda_intel: disagrees about version of symbol snd_card_new                                                                                                       
[   11.539543] snd_hda_intel: Unknown symbol snd_card_new                                                                                                                          
[   11.539679] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages                                                                                           
[   11.539681] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages                                                                                                              
[   11.539746] snd_hda_intel: disagrees about version of symbol snd_ctl_boolean_mono_info                                                                                          
[   11.539748] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info                                                                                                             
[   11.539836] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl                                                                                                  
[   11.539838] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl                                                                                                                     
[   11.539908] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages                                                                                             
[   11.539910] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages                                                                                                                
[   11.540013] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops                                                                                                    
[   11.540014] snd_hda_intel: Unknown symbol snd_pcm_set_ops                                                                                                                       
[   11.540094] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list                                                                                         
[   11.540095] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list                                                                                                            
[   11.540211] snd_hda_intel: disagrees about version of symbol snd_device_new                                                                                                     
[   11.540212] snd_hda_intel: Unknown symbol snd_device_new                                                                                                                        
[   11.540274] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_ops_page                                                                                             
[   11.540276] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page                                                                                                                
[   11.540376] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all                                                                                                
[   11.540377] snd_hda_intel: Unknown symbol snd_pcm_suspend_all                                                                                                                   
[   11.540475] snd_hda_intel: disagrees about version of symbol snd_card_disconnect                                                                                                
[   11.540477] snd_hda_intel: Unknown symbol snd_card_disconnect                                                                                                                   
[   11.540539] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer                                                                                      
[   11.540541] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer                                                                                                         
[   11.540889] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed                                                                                             
[   11.540891] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed                                                                                                                
[   11.540952] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step                                                                                         
[   11.540954] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
```

---

### Post by tneva82 on 2009-04-16
> **markbuntu said:**
> This problem is an ongoing bug in the snd-hda-intel alsa driver. If this happens to you you can reload alsa and pulseaudio and avoid having to reboot

```

killall pulseaudio

sudo alsa force-reload

pulseaudio -D

```

This is a temporary workaroumd. A more permanent fix can only come from driver/kernel updates.

The sudo alsa force-reload gave following errors:
```

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tnevalainen/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tnevalainen/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-pcm-oss snd-mixer-oss snd-seq-device snd-pcm snd-timer snd-page-alloc.
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-pcm-oss snd-mixer-oss snd-seq-device snd-pcm snd-timer snd-page-alloc.

```

---

