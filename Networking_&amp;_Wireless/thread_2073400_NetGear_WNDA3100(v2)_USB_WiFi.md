---
title: "NetGear WNDA3100(v2) USB WiFi?"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by Cam! on 2012-10-19
I had to get a USB WiFi adapter due to a new router, and it won't work on my 64-bit 12.10 installation.

I know that I have to get the drivers from within Windows and do something with "ndiswrappers", but I'm not sure the exact method.

---

### Post by chili555 on 2012-10-19
Please run and post:```
lsusb
```Is ndiswrapper installed?```
sudo apt-get install ndisgtk
```We will be looking here: [http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173)

We will need Windows ***XP*** drivers and I have them for you, depending on your exact device. 64-bit is tricky, you lucky person!!!

---

### Post by Joseph Rinaldi on 2012-10-24
Hi,
I spent hours on this but found a simply way to get this working flawlessly.
1. From the Ubuntu Software Centre, install Windows Wireless Drivers (NDISWrapper) and the two add-ons, [FONT=Calibri]ndiswrapper-dkms and ndiswrapper-source.[/FONT]
[FONT=Calibri]2. I installed the latest drivers from Netgear on a Windows XP computer. (Just a VM will do, can be on a Linux Box).[/FONT]
[FONT=Calibri]3. This creates a folder in C:\Program Files\NETGEAR\WNDA3100v2\Driver, called WinXP2000. This contains the latest drivers for this adapter. The .sys file should be version 5.100.68.46.[/FONT]
[FONT=Calibri]4. Copy the folder to your Ubuntu (or Xubuntu) computer.[/FONT]
[FONT=Calibri]5. Run the Windows Wireless Drivers software and point to the inf file in this folder.[/FONT]
[FONT=Calibri]6. Reboot. All done![/FONT]

---

### Post by Cam! on 2012-11-21
How am I supposed to install something from Ubuntu Software Centre if I can't connect to the internet at all?

---

### Post by chili555 on 2012-11-21
> **Cam! said:**
> How am I supposed to install something from Ubuntu Software Centre if I can't connect to the internet at all?Do you have your install CD? Please navigate to pool > main > n > ndiswrapper and right-click both packages and select 'Open with Ubuntu Software Center.' Do the same with pool > main > n > ndisgtk.

---

### Post by Cam! on 2012-12-06
Ah. Makes sense. If I do this on an old version and upgrade, will I have to repeat the process?

---

### Post by chili555 on 2012-12-06
You can't have installed 12.10 that long ago. I'm sure the ndiswrapper versions on the CD will be fine. Is that what you mean?

---

### Post by Cam! on 2012-12-08
I'm going to install 12.04 LTS, and then upgrade.

---

### Post by Cam! on 2012-12-08
> **Joseph Rinaldi said:**
> Hi,
I spent hours on this but found a simply way to get this working flawlessly.
1. From the Ubuntu Software Centre, install Windows Wireless Drivers (NDISWrapper) and the two add-ons, [FONT=Calibri]ndiswrapper-dkms and ndiswrapper-source.[/FONT]
[FONT=Calibri]2. I installed the latest drivers from Netgear on a Windows XP computer. (Just a VM will do, can be on a Linux Box).[/FONT]
[FONT=Calibri]3. This creates a folder in C:\Program Files\NETGEAR\WNDA3100v2\Driver, called WinXP2000. This contains the latest drivers for this adapter. The .sys file should be version 5.100.68.46.[/FONT]
[FONT=Calibri]4. Copy the folder to your Ubuntu (or Xubuntu) computer.[/FONT]
[FONT=Calibri]5. Run the Windows Wireless Drivers software and point to the inf file in this folder.[/FONT]
[FONT=Calibri]6. Reboot. All done![/FONT]

That didnt work at all. I can't get Windows Wireless Drivers to show up.

---

### Post by chili555 on 2012-12-08
> **Cam! said:**
> That didnt work at all. I can't get Windows Wireless Drivers to show up.Aren't the files on the install CD as I outlined above?

---

### Post by Cam! on 2012-12-09
> **chili555 said:**
> Aren't the files on the install CD as I outlined above?

They are but I get an error while installing the ndisgtk file.

---

### Post by johnycsf on 2012-12-09
I have the SAME usb adapter and I spent about a week trying EVERY possible way to make it work.
Even after my computer says that it was successfully installed. It still wouldn't work.
So I had to buy an Alfa.
If this works for you. Please let me know!

---

### Post by chili555 on 2012-12-09
> **Cam! said:**
> They are but I get an error while installing the ndisgtk file.It will be helpful to know the exact error.

---

