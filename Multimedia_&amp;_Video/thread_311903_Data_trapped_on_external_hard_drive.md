---
title: "Data trapped on external hard drive"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by sp0nge on 2006-12-03
Once upon a time not too long ago, I was dependant upon window$ as are so many in the world today. When I made the final leap, I failed to think through all the details and now am faced with the following issue:

My desktop PC has a 300GB external hard drive which stores all my movies, music, and other various data. The hard drive was formatted in NTFS which, of course, works seamlessly with window$. The desktop soon crashed and died on me and now all I have is my laptop running Dapper (although I do have a VM winXP partition that works great).

The challenge I am facing is extracting the data from the HDD so I can format it to FAT32. I've tried to access the HDD normally and apparently can not even read it at the present moment. I also rebuilt the Virtual Machine settings to include USB devices in hopes of accessing the HDD through the winXP partition but this doesn't work either. 

Once again I turn to the pages of the forums and find little solace. Any input here to help me figure this out? I know I'm not the only one to face this debacle.

---

### Post by an.echte.trilingue on 2006-12-03
There is a program called libntfs9 that will allow you to do what you have described.  Beware, ntfs write support is very, very if-y.

There is also a [page about ntfs]("https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite") in the wiki.

Take care, 

-mat

---

### Post by sp0nge on 2006-12-03
I don't know that I necessarily need to write. I just want to move the data off this external HD so I can re-format as FAT32 (to access from either OS).

I searched synaptic for libntfs9 to no avail. When I google this, I get information as to what it is and is supposed to do, but no detail as to how or where to get it?!

If I am able to get libntfs9, will this allow me to access the external HD and move the data off the device so I can re-format it?

---

### Post by an.echte.trilingue on 2006-12-04
You need to read the [ page about ntfs (click this link)]("https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite") in the wiki.  I might not have the same version of Ubuntu as you.

Also, you can search synaptic for "ntfs" and read the summaries of the programs it returns.  Usually an app that will allow you to read ntfs will sayso in the summary.  Be sure you have universe and multiverse enabled, I am not sure which repository the library is in.

Take care, 

-mat

---

