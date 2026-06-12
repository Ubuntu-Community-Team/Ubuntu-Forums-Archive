---
title: "Solution: Inno3D GeForce 6600 - nVidia driver"
date: 2006-07-06
forum: Multimedia &amp; Video
---

### Post by EnsilZah on 2006-07-06
I had this problem where i couldn't get my Inno3D GeForce 6600 256MB to work with the nVidia driver.
After installing the driver as per instrunctions, when starting X my monitor would go black and nothing would happen.

If you are experiencing this problem and your card identifies as GeForce Go 6600 GT PCI-E while it's actually a regular 6600 AGP, this should solve it.

You are doing this at your own risk, it worked for me, but it might not work for you.

The attached zip includes:
   Windows XP created bootdisk files
   nvFlash.exe + cwsdpmi.exe (program that flashes the card and a dependancy file)
   Club3D.rom (new bios to flash the card of an equivalent card by another company)
   Backup.bat (Batch file that should back up your existing file to backup.rom)
   Flash.bat (Batch file that should flash your card to the new bios)
   Restore.bat (Batch file that should restore your card from backup.rom)

Instructions:
   Extract zip to a floppy.
   Reboot with floppy.
   Run Backup.bat
   Run Flash.bat (there's a yes/no question stage in here, pay attention in case you'll need to restore a bad flash)
   Reboot

If you see everything fine then it succeeded and you should be able to safely install the nvidia driver as per instructions (i had trouble with the default nv driver at this stage so i just installed from the command line).

If your screen is garbeled or somesuch then the flash failed and you'll have to restore the original bios (happened to me when i tried some other bios).
If this happened then you'll need to boot blind with the disk, wait for it to stop loading, type 'restore', enter , wait for it to stop again, type 'y', enter, wait for it to stop again and reboot.

Hope this helps.

---

### Post by barry_hk on 2007-11-18
Just want all to know that Ubuntu 7.10 also recognised my regular 6600 AGP 256MB card as a GeForce Go 6600 GT PCI-E.  The solution provided by EnsilZah worked perfectly well.

Thanks to EnsilZah on this.  I spent over 30 hours in the last week trying to figure out how to enable my card to have 3D acceleration and all methods failed.

---

### Post by brazzmonkey on 2008-05-07
i have had troubles with nvidia drivers on my twintech GeForce 6600 AGP for about 1.5 year. as a workaround i used to manually install 96.29 drivers, which were the only ones that could make my 6600 working (to my knowledge - i have tried many others which would give me blank screens with locks up).
that satisfied me until i upgraded to hardy and realised i was no longer able to compile 96.29 drivers.

i tried to flash my video card bios with bioses from other brands, it just didn't make it (scrambled display everytime).

finally i cam along you post, grabbed your file, copied Club3D.rom to my fellow nvflash floppy, and oh surprise i didn't get scrambled video ! even better,i'm now able to use nvidia drivers.

so thanks a bunch EnsilZah, you saved my evening. i guess i owe you one.
thanks so much again !

---

