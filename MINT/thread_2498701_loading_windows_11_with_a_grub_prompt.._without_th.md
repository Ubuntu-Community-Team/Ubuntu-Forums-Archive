---
title: "loading windows 11 with a grub prompt.. without the actuall grub records.."
date: 2024-06-24
forum: MINT
---

### Post by ronjjjg8885 on 2024-06-24
i'm having a little problem
i had linux mint dual boot and dual disk with windows 11 as a second os.
the records were on the linux disk.
but i disconnected this disk from the computer.

when i boot the pc i get "grub>" thing..

can i give it a command to run windows 11 without having the other disk around?

thanks..

---

### Post by oldfred on 2024-06-24
Moved to the Mint sub-forum.

If UEFI install can you not boot Windows from UEFI boot menu? Some menu you used to boot live installer for Mint.

Best to always have boot loader for system on disk when multiple drives and multiple installs.
Or you need an ESP - efi system partition on Mint drive and a ESP on Windows drive with Windows boot files.

Need to know if installs are UEFI or BIOS as how you boot is different.

Best if both drives plugged in when you run this:
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by ronjjjg8885 on 2024-06-24
sorry, i thought it would be like entering a simple command.
i will have to use another computer for the windows 11 installation and continue from there.
tnx anyway

---

### Post by yancek on 2024-06-24
Did you try the simple suggestion in post 2 to access the BIOS firmware on boot to select windows?  You indicate you have each OS on a separate drive so this should be simple if you installed correctly.

>  the records were on the linux disk.

What records?  I would expect that windows 11 would be EFI and would have an EFI partition on its disk.

Downloading and running boot repair as suggested in post 2 is about the only way you will be able to get help as you haven't post enough information for us to do any more than guess.

---

