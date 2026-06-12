---
title: "File format problem after update"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by christoph411 on 2011-04-05
Hello!
After I updated my 11.04 install today, it appears that I cannot open and the system cannot read any .png files!!! Of course, not being able to read .png files causes HUGE ISSUES (no program icons, only certain themes work, absolutely no unity:()
 I'm not sure if this is related the update (probably not, fully updated on a second 11.04 computer without problem) but i would really appreciate any help i can get anyway so i can avoid a reinstall, because i haven't gotten a live cd/usb to work since alpha 2:P After taking my screenshot, it also appears that .jpeg images don"t work:confused:   I have never seen anything like this before. I'm not sure if this will help, but i noticed that chrome also acts very strangely (see the attached image)  

Thanks for any help in advance! :tongue:

---

### Post by prusis on 2011-04-07
Exactly the same problem here. I am using natty since Alpha 2, everything was more or less fine with occasional crashes, but cannot figure what to do with this. Only happened after update on Tuesday and I can log only in failsafe through recovery.

---

### Post by prusis on 2011-04-07
Any ideas would be great!

 When trying to load Ubuntu without recovery it gets stuck at:

Starting save udev log and update rules         [fail]
or
Staring load fallback graphics device              [fail]

If I manage to load desktop (preceded by Nvidia symbol fullscreen), all I can do is move mouse on gray background (Background is gray in failsafe as well since it wouldn't load .jpeg). Only thing that works from then on is Ctrl-alt-F2 to terminal.

I am using NVIDIA GeForce 8400M GS with proprietary drivers.

Also, when trying to open NVIDIA X Server Settings in failsafe I get: "You do not appear to be using the NVIDIA X driver."

---

### Post by prusis on 2011-04-10
Bump!

Also after newest updates and reinstalling my nvidia drivers I can log in regular safe mode Ubuntu without going to recovery and failsafe.

Hence, I believe I am in exactly the same situation as originally reported by christoph411

Also, I do not know how christoph411 took screenshots, since print screen gives me:

Unable to save the screenshot to disk:

Image type 'png' is not supported

---

### Post by christoph411 on 2011-04-10
Hi there prusis! I'm sorry, I haven't been keeping tabs on this thread anymore since I was forced to do a reinstall :( I couldn't find anything at all after hours of google searching, but i did find that starting the gnome-settings-daemon did get a little less of a "win 98" theme, but i can not for the life of me figure out what on the sytem would cause images to not load? :confused:  (ps. you can take pictures in gimp from file-create-screenshot) I also do not understand how this appears to have been update related, yet we were the only ones experiencing this? (I have a nvidia card and i could only log in in safe graphics mode).But, after i reinstalled and updated this did not happen again, so at least thats a little positive ray of light in this situation.

---

### Post by prusis on 2011-04-10
Thanks for info,

Good to hear that reinstall helped, but right now I have lot of data on my hard drive and would not want to erase it :(. Hence, since all essentials are running (Wireless card, Firefox, VLC, Skype, Rhythmbox) I am willing to wait for a while... gnome-settings-daemon is running for me by default. Also, I find it peculiar that it seems we were the only ones experiencing it.

---

### Post by christoph411 on 2011-04-10
I also can't believe we have 155 views and we're still the only two that have replied! :eek:  (this is a mini-bump, because i don't have any new info, so i will throw us to the top for a while :D)

---

### Post by ronacc on 2011-04-10
I'm not seeing that here is not a helpful reply but it is the only one I can make . You have checked for broken packages haven't you ? is there anything non default that you have installed or have you had to "force" any installs ?

---

### Post by prusis on 2011-04-10
Yes, several times I have tried to fix broken packages but there just isn't any. Also I have tried to reinstall several packages through terminal just hoping it might help. If I remove Nvidia proprietary drivers it doesn't load safe mode at all, the same goes if I install experimental drivers and I have to install proprietary drivers back through failsafe just to get back to safe mode. All updates were regular natty updates and none of them were forced.

---

### Post by ronacc on 2011-04-10
sounds like you've got a corrupted file somewhere , fix broken only finds things with missing dependencies and if the file is installed but corrupt it doesn't fix that .If you can find which file is causing the problem a reinstall would probably fix it . try this , in /boot/grub edit grub.cfg and remove quiet splash and vt.handoff=7  from the boot line also change the line that says set graphics mode=$linuxgfx mode ( not sure about the exact wording of that and that box isn't on right now so I can't check) anyway make it =text . that will let you see what is gonig on during boot and maybe let you spot something also it should help you getting to safe mode .

---

### Post by prusis on 2011-04-11
Yes, I actually have modified grub.cfg before, I just tried again, but I cannot see anything bold,

Yet, following the line

Begin: Running /scripts/init-bottom ... done.

there are always bundles of lines such as:

[   2.148226] firewire_core: created device fw0: GUID 00241b00aa882201, S400
[  20.533172] ata3.00: exception Emask 0x0 SAct 0x13 SErr 0x0 action 0x0
[  20.533263] ata3.00: irq_stat 0x40000008
[  20.533342] ata3.00: failed command: READ FPDMA QUEUED
[  20.533429] ata3.00: cmd 60/08:20:10:2c:9c/00:00:20:00:00/40 tag 4 ncq 4096 n
[  20.533432]          res 41/40:00:12:2c:9c/00:00:20:00:00/40 Emask 0x409 (media error) <F>
[  20.533609] ata3.00: status: { DRDY ERR }
[  20.533677] ata3.00: error: { UNC }

Though first numbers change for each bundle (18. ... 23. ... 28. .... etc)

---

### Post by ronacc on 2011-04-11
I have no idea what that error message means , have you tried googleing it ?

---

### Post by prusis on 2011-04-11
Well, I cannot get anything out of this error... Googleing portions of it gives links to several rather unrelated problems. If it holds key to my problems  I am just not experienced enough to figure it out. What really bothers me is that about 200mb of natty updates I installed today didn't change a thing to my problems...

---

### Post by prusis on 2011-04-12
Ok, I gave up, reinstalled natty, everything works fine now... Thanks for your help though :-)

---

