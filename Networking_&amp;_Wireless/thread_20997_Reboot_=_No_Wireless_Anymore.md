---
title: "Reboot = No Wireless Anymore"
date: 2005-03-19
forum: Networking &amp; Wireless
---

### Post by Mr Black on 2005-03-19
I spent a few days trying to get my wireless card working and I did via ndiswrapper.  See [this post](http://www.ubuntuforums.org/showthread.php?t=19978) for more info on that.

I just rebooted my Ubuntu system and now the wireless card isn't working anymore. I did notice some messages during boot.

Just after the system is uncompressing the kernel the follwoing message is displayed:

*PCI: Cannot allocate resource region 4 of device 0000:00:02.1*

Then the system continues to boot until the following is displayed:
[I]
*Starting hotplug subsystem...

Modprobe: FATAL: Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko): Operation not permitted

Modprobe: FATAL: Error inserting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permitted

*Configuring network interfaces...[/I]

Then the system will sit at the **Configuring network interfaces...* for a few minutes and then continue. Once I log into the system the wireless card isn't working.  I checked to see if the driver was still loaded and according to ndiswrapper it was loaded and the hardware was present.  

[I]jason@ubuntu:~ $ ndiswrapper -l
Installed ndis drivers:
rt2500  driver present hardware present[/I]

I then tried to reasign the driver to the device, but that didn't do any good either.

[I]root@ubuntu: # ndiswrapper -d 1814:0201 rt2500
ln: '/etc/ndiswrapper/rt2500/1814:0201.5.conf': File exists
Driver 'rt2500' is used for '1814:0201'[/I]

I also noticed that ndiswrapper has an option for recreating the hotplug information, and since the error message was just after the system was trying to load the hotplug subsystem I figured it was worth a shot.

*jason@ubuntu:~ $ ndiswrapper -hotplug*

Still no change.  I then figured I would try to redo the *modprobe* command that I used when setting up the device since that was the actual error while booting.

*root@ubuntu: # modprobe ndiswrapper*

Still no change. I didn't expect that to work anyway since I setup the modprobe alias when I initially setup the device, but just to make sure I checked.

[I]root@ubuntu: # ndiswrapper -m
modprobe config already contains alias directive[/I]

I don't know what else to look at or try to get the thing working.  None of the router settings were changed and I have no problem using my WinXP box so I'm pretty sure that its something on the Ubuntu box. I just don't know where to look or what to change in order to get it working.  Any idea would be great.

---

### Post by Mr Black on 2005-03-20
Ok, I was able to get the wireless card working again.  I have no idea why this happens, maybe cause ndiswrapper is just a "hack" to the kernel in order to get the wireless card working in the first place.

So, the reason why the wireless card wasn't working was due to an issue loading something related to ndiswrapper while booting.  It also seems to messup the loaded ndiswrapper module in the kernel.  So a simple running of two commands 

*modprobe -r ndiswrapper* #removes broken version of ndiswrapper module
*modprobe ndiswrapper* #adds back a new working version of ndiswrapper module

I just created a script and have it running on login via the sessions settings, which you can get to by going to Computer->Desktop Settings->Sessions and then click on the Startup Progams tab.

Once the ndiswrapper module is loaded back into the kernel you will need to go into the Computer->System Configuration->Networking and re-activate the wlan0 connection. (or what ever your connection is called) There is probably some way of doing this via a shell script but I haven't had the time to look into it yet. (I'm just glad I can get the damn thing working  :grin: )

This is kind of a half-assed work around, but it works and I don't plan on rebooting very often.

---

