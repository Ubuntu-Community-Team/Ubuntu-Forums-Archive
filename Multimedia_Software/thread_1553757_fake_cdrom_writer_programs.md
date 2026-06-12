---
title: "fake cdrom writer programs"
date: 2010-08-15
forum: Multimedia Software
---

### Post by kennybob on 2010-08-15
Why the heck do all these suedo programs on Ubuntu to write a cd ALL require cdrecord or mkisofs.  If I get a cdrecorder program for Windoze, it writes it, and doesnt depend on if Nero or some other such program is installed. If so, I'd probably just use that.  Are all these suedo writers, just batch programs or shell programs. Doesn't anyone know how to program a decent cdwriter programs without relying on other peoples work?

Sorry if I sound pissed (which I am), and yes, I should try to write a program that I want.

I guess I'm really mad at Ubuntu, which although they have a built in cd writer thru Nautilus, it requires cdrecord and mkisofs, which is no longer installed or able to be installed in Ubuntu. And Brasero also requires the same thing, as does Xcdroast.  Which is why I wish I knew where to turn.

---

### Post by ajgreeny on 2010-08-15
> **kennybob said:**
> Why the heck do all these suedo programs on Ubuntu to write a cd ALL require cdrecord or mkisofs.  If I get a cdrecorder program for Windoze, it writes it, and doesnt depend on if Nero or some other such program is installed. If so, I'd probably just use that.  Are all these suedo writers, just batch programs or shell programs. Doesn't anyone know how to program a decent cdwriter programs without relying on other peoples work?

Sorry if I sound pissed (which I am), and yes, I should try to write a program that I want.

I guess I'm really mad at Ubuntu, which although they have a built in cd writer thru Nautilus, it requires cdrecord and mkisofs, which is no longer installed or able to be installed in Ubuntu. And Brasero also requires the same thing, as does Xcdroast.  Which is why I wish I knew where to turn.
None of those CD writers are "fake" as you describe them.

Have you tried installing brasero?  Though you shouldn't need to; it is installed by default, so I'm not at all certain why you think it depends on packages that are not available.

What exactly are you trying to do that a standard ubuntu system can not do out of the box?

---

### Post by kennybob on 2010-08-15
If you read the post, I said that Brasero also requires the use of cdrecord, I dont know why, but it does. Maybe, because it depends on it like a shell program.

---

### Post by ajgreeny on 2010-08-16
I am not sure why you are getting that error message;  I certainly don't when I burn data disks of mp3s, rather like you seem to be trying to burn at the moment, nor if I make an iso of a number of mp3s.

Is your system a standard Ubuntu desktop setup or have you removed a number of packages that may have contained cdrecord and mkisofs?

I am baffled!  Can you burn anything with brasero at all?

---

### Post by davidogg on 2010-08-16
> **kennybob said:**
> Why the heck do all these suedo programs on Ubuntu to write a cd ALL require cdrecord or mkisofs.  If I get a cdrecorder program for Windoze, it writes it, and doesnt depend on if Nero or some other such program is installed. If so, I'd probably just use that.  Are all these suedo writers, just batch programs or shell programs. Doesn't anyone know how to program a decent cdwriter programs without relying on other peoples work?

Sorry if I sound pissed (which I am), and yes, I should try to write a program that I want.

I guess I'm really mad at Ubuntu, which although they have a built in cd writer thru Nautilus, it requires cdrecord and mkisofs, which is no longer installed or able to be installed in Ubuntu. And Brasero also requires the same thing, as does Xcdroast.  Which is why I wish I knew where to turn.

For years on Windows many CD recording apps required Adaptecs ASPI layer, even on SCSI and Adaptec-product-free systems. Not exactly the same thing, but similar.

[http://web.ncf.ca/aa571/aspi.htm](http://web.ncf.ca/aa571/aspi.htm)

cdrecord is provided inside the package "wodim" in lucid.

---

### Post by kennybob on 2010-08-16
I have the most updated system of Ubuntu 10.04 (lucid). Yes, its a x64 bit system.  And yes, the 32 bit version might work, but I'm not gonna downgrade my system for one problem.

Gnome version 2.30.2 (Ubuntu 2010-06-25). Kernel 2.6.32-24-generic (#39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010).

Yes, Brasero did work.  But have been told that Ubuntu will not support mkisofs and probably cdrecord anymore.  In fact mkisofs now is just a symbolic link to genisoimage.  But cdrecord is no longer included.

I believe that when the update took place they must have removed cdrecord, because even the nautilus cd writer program (which seems alot like Brasero), doesn't work anymore.

I removed Brasero and reinstalled it. It did not install cdrecord, did not even say it required it. But it still comes up with the error message, that it requires it, the same with mkisofs.

When I run cdrecord thru a command prompt I get this: 
wodim: No tracks specified. Need at least one.
Usage: wodim [options] track1...trackn

So it looks like cdrecord doesn't exist anymore either.

---

### Post by Yellow Pasque on 2010-08-16
> Doesn't anyone know how to program a decent cdwriter programs without relying on other peoples work?
Feel free to reinvent the wheel if you'd like.. Also feel free to actually address your issue in the initial post instead of ranting and actually posting your issue 3 posts later...

Also, can you sum up your last post? It doesn't make sense.

---

### Post by kennybob on 2010-08-17
Well after some investigating, I have found something that does work. It's GnomeBaker.

It seems that this is a bug from way back in March, (Bug 531901), and hasn't been addressed yet. It has something to do with hal, but not sure hal is even used in Lucid. I think udev replaced hal.

Seems this bug or others like it are all over launchpad. And it only effects cds not dvds.

So I'm removing my statement that all cdwriters in Ubuntu are fake. There seems to be one that stands out, but is rarely used.

---

