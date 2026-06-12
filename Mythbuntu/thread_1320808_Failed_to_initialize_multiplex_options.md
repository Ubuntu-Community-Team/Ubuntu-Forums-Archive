---
title: "Failed to initialize multiplex options"
date: 2009-11-09
forum: Mythbuntu
---

### Post by SiHa on 2009-11-09
Started getting these yesterday, and nothing's recording.

Did a Google, and turned up this on the Gossamer Threads list:
> > I've pasted a bit of the output from mythbacked below. Its the "Error: 
> Failed to initialize multiplex options" line that concerns me. 
> 
> Does anyone know what this error is? Or, more importantly I suppose, how 
> I fix it? 

Do you have any other capture cards in the system? I've seen this 
error (or extremely similar) when DVB-T and DVB-S cards swapped device 
nodes and the DVB-S card was trying to tune to DVB-T multiplexes... 

Nick 


Almost certainly my problem, as I do have a DVB-T & DVB-S card.

Has anyone got any idea how I can stop this happening? Is this similar to the problem where the remote receivers swap, and I can create a UDEV rule to fix it?

TIA,

Simon

Edit: Confirmed this is the problem. Just run mythtv-setup, and adapter 0 & 1 have swapped. Anyone got any bright ideas please??

---

### Post by ian dobson on 2009-11-09
Hi,

Maybe you could setup hotplug (or what every it's called) so that when it "sees" your DVB-s card it creates a symbolic link from the real device to a fixed name.

Have a look here [http://ubuntuforums.org/showthread.php?t=753434&highlight=python](http://ubuntuforums.org/showthread.php?t=753434&highlight=python) for tips on how to do it.

Regards
Ian Dobson

---

### Post by SiHa on 2009-11-09
Ian, thanks for the quick response, looks very promising!

WAF plummeted this evening, hopefully I can get it back up soon!

Cheers,

Simon

---

