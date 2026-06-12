---
title: "Gxine does not recognize DVD rom drive"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by kenny1948 on 2008-03-13
I just installed Gxine, and all the codecs to play DVD's

When I opened Gxine for the first time I got this:see attached screenshot.

I presume it means I need to install drivers or something. However I am not computer literate enough to understand just what this means.

Likewise when I put a disk in the drive it automatically tries to open in Totem Player. Is there any way around this?
Can someone help? Please!:(

Thanks
Kenny1948

---

### Post by xc3RnbFO8P on 2008-03-14
In terminal:

> gedit /etc/hdparm.conf

See if there is /dev/dvd  dma ? and /dev/cdrom dma ?

---

### Post by kenny1948 on 2008-03-14
This is what happened when I entered that command, I really do not understand it

## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -s Turn on/off power on in standby mode
#poweron_standby = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode
# --security-freeze Freeze the drive's security status
# security_freeze
# --security-unlock Unlock the drive's security
# security_unlock = PWD
# --security-set-pass Set security password
# security_pass = password
# --security-disable Disable drive locking
# security_disable
# --user-master Select password to use
# user-master = u
# --security-mode Set the security mode
# security_mode = h

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

---

### Post by xc3RnbFO8P on 2008-03-14
There is nothing wrong there, it is just like mine and evrything is working.
Is it only in Xine you got problem with playing dvds?

---

### Post by Cresho on 2008-03-14
use kaffeine to play dvd's  its the best....really!

---

### Post by xc3RnbFO8P on 2008-03-14
In Synaptic Package Manager search **xine**.
See what you are missing there.

---

### Post by xc3RnbFO8P on 2008-03-14
> **Cresho said:**
> use kaffeine to play dvd's  its the best....really!
 I use VLC and Mplayer.

---

### Post by cor2y on 2008-03-14
Ok first off if you want something other than totem to play your dvds go to System->Preferences->Removable Drives And Media.
And then go to the Multimedia Tab and under Video Dvd Discs Replace the word totem with gxine, leave the %m in place.
And thats how to replace your default dvd player in ubuntu.
Once that is done Gxine should start playing your dvds once inserted IF you have enabled and installed all the extras like libdvdcss and libdvdnav etc needed for dvd playback.

---

### Post by kenny1948 on 2008-03-15
> **cor2y said:**
> Ok first off if you want something other than totem to play your dvds 

actually I simply wanted something that COULD play my DVD's. Totem won't play anything,and I have all the plugins installed. It's a USA thing, from what I have read on the forums. 

I don't know if anything will play NTSC, or convert other file types to NTSC under Linux it's a legality thing. I was able to play homeade DVD's with Feisty, but now with Gutsy nothing plays. Supposedly Gxine had the extra codecs needed. I have since uninstalled Gxine and only have Totem on my machine. 

It's not absolutely necessary for me to be able to play or burn DVD's, however it was something I enjoyed doing in my spare time. Downloading clips from You Tube and some other sites, and burning them so I could watch them on my DVD player.

Nero in Windows worked fine for that, however I got rid of windows and am now only using Gutsy.

Sorry to go on and on.  I'm not very adept at using "terminal commands" so, although there are some programs out there that work, you really need to understand typed commands, and I do not.:confused:

Thanks for all your help,
Kenny

---

### Post by kenny1948 on 2008-03-15
> **Cresho said:**
> use kaffeine to play dvd's  its the best....really!

Well I tried  Kaffeine, and this is what happened! I used the advice of another poster on how to change my default, so that worked. However I'm having the same type of problem with playing my DVD's

If anyone has suggestions. Greatfully appreciated!

I will check back on this thread tomorrow. Have to sign off now.

Kenny

---

### Post by Cresho on 2008-03-15
this is how you get those working.

in the 
system->administration->software sources you choose "source code" and also you change the "download from:" from usa server, to  "main server."

Now for the codecs.

open up the terminal and you copy and paste each line and enter.

```
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
```

and then you 

```
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O-¦ sudo apt-key add -
```

then finally you 

```
sudo apt-get update
```

after you entered those and updated your software source for your operating system, you install 2 important stuff to your pc which will allow y our thing to work.

```
sudo apt-get install w32codecs libdvdcss2
```

say 'Y" or "n" to questions if it asks you.  now you can reboot (not needed but I do it because i come from windows) and insert a dvd and open kaffeine and it will see the dvd...or do what you were doing and it will play the dvd.

---

### Post by cor2y on 2008-03-16
kenny1940 you didn't install the necessary files for encrypted dvd playback, see Cresho's advice to do this , then dvd playback should work.

---

### Post by kenny1948 on 2008-03-18
OK, I removed Kaffeine, and installed klv plaver, and it works fine!

Problem Solved!

oh yes, I also set klv as my default player. :)

However thanks for all your help. klv seems to be working fine with no problems. So I will just stay with it.

---

