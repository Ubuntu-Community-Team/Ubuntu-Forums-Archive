---
title: "skype resolution only 320x200"
date: 2012-10-18
forum: Multimedia Software
---

### Post by kridybel on 2012-10-18
Hi,

The resolution of the videos sent from my asus eee pc is only 320 x 200. The os is xubuntu 12.04. Skype version 4.0.0.8

I have added 

<Video> 
 <CaptureHeight>480</CaptureHeight> 
 <CaptureWidth>640</CaptureWidth> 
</Video>

to the /home/(User)/.Skype/(YourUserName)/config.xml 

but no avail.


Here are some specs of my 1011 px:
```
kris-1011px               
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2004MiB
     *-cpu
          product: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.12.10
          serial: 0001-06CA-0000-0000-0000-0000
          size: 1667MHz
          capacity: 1667MHz
          width: 64 bits
```

---

