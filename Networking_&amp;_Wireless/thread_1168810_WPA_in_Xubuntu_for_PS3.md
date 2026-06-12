---
title: "WPA in Xubuntu for PS3"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by mesogen on 2009-05-24
Hi everyone,

I am a total Linux newbie. I recently got a PS3 and installed Xubuntu 9.04 on it. I tried a few different versions of Unbuntu, but none of them would install properly. I finally got Xubuntu to work.

But, when I went to connect through my wireless router, the OS simply cannot recognize it. Well, it recognizes the SSID and shows it on the connections list, but when I try to connect it always fails. Actually, it worked the first time I tried it, but then never worked again. 

The problems I see with it are the fact that the network manager is asking for a WPA password when WPA uses encryption keys and doesn't really use passwords, per se. 

I've looked online and got some commands that I tried to use in the terminal, but anything involving sudo or su are off limits to me. I only have one user established and apparently this user has no root privileges and I have no idea how to get these privileges. 

Does anyone have any advice for how I can get the network manager to recognize the WPA from my wireless router?

Thanks in advance.

---

### Post by del_diablo on 2009-05-24
PS3 is PPC arcitecture, Xubuntu and other *buntus run on x86(usually reffered to as the PC arcitecture).
Debian and Yellowdog got support for PPC, Ubuntu do NOT have.

---

### Post by mesogen on 2009-05-24
OOH

So I should install some other version than Xubuntu? 

Which do you like the best? This Debian or Yellowdog?

---

### Post by del_diablo on 2009-05-24
Have not tried Yellowdog, but Debian is quite solide. Ubuntu is passed of that one, and we are still likely to be able to help you(since lots in Ubuntu and Debian in the same).

[Link to Debian PPC .ISO if you don't bother to find it yourself]("http://cdimage.debian.org/debian-cd/5.0.1/powerpc/iso-cd/debian-501-powerpc-CD-1.iso")

---

### Post by mesogen on 2009-05-25
Before I go installing a whole other OS, does anyone else have any suggestions on how I can get root privileges to at least install wicd?

---

### Post by laughing_badger on 2009-05-28
May be a bug. I installed the PS3 version of Ubuntu 9.04 last night from the alternate installer (desktop freezes apparently). All went fine, but I can't su or sudo from the user account. su rejects the password and sudo says that I'm not in the sudoers file. Hard to debug.

Tried the i386 alternate installer in VirtualBox on a normal machine this morning and it doesn't replicate this.

---

