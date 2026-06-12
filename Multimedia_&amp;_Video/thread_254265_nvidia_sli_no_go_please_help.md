---
title: "nvidia sli no go please help"
date: 2006-09-09
forum: Multimedia &amp; Video
---

### Post by fokuslee on 2006-09-09
i have gv-3d1 which is a dual 6600gt gpu card with 256mb of memory it is pluged into ONLY ONE pci-express slot but sli works fine under window xp
here is what i have now 
ubuntu dapper 
vanilla kernel 2.6.17.11 k8
nvidia 64bit binary driver

here is the problem
nvidia-settings do not show slihud option 
infact no mention of sli at all
-i tried nvidia-xconfig --sli="auto"/afr/sfr/on/off etc  

here is a print out from lspci

fokuslee@fokuslee-linux:~$ lspci | grep -i vga
0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

fokuslee@fokuslee-linux:~$ lspci -t
-[00]-+-00.0
      +-01.0
      +-01.1
      +-02.0
      +-02.1
      +-04.0
      +-06.0
      +-07.0
      +-08.0
      +-09.0-[05]--+-07.0
      |            \-0b.0
      +-0a.0
      +-0b.0-[04]--
      +-0c.0-[03]--
[COLOR="Red"]      +-0d.0-[02]----00.0
      +-0e.0-[01]----00.0[/COLOR]
      +-18.0
      +-18.1
      +-18.2
      \-18.3

the entire Xorg.0.log is available at [http://paste.ubuntu-nl.org/23239](http://paste.ubuntu-nl.org/23239) 

now for questions:
does this mean there is no Root Bridge and bus 02 is incorrectly connected at the base of the device tree.
If it is so then is there a problem with the kernel i compiled? 
or is it that the current kernel does not support my hardware setup? 

i am a total linux nub only used ubuntu 3 days so please explain as much as you can 
any input is more than welcome 
pleasesss help ](*,)

---

### Post by fokuslee on 2007-01-03
I solved it by getting two 7600gt and running sli off of that.
my wallet is bleeding 
: ( 
someone plz add gv-3d1 to unsupported hardware

---

