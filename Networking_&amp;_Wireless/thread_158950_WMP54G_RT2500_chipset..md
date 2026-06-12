---
title: "WMP54G RT2500 chipset."
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by facehead on 2006-04-12
I'm new to not only Ubuntu, but Linux. I've read about ndiswrapper and installed it and used the correct drivers. I did not install them off the cd.

Both of these steps worked:

sudo ndiswrapper -i rt2500.inf
sudo ndiswrapper -l

rt2500 driver present, hardware present

Good stuff. When I modprobe ndiswrapper though the terminal seems to freeze. This isn't the case I've been reading about though where the whole thing freezes up and requires a restart, nor is it the case where I just don't realize that it's worked. The terminal goes from:

facehead@ubuntu > sudo modprobe ndiswrapper

to:

Nothing. And it stays that way until I close the terminal, nothing can be done in it. Now is this the kernal crashing? What am I doing wrong here?

Now I managed to find this link on the forums:

[http://doc.gwos.org/index.php/Rt2x00drivers]("http://doc.gwos.org/index.php/Rt2x00drivers")

But I don't get what's going on, not to mention I have a second problem.

Following this guide perfectly ([http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)) my NTFS partition still says I don't have permission to view it. Otherwise I'd have some text and stats copied straight over. Unforunately I have no floppy drive and no blank cd's so I have no other way of transferring files between Windows and Ubuntu. Can anyone help at all?

---

### Post by evilgold on 2006-04-12
rt2500 shouldnt need ndiswrapper, its the linux drivers are in the ubuntu kernel since breezy. without doing anything with ndiswrapper run this in a terminal  "ifconfig -a" see if somthing with rt... or ra... comes up. If it does, the card is already working.

Cant really help with your second problem, but try accessing it as root.

---

### Post by facehead on 2006-04-12
[QUOTE=evilgold]rt2500 shouldnt need ndiswrapper, its the linux drivers are in the ubuntu kernel since breezy. without doing anything with ndiswrapper run this in a terminal  "ifconfig -a" see if somthing with rt... or ra... comes up. If it does, the card is already working.

Cant really help with your second problem, but try accessing it as root.[/QUOTE]

I'll go do this except that it doesn't matter if I do or not. The card does not show up in Networking. If it is working it would be there.

EDIT: I'm sorry if this sounds arrogant/rude. Thank you for taking the time to respond, I'm just very frustrated.

---

### Post by evilgold on 2006-04-12
well i dont know if it would show up in networking if its not turned on, it will with ifconfig -a though. I've always done my wireless setup from the terminal. Anyways, if it doesnt show up AT ALL then there is probably somthing else wrong... is it a pci or a usb card?

---

### Post by facehead on 2006-04-12
It's a PCI card.

I did the ifconfig -a and it gave me two entries:

lo local loopback

and

sit0 IPV6-in-IPV4

Also perhaps worth noting is that when I start up it stops on loading hotplug (system?) and I have to hit alt-sysrq-e to get into Ubuntu.

Relating to the other problem I also get a "Mounting local filesystems...    failed" at startup before the hotplug thing happens.

---

### Post by mozetti on 2006-04-12
Just to confirm what **evilgold** stated. I have a Linksys WMP54G with the Ralink RT2500 chipset. The installer could not use the card, but the first time I logged in the WiFi card was listed in Admin-Networking. I just had to activate it.

If it's not showing up there, maybe installing the ndiswrapper/win drivers fouled something? Have you tried removing all that?

---

### Post by facehead on 2006-04-12
Thanks for the reply, and yes I did that before I tried ipconfig -a. Also the first thing I did after installing Ubuntu was to look in Networking where it still wasn't there, before I even knew of Ndiswrapper.

I hadn't run ipconfig -a before installing Ndiswrapper, however I did recognize the lo and sit0 entries both from the Network Tools menu, where there was nothing else.

---

### Post by evilgold on 2006-04-12
run "lspci" and post the results, if you can, just post the one regarding you rt2500 card. 

does the card work in windows?

to you second problem, please post your /etc/fstab and i'll try to help you out, I'll try to help you out setting it up correctly, but you could try the opposite and access your linux partition from windows, It's probably be easier to setup and you'll get read and write access. Thats what i do anyways.

---

### Post by facehead on 2006-04-12
[QUOTE=evilgold]run "lspci" and post the results, if you can, just post the one regarding you rt2500 card. 

does the card work in windows?

to you second problem, please post your /etc/fstab and i'll try to help you out, I'll try to help you out setting it up correctly, but you could try the opposite and access your linux partition from windows, It's probably be easier to setup and you'll get read and write access. Thats what i do anyways.[/QUOTE]

The "backwards" suggestion is an excellent one, I'll read up on setting that up right now.

I'll boot up in linux in a second and get you the lspci and /etc/fstab stuff but before i do that please just bear in mind that I can't ACTUALLY copy them, so I'll be transferring to a piece of paper and back here if the formatting looks off.

---

### Post by evilgold on 2006-04-12
here : [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

Provided your using the standard ext3 fs, and you shutdown linux properly last time, it should work right after install. You'll be able to acess your fstab from there... and for lspci run it like this "lspci > lspci.txt" That should output the results to lspci.txt in /home/yourusername... if you get the ext3fs driver working in windows it should be no problem copying and pasting.

---

### Post by facehead on 2006-04-12
[QUOTE=evilgold]here : [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

Provided your using the standard ext3 fs, and you shutdown linux properly last time, it should work right after install. You'll be able to acess your fstab from there... and for lspci run it like this "lspci > lspci.txt" That should output the results to lspci.txt in /home/yourusername... if you get the ext3fs driver working in windows it should be no problem copying and pasting.[/QUOTE]

Alright I'll get that done, but I copied the entries identically probably while you were posting that.

Two things in lspci worth noting:

0000:01:09.0 Network Controller: Ralink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)

0000:02:00.0 Ethernet Controller: Marvell Technology Group Ltd.: Unknown device 4362 (rev 19)

Now unless there is some way I have mistaken what chipset my card is using, I am sure it is a Linksys WMP54G PCI card, and windows uses the rt2500 drivers from the cd and it works that way. I suspect the other option is onboard which is not an option for me because even if it did work I don't have access to the router, and can't enter a MAC address for that into the router.

As for fstab

# /etc/fstab: static file system information.
#
#<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc               /proc                proc     defaults          0            0
/dev/sda2       /                      ext3     defaults,errors=remount-ro 0       1
/dev/sda5       none                 swap    sw                 0            0
/dev/hda         /media/cdrom0   udf,iso9660 user,noauto   0         0
/dev/sda1       /media/windows  ntfs       defaults,unmask=0222      0        0

before I had "defaults" on sda1 set to nls=utf8 but I changed it to see if it would help at all (it didn't.) Anyhow I'll try this link you sent me for that.

---

### Post by evilgold on 2006-04-12
well i'll check back with you tomorrow, I'm going to bed now. 

Last thing i can think of is, go here: [https://wiki.ubuntu.com/WifiDocs/RalinkRT2500](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500)
and/or here;
[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500/DriverAndRaconfig](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500/DriverAndRaconfig)

---

### Post by facehead on 2006-04-12
I tried that program, unfortunately it asks me to format the drive whenever I try and browse it.

I looked in their faq and downloaded their mountdiag program to see what it had to say:

[[IMG]http://img82.imageshack.us/img82/6295/mountdiag4sl.jpg[/IMG]](http://imageshack.us)

Apparently Ubuntu isn't actually shutting down properly now I don't think. The same "mounting local file systems" that failed in startup now fail in dismounting because the drive is busy?

I took what I added to fstab out again, restarted, and shut down and it still messes up. At this point I'm not sure how much I can do, according to the one site you sent me I need another pack of drivers and perhaps some packages to install as well.

What version of Ubuntu do you use if you have an rt2500 card that works? Are you using 6? Would that be worth maybe formatting and trying?

---

### Post by mozetti on 2006-04-12
1) WMP54G - it **is** the RT2500 entry in your lspci. In Admin-Networking, can you see the onboard ethernet controller? If so, deactivate it - maybe it's causing confusion since Ubuntu reports it as and unknown device?

I'm thinking your RT2500 issues are happening because of these other issues. Hopefully if you get them cleared up, the WiFi card will start working. Mine was easy -- just be aware, **don't** use the 686-smp kernel because the current RaLink drivers don't work with an smp kernel. Just go with the regular 686 kernel if you upgrade.

2)fstab - can you boot a Live CD, mount the partitions, then reboot into Windows? Maybe if the Live CD unmounts them properly, Windows will be able to use them. I also installed the Windows EXT2 file system driver, and it works fine on my computer.

---

### Post by facehead on 2006-04-12
Hi Mozetti,

There isn't anything in Networking other than a disabled ppp0 connection that can't be removed.

I am doubting that the other issues (the fstab thing) is the cause for my rt2500 problems simply because they've been an issue since before I even tried mounting a drive or editing anything in fstab. I'm not actually aware of anything about kernels or smp other than the driver I used with ndiswrapper wasn't that kind (it said nosmp somewhere.) I'll try reading up on it though. Thanks for your reply.

---

### Post by mozetti on 2006-04-12
Well, I was actually thinking that your Hotplug Subsystem problems were the cause of your network adapters not showing up. I'm new, thought, so I could be completely out of the ballpark on that one. Maybe you can disable the wired-ethernet port in your BIOS so Ubuntu doesn't even see it? If that was causing some of your problems, maybe removing it from the equation will help?

The Kernel I was referring to was the linux kernel. Ubuntu installs the i386 kernel, which should work with most processors. If you have a newer Intel Processor, you can upgrade your kernel to 686 or 686-SMP (designed for Hyperthreading/Dual-cores/Multiple-processor machines). I upgraded to 686-SMP and my system stopped responding. The regular 686 kernel works fine, though. I had just put that in there as some advice if you decide to upgrade your kernel later. ;)

---

### Post by facehead on 2006-04-12
[QUOTE=mozetti]Well, I was actually thinking that your Hotplug Subsystem problems were the cause of your network adapters not showing up. I'm new, thought, so I could be completely out of the ballpark on that one. Maybe you can disable the wired-ethernet port in your BIOS so Ubuntu doesn't even see it? If that was causing some of your problems, maybe removing it from the equation will help?

The Kernel I was referring to was the linux kernel. Ubuntu installs the i386 kernel, which should work with most processors. If you have a newer Intel Processor, you can upgrade your kernel to 686 or 686-SMP (designed for Hyperthreading/Dual-cores/Multiple-processor machines). I upgraded to 686-SMP and my system stopped responding. The regular 686 kernel works fine, though. I had just put that in there as some advice if you decide to upgrade your kernel later. ;)[/QUOTE]

Yeah thanks for that, I mighta done that otherwise. I agree with the hotplug part I think because I don't like/understand having to override that to boot up Ubuntu. Does anyone know why this is happening? I can try disabling the Ethernet controller though and I'll be back to tell if it made a difference or not.

---

### Post by facehead on 2006-04-12
Apparently it did make a difference. Now, not only is the hotplugs issue not resolved, the gui won't start at all. I'm left with a terminal. I'm VERY confused.

I feel this leaves me with no other option but to format and start fresh, so I'd like to ask some opinions. Breezy or Dapper? Live or install? In the Installer there was a screen with network options to fill out. I didn't bother because I didn't have them for sure as most of them are automatically assigned by windows. Was it bad that I skipped this? Any advice for restarting and any things i should make sure to burn to take into Ubuntu?

---

### Post by mozetti on 2006-04-12
Well, when I did my install I used the hard-wired onboard ethernet connection (eth0) because my WiFi (ra0) didn't work in the installer. My router is running DHCP, and the installer configured eth0 for the install. 

The installer does download some things, I believe, so maybe you missed some parts of the install if you weren't online? Try re-installing with a wired connection. If you have DHCP set up on your router or ISP, try to use that. If not, you can put in your IP addy info (subnet, default gateway, etc) manually and try to connect that way.

---

### Post by facehead on 2006-04-12
Thanks for the suggestion but as I need a mac address to enable me to connect to the internet and I don't have access to the router this card is my only option. Also, I need to enter in a WEP key.

---

### Post by evilgold on 2006-04-12
I just got around to setting up my ntfs partition to work under linux, heres the fstab entry for it

/dev/hda1 	/windows	ntfs 	ro,nls=utf8,umask=0222 0 0


you'd have to change /dev/hda1 to  /dev/sda1, and make sure you have a /windows ("sudo mkdir /windows" if you dont)

---

### Post by facehead on 2006-04-13
[QUOTE=evilgold]I just got around to setting up my ntfs partition to work under linux, heres the fstab entry for it

/dev/hda1 	/windows	ntfs 	ro,nls=utf8,umask=0222 0 0


you'd have to change /dev/hda1 to  /dev/sda1, and make sure you have a /windows ("sudo mkdir /windows" if you dont)[/QUOTE]

what I did, except without the "ro." I'll probably be absent from here for a day or two, but I'm going to reinstall Ubuntu and see how things go.

---

### Post by sadjack on 2006-04-13
I have a Belkin PCMCIA card which has the Ralink RT2500 chipset. There are drivers for this chipset at [www.serialmonkey.com](www.serialmonkey.com) follow the link to sourceforge and download the driver from there.

Ubuntu, as far as I can tell, see's the card, identifies it but still needs the drivers installed. I could be wronge there, but after installing the drivers, my card works.

Just something else to try.

---

