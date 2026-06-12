---
title: "Question about Linksys AE1000 wireless adapter, creating /tftpboot. Why?"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by sandman887 on 2011-07-08
Ok so I tried to follow the directions here:
[http://ubuntuforums.org/showthread.php?t=1630358&highlight=Linksys+AE1000]("http://ubuntuforums.org/showthread.php?t=1630358&highlight=Linksys+AE1000")

However, I couldn't find 2010_0915_RT3572_Linux_STA_v2.4.0.2.tar.bz2. Instead, the closest I could find was 2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2, so I tried it.

I edited config.mk and rtusb_dev_id.c as chili555 advised.

I tried to edit linux_rt.h, however, the only file I saw was rt_linux.h. I edited it according to chili555's post, message #7.

I went back to the root directory of the extracted .bz2 file and did
```
make
```

I got
```
make[2]: *** [/home/shredder/Desktop/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/shredder/Desktop/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-32-generic'
make: *** [LINUX] Error 2

```

I had NOT yet done this following command because I wanted to see what happened before I ran the command:
```
sudo apt-get install build-essential linux-headers-generic
```

So, after that error like I posted above, I tried the sudo apt-get ... command above, but I discovered they were already installed.

I made the mistake of doing
```
sudo bash
```

Instead of
```
sudo apt-get install build-essential linux-headers-generic
```

Obviously, after the command, I was still root. I had forgot that I was still root. Anyway, I tried make again. 

After make completed (successfully, without errors) I realized that I had just ran that as root. I ran make as my regular user, and ran into errors, saying it could not create certain files. I figured it was because I had ran make as root, and it created files owned by root. So I copied the files I edited onto my desktop, became root again, and removed the entire extracted directory and exited back to my regular user. 

I re-extracted the .bz2 file to a directory named after itself, and copied the files I had just copied to my desktop back to the directories where they were supposed to be, and ran make again. 

I think this would have finished successfully, however, I noticed that at my userlevel, it could not write to /tftpboot. I'm not sure, but that just seems kind of weird. Why would it create a file in the / directory? 

Is this normal? Maybe I'm just ignorant and paranoid.

Also, later on after that post, I read that if you have a kernel lower than 2.6.35, you don't need to edit the .h file, which I did. So when I re-extracted the .bz2 file, I didn't edit it, because I have 2.6.32-32-generic. But I don't think I need help with that part. 

I'm just curious about the /tftpboot file. I don't have the root directory contents memorized, but why would the make script care about that file?

---

### Post by chili555 on 2011-07-08
> I'm just curious about the /tftpboot file. I don't have the root directory contents memorized, but why would the make script care about that file?It cares because that file is not writable, except by superuser or root. The proper way to compile this package is:```
cd directorycontainingmakefile
[COLOR="Red"]sudo su[/COLOR]
make
make install
modprobe rt5370sta
[COLOR="Red"]exit[/COLOR]
```If you think you've made a mistake or need to fine-tune something and, most particularly, when a later version of linux-image, also known as kernel, is installed by Update Manager, then do:```
cd directorycontainingmakefile
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt5370sta
exit
```'make clean' does pretty much what it sounds like, clean out all the old stuff that was created by 'make' against my older kernel and possibly my older gcc version and give me a fresh clean slate.

---

### Post by sandman887 on 2011-07-08
What I'm asking is why is the file /tftpboot even involved in this install? Like I said, it may be my ignorance and/or paranoia showing, but why is it trying to write to my root directory, and why is an ftp program involved in this driver install?

---

### Post by chili555 on 2011-07-08
I don't believe it's an FTP program at all: [http://www.redhat.com/archives/rhl-devel-list/2007-November/msg00937.html](http://www.redhat.com/archives/rhl-devel-list/2007-November/msg00937.html)> TFTP is often used to store firmware images and configuration files 
for embedded devices, and as a place for such devices to write crash 
dumps, log files, etc.I think its use and the fact that it's written to in 'make' is a reflection of the source file being written for every possible version of Linux, whether or not it's Debian-based and whether or not it's Ubuntu. I think that's also why we need to tweak a .c file once in a while.

I know this can be frustrating to new users who want it all to just work. However, the 5390 chipset is rather new; I never saw it on the forum until maybe 90 days ago. It is a fact of life that sometimes we have to compile from source for new products.

Actually, and I probably shouldn't admit this out loud, but I enjoy working out all the kinks and getting the file to compile; posting it and then seeing posters reply that it's working. Is there a twelve-step program for me? 

Stop me before I compile again...

---

### Post by headvampyre@hotmail.co.uk on 2011-07-08
/tftpboot is a directory created by the TFTPD-HPA server. Its used for storing the boot files for network booting, e.g. pxelinux.0

To uninstall it, run:

apt-get purge tftpd-hpa

---

### Post by sandman887 on 2011-07-08
I still don't know why the author of the make script would worry about network booting, but as long as it sounds normal and nothing malicious, I guess I'll go ahead and install it. I renamed /tftpboot to /tftpboot2 just in case I needed the file. 

Thanks for the prompt replies.

---

