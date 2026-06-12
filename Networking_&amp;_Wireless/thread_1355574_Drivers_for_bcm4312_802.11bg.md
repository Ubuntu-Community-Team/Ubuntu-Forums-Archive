---
title: "Drivers for bcm4312 802.11b/g"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Matthew M on 2009-12-15
I just set up an Ubuntu partition on my Vista laptop, and I can't get wireless to work. Right now I'm on a wired network.

I have a bcm4312 wireless card, and I've downloaded both a Windows driver from the HP website and a Linux driver from the wireless card support website, but I don't know how to use either.
I understand that to use the Windows driver, I need to run it through ndiswrapper somehow, but I don't understand how to run ndiswrapper. When I click on it, it just opens up into folders of more and more individual packets of code. The Linux driver is set up in a similar way; I just don't know what to do with it. My Windows driver is an .exe and shows me an error message when I try to extract files:

Archive:  /home/matthew/Downloads/sp45222.exe
[/home/matthew/Downloads/sp45222.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/matthew/Downloads/sp45222.exe or
          /home/matthew/Downloads/sp45222.exe.zip, and cannot find /home/matthew/Downloads/sp45222.exe.ZIP, period.

I realize that there's a sticky for troubleshooting ndiswrapper, but I really don't understand the language used there; I am extremely new to this. Sorry.
Thank you for your help!

---

### Post by Bachstelze on 2009-12-15
In order to extract the Windows driver from the EXE, you must use cabextract.

```
cabextract sp45222.exe
```

The Linux driver is probably some source code you have to compile, you should have a README somewhere in the source archive.

---

### Post by Matthew M on 2009-12-15
matthew@MATTHEW-PC:~$ cabextract sp45222.exe
The program 'cabextract' is currently not installed. You can install it by typing:
sudo apt-get install cabextract
cabextract: command not found


That is the result I got. Do I need to download cabextract somewhere?

---

### Post by Matthew M on 2009-12-15
I also could not find a readme for the Linux driver.

---

