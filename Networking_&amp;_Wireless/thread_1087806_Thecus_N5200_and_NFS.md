---
title: "Thecus N5200 and NFS"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by slyman1973 on 2009-03-05
Ok, I'm an ubuntu noob and know nothing about NFS, and here is my goal. I want to permanently mount 2 folders on my Thecus N5200 that has NFS enabled, on my ubuntu machine. My overall goal is to have virtual machines stored on my thecus box via VMware's server Datastore settings. Is there a way to do that does not involve a million lines of data entry at the terminal, and editing a million files. Please help!   

Thanks

Doug

---

### Post by slyman1973 on 2009-03-09
Well I managed to mount a NFS folder from my Thecus box on my client computer using the following command:

sudo mount 192.168.0.100:/raid0/data/Main /mnt/Main


but I have no rights to that folder, even though on the thecus box I do have administrator rights. Any thoughts?

---

