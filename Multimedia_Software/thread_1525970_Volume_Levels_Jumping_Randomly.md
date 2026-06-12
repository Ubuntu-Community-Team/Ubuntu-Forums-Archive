---
title: "Volume Levels Jumping Randomly"
date: 2010-07-07
forum: Multimedia Software
---

### Post by ks07 on 2010-07-07
Hey all.
I am currently troubled with a very annoying problem - the volume level of the PC is jumping higher and lower at random intervals. It makes listening to music very difficult, as at times the music can go from just right to overly loud, just to fall right down so that it is hard to hear. I've only noticed this problem in the past few weeks, and I can definitely say it wasn't an issue in 9.10. This is a fresh install btw, not an upgrade.

Some details:
Using motherboard sound, Realtek HD Audio, iirc. Below is the output of lshw, with the irrelevant parts cut out.
```
ks07-ubuntu
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2
  *-core
       description: Motherboard
       product: M2NPV-VM
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.xx
       serial: 123456789000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS M2NPV-VM ACPI BIOS Revision 0202 (09/22/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fe024000-fe027fff

```

Also, see this link for the output of the ALSA info script: [http://www.alsa-project.org/db/?f=e95bd9539da5cfab15efcf9ea7f050de19164d9c](http://www.alsa-project.org/db/?f=e95bd9539da5cfab15efcf9ea7f050de19164d9c)

Thanks for your time. :popcorn:

---

### Post by lidex on 2010-07-08
Is this a home-built computer? If not, can you provide make/model please?
You do have mismatched alsa components. I would suggest uninstalling any alsa-backports and then 
follow the alsa-upgrade link in my sig to get v. 1.0.23

---

### Post by ks07 on 2010-07-09
> **lidex said:**
> Is this a home-built computer? If not, can you provide make/model please?
You do have mismatched alsa components. I would suggest uninstalling any alsa-backports and then 
follow the alsa-upgrade link in my sig to get v. 1.0.23
Thanks for the reply. The PC is a budget box from Targa, an AN 3400+, [see here]("http://www.targa.co.uk/index.jsp?SID=0&NAV=236&DOC=&PAGE=&PCAT=2&PROD=316&PTUBE=10&PARAMS=undefined&PARAMS2=undefined&SPCAREA=undefined"). It's been upgraded over the years with new memory, gpu, cpu and HDD, so all thats left of the original is the motherboard and case. :p

I uninstalled alsa-backports with --purge and then ran the alsa-upgrade script according to the instructions in the thread. It appears to have worked, and sound works. *However*, after restarting the problem still remains. :( (Although it seems to happen less frequently... although that could just be me)

I have ran the alsa-info script again, in the hope it may shed some light on the problem.
[http://www.alsa-project.org/db/?f=83cab71a17eec9b6c414606239ef220ebce47eff](http://www.alsa-project.org/db/?f=83cab71a17eec9b6c414606239ef220ebce47eff)

---

### Post by lidex on 2010-07-09
Any chance of a bios update?
```
version: ASUS M2NPV-VM ACPI BIOS Revision 0202 (09/22/2006)

```

I'm really not too keen on this error message:
```
[  929.656030] ALSA hda_codec.c:385: hda_codec: invalid CONNECT_LIST verb 12[2]:2100

```

How many audio jacks on the board?

---

### Post by ks07 on 2010-07-09
> **lidex said:**
> Any chance of a bios update?
```
version: ASUS M2NPV-VM ACPI BIOS Revision 0202 (09/22/2006)

```I'm really not too keen on this error message:
```
[  929.656030] ALSA hda_codec.c:385: hda_codec: invalid CONNECT_LIST verb 12[2]:2100

```How many audio jacks on the board?
I've been pondering over a bios update for a while, I tried the Asus version but it would not work, turns out I need one from the original manufacturer. I'll give it a go, but I need to use Windows... :sigh:

There are three jacks on the mobo itself, line out, line in and microphone. There's also a pci add-on card with s/pdif thats plugged in to the mobo that came pre-installed.

---

### Post by lidex on 2010-07-09
No guarantees, but you can try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```

---

### Post by ks07 on 2010-07-09
Okay, I've updated the bios (a little scared when presented with a black screen on boot, turns out I had to switch monitor cables :p) and added the given line to the config file. The good news: It seems to have worked! I've played a few songs and have not noticed any volume problems! :KS Thanks very much!

Overview for others who may have this problem:

[LIST=1]
[*]Completely remove any alsa-backports in synaptic
[*]Download, compile and install latest ALSA drivers using the script.
[*]Update bios (! risky, may not be necessary !)
[*]Add 'options snd-hda-intel model=3stack' to the end of /etc/modprobe.d/alsa-base.conf
[/LIST]
Some combination of these steps should solve the problem. Once again, many thanks to lidex for the help. :D

**EDIT:** This process caused part of gstreamer to break, specifically it caused rhythmbox to be unable to play most (weirdly not all) music, because of missing 'autoaudiosink'. This is a known bug that has already been fixed, so I presume using the alsa update script caused this fix to be reset. [Follow this link if you experience this problem for a fix (scroll to the posts about using gconf-editor).]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/442157")

---

### Post by lidex on 2010-07-09
You're welcome. Good job, BTW.

---

