---
title: "Sound is extremly quiet"
date: 2011-07-29
forum: Multimedia Software
---

### Post by Shadowrain on 2011-07-29
Hello,
despite all volumes in alsamixer are turned up to level 100, the sound in my speaker or earphones is extremely quiet. I can almost hear nothing at all.
Until now I haven't found any solution to this problem in my search, so I hope for suggestions to solve this problem.

---

### Post by aeiah on 2011-07-29
what about pulse audio settings?

---

### Post by Shadowrain on 2011-07-29
I installed pulseaudio, but I fail at understanding how I can see the settings, for example the volume control. 
I found the website for the command line interface at [http://pulseaudio.org/wiki/CLI](http://pulseaudio.org/wiki/CLI), but I still have problems to understand what to do.

When I run ```
pulseaudio
``` nothing happens.

---

### Post by BicyclerBoy on 2011-07-29
Try running (install if necessary)
pavucontrol

---

### Post by Shadowrain on 2011-07-30
In pavucontrol all volumes levels are at 100 percent, but still no change.

---

### Post by ankspo71 on 2011-07-30
Hi,
I'm not an expert on this type of thing, but this sounds like it could be a driver problem, but first try going to System Settings > Multimedia > Phonon;
and check to see if your default preference for 'audio output' works well. If you have multiple choices for 'audio output', find the one that works best and use the 'prefer' and 'defer' buttons to move the best choice to the top of the list.

If that doesn't help anything, go to the 'speaker setup' tab and see of your speaker setup is correct. 

Note that changes to these settings might not take affect until after a reboot.

----

If this ends up being a driver problem then use the following general commands to identify your audio hardware and audo driver in use:

```
sudo lshw -class multimedia
```
```
cat /proc/asound/cards
```
```
cat /proc/asound/card0/codec* | grep Codec
```

Paste the outputs of these commands here to help other people help you solve the problem too.

If your audio driver is an HDA Intel driver, then you can refer to this page:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Hope this helps.

---

### Post by .... on 2011-07-30
The best way to gather info on your sound setup is the alsa-info script: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)
I'm thinking you might need eapd=1 added to your alsa-base.conf to turn on the amp.

---

### Post by Shadowrain on 2011-07-31
It seems to be an driver Problem, because I can't find any change in my multimedia settings helping. By the way, I have no tab for speaker setup.

The output of the commands posted by ankspo71 is:

```

ubuntu@ubuntu:~$ sudo lshw -class multimedia
  *-multimedia            
       description: Audio device
       product: Redwood HDMI Audio [Radeon HD 5600 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:17 memory:f0040000-f0043fff
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:f5e00000-f5e03fff

``````

ubuntu@ubuntu:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf5e00000 irq 22
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0040000 irq 17

``````

ubuntu@ubuntu:~$ cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC269

```
I tried to follow the instructions from your link, to find the best driver for my chipset. I haven't tested all of them yet. My Notebook is a Sony Vaio and it doens't appear in the list.

@... : In my alsa-base.conf there is no entry of 'eapd'.

---

### Post by BicyclerBoy on 2011-07-31
You do realize you have (2) sound-card audio devices ?
You should be able to switch between them in the gnome sound control or pavucontrol.

Do you have (2) devices listed in the "hardware" tab (HDMI audio & mobo HDA) ?

You need to be careful with modprobe.d/*.conf options.
- With multiple soundcards you need to make sure the option refers to correct card.
- need to rebuild the boot image for modeule options to work (update-initramfs)
- difficult to know what options to use..
(Lidex is the undisputed expert)

---

### Post by Shadowrain on 2011-07-31
I found the solution in this post: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/537448](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/537448)

I went to [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)
and downloaded the python script. Then I ran it and went looking for Node[0x19] on the left hand side panel and clicked it. Under "widget control" on the right hand side panel I changed the VREF value from 80 to HIZ.
That worked for me, but I wished I understand, why it worked.
Maybe this will help someone in the future.

Thank you for all your replys.

---

### Post by BicyclerBoy on 2011-08-01
Good for you...

Great program (HDA_analyser) if anyone know how to use it..

Are you running an old 10.04 with no extra alsa ppa's updates ? Because this problem is meant to have been fixed..

---

### Post by Shadowrain on 2011-08-01
I haven't yet updated anything, because when I ask my Package Control Center about updates it says that there are none. And I am not yet comfortable with aptitude.


*Edit*: Now the Package Control Center informed me about bug fixes and security updates. Maybe my problem will be solved after the updates, because its a nuisance that I will have to run the python script every time manually and do as I told.

---

### Post by BicyclerBoy on 2011-08-01
In synaptic package manager you need to hit the "reload" button after any repository changes & to refresh the package cache..
Sounds like you have updates set to manual mode & your package cache is out of date..

I would suggest selecting "proposed updates" but make sure that distribution upgrades is NOT ticked/selected.

---

### Post by Shadowrain on 2011-08-02
Thank you,
I have one last question, because the updates didn't change the fact that I have to use the HDA-Analyser every time:
The only updates I didn't installed are for the kernel. Did you mean that with ppa? I don't know this term.

---

