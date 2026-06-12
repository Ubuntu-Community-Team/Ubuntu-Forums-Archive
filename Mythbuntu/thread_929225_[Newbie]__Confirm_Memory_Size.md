---
title: "[Newbie]  Confirm Memory Size"
date: 2008-09-24
forum: Mythbuntu
---

### Post by ptmuldoon on 2008-09-24
I completely apologize if I'm in the wrong forum, as I am just getting started with both Mythbuntu and Linux in general, but am also building an x64 bit system.

I've started assembly on a HTPC, hoping to use Mythbuntu as the 'main' OS.  The primary system specs are.

Intel E8400 3.0ghz processeor
DFI bloodiron board
8GB of OCZ DDR2 memory

For now, I'm just doing basic testing on a spare 240gig drive till my primary drives arrive for a raid setup.  But I've setup a triple Boot with WinXP, Vista, and Mythbuntu.  So I know my way around and pc and windows some, just getting started with Mythbuntu and Linux in general.

So, all that said....  How can I simply confirm in mythbuntu that I am seeing my correct processor and full 8gig memory specs?  I'd like to eventually OC the processor some, but for now, just want to make sure its seeing the default.  Once I'm sure of that, I think I can begin diving in more to Mythbuntu.

Thanks
pt

---

### Post by soxs on 2008-09-24
for cpu
```
cat /proc/cpuinfo
```
for cpu
```
cat /proc/meminfo
```


Note: this shows a very detailed spec of your CPU/MEMORY

For the common use, use free (with m switch to show everything in MiB):
```
free -m
```

Note: You won't see Full 8 GiB (aka 8192MiB), the kernel and some other stuff neeeds some MiBs of ram aswell which will never be touable by the system.
E.g. I have a 4 GiB DDR2 RAM System and freee -m reports 3960 MiB of availiable RAM.

Note: Another option which wastes your ram is your BIOS. It may have (mine does not) have a "Memory Remapping"-switch, turn it on. This will increase your useable memory by ~60-120 MiB (as my castrated BIOS doesn't have that shiny option of glory, I am forced to "waste" 60MiB of RAM)

Use the thank button if you feel like ;-)

---

### Post by Sef on 2008-09-24
> for cpu
     Code:
     cat /proc/memory 
The command for memory is incorrect.   It should be ```
cat /proc/meminfo
```


> I completely apologize if I'm in the wrong forum, as I am just getting started with both Mythbuntu and Linux in general, but am also building an x64 bit system.

I've started assembly on a HTPC, hoping to use Mythbuntu as the 'main' OS.  T

No worries.  I just moved you to the mythbuntu forum since it would be more helpful to you with Mythbuntu problems.

---

### Post by soxs on 2008-09-25
> **Sef said:**
> The command for memory is incorrect.   It should be ```
cat /proc/meminfo
```




No worries.  I just moved you to the mythbuntu forum since it would be more helpful to you with Mythbuntu problems.

Oh, well.. I actually wanted to write meminfo *g*

-> Edited according

---

### Post by ptmuldoon on 2008-09-25
Thanks for the excellent great help.   I'm sure I'll be in here a lot going forward.  

But to perhaps curtail the asking of a 1,000+ questions, I can across this guide here.  I know its technically for Ubuntu, and not Mythbuntu, but it should be pretty good to start with it.

But does anyone know if its printable?  A pdf of that help guide would be pretty beneficial.

[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

---

### Post by soxs on 2008-09-29
go and mark as <solved> (top right, thread tools, only the creator, you can do that)

---

