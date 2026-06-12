---
title: "Rosegarden crashes computer on startup"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by philh99 on 2007-01-16
I am using v6.0 of Ubuntu, however, I di have th same problem in 6.06.

Hi, I can successfully use MuSe, however, looking at the features, I want to try RoseGarden before I fully decide which to use.

I'm having a problem with starting up rosegarden, in that I get the splash screen, but then it hangs my computer completely and I have to do a hardware reset.

I have started jack and if I have the connections window open, I can see that resegarden sets up the connections on the GUI but then it locks the whole computer.

The confusing thing is that MuSe boots up and runs fine.

To try and get some messages out, I used nohup rosegarden & and am including the details of the nohup.out file here:
[I][COLOR="Blue"][SIZE="1"]
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
Creating link /home/philip/.kde/socket-p-ubuntu.
Created link from "/home/philip/.kde/socket-p-ubuntu" to "/tmp/ksocket-philip"
Link points to "/tmp/kde-philip"
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
PluginFactory::instance(dssi): creating new DSSIPluginFactory
[/home/philip/.dssi] [/usr/local/lib/dssi] [/usr/lib/dssi] 
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Rosegarden 1.2.4 - AlsaDriver - alsa-lib version 1.0.11

JackDriver::initialiseAudio - JACK sample rate = 96000Hz, buffer size = 1024
JackDriver::initialiseAudio - creating disk thread
JackDriver::initialiseAudio - found 2 JACK physical outputs
JackDriver::initialiseAudio - connecting from "rosegarden:master out L" to "oss: playback_1"
JackDriver::initialiseAudio - connecting from "rosegarden:master out R" to "oss: playback_2"
JackDriver::initialiseAudio - found 2 JACK physical inputs
JackDriver::initialiseAudio - connecting from "oss:capture_1" to "rosegarden: record in 1 L"
JackDriver::initialiseAudio - connecting from "oss:capture_2" to "rosegarden: record in 1 R"
JackDriver::initialiseAudio - initialised JACK audio subsystem

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    16,0 - (M Audio Delta 410, M Audio Delta 410 MIDI)			(DUPLEX) [ctype 2, ptype 589826, cap 127]
    28,0 - (MidiSport 4x4, MidiSport 4x4 MIDI 1)			(DUPLEX) [ctype 2, ptype 589826, cap 127]
    28,1 - (MidiSport 4x4, MidiSport 4x4 MIDI 2)			(DUPLEX) [ctype 2, ptype 589826, cap 127]
    28,2 - (MidiSport 4x4, MidiSport 4x4 MIDI 3)			(DUPLEX) [ctype 2, ptype 589826, cap 127]
    28,3 - (MidiSport 4x4, MidiSport 4x4 MIDI 4)			(DUPLEX) [ctype 2, ptype 589826, cap 127]

CREATED OUTPUT PORT 3: out 1 - MIDI external device for device 0
Connecting my port 3 to 16:0 on initialisation
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
[/home/philip/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa] 
done
Creating device 0 in Play mode for connection 16:0 M Audio Delta 410 MIDI (duplex)
Default device name for this device is MIDI external device
Creating device 1 in Record mode for connection 16:0 M Audio Delta 410 MIDI (duplex)
Default device name for this device is MIDI hardware input device
CREATED OUTPUT PORT 4: out 2 - MIDI external device 2 for device 2
Connecting my port 4 to 28:0 on initialisation
done
Creating device 2 in Play mode for connection 28:0 MidiSport 4x4 MIDI 1 (duplex)
Default device name for this device is MIDI external device 2
Creating device 3 in Record mode for connection 28:0 MidiSport 4x4 MIDI 1 (duplex)
Default device name for this device is MIDI hardware input device 2
CREATED OUTPUT PORT 5: out 3 - MIDI external device 3 for device 4
Connecting my port 5 to 28:1 on initialisation
done
Creating device 4 in Play mode for connection 28:1 MidiSport 4x4 MIDI 2 (duplex)
Default device name for this device is MIDI external device 3
Creating device 5 in Record mode for connection 28:1 MidiSport 4x4 MIDI 2 (duplex)
Default device name for this device is MIDI hardware input device 3
CREATED OUTPUT PORT 6: out 4 - MIDI external device 4 for device 6
Connecting my port 6 to 28:2 on initialisation
done
Creating device 6 in Play mode for connection 28:2 MidiSport 4x4 MIDI 3 (duplex)
Default device name for this device is MIDI external device 4
Creating device 7 in Record mode for connection 28:2 MidiSport 4x4 MIDI 3 (duplex)
Default device name for this device is MIDI hardware input device 4
CREATED OUTPUT PORT 7: out 5 - MIDI external device 5 for device 8
Connecting my port 7 to 28:3 on initialisation
done
Creating device 8 in Play mode for connection 28:3 MidiSport 4x4 MIDI 4 (duplex)
Default device name for this device is MIDI external device 5
Creating device 9 in Record mode for connection 28:3 MidiSport 4x4 MIDI 4 (duplex)
Default device name for this device is MIDI hardware input device 5
CREATED OUTPUT PORT 8: out 6 - MIDI output system device for device 10
done
Creating device 10 in Play mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI output system device
Creating device 11 in Record mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI input system device
AlsaDriver::setCurrentTimer((auto))
System timer is only 250Hz, sending a warning
    Current timer set to "system timer" with timer checks
    WARNING: using system timer with only 250Hz resolution!
AlsaDriver::initialiseMidi -  initialised MIDI subsystem[/SIZE][/COLOR][/I]

Thanks for any help you can be.

---

### Post by sgx on 2007-01-16
based on what others in misc distros have suffered. I'm guessing the
timer in your kernel is wrong for midi use, so google search the relevant
terms, and you should find lots of company, and hopefully their solutions for a more midi friendly kernel...on a Fedora 5 box, I had to get an -older- kernel to even test rosegarden basics...

---

