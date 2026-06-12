---
title: "Question : s/pdif, why won't you work?"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by Maximilian&quot; on 2006-10-22
Hi fellow ubunters!

I have this little sound issue that I'd like to get in my "finished basket"
Im gonna make this a long thread with all the info I think you will need to get a grip on the situation. 

I've built a HTPC computer and one of big things are audio and in this case digital audio to my receiver so I can get Dolby Digital and DTS. I do have audio via the usual headphone jackets and such but can't get out put on the s-pdif. I know people solving this problem with unmuting the s-pdif in alsamixer but my problem is that I don't even have a option in alsamixer for s-pdif thus making the unmute impossible. My hardware spec are following.

Gigabyte K8N51PVM9-RH (nForce 430) 
Athlon64 3500+
Sound are from the nForce 430 Chipset, Alsa reports RealTek alc880.
The s-pdif connector is on a optional bracket that I've installed that has
1 Coaxial and 1 optical. I'm using the optical output.

Im running on Ubuntu edgy with alsa-base 1.0.11 drivers.

Running the aplay -l in terminal gives me.
card 0: NVidia [HDA NVidia], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

No digital so it seems, thou I know very well that I have a output for it and it's implented into the nForce 430 chipset. 
I was asking around in the IRC #ubuntu but that resolved into a format and reinstall of ubuntu.

lspci -v 
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Giga-byte Technology Unknown device a102
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 209
        Memory at f5000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

I don't know if I have to enable s-pdif in anyway in linux. It's maybe something so easy that only editing a config file of some sort to get it to detect my s-pdif out. Mabybe installing a newer version of the alsa-base? Saw that there is a version 1.0.13 out. I have as I wrote further up version 1.0.11 installed. 

If you know what to do, please help me so I in a close future can start using this pc as a HTPC as the puropse was from the beginning.

(next part is getting my VFD display to work.. but first sound :))

---

### Post by SP8472 on 2006-10-22
download aumix.probably wont show up in the menu,if not run /usr/bin/aumix.

open aumix,it has the digital control,and slide the Igain up too.
hope that helps.worked on my alc 850 on nvidia sli intel chipset

---

### Post by Maximilian&quot; on 2006-10-22
nope.. that didn't show the s-pdif bar.. I don't think that the system even detects that I have spdif.. I have lots of ? and 0 solutions.. not fun ](*,)

---

### Post by Maximilian&quot; on 2006-10-23
bump!

---

### Post by jaripetteri on 2006-11-01
have you find solution yet?

---

### Post by Maximilian&quot; on 2006-11-01
Well! I have been told that a fix has been added to the newer versions of alsa-drivers. The hg release but maybe even the 1.0.13 version. Tried to install these but it seems like the only version that work to compile for my computer is the 1.0.12.. So I have to wait or buy another soundcard. I would guess another soundcard.

---

