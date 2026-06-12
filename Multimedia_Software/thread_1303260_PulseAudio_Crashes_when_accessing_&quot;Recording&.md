---
title: "PulseAudio Crashes when accessing &quot;Recording&quot;"
date: 2009-10-28
forum: Multimedia Software
---

### Post by NaOH on 2009-10-28
Hey Everyone

This is really sticking in my craw.  First off, a little info on my system:

Linux Mint 7 KDE
Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller
HDA-Intel - HDA ATI SB

So here's what happens:  seems like any form of accessing recording/capture devices results in that infamous cpu overload bug.  I've tried all the prescribed fixes to daemon.conf: changing resampling method to trivial, no cpulimit = yes.  I did upgrade to the latest version of pulseaudio, but this has had no effect.  It may also be worth mentioning that there is a sabrent tv tuner in the mix, saa7130, but unless this is related I've had no issues with it.

I've been toiling with this for two weeks now, any guidance would be most appreciated.

The following are logs from killing pulseaudio, launching it, and selecting the "Volume Meter (Recording) from the tray applet (quickest way of invoking the problem):

```

I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_1002_437b_sound_card_0 idle for too long, suspending ...
I: alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
D: alsa-sink.c: Requested volume: 0: 100% 1: 100%
D: alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
D: alsa-sink.c: Calculated software volume: 0: 100% 1: 100%
D: alsa-sink.c: Requested to rewind 14080 bytes.
D: alsa-sink.c: Limited to 10540 bytes.
D: alsa-sink.c: before: 2635
D: alsa-sink.c: after: 2635
D: alsa-sink.c: Rewound 10540 bytes.
D: sink.c: Processing rewind...
D: source.c: Processing rewind...
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_437b_sound_card_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_437b_sound_card_0 becomes idle.
D: core.c: Hmm, no streams around, trying to vacuum.
I: sink-input.c: Freeing input 0 "Simultaneous output on HDA ATI SB"
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1002_437b_sound_card_0 idle for too long, suspending ...
I: alsa-sink.c: Device suspended...
I: memblock.c: Pool full                                                                                                                                                            
I: memblock.c: Pool full                                                                                                                                                            
I: memblock.c: Pool full                                                                                                                                                            
E: cpulimit.c: Received request to terminate due to CPU overload.                                                                                                                   
I: main.c: Daemon shutdown initiated.                                                                                                                                               
I: module.c: Unloading "module-suspend-on-idle" (index: #0).                                                                                                                        
I: module.c: Unloaded "module-suspend-on-idle" (index: #0).                                                                                                                         
I: module.c: Unloading "module-device-restore" (index: #1).                                                                                                                         
I: module.c: Unloaded "module-device-restore" (index: #1).                                                                                                                          
I: module.c: Unloading "module-stream-restore" (index: #2).                                                                                                                         
I: module.c: Unloaded "module-stream-restore" (index: #2).                                                                                                                          
I: module.c: Unloading "module-card-restore" (index: #3).                                                                                                                           
I: module.c: Unloaded "module-card-restore" (index: #3).                                                                                                                            
I: module.c: Unloading "module-augment-properties" (index: #4).                                                                                                                     
I: module.c: Unloaded "module-augment-properties" (index: #4).                                                                                                                      
I: module.c: Unloading "module-alsa-card" (index: #5).                                                                                                                              
I: module-combine.c: Unconfiguring sink: alsa_output.pci_1002_437b_sound_card_0                                                                                                     
I: memblock.c: Pool full                                                                                                                                                            
I: memblock.c: Pool full                                                                                                                                                            
I: memblock.c: Pool full                                                                                                                                                            
I: memblock.c: Pool full                                                                                                                                                            
I: memblock.c: Pool full                                                                                                                                                            
I: memblock.c: Pool full                                                                                                                                                            
I: memblock.c: Pool full                                                                                                                                                            
I: memblock.c: Pool full                                                                                                                                                            
I: memblock.c: Pool full                                                                                                                                                            
I: memblock.c: Pool full                                                                                                                                                            
I: memblock.c: Pool full
I: memblock.c: Pool full
I: memblock.c: Pool full
D: alsa-sink.c: Thread shutting down
I: memblock.c: Pool full
I: memblock.c: Pool full
I: memblock.c: Pool full
I: memblock.c: Pool full
I: sink.c: Freeing sink 0 "alsa_output.pci_1002_437b_sound_card_0"
I: source.c: Freeing source 0 "alsa_output.pci_1002_437b_sound_card_0.monitor"
D: core-subscribe.c: Dropped redundant event due to change event.
I: memblock.c: Pool full
I: memblock.c: Pool full
I: memblock.c: Pool full
I: memblock.c: Pool full
I: memblock.c: Pool full
I: memblock.c: Pool full
I: memblock.c: Pool full
D: core.c: Hmm, no streams around, trying to vacuum.
I: source-output.c: Freeing output 0 "PulseAudio Volume Meter"
D: core-subscribe.c: Dropped redundant event due to remove event.
D: alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci_1002_437b_sound_card_0"
I: card.c: Freed 0 "alsa_card.pci_1002_437b_sound_card_0"
I: module.c: Unloaded "module-alsa-card" (index: #5).
I: module.c: Unloading "module-hal-detect" (index: #6).
I: module.c: Unloaded "module-hal-detect" (index: #6).
I: module.c: Unloading "module-esound-protocol-unix" (index: #7).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #7).
I: module.c: Unloading "module-native-protocol-unix" (index: #8).
I: client.c: Freed 1 "PulseAudio Volume Meter"
I: module.c: Unloaded "module-native-protocol-unix" (index: #8).
I: module.c: Unloading "module-combine" (index: #9).
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: module-combine.c: Thread shutting down
I: sink.c: Freeing sink 1 "combined"
I: source.c: Freeing source 2 "combined.monitor"
I: module.c: Unloaded "module-combine" (index: #9).
I: module.c: Unloading "module-gconf" (index: #10).
D: module-gconf.c: Unloading module #9
I: module.c: Unloaded "module-gconf" (index: #10).
I: module.c: Unloading "module-default-device-restore" (index: #11).
I: module.c: Unloaded "module-default-device-restore" (index: #11).
I: module.c: Unloading "module-rescue-streams" (index: #12).
I: module.c: Unloaded "module-rescue-streams" (index: #12).
I: module.c: Unloading "module-always-sink" (index: #13).
I: module.c: Unloaded "module-always-sink" (index: #13).
I: module.c: Unloading "module-console-kit" (index: #14).
D: module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session1
I: client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
I: module.c: Unloaded "module-console-kit" (index: #14).
I: module.c: Unloading "module-position-event-sounds" (index: #15).
I: module.c: Unloaded "module-position-event-sounds" (index: #15).
I: module.c: Unloading "module-cork-music-on-phone" (index: #16).
I: module.c: Unloaded "module-cork-music-on-phone" (index: #16).
E: memblock.c: Memory pool destroyed but not all memory blocks freed! 1128 remain.
I: main.c: Daemon terminated.

```

---

### Post by NaOH on 2009-10-28
bump

---

