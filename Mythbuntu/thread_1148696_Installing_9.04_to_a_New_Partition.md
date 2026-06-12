---
title: "Installing 9.04 to a New Partition"
date: 2009-05-04
forum: Mythbuntu
---

### Post by SeanOB on 2009-05-04
Hello,

I have an 8.10 frontend (only) machine that's been working great.
Originally I was planning on just skipping the 9.04 release and waiting for MythTV 0.22...  but now I'm tempted with the VDPAU - and having a kernel that natively supports HDMI audio (without manually compiling.)

So...

I'd like to install 9.04 to a new partition - this way I can get everything working at my leisure and still have a frontend for watching TV. I figure that I'll configure grub to boot 8.10 automatically - and manually boot to 9.04 so that I can bring it up.

I was hoping that this installation process would be obvious.  Is it?
Is it as easy as telling the installer gui that I want to create and install the OS to a new partition?

I really don't want to risk breaking my perfectly good 8.10 install. Taking down the entertainment system will greatly affect the WAF!  (Ask me how I know this ;) )


Thanks!

-Sean

---

### Post by superm1 on 2009-05-04
> **SeanOB said:**
> Hello,

I was hoping that this installation process would be obvious.  Is it?

Quite.

> 
Is it as easy as telling the installer gui that I want to create and install the OS to a new partition?

Yeah, more or less

> 
I really don't want to risk breaking my perfectly good 8.10 install. Taking down the entertainment system will greatly affect the WAF!  (Ask me how I know this ;) )
Thanks!

-Sean
There is a small snag with frontend only installs that the backend and mysql aren't getting removed, so you just might need to remove them after the install gets done.   Otherwise, should be very straightforward.

---

### Post by dsauter on 2009-05-13
<cut>

---

