---
title: "using ROSEGARDEN and the sound does not always start but sometimes does"
date: 2010-01-15
forum: Multimedia Software
---

### Post by shantiq on 2010-01-15
[COLOR=Blue][B];);)  using ROSEGARDEN and the sound does not always start but sometimes does

and the thing is i am not using anything but midi just midi

sometimes it starts the sound is there other times it does not


can any of you spot anything in the terminal which might explain that?



1.  i understand and i know because it works one out of 3 or four that i do not need jack driver for this task


2.  is the problem with timidity/?



any intelligent suggestion welcome   shan

[/B][/COLOR]```
shantiq@shantiq-desktop:~$ rosegarden
kbuildsycoca running...
shantiq@shantiq-desktop:~$ PluginFactory::instance(dssi): creating new DSSIPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/shantiq/.dssi] [/usr/local/lib/dssi] [/usr/lib/dssi] 
Rosegarden 1.7.3 - AlsaDriver [ALSA library version 1.0.18, module version 1.0.20, kernel version 2.6.31-17-generic]

JackDriver::initialiseAudio - JACK server not running

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)            (DUPLEX) [ctype 2, ptype 655362, cap 99]
    128,0 - (TiMidity, TiMidity port 0)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,1 - (TiMidity, TiMidity port 1)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,2 - (TiMidity, TiMidity port 2)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,3 - (TiMidity, TiMidity port 3)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    129,0 - (TiMidity, TiMidity port 0)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    129,1 - (TiMidity, TiMidity port 1)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    129,2 - (TiMidity, TiMidity port 2)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    129,3 - (TiMidity, TiMidity port 3)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]

CREATED OUTPUT PORT 3:out 1 - MIDI software device for device 0
Connecting my port 3 to 128:0 on initialisation
done
Creating device 0 in Play mode for connection 128:0 TiMidity port 0 (write)
Default device name for this device is MIDI software device
CREATED OUTPUT PORT 4:out 2 - MIDI software device 2 for device 1
Connecting my port 4 to 128:1 on initialisation
done
Creating device 1 in Play mode for connection 128:1 TiMidity port 1 (write)
Default device name for this device is MIDI software device 2
CREATED OUTPUT PORT 5:out 3 - MIDI software device 3 for device 2
Connecting my port 5 to 128:2 on initialisation
done
Creating device 2 in Play mode for connection 128:2 TiMidity port 2 (write)
Default device name for this device is MIDI software device 3
CREATED OUTPUT PORT 6:out 4 - MIDI software device 4 for device 3
Connecting my port 6 to 128:3 on initialisation
done
Creating device 3 in Play mode for connection 128:3 TiMidity port 3 (write)
Default device name for this device is MIDI software device 4
CREATED OUTPUT PORT 7:out 5 - MIDI software device 5 for device 4
Connecting my port 7 to 129:0 on initialisation
done
Creating device 4 in Play mode for connection 129:0 TiMidity port 0 (write)
Default device name for this device is MIDI software device 5
CREATED OUTPUT PORT 8:out 6 - MIDI software device 6 for device 5
Connecting my port 8 to 129:1 on initialisation
done
Creating device 5 in Play mode for connection 129:1 TiMidity port 1 (write)
Default device name for this device is MIDI software device 6
CREATED OUTPUT PORT 9:out 7 - MIDI software device 7 for device 6
Connecting my port 9 to 129:2 on initialisation
done
Creating device 6 in Play mode for connection 129:2 TiMidity port 2 (write)
Default device name for this device is MIDI software device 7
CREATED OUTPUT PORT 10:out 8 - MIDI software device 8 for device 7
Connecting my port 10 to 129:3 on initialisation
done
Creating device 7 in Play mode for connection 129:3 TiMidity port 3 (write)
Default device name for this device is MIDI software device 8
CREATED OUTPUT PORT 11:out 9 - MIDI output system device for device 8
done
Creating device 8 in Play mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI output system device
Creating device 9 in Record mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI input system device
AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 20, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.20 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 31, suffix = "generic"
AlsaDriver::versionIsAtLeast: is version 2.6.31-17-generic at least 2.6.20? yes
Using low-resolution system timer, sending a warning
    Current timer set to "system timer"
    WARNING: using system timer with only 250Hz resolution!
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 20, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.20 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 31, suffix = "generic"
AlsaDriver::versionIsAtLeast: is version 2.6.31-17-generic at least 2.6.20? yes
Using low-resolution system timer, sending a warning
    Current timer set to "system timer"
    WARNING: using system timer with only 250Hz resolution!
Composition::getTrackById(0) - WARNING - track id not found, this is probably a BUG /build/buildd/rosegarden-1.7.3/src/base/Composition.cpp:1533
Available track ids are: 
Renaming device 0 to General MIDI Device
Renamed 130:3 to General MIDI Device
LADSPAPluginFactory::discoverPlugins - done
CompositionModelImpl::slotInstrumentParametersChanged()
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/shantiq/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa] 
RosegardenGUIApp::awaitDialogClearance: entering
RosegardenGUIApp::awaitDialogClearance: exiting
TrackButtons::slotUpdateTracks
LADSPAPluginFactory::discoverPlugins - done

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)            (DUPLEX) [ctype 2, ptype 655362, cap 99]
    128,0 - (TiMidity, TiMidity port 0)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,1 - (TiMidity, TiMidity port 1)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,2 - (TiMidity, TiMidity port 2)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,3 - (TiMidity, TiMidity port 3)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    129,0 - (TiMidity, TiMidity port 0)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    129,1 - (TiMidity, TiMidity port 1)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    129,2 - (TiMidity, TiMidity port 2)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    129,3 - (TiMidity, TiMidity port 3)        (WRITE ONLY) [ctype 1, ptype 2, cap 66]

Rosegarden: WARNING: No accurate sequencer timer available
RosegardenGUIApp::awaitDialogClearance: entering
RosegardenGUIApp::awaitDialogClearance: exiting
Comparing current version "1.7.3" with latest version "1.7.3"
CompositionModelImpl::segmentAdded: segment 0x8f892d8 on track 0: calling setTrackHeights
TrackButtons::slotUpdateTracks
CompositionModelImpl::slotInstrumentParametersChanged()
CompositionModelImpl::slotInstrumentParametersChanged()
CompositionModelImpl::slotInstrumentParametersChanged()
QMetaObject::findSignal:Rosegarden::PianoKeyboard: Conflict with Rosegarden::PitchRuler::hoveredOverKeyChanged(unsigned int)
QMetaObject::findSignal:Rosegarden::PianoKeyboard: Conflict with Rosegarden::PitchRuler::keyPressed(unsigned int,bool)
QMetaObject::findSignal:Rosegarden::PianoKeyboard: Conflict with Rosegarden::PitchRuler::keySelected(unsigned int,bool)
CompositionModelImpl::segmentAdded: segment 0x8fb6028 on track 11: calling setTrackHeights
TrackButtons::slotUpdateTracks
RosegardenSequencerApp::quit()
DataBlockRepository::clear()
SoundDriver::~SoundDriver (exiting)
AudioPlayQueue::~AudioPlayQueue()
Toodle-pip.
Warning: Composition::~Composition() with 3 observers still extant
Observers are: 0x8e282d4 [N10Rosegarden19SegmentParameterBoxE] 0x8ca375c [N10Rosegarden17TrackParameterBoxE] 0x8e74348 [N10Rosegarden20CompositionModelImplE]
WARNING: Composition::getSegmentVoiceIndex: segment 0x8f892d8 not found in composition
WARNING: Composition::getSegmentVoiceIndex: segment 0x8fb6028 not found in composition
ICE default IO error handler doing an exit(), pid = 2615, errno = 11
shantiq@shantiq-desktop:~$ 


```

---

### Post by shantiq on 2010-01-15
[COLOR=Blue][B]also and this might have something to do with it mayhaps i always get this message when i open rosegarden


[IMG]http://img685.imageshack.us/img685/3404/screenshotfv.png[/IMG]



and when i run it in the terminal i get this

[/B][/COLOR]```
shantiq@shantiq-desktop:~$ sudo modprobe snd-rtctimer
FATAL: Module snd_rtctimer not found.
shantiq@shantiq-desktop:~$ 

```

---

