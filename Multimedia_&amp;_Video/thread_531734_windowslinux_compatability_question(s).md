---
title: "windows/linux compatability question(s)"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by Parms on 2007-08-21
I was wondering if I put something on disc from windows, or SD if linux would be able to read it. Or accept the files. 

Things I plan on moving from windows to linux...Ubuntu 7.04 (64bit)
                                        Windows XP media center vs.2005   (?? Bit)
Pictures..
Music.. MPEG layer 3 audio (is that MP3 ??)

I'm assuming you have to use a program or something, but the question I really want to know is... the disc and SD one..

For example I install a package or theme (linux format) from windows enviroment onto say a SD would linux be able to open that scan disk.

That would help.. Thanks in advance.

Also If I use VMWARE in linux, can I actually run my windows on my other hard drive? Or vice versa? Or would it need a new install? I have been using VMWARE for awhile on windows, mostly to set-up virtual networks for practice (ITT student). Don't know how to use it for anything else.

---

### Post by Ek0nomik on 2007-08-22
Ubuntu will be able to read the files from your SD=>USB device and also any CD-ROM you insert into the computer as well.

You can play MP3's but you need to download something to allow you to do it.

> 
1. Check, if you have included the Universe sources in /etc/apt/sources.list

2. Type "sudo apt update" in the shell (or use the Update Button in Synaptic)

3. Type "sudo apt install gstreamer0.8-mad" (or select and install it in Synaptic)
This will install the needed libmad0 library as well.

---

