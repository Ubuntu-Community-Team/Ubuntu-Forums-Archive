---
title: "Diskless with mixed architectures"
date: 2008-05-06
forum: Mythbuntu
---

### Post by ares01590 on 2008-05-06
I can't tell from the documentation and forum whether the following is supported in the MCC.

I have a combined FE/BE pentium 4 machine, and I intend to setup a diskless amd64 FE-only machine.  The docs say that mixed architecture is not OK, then says some thing like its actually OK if the server is amd64.  I'm the opposite, however.

Thanks,

David.

---

### Post by tgm4883 on 2008-05-06
You won't be able to build the amd64 image on an i386 machine

---

### Post by MaindotC on 2008-05-06
Is FE/BE Front End / Back End and is MCC micro computer controller?

---

### Post by laga on 2008-05-07
MCC stands for 'mythbuntu control centre'.

It is still possible to create the amd64 image on your client and then copying it to the i386 server. You could use an amd64 live disk and some nfs shares for /opt/ltsp/ and /var/lib/tftpboot. Figuring out how it's done is left as an exercise for the reader ;)

Of course, just using i386 might work just as well.

---

### Post by ares01590 on 2008-05-07
Bummer.  I was afraid that would be the problem.

So do you think I would be better off just not telling MCC that I want the P4 FE/BE to be a diskless server.  Or should I set up as a i386 diskless server and mess around afterwards to make the amd64 image?

I assume that building an amd64 image on an i386 machine is a larger problem than just a mythbuntu restriction?  (this is my first foray in amd64 PCs).

Thanks,

David.

---

### Post by tgm4883 on 2008-05-07
> **ares01590 said:**
> Bummer.  I was afraid that would be the problem.

So do you think I would be better off just not telling MCC that I want the P4 FE/BE to be a diskless server.  Or should I set up as a i386 diskless server and mess around afterwards to make the amd64 image?

I assume that building an amd64 image on an i386 machine is a larger problem than just a mythbuntu restriction?  (this is my first foray in amd64 PCs).

Thanks,

David.

You can't build and amd64 image on i386 hardware period.  You could build the image on the amd64 hardware then copy the image over.  That though hasn't been done so there are no instructions to guide you.  In theory it would work though.

You have a few options.
1.  Build the image on amd64 hardware then copy the image over.
2.  Have your amd64 machine boot the i386 image.
3.  Have an amd64 machine be the diskless server.

---

