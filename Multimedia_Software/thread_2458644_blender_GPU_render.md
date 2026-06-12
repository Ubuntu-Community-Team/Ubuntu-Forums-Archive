---
title: "blender GPU render"
date: 2021-03-01
forum: Multimedia Software
---

### Post by tangierian on 2021-03-01
hello everyone hope you guys doing ok, straight forward to it trying to use blender but i see "no compatible GPUs found on path tracing cycles will render oon the CPU". tested it in windows 10 all works fine.installed the proprietary nvidia driver on ubuntu but still nothing if anyone know what's going on pls help GPU : 1070 Ti

---

### Post by CelticWarrior on 2021-03-01
Which driver version have you installed and how?
Have you disabled Secure Boot in UEFI?

---

### Post by tangierian on 2021-03-01
> **CelticWarrior said:**
> Which driver version have you installed and how?
Have you disabled Secure Boot in UEFI?

tried 460 and 450 from additional drivers in software and update no change
and what you meant by disabling secure boot in UEFI ?

---

### Post by CelticWarrior on 2021-03-01
I mean the Secure Boot feature in the motherboard's firmware (UEFI) that many wrongly refer to as "BIOS".
That feature prevents loading unsigned drivers like Nvidia's even if correctly installed. That would explain why Blender is complaining.

---

### Post by tangierian on 2021-03-01
> **CelticWarrior said:**
> I mean the Secure Boot feature in the motherboard's firmware (UEFI) that many wrongly refer to as "BIOS".
That feature prevents loading unsigned drivers like Nvidia's even if correctly installed. That would explain why Blender is complaining.

ok will try later and let you know thx

---

### Post by tangierian on 2021-03-02
> **CelticWarrior said:**
> I mean the Secure Boot feature in the motherboard's firmware (UEFI) that many wrongly refer to as "BIOS".
That feature prevents loading unsigned drivers like Nvidia's even if correctly installed. That would explain why Blender is complaining.

i went to the BIOS i found no secure boot only fast boot options for win8.1 and are disabled BTW motherboard Z87Mpower

---

### Post by CelticWarrior on 2021-03-03
Not all firmwares call Secure Boot by its name. In many it's "OS selection" or similar, where "Other", "Linux", "Android", ... means Secure Boot OFF and "Windows 8" or "Windows 10" means Secure Boot ON. 
Please check your user's manual.

EDIT:
I just did your homework and it's in Advanced > Windows 8 feature. It should be disabled. Or, keep the "Windows 8 feature" enabled and then you'll have a sub-menu Secure Boot > Secure Boot control where it can be disabled.

Also in Boot > Boot Mode Select > UEFI only.

Also in Security > Trusted Computing set TPM to disabled.

---

### Post by tangierian on 2021-03-05
> **CelticWarrior said:**
> 
I just did your homework and it's in Advanced > Windows 8 feature. It  should be disabled. Or, keep the "Windows 8 feature" enabled and then  you'll have a sub-menu Secure Boot > Secure Boot control where it can  be disabled.

tried to attach some pictures but site seems doesn't let me anyway

it was disabled but when i went there and turned it on i got the secure boot option


when i enter secure boot i wasn't able to enable the support options for it  but anyway you said we don't need it on 

> **CelticWarrior said:**
> 
Also in Boot > Boot Mode Select > UEFI only

UEFI was on , there is two options UEFI or UEFI+LEGACY and only UEFI was there

> **CelticWarrior said:**
> 
Also in Security > Trusted Computing set TPM to disabled.

in security there is no "Trusted Computing" but there is some key management 


and while i was checking i left fast boot MSI on 


now  i can't even get to the bios when i turn on computer it directly goes  to windows drive i got dual boot windows on one drive and ubuntu on  another will try figure out how to get into bios again tried F11/DEL buttons +20 times (hold/fast clicks )nothing it goes directly to win10

---

### Post by tangierian on 2021-03-05
ok nvm i was able to load to bios while restarting win10 while pressing shiftkey 

when i turn on windows 8.1 features i get option called Internal GOP configuration on side it give details "manages the onboard graphics output protocol (GOP)"

it says

IGFX Driver version
N/A.

---

