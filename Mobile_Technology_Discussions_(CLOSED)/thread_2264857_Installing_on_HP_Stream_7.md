---
title: "Installing on HP Stream 7"
date: 2015-02-10
forum: Mobile Technology Discussions (CLOSED)
---

### Post by dkz666 on 2015-02-10
Hello All,

I have been working on installing Ubuntu on the hp stream 7 on and off since about Xmas. Windows and  associated partitions are long gone and the  UEFI firmware works just fine.

I  have been able to successfully boot a number of different distributions(all ubuntu flavored; Mate, Kubuntu, Lubuntu, Ubuntu,  UbuntuGNOME, ...),  using a combination of methods listed above, and elsewhere (though I  can't find it now), via bootableUSB. (Please note, for nothing discussed below was there an SD card in the tablet) 

Before I had a chance to sit down and take the project back up, (and notice [this]("http://ubuntuforums.org/showthread.php?t=2261294") awesome post!), I had followed a guide that only required moving bootia32.efi to  an /EFI/BOOT folder with the native grub.cfg file and making the  modification in 4 (for a different device, see [here]("http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/comment-page-4/")).

_Current Method:_[INDENT]
0) Get USB install disk.
1) Copy fedlet /EFI to install disk's /.
2) Delete /EFI/BOOT/grub.cfg, move[COLOR=#000000][FONT=verdana]/boot/grub/loopback.cfg[/FONT][/COLOR] to its place.
3) append *efi to linux initrd as described above
4) Replace instances of ```
quiet splash
``` with ```
video=VGA-1:800x1280e reboot=pci,force
``` in grub boot options.

If it doesn't work or display, I just reboot and delete the video and reboot settings from (4) before booting.
[/INDENT]

_Problem:_

On _every_ ubuntu distibution I tried, the installation process takes inordinately long. By installation process, I mean ubiquity getting ready to install, **not the actual install** and by long I mean like, **battery-life long**. 

I think I have some indication that it may have to do with the constant error message I see during boot and operation about a blk  partition and rw status (including ```
[COLOR=#404040][FONT=Roboto]mmcblk0rpmb: timed out sending r/w cmd command[/FONT][/COLOR]
``` ). I will get an exact log when I reboot it. See Below.


_Some History :_

I have managed to have it actually install twice (with no particular pattern). Each time after telling grub where to look, booting, and updating / grub-updating, the tablet wouldn't boot. So I was back to the USBdisk.

When I am running ubiquity, I can't see any indication in top, nor info in dmesg that would give me any impression that the install is getting set-up. I have tried with and without thrid-party pkgs and updates (via an ethernet thether that is recognized), as I noticed a bug relating to this and 14.x variants.

This  was going nowhere very slowly, and like many a foolish delatante  linuxer, i tried to dd an image to mmcblk0 from the install USB. I know that was stupid - It was even studpider  was when I tried it again, a couple attempts later. Granted I had rebooted and formatted the  partition, but this didn't get me anywhere.

_Now:_

Now, I can still boot everything, from a USB. There  is a 30 gig main device listed at /dev/mmcblk0 and two /mmcblk0boot[x]  partitions, in addition to a few mmcblk0zrams, which I can only assume  to be old swap spaces? There is also the mmcblk0prmb which seems to be causing issues. 

I know for a fact I haven't done near enough to fry the flash memory from writes. That said, I completely grant I may have fried the SD card from dd or otherwise. Hopefully  not. 

If your impression is that I did **not**, do you have any recommendations on how to clean upthe internalSD for install? Once installed, it seems to just be a matter of updating the grub and its paths, _though if there is something that needs to be done to a new install (say, like was required for the USB) I would greatly appreciate suggestions_.

If you think I **did fry** the SD, would anyone know if it is  possible to boot regularly from an externalSD? I figure there is still  30 gigs of just fine space in there one way or another, and a large SDs  are easy to come by. I apologize for asking something I can probably  check in the UEFI settings, the tablet is just quite out of juice after my last 24hr attack.

Any suggestions or recommendations would be  greatly appreciated. I am obtaining a copy of windows now, to see if  daddy Gates can help. Barring that working, I am going to try and go  down the externalSD route, time for homework kept in mind :P .

Many thanks
[Please Note: I have exerience *and* no formal training with ubuntu/gnu-linux. I also don't post a lot, so please forgive any over obvious points or things I missed.]

UPDATE:

Uefi boot order lists a "USB diskette on Key/USB Hard Disk" and a "USB CD/DVD ROM Drive" - any indications which if either would be SD?
 Will try myself later.

Error  is ```
mmcblk0rpmb: error -110 
``` . This seems to be a larger problem with the kernel. Suppose I will just look into compiling my own, with one of the many patches out there? Any suggestions on comiling?

---

### Post by dkz666 on 2015-02-12
hello all,

I got it. Will post detailed instructions after a nap.

---

### Post by dkz666 on 2015-02-12
Medium Risk, Large Headache

okay, so, going to need to edit this thing to heck. I will probably turn it into a guide with the above post. But for the immediately curious, here is how I got it working:

Please note, these steps nuke windows.

1) Make sure the thing is fully charged....Once you get rid of windows, it will be pretty hard to tell how charged it is, so maybe doing this before hand is a wise decision.

2) Make Bootable USB - as described above, in whatever combination works. I can definitively say the minimum I have seen work was placing a file named bootia32.efi into a /EFU/BOOT/* and doing the grub modification I indicated at (4) above. The method from fedlet seems solid though, and is probably essential to making it boot on its own after, so I would suggest continue preparing in that way. These methods, or a combination of them, has worked to boot every ubuntu flavor I tried. I ended up using a 64bit iso (ubuntuGNOME), same as the tablet is pre-loaded with, the trick is getting the 32bit GRUB.

2.5) I also ensured that the drive was a GPT general partition and used a fat local. From playing around with the grub it seems that the tablet is fine loading about any, though the native agreement can't hurt. Also found out that it can't recognize the externalSD on boot (though now that it is running ubuntu, I bet someone can get that working).

3) You need to get Secure boot off. I turned off signature verification too. You will also need to prioritize everything dealing with a USB, and deprioritize the OS/"hard drive"(or internalSD here) with F5/F6. These are in the BIOS/UEFI settings. This will not work until that is done.

3.5) This highlights a good point. 

While the tablet is cheap, there are additional expenses to getting it running Ubuntu. I had to purchase a USB hub and a USB-ethernet dogle. They make these combined, which is probably a lot better than my jimmy-rigged set up (which I will include a picture of if people are interested). In addition, you will need an external keyboard/mouse. I seriously suggest checking to make sure all the hardware works under windows first, to avoid unnecessary troubleshooting. 

Please note, as well, that I was not able to use the logitech wireless keyboard I normally do for accessing the boot options on start-up - i needed a hard-wired keyboard. This isn't the case once the UEFI loads, and the wireless worked fine there. My point - if your favorite modern keyboard doesn't work at any point, try analog.

4) Go through the easy steps provided by windows to boot from a UEFI enabled flash drive. If you can't figure out my sarcasm, I apologize, but if you can't figure out how to do this, I can't help...

5) Boot your USB! - Make sure its charged!

6) If you're lucky, and the efi gods shine bright upon you, you will see a couple million screen-fulls of crap, then some that is broadcasting messages about.... Kernel modules actually loading! If the kernel doesn't panic (which, if it does, make a new usb and mess with efi folders/grub.cfg/flavor/OS) you will be brought to the grub options which you presumably saw in (2). Remember, only entries you modify will work. I suggest putting more info in than less (i.e. just doing the video=VGA.... reboot=... ) because its easier to delete in the grub than look from one computer to this little _ while trying to type unfamiliar stuff.

6.5) Trouble shoot until you get it booted.

7) I suggest to wipe partitions before trying to install and, as usual, to wipe _everything_. This will take forever. If you are really masochistic, you can run ```
 sudo watch 'dmesg | tail -50 
``` . More on why I think this takes forever below.

If it dies, charge it back up to full, try again. After a patient try or two, you will have a clean machine that complains about not having an OS when you boot it - BUT THAT WILL BOOT IF THE USB OPTIONS REMAIN PRIORITIZED AND THE EFI FILE STRUCTURE CORRECT ON THE USB. This complaint itself indicates that the EFI firmware is still operating. You won't wipe the firmware by wiping the partitions, or at least I didn't. I think may have access to that device now, but I won't be tempting fate by messing with it. I don't want to give the impression this is low-risk, but I don't want people thinking it is impossible.

6) There seems to be a hang on some releases when trying to install 3rd  party soft and/or download updates while installing. In the interest of  avoiding unnecessary complications, I suggest just leaving them out for  now. You will have time later.

8) After wipe, do install. I let the installer wipe everything. Be patient.

9) If install fails or the tablet dies, keep going? Retry.

10) Persistance and Automatic Boot

Someone who is more knowledgeable can probably give you a better way to do this next part. Basically, when I rebooted (with the flash drive removed), I got the same error message that I did before I installed. This caused me to reinstall more than I want to admit, but I figured out the issue.

The system is such right now that there is a EFI layer (a boot manager? or whatever the proprietary complex calls it), a bootloader, and a system layer. The problem is that the EFI can't communicate with the GRUB (the bootloader). It *can* on the flash drive though, due to the fedlet and grub modifications you did. As you can guess, you're going to need to do those again.

A) You can try holding F9 (i believe) on an analog keyboard while booting and there should be an ubuntu entry, but for me, this didn't work at first. I solved by using the USB grub to bootstrap myself onto the device. It was actually really easy:

At grub menu, hit " c " and enter GRUB shell. (see [here]("http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/") for better GRUB instructions)

```
grub> ls
``` - Find out where your "hard drive" (sd) card is in grubs langauge. It will be something like (hdX,gptX) . Mine was at (hd1,gpt2) with a USB in and the GRUB on that USB.
Then, (PLEASE NOTE the efi appx to the linux and initrd commands)
```
grub> set root=( YOUR INTERNAL SD-ID HERE )
grub> linuxefi /boot/vmlinuz-3.13.0-29-generic root=/dev/(YOUR INTERNAL SD) video=VGA-1:800x1280e reboot=pci,force
grub> initrdefi /boot/initrd.img-3.13.0-29-generic
grub> boot
```

My device ended up being mmcblk0p1 . the mmcblk indicates its an SD, the integer the index of the drive, and the pX the parition. Be careful if you have another SD in there, you may end up marking that one. I considered trying to use a bootable sd to get the install when I thought the USBhub was too slow, turned out not to need it.

11) If it works, cautiously remove that USB and feel the power!
Now to make sure it continues to boot. 

First, update grub. 
Next, update, upgrade, dist-upgrade 
Next, download synaptic
Next, download grub-efi-32 packages - signed if they appear. I grabbed the signed kernel packages/headers/common too.
Last, update grub. It should say something about putting in a UEFI entry.

12) If someone decides to restart here, please let me know if it works. I ended up basically doing the mod for the USB stick again, just to be safe. I copied the fedlet files into my /boot/efi/BOOT dir, which I made, and made a grub.cfg there that reflected the boot process given here, made from /boot/grub/loopback.cfg.

13) updated, cleaned up, dist-upgraded, added some of my favorite ppas, etc. Shutdown, pulled all the usb, and watched it fly!


State of Things:

The mmcblk0rpmb errors affect the live CD, and any partition tools i've seen. It causes a critical reduction in speed. 
For me, however, once the rootfs is fully loaded, i.e. when dealing with mmcblk0p2 and not mmcblk0. This partition doesn't seem to be called, and therfoer doesn't cause errors. That said, it appears that this is manufacture/radio partition that probably is a security issue and will eventually need to be wiped. On that front, I attempted to dd wipe it. If you don't know what that means, you probably shouldn't try it. But for those who feel comfortable using the tool, I think it may have actually reduced the errors I noticed during boot, at least. The tablet didn't have enough battery to let dd finish, but it hasn't affected usability.

The touch driver given [here]("http://ubuntuforums.org/showthread.php?t=2261294") works with considerable configuration necessary.
The wifi driver given at the same has not worked yet for me, however.

Charging/using the usb port is something that I am hesitant about. I have not had any issue switching between data and power connections, but I have my worries.

Needs battery set-up.
Needs sensors set-up.
Needs on-screen keyboard that is easily accessable. I am going to look into cusomizing GNOME hotcorners to do some of the more tablety stuff, and will share my progress as it goes.

Just tried turning it on to take a pic, and its hanging after boot :) - pretty sure it was caused by post install packages. fixing it, but in doing so i noticed that 1) there is a default ubuntu entry, and a duplicate which point to different grub.cfg files 2) that recovery options worked out of box, i.e. w/o grub.cfg mods.

for ref to start eth0 in recovery root shell :

```

sudo mount -o remount,rw /
sudo dhclient eth0
sudo ifconfig eth0 up
```

---

### Post by litemint on 2015-02-25
Hi, had you tried installing elementaryOs luna or freya on it?

---

