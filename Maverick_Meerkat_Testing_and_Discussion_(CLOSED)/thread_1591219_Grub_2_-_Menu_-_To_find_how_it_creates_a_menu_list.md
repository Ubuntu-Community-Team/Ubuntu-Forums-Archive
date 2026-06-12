---
title: "Grub 2 - Menu - To find how it creates a menu list"
date: 2010-10-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2010-10-08
I thought I would add this as we had started to hijack another thread .....

The Grub2 Menu List shows all of our entries - but is not specific enough .....

I have

Ultimate Edition 2.8
PinguyOS
Zorin OS

But all are labelled as 10.04 or 10.10 in my Grub 2 menu ....... by tracking down how the system gets its information ...... maybe we can get it to customize the menu for us ......


It started here  [LINK]("http://ubuntuforums.org/showthread.php?p=9942222#post9942222")

> 
I must admit .... 

I created a custom menu once after ranch hand and yourself had shown me  how to do this - but the odd line from that ( that I had entered  manually ) got pulled into some other Grub 2 menus that I had running at  the time ( after grub-updates ) the grub 2 menus were on different  drives as far as I remember ......

At the time I thought it was strange ... and just put it down to being a glitch ....

It would be nice if it could identify them ..... maybe if we had one file in each boot folder
just with the identification string in it ..... the system could then easily go get them ....

OSNAME.txt .......... and in it .........  ZORIN 3 ( or whatever the OS happens to be )

Then it would just be a case of ..... if that file exists ...... use its contents as a Menu Option ....

Which directory is this in ? common.sh (got it)

[IMG]http://img163.imageshack.us/img163/2739/1screenshot1.jpg[/IMG]
                                                                                               __________________
                [LEFT]           :confused:     Thing's change - we can all learn something NEW ......
[Menu]("https://sites.google.com/site/000menu/")
[BootScript]("http://bootinfoscript.sourceforge.net/") 
[/LEFT]
             
                                                                                              *                                              [Last edited by 23dornot23d]("http://ubuntuforums.org/posthistory.php?p=9942100"); 46 Minutes Ago at 04:46 AM..                                                           *             

Then looking at the script it went to the prober labels ,,,, to grep info from here 

> 
Good to know you are sorted ..... its interesting now to know where the names are picked up from !!! :smile:

[IMG]http://img824.imageshack.us/img824/2008/screenshot2ym.jpg[/IMG]
I am also getting a lot of warnings ..... so would like to track down why too ...... !!!!

```

root@keith-laptop:/home/keith# update-grub
Generating grub.cfg ...
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
Found memtest86+ image: /boot/memtest86+.bin
Found Mandriva Linux 2010.0 (2010.0) on /dev/sda10
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
Found Ubuntu maverick (development branch) (10.10) on /dev/sda2
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
Found Ubuntu 10.10 (10.10) on /dev/sda5
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
Found Ubuntu maverick (development branch) (10.10) on /dev/sda6
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
Found Ubuntu 9.10 (9.10) on /dev/sda7
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
Found Ubuntu 8.10 (8.10) on /dev/sda8
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda9
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (/dev/sda,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,msdos5,msdos1).
done
root@keith-laptop:/home/keith# 


```The Menu is created ok ...... I just do not understamd why I suddenly have got all these warnings ....

[COLOR=Teal][B]sda1 is Maverick 10.10 .... running Gnome 3 with Compiz ....
sda2   is Ultimate Edition 2.8 ..... running Gnome-Shell
[/B][/COLOR][COLOR=Teal]**( a Ubuntu version 9.04 should be here too )**[/COLOR]
[COLOR=Teal]** sda5   is PinguyOS**[B]
    sda6 is A upgraded version of Linux mint .... to Lubuntu 10.10 ..... with Gnome Shell and Compiz GL
sda7   is Ubuntu 9.10[/B][B]
sda8   is Ubuntu 8.10
sda9   is Zorin 3
sda10 is Mandriva 2010

There is also a sda12 ......... 10.10 not showing up here ..... for test work ......

[[COLOR=Black]Link to Gparted Table[/COLOR]]("http://img828.imageshack.us/img828/618/gparted.jpg")
[/B][/COLOR]

---

### Post by drs305 on 2010-10-09
Well, here's my contribution. Just what the variables from some of the scripts in the /etc/grub.d folder:

> 
**VARIABLES / Example Result**

**10_linux:**

version_find_latest: 
linux: 		/boot/vmlinuz-2.6.32-22-generic 
basename: 	vmlinuz-2.6.32-22-generic 
dirname: 	/boot 
version:	2.6.32-22-generic 
alt_version: 	2.6.32-22-generic 
linux_root_device_thisversion: 	UUID=c5163c70-4f77-4034-a218-5dae03b07eed

**30_os-prober:**

DEVICE:   	/dev/sda9 
LONGNAME:  	Ubuntu 8.10 (8.10) 
OS: 		/dev/sda9:Ubuntu^8.10^(8.10):Ubuntu:linux 
LABEL:		Ubuntu 
BOOT: 		linux 
LROOT: 		/dev/sda9 
LINUX: 		/dev/sda9:/dev/sda9:Ubuntu^8.10,^kernel^2.6.27-9-generic:/boot/vmlinuz-2.6.27-9-generic:/boot/initrd.img-2.6.27-9-generic:root=UUID=ba83d184-705e-4115-9d42-0823c698a757^ro^splash^quiet 
LLABEL: 	Ubuntu 8.10, kernel 2.6.27-9-generic 
LKERNEL: 	/boot/vmlinuz-2.6.27-9-generic 
LINITRD:	/boot/initrd.img-2.6.27-9-generic 
LPARAMS: 	root=UUID=ba83d184-705e-4115-9d42-0823c698a757 ro splash quiet



As mentioned elsewhere, I know that os-prober can 'mine' information from the grub.cfg files from other linux partitions, and that linux-boot-prober and a script named common.sh also come into play when Grub2 searches a system for other OS's.

---

### Post by 23dornot23d on 2010-10-09
I am looking at that now the common.sh script 

line by line ....

```


the common.sh script is in ...... 

usr/share/os-prober/

shortly after it goes here to fins information I think .....

/var/lib/os-prober/labels

it has these same 2 lines

MandrivaLinux 1
Ubuntu 6

```Probably not using this info .... so moving right along .... lets look at the next bit ......

The common.sh script in OS-prober seems to find devices and then mount them ......

OK you are on the right track ..... looking at this is not making a lot of sense right now .....

I will have a fresh start in the morning ...... tired now .... 
just grep and sed ... learning what they extract and change.

I would like them to get the names from a file that I create .... so I guess that's the idea of custom
but I would like it to do it automatically for all my Distros and Menu items .... using names that
mean something to me ......

---

