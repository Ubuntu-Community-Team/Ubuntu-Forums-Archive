---
title: "&quot;nvidia-glx-config enable&quot; failed - no GL - now what?!"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by sander marechal on 2005-10-14
Somehow nvidia-glx seems to keep failing for me. Here's what I did:

[list]
[*]I installed a K7 kernel image
[*]I installed nvidia-glx from Synaptic
[*]I installed nvidia-settings from Synaptic
[*]I enter "sudo nvidia-glx-config enable"
[*]Restart -- no OpenGL
[*]I find out from [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia) that I need K7 linux-restricted-modules
[*]I install linux-restricted-modules for K7 from Synaptic
[*]I also add "RenderAccel" "false" to xorg.conf as suggested by the wiki
[*]Restart -- no OpenGL
[*]I read though the "latest nvidia drivers" thread
[*]I see that load "GLcore" and load "dri" need to be commented out. I do so
[*]Restart -- no OpenGL
[*]I post here because I have no idea how to fix this :???: 
[/list]

I have a GeForce 6600 GT card and it worked brilliantly under Hoary. Please help!

Thanks in advance!

--
Sander Marechal

---

### Post by dahli.llama on 2005-10-14
Read through the "Latest Nvidia Drivers" thread closely.  There seems to be a bit more you need to do with your xorg.conf before it will work.

One thing you need to check is make sure that in the Devices section you change the driver from "nv" to "nvidia"

If you're still having problems I can help later today, because I need to do the same thing with my 6600GT.

---

### Post by sander marechal on 2005-10-14
Thanks, the nv<->nvidia thing was what I screwed up. It's all working now!

---

### Post by dahli.llama on 2005-10-14
Good to know.

---

### Post by hone on 2005-10-15
I have this same problem w/ a 6800 GT but I already changed it to nvidia.

---

### Post by kudu on 2005-10-15
I'm having troubles too. I've commented out "GLCore" and "DRI" and changed "nv" to "nvidia". When I try "glxgears" I get the following error message:

"X connection to :0.0 broken (explicit kill or server shutdown)."

and I don't get any read out of fps. What the heck ? I want my nvidia, I need my nvidia!

Help!

kudu

---

