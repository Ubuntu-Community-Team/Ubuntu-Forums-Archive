---
title: "Trying to install 8.10 alpha4 but not booting - sticks on starting NTP server ntpd"
date: 2008-09-01
forum: Mythbuntu
---

### Post by bob808 on 2008-09-01
I am trying to install mythbuntu on my machine but am having problems with the install disc.

on bootup if I pick live cd or install it starts to boot but then after the splash screen it goes to a bash screen and tells me what kernel is in use, then the no warranty disclaimer and where to go for documentation.

My problem is after that - rather than launching the gui like on other mythbuntu disks it just says

Stopping NTP server ntpd
* Starting NTP server ntpd

then nothing - just a blinking curser - it says kernel alive and direct mapping tables up to 100000000 @ 8000-d000 at the bottom.

I cant use the 8.04 release as the kernel does not support my motherboard so I have no LAN or graphics drivers (nvidia 8200 chipset board) but 2.6.25 kernel and above should and 8.10 uses 2.6.26-5-generic so it should be ok if only I can get it to install.

Any ideas if I am doing anything wrong, or how to get around this?

Thanks

bob808

---

### Post by bob808 on 2008-09-01
ok, I have tried the cd on my laptop and another pc and it loads to the live environment ok, so the disc is fine...

odd thing is if I boot with 8.04 live cd on the pc I want to install on it loads ok, but the network doesnt work...  I have the asus M3N78-EMH-HDMI motherboard so need the newer kernel that 8.10 alpha 4 uses to get support for the chipset and lan so that is why I need to use this one.

Just now I tried again and again it went to the bash prompt, it goes very quick from the mythbuntu logo screen to the bash prompt, possibly flashing an error or info first, but not for long enough to catch what it says - any way to find out what is causing it to not launch into the install screen or the live environment on the 8.10 cd?  It just seems odd given that 8.04 CD works fine on this machine.

fyi the hardware is the m3n78 motherboard and a hauppauge nova-hd-s2 sat card with an amd x64 dual core cpu, no other cards in use as I am using the onboard lan, sound and graphics.  I have 2gb of ram, so the system should work fine.

I am trying the amd x64 build of the live cd.

Is there a log or anything that can identify the problem and hopefully hint towards a solution?

Thanks

bob808

---

### Post by bob808 on 2008-09-02
can anyone help with this?  at the moment I can not get as far as the install prompt for 8.10 alpha 4 even though I can with 8.04

Is there a log to show why I am being dumped to a command prompt rather than launched into the installer?

---

### Post by JB2007 on 2008-09-15
hey bob, I found the same issue with the 64bit release of 8.10 Alpha 4.

I have not tried the 32bit - as 8.04.1 works fine for me...

I have an ASROCK ALiveNF7G-FullHD motherboard.

---

### Post by aross01 on 2008-09-16
CPU: AMD Phenom 9850 Quad Core Socket AM2
MB: ASUSTek M3N-HT Deluxe/HDMI
MythBuntu 8.10 

My first time installing MythTV but this sounds like the problems I was having.

Mine was stopping at the same place I was using the onboard video it lookeds like this is the place right before displaying the GUI interface.

Later I found vid init errors 640x480, 800x600, every mode was listed.

I pluged in a video card and after the install and updates I removed the card rebooted and selected the right video driver for the onboard video and everything was ok

Let me know if this helps

---

