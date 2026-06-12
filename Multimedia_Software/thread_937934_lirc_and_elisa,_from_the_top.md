---
title: "lirc and elisa, from the top"
date: 2008-10-04
forum: Multimedia Software
---

### Post by Miserableman on 2008-10-04
Hello all. I was originally planning to post this on the [elisa forums](http://elisa.fluendo.com/forums/) but in the process of doing so I got banned (!), presumably because I was generating load on their already overstrained server. In desperation therefore, I'm turning to you guys to see if you can help :0)


I've been struggling to get my Windows Media remote control working with elisa without success in any way, shape or form. I'm now thoroughly bamboozled by innaccuracies and inconsistencies between what I read on the web in various forums/tutorials about the way elisa/lirc *should* work and the way they actually *do* seem to work, and could use some help, a sit down and a nice cup of tea to be frank. I've come to the conclusion that either I'm stupid, my installation of elisa is brain-damaged or the architecture of the elisa project has fundamentally been changed recently, or perhaps all three.

So, from the top.

**The Remote**

I have a Windows Media Center remote (if you consult [http://www.mythtv.org/wiki/index.php/MCE_Remote](http://www.mythtv.org/wiki/index.php/MCE_Remote), it's the second from left as pictured). As best as I can tell this is fully working, although I've yet to get it doing anything useful.

less /etc/lirc/lircd.conf
```

#comments removed for brevity
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

```
less /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
```

begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

        Blue    0x00007ba1
        Yellow  0x00007ba2
        Green   0x00007ba3
        Red     0x00007ba4
        Teletext        0x00007ba5

# starts at af
        Radio    0x00007baf
        Print    0x00007bb1
        Videos   0x00007bb5
        Pictures 0x00007bb6
        RecTV    0x00007bb7
        Music    0x00007bb8
        TV       0x00007bb9
# no ba - d8

        Guide    0x00007bd9
        LiveTV   0x00007bda
        DVD      0x00007bdb
        Back     0x00007bdc
        OK       0x00007bdd
        Right    0x00007bde
        Left     0x00007bdf
        Down     0x00007be0
        Up       0x00007be1

        Star       0x00007be2
        Hash       0x00007be3

        Replay   0x00007be4
        Skip     0x00007be5
        Stop     0x00007be6
        Pause    0x00007be7
        Record   0x00007be8
        Play     0x00007be9
        Rewind   0x00007bea
        Forward  0x00007beb
        ChanDown 0x00007bec
        ChanUp   0x00007bed
        VolDown  0x00007bee
        VolUp    0x00007bef
        More     0x00007bf0
        Mute     0x00007bf1
        Home     0x00007bf2
        Power    0x00007bf3
        Enter    0x00007bf4
        Clear    0x00007bf5
        Nine     0x00007bf6
        Eight    0x00007bf7
        Seven    0x00007bf8
        Six      0x00007bf9
        Five     0x00007bfa
        Four     0x00007bfb
        Three    0x00007bfc
        Two      0x00007bfd
        One      0x00007bfe
        Zero     0x00007bff
      end codes

end remote

```
Some sample output from irw (all the buttons on the remote seem to produce something):
```

000000037ff07be7 00 Pause mceusb
000000037ff07be9 00 Play mceusb
000000037ff07be5 00 Skip mceusb
000000037ff07be1 00 Up mceusb

```
**Elisa**
I'm running the 0.5.12 packages from the elisa-developers repository on Ubuntu Hardy. The system throws quite a few warnings on startup, and I'm not discounting for a second the possibility that my elisa installation is fundamentally wonked.

The following is the console output from me starting elisa and then shutting it down again. Even if you remove the lines moaning about not being able to understand the remote control config file there's still a lot of stuff going wrong. Is this normal? I upgraded from the stock 0.3.5 in the Ubuntu repositories to the developer repository and quickly became unstuck (see [this thread](https://elisa.fluendo.com/forums/viewtopic.php?id=741)), only managing to fix that problem properly yesterday by deleting a directory deep inside /usr/lib/python2.5 and reinstalling python-elisa.
```

WARN  MainThread      plugin_registry             Oct 04 15:31:04  plugin conflict elisa-plugin-coherence 0.1 (elisa/core/plugin_registry.py:220)
WARN  MainThread      gst_metadata_slave_process_protocol Oct 04 15:31:05  Starting Slave-2 on unix:/tmp/elisa-metadata-V5O7wv.socket launching elisa.plugins.gstreamer.amp_slave.run_slave
(Slave-2 stdout) (elisa/plugins/amp/master.py:54)
WARN  MainThread      gst_metadata_slave_process_protocol Oct 04 15:31:05  /usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
(Slave-2 stderr) (elisa/plugins/amp/master.py:57)
==> at https://login.yahoo.com/config/login?.src=flickr&.pc=5134&.scrumb=0&.pd=c%3DE0.GahOp2e4MjkX.5l2HgAoLkpmyPvccpVM-&.intl=us&.done=https%3A%2F%2Flogin.yahoo.com%2Fconfig%2Fvalidate%3F.src%3Dflickr%26.pc%3D5134%26.scrumb%3D0%26.pd%3Dc%253DE0.GahOp2e4MjkX.5l2HgAoLkpmyPvccpVM-%26.intl%3Dus%26.done%3Dhttp%253A%252F%252Fwww.flickr.com%252Fsignin%252Fyahoo%252F%253Fredir%253D%25252Fservices%25252Fauth%25252F%25253Fperms%25253Ddelete%252526api_key%25253Def2cc311ac8916c794b436bf482c5de5%252526frob%25253D72157607729785303-0b4d43e73daf6b70-1008964%252526api_sig%25253Dd0b00ef6904075706b9f8a561a95468c
Note: submit is using submit button: name=".save", value="Sign In"
WARN  MainThread      resource_manager            Oct 04 15:31:10  Creating wmd.wmd_resource:WMDResource failed. A full traceback can be found at /tmp/elisa_6A4itC.txt (elisa/core/manager.py:83)
WARN  coherence                   Oct 04 15:31:11  Coherence UPnP framework version 0.5.8 starting... (coherence/base.py:251)
WARN  webserver                   Oct 04 15:31:11  WebServer on port 54513 ready (coherence/base.py:106)
WARN  MainThread      resource_manager            Oct 04 15:31:11  Creating smbwin32.smbwin32_resource:SmbWin32Resource failed. A full traceback can be found at /tmp/elisa_v7Tx9E.txt (elisa/core/manager.py:83)
WARN  MainThread      service_manager             Oct 04 15:31:11  Creating osso.osso_service:OssoService failed. A full traceback can be found at /tmp/elisa_hQML6u.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               Oct 04 15:31:11  Creating winremote.streamzap_input:StreamzapInput failed. A full traceback can be found at /tmp/elisa_XKk47W.txt (elisa/core/manager.py:83)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Play'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'toggle_play_pause_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Right'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'move_right_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'OK'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know ke
y 'activate_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Power'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'close_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Mute'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'toggle_mute_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'VolDown'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'decrement_volume_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Rewind'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'seek_backward_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Stop'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'stop_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Up'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'move_up_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'VolUp'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'increment_volume_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Down'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'move_down_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Pause'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'pause_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Enter'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'activate_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Forward'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'seek_forward_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Home'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'toggle_menu_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Red'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'toggle_fullscreen_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Left'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'move_left_key'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key '0'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      input_manager               Oct 04 15:31:11  Creating lirc.lirc_input:LircInput failed. A full traceback can be found at /tmp/elisa_Xsurmy.txt (elisa/core/manager.py:83)
WARNING:root:Cannot find theme file: /usr/lib/python2.5/site-packages/elisa/plugins/poblesec/widgets/player/styles.conf
WARNING:root:Cannot find resource file: /usr/lib/python2.5/site-packages/elisa/plugins/poblesec/widgets/player/resources.conf
WARNING:root:Cannot find theme configuration files
WARNING:root:Cannot find resource file: /usr/lib/python2.5/site-packages/elisa/plugins/poblesec/widgets/resources.conf
WARN  MainThread      gst_metadata_slave_process_protocol Oct 04 15:31:20  Starting Slave-6 on unix:/tmp/elisa-metadata--KxSpf.socket launching elisa.plugins.gstreamer.amp_slave.run_slave
(Slave-6 stdout) (elisa/plugins/amp/master.py:54)
WARN  MainThread      gst_metadata_slave_process_protocol Oct 04 15:31:20  /usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
(Slave-6 stderr) (elisa/plugins/amp/master.py:57)
WARN  coherence                   Oct 04 15:31:36  Coherence UPnP framework shutdown (coherence/base.py:423)
WARN  MainThread      twisted                     Oct 04 15:31:36  A twisted traceback occurred. (twisted/internet/defer.py:402)

Twisted traceback:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 191, in addCallback
    callbackKeywords=kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 182, in addCallbacks
    self._runCallbacks()
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 317, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/lib/python2.5/site-packages/elisa/core/application.py", line 470, in interface_controller_stopped
    manager_deferreds.append(defer.maybeDeferred(manager.stop))
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 107, in maybeDeferred
    result = f(*args, **kw)
  File "/usr/lib/python2.5/site-packages/elisa/core/input_manager.py", line 77, in stop
    self._poll_call.stop()
  File "/usr/lib/python2.5/site-packages/twisted/internet/task.py", line 85, in stop
    assert self.running, ("Tried to stop a LoopingCall that was "
exceptions.AssertionError: Tried to stop a LoopingCall that was not running.

WARN  coherence                   Oct 04 15:31:37  Coherence UPnP framework shutdown (coherence/base.py:423)
Segmentation fault

```
It gets even more bizarre when I start following tutorials and attempting to configure things. A lot of things seem to be different with my elisa installation compared to those of the recent past. The first thing I attempted to do was follow [this tutorial](http://sidrit.wordpress.com/2008/08/09/configuring-windows-media-center-remote-control-for-elisa-on-ubuntu-804/), written all of two months ago.

The first difference is that ~/.elisa seems to have been deprecated in favour of ~/.elisa-0.5. Inspecting this directory, the closest I can find to a configuration file seems to be elisa_0_5_6.conf. Changing this does seem to have an effect so I guess this is the new location for the elisa.conf file, for me at least.

Following the above tutorial, I came a cropper when attempting to run the following command:
```

sudo cp elisa.lirc /usr/share/pyshared/elisa/plugins/lirc_plugin/data/lirc/

```
There is no lirc_plugin directory in /usr/share/pyshared/elisa/plugins/, only an lirc directory. Continuing on with the tutorial, when I continued I found that my elisa_0_5_6.conf file contained no reference to any lirc_rc parameter. The closest I could find was the following parameter, which was originally pointing at streamzap.map.
```

# Path to the file containing the lircmapping
input_map = '/home/stephen/.lirc/elisa'

```
Abandoning this tutorial I looked at [this site](http://jaykinzer.blogspot.com/2008/02/setting-up-remote-control-lirc.html) instead, which seemed to make a lot more sense. Mythbuntu-lircrc-generator generated the following file for me:

~/.lirc/elisa
```

begin
    remote = mceusb
    prog = elisa
    button = Play
    config = toggle_play_pause_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = Right
    config = move_right_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = OK
    config = activate_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = Power
    config = close_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = Mute
    config = toggle_mute_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = VolDown
    config = decrement_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = Rewind
    config = seek_backward_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = Stop
    config = stop_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = Up
    config = move_up_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = VolUp
    config = increment_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = Down
    config = move_down_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = Pause
    config = pause_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = Enter
    config = activate_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = Forward
    config = seek_forward_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = Home
    config = toggle_menu_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = Red
    config = toggle_fullscreen_key
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = elisa
    button = Left
    config = move_left_key
    repeat = 0
    delay = 0
end

```
I edited elisa_0_5_6.conf to point at the latter file, as indeed it still does. However as you can see from the console output printed earlier, elisa seems to choke on the format of this file.

Part of elisa's console output:
```

WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'mceusb'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'elisa'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'Play'. (elisa/plugins/lirc/lirc_input.py:165)
WARN  MainThread      lirc_input                  Oct 04 15:31:11  Don't know key 'toggle_play_pause_key'. (elisa/plugins/lirc/lirc_input.py:165)

```
Searching round a bit, the only clue I could find was [this thread](https://elisa.fluendo.com/forums/viewtopic.php?id=651) which seems to hint at a completely different format of lirc configuration file, but one that I couldn't work out from just that thread.

Which leaves me approximately here. No variation of the above lirc config looks likely to work, despite the variety of internet tutorials and forum hints which point in that direction. Does anyone have any idea what's going wrong, and what the current state of the art is with regards to how elisa.conf should look, how it should reference an lirc configuration file, what that configuration file should look like and where it should all live?

For reference, my complete ~/.elisa-0.5/elisa_0_5_6.conf:
```

[general]
version = '0.5.12'
install_date = '2008-09-07'
resource_providers = ['amazon.resource_provider:AmazonResourceProvider', 'discogs.discogs_resource:DiscogsResource', 'database.media_scanner:MediaScanner', 'weather.report_provider:WeatherReportProvider', 'base.local_resource:LocalResource', 'youtube.resource_provider:YoutubeResourceProvider', 'shoutcast.shoutcast_resource:ShoutcastResource', 'flickr.resource_provider:FlickrResourceProvider', 'wmd.wmd_resource:WMDResource', 'filtered_shares.filtered_shares_resource:FilteredSharesResource', 'coherence.coherence_resource:CoherenceResource', 'coherence.upnp_resource:UpnpResource', 'smbwin32.smbwin32_resource:SmbWin32Resource', 'elisa_updater.resource_provider:UpdaterResourceProvider', 'ipod.ipod_resource:IpodResource', 'hal.hal_resource:HALResource', 'avahi.avahi_resource_provider:AvahiResourceProvider', 'daap.daap_resource_provider:DaapResourceProvider', 'search.search_metaresource_provider:SearchMetaresourceProvider', 'yesfm.yesfm_resource:YesfmResource']
metadata_providers = []
service_providers = ['coherence.coherence_service:CoherenceService', 'osso.osso_service:OssoService', 'gnome.gnome_screensaver_service:GnomeScreensaverService', 'database.dbus_service:DatabaseDBusServiceProvider']
input_providers = ['winremote.streamzap_input:StreamzapInput', 'lirc.lirc_input:LircInput']
frontends = ['frontend1']
# database connection string. see https://storm.canonical.com/Manual
database = 'sqlite:/home/stephen/.elisa-0.5/elisa.db'
user_id = '49294'

[frontend1]
frontend = 'pigment.pigment_frontend:PigmentFrontend'
theme = 'elisa.plugins.poblesec'
controller_path = '/poblesec'
touchscreen = '0'
use_gtk = '0'
window_width = '0'
headless = '0'
start_fullscreen = '1'

[directories]
video = [u'/raid/Video']
pictures = [u'/raid/Pictures']
music = [u'/raid/Music']
[database.media_scanner:MediaScanner]
# the delay (in seconds) between processing two files
delay = 0.10000000000000001
[weather.report_provider:WeatherReportProvider]
# The URL where to get METAR data from
base_url = 'http://weather.noaa.gov/pub/data/observations/metar/decoded'
[gnome.gnome_screensaver_service:GnomeScreensaverService]
# Block the Screensaver. Available modes are:   * 1 : block on playing only  *
# 2 : block from the start to the end, use this, if you are only using remotes,
# on which the screensaver is not reacting * else: do not block!
blocking_mode = 1
[shoutcast.shoutcast_resource:ShoutcastResource]
genres = ['Alternative', 'Hardcore', 'Industrial', 'Punk', 'Blues', 'Folk', 'Classical', 'Country', 'Electronic', 'Ambient', 'House', 'Trance', 'Techno', 'Hiphop', 'Jazz', 'Latin', 'Pop', 'Metal', 'Rnb', 'Classic', 'Contemporary', 'Funk', 'Gospel', 'World', 'Reggae', 'Instrumental']
decades = ['50s', '60s', '70s', '80s', '90s']
[lirc.lirc_input:LircInput]
# the lirc deamon device
device = '/dev/lircd'
# Path to the file containing the lircmapping
input_map = '/home/stephen/.lirc/elisa'
[poblesec.poblesec_browser_controller:PoblesecBrowserController]
home = '/poblesec/sections_menu'
[search.search_metaresource_provider:SearchMetaresourceProvider]
# The default searcher is the searcher that is always asked first for the
# search result and fills the reference model with data
default_searcher = 'DBSearcher'
[yesfm.yesfm_resource:YesfmResource]
# the login key against the API. please use the GUI to perform a User-Password
# Login
userkey = ''
[poblesec.main:PoblesecController]
# Whether or not to allow the user to  remove/hide videos/tracks/photos
enable_remove = '0'
# what to display in the top-right corner of the viewport. Two modes available:
# "desktop" and "embedded". In "desktop" we show the minimize/maxmimize/close
# buttons and in "embedded" we show only an home button
viewport_buttons_mode = 'desktop'

```
Thanks in advance for any help.

---

### Post by Dustout on 2008-11-12
I am having the exact same issue as you, still haven't found a solution but when I do I'll be sure to add it to this topic :)

---

### Post by deadland on 2009-01-24
I have the same problem with 0.5.24.1. Any ideas?

---

### Post by lzap on 2009-03-16
The very same here. Any suggestions?

---

### Post by lzap on 2009-03-16
Maybe this help: [http://elisa.fluendo.com/wiki/Docs/RemoteControls](http://elisa.fluendo.com/wiki/Docs/RemoteControls)

---

