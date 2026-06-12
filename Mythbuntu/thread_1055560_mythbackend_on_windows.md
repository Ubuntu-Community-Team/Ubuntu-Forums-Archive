---
title: "mythbackend on windows"
date: 2009-01-30
forum: Mythbuntu
---

### Post by ~~MAINFRAIME²~~ on 2009-01-30
Are there precompiled windows binaries of the mythbackend? (Is this even working?)

Or is there another way of running the backend on a windows machine with a dvb-s tuner?

---

### Post by ian dobson on 2009-01-31
Hi,

Mythbackend doesn't run on windows as linux has a totally different method to access tuners as windows.

There is a windows frontend in process, which is much easier to do as both windows and linux support OpenGL for graphic display.

Regards
Ian Dobson

---

### Post by ~~MAINFRAIME²~~ on 2009-01-31
Yeah I know windows is totally different but in the mythtv wiki there is a windows port article
> Now that the frontend is reliable, we can start to see about getting the changes necessary to get MythBackend.exe to connect to a Tuner!
[Windows Port - MythTV](http://www.mythtv.org/wiki/Windows_Port)

Has anyone tried this yet, is it already working?


A VM would be another possibility but how am I supposed to get the tuner in it?


I don't need a frontend for windows I use XBMC for that.

---

### Post by ian dobson on 2009-02-01
Hi,

I don't think the VM trick would work. VM's are all about emulating hardware and unless the VM supports direct access to the hardware (tuner) which goes against the idea of virtualising the hardware.

Maybe one day mythbackend.exe would support access to tuners but looking at how long it's taken to get the frontend working I wouldn't hold my breath :)

Have a look here:- [http://communities.vmware.com/thread/41266](http://communities.vmware.com/thread/41266) an USB tuner "might" work in a VM.

Regards
Ian Dobson

---

