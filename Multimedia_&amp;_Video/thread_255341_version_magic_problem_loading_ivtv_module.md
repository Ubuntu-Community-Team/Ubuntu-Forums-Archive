---
title: "version magic problem loading ivtv module"
date: 2006-09-11
forum: Multimedia &amp; Video
---

### Post by Marek McGann on 2006-09-11
Hi,

I'm trying to put together a MythTV box on a new machine, running 6.06.1 (Kubuntu, actually, but don't hold it against me, my difficulty isn't KDE related).

I've downloaded the ivtv driver source, and run 'make' and 'make install'. 'make install' required me to delete a single space from the end of the EXTRAVERSION tag in /usr/src/linux/.config

Loading the module is the problem. 'depmod' runs fine, but 'modprobe ivtv' produces the following error:

```
FATAL: Error inserting ivtv (/lib/modules/2.6.15-26-386/ivtv/ivtv.ko): Invalid module format
```

dmesg tells me this:

```
ivtv: version magic '2.6.15-26-386  preempt 486 gcc-4.0' should 
be '2.6.15-26-386 preempt 486 gcc-4.0
```

Which was a bit confusing at first. I then noticed that there are two spaces between the first '386' and 'preempt'. The question now becomes, how do I get rid of the extra space?

I've no idea where I should be looking for this. Googling for version magic gives me lots of information on the fact that it exists, but I haven't found anything to tell me how to set it up or alter its tagging of a compiling kernel module.

Any pointers here would be greatly appreciated.

---

### Post by dmccartney on 2006-09-12
I am having the identical issue.
I will post if I find the solution.

---

### Post by dmccartney on 2006-09-13
I simply went back to the place where we edit the Makefile and continued from there (making certain to issue "make clean" calls along the way.)

This seems to clear up the extra space in ivtv module's version magic issue.

---

### Post by BathroomNinja on 2006-09-14
How exactly do you issue 'make clean' commands?

---

### Post by dancro on 2006-09-17
Thanks for the info dmccartney.  However, I am lost in trying to find where I was supposed to edit the Makefile.  Can you give me any guidance? 

Following the "MythTV 0.19 on Ubuntu 6.06" by Sean Gardner, on page 12 
modprobe ivtv
got response: FATAL: Error inserting ivtv (/lib/modules/2.6.15-26-386/ivtv/ivtv.ko): Invalid module format

dmesg reported:
ivtv: version magic '2.6.15-26-386  preempt 486 gcc-4.0' should be '2.6.15-26-386 preempt 486 gcc-4.0'

I gather that somewhere there is a statement with the extra space before preempt and that is what I need to fix, but I don't know where to look.  

Thanks in advance for any help.
Dan :)

---

### Post by dancro on 2006-09-17
OK.  I found the Makefile change.  It was back there where we removed the extra space from EXTRAVERSION.

Went back there and did 
```
make clean oldconfig
make clean perpare0
make clean scripts
rm build
ln -s /usr/src/linux build
```

then
```
cd /usr/src
cd ivtv-0.4.6
make clean
make clean install
```

then
```
depmod
modprobe ivtv
```
and got no errors this time.

Now on to testing ivtv.  :D

---

