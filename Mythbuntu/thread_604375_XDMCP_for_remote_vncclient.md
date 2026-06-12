---
title: "XDMCP for remote vncclient"
date: 2007-11-06
forum: Mythbuntu
---

### Post by pasta514 on 2007-11-06
I'm looking to use remote desktop to access my backend box.

Looks like I need to enable XDMCP, but the istructions say
> 1. Enable XDMCP
System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"


This menu does not exist in mythbuntu (or am I just blind?) :confused:

I have vncserver running and can get a minimal X screen on my windoze machine using tightVNC viewer

 Do I need XDMCP enabled? If so, how to do so in mythbuntu?

Is VNC the same/similar to LTSP?  Am I on the right track? 

Thanks,

---

### Post by njparton on 2007-11-06
VNC and XDMCP are different.

VNC is a screen sharing solution, XDMCP is a way of logging on to the X server remotely.

I use the latter rather than VNC as it saves installing extra servers etc.

I don't use mythubuntu so I can't help you directly, but I would suggest delving into XDMCP a bit more and forgetting about VNC.

If you want to log into mythubuntu from Windows, then I find Xming an excellent Xclient.

---

### Post by pasta514 on 2007-11-06
Thanks, and how are XDMCP and LTSP related?  Will I need to use both or are they independent?  Looks like I need both, but wanted to check.

---

### Post by njparton on 2007-11-06
LTSP - no idea.

I just log onto X remotely

---

### Post by pasta514 on 2007-11-07
Thank you again.

I followed these instructions
[https://help.ubuntu.com/community/VNC#head-3c64771b3e130cde605dade8868ad840f5992be1](https://help.ubuntu.com/community/VNC#head-3c64771b3e130cde605dade8868ad840f5992be1)
which is getting me closer, but I'm not all the way there yet.

I was discouraged to attempt the XDMCP way because of this
[http://ubuntuforums.org/showthread.php?t=565383&highlight=vnc+client](http://ubuntuforums.org/showthread.php?t=565383&highlight=vnc+client)
 and also unable to figure out how to enable it from the command line.

---

