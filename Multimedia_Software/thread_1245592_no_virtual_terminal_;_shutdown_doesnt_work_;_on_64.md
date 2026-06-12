---
title: "no virtual terminal ; shutdown doesnt work ; on 64Bit Jaunty"
date: 2009-08-20
forum: Multimedia Software
---

### Post by vikofle on 2009-08-20
Hi all

I ve been following several threads here for months but none of them seem to be describimg exactly my problems - so I here go : 

I run Ubuntu 9.04 64 Bit Desktop on AMD Athlon 64 X 2 with 2 G Ram and I have ***2*** Monitors connected to a NVIDIA 7300GT. 
The system is setup with ***TwinView*** having used nvidia-settings. The driver is the latest nvidia (180). 

The problem actually presents itself with 2 symptons 
1.) I cannot access the virtual terminals CTRL+ALT+F1-6, by which I mean that I dont see anything there - however the vt's work. I can log in blindly an type 'ls -l > /tmp/test' switch back to vt7/X and access that file from there. I can switch between vts and X a small number of times before it wont let me do that again (cant get back to X) 

2.) Shutting down or restarting doesn't work. Opening a gnome-terminal and running *sudo shutdown -h now* (or clicking the turn off button) quits X but freezes the system shortly afterwards and I am left no option but to turn off the pc the hard way. That is if I start the computer, log in to Gnome, and klick to turn off the pc before actually working (doing stuff for some time) then it does work.

I was able to determine that this problem occurs no matter which driver version I use (offered and tested: nvidia 180, 173,96). Furthermore, when disabling one monitor in nvidia settings it works (from next time onwards). Also when using seperate X with xinerama (then without compositing) it works. 

I've tried several way all suggested in this forum. I ve disabled framebuffers, turned them on, installed fbset, loaded nvidiafb, etc. 
none worked. I have even exchanged the card with a nvidia 7300 GS. nope.

I ve spent weeks on this problem before deciding to work with only one monitor for now.

Yet, I would love to have my second screen back. Any body has any new updates on this problem? 

vikofle

---

### Post by techstop on 2009-08-20
How about that? I am struggling with exactly the same thing.

Dell XPS M1210
64-bit Jaunty

Trying to attach an external monitor, no luck at all. TTYs are not working.

No answers here I'm afraid, but subscribing...

---

### Post by pstracha on 2009-09-05
Hi Guys, 

I had similar problems but got things working (including my virtual terminals) by installing the latest nvidia drivers. 

Here's what I did:

1. Visit [nvidia.com]("http://www.nvidia.com/Download/index.aspx?lang=en-us") to download the latest driver (v.185)
2. Fall back to the open source driver "nv" so you can access a terminal
3. Stop X with 
```
sudo /etc/init.d/gdm stop
```
4. Prep nvidia driver for execution
```
chmod +x NVIDIA-Linux-x86-185.18.36-pkg1.run
```
5. Start installation of driver
```
sudo ./NVIDIA-Linux-x86-185.18.36-pkg1.run
```

As the installation progressed I let it build a kernal module for me and let it set my xorg.conf settings. After it was installed I restarted the computer and all was well :D

Hope this works for you, one caveat - while I'm on an AMD64 machine I have installed the 32 bit version of Ubuntu (because I can't stand how slow FLASH is on 64 bit). But the symptoms you describe were similar with the 32bit OS, I'm thinking the new nvidia drivers should help you too.

PS: This fellow's post helped me with the above [http://buranen.info/?p=339](http://buranen.info/?p=339)

Good Luck!

Cheers,
Paul

---

