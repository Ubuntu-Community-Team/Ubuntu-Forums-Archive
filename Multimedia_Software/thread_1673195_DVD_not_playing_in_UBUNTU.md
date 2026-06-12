---
title: "DVD not playing in UBUNTU"
date: 2011-01-22
forum: Multimedia Software
---

### Post by pankajsisodiya on 2011-01-22
Hi All,

I had installed UBUNTU 10.10 on my Thinkpad. I had also installed libdvdread4 using below 2 commands. But DVD is still not playing
sudo apt-get install libdvdread4

sudo /usr/share/doc/libdvdread4/install-css.sh

Playing of DVD is a basic thing which UBUNTU must provide. Please help

---

### Post by wilee-nilee on 2011-01-22
Install the restricted extras, libdvdcss2, and load the medibuntu, w32codecs.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Load the medibuntu run sudo apt-get update, then install, all these from synaptic it is probably easiest.

---

### Post by pankajsisodiya on 2011-01-22
No, its not working still

The steps i followed are,

1.  sudo apt-get update

2.  sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list  http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list  && sudo apt-get --quiet update && sudo apt-get --yes  --quiet --allow-unauthenticated install medibuntu-keyring &&  sudo apt-get --quiet update

3.  sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu

4.  sudo apt-get install ubuntu-restricted-extras

5.  sudo apt-get install libdvdread4

6.  sudo apt-get install w32codecs

7. Then Restarted the Computer

I am unable to run a DVD/CD on UBUNTU 10.10. Its really painful in UBUNTU to run a DVD or CD. Can anyone here help me in running DVD/CD on UBUNTU. Please tell me the steps. Even i tried lots of other commands i googled. But no luck still

---

### Post by Yellow Pasque on 2011-01-22
Those are the steps. If it's still not working, start your movie player program from the terminal to get more specific error messages.

---

### Post by Tigerlinux on 2011-01-22
install Totem.

---

### Post by pankajsisodiya on 2011-01-22
Still same problem, See what message i got after running VLC player from command prompt,

pankaj@pankaj-ThinkPad-R61i:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8789914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb748f0d4, 0xb748f048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1295872823)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2778): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
`menu_proxy_module_load': vlc: undefined symbol: menu_proxy_module_load

(<unknown>:2778): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': vlc: undefined symbol: menu_proxy_module_load

(<unknown>:2778): Gtk-WARNING **: Failed to load type module: (null)

Warning: call to signal(13, 0x1)
`menu_proxy_module_load': vlc: undefined symbol: menu_proxy_module_load

(<unknown>:2778): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': vlc: undefined symbol: menu_proxy_module_load

(<unknown>:2778): Gtk-WARNING **: Failed to load type module: (null)

Blocked: call to setlocale(6, "")
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
[0x8a2d69c] dvdread demux error: DVDRead cannot open source: /dev/dvd
[0xb6a00624] main input error: open of `dvdsimple:///dev/dvd' failed: (null)

Also i installed Totem using command,
sudo apt-get install totem-gstreamer


But how to run totem. I didn't see totem in Application >> Sound & Video Menu

Really it seems like Running DVD/CD in a UBUNTU system is a Rocket Science. Please help me in this Rocket Science

---

### Post by mc4man on 2011-01-22
with the dvd in the drive what does this show for the *-cdrom  section
```
sudo lshw -C disk
```

---

### Post by pankajsisodiya on 2011-01-22
*-disk                  
       description: ATA Disk
       product: HITACHI HTS54321
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: FBBZ
       serial: 090207FB2B32LGD15PPB
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=a651a651
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GSA-T20N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: WX05
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-cdrom
       description: SCSI CD-ROM
       product: Mass Storage
       vendor: HUAWEI
       physical id: 0.0.0
       bus info: scsi@17:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 2.31
       serial: 3
       capabilities: removable audio
       configuration: status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          capabilities: partitioned partitioned:mac
  *-disk
       description: SCSI Disk
       product: SD Storage
       vendor: HUAWEI
       physical id: 0.0.1
       bus info: scsi@17:0.0.1
       logical name: /dev/sdb
       version: 2.31
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk
       description: SCSI Disk
       product: FreeAgent
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sdc
       version: 102F
       serial: 2GEYP2KZ
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=65839819

---

### Post by mc4man on 2011-01-22
you can take a look thru this thread starting at linked post - same drive, same problem as simormate. Maybe something in there will help

[http://ubuntuforums.org/showthread.php?p=10343732#post10343732](http://ubuntuforums.org/showthread.php?p=10343732#post10343732)

Off the bat try this from terminal
```
vlc dvdsimple:///dev/sr0
```

---

### Post by leclerc65 on 2011-01-22
Did you do

 sudo apt-get install  libdvdcss2

---

### Post by pankajsisodiya on 2011-01-22
Yes. I did sudo apt-get install  libdvdcss2 also

But DVD/CD still not running

Is there someone Superman from ubuntu forum who will help me in running DVD/CD on my Thinkpad

---

### Post by SeijiSensei on 2011-01-22
Where did you get the copy of VLC that you're using?  The errors you report suggest the binary you're using was compiled against libraries you don't have on your machine.  If you're using the copy of VLC in the Ubuntu repositories, this shouldn't happen.  If you're using a version from somewhere else, you're on your own.

Personally, I'd try "sudo apt-get install smplayer" and use it to watch DVDs and other video files.  I needed only to do as you did, installing ubuntu-restricted-extras, libdvdread4, and running the script to get libdvdcss2.

---

### Post by Yellow Pasque on 2011-01-22
I don't see anything out of the ordinary in the vlc output and I doubt the OP has a non-standard version (lots of apps throw gtk-warnings). If the system can't read DVD's properly, then it doesn't matter what player you use.

---

### Post by mc4man on 2011-01-22
pankajsisodiya - 
I don't know if you read thru the thread linked or not, if you did then 2 things to note - 
the filesystem on the dvd is not being mounted, that by itself is not a showstopper, dvd video disks do not need to be mounted to be played.

the other, possibly more relevant, is that your drive has a history of inconsistent and poor behavior with commercial dvd video disks
(bluntly put it's not a very good drive

---

### Post by Tigerlinux on 2011-01-22
> **pankajsisodiya said:**
> Yes. I did sudo apt-get install libdvdcss2 also
 
But DVD/CD still not running
 
Is there someone Superman from ubuntu forum who will help me in running DVD/CD on my Thinkpad
 
you are using ubuntu which version?

---

### Post by pankajsisodiya on 2011-01-23
Hi,  I have UBUNTU 10.10. I Tried almost everything but unable to solve Rocket Science of playing DVD/VD UBUNTU. Please help

---

### Post by Yellow Pasque on 2011-01-23
> **pankajsisodiya said:**
> Hi,  I have UBUNTU 10.10. I Tried almost everything but unable to solve Rocket Science of playing DVD/VD UBUNTU. Please help
We can't help you unless you provide more information on your DVD drive and/or try another one. It's not "Rocket Science" and we're not Supermen, so quit being so grandiose about a bum DVD drive..

---

### Post by pankajsisodiya on 2011-01-23
Hi,

Yes Its not a Rocket Science, but UBUNTU should provide playing of DVD/CD by default like other OS provide. I know because of some copyrights issue they don't provide same, but don't you think almost eveyone plays DVD/CD.

Please find my DVD Drive info below,

*-cdrom
       description: DVD-RAM writer
       product: DVDRAM GSA-T20N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: WX05
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

---

### Post by BicyclerBoy on 2011-01-24
A windows & OS-X licence includes royalty payments to MPEG-LA for DVD playback.
There are also many other non-free items in windoze (&OS-X).
So Ubuntu will not provide DVD playback.

Ownership of a DVD does not guarantee playback on all or any equipment, least of all a PC!

So Ubuntu users should not complain about DVD playback..at least you do not have to pay for AnyDVD or DVDDecrypter etc..

The Ubuntu website has an excellent step-by-step instructions for DVD playback & other non-free restricted items...

---

