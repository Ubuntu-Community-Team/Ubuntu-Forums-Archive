---
title: "Invisible kmix"
date: 2011-03-27
forum: Multimedia Software
---

### Post by jandac2011 on 2011-03-27
I don't know what I did, or maybe it was some update. I'm running Kubuntu Maverick 64-bit. Kmix in system tray disappeared. Sometimes it shows up after some long time, but I haven't seen it for the last month. Kmix process still runs, and it takes one entire thread of my Intel i3 processor. Killing kmix and restarting it does not change anything. Sound applications work as expected, but I cannot change volume. They work well also when I kill kmix. When I invoke kmix from xterm, I get the following messages:
```
QMetaObject::invokeMethod: No such method KMixApp::loadCommandLineOptionsForNewInstance()
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kmix(12181) Mixer::setGlobalMaster: Mixer::setGlobalMaster() card= "PulseAudio::Playback_Devices:1"  control= "alsa_output.pci-0000_00_1b.0.analog-stereo"
kmix(12181) MixerToolBox::initMixer: Looking for mixers with the :  "PulseAudio"  driver
kmix(12181) Mixer_PULSE::Mixer_PULSE: Probing for PulseAudio...
kmix(12181) sink_cb: Got some info about sink:  "Internal Audio Analog Stereo"
kmix(12181) source_cb: Got some info about source:  "Internal Audio Analog Stereo"
kmix(12181) source_cb: Ignoring Monitor Source:  Monitor of Internal Audio Analog Stereo
kmix(12181) client_cb: Got some info about client:  "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
kmix(12181) client_cb: Got some info about client:  "XSMP Session on KDE as 10d8cbdb6f000130045430400000017460015"
kmix(12181) client_cb: Got some info about client:  "libphonon"
kmix(12181) client_cb: Got some info about client:  "knotify4"
kmix(12181) client_cb: Got some info about client:  "Skype"
kmix(12181) client_cb: Got some info about client:  "PulseAudio Device Chooser"
kmix(12181) client_cb: Got some info about client:  "emacs"
kmix(12181) client_cb: Got some info about client:  "kmix-probe"
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-application-name:ALSA plug-in [speaker-test]
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-media-role:video
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-application-name:MPlayer
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  source-output-by-application-name:VBox
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-media-role:none
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-application-name:ALSA plug-in [mplayer]
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-application-name:Multimedia Systems Selector
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  source-output-by-media-role:phone
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-media-role:phone
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-media-role:a11y
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-application-name:OSS Emulation[Emu]
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-media-role:abstract
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-application-name:ALSA plug-in [sox]
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-application-name:kaffeine-xbu
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-media-role:music
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-media-role:event
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-application-name:ALSA plug-in [audacity]
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  source-output-by-application-id:org.PulseAudio.pavucontrol
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  source-output-by-media-role:abstract
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-application-name:ALSA plug-in [npviewer.bin]
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  source-output-by-application-name:ALSA plug-in [audacity]
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-application-name:Sound Recorder
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  source-output-by-application-name:Sound Recorder
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  source-output-by-application-name:PulseAudio Volume Meter
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-media-role:game
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-application-name:VBox
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  source-output-by-application-name:ALSA plug-in [gstreamer-properties]
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  source-output-by-application-name:Multimedia Systems Selector
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-application-name:VLC media player
kmix(12181) ext_stream_restore_read_cb: Got some info about restore rule:  sink-input-by-application-name:ALSA plug-in [operapluginwrapper-ia32-linux]
kmix(12181) Mixer_PULSE::Mixer_PULSE: PulseAudio probe complete.
kmix(12181) Mixer_PULSE::connectToDaemon: Attempting connection to PulseAudio sound daemon
kmix(12181) Mixer_PULSE::Mixer_PULSE: PulseAudio status:  Active
kmix(12181) Mixer_PULSE::open: Using PulseAudio for mixer:  "Playback Devices"
kmix(12181) Mixer::openIfValid: Mixer::open() detected master:  "alsa_output.pci-0000_00_1b.0.analog-stereo"
kmix(12181) MixerToolBox::possiblyAddMixer: mixerNums entry of added mixer is now:  1
kmix(12181) MixerToolBox::initMixer: Success! Found a mixer with the :  "PulseAudio"  driver
kmix(12181) Mixer_PULSE::open: Using PulseAudio for mixer:  "Capture Devices"
kmix(12181) Mixer::openIfValid: Mixer::open() detected master:  "alsa_input.pci-0000_00_1b.0.analog-stereo"
kmix(12181) MixerToolBox::possiblyAddMixer: mixerNums entry of added mixer is now:  1
kmix(12181) MixerToolBox::initMixer: Success! Found a mixer with the :  "PulseAudio"  driver
kmix(12181) Mixer_PULSE::open: Using PulseAudio for mixer:  "Playback Streams"
kmix(12181) Mixer::openIfValid: Mixer::open() detected master:  "restore:sink-input-by-media-role:event"
kmix(12181) MixerToolBox::possiblyAddMixer: mixerNums entry of added mixer is now:  1
kmix(12181) MixerToolBox::initMixer: Success! Found a mixer with the :  "PulseAudio"  driver
kmix(12181) Mixer_PULSE::open: Using PulseAudio for mixer:  "Capture Streams"
kmix(12181) MixerToolBox::possiblyAddMixer: mixerNums entry of added mixer is now:  1
kmix(12181) MixerToolBox::initMixer: Success! Found a mixer with the :  "PulseAudio"  driver
kmix(12181) MixerToolBox::initMixer: "Sound drivers supported: PulseAudio + ALSA + OSS
Sound drivers used: PulseAudio"
Total number of detected Mixers:  4
kmix(12181) KMixWindow::saveViewConfig: About to save config (View)
kmix(12181) KMixWindow::saveViewConfig: Config (View) saving done
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.default.xml" ; fnfq1= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.Playback_Devices.xml" ; fnfq2= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.default.xml" ; fnfq1= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.Capture_Devices.xml" ; fnfq2= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.default.xml" ; fnfq1= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.Playback_Streams.xml" ; fnfq2= ""
kmix(12181) MixerToolBox::selectProfile: 0 : Try user profile  "/home/jandac/.kde/share/apps/kmix/profiles/PulseAudio.Playback_Streams.1.Controls.xml"
kmix(12181) GUIProfile::readProfile: Read profile: "profiles/PulseAudio.Playback_Streams.1.Controls.xml"  =>  "/home/jandac/.kde/share/apps/kmix/profiles/PulseAudio.Playback_Streams.1.Controls.xml"
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.default.xml" ; fnfq1= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.Capture_Streams.xml" ; fnfq2= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.default.xml" ; fnfq1= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.Playback_Devices.xml" ; fnfq2= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.default.xml" ; fnfq1= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.Playback_Devices.xml" ; fnfq2= ""
kmix(12181) KMixerWidget::loadConfig: KMixerWidget::loadConfig()
kmix(12181) KMixerWidget::loadConfig: KMixerWidget::loadConfig() "Controls"
kmix(12181) KMixToolBox::loadView: KMixToolBox::loadView() grp= "View.Controls"
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.default.xml" ; fnfq1= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.Capture_Devices.xml" ; fnfq2= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.default.xml" ; fnfq1= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.Capture_Devices.xml" ; fnfq2= ""
kmix(12181) KMixerWidget::loadConfig: KMixerWidget::loadConfig()
kmix(12181) KMixerWidget::loadConfig: KMixerWidget::loadConfig() "Controls"
kmix(12181) KMixToolBox::loadView: KMixToolBox::loadView() grp= "View.Controls"
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.default.xml" ; fnfq1= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.Playback_Streams.xml" ; fnfq2= ""
kmix(12181) MixerToolBox::selectProfile: 0 : Try user profile  "/home/jandac/.kde/share/apps/kmix/profiles/PulseAudio.Playback_Streams.1.Controls.xml"
kmix(12181) GUIProfile::readProfile: Read profile: "profiles/PulseAudio.Playback_Streams.1.Controls.xml"  =>  "/home/jandac/.kde/share/apps/kmix/profiles/PulseAudio.Playback_Streams.1.Controls.xml"
kmix(12181): _refcount already 0 
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.default.xml" ; fnfq1= ""
kmix(12181) MixerToolBox::selectProfile: "profiles/PulseAudio.Playback_Streams.xml" ; fnfq2= ""
kmix(12181) MixerToolBox::selectProfile: 0 : Try user profile  "/home/jandac/.kde/share/apps/kmix/profiles/PulseAudio.Playback_Streams.1.Controls.xml"
kmix(12181) GUIProfile::readProfile: Read profile: "profiles/PulseAudio.Playback_Streams.1.Controls.xml"  =>  "/home/jandac/.kde/share/apps/kmix/profiles/PulseAudio.Playback_Streams.1.Controls.xml"
kmix(12181) ViewBase::setMixSet: Dynamic mixer  "PulseAudio::Playback_Streams:1"  is NOT using Fallback GUIProfile. Checking to see if new controls are present
<unknown program name>(12180)/: Communication problem with  "kmix" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 

```
At the same time, phonom complains that some devices have disappeared (they do not show up in other places anymore):
[LIST]
[*]Internal Audio Digital Stereo (IEC 958)
[*]Internal Audio Digital Stereo (HDMI)
[*]Internal Audio Analog Surround 5.1
[/LIST]
What should I do to get my mixer back?

---

### Post by Yellow Pasque on 2011-03-27
Sounds like a good problem to report on launchpad (you might want to install gdb and kdemultimedia-dbg and try and get more detailed error output).

---

### Post by SeijiSensei on 2011-03-27
You might be able to sort some of this out using the Phonon controls in System Settings > Multimedia > Phonon.

When kmix disappeared from my system tray a while back, I fixed the problem simply by running "kmix &" from the terminal and logging out to save my KDE configuration.  Don't know if you have a deeper problem than that, though.

---

### Post by jandac2011 on 2011-03-27
> **Temüjin said:**
> Sounds like a good problem to report on launchpad (you might want to install gdb and kdemultimedia-dbg and try and get more detailed error output).
I'm not sure if I should bother developers with that - perhaps it is only my fault or a hardware error. I have gdb installed, I will install kdemultimedia-gdb and see what I can learn from that.

---

### Post by jandac2011 on 2011-03-27
> **SeijiSensei said:**
> You might be able to sort some of this out using the Phonon controls in System Settings > Multimedia > Phonon.

When kmix disappeared from my system tray a while back, I fixed the problem simply by running "kmix &" from the terminal and logging out to save my KDE configuration.  Don't know if you have a deeper problem than that, though.
System Settings > Multimedia > Phonom gave me the following pop-up window error:
```
KDE detected that one or more internal sound devices were removed.
Do you want KDE to permanently forget about these devices?
This is the list of devices KDE thinks can be removed:
Capture: NVidia CK804 with ALC850
Output: HDA Intel, ALC889 Analog (Direct hardware device without any conversions)
Output: HDA Intel, ALC889 Analog (Direct sample mixing device)
Output: HDA Intel, ALC889 Analog (Hardware device with all software conversions)
Output: NVidia CK804 with ALC850
```
Perhaps this is because I have killed kmix, but when I invoke it again, there is only Internal Audio Analog Stereo, and dimmed: some kind of sink (unfortunately with translated name for no apparent reason), Internal Audio Digital Stereo (IEC958), Internal Audio Digital Stereo (HDMI), and Internal Audio Analog Surround 5.1. This is for output, input is even more limited in the gray section. So I can only choose Internal Audio Analog Stereo, defer it (so that a dimmed option takes precedence - it does not seem a good choice), or test it (it works fine). 

I do run kmix from a terminal, but it just does not show up, neither as a separate window, nor in the system tray. It terminates, but it calls another kmix process before that, and that second process does not terminate on its own:
```
~ $ ps -Af f | grep kmix
jandac   19092  1879  0 20:59 pts/3    S+     0:00  |       \_ grep kmix
jandac   19088  1878  0 20:59 pts/1    S      0:00  |       \_ kmix
jandac   19089 19088 99 20:59 pts/1    Rl     0:20  |           \_ kmix
~ $ ps -Af f | grep kmix
jandac   19094  1879  0 20:59 pts/3    S+     0:00  |       \_ grep kmix
jandac   19089     1 97 20:59 pts/1    Rl     0:25 kmix
```
Perhaps the last messages from kmix on the console are significant:
```
kmix(19089) GUIProfile::readProfile: Read profile: "profiles/PulseAudio.Playback_Streams.1.Controls.xml"  =>  "/home/jandac/.kde/share/apps/kmix/profiles/PulseAudio.Playback_Streams.1.Controls.xml"
kmix(19089) ViewBase::setMixSet: Dynamic mixer  "PulseAudio::Playback_Streams:1"  is NOT using Fallback GUIProfile. Checking to see if new controls are present
<unknown program name>(19088)/: Communication problem with  "kmix" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 

```

---

### Post by SeijiSensei on 2011-03-27
First, try deleting $HOME/.pulse, logging out then logging back in.  Did that help?

Another strategy I use in cases like this is to create a brand-new user account and see if it works correctly when logged in as that user.  Sometimes funky settings in .kde may be to blame.

If those approaches don't work, you can try forcing PulseAudio to reconfigure itself with "sudo dkpg-reconfigure pulseaudio".  If that doesn't help, you could remove and reinstall Pulse with "sudo apt-get purge pulseaudio; sudo apt-get install pulseaudio".  

I had many issues with Pulse in earlier releases, but they generally went away after moving to 10.10.

---

### Post by jandac2011 on 2011-03-27
> **SeijiSensei said:**
> First, try deleting $HOME/.pulse, logging out then logging back in.  Did that help?

Another strategy I use in cases like this is to create a brand-new user account and see if it works correctly when logged in as that user.  Sometimes funky settings in .kde may be to blame.

If those approaches don't work, you can try forcing PulseAudio to reconfigure itself with "sudo dkpg-reconfigure pulseaudio".  If that doesn't help, you could remove and reinstall Pulse with "sudo apt-get purge pulseaudio; sudo apt-get install pulseaudio".  

I had many issues with Pulse in earlier releases, but they generally went away after moving to 10.10.
Thanks, it worked. Removing ~/.pulse did the trick, and I have plenty of new devices in phonom.

Strangely, when I added a new user, and I tried to log in, that led to problems. I had to change the password for the new user, but I could not type it into the provided box. I had to change that password under gnome (from gnome administration menu), and then log in into KDE as the new user. The new user had kmix widget in the panel.

---

### Post by jandac2011 on 2011-03-27
> **jandac2011 said:**
> Thanks, it worked. Removing ~/.pulse did the trick, and I have plenty of new devices in phonom.

Strangely, when I added a new user, and I tried to log in, that led to problems. I had to change the password for the new user, but I could not type it into the provided box. I had to change that password under gnome (from gnome administration menu), and then log in into KDE as the new user. The new user had kmix widget in the panel.
That was too quick. I checked with audacity, and it worked. But smplayer stopped working, and padevchooser cannot connect to the sound server. I should have kept the old ~/.pulse.

---

### Post by jandac2011 on 2011-03-27
> **jandac2011 said:**
> That was too quick. I checked with audacity, and it worked. But smplayer stopped working, and padevchooser cannot connect to the sound server. I should have kept the old ~/.pulse.
Removing ~/.pulse had also a strange effect on emacs. Every menu action is now delayed, and a console prints > waitpid(): No child processes.

---

### Post by jandac2011 on 2011-03-28
> **jandac2011 said:**
> Removing ~/.pulse had also a strange effect on emacs. Every menu action is now delayed, and a console prints .
This morning everything works again. It looks like I had to reload the whole system to make it work after changes. Simply logging out and in did not work.

---

### Post by SeijiSensei on 2011-03-28
> **jandac2011 said:**
> This morning everything works again. It looks like I had to reload the whole system to make it work after changes. Simply logging out and in did not work.

That's good to hear.  I was worried I had led you down the path to destruction!

---

### Post by jandac2011 on 2011-04-12
The solution worked for some time, but strange things happen. It is not a serious problem, as I always have sound regardless of the state of my pulse audio. But most of the devices in phonon disappeared by now. They did so also for the new user I created. The only device left is "Internal Audio Analog Stereo". Nothing about HDMI or other fancy devices that I should presumably have, as my motherboard is Gigabyte GA-H55MM-USB3, and it does have a HDMI port, and a Realtek ALC889 codec 2/4/5.1/7.1-channel. kmix shows only "Internal Audio Analog Stereo", GNOME Alsa mixer shows controls for Intel IbexPeak HDMI (and only those, which is strange, as I don't use HDMI). 

The only thing I did was to remove .pulse again (with .pulsecookie) because kmix again would take an entire thread out of the four that my Intel i3 processor has, and it would not show the mixer window nor the simple slider. After the removal, it works again, but with showing only one device.

What else should I delete, and why is this happening on its own?

---

### Post by jandac2011 on 2011-04-12
Removing .pulseaudio and rebooting solves the problem of invisible kmix only temporarily. Three quarters of an hour ago kmix worked (I could change the volume with the slider in the panel, I could invoke the mixer window), but it does not any more without any intervention from my part. And again kmix process takes one entire thread. I suspect that it is also responsible for a very long time (minutes) it takes digikam to start. I use Kubuntu 10.10 on this desktop computer, maybe that is the problem, but moving back to 10.04 is difficult, as I don't have enough space on an external disk.

The only two applications I used today that use sound are speech dispatcher (talking clock) and amarok (listening to foreign radio).

---

