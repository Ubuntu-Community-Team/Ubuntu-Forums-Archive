---
title: "unable to connect to LAN from laptop"
date: 2005-01-19
forum: Networking &amp; Wireless
---

### Post by nightmorph on 2005-01-19
Here's the scoop:

I have an Intel Pro/100 integrated ethernet card on my laptop (Toshiba Satellite 2805-S603). The Ubuntu LiveCD (and any other distro's liveCD, actually) uses my card just fine; I can connect to both the internet and my Windows network.

However, not only was Ubuntu not able to detect my card (or network, which uses DHCP or whatever it is) during the install process, it is still unable to use it now that it's been installed.

LiveCDs still work; the OS on my harddrive doesn't. What gives? I went into the Gnome networking options and changed from "loopback" to the card on "eth0", which was somewhat recognized; at least, some correct information about it was displayed.

I know that my IP address, gateway, and subnet mask are correct, but I don't know why I can't even ping an IP or website. I'm borrowing another computer to write this thread, so it might be a day or so before I'll be able to review any responses.

As a first-time Linux user, I have no real idea where to find relevant information or configuration files for my card; the filesystem is still somewhat of a mystery to me, despite my best efforts to understand what goes where.

So if you'd please bear with me and point out the location of files to check/alter?

Thanks.

---

### Post by poofyhairguy on 2005-01-19
[QUOTE=nightmorph]Here's the scoop:

I have an Intel Pro/100 integrated ethernet card on my laptop (Toshiba Satellite 2805-S603). The Ubuntu LiveCD (and any other distro's liveCD, actually) uses my card just fine; I can connect to both the internet and my Windows network.

However, not only was Ubuntu not able to detect my card (or network, which uses DHCP or whatever it is) during the install process, it is still unable to use it now that it's been installed.

LiveCDs still work; the OS on my harddrive doesn't. What gives? I went into the Gnome networking options and changed from "loopback" to the card on "eth0", which was somewhat recognized; at least, some correct information about it was displayed.

I know that my IP address, gateway, and subnet mask are correct, but I don't know why I can't even ping an IP or website. I'm borrowing another computer to write this thread, so it might be a day or so before I'll be able to review any responses.

As a first-time Linux user, I have no real idea where to find relevant information or configuration files for my card; the filesystem is still somewhat of a mystery to me, despite my best efforts to understand what goes where.

So if you'd please bear with me and point out the location of files to check/alter?

Thanks.[/QUOTE]


did you try to activate the network using the gnome network tool?

Often my computer needs me to go in and activate its network!

---

### Post by nightmorph on 2005-01-20
[QUOTE=poofyhairguy]did you try to activate the network using the gnome network tool?

Often my computer needs me to go in and activate its network![/QUOTE]

Yes. The Gnome tool is completely unhelpful. The problem originally began during the Ubuntu installation process; the install CD couldn't find my hardware, although somehow it did know one of the drivers needed for its type and "included" it in the kernel or something like that. But it didn't recognize my DHCP network; it said there wasn't one, which of course there is.

None of the options provided through Gnome controls seem to be working.

---

### Post by bin on 2005-01-20
Sounds a little bizarre but.....

Couple of questions.

If you load up the gnome network settings tool, it souds like it is listing the ethernet device. It should be showing Ethernet LAN card as eth0 and the active box should be ticked.

If it is not ticked, when you click on Activate does it do anything.

Assuming you've gone this way before, keep the network settings tool open, then open a terminal and type lspci and hit return.

It should show amongst the guff Ethernet Controller: Intel Corp [Ethernet Pro 100]

If it does, then do lsmod and hit return. In the longish list look for e100.
If it is not there, do sudo modprobe e100 and hit return - put in password when asked.

If it just comes back to the prompt, then go back to the network tool and try the activate button again.

Please report what happens.

in light

bin

---

### Post by nightmorph on 2005-01-20
Nothing, apparently. Turns out that if I have selected automatic DHCP on the tools menu, the card WILL BE deactivated. Switching settings to manual lets me work with the tool again, but nothing is working just yet, even though the card is activated and is set to be activated on boot.

So now I will probably have to reinstall gnome again, since I made the mistake of restarting to load a few modules into the kernel; I didn't know if there was a way to activate modules like agpgart, eepro100 (or whatever it was), etc. except during boot.

That's the problem with my installation; on the rare chance that I get the base system + Gnome working, if I reboot the boot process will hang immediately after the "starting hotplug" dialog; I get an odd modprobe: FATAL error, the one the FAQs address (pcieh and schpch or whatever they were). Placing them in /etc/module/blacklist doesn't help, and neither does running modprobe to load the needed network module(s). For that matter, even editing the "load these modules at bootup" file, whichever it was. Sorry. It's been a long, unsuccessful night, and I still don't know the ins and outs of my system.

For the record, I am typing this from the laptop in question, but using the LiveCD. Even when I try to match settings displayed in the network tools and networking dialogs, the installed system still doesn't recognize my DHCP network.

Oh, and on the network tools dialogue, when I highlight "ethernet device eth0" and click "configure" I get a prompt for root password. When I enter my user password I get a message saying "the password entered is invalid." So, I remain unable to even explore the options available in this particular config tool.

---

### Post by nightmorph on 2005-01-20
Output of **lspci**  (from working Warty LiveCD) as requested:

0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
0000:00:01.0 PCI bridge: Intel Corp. 82815 815 Chipset AGP Bridge (rev 11)
0000:00:1e.0 PCI bridge: Intel Corp. 82801BAM/CAM PCI Bridge (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BAM ISA Bridge (LPC) (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801BAM IDE U100 (rev 03)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 03)
0000:00:1f.6 Modem: Intel Corp. Intel 537 [82801BA/BAM AC'97 Modem] (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
0000:02:03.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:02:07.0 Multimedia audio controller: Yamaha Corporation YMF-754 [DS-1E Audio Controller]
0000:02:08.0 Ethernet controller: Intel Corp. 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
0000:02:09.0 System peripheral: Toshiba America Info Systems TC6371AF SmartMedia Controller
0000:02:0d.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 31)
0000:02:0d.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 31)


who knows, maybe I need a software package or drivers that can work with my hardware. Would it be anything that would fit on a floppy, this enabling me to download it using the LiveCD and transferring it to the installed system? All this WITHOUT rebooting and causing me to have to reinstall Ubuntu?

---

### Post by bin on 2005-01-20
The fact that all this runs smoothly from the live cd but is giving grief on the install makes me wonder about the install CD that you are using.

Your hardware is not particularly esoteric, maybe a quick search in google land would point up any generic linux / toshiba incompatibilities.

I haven't looked at the ubuntu live cd so I don't know if you installed from that or a different source. If it was a download I would suspect possibly a bad file or bad burn - I've had a few, but then again, too few to mention :-({|= .........sorreeeee.

It is a Warty *install* that you are working from?

One useful source of information is the dmesg command, you can also look at this in /var/log various files. What it does is to show you all the rubble that runs down the screen when you boot, and which sometimes contains useful info about device loading probs.

in light

bin

> Oh, and on the network tools dialogue, when I highlight "ethernet device eth0" and click "configure" I get a prompt for root password. When I enter my user password I get a message saying "the password entered is invalid." So, I remain unable to even explore the options available in this particular config tool.  This puzzles me. Are you going Computer, System Configuration, Networking? If so, the password is when you start the app. You then select the card and hit properties.

---

### Post by nightmorph on 2005-01-20
[QUOTE=bin]
I haven't looked at the ubuntu live cd so I don't know if you installed from that or a different source. If it was a download I would suspect possibly a bad file or bad burn - I've had a few, but then again, too few to mention :-({|= .........sorreeeee.

It is a Warty *install* that you are working from?

One useful source of information is the dmesg command, you can also look at this in /var/log various files. What it does is to show you all the rubble that runs down the screen when you boot, and which sometimes contains useful info about device loading probs.

  This puzzles me. Are you going Computer, System Configuration, Networking? If so, the password is when you start the app. You then select the card and hit properties.[/QUOTE]

No, I am using the official Ubuntu LiveCD and Install CDs shipped to me via the ShipIt distribution system; I ordered them back in November and they only arrived a week or so ago. The Install CD has an option to verify disc/data integrity, and the CD informs me that it checks out cleanly. It's Warty 4.10 on both CDs, as far as I know, although the documentation tells me that the actual install is more "Ubuntu-like" than the LiveCD. Or something like that.

Oh, and I did run dmesg before I made the mistake of rebooting the system; it had a lot to tell me, but nothing caught my attention, though admittedly I'm not positive about what I should be looking for.

Perhaps I should clarify: I am now unable to boot the installed system AT ALL; I get two errors, each repeated once during the boot, something along the lines of:

"module: FATAL: failure to insert /lib/modules/2.6.8.1-3-386/pci/hotplug/shpchp.ko : operation not permitted."

I get this message paired with the pciehp.ko module in the same directory; both messages appear twice immediately after the hotplug begins. Even when my system was up and running (immediately after install), though I added a few other modules shortly before them, thinking they were dependent (though depmod didn't work), nothing makes them go away, not even restoring the /etc/module/blacklist file to its original state.

Now the only way I can get into my system is by using this LiveCD and hacking into the config files, whereever they might be.

And I've used both Computer > System Configuration > Networking as well as Applications > System Tools > Network Tools, and neither of them were able to resolve my network difficulties.

It's the latter Network Tools that prompts for the admin/root password; it does it in this LiveCD, too. I have no idea what options might be on it.

I did notice that many of the config files for both networking and Xfree86 seem to be much more... "complete", if that's the word, than the ones on the installed system. However, I'm hesitant about altering them, unless there is one single config file that contains all the necessary settings; I don't want to have missed something crucial that is kept in another file.

Would copying some/most/all of the config files from this LiveCD to the respective directories on hda3 solve my networking woes? I can paste the contents of any files from the installed system if they're necessary, and if you could point me in their direction. At least I can still access the partition.

---

### Post by nightmorph on 2005-01-23
Never mind. I've switched to Gentoo.

It's a shame that the LiveCD works so well (possibly because it uses Morphix) and the install CD is so worthless

My hardware isn't particularly esoteric, so I've gone with a distro that actually supports my system.

But really, the LiveCD is nice. Installation just doesn't work, that's all. If installation from the LiveCD was possible, I'd put it on my computer without question; Ubuntu is very nice.

But until I see some more progress, I won't be touching it again any time soon.

---

### Post by ommy69 on 2006-02-10
Hi I am having a somewhat similar problem.  I am using gentoo.  This is my first linux box.  Here is the issue.  I am trying to install gnome.  But after installing grub and booting into the Command Line i ran emerge gnome.  Failed because it couldn't connect to the net.  After some researching i found my nic isn't loading in a normal boot.  I use module e100.  I can load the module in livecd and connect to the net but when i boot normally i cannot load it.  when I ls /lib/modules/2.6.15-gentoo-r1/kernel/drivers/net the only things in there are dummy.ko and s2io.ko.  So long store short and my question is:
How do I get this driver from the cd to my hda?

---

