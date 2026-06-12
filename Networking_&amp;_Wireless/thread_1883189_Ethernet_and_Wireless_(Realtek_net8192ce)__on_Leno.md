---
title: "Ethernet and Wireless (Realtek net8192ce)  on Lenovo IdeaCentre K330"
date: 2011-11-18
forum: Networking &amp; Wireless
---

### Post by dpollen on 2011-11-18
I recently bought a _Lenovo K330_, completely wiped Windows and the recovery partition and tried to install Ubuntu.

Install CDs 11.10, 11.04, 10.10 and Linux Mint all fail to boot to Live CD, halting on the line: 
```
[sde] Attached SCSI removable disk
```

I have managed to get 10.04 to install, but ethernet and wireless is not recognized at all... making the computer somewhat useless.

I have installed **ndisgtk** and added each .inf (Win7,V,XP) in turn from the Windows driver CD, rebooted... no banana.

I managed to find the **rtl8192ce-dkms** deb files and install them... but they too have produced no result.

I desperately need some help to un-brick my computer please! :)

PS: I know, deleting Windows before getting a running Ubuntu installation was a stupid move! :P

---

### Post by dpollen on 2011-11-19
I think the error might be caused by the built-in card readers?

There are 4 of them, and they turn up as drives in 10.04... and the messages say:

```
[sdd] Attached SCSI removable disk
[sdc] Attached SCSI removable disk
[sde] Attached SCSI removable disk
[sdb] Attached SCSI removable disk
```

---

