---
title: "UbuntuStudio : Upgrade to 17.10 audio problem : no detectable sound card in xfce"
date: 2018-02-21
forum: Multimedia Software
---

### Post by achix2 on 2018-02-21
Hello forum! My son uses and likes Ubuntu Studio for audio/video/gaming. I  am an old Unix die-hard using unix since early SunOS, and also  FreeBSD/Linux since the early 90s. 
Ok, enough with the intros, here is the steps that lead to the problem : 
At first I tried to upgrade from 16.10 but obviously there was no  update path due to 16.10 being obsolete. Then I tried a hack to force  upgrade directly to artful , by changing /etc/apt/sources.list  but this resulted in an unstable system (no grub, ultra slow USB  wireless mouse and keyboard, upstart problems, blank blue screen after login (due to upstart being corrupted) etc). And finally decided to bite the  bullet, back everything up and go for a fresh installation. In the  process of installation I decided to keep old user data files (i.e. not  format). 
Files were kept, but not the exact users -> uid , groups -> gid mappings. So I had to do some editing there. 
Everything seemed to go semi-OK, but then started some more  problems. Mouse/Keaybord were still slow, laggy even lossy (keyboard). I  changed the USB port and keyboard and mouse started behaving good. 
Then I decided to test some sound. I am not currently on the box,  but i supposed the tool I used was : xfce4-pulseaudio-plugin . This  detected no audio card. Just a dummy card. 

Can you guys shed some light on what to do next?

---

### Post by achix2 on 2018-02-21
For some peculiar reason this kernel -4.13.0-36-lowlatency was present in /boot along with its files : 
abi-4.13.0-36-lowlatency         retpoline-4.13.0-36-lowlatency
config-4.13.0-36-lowlatency      System.map-4.13.0-36-lowlatency
initrd.img-4.13.0-36-lowlatency  vmlinuz-4.13.0-36-lowlatency

Those were not owned by any installed package, but grub had this as the default options. Not having the corresponding (... also zombie) drivers in the /lib/modules , many things (audio being among them) naturally didn't work.
I am puzzled how this might have happened from an easy default DVD installation.

---

