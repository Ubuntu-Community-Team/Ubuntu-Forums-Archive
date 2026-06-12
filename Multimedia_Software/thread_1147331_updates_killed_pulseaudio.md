---
title: "updates killed pulseaudio"
date: 2009-05-03
forum: Multimedia Software
---

### Post by element_G on 2009-05-03
Hi, I know there are a lot of threads on pulseaudio and this may have been asked before, apologies if this is the case ;)

I use pulseaudio for sound, but it doesn't recognize the digital out of my card which goes to my surround system. I have to use a workaround and have this line:
```
load-module module-alsa-sink device=hw:0,1
``` at the bottom of my /etc/pulse/default.pa file. This has allowed me to see the device in pavucontrol until I updated last night. Now pulse audio fails to start :(

Output of pulseaudio -vvv: 
```
~$ pulseaudio -vvv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.                         
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes          
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted 
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted 
I: core-util.c: Successfully gained nice level -11.                         
D: main.c: Can realtime: yes, can high-priority: yes                        
I: main.c: Giving up CAP_NICE                                               
D: main.c: Can realtime: no, can high-priority: no                          
I: main.c: This is PulseAudio 0.9.14                                        
D: main.c: Compilation host: i486-pc-linux-gnu                              
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math                                                       
D: main.c: Running on host: Linux i686 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009                                                                                         
I: main.c: Page size is 4096 bytes                                                                                                                                                           
D: main.c: Compiled with Valgrind support: no                                                                                                                                                
D: main.c: Running in valgrind mode: no                                                                                                                                                      
D: main.c: Optimized build: yes                                                                                                                                                              
I: main.c: Machine ID is df88421d389037b0518ec4e449bbd813.                                                                                                                                   
I: main.c: Using runtime directory /home/gary/.pulse/df88421d389037b0518ec4e449bbd813:runtime.                                                                                               
I: main.c: Using state directory /home/gary/.pulse.                                                                                                                                          
I: main.c: Running in system mode: no                                                                                                                                                        
I: main.c: Fresh high-resolution timers available! Bon appetit!                                                                                                                              
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496                                                     
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success                                                                                            
I: module.c: Loaded "module-gconf" (index: #0; argument: "").                                                                                                                                
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").                                                                                                                      
I: module-device-restore.c: Sucessfully opened database file '/home/gary/.pulse/df88421d389037b0518ec4e449bbd813:device-volumes.i486-pc-linux-gnu.gdbm'.                                     
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").                                                                                                                       
I: module-stream-restore.c: Sucessfully opened database file '/home/gary/.pulse/df88421d389037b0518ec4e449bbd813:stream-volumes.i486-pc-linux-gnu.gdbm'.                                     
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").                                                                                                                       
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success                                                                                       
I: module-hal-detect.c: Trying capability alsa                                                                                                                                               
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1412_1724_sound_card_0_alsa_control__1                                                                            
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1412_1724_sound_card_0_alsa_capture_0 tsched=0'                                    
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...                                                                                                                               
W: alsa-util.c: Device front:0 doesn't support sample format s16le, changed to s32le.                                                                                                        
I: module-alsa-source.c: Successfully opened device front:0.                                                                                                                                 
I: module-alsa-source.c: Successfully enabled mmap() mode.                                                                                                                                   
I: (alsa-lib)control.c: Invalid CTL front:0                                                                                                                                                  
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory                                                                                                                 
I: alsa-util.c: Successfully attached to mixer 'hw:0'                                                                                                                                        
I: alsa-util.c: Cannot find mixer control "Capture" or mixer control is no combination of switch/volume.                                                                                     
W: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.                                                                                
I: module-device-restore.c: Restoring volume for source alsa_input.pci_1412_1724_sound_card_0_alsa_capture_0.                                                                                
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_1412_1724_sound_card_0_alsa_capture_0.                                                                            
I: source.c: Created source 0 "alsa_input.pci_1412_1724_sound_card_0_alsa_capture_0" with sample spec s32le 2ch 44100Hz and channel map front-left,front-right                               
I: module-alsa-source.c: Using 8 fragments of size 3520 bytes, buffer time is 79.82ms                                                                                                        
D: module-alsa-source.c: hwbuf_unused=0                                                                                                                                                      
D: module-alsa-source.c: setting avail_min=1                                                                                                                                                 
D: alsa-util.c: snd_pcm_dump():                                                                                                                                                              
D: alsa-util.c: Hardware PCM card 0 'M Audio Revolution-5.1' device 0 subdevice 0                                                                                                            
D: alsa-util.c: Its setup is:                                                                                                                                                                
D: alsa-util.c:   stream       : CAPTURE                                                                                                                                                     
D: alsa-util.c:   access       : MMAP_INTERLEAVED                                                                                                                                            
D: alsa-util.c:   format       : S32_LE                                                                                                                                                      
D: alsa-util.c:   subformat    : STD                                                                                                                                                         
D: alsa-util.c:   channels     : 2                                                                                                                                                           
D: alsa-util.c:   rate         : 44100                                                                                                                                                       
D: alsa-util.c:   exact rate   : 44100 (44100/1)                                                                                                                                             
D: alsa-util.c:   msbits       : 24                                                                                                                                                          
D: alsa-util.c:   buffer_size  : 3520                                                                                                                                                        
D: alsa-util.c:   period_size  : 440                                                                                                                                                         
D: alsa-util.c:   period_time  : 9977                                                                                                                                                        
D: alsa-util.c:   tstamp_mode  : ENABLE                                                                                                                                                      
D: alsa-util.c:   period_step  : 1                                                                                                                                                           
D: alsa-util.c:   avail_min    : 440                                                                                                                                                         
D: alsa-util.c:   period_event : 0                                                                                                                                                           
D: alsa-util.c:   start_threshold  : -1                                                                                                                                                      
D: alsa-util.c:   stop_threshold   : 1845493760                                                                                                                                              
D: alsa-util.c:   silence_threshold: 0                                                                                                                                                       
D: alsa-util.c:   silence_size : 0                                                                                                                                                           
D: alsa-util.c:   boundary     : 1845493760                                                                                                                                                  
D: module-alsa-source.c: Thread starting up                                                                                                                                                  
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29                                                                                                                                      
D: module-suspend-on-idle.c: Source alsa_input.pci_1412_1724_sound_card_0_alsa_capture_0 becomes idle.                                                                                       
I: module.c: Loaded "module-alsa-source" (index: #4; argument: "device_id=0 source_name=alsa_input.pci_1412_1724_sound_card_0_alsa_capture_0 tsched=0").                                     
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1412_1724_sound_card_0_alsa_playback_2                                                                            
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0 tsched=0'                                      
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...                                                                                                                               
W: alsa-util.c: Device front:0 doesn't support sample format s16le, changed to s32le.                                                                                                        
I: module-alsa-sink.c: Successfully opened device front:0.                                                                                                                                   
I: module-alsa-sink.c: Successfully enabled mmap() mode.                                                                                                                                     
I: (alsa-lib)control.c: Invalid CTL front:0                                                                                                                                                  
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory                                                                                                                 
I: alsa-util.c: Successfully attached to mixer 'hw:0'                                                                                                                                        
I: alsa-util.c: Cannot find mixer control "Master" or mixer control is no combination of switch/volume.                                                                                      
W: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.                                                                                
I: alsa-util.c: Using mixer control "PCM".                                                                                                                                                   
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0.                                                                                
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0.                                                                            
I: sink.c: Created sink 0 "alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0" with sample spec s32le 2ch 44100Hz and channel map front-left,front-right                                 
I: module-device-restore.c: Restoring volume for source alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0.monitor.                                                                      
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0.monitor.                                                                  
I: source.c: Created source 1 "alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0.monitor" with sample spec s32le 2ch 44100Hz and channel map front-left,front-right                     
I: module-alsa-sink.c: Using 8 fragments of size 3520 bytes, buffer time is 79.82ms                                                                                                          
D: module-alsa-sink.c: hwbuf_unused=0                                                                                                                                                        
D: module-alsa-sink.c: setting avail_min=1                                                                                                                                                   
I: module-alsa-sink.c: Volume ranges from 0 to 127.                                                                                                                                          
I: module-alsa-sink.c: Volume ranges from -63.50 dB to 0.00 dB.                                                                                                                              
I: alsa-util.c: All 2 channels can be mapped to mixer channels.                                                                                                                              
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.                                                                                                           
I: module-alsa-sink.c: Using software mute control.                                                                                                                                          
D: alsa-util.c: snd_pcm_dump():                                                                                                                                                              
D: alsa-util.c: Hardware PCM card 0 'M Audio Revolution-5.1' device 0 subdevice 0                                                                                                            
D: alsa-util.c: Its setup is:                                                                                                                                                                
D: alsa-util.c:   stream       : PLAYBACK                                                                                                                                                    
D: alsa-util.c:   access       : MMAP_INTERLEAVED                                                                                                                                            
D: alsa-util.c:   format       : S32_LE                                                                                                                                                      
D: alsa-util.c:   subformat    : STD                                                                                                                                                         
D: alsa-util.c:   channels     : 2                                                                                                                                                           
D: alsa-util.c:   rate         : 44100                                                                                                                                                       
D: alsa-util.c:   exact rate   : 44100 (44100/1)                                                                                                                                             
D: alsa-util.c:   msbits       : 24                                                                                                                                                          
D: alsa-util.c:   buffer_size  : 3520                                                                                                                                                        
D: alsa-util.c:   period_size  : 440                                                                                                                                                         
D: alsa-util.c:   period_time  : 9977                                                                                                                                                        
D: alsa-util.c:   tstamp_mode  : ENABLE                                                                                                                                                      
D: alsa-util.c:   period_step  : 1                                                                                                                                                           
D: alsa-util.c:   avail_min    : 440                                                                                                                                                         
D: alsa-util.c:   period_event : 0                                                                                                                                                           
D: alsa-util.c:   start_threshold  : -1                                                                                                                                                      
D: alsa-util.c:   stop_threshold   : 1845493760                                                                                                                                              
D: alsa-util.c:   silence_threshold: 0                                                                                                                                                       
D: alsa-util.c:   silence_size : 0                                                                                                                                                           
D: alsa-util.c:   boundary     : 1845493760                                                                                                                                                  
D: module-alsa-sink.c: Requested volume: 0:  80% 1:  80%                                                                                                                                     
D: module-alsa-sink.c: Got hardware volume: 0:  80% 1:  80%                                                                                                                                  
D: module-alsa-sink.c: Thread starting up                                                                                                                                                    
D: module-alsa-sink.c: Calculated software volume: 0:  99% 1:  99%                                                                                                                           
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28                                                                                                                                      
I: module-alsa-sink.c: Starting playback.                                                                                                                                                    
D: module-suspend-on-idle.c: Source alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0.monitor becomes idle.                                                                             
D: module-suspend-on-idle.c: Sink alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0 becomes idle.                                                                                       
I: module.c: Loaded "module-alsa-sink" (index: #5; argument: "device_id=0 sink_name=alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0 tsched=0").                                       
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1412_1724_sound_card_0_alsa_playback_1                                                                            
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer                                                                                                   
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer                                                                                               
I: module-hal-detect.c: Loaded 2 modules.                                                                                                                                                    
I: module.c: Loaded "module-hal-detect" (index: #6; argument: "tsched=0").                                                                                                                   
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': failure                                                                             
I: module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").                                                                                                                 
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0'.                                                                          
D: core-subscribe.c: Dropped redundant event due to change event.                                                                                                                            
I: module-default-device-restore.c: Restored default source 'alsa_input.pci_1412_1724_sound_card_0_alsa_capture_0'.                                                                          
I: module.c: Loaded "module-default-device-restore" (index: #8; argument: "").                                                                                                               
I: module.c: Loaded "module-rescue-streams" (index: #9; argument: "").                                                                                                                       
I: module.c: Loaded "module-always-sink" (index: #10; argument: "").                                                                                                                         
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"                                                                                                             
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1                                                                                                              
I: module.c: Loaded "module-console-kit" (index: #11; argument: "").                                                                                                                         
I: module.c: Loaded "module-position-event-sounds" (index: #12; argument: "").                                                                                                               
D: alsa-util.c: Trying hw:0,1 with SND_PCM_NO_AUTO_FORMAT ...                                                                                                                                
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed                                                                                                                                         
E: alsa-util.c: Error opening PCM device hw:0,1: Permission denied                                                                                                                           
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=hw:0,1"): initialization failed.                                                                                   
E: main.c: Module load failed.                                                                                                                                                               
E: main.c: Failed to initialize daemon.                                                                                                                                                      
I: module.c: Unloading "module-gconf" (index: #0).                                                                                                                                           
I: module.c: Unloaded "module-gconf" (index: #0).                                                                                                                                            
I: module.c: Unloading "module-suspend-on-idle" (index: #1).                                                                                                                                 
I: module.c: Unloaded "module-suspend-on-idle" (index: #1).                                                                                                                                  
I: module.c: Unloading "module-device-restore" (index: #2).                                                                                                                                  
I: module.c: Unloaded "module-device-restore" (index: #2).                                                                                                                                   
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
I: module.c: Unloading "module-stream-restore" (index: #3).                                                                                                                                  
I: module.c: Unloaded "module-stream-restore" (index: #3).                                                                                                                                   
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
I: module.c: Unloading "module-alsa-source" (index: #4).                                                                                                                                     
D: module-rescue-streams.c: No source outputs to move away.                                                                                                                                  
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
D: module-alsa-source.c: Thread shutting down                                                                                                                                                
I: source.c: Freeing source 0 "alsa_input.pci_1412_1724_sound_card_0_alsa_capture_0"                                                                                                         
I: module.c: Unloaded "module-alsa-source" (index: #4).                                                                                                                                      
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
I: module.c: Unloading "module-alsa-sink" (index: #5).                                                                                                                                       
D: module-always-sink.c: Autoloading null-sink as no other sinks detected.                                                                                                                   
I: sink.c: Created sink 1 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right                                                                              
I: source.c: Created source 2 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right                                                                  
D: module-null-sink.c: Thread starting up                                                                                                                                                    
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29                                                                                                                                      
I: module.c: Loaded "module-null-sink" (index: #13; argument: "sink_name=auto_null").                                                                                                        
D: module-rescue-streams.c: No sink inputs to move away.                                                                                                                                     
D: module-rescue-streams.c: No source outputs to move away.                                                                                                                                  
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
D: module-alsa-sink.c: Thread shutting down                                                                                                                                                  
I: sink.c: Freeing sink 0 "alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0"                                                                                                           
I: source.c: Freeing source 1 "alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0.monitor"                                                                                               
I: module.c: Unloaded "module-alsa-sink" (index: #5).                                                                                                                                        
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
I: module.c: Unloading "module-hal-detect" (index: #6).                                                                                                                                      
I: module.c: Unloaded "module-hal-detect" (index: #6).                                                                                                                                       
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
I: module.c: Unloading "module-native-protocol-unix" (index: #7).                                                                                                                            
I: module.c: Unloaded "module-native-protocol-unix" (index: #7).                                                                                                                             
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
I: module.c: Unloading "module-default-device-restore" (index: #8).                                                                                                                          
I: module.c: Unloaded "module-default-device-restore" (index: #8).                                                                                                                           
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
I: module.c: Unloading "module-rescue-streams" (index: #9).                                                                                                                                  
I: module.c: Unloaded "module-rescue-streams" (index: #9).                                                                                                                                   
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
I: module.c: Unloading "module-always-sink" (index: #10).                                                                                                                                    
I: module.c: Unloaded "module-always-sink" (index: #10).                                                                                                                                     
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
I: module.c: Unloading "module-console-kit" (index: #11).                                                                                                                                    
D: module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session1                                                                                                               
I: client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"                                                                                                               
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
I: module.c: Unloaded "module-console-kit" (index: #11).                                                                                                                                     
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
I: module.c: Unloading "module-position-event-sounds" (index: #12).                                                                                                                          
I: module.c: Unloaded "module-position-event-sounds" (index: #12).                                                                                                                           
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
I: module.c: Unloading "module-null-sink" (index: #13).                                                                                                                                      
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                            
D: module-null-sink.c: Thread shutting down                                                                                                                                                  
I: sink.c: Freeing sink 1 "auto_null"                                                                                                                                                        
I: source.c: Freeing source 2 "auto_null.monitor"                                                                                                                                            
I: module.c: Unloaded "module-null-sink" (index: #13).                                                                                                                                       
D: core-subscribe.c: Dropped redundant event due to remove event.                                                                                                                           
I: main.c: Daemon terminated. 
```I think the important part is:
```
E: alsa-util.c: Error opening PCM device hw:0,1: Permission denied                                                                                                                           
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=hw:0,1"): initialization failed.                                                                                   
E: main.c: Module load failed.                                                                                                                                                               
E: main.c: Failed to initialize daemon.  
```

---

