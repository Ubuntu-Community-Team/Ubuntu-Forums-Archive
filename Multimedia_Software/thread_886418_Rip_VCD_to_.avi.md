---
title: "Rip VCD to .avi?"
date: 2008-08-11
forum: Multimedia Software
---

### Post by GabrielWolff on 2008-08-11
I have a VCD which I would like to put on my HDD. The mpeg rip made by VLC is really bad quality, and so I thought I'd like to convert the film to .avi.

Anyone knows how to do that OR has another suggestion?

---

### Post by Major_Kong on 2008-08-11
Try using avidemux.

---

### Post by GabrielWolff on 2008-08-11
> **Major_Kong said:**
> Try using avidemux.

You sure? It seems like the program is not exactly built for ripping. Or am I just missing how to?

---

### Post by forger on 2008-08-11
Try with programs such as:
acidrip
thoggen

or this one:
> Package: vcdimager
A VideoCD (VCD) image mastering and ripping tool

This package contains a collection of tools to master (Super)VideoCD, either directly from compliant MPEG streams with no PlayBack Control (PBC), or out of an XML description for a full-featured (S)VCD.

This package also contains a VideoCD ripping tool to rip mpeg streams from VideoCD images, and some debugging tools. 

Commands used:
> /usr/bin/cdxa2mpeg
/usr/bin/vcd-info
/usr/bin/vcdimager
/usr/bin/vcdxbuild
/usr/bin/vcdxgen
/usr/bin/vcdxminfo
/usr/bin/vcdxrip


---

### Post by mamcak on 2009-02-11
Hi everyone!
Firstly you cannot rip vcd's with dvd rip softwares.

for ubuntu 8.10 (i was tested)

install vcdimager:
sudo apt-get install vcdimager (or use synaptic)

Now, you have a command line vcd ripper called "vcdxrip"

put the vcd in your optic driver
open the command line and run:

$ vcdxrip --nofiles

it just start copy vcd's AVSEQ0x.DAT to your home as AVSEQ0x.MPG

Have a nice works!

---

### Post by zisun666 on 2009-02-26
Try ffmpeg, ffmpeg -i yourVCD.dat -y output.avi.

---

### Post by exozito on 2009-04-10
> **mamcak said:**
> Hi everyone!
Firstly you cannot rip vcd's with dvd rip softwares.

for ubuntu 8.10 (i was tested)

install vcdimager:
sudo apt-get install vcdimager (or use synaptic)

Now, you have a command line vcd ripper called "vcdxrip"

put the vcd in your optic driver
open the command line and run:

$ vcdxrip --nofiles

it just start copy vcd's AVSEQ0x.DAT to your home as AVSEQ0x.MPG

Have a nice works!

Thank you! That worked for me.

---

### Post by Saisombun on 2009-05-06
> **zisun666 said:**
> Try ffmpeg, ffmpeg -i yourVCD.dat -y output.avi.
Didn't help: 
**avseq01.dat: Unknown format**

[QUOTE=mamcak]$ vcdxrip --nofiles[/QUOTE]
Not successful...
**fopen(): Read-only file system**

What can I do else?? ](*,):cry::cry::cry:

---

### Post by Saisombun on 2009-05-06
About 'Read only'
I got it! :) I was INSIDE the folder with *.dat files in Terminal. When I  returned to my home folder, the problem solved. So simple. :) I didn't know, that 'cd' command can block working with CD-ROM... Sorry

---

### Post by eladamri on 2009-06-01
The only easy way I found to do it, since vcdxrip did not work for me was I installed k3b, then tools-> rip video cd

---

### Post by masoud77 on 2011-10-06
Wow. That works. Thanks a ton!!!!

---

### Post by xianbei on 2012-03-31
here's another shout to k3b... shout!

---

### Post by Yasho on 2012-05-10
> **mamcak said:**
> 
for ubuntu 8.10 (i was tested)

install vcdimager:

it just start copy vcd's AVSEQ0x.DAT to your home as AVSEQ0x.MPG

Have a nice works!

Thanks a TON. Worked great for me.

Regards

---

