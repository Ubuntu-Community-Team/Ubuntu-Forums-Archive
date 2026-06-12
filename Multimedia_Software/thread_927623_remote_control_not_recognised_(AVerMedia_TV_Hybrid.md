---
title: "remote control not recognised (AVerMedia TV Hybrid A16AR)"
date: 2008-09-23
forum: Multimedia Software
---

### Post by Peter Wagner on 2008-09-23
I have spent tenth of hours looking around on forums, wikis and documentations for Ubuntu, Linux tv, LIRC in english and Czech, googled anything which came to my mind, installed and deinstalled packages and different lirc control files. I stopped when it came up to compiling kernels etc.

My phenomenology is as follows:

* Me TV and Totem are running, Mythtv offers "Analog tuner" or "DVB tuners 3.x", but no channel scan works.
* dmesg | grep remote is empty
* sudo /etc/init.d/lirc restart is empty (somehow before trying mythtv it yielded three lines: stopping processes-failed, configuring, launching processes-failed)
* control reacts every time the same way, independent on application: three buttons cause a) shutdown screen, b) mute, c) unmute
* irw works (after installation of lircinput), but yields different results than in the Wiki:
193 0 KEY_CHANNELDOWN event6
192 0 KEY_CHANNELUP event6

Is there an analytic way to find out what's going wrong (that means no trial-and-error)?
Is the control rujnning (there are reactions) or not (no trace in the logfile, irw)?

State:
AVerMedia TV Hybrid A16AR
.ircrc file is created with the mythtv tool

sample of the lircd.conf file:
          BACKWARD                 0x40BFA857
          FORWARD                  0x40BF6897
          CAPTURE                  0x40BFE817
          MUTE                     0x40BF28D7
 sample of the .lircrc file (via +input)
begin
    remote = rmfp
    prog = totem
    button = forward
    config = seek_forward
    repeat = 0
    delay = 0
end

---

