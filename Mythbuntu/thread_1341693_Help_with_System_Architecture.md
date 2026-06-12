---
title: "Help with System Architecture"
date: 2009-11-30
forum: Mythbuntu
---

### Post by atjensen11 on 2009-11-30
Hello,

I am very new to MythUbuntu, but I am not new to Linux.  I have been wanting to build a MythTV setup for some time and the project has finally boiled to the top of my list.

I am looking for help in designing a system and then eventually procuring components.

I currently have a Dell Precision 670.  From a hardware perspective, the workstation has 2 3.0 GHz Intel dual core processors; four cores total.  This workstation is actually a Xen Dom0 machine built on Debian Lenny.  However, I think it might make a good candidate to host a Mythbuntu backend system within a DomU.  Other DomUs are responsible for web services (DNS, email, web) and a file server.  If I were to use this machine for the backend, I believe I would only need to add a video capture card.

Any suggestions on this approach?

If this setup wasn't ideal, I have a Dell Optiplex 260 that is lying around or I could build a dedicated system for a reasonable price too.

I have a lot of other questions about remote controls and front end system hardware, but I think figuring out the backend first should probably take priority.

Please feel free to make recommendations on this potential setup.

---

### Post by williammanda on 2009-11-30
> **atjensen11 said:**
> Hello,

I am very new to MythUbuntu, but I am not new to Linux.  I have been wanting to build a MythTV setup for some time and the project has finally boiled to the top of my list.

I am looking for help in designing a system and then eventually procuring components.

I currently have a Dell Precision 670.  From a hardware perspective, the workstation has 2 3.0 GHz Intel dual core processors; four cores total.  This workstation is actually a Xen Dom0 machine built on Debian Lenny.  However, I think it might make a good candidate to host a Mythbuntu backend system within a DomU.  Other DomUs are responsible for web services (DNS, email, web) and a file server.  If I were to use this machine for the backend, I believe I would only need to add a video capture card.

Any suggestions on this approach?

If this setup wasn't ideal, I have a Dell Optiplex 260 that is lying around or I could build a dedicated system for a reasonable price too.

If the backend your wanting to use is going to serve one frontend than a basic intel core 2 duo will work. With that said obiviously you will need to increase the cpu horse power for more frontends. Also if you use a vdpau supported nvidia video card that will figure into the cpu load since the video gpu will take over some of the cpu load.

> I have a lot of other questions about remote controls and front end system hardware, but I think figuring out the backend first should probably take priority.

There is a large number of remote controls that can be used. Refer to:

[http://www.lirc.org/]("http://www.lirc.org/")

and

[http://ubuntuforums.org/showthread.php?t=566529]("http://ubuntuforums.org/showthread.php?t=566529")

---

