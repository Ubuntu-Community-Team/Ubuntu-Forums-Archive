---
title: "no devices in DVDDecrypter"
date: 2009-01-25
forum: Multimedia Software
---

### Post by mikeuhlik on 2009-01-25
bubs posted this.

I installed DVD Decrypter under wine and when I run it it says no devices found.

How do I fix this?

using edgy 64bit

I followed 3 tutorials online on how to install dvd decrypter in wine but every time It can't find my dvd drive
i even downloaded some dll's that people say I needed and still nada

I was using k9copy but I messed with some setting and it crashed and I haven't been able to run it since. I even removed it and reinstalled it but it still won't run.

so How can I get dvddecrypter to work or how can I get k9copy to work again

bubs:(

---

### Post by mikeuhlik on 2009-01-25
This is what i did to solve this issue 

For those of you having some difficulty getting drives recognized, after following the original post's directions, you might want to try this.

1. Open DVD Decrypter.
2. Click Settings | I/O
3. Check "ASPI",and hit OK.

When I originally installed, it was set to "SPTI - Microsoft". After selecting ASPI in I/O, everything magically worked, albeit somewhat slowly.

Also, I made sure that devices in $HOME/.wine/dosdevices were set up correctly. I didn't use winetools, but I assume this does the job correctly.

To make sure that devices in $HOME/.wine/dosdevices were set up correctly

you need to do this

cd ~/.wine/dosdevices
rm d:
ln -s /media/cdrom d:

Later versions of wine, like the one shipped in Dapper Drake (0.9.9) ignore settings in ~/.wine/config
You have to use the "winecfg" program to set windows version to NT 4.0 (thanks to Phil B. July 2006)

gedit ~/.wine/config
[Version]
"Windows"="win98"
change to
"Windows"="nt40" 


Download dll.zip [http://www.mrbass.org/linux/ubuntu/dvdshrink/dll.zip]("http://www.mrbass.org/linux/ubuntu/dvdshrink/dll.zip")
1.1MB to your desktop (contains riched20, quartz and mfc42 dlls)
unzip Desktop/dll.zip -d ~/.wine/fake_windows/Windows/System/

[COLOR="Red"]Please remember to Backup all file you edit so you can restore your system if it dose not go as planned 
[/COLOR]
[COLOR="Red"]
If none of this worked you may need to try this 
P.S. The first section should do just fine only do this last section if none of the above worked out.[/COLOR]

This how-to is pretty long because it also walks you through changing your dvd drive's setup to work with Wine and installing and configuring wine itself. Even if you don't want DVD Decrypter but are having Wine configuration problems or want to install Internet Explorer and Windows Media Player, this how-to will help you get it working (delete your ~/.wine directory before starting if you want to follow the Wine config in this how-to because yours isn't working).


SECTION 1: Configure your DVD-RW or DVDROM drive.


First, we setup your DVD-RW drive (or DVDROM if you just want to decrypt DVDs and not burn them) so it will be recognized in Wine. If someone knows a downside to making it run in scsi emulation mode, please tell me so I can add a warning about it.

1. Run:

$ cat /etc/fstab

And find your dvd-rw drive's device in the output. Eg: hdd

An example might be: /dev/hdd /media/cdrom1 udf,iso9660 ro,user,noauto 0 0
where your DVD-RW/DVDROM is mounted on /media/cdrom1.

2. Edit the kernel boot paramaters (make a backup first):

$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

$ sudo gedit /boot/grub/menu.lst

Add 'hdx=ide-scsi' to the end of your kernel line, where 'x' is your dvd-rw drive's device. The correct line is probably the first kernel line (example below) that is not commented with a '#' in front.

Example kernel line including 'hdd=ide-scsi':

kernel /boot/vmlinuz-2.6.10-5-k7 root=/dev/hdb1 ro quiet splash hdd=ide-scsi

Do not just copy my example because it probably won't work for your computer. Just edit yours, which will be similar. The recovery mode grub boot option will let you go to the console and restore your menu.lst file if this change prevents your computer from booting.

3. Add the ide-scsi module to the module list that your kernel loads, otherwise your kernel will not know how to read from the drive anymore.

$ sudo gedit /etc/modules


Add the module 'ide-scsi' to the bottom of the list. Example completed /etc/modules file below:


ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod
ide-scsi


4. Reboot your computer so the ide-scsi settings take effect. After it reboots you should be able to mount CDs and DVDs. Check to make sure you can mount them so we know it's working.


SECTION 2: Install and configure Wine.


Now let's install and configure Wine. If you have Wine already running, skip to the next section where we install DVD Decrypter.

1. Open your apt-get sources file:


$ sudo gedit /etc/apt/sources.list

Add this line to the end of the file: deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

That will give you the repository for the latest version of Wine and related tools.

2. Install Wine and the configuration utility:

$ sudo apt-get update

$ sudo apt-get install winetools

Installing winetools will get you Wine and libwine. We will use winetools to configure Wine.

3. Configure Wine:

$ winetools

Go through the winetools GUI config. It will help you install various necessary bits to make Wine work better. You do not need to complete the IE 6 installation unless you want IE and Windows Media Player. You can also skip the Arial and other font installations because they're broken anyway (bad download location). Hopefully winetools is self-explanatory so I will not go into more details. When it's done, continue with this how-to. Even if winetools gives you some errors, just keep going with as much as possible.


SECTION 3: Installing DVD Decrypter


1. Go to the DVD Decrypter ([http://www.dvddecrypter.com/index.php?act=download](http://www.dvddecrypter.com/index.php?act=download)) web site and download the latest version. Continue below after cd-ing to your download directory.

2. Run the DVD Decrypter setup (filename will change if you have a newer version of DVD Decrypter):

wine SetupDVDDecrypter_3.5.4.0.exe

Go through the DVD Decrypter setup wizard. Accepting the defaults is fine.

3. Run DVD Decrypter:

$ wine ~/.wine/fake_windows/Program\ Files/DVD\ Decrypter/DVDDecrypter.exe


In the Source dropdown box within DVD Decrypter you should see your DVD-RW/DVDROM selected. If not, return to section 1 and make sure you have scsi emulation working correctly.

To make running DVD Decrypter easier, add it to your Gnome menu using the menu editor ([http://ubuntuforums.org/forumdisplay.php?f=67](http://ubuntuforums.org/forumdisplay.php?f=67)).

[COLOR="Red"]P.S. The first section should do just fine only do this last section if none of the above worked out.[/COLOR]

---

### Post by Himself2007 on 2009-11-06
mikeuhlik

I had the problem.
And your solution solved it.
Despite it's an old post...
The least I can say is...
[SIZE="5"][COLOR="Navy"]Thanks very much!!![/COLOR][/SIZE]

Luc

---

