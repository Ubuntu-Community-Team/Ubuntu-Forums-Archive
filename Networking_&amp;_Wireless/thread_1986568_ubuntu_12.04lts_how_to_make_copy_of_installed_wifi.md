---
title: "ubuntu 12.04lts how to make copy of installed wifi card driver?"
date: 2012-05-25
forum: Networking &amp; Wireless
---

### Post by ubto66 on 2012-05-25
About: Getting a copy of a wifi card driver in ubuntu 12.04lts.
   

Info: My wifi card is not supported by default by ubuntu 12.04lts.
To make the wifi card run I do this:
I connect the wifi card to the computer. I connect the computer to the internet, using a lan cable. The lan driver is installed by default on the system.
I try to install this deb package on the system: linux-firmware-nonfree_1.8_all.deb
Ubuntu refuses, and offers to install its own driver. Clicking 'install' in ubuntu software center, that happens.
After that the wifi card is running stable.
I think that ubuntu also updates the driver when hitting 'software updater', but I'm not sure.
 

Q: Can I somehow make a copy of the installed wifi card driver, so I will be able to install the driver, without having internet access?
Thanks.

---

### Post by chili555 on 2012-05-25
It depends on the specific driver and wireless card. It actually sounds like you only needed firmware and, if so, we can copy that to a USB stick or CD and you can install it without internet access easily. Let's find out for sure. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by ubto66 on 2012-05-28
Thank you for answering. I wrote the code lspci -nn | grep 0280
but nothing happens.
Terminal just answers nothing.
Does it matter that the os is running on a usb stick?

---

### Post by chili555 on 2012-05-28
> Does it matter that the os is running on a usb stick? Not really.

We need to know about your wireless card in order to see how to proceed. Is it a PCI internal card? If so, please run:```
lspci -nn
```Pick out the line that relates to your wireless card and post it here. Is it a USB card?```
lsusb
```Thanks.

---

### Post by ubto66 on 2012-05-29
Its a usb wifi card.
 
I wrote the command and  it listed that a 
usb keyboard and usb pc mouse is connected.
And that my dell wifi card is connected, and there is an id number and an intersil number, what are they?
Thank you.

---

### Post by chili555 on 2012-05-29
> And that my dell wifi card is connected, and there is an id number and an intersil number, what are they?Yes, indeed; what are they? Without knowing those wifi card details, I don't know how I can help you. Can't you jot them down on paper so you can post them here?

---

### Post by ubto66 on 2012-05-30
Its ven413c pid8104. And isl3887, I've googled it and it should be the card's chipset.

---

### Post by chili555 on 2012-05-30
The driver in question p54usb requires firmware as you may have guessed. Let's make a copy of the firmware so you can keep it on a USB key or CD. Please open a terminal and do:```
mkdir firmware
sudo cp /lib/firmware/isl3887usb ~/firmware
sudo cp /lib/firmware/isl3886usb ~/firmware
sudo cp /lib/firmware/prism54usb ~/firmware
```Now you can look in your user directory and find the folder *firmware*. Copy it to a USB key or CD. 

The driver itself, p54usb, is installed by default in most Linux distributions.

Now if you ever have to reinstall, reverse the process. Drag and drop the folder from the USB key or CD to the user directory. Open a terminal and do:```
sudo cp ~/firmware/* /lib/firmware
```Now unload the driver and reload it so it sees and grabs the firmware:```
sudo modprobe -r p54usb
sudo modprobe p54usb
```You may want to copy and paste these instructions into a text document to keep on the USB key or CD so you'll recall how to proceed.

---

### Post by ubto66 on 2012-05-31
I followed your instructions.
When I run 
sudo cp /lib/firmware/prism54usb ~/firmware
I get this error message
x@y:~$ sudo cp /lib/firmware/prism54usb ~/firmware
cp: cannot stat `/lib/firmware/prism54usb': No such file or directory
x@y:~$

I found the firmware folder in lib.
It contains 1079items, both folders and files, 52.7mb in total.
Do I understand it correctly that I shall copy the whole firmware folder?
And doing the installing of the wifi firmware, by pasting the whole folder into
the lib folder and then run sudo cp ~/firmware/* /lib/firmware, sudo modprobe -r p54usb
and sudo modprobe p54usb?
That means that in a new ubuntu 12 installation there is no firmware folder?
I haven't actually tried to paste the copied firmware folder into a new installed ubuntu 12 installation yet. 
I wanted to give you these pieces of information, before reinstalling ubuntu 12 on the usb stick.
Thank you for your effort. For me finding the location, and the commands seems complicated.

---

### Post by chili555 on 2012-05-31
> Do I understand it correctly that I shall copy the whole firmware folder?No. That command was to copy *ONLY* the firmware file named prism54usb, after you had also copied isl3887 and isl3886. However, as happens, I made a mistake. There is no firmware file prism54usb! I apologize. Please skip that step only.> And doing the installing of the wifi firmware, by pasting the whole folder into
the lib folderNo. You are going to pluck two files only out of your existing /lib/firmware file: isl3886 and isl3887. When and if you need to reinstall, copy them from the USB or CD and place them in the very full existing /lib/firmware file.> That means that in a new ubuntu 12 installation there is no firmware folder?Incorrect; there is a /lib/firmware folder. It just doesn't contain just two little firmware files you need, isl3886 and isl3887. As you said in your first post, you installed linux-firmware-nonfree. One of the dozens of components of that package is firmware files you need, isl3886 and isl3887. So our strategy, now that you have them, is to copy just those two to a new folder and file it away on a CD or USB so you can restore those two to /lib/firmware at any time. 

Is that clearer now? If not, please ask. That's why I'm here.

---

### Post by ubto66 on 2012-06-02
Ok, I looked for file isl3886 and isl3887. Finding them is not that easy.
I go to places and computer and File system and lib and firmware folder.
In the firmware folder are many folders and files present.
There are these isl files present.
isl3877 <---          its isl3877 and not isl3887
isl3886pci
isl3886usb
isl3887usb
isl3890
Whether there are isl files in the firmware subfolders, I do not know.
I know you stated, that I should only copy these files named
isl3886
isl3887
But none of them are there..
Among the 5 files I stated, can you please confirm whichones that must be copied, if any?
Thanks.

---

### Post by chili555 on 2012-06-02
> There are these isl files present.
isl3877 <--- its isl3877 and not isl3887
isl3886pci
[COLOR="Red"]isl3886usb
isl3887usb[/COLOR]
isl3890I believe your driver needs the ones I've highlighted. However, CD and USB space is cheap; why not copy them all and be sure? All of them together are only about 200Kb.

---

### Post by ubto66 on 2012-06-03
You are right. I will copy all files, and try to reinstall ubuntu on the usb stick. And then check again what isl files are already there in the firmware folder. 
Thank you.

---

### Post by ubto66 on 2012-06-09
[SIZE=2]I now have reinstalled ubuntu 12 on a usb stick.[/SIZE]
 [SIZE=2]It turns out, that in the lib/firmware folder, none of the files[/SIZE]
 [SIZE=2]isl3877 [/SIZE] 
 [SIZE=2]isl3886pci [/SIZE]
 [SIZE=2]isl3886usb [/SIZE]
 [SIZE=2]isl3887usb [/SIZE]
 [SIZE=2]isl3890[/SIZE]
 [SIZE=2]are present, so I guess I have to paste all 5 files into the lib/firmware folder?[/SIZE]
 [SIZE=2]You wrote:[/SIZE]
 “[SIZE=2]Drag and drop the folder from the USB key or CD to the user directory.”[/SIZE]
 [SIZE=2]I'm not sure what you mean.[/SIZE]
 [SIZE=2]I'm not able to paste any file into this folder: lib/firmware.[/SIZE]
 [SIZE=2]And I don't now how to change permissions?[/SIZE]
 [SIZE=2]Can you specify, how I can get the files into the firmware folder?[/SIZE]
 [SIZE=2]If I had knew how difficult this is, I probably had not asked the question.[/SIZE]
 [SIZE=2]Thanks.[/SIZE]

---

### Post by chili555 on 2012-06-09
When you insert the USB key, it should pop open a window showing the contents of the key. Drag and drop everything in there to your desktop.

The cntents of /lib/firmware are owned by root. Only the super-user, root, can add, remove or change files in there. Let's become a super-user temporarily. Open a terminal and do:```
[COLOR="Red"]sudo cp Desktop/isl38* /lib/firmware[/COLOR]
```Now we unload and reload the driver so it sees the shiny new firmware:```
sudo modprobe -r p54usb
sudo modprobe p54usb
```

In the command I highlighted above, we said we wish to do a command as super-user: sudo. We copied (cp) every file on the desktop named isl38something to /lib/firmware. I hope that makes it a bit clearer.

---

### Post by ubto66 on 2012-06-21
Thank you.  It runs. You know what you're doing.

---

