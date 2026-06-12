---
title: "Toshiba Sound"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by gj15987 on 2007-09-18
I know this is a common problem with Toshiba laptops. I have tried A LOT of tutorials and guides to fix it but to no avail.

The problem is however, that it's not that I have no sound, but the fact that the sound is extremely quiet. It's there, but I can only hear it when I have my ear pressed right against the speakers and the volume is up full.

I have all the latest drivers and updates installed.

Make and model: Toshiba Satellite P100-227.

Any help would be GREATLY appreciated.

---

### Post by arkara on 2007-09-18
ok i got a toshiba too...

and the same problem
you have to turn apci off
but your computer wontturn off and not tell you if you are on batery or ac
at least mine does
i got a toshiba satellite p100-106 
now go to the shell and type

sudo gedit /boot/grub/menu.lst
or kate instead of gedit if you use kubuntu

now look my file and see

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=dff38c85-4c27-4138-888a-9bfe1b07941b ro acpi=off
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=dff38c85-4c27-4138-888a-9bfe1b07941b ro single
initrd		/boot/initrd.img-2.6.20-16-generic


do you see that i the line of the kernel i deleted quiet splash and replaced it with acpi=off

do the same and save the file
dont forget to get a backup of menu.lst
then reboot
no screen of ubuntu will come up just the processes that ubuntu uses..
so you can see if anything go wrong and sound will work
if want the ubuntu screen back add quiet splash next to acpi=off
thats all m8
 good luck

---

### Post by gj15987 on 2007-09-18
Thanks alot for your reply!

Is there any danger in turning ACPI off? Doesn't ACPI control the fans in the laptop or am I getting that confused with something else? I don't want to turn it off and then find out my laptop is overheating.

---

### Post by arkara on 2007-09-18
yeah acpi turns fan control off

in fact your fans will work full job all the time and wont stop. if there is any overheating problem which i dont think so, you can always turn acpi on by removing  the acpi=off but you always have to experiment dude
try it out and give me some feedback... in my laptop it works just fine and given the fact that you   have the same bios manufacturer you wont have any problems

---

### Post by gj15987 on 2007-09-18
*Jumps up and down with joy*

It worked :D
Thanks a lot for the help.
I'll let you know if having ACPI off affects anything else!

Thanks again.

---

### Post by arkara on 2007-09-18
ok man glad to help you

now one effect that i know is:
when you are going to shutdown your system it will say the shutdown blah blah..
then halting system
and then system halted
but wont power off.so you have to do that manually
i ve heard that its completely safe so you dont need to worry about it

---

