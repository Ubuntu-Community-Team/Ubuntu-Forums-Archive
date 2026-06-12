---
title: "Error 17 on Fresh 9.04 install"
date: 2009-04-28
forum: Mythbuntu
---

### Post by brian_hayward on 2009-04-28
I tried to install the latest and greatest Mythbuntu 9.04.  When i went to restart the machine i got an Error 17 message.  I did a little research and i came to the conclusion that my boot list was messed up some how.  so i loaded up the Mythbuntu live cd and mounted the ext3 partition.  i navigated to the /boot directory and i didnt see a grub directory in it.  so i did more research and found a post that described running sudo update-grub...it did a little searching and said it couldn't find /boot/grub directory...so i created it...then i ran sudo update-grub again and it told me it couldn't find the /boot/grub/menu.lst (i shut my computer down out of frustration so i cant remember what the file with the menu list was called so i hope you all are following me up to this point) it asked me if i wanted to create it and i told it yes.  then i shut everything down and tried to reboot but i still go the error 17.  Can somebody please shoot me some suggestions.  i thought my install was bad so i reinstalled...didnt help.  I am using a 320 gb ATA Western Digital Hard drive.  I had Ubuntu 8.10 installed and working previoulsy so i know that the jumpers are all set correctly and the bios is fine.  what else am i missing?  after running the update-grub do i need to go back into the /boot/grub/menu.lst file and add the information to get ubuntu to load?  Any help or suggestions are greatly appreciated.  Thanks.

---

### Post by SiHa on 2009-04-29
Just one thought.

When installing, there is an 'advanced' tab, and a little checkbox that says 'Install Bootloader'. Did you by any chance uncheck that?

I mad a similar mistake when I first installed Ubuntu on a machine that was only going to have that OS on it, so I assumed I didn't need the bootloader and unchecked the box.

---

### Post by brian_hayward on 2009-04-29
> **SiHa said:**
> Just one thought.

When installing, there is an 'advanced' tab, and a little checkbox that says 'Install Bootloader'. Did you by any chance uncheck that?

I mad a similar mistake when I first installed Ubuntu on a machine that was only going to have that OS on it, so I assumed I didn't need the bootloader and unchecked the box.
That is a good point...I wanted to add another partion to the default partions created at install, and each time i tried to install the Mythbuntu i clicked the advanced button.  I don't think i unchecked anything but the next time i try an install i will not click the advanced button.  thanks for the suggestion.

---

### Post by brian_hayward on 2009-04-29
> **brian_hayward said:**
> That is a good point...I wanted to add another partion to the default partions created at install, and each time i tried to install the Mythbuntu i clicked the advanced button.  I don't think i unchecked anything but the next time i try an install i will not click the advanced button.  thanks for the suggestion.

I tried to reinstall without checking the advanced tab and I still get the Grub Error 17 message.  Anybody else have any suggestions?

---

### Post by brian_hayward on 2009-05-05
I finally got my Mythbuntu to work.  When i was going thru the installation, instead of checking the box "log on automatically" i chose "log on using password" (yes i understand the wording isn't exact but I hope you get the point)and it booted up and everything works fine, but now i have to login every time i boot up where i didn't have to do that in 8.10.  

Has anybody else been had the same problems installing Mythbuntu 9.04?????

---

### Post by klc5555 on 2009-05-05
> **brian_hayward said:**
> I finally got my Mythbuntu to work.  When i was going thru the installation, instead of checking the box "log on automatically" i chose "log on using password" (yes i understand the wording isn't exact but I hope you get the point)and it booted up and everything works fine, but now i have to login every time i boot up where i didn't have to do that in 8.10.  

Has anybody else been had the same problems installing Mythbuntu 9.04?????

My own personal bete noire since 8.04 came out has been Grub Error 2's. But anyway...

Error 17 is supposed to designate unrecognized partition/file system structure (say, when an extra partition has been added), requiring installation of Grub to MBR using grub-install. Syntax/use of the command is explained here:
[http://www.gnu.org/software/grub/manual/html_node/Invoking-grub-install.html](http://www.gnu.org/software/grub/manual/html_node/Invoking-grub-install.html)

I don't know whether the command 'sudo grub-install' is available from a terminal when the CD has been booted --this will need to be checked.

Cheers!

---

