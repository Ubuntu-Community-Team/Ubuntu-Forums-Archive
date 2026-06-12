---
title: "Resolution problems"
date: 2006-02-24
forum: Multimedia &amp; Video
---

### Post by fannymites on 2006-02-24
As long as I've used linux I've had my resolution set at 1024x768 and never bothered to change it but now I want it higher - 1280x960.
When I try to change it via kde control centre it only goes as high as 1024x768 but after looking at xorg.conf I noticed that the vert and horizontal refresh rates were completely wrong for my monitor.
So I've reconfigured xorg and used the correct rates and when I go back into kde I can select higher ones and I've gone as high as 1600x1200 with no problems but after a reboot it is reset to 1024x768 and the higher options are gone.
I've recently been trying the same thing on suse and after many reboots there it's keeping the higher resolutions so I'm not sure it's a problem with the hardware.
I don't know if it makes a difference but I'm using kde on ubuntu, not kubuntu.  I haven't installed kubuntu-desktop or anything kubuntu related.

I have an old, unsupported video card (Hercules kyro2 64MB ) and am using the vesa driver.
I understand there is a kyrofb driver for this card but I can't work out how to get it to work - if I modprobe it the monitor shuts off and I can't do anything.  I've tried recompiling the kernel with kyrofb built in instead of as a module but when booting the monitor shuts off again.

---

### Post by fannymites on 2006-02-24
I've gotten round to reconfiguring xorg in dapper and, like suse, it's letting me change the resolutions at will.  In dapper I'm using gnome with gdm as display manager and in breezy I'm using kdm (kde 3.5) from the alioth repo.
Could that be something to do with it?

---

### Post by fannymites on 2006-02-27
Can no-one help?  I've been trawling the net and have found tons of ubuntu specific howto's regarding res and refresh rates but nothing will work.  I now have a resolution of 1280x1024 on suse, ubuntu dapper, gentoo and fedora core but not in breezy.
The refresh rate is stuck at 61 and res at 1024x768.  I know I can get it up to 1280x1024 on ubuntu but I just can't make it stick after reboot.  My xorg.conf doesn't even have 1024x768 as an option so why is it being ignored?
I've tried using gdm and kdm and it's the same with both.

[EDIT] I've just realised that if I do a console login at the login screen then do "startx"  I get my 1280x1024 res every time, even after reboots so it seems it is a display manager problem.  Any ideas?

---

### Post by WretchedSpawn on 2006-03-07
a very simple solution would be to simply install kubuntu desktop, as really all it is is kde with a few tweeks to make it more compatible with ubuntu. kubuntu and ubuntu share the vast majority of the core files so it's not as if they're two sepparate operating systems or anything.

if that doesn't sound appealing you should post your xorg.conf.

---

### Post by fannymites on 2006-03-07
The problem with that is that it also installs tons of stuff I don't want or need, so it means downloading tons of packages then removing half of them.
I've done several clean installs of ubuntu and then installed kde both ways, via kubuntu desktop and by installing the seperate components and haven't had any problems either way.

However, the kde I installed this time was 3.5 from the alioth repos and it looks like that was the problem, seems something was installed or removed during the install that caused the problem.
I've now stopped using ubuntu now for various reason but while sorting through some disks I found a backup that I had made just before the kde 3.5 install so I tried restoring it and sure enough, I was able to change resolutions at will and it stayed at my selected res after a couple of reboots.  But like I said, I'm not using ubuntu anymore so it's not much help now but I'm still glad I found out what the problem was (though not the exact cause but close enough for me), otherwise it would have been the first ever problem with ubuntu that I hadn't found a way to solve.

---

