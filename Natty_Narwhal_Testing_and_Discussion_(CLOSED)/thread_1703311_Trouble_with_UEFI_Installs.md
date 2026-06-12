---
title: "Trouble with UEFI Installs"
date: 2011-03-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Espionage724 on 2011-03-09
(Results from Alpha 3 of Ubuntu 11.04)

I have two UEFI-compatible notebooks:

- CR-48 (yes the Google ChromeOS test notebook)
- Compaq 515

**Compaq 515**
Problem: The installer never starts; black screen

Steps Taken:
1. I insert the natty amd64 disc into my laptop
2. I press F9 to get to the boot menu
3. I press the EFI boot option
4. I find the bootx64.efi file located on the CD
5. I see a brief "no prefix set" error before seeing the GRUB2 menu
6. I press "Try Ubuntu before Installing"
7. It goes to a black screen that I am not able to pass.

Additional Info: Maybe it has to do with the graphics? I can run normal Ubuntu just fine though out the box without any modifications to anything. I'm not that great with linux, but I tried the vga=777 option and it did nothing. Maybe if I can get it to output all verbose info, I can see whats up?

**CR-48**
Problem: I cannot boot Ubuntu 11.04 after installing (no GRUB2 efi entry)

Steps Taken:
1. I put the SD card containing the natty amd64 desktop files into the netbook
2. I press F10 to get to boot menu
3. I select the EFI entry on the SD card
4. I press enter on "Try Ubuntu Before Installing"
5. I wait, then eventally I get to the desktop
6. I install Ubuntu, choosing to use the entire drive for Ubuntu
7. I restart
8. I can't start Ubuntu because theres no choice to boot it (my boot menu does not show the GRUB2 loader as a choice, nor does the EFI file chooser pick up the grub.efi file)

Additional Info: I notice the EFI partition exists, but it has the file structure in a way that I don't know if my laptop would recognize it. (the laptop is very picky about detecting the EFI loader, in other words, if it doesn't find a efi/boot/bootx64.efi file, I don't think it will show a choice to boot it).

Any ideas as to what I could try to make it work on either computer?

---

### Post by sanderj on 2011-03-09
Have you seen and read [https://wiki.ubuntu.com/Kernel/Testing/UbuntuUEFI](https://wiki.ubuntu.com/Kernel/Testing/UbuntuUEFI) ? It contains some variations (CD vs USB) and some experience based tips (like: install updates).

So maybe useful.

---

### Post by Espionage724 on 2011-03-09
Thanks for the info, but nothing there seemed to help.

Also on my CR-48 with Kubuntu 11.04 (the latest daily build, not alpha), the grub-efi installer failed to install. Screenshot included:

---

### Post by dino99 on 2011-03-09
is /target/ created ?

---

### Post by Espionage724 on 2011-03-09
I didn't check I went back to Ubuntu 11.04 alpha 3 a while ago to see something else.

But the strange thing is though is that Ubuntu 11.04 Alpha 3 installs just fine in UEFI mode (EFI partition exists, grub-efi installs without error, etc), it's just that I can't boot grub.efi from my UEFI bootloader.

Kubuntu 11.04 (today's daily) is the only one that fails with grub-efi

Edit:
Although I think I am onto something. I made the /efi/boot structure on my flash drive. I then took the contents of the grub folder from the 11.04 installation and threw them in the boot folder. I then made a copy of grub.efi and made it bootx64.efi.

I thought for sure it would work but now I'm at a grub rescue> prompt :( (maybe if I can get grub.cfg fixed, it might work?)

---

### Post by VMC on 2011-03-09
> **Espionage724 said:**
> I didn't check I went back to Ubuntu 11.04 alpha 3 a while ago to see something else.

But the strange thing is though is that Ubuntu 11.04 Alpha 3 installs just fine in UEFI mode (EFI partition exists, grub-efi installs without error, etc), it's just that I can't boot grub.efi from my UEFI bootloader.

Kubuntu 11.04 (today's daily) is the only one that fails with grub-efi

Edit:
Although I think I am onto something. I made the /efi/boot structure on my flash drive. I then took the contents of the grub folder from the 11.04 installation and threw them in the boot folder. I then made a copy of grub.efi and made it bootx64.efi.

I thought for sure it would work but now I'm at a grub rescue> prompt :( (maybe if I can get grub.cfg fixed, it might work?)
Run boot_info_script from a livecd then output the results back here.

---

### Post by Espionage724 on 2011-03-09
I ran the boot_info_script005.sh file with sudo sh but nothing is outputted.

---

### Post by oldfred on 2011-03-09
Is that a typo in your post or in the command you ran?

```
 sudo bash boot_info_script055.sh
```

---

### Post by alphaamanitin on 2011-04-25
> **Espionage724 said:**
> (Results from Alpha 3 of Ubuntu 11.04)

I have two UEFI-compatible notebooks:

- CR-48 (yes the Google ChromeOS test notebook)
- Compaq 515

**Compaq 515**
Problem: The installer never starts; black screen

Steps Taken:
1. I insert the natty amd64 disc into my laptop
2. I press F9 to get to the boot menu
3. I press the EFI boot option
4. I find the bootx64.efi file located on the CD
5. I see a brief "no prefix set" error before seeing the GRUB2 menu
6. I press "Try Ubuntu before Installing"
7. It goes to a black screen that I am not able to pass.[...]

Are you sure it is a black screen?  I have a very similar problem with a ASRock 880G Pro3 mobo.  The disk will boot fine in BIOS mode, but in UEFI mode I get the exact messages you do, except I do not have a solid black screen as 7.  If I look at the very top of the screen I have 2 to 4 mm of screen and can see my mouse if I move it up there.  

AlphaA

---

### Post by VMC on 2011-04-25
> **Espionage724 said:**
> I ran the boot_info_script005.sh file with sudo sh but nothing is outputted.

From the directory where its located copy&paste this:

```
sudo ./boot_info_script.sh
```

Then **RESULTS.txt** will be in that same directory.

---

### Post by oldfred on 2011-04-26
If running Natty & gpt partitions, you need this version. But I can see it does not parse all the efi files.

Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

I understand that Gert Hulselmans has been busy but was working on many updates for grub 1.99 and will get back to it soon. If you want to test with efi I am sure that it would help. Not many of us have efi systems.

---

