---
title: "Getting iPod setup with Amarok?"
date: 2008-08-18
forum: Multimedia Software
---

### Post by kooldino on 2008-08-18
I have an iPod nano 3g (fatty).  

I have the latest and greatest library and such that will apparently allow Amarok connect to my iPod.

However, I don't understand how to do it.

When I go to Devices-> Connect, I am prompted with a dialog to configure my media device. 

For my pre-connect command, I enter 

```
sudo mount /dev/sdd /media/IPOD
```

The above is how I mount it through the command line, so I figured it should work.  I tried it without the sudo, but it made no difference.

Here's the output of an fdisk -l:

```

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         280     7765508    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 32)
Partition 1 has different physical/logical endings:
     phys=(120, 216, 32) logical=(279, 126, 32)

```

I'm not quite sure what I'm supposed to be doing here...

---

### Post by mc4man on 2008-08-18
I was just as confused doing this last wk. Forget the precomm. and eject comm. screen. You  either use the main setup screen or if not, the add screen.
See here  and look at 2nd screenshot.
[http://ubuntuforums.org/showthread.php?p=5610808#post5610808](http://ubuntuforums.org/showthread.php?p=5610808#post5610808)

You really only want to set the plugin and if need be give it a name. (anything simple
**Don't set a mountpoint** in the configure.

After the device is configured there's a way to pick a specific ipod model from a list. I stumbled across it and atm can't stumble back. Don't think it matters much, may be just a naming thing.

The default eject comm. will work even though it will say it fails. (it may not error message in kubuntu

Edit: here's the initial set up screen showing the device in name box. (would probably be sdd1 for you 

If you see that then just pick the plugin, apply and your done. Otherwise try autodetect and or add, ect.

---

### Post by kooldino on 2008-08-18
Awesome, I'll give this a whirl when I get home.

---

### Post by kooldino on 2008-08-19
Ok great, seems like everything worked out.  The only iffy thing is when I "safely remove" my iPod, it still says "Connected" on the iPod's display.

---

### Post by kooldino on 2008-08-20
Does anyone know if the above is kosher?

---

### Post by mc4man on 2008-08-20
> Does anyone know if the above is kosher? 
Well it certainly doesn't seem right.
I use Ubuntu where 'eject' works perfectly with ipods.

It seems kubuntu wants to 'safely remove' which doesn't work, the ipod should be ejected. 
Unfortunately 'eject' seems to only work as root, so 'sudo eject /dev/sdxx' seems to properly eject the ipod. (any  way I've tried to eject thru amarok only unmounts the ipod and ejects (opens) the dvd drive

I'd do some research, I remember reading something about this though I think it was 7.04 or 7.10

Also noticed occasionally when plugging in the ipod kubuntu 'sees' it as a disk drive, yet another way the default kubuntu install is slightly 'whacked'

---

### Post by kooldino on 2008-08-21
I've noticed the same issue as well.

I'll give eject a shot as root.

---

### Post by mc4man on 2008-10-28
As an update
This will work as a post-disconnect command for Amarok in kubuntu (8.04) to disconnect and eject properly.
```

echo <password> | sudo eject %d
```

---

### Post by timcredible on 2008-10-28
> **kooldino said:**
> Ok great, seems like everything worked out.  The only iffy thing is when I "safely remove" my iPod, it still says "Connected" on the iPod's display.

that's normal, nothing to worry about, happens on every usb-connected device, from ipods to sansa mp3 players to flash drives (light doesn't go out).  just make sure you do the safely remove, or files won't get written to the ipod.

---

