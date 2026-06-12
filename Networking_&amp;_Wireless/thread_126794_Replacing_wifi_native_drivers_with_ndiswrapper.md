---
title: "Replacing wifi native drivers with ndiswrapper"
date: 2006-02-07
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-02-07
How would I deactivate/unload or prevent native linux wifi drivers (airo.o/airo_cs.o) from loading at boot so that I can install ndiswrapper with XP drivers instead. I'm doing this to get WPA connection with my PCMCIA card. Thanks.

---

### Post by mpvano on 2006-02-07
Using sudo, create and edit a file in

/etc/hotplug/blacklist.d

Name the file something you'll remember like "myblacklist"

list, one per line, the names of the modules (note - the NAMES, not the filenames) that you do NOT want loaded automatically.

You also need to make sure that modules are not being loaded anywhere else by non-hotplug means. For wireleass, this means checking

/etc/modules

which is a similar file containing a list of modules which are unconditionally loaded early in the startup process because they may be needed later in the boot process.

For example, one of my machines uses orinoco wireless drivers, of which there are many flavors, but the automatically selected choice is the "orinocoxxx" drivers.

To load alternative drivers I need to have the following in my /etc/hotplug/blacklist.d/wireless file:

orinoco
orinoco_cs
orinoco_pci

If you want to change your mind and allow those drivers to take effect again, just put an octothorpe (#) character ahead of each line - that will make it into a comment.

CAUTION! If you use an editor that leaves backup files around, THE BACKUP FILE WILL BE TREATED AS A BLACKLIST FILE AS WELL. This is very confusing to deal with! If your editor works this way, make sure you manually delete the backup file after editing or you may find yourself scratching your head trying to understand why your edit seems to have had no effect.

Of course the blacklist file is only read at a hotplug opportunity like at boot time or when a removable card is plugged in. You won't see any effect for already loaded modules until that happens. In some cases (i.e. built-in wireless cards), you may see no effect until you reboot.

hope this helps,

Mario

---

### Post by ssalman on 2006-02-08
Thanks Mario for your help, but it did not work for me :confused:, This card is driving me crazy:evil:.

I created a file "MyBlackList" and had two lines in it:
```
airo
airo_cs
```

rebooted and I got to gnome, the card was blinking, and when I used "lsmod | grep airo" the modules were loaded.

I checked the /etc/modules file and nothing relating to airo was there... how is it that drivers keep on getting loaded??

---

### Post by mpvano on 2006-02-08
Sorry, momentary lapse - You said you have a pcmcia card...

Try this:

Run cardinfo from the run dialog or from a terminal shell. It will let you find out the pcmcia information for your card.

Then find that line in /etc/pcmcia/config and comment out the whole stanza (all the lines up to the next blank line).

You might continue the search and see if there are other lines matching the card info.

Note that you may also need to use the other blacklist methods I suggested as well, depending on how your replacement driver is loaded. I suggest removing the lines from them to start with, however.

If you still can't get it to stop loading, you should also note that there are other ways a driver can be loaded - one method is as a dependency of another driver. You might try the following and see if some other module loads  your driver as something it requires:

lsmod | grep airo and see if airo... shows up anywhere else.

hope this is the right info this time....

Mario

---

### Post by ssalman on 2006-02-09
Thanks Mario, it worked :D...

Now I will experiment with NDISwrapper... :mrgreen:

Thanks to you, I've learned 3 new things: how to blacklist a pci device, stop a PCMCIA device from loading, and that cardinfo existed!! 

Thanks.

---

