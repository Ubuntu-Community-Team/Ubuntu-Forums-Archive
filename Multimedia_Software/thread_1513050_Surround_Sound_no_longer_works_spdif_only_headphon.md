---
title: "Surround Sound no longer works spdif only headphones now"
date: 2010-06-18
forum: Multimedia Software
---

### Post by marcoftheknight on 2010-06-18
On my initial setup I follow the Comprehensive sound guide that is posted on the ubuntu forums because I wanted to get the spdif work Optical out with surround. After a while I was able some how to get it to work and but my headphones would no longer output sound :( so in an effort to get sound back to the headphones I maanged to ruin the the settings for the spdif and now I have some weird problems for example:
Terminal :
~$ gnome-volume-control

** (gnome-volume-control:2162): WARNING **: Connection failed, reconnecting...


TErminal :
-desktop:~$ /usr/bin/asoundconf-gtk
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!
marcoftheknight@marcoftheknight-desktop:~$ 

My question is how can I get spdif back and switch between headphones and spdif. 

I there no way to figure it out how do I purge every file that has to do with sound and recompile. ( THe comprehensive sound guide showed how to purge the alsa utils but that didnt work if someone know why please let me know and if you could explain.)

Thanks

---

### Post by marcoftheknight on 2010-06-19
Is there any sound experts out there I dont really know what to do now Im stuck.

Im thinking may a fresh install of ubuntu might be the answer.

        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:fe024000-fe027fff

  *-multimedia
                description: Audio device
                product: Juniper HDMI Audio [Radeon HD 5700 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:fdefc000-fdeffff

---

