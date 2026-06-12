---
title: "My Mpeg-2 DVD's having issues..like low framrate blurry"
date: 2006-02-12
forum: Multimedia &amp; Video
---

### Post by gordong11 on 2006-02-12
Hi I"m running 64bit Breezy on self made PC with a MSI mobo with ATI graphics onboard, but set to VESA with 128mb of shared total 512mb.

My video playback using gxine is very slow..like low memory. I was told enabling DMA will help, but the instructions at wiki do not work. I get "no such file"(sudo hdparm /dev/hdc). here is my infoon the terminal:

dan@ubuntu:~$ sudo hdparm

hdparm - get/set hard disk parameters - version v6.1

Usage:  hdparm  [options] [device] ..

Options:
 -a   get/set fs readahead
 -A   set drive read-lookahead flag (0/1)
 -b   get/set bus state (0 == off, 1 == on, 2 == tristate)
 -B   set Advanced Power Management setting (1-255)
 -c   get/set IDE 32-bit IO setting
 -C   check IDE power mode status
 -d   get/set using_dma flag
 --direct  use O_DIRECT to bypass page cache for timings
 -D   enable/disable drive defect management
 -E   set cd-rom drive speed
 -f   flush buffer cache for device on exit
 -g   display drive geometry
 -h   display terse usage information
 -i   display drive identification
 -I   detailed/current information directly from drive
 --Istdin  reads identify data from stdin as ASCII hex
 --Istdout writes identify data to stdout as ASCII hex
 -k   get/set keep_settings_over_reset flag (0/1)
 -K   set drive keep_features_over_reset flag (0/1)
 -L   set drive doorlock (0/1) (removable harddisks only)
 -M   get/set acoustic management (0-254, 128: quiet, 254: fast) (EXPERIMENTAL)
 -m   get/set multiple sector count
 -n   get/set ignore-write-errors flag (0/1)
 -p   set PIO mode on IDE interface chipset (0,1,2,3,4,...)
 -P   set drive prefetch count
 -q   change next setting quietly
 -Q   get/set DMA tagged-queuing depth (if supported)
 -r   get/set device  readonly flag (DANGEROUS to set)
 -R   register an IDE interface (DANGEROUS)
 -S   set standby (spindown) timeout
 -t   perform device read timings
 -T   perform cache read timings
 -u   get/set unmaskirq flag (0/1)
 -U   un-register an IDE interface (DANGEROUS)
 -v   defaults; same as -mcudkrag for IDE drives
 -V   display program version and exit immediately
 -w   perform device reset (DANGEROUS)
 -W   set drive write-caching flag (0/1) (DANGEROUS)
 -x   tristate device for hotswap (0/1) (DANGEROUS)
 -X   set IDE xfer mode (DANGEROUS)
 -y   put IDE drive in standby mode
 -Y   put IDE drive to sleep
 -Z   disable Seagate auto-powersaving mode
 -z   re-read partition table

ATA Security Options:
 --security-freeze              Freeze security settings (until next reset)
 --security-unlock PWD          Unlock drive, using password PWD (DANGEROUS)
 --security-set-pass PWD        Lock drive, using password PWD (DANGEROUS)
 --security-disable PWD         Disable drive locking, using password PWD (DANGEROUS)
 --security-mode MODE           Specify user/master password and high/maximum security
        u       user password, high security
        U       user password, maximum security
        m       master password, high security
        M       master password, maximum security


How do I enable DMA..I'm a noob. Or is DMA not the issue? It is just hard to believe that I cannot achieve simple, smooth video playback. Thanks

PS I can bring up... sudo gedit /etc/hdparm.conf, and tried adding /dev/hdc {
   dma = on
   }

at the end of the script, but still no luck.

---

