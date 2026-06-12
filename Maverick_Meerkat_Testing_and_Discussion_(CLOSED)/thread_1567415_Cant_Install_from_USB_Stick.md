---
title: "Cant Install from USB Stick"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Redcode on 2010-09-03
i made the mistake yesterday of removing 10.04..and i thought to give the new beta a try today..so i used the usb-creator inside the iso to put it on usb...when i boot from it give me the first line
"syslinux whatever the rest of this line is"
and it stop dead there nothing happens and it hangs like this..
i tried liveusb-creator with the same result as the above...
unetbootin give me a different error but i cant remember what it was..
i dont have a blank cd around me now and i was wishing to install it today thats why i need to do it from the usb...anyone knows what could be wrong

---

### Post by bennachie on 2010-09-03
Repeat the exercise, but disable persistence when running usb-startup-disk-creator. This is a known bug in the most recent version of the package, and should be fixed in the next round of updates.

---

### Post by VMC on 2010-09-03
> **Redcode said:**
> i made the mistake yesterday of removing 10.04..and i thought to give the new beta a try today..so i used the usb-creator inside the iso to put it on usb...when i boot from it give me the first line
"syslinux whatever the rest of this line is"
and it stop dead there nothing happens and it hangs like this..
i tried liveusb-creator with the same result as the above...
unetbootin give me a different error but i cant remember what it was..
i dont have a blank cd around me now and i was wishing to install it today thats why i need to do it from the usb...anyone knows what could be wrong

From the syslinux prompt type *help*

---

### Post by Redcode on 2010-09-03
> **bennachie said:**
> Repeat the exercise, but disable persistence when running usb-startup-disk-creator. This is a known bug in the most recent version of the package, and should be fixed in the next round of updates.

where's that "persistence" option to disable
see attachment

---

### Post by cariboo on 2010-09-03
There's your problem, you're trying to set it up in Windows. :) I setup the netbook edition this morning with a 4Gb thumb drive, that I created on my desktop system running Maverick.

There was a problem with people creating the image from Lucid, because there is a new version of syslinux. What I suggest you try is once you have transfered the image, go to the syslinux director on the thumb drive and modify the syslinux.cfg file. This is what the file looks like:

```
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
**ui** gfxboot bootlogo
```

all you have to do is remove the **ui** from the start of the last line. save the file, then reboot.

---

### Post by naxir on 2010-09-03
> **Redcode said:**
> where's that "persistence" option to disable
see attachment

discarded on shutdown should disable persistence.  I'm having the same issue myself, trying this out now.

edit: I noticed that you also either burned the iso or mounted it.  I had to mount the iso because when clicking other and selecting the iso, the list didn't populate with the selected image.

edit 2: It didn't work, still looking at SYSLINUX 3.82, etc.

---

### Post by aszlej on 2010-09-03
I'm having the same problem. Stuck at Syslinux 3.83, no prompt to enter anything, just appears frozen.

I tried removing the ui option from syslinux.cfg like some forum posts suggested, but that had no effect.

---

### Post by aszlej on 2010-09-03
> **cariboo907 said:**
> all you have to do is remove the **ui** from the start of the last line. save the file, then reboot.

Removing ui in my case produced a different error message:

"Unknown keyword in configuration file: gfxboot.

---

### Post by inso_741 on 2010-09-03
same problem...removing ui dint work...persistence disabled...any ideas?

---

### Post by cariboo on 2010-09-04
Maybe you could tells us what you mean by can't install, where does it stop? have you tries pressing the any key to get to the menu, and selecting the options available when you press F6?

---

### Post by inso_741 on 2010-09-04
> **cariboo907 said:**
> Maybe you could tells us what you mean by can't install, where does it stop? have you tries pressing the any key to get to the menu, and selecting the options available when you press F6?

the flash drive boots and displays Syslinux 3.8 (plus some info bout syslinux)
with a blinking cursor on the next line thats it...it goes on forever

---

### Post by Redcode on 2010-09-04
> **inso_741 said:**
> the flash drive boots and displays Syslinux 3.8 (plus some info bout syslinux)
with a blinking cursor on the next line thats it...it goes on forever

yop thats what i mentioned in the first post.
as for removing this line "ui gfxboot bootlogo"
it didnt make a difference...
i gave up i will buy blank cd tomorrow..or install 10.04 again..
its funny how you have to burn beta to try it while the final version you could put it on usb....i thought it should be the other way around since you wont be keeping the beta anyway ;)

---

### Post by inso_741 on 2010-09-04
the syslinux thing happens when I make the usb in windows
when I make it in Lucid it just says boot error!!

---

### Post by Redcode on 2010-09-04
going to try Universal USB Installer
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Edit:
Didnt work either same as before

---

### Post by VMC on 2010-09-04
If you guys type the word *help* from that syslinux cursor it should default boot  Maverick.

---

### Post by naxir on 2010-09-04
> **VMC said:**
> If you guys type the word *help* from that syslinux cursor it should default boot  Maverick.

I'm not able to type anything.

---

### Post by inso_741 on 2010-09-04
> **naxir said:**
> i'm not able to type anything.

+1

---

### Post by Redcode on 2010-09-04
ok all windows tools available to create usb live cd sucks...you will end up with the same error me and some other guys above are getting...i've been able finally to use the one in ubuntu (through another computer) to put it on the usb ...now it stop at the ubuntu logo with progress bar and nothing happens...i think i saw someone else complain about this earlier so to the searchmobile

Note to myself..never remove a stable version and try beta again :D

---

### Post by inso_741 on 2010-09-04
> **Redcode said:**
> ok all windows tools available to create usb live cd sucks...you will end up with the same error me and some other guys above are getting...i've been able finally to use the one in ubuntu (through another computer) to put it on the usb ...now it stop at the ubuntu logo with progress bar and nothing happens...i think i saw someone else complain about this earlier so to the searchmobile

Note to myself..never remove a stable version and try beta again :D

I gave up on usb...burned a dvd rw....installing it now:p
hope they'll fix it before final release

---

### Post by ranch hand on 2010-09-04
> **Redcode said:**
> ok all windows tools available to create usb live cd sucks...you will end up with the same error me and some other guys above are getting...i've been able finally to use the one in ubuntu (through another computer) to put it on the usb ...now it stop at the ubuntu logo with progress bar and nothing happens...i think i saw someone else complain about this earlier so to the searchmobile

Note to myself..never remove a stable version and try beta again :D
Good note.  Great idea.

The best thing to do is to dual boot the testing version with a stable version.  That way you can always have a nice, dependable, comfortable place to chroot into your broken system from.

Takes a lot of the stress out if you KNOW you can boot something, do your normal stuff and still be able to update/upgrade the Testing OS.  For a week or so if you have to.  It does happen.

I have a system that lets me always have a working testing OS but it takes several installs and a large dedicated drive.  Even there I have an install of 9.10 just in case.

---

### Post by Borsook on 2010-09-04
I can only say that I have exactly the same problem, can't do anything about it too, as I'm using a netbook so no booting from CD. And so ends my wanting to do some testing on the beta...

---

### Post by Starks on 2010-09-04
Why is persistence even an option?

Persistence space is worthless and cripples LiveUSB drives.

It only takes a few uses of a LiveUSB drive with a persistence file to fully saturate and generate "0 bytes remaining" messages.
 
When this happens, you can no longer use the drive to install Ubuntu  until casper-rw is resized or deleted or the USB device is reformatted.

I think persistence shouldn't even be an option and that storing files temporarily in RAM is a better solution.


[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/626585](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/626585)

---

### Post by VMC on 2010-09-04
> **Starks said:**
> Why is persistence even an option?

Persistence space is worthless and cripples LiveUSB drives.

...I've wondered that myself. I only use LiveUSB because it boots faster than LiveCD and works better. I don't know the value in using persistence.

---

### Post by naxir on 2010-09-04
I got mine to work, however I had to install 10.04 to my netbook first, then format the drive for 10.10 netbook edition.  then you have to remove the 'ui' keyword in syslinux.cfg on the drive.

edit: note that if you have two thumb drives, you could live boot 10.04 with an image of 10.10 on that usb drive and then use the startup disk creator within the live boot to make a bootable 10.10.  I didn't think the wife would care for me wiping her's out though.

---

### Post by Redcode on 2010-09-04
> **naxir said:**
> I got mine to work, however I had to install 10.04 to my netbook first, then format the drive for 10.10 netbook edition.  then you have to remove the 'ui' keyword in syslinux.cfg on the drive.

edit: note that if you have two thumb drives, you could live boot 10.04 with an image of 10.10 on that usb drive and then use the startup disk creator within the live boot to make a bootable 10.10.  I didn't think the wife would care for me wiping her's out though.

thats what i did yesterday (using my gf thumb drive to boot 10.04 then mine to create 10.10)...but i faced other problems after that..so i'm happily back to 10.04.1 this morning :D..one more month till final stable version of Maverick is out so its not a big a deal i will wait..

---

### Post by naxir on 2010-09-04
> **Redcode said:**
> thats what i did yesterday (using my gf thumb drive to boot 10.04 then mine to create 10.10)...but i faced other problems after that..so i'm happily back to 10.04.1 this morning :D..one more month till final stable version of Maverick is out so its not a big a deal i will wait..

laggy interface with unity? if so, me too.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/604777](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/604777)

---

### Post by Borsook on 2010-09-04
> **Starks said:**
> Why is persistence even an option?

Persistence space is worthless and cripples LiveUSB drives.

It only takes a few uses of a LiveUSB drive with a persistence file to fully saturate and generate "0 bytes remaining" messages.
 
When this happens, you can no longer use the drive to install Ubuntu  until casper-rw is resized or deleted or the USB device is reformatted.

I think persistence shouldn't even be an option and that storing files temporarily in RAM is a better solution.


[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/626585](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/626585)

1st the problem mention exist without persistence too

2nd Are you joking??? Persistence is the best possible feature, without it usb install is useless. Example - 10.04 does not work with my wireless, but it can be made to work by installing a driver. Thanks to persistence I don't have to do that upon every reboot. I do not have to readd diagnostic programmes over and over again, etc. etc

---

### Post by ktp on 2010-09-04
persistence does have it's advantages when it comes to drivers.

---

### Post by The Cog on 2010-09-04
> **Borsook said:**
> I can only say that I have exactly the same problem, can't do anything about it too, as I'm using a netbook so no booting from CD. And so ends my wanting to do some testing on the beta...

Same problem here.
I installed 10.10 beta on my desktop and used that to create a 10.10 boot USB stick. Same problem - one syslinux line and nothing else. Removing ui from the config makes no difference.

---

### Post by sylvester_0 on 2010-09-04
Isn't it possible to just "dd" the ISO onto a USB device? I know this isn't possible with every ISO but I believe Ubuntu spins theirs this way.

```
sudo dd if=~/Downloads/ubuntu.iso of=/dev/sdb
```

---

### Post by Hogmeister on 2010-09-04
i had a problem w/ this same thing, tried making a 10.04 usb stick in 10.10 and when i used it to boot w/ i got a syslinux screen with something along the lines of vesamenu.c32 is not a proper 32 something or other... did some scouring (took about 30 minutes of hardcore searching (i was sweating....... ) ) and came across a post buried inside of another one that said to comment out the vesamenu.c32 line of syslinux.cfg on the usb stick.

give it a whirl, it worked great for me. it threw an error upon bootup but it continued and the install is flawless so i hope it helps.. this is what my syslinux.cfg looks like on my usb stick.


include menu.cfg
#default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo

---

### Post by ranch hand on 2010-09-04
> **sylvester_0 said:**
> Isn't it possible to just "dd" the ISO onto a USB device? I know this isn't possible with every ISO but I believe Ubuntu spins theirs this way.

```
sudo dd if=~/Downloads/ubuntu.iso of=/dev/sdb
```
I think you may be interested in reading this, very superficial and short, link before trying that.
[http://www.search.com/reference/Dd_%28Unix%29](http://www.search.com/reference/Dd_%28Unix%29)

---

### Post by ranch hand on 2010-09-04
There is of coarse;
```

man dd

```

---

### Post by ronacc on 2010-09-05
for what its worth I cant even get a usb stick to boot ( the box will boot from one , I've installed from them before) , with the beta (64bit) the box recognises the stick as the boot dev and doesn't go on to the second boot dev but the just sits there contemplating its navel doesn't seem frozen or hung just lost in never never land . aborted and installed from dvd burnt from the same .iso with no problem .

---

### Post by VMC on 2010-09-05
Has anyone tried booting using one of the mini distros and using their syslinux command.

I know Parted Magic has the latest version 4 installed.

I just install grub2 on my usb stick, using this command:

```
grub-install --root-directory=/media/TinyCore /dev/sdb

```(I have TinyCore on that usb stick)

Then I copied my grub.cfg from my current hard drive to the usb stick. Now when  I plug in the usb stick I can boot TinyCore or any of my Ubuntu installs, including Maverick. Its a good backup for booting in case something goes wrong using ubiquity from Maverick.

Here's another thought. I did this during the Lucid cycle. I used the loop-back method of booting the ISO:

```
menuentry "Ubuntu Live" {
loopback loop (hd1,8)/lucid-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lucid-desktop-i386.iso --
initrd (loop)/casper/initrd.lz
}
```

At the time the ISO was sitting on partition 7 or the second hard drive.

---

### Post by ronacc on 2010-09-05
@ VMC  that grub on a stick trick looks like a good idea , I think Ill give it a whirl with Puppy , my favorite mini .

---

### Post by ranch hand on 2010-09-05
If anyone wants a little more info on booting the ISO here is a link.

WARNING
This is one of drs305s posts;
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

I even finally can do this.

---

### Post by VMC on 2010-09-05
> **ronacc said:**
> @ VMC  that grub on a stick trick looks like a good idea , I think Ill give it a whirl with Puppy , my favorite mini .

Just remember if you copy the grub.cfg to the usb stick you need to edit the hd info. For my case, the stick was hd0,1 and the rest of my internal hard drive became hd1,X

---

### Post by steve.horsley on 2010-09-05
You can't just dd the iso image to the USB stick as far as I know. USB sticks look more like hard drives than cdrom drives.

I just managed to make a working USB installer stick using Maverick beta on a desktop. I haven't changed anything I know of since last time I tried and failed, other than reformatting the stick to FAT32 rather than the FAT16 it was originally formatted to. I formatted it with the command:
sudo mkfs.vfat -F 32 /dev/sdf1
then used the boot disk maker, choosing no persistence.

For reference, here is the contents of the working syslinux.cfg:

# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo


I attach a screenshot of how I created it.

---

### Post by VMC on 2010-09-05
> **steve.horsley said:**
> You can't just dd the iso image to the USB stick as far as I know. USB sticks look more like hard drives than cdrom drives.

I just managed to make a working USB installer stick using Maverick beta on a desktop. I haven't changed anything I know of since last time I tried and failed, other than reformatting the stick to FAT32 rather than the FAT16 it was originally formatted to. I formatted it with the command:
sudo mkfs.vfat -F 32 /dev/sdf1
....
I've had problems in the past with the "proper" formatting of USB sticks. Now I use the Disk Utility to format my USB sticks to Fat, and afterwards they are always Fat32. As I recall having problems using Fat16.

---

### Post by ktp on 2010-09-05
> **VMC said:**
> Has anyone tried booting using one of the mini distros and using their syslinux command.

I know Parted Magic has the latest version 4 installed.

I just install grub2 on my usb stick, using this command:

```
grub-install --root-directory=/media/TinyCore /dev/sdb

```(I have TinyCore on that usb stick)

Then I copied my grub.cfg from my current hard drive to the usb stick. Now when  I plug in the usb stick I can boot TinyCore or any of my Ubuntu installs, including Maverick. Its a good backup for booting in case something goes wrong using ubiquity from Maverick.

Here's another thought. I did this during the Lucid cycle. I used the loop-back method of booting the ISO:

```
menuentry "Ubuntu Live" {
loopback loop (hd1,8)/lucid-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lucid-desktop-i386.iso --
initrd (loop)/casper/initrd.lz
}
```

At the time the ISO was sitting on partition 7 or the second hard drive.

This is nice...I was doing something like this on my usb harddrive to create portable "rescue disk". I would have iso on the usb so i can just upgrade to the latest with minimal work.

---

### Post by aaronwe on 2010-09-05
So bottom line here: USB install of Maverick Netbook is totally broken in the beta?

Sure makes it hard to test what you can't install, especially since almost all netbooks don't have optical drives.

---

### Post by cariboo on 2010-09-05
> **aaronwe said:**
> So bottom line here: USB install of Maverick Netbook is totally broken in the beta?

Sure makes it hard to test what you can't install, especially since almost all netbooks don't have optical drives.

No, for most of us it works the way it should. I've had no problems using the Startup Disk Creator utility and being able to install to my netbook. Press any key when you see the keyboard and man, and you get the regular old menu and options.

---

### Post by ranch hand on 2010-09-05
> **cariboo907 said:**
> No, for most of us it works the way it should. I've had no problems using the Startup Disk Creator utility and being able to install to my netbook. Press any key when you see the keyboard and man, and you get the regular old menu and options.
Keyboard and Man?  You mean those cryptic blobs at the bottom of that first purple screen?

I knew you hit a key to get to a usable menu but had not known what those blobs were supposed to be.

---

### Post by cariboo on 2010-09-05
Maybe this will help. :) I used gimp to double the size.

---

### Post by ranch hand on 2010-09-05
Well I can see the boys room sign.  If that other thing is a keyboard I must need a new one.

Nice to know what someone thinks it is anyway.

So, what is the message there supposed to be once you decipher the hieroglyphics?  Keyboard Man?

I must really be slow.  Now that I know what they are supposed to be I can't figure out what they are for.

---

### Post by VMC on 2010-09-05
> **cariboo907 said:**
> Maybe this will help. :) I used gimp to double the size.
thanks. I'm going to put that to some good use. :)

---

### Post by RJ12 on 2010-09-05
> **VMC said:**
> thanks. I'm going to put that to some good use. :)

LOL!

The way I got My Maverick USB stick to work is by using the startup creator that came with Karmic (Lucid doesn't really like my computer) and setting no persistence. After that I booted up my flash drive, it got to a syslinux prompt and said boot: and I typed help (followed by enter) and then it gave me some options. One of them was press enter to boot. I pressed enter and it proceeded to boot up into maverick. It doesn't have the screen with the "Try Ubuntu" or "Install Ubuntu" it just defaulted to the live environment.

Hope it helps

---

### Post by cariboo on 2010-09-05
It's got to be some Euro-Design thing, they tend to go for symbols, because there isn't a common language there, like there is here. :)

---

### Post by ktp on 2010-09-05
> **VMC said:**
> thanks. I'm going to put that to some good use. :)

:lolflag:

---

### Post by FiremanEd on 2010-09-05
I was having the same issue installing via USB stick onto my Asus Eee with the Live CD release.  I switched to the daily build and it worked without a hitch.  I think it's was the 4th of Sept.  Booted onto my netbook, no errors.

---

### Post by The Cog on 2010-09-06
> **cariboo907 said:**
> Maybe this will help. :) I used gimp to double the size.

Hmm. The meaning is not clear to me. Something about cine films and little boys, perhaps?

---

### Post by ronacc on 2010-09-06
> **cariboo907 said:**
> It's got to be some Euro-Design thing, they tend to go for symbols, because there isn't a common language there, like there is here. :)

simple clear and easy to understand , yes thats the goal . :confused:

---

### Post by ranch hand on 2010-09-06
> **ronacc said:**
> simple clear and easy to understand , yes thats the goal . :confused:
They are taking the advise in you sig.

I still think it means Keyboard Man but The Cog may have it right too.  I think a lot of "those" kind of flicks are illegal here.

---

### Post by ronacc on 2010-09-07
Has anyone bugged the failure to boot from usb ? new threads keep poping up about it .

---

### Post by dondada on 2010-09-15
I was able to successfully boot Maverick from USB on my EeePc netbook. I used [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") in Windows 7 but in a roundabout way. I selected Lucid 10.04 Netbook Remix from the dropdown menu. This reveals the 'Persistence' option which needs to be turned off. Then, I manually pointed the location of the ISO to the Maverick 10.10 ISO I had downloaded earlier and created my USB.

I rebooted and it worked!

---

### Post by dondada on 2010-09-16
Disregard my post above. This just installed Lucid again.

---

### Post by KristinaK on 2010-09-23
so, how to solve this problem with 10.10?

---

