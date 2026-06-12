---
title: "Diskless Server - Build Image"
date: 2009-01-25
forum: Mythbuntu
---

### Post by stevedaniels on 2009-01-25
Hi,

I installed Ubuntu 8.10 i386 Desktop last week and subsequently installed mythbuntu on it. Everything is running pretty well (apart from running mythfrontend as non-root causes it to squeeze two mangled copies of the screen side-by-side on one monitor, great!).

I've now tried to deploy a diskless client, but I'm having a problem where when I click on the "Build Image" button on the Diskless Server page, nothing happens, at all. Watching top provides little insight.

Does anyone know what commands I should run manually to replicate the process this button should carry out?

[Update]
When running mythbuntu-control-centre from the command line I get this:

> 
steve@terra:~$ mythbuntu-control-centre 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 1803, in on_diskless_server_install_toggled
    self.diskless_server_dhcp.set_activce(True)
AttributeError: 'gtk.CheckButton' object has no attribute 'set_activce'
SSSSSSSSSSSS




Thanks,

Steve Daniels

---

### Post by stevedaniels on 2009-01-25
I fixed the line in /usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py so now no errors appear when opening mythbuntu-control-centre. This doesn't fix my problem where clicking "Build Image" results in no apparent action.

Is there the ability to add verbosity to mythbuntu-control-centre?

Thanks,

Steve Daniels

---

### Post by laga on 2009-01-26
What version of mythbuntu-control-centre are you running?

---

### Post by stevedaniels on 2009-01-26
Hi,

0.31-0ubuntu1

It also says that's the latest in synaptic.

Thanks,

Steve Daniels

---

