---
title: "boot_info_script and natty"
date: 2011-01-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-01-18
Note to mods: I know this may seem to be a Natty problem but I know a lot of grub aficionados frequent this section of the forums and thought a heads up was in order ;)

I started a thread here:

[https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900](https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900)

> I first noticed with version 1.99~20101126-1ubuntu3 of grub-common and grub-pc the RESULTS.txt would post this: "Grub 2 is installed in the MBR of /dev/sda and looks for 9dem." With version 1.99~20110112-1ubuntu1 it's changed a bit more: "Grub 2 is installed in the MBR of /dev/sda and looks for :em." Of course with Natty being in early development I'm not too concerned but thought Meierfra would want to know. 

Just as it says, I've noticed that the newest versions of grub-pc and grub-common change the readout so you really can't tell what OS the MBR is assigned to, with the most current packages:

> => Grub 2 is installed in the MBR of /dev/sda and looks for :em.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

Not really sure how we'd work around that :confused:

Since I multi-boot a lot of distros I could presumably chroot any one OS and use "grub-probe -t device /boot/grub" to figure out which OS is controlling boot if I wasn't sure.

Any thoughts?

---

### Post by Quackers on 2011-01-18
This started happening for me after the first Natty grub updates. Apparently it is something to do with a hexdump in the boot script process. Obviously something has changed. I was hoping this wouldn't be an issue by the time Natty is released. Still am! :-)

---

### Post by kansasnoob on 2011-01-18
> **Quackers said:**
> This started happening for me after the first Natty grub updates. Apparently it is something to do with a hexdump in the boot script process. Obviously something has changed. I was hoping this wouldn't be an issue by the time Natty is released. Still am! :-)

ATM it's not a big deal but just thought I should mention it in case folks start seeing that behavior.

I'm having to think ahead a bit because I got roped into doing tax filing again this year for seniors and others that qualify due to low income. I really hate doing this!!!!!!!!!

I'm low income too, but soooooooooo many of these people are totally unappreciative it's like volunteering to be kicked in the ***!

---

### Post by Rubi1200 on 2011-01-18
Thanks for the information kansasnoob. Let's hope this does not become a problem (aside from all the other issues we have to deal with).

Good luck with the tax filings!

---

### Post by kansasnoob on 2011-01-24
I'm using this forum thread to post some info for Gert Hulselmans (re: the aforementioned SourceForge post):

[ATTACH]181847[/ATTACH]

Hopefully this will work :)

---

### Post by VMC on 2011-01-26
Running the boot_info_script under a natty install has a weird  statement:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for Bem.
```

But under Lucid it is correctly identified:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #10 for /boot/grub.

```

I have no idea what "Bem." is in reference to. Anyone else try boot_info_script yet under natty?

---

### Post by Quackers on 2011-01-26
Yes, it's been doing this for a few weeks. Mine says looking for 9cem.
I hope this is cleared up or sorted out some time before release. It would be a serious handicap in helping people with boot problems.

---

### Post by VMC on 2011-01-27
> **Quackers said:**
> Yes, it's been doing this for a few weeks. Mine says looking for 9cem.
I hope this is cleared up or sorted out some time before release. It would be a serious handicap in helping people with boot problems.

I believe its a boot_info_script problem. I need to register first at sourceforge to relay the bug.

Edit: Yes, its already been reported to SourceForge [here]("http://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900").

---

### Post by kansasnoob on 2011-01-27
I'm pursuing a fix for that with Gert Hulselmans:

[http://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900](http://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900)

In fact I need to send him some additional info ASAP.

---

### Post by kansasnoob on 2011-01-27
Attaching another file for Gert:

[ATTACH]182101[/ATTACH]

---

### Post by cariboo on 2011-01-27
Merged kansasnoob's thread from Installation & upgrades, by request.

---

### Post by kansasnoob on 2011-01-31
Just got notified of a new test version:

[https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900](https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900)

I'm having some trouble understanding just what to do :confused:

In my defense I'm all doped up because I dislocated my knee but I'm still smart enough to know when to share news ;)

It's great that this is a community project.

---

### Post by Quackers on 2011-01-31
Output is back to normal with that :-)
Smashing! Thanks :-)

---

### Post by VMC on 2011-02-01
> **kansasnoob said:**
> Just got notified of a new test version:

[https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900](https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900)

I'm having some trouble understanding just what to do :confused:

In my defense I'm all doped up because I dislocated my knee but I'm still smart enough to know when to share news ;)

It's great that this is a community project.

Thanks for first reporting to Sourceforge Kansas.

---

### Post by kansasnoob on 2011-02-01
My heads a bit clearer this AM and I now see where I was stumbling. I normally just "cd" whatever directory the script is in and copy-n-paste the "sudo bash" from the instructions in the script, eg: "sudo bash ./boot_info_script*.sh" as shown in the new script.

But, where "*" is a wildcard, if both the old and new script are in the same directory I guess things get confused ;) So it needs to be run as such:

```
sudo bash ./boot_info_script056-grub199.sh
```

That way both the old and new script can coexist in the same directory, in peace and harmony :lolflag:

I'll be able to really kick the tires and try several different scenarios as I perform update and iso-testing for Alpha 2.

I do think I'll probably just mention this to Gert also:

>  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => [B][COLOR="Red"]Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1[/COLOR][/B] for (,msdos1)/boot/grub.

That's actually incorrect as my drive sdb has no OS installed ATM. I actually ran "dpkg-reconfigure grub-pc" and installed grub to both MBRs and the PBR of it's / partition.

---

### Post by dino99 on 2011-02-01
> **kansasnoob said:**
> 

I do think I'll probably just mention this to Gert also:



That's actually incorrect as my drive sdb has no OS installed ATM. I actually ran "dpkg-reconfigure grub-pc" and installed grub to both MBRs and the PBR of it's / partition.

i've experimented grub installed only into PBR, got a warning: bad idea, bla bla) but it accept, then the bad surprise come: os-prober dont find it: still need to clean the design logic then clean the code.

---

### Post by kansasnoob on 2011-02-07
Posting a couple more tar.gz's for Gert Hulselmans.

[ATTACH]182917[/ATTACH]

[ATTACH]182918[/ATTACH]

---

### Post by kansasnoob on 2011-02-07
One more:

[ATTACH]182922[/ATTACH]

---

### Post by drs305 on 2011-02-07
With the differences in file formats about to appear once Grub 1.99/Natty is released, it might be nice to have the Grub version in the new script, if it isn't in there already. 

It will probably be apparent by looking at the file output but having it at the top of the page would make troubleshooting a bit easier.

Excuse the code:
```
grub-install -v | cut -d "(" -f2 | sed 's:): :g'
```

---

### Post by kansasnoob on 2011-02-07
Keep reading here:

[https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900/index/page/1](https://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900/index/page/1)

Gert is knocking out problems faster than I can catch my breath :D

---

### Post by kansasnoob on 2011-02-07
> **drs305 said:**
> With the differences in file formats about to appear once Grub 1.99/Natty is released, it might be nice to have the Grub version in the new script, if it isn't in there already. 

It will probably be apparent by looking at the file output but having it at the top of the page would make troubleshooting a bit easier.

Excuse the code:
```
grub-install -v | cut -d "(" -f2 | sed 's:): :g'
```

I hadn't thought about that but you may be right. Just as a personal desire I'd like to see it include "parted -l" (because I'm old and lazy) :lolflag:

Do you want me to ask if "grub-install -v" can be added to the BIS?

---

### Post by drs305 on 2011-02-07
> **kansasnoob said:**
> I hadn't thought about that but you may be right. Just as a personal desire I'd like to see it include "parted -l" (because I'm old and lazy) :lolflag:

Do you want me to ask if "grub-install -v" can be added to the BIS?

Yes, I think it would be helpful.

I monitor the site and see the good cooperation you two are achieving. I don't know how different (or large) the two versions of BIS will be, or whether they will be merged.  For the user it would be ideal for the script to identify the version of G2 being used and respond appropriately. I'm no scripter, so I'd just tack the two together with one conditional determining whether 1.98 or 1.99 is being used. Of course, I'm not the one writing or maintaining it.  ;-)

---

### Post by kansasnoob on 2011-02-07
Somewhat off-topic but I think this thread of mine should be retired:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

What do the rest of you think?

I know I get frustrated when I'm searching for a HowTo and it's outdated.

---

### Post by kansasnoob on 2011-02-07
> **drs305 said:**
> Yes, I think it would be helpful.

I monitor the site and see the good cooperation you two are achieving. I don't know how different (or large) the two versions of BIS will be, or whether they will be merged.  For the user it would be ideal for the script to identify the version of G2 being used and respond appropriately. I'm no scripter, so I'd just tack the two together with one conditional determining whether 1.98 or 1.99 is being used. Of course, I'm not the one writing or maintaining it.  ;-)

OK, I'll ask.

But I'm going to be patient. I don't want to flood Gert with request after request.

BTW thank you for all the work you've poured into the transition to grub2, without you things would have been nearly impossible!

---

### Post by drs305 on 2011-02-07
We all have skeletons in our closet...  ;-)

If you really want you could add a line at the top saying you aren't maintaining it any longer and I can close the thread.

Seriously though, from a quick scan it seems like the commands are still valid so I'd recommend leaving it.

---

### Post by kansasnoob on 2011-02-10
Are there any artists among us? The BIS is getting a major overhaul and one of the requests is as follows:

> Maybe you know somebody who wants to make an icon for Boot Info Script (favicon for the website).

It should look good at a size of 48x48.

But a greater size would be nice to, to add on the website itself.


I've never been artsy, and my graphics abilities are pitifully lacking. Sheesh, I have a hard time managing simple photos and such, so I really don't even understand "48x48" :redface:

I'm thinking it should indicate something diagnostic, any thoughts?

There is going to be a lot of testing involved, particularly because the new script will require 'gawk' because 'mawk' (default in Debian/Ubuntu) doesn't work for some of the new code, specifically:
- 'mawk' can't extract embedded grub4dos config file
- 'mawk' calculates wrong values for GiB/GB stuff (filefrag -v)

I'm currently making some changes to my installed OS's to be able to perform 10.04.2 iso and upgrade testing just prior to the 17th, and I'm digging out of a 17" snow storm, so my plate is rather full. But it'll be good to test this on all currently supported versions of Ubuntu so it's all worth the effort.

I do plan on doing some preliminary testing within just the next 24 hours or so and I'll do my best to keep everyone informed. In fact I just thought of something I need to check right after my next round of snow shoveling :frown:

---

### Post by kansasnoob on 2011-02-10
> **drs305 said:**
> We all have skeletons in our closet...  ;-)

If you really want you could add a line at the top saying you aren't maintaining it any longer and I can close the thread.

Seriously though, from a quick scan it seems like the commands are still valid so I'd recommend leaving it.

Yeah, let's just leave it for the time being. I do need to clean it up and add what to do if a separate /boot partition is used, which wouldn't be necessary if just installing legacy grub **always** worked without running what I'd call the "sanity check" in a grub shell. But I've tried the "official" way:

[https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy](https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy)

And sometimes it fails to generate all of the legacy grub files. Even my method fails occasionally if Step #3 is substituted with simply "grub-install /dev/sdX". I don't totally understand why, suffice it to say that legacy grub could be even more finicky than grub2.

---

### Post by kansasnoob on 2011-02-11
I was just fiddling around a bit this AM and I see this additional change:

NEW:

> sda1: __________________________________________________________________________

    File system:       ext3
    **[COLOR="Red"]Boot sector type:  Grub 1.97 - 1.98[/COLOR]**
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 12587135 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

OLD:

> sda1: _________________________________________________________________________

    File system:       ext3
    **[COLOR="Red"]Boot sector type:  Grub 2[/COLOR]**
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 12587135 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

Anyone interested in testing can always get the newest version available using wget:

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
```

That will drop BIS in your home directory.

---

### Post by Quackers on 2011-02-11
Tested the newest version and there seem to be one or two differences.
Grub is installed in sda and sdb on my system and the first lines of the script differ in their desciption of the partitions looked at for /boot/grub
I also don't see any output for the Boot sector type, in any of the ext4 partitions.
I'm still inspecting the output :-)

Edit  I see that the new BIS is outputting all instances of grub.cfg and etc/fstab installed (rather than just the one in control).

```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   157,645,844   157,645,782   7 NTFS / exFAT / HPFS
/dev/sda2         157,646,846   488,396,799   330,749,954   5 Extended
/dev/sda5         157,646,848   186,943,487    29,296,640  83 Linux
/dev/sda6         186,945,536   313,896,959   126,951,424  83 Linux
/dev/sda7         313,899,008   318,584,831     4,685,824  82 Linux swap / Solaris
/dev/sda8         318,586,880   343,975,935    25,389,056  83 Linux
/dev/sda9         343,977,984   488,396,799   144,418,816  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1         153,147,706   488,396,799   335,249,094   5 Extended
/dev/sdb5         153,147,708   157,453,064     4,305,357  82 Linux swap / Solaris
/dev/sdb6         157,453,128   179,976,194    22,523,067  83 Linux
/dev/sdb7         179,976,258   302,857,379   122,881,122  83 Linux
/dev/sdb8         302,858,240   488,396,799   185,538,560  83 Linux
/dev/sdb2    *      5,859,328    30,273,535    24,414,208  83 Linux
/dev/sdb3          30,282,525   153,147,644   122,865,120  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        24AFF28A10C76E23                       ntfs       New Volume
/dev/sda5        1ee3d06b-96cd-446f-a38d-277f6643d173   ext4       
/dev/sda6        bbc193e8-8fa3-4297-a338-d09714ad8b57   ext4       
/dev/sda7        b2c066b6-fb5e-4056-9e81-ca7762527c95   swap       
/dev/sda8        d3f093d0-c583-4d78-8e37-2b540a3b90a8   ext4       
/dev/sda9        928c40f2-f671-47ca-ba05-c4f0631ba106   ext4       
/dev/sdb2        3f349741-954f-46c9-9467-67f8a3abd277   ext4       
/dev/sdb3        e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2   ext4       
/dev/sdb5        594a1856-3e11-4728-9293-72e85b43ffe5   swap       
/dev/sdb6        6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb   ext4       
/dev/sdb7        5f1485be-ef78-4354-bde5-61b4454e113a   ext4       
/dev/sdb8        3639199d-deb5-445a-a5b9-0ff3a6e35a17   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
insmod tga
if background_image /usr/share/images/grub/B-1B_over_the_pacific_ocean.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
set linux_gfx_mode=1920x1200
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	echo	'Loading Linux 2.6.38-3-generic ...'
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-3-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-2-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux	/boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-2-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-2-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	echo	'Loading Linux 2.6.38-2-generic ...'
	linux	/boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-2-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 24AFF28A10C76E23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sdb8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sdb8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=bbc193e8-8fa3-4297-a338-d09714ad8b57 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  77.316799164 = 83.018280960   boot/grub/core.img                             1
  84.092079163 = 90.293182464   boot/grub/grub.cfg                             1
  78.363761902 = 84.142448640   boot/initrd.img-2.6.38-2-generic               2
  86.238769531 = 92.598173696   boot/initrd.img-2.6.38-3-generic               2
  78.652610779 = 84.452597760   boot/vmlinuz-2.6.38-2-generic                  2
  86.101852417 = 92.451160064   boot/vmlinuz-2.6.38-3-generic                  1
  86.238769531 = 92.598173696   initrd.img                                     2
  78.363761902 = 84.142448640   initrd.img.old                                 2
  86.101852417 = 92.451160064   vmlinuz                                        1
  78.652610779 = 84.452597760   vmlinuz.old                                    2

=========================== sda8/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
insmod tga
if background_image /usr/share/images/grub/Moraine_Lake_17092005.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
set linux_gfx_mode=1920x1200
export linux_gfx_mode
if [ "" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-1-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux	/boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-1-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-1-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	echo	'Loading Linux 2.6.38-1-generic ...'
	linux	/boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-1-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 24AFF28A10C76E23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=928c40f2-f671-47ca-ba05-c4f0631ba106 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=add3dc6e-bcd4-4f6b-8282-280a16d2636f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 154.053401947 = 165.413580800  boot/grub/core.img                             1
 159.117282867 = 170.850881536  boot/grub/grub.cfg                             1
 157.043312073 = 168.623972352  boot/initrd.img-2.6.38-1-generic               2
 153.109622955 = 164.400205824  boot/vmlinuz-2.6.38-1-generic                  1
 157.043312073 = 168.623972352  initrd.img                                     2
 153.109622955 = 164.400205824  vmlinuz                                        1

=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1920x1200
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 24aff28a10c76e23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=5f1485be-ef78-4354-bde5-61b4454e113a /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  79.348979950 = 85.200318464   boot/grub/core.img                             1
  79.651866913 = 85.525540864   boot/grub/grub.cfg                             1
  79.665321350 = 85.539987456   boot/initrd.img-2.6.32-28-generic              1
  79.601364136 = 85.471313920   boot/vmlinuz-2.6.32-28-generic                 1
  79.665321350 = 85.539987456   initrd.img                                     1
  79.601364136 = 85.471313920   vmlinuz                                        1

=========================== sdb8/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos8)'
search --no-floppy --fs-uuid --set=root 3639199d-deb5-445a-a5b9-0ff3a6e35a17
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos8)'
search --no-floppy --fs-uuid --set=root 3639199d-deb5-445a-a5b9-0ff3a6e35a17
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-2-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux	/boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-2-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-2-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	echo	'Loading Linux 2.6.38-2-generic ...'
	linux	/boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-2-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 24AFF28A10C76E23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 190.550930023 = 204.602503168  boot/grub/core.img                             1
 186.684844971 = 200.451325952  boot/grub/grub.cfg                             1
 144.808937073 = 155.487412224  boot/initrd.img-2.6.38-2-generic               2
 181.265892029 = 194.632769536  boot/vmlinuz-2.6.38-2-generic                  2
 144.808937073 = 155.487412224  initrd.img                                     2
 181.265892029 = 194.632769536  vmlinuz                                        2

=========================== sdb2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Maverick, with Linux 2.6.35-25' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1920x1200
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 24aff28a10c76e23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=3f349741-954f-46c9-9467-67f8a3abd277 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.927371979 = 9.585692672    boot/grub/core.img                             1
  11.788204193 = 12.657487872   boot/grub/grub.cfg                             2
   5.520507812 = 5.927600128    boot/initrd.img-2.6.35-25-generic              2
   9.207931519 = 9.886941184    boot/vmlinuz-2.6.35-25-generic                 1
   5.520507812 = 5.927600128    initrd.img                                     2
   9.207931519 = 9.886941184    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  41 00 00 30 78 43 30 30  35 30 30 37 42 00 00 30  |A..0xC005007B..0|
00000010  78 43 30 30 35 30 30 37  43 00 00 30 78 43 30 30  |xC005007C..0xC00|
00000020  35 30 30 37 44 00 00 30  78 43 30 30 35 30 30 37  |5007D..0xC005007|
00000030  45 00 00 30 78 43 30 30  35 30 30 37 46 00 00 56  |E..0xC005007F..V|
00000040  41 4c 49 44 41 54 49 4f  4e 5f 42 49 54 53 00 15  |ALIDATION_BITS..|
00000050  00 00 00 0a 00 2b 00 00  00 05 00 00 00 2b 00 00  |.....+.......+..|
00000060  00 0a 00 00 80 03 08 00  00 00 8c 12 00 00 94 12  |................|
00000070  00 00 00 03 00 00 00 07  00 00 00 9f 12 00 00 00  |................|
00000080  08 20 00 00 a7 12 00 00  00 75 69 6e 74 36 34 00  |. .......uint64.|
00000090  00 57 6d 69 44 61 74 61  49 64 00 00 42 69 74 4d  |.WmiDataId..BitM|
000000a0  61 70 00 0a 00 00 00 d3  12 00 00 d6 12 00 00 d9  |ap..............|
000000b0  12 00 00 dc 12 00 00 df  12 00 00 e2 12 00 00 e5  |................|
000000c0  12 00 00 e8 12 00 00 eb  12 00 00 ee 12 00 00 00  |................|
000000d0  30 00 00 31 00 00 32 00  00 33 00 00 34 00 00 35  |0..1..2..3..4..5|
000000e0  00 00 36 00 00 37 00 00  38 00 00 39 00 0c 00 00  |..6..7..8..9....|
000000f0  00 00 00 00 00 00 00 00  80 06 00 00 00 4d 00 53  |.............M.S|
00000100  00 4e 00 64 00 69 00 73  00 a9 b4 9e df 7e fe c6  |.N.d.i.s.....~..|
00000110  01 c8 01 00 00 00 00 00  00 00 09 00 00 00 10 00  |................|
00000120  00 00 00 4d 53 4e 64 69  73 00 08 00 00 00 41 00  |...MSNdis.....A.|
00000130  00 00 16 00 00 00 00 0b  00 00 00 ff ff 07 00 00  |................|
00000140  80 01 0b 00 00 00 ff ff  06 00 00 80 00 08 00 00  |................|
00000150  00 1b 00 00 00 24 00 00  00 00 08 00 00 00 2a 00  |.....$........*.|
00000160  00 00 52 00 00 00 00 03  00 00 00 01 00 00 00 03  |..R.............|
00000170  00 00 00 5e 00 00 00 66  00 00 00 99 00 00 00 a7  |...^...f........|
00000180  00 00 00 e4 00 00 00 f7  00 00 00 55 ff ff ff ff  |...........U....|
00000190  ff ff ff ff 41 01 00 80  00 4d 53 4e 64 69 73 5f  |....A....MSNdis_|
000001a0  44 72 69 76 65 72 56 65  72 73 69 6f 6e 00 00 57  |DriverVersion..W|
000001b0  4d 49 00 00 57 4d 49 50  72 6f 76 00 00 67 00 fe  |MI..WMIProv..g..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 bf 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 08  bf 01 00 28 91 07 00 00  |...........(....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by kansasnoob on 2011-02-11
@ Quackers,

If you could please provide the actual differences between versions like I did previously.

I hope we can find some artist to create a favicon :D

I've been working on figuring out just what versions of gawk and/or mawk are installed in current versions of Ubuntu and if installing gawk creates any conflicts.

I'm now testing a few different versions of Puppy.

---

### Post by Quackers on 2011-02-11
I ran this script (version 056) from a fully updated Natty alpha1 installation a few minutes ago. The second was run using the old (055) version from the same installation.
I needed to install gawk before the new version would run.
An icon would be nice (maybe a magnifying glass looking at script, or something) but, alas, I am no graphics type either :-(

Any further details, just ask.
```
                Boot Info Script 0.56-wip    dated January 31th, 2011                    

============================= Boot Info Summary: ===============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   157,645,844   157,645,782   7 NTFS / exFAT / HPFS
/dev/sda2         157,646,846   488,396,799   330,749,954   5 Extended
/dev/sda5         157,646,848   186,943,487    29,296,640  83 Linux
/dev/sda6         186,945,536   313,896,959   126,951,424  83 Linux
/dev/sda7         313,899,008   318,584,831     4,685,824  82 Linux swap / Solaris
/dev/sda8         318,586,880   343,975,935    25,389,056  83 Linux
/dev/sda9         343,977,984   488,396,799   144,418,816  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         153,147,706   302,857,379   149,709,674   5 Extended
/dev/sdb5         153,147,708   157,453,064     4,305,357  82 Linux swap / Solaris
/dev/sdb6         157,453,128   179,976,194    22,523,067  83 Linux
/dev/sdb7         179,976,258   302,857,379   122,881,122  83 Linux
/dev/sdb2    *      5,859,328    30,273,535    24,414,208  83 Linux
/dev/sdb3          30,282,525   153,147,644   122,865,120  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        24AFF28A10C76E23                       ntfs       New Volume                    
/dev/sda5        1ee3d06b-96cd-446f-a38d-277f6643d173   ext4                                     
/dev/sda6        bbc193e8-8fa3-4297-a338-d09714ad8b57   ext4                                     
/dev/sda7        b2c066b6-fb5e-4056-9e81-ca7762527c95   swap                                     
/dev/sda8        d3f093d0-c583-4d78-8e37-2b540a3b90a8   ext4                                     
/dev/sda9        928c40f2-f671-47ca-ba05-c4f0631ba106   ext4                                     
/dev/sdb2        3f349741-954f-46c9-9467-67f8a3abd277   ext4                                     
/dev/sdb3        e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2   ext4                                     
/dev/sdb5        594a1856-3e11-4728-9293-72e85b43ffe5   swap                                     
/dev/sdb6        6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb   ext4                                     
/dev/sdb7        5f1485be-ef78-4354-bde5-61b4454e113a   ext4                                     

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
insmod tga
if background_image /usr/share/images/grub/B-1B_over_the_pacific_ocean.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
set linux_gfx_mode=1920x1200
export linux_gfx_mode
if [ "" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-1-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux	/boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-1-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-1-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	echo	'Loading Linux 2.6.38-1-generic ...'
	linux	/boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-1-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 24AFF28A10C76E23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=bbc193e8-8fa3-4297-a338-d09714ad8b57 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=add3dc6e-bcd4-4f6b-8282-280a16d2636f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

 75.3859 GiB / 80.945 GB   :  boot/grub/core.img                  1 fragments(s)
  76.001 GiB / 81.6054 GB  :  boot/grub/grub.cfg                  1 fragments(s)
 75.6896 GiB / 81.271 GB   :  boot/initrd.img-2.6.38-1-generic    2 fragments(s)
 75.3552 GiB / 80.9121 GB  :  boot/vmlinuz-2.6.38-1-generic       2 fragments(s)
 75.6896 GiB / 81.271 GB   :  initrd.img                          2 fragments(s)
 75.3552 GiB / 80.9121 GB  :  vmlinuz                             2 fragments(s)

=========================== sda8/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
insmod tga
if background_image /usr/share/images/grub/Moraine_Lake_17092005.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
set linux_gfx_mode=1920x1200
export linux_gfx_mode
if [ "" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-1-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux	/boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-1-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-1-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	echo	'Loading Linux 2.6.38-1-generic ...'
	linux	/boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-1-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 24AFF28A10C76E23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=928c40f2-f671-47ca-ba05-c4f0631ba106 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=add3dc6e-bcd4-4f6b-8282-280a16d2636f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

 152.128 GiB / 163.346 GB  :  boot/grub/core.img                  1 fragments(s)
 152.633 GiB / 163.889 GB  :  boot/grub/grub.cfg                  1 fragments(s)
 152.426 GiB / 163.666 GB  :  boot/initrd.img-2.6.38-1-generic    2 fragments(s)
 152.033 GiB / 163.245 GB  :  boot/vmlinuz-2.6.38-1-generic       1 fragments(s)
 152.426 GiB / 163.666 GB  :  initrd.img                          2 fragments(s)
 152.033 GiB / 163.245 GB  :  vmlinuz                             1 fragments(s)

=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1920x1200
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 24aff28a10c76e23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=5f1485be-ef78-4354-bde5-61b4454e113a /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

 75.5096 GiB / 81.0778 GB  :  boot/grub/core.img                  1 fragments(s)
 75.7613 GiB / 81.3481 GB  :  boot/grub/grub.cfg                  1 fragments(s)
 75.5374 GiB / 81.1077 GB  :  boot/initrd.img-2.6.32-28-generic   1 fragments(s)
  75.531 GiB / 81.1008 GB  :  boot/vmlinuz-2.6.32-28-generic      1 fragments(s)
 75.5374 GiB / 81.1077 GB  :  initrd.img                          1 fragments(s)
  75.531 GiB / 81.1008 GB  :  vmlinuz                             1 fragments(s)

=========================== sdb2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Maverick, with Linux 2.6.35-25' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1920x1200
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 24aff28a10c76e23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=3f349741-954f-46c9-9467-67f8a3abd277 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

 3.40639 GiB / 3.65758 GB  :  boot/grub/core.img                  1 fragments(s)
 3.69205 GiB / 3.96431 GB  :  boot/grub/grub.cfg                  2 fragments(s)
  3.0662 GiB / 3.29231 GB  :  boot/initrd.img-2.6.35-25-generic   2 fragments(s)
  3.4344 GiB / 3.68766 GB  :  boot/vmlinuz-2.6.35-25-generic      1 fragments(s)
  3.0662 GiB / 3.29231 GB  :  initrd.img                          2 fragments(s)
  3.4344 GiB / 3.68766 GB  :  vmlinuz                             1 fragments(s)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  41 00 00 30 78 43 30 30  35 30 30 37 42 00 00 30  |A..0xC005007B..0|
00000010  78 43 30 30 35 30 30 37  43 00 00 30 78 43 30 30  |xC005007C..0xC00|
00000020  35 30 30 37 44 00 00 30  78 43 30 30 35 30 30 37  |5007D..0xC005007|
00000030  45 00 00 30 78 43 30 30  35 30 30 37 46 00 00 56  |E..0xC005007F..V|
00000040  41 4c 49 44 41 54 49 4f  4e 5f 42 49 54 53 00 15  |ALIDATION_BITS..|
00000050  00 00 00 0a 00 2b 00 00  00 05 00 00 00 2b 00 00  |.....+.......+..|
00000060  00 0a 00 00 80 03 08 00  00 00 8c 12 00 00 94 12  |................|
00000070  00 00 00 03 00 00 00 07  00 00 00 9f 12 00 00 00  |................|
00000080  08 20 00 00 a7 12 00 00  00 75 69 6e 74 36 34 00  |. .......uint64.|
00000090  00 57 6d 69 44 61 74 61  49 64 00 00 42 69 74 4d  |.WmiDataId..BitM|
000000a0  61 70 00 0a 00 00 00 d3  12 00 00 d6 12 00 00 d9  |ap..............|
000000b0  12 00 00 dc 12 00 00 df  12 00 00 e2 12 00 00 e5  |................|
000000c0  12 00 00 e8 12 00 00 eb  12 00 00 ee 12 00 00 00  |................|
000000d0  30 00 00 31 00 00 32 00  00 33 00 00 34 00 00 35  |0..1..2..3..4..5|
000000e0  00 00 36 00 00 37 00 00  38 00 00 39 00 0c 00 00  |..6..7..8..9....|
000000f0  00 00 00 00 00 00 00 00  80 06 00 00 00 4d 00 53  |.............M.S|
00000100  00 4e 00 64 00 69 00 73  00 a9 b4 9e df 7e fe c6  |.N.d.i.s.....~..|
00000110  01 c8 01 00 00 00 00 00  00 00 09 00 00 00 10 00  |................|
00000120  00 00 00 4d 53 4e 64 69  73 00 08 00 00 00 41 00  |...MSNdis.....A.|
00000130  00 00 16 00 00 00 00 0b  00 00 00 ff ff 07 00 00  |................|
00000140  80 01 0b 00 00 00 ff ff  06 00 00 80 00 08 00 00  |................|
00000150  00 1b 00 00 00 24 00 00  00 00 08 00 00 00 2a 00  |.....$........*.|
00000160  00 00 52 00 00 00 00 03  00 00 00 01 00 00 00 03  |..R.............|
00000170  00 00 00 5e 00 00 00 66  00 00 00 99 00 00 00 a7  |...^...f........|
00000180  00 00 00 e4 00 00 00 f7  00 00 00 55 ff ff ff ff  |...........U....|
00000190  ff ff ff ff 41 01 00 80  00 4d 53 4e 64 69 73 5f  |....A....MSNdis_|
000001a0  44 72 69 76 65 72 56 65  72 73 69 6f 6e 00 00 57  |DriverVersion..W|
000001b0  4d 49 00 00 57 4d 49 50  72 6f 76 00 00 67 00 fe  |MI..WMIProv..g..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 bf 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 08  bf 01 00 28 91 07 00 00  |...........(....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for Bem.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   157,645,844   157,645,782   7 HPFS/NTFS
/dev/sda2         157,646,846   488,396,799   330,749,954   5 Extended
/dev/sda5         157,646,848   186,943,487    29,296,640  83 Linux
/dev/sda6         186,945,536   313,896,959   126,951,424  83 Linux
/dev/sda7         313,899,008   318,584,831     4,685,824  82 Linux swap / Solaris
/dev/sda8         318,586,880   343,975,935    25,389,056  83 Linux
/dev/sda9         343,977,984   488,396,799   144,418,816  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         153,147,706   488,396,799   335,249,094   5 Extended
/dev/sdb5         153,147,708   157,453,064     4,305,357  82 Linux swap / Solaris
/dev/sdb6         157,453,128   179,976,194    22,523,067  83 Linux
/dev/sdb7         179,976,258   302,857,379   122,881,122  83 Linux
/dev/sdb2    *      5,859,328    30,273,535    24,414,208  83 Linux
/dev/sdb3          30,282,525   153,147,644   122,865,120  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        24AFF28A10C76E23                       ntfs       New Volume                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1ee3d06b-96cd-446f-a38d-277f6643d173   ext4                                     
/dev/sda6        bbc193e8-8fa3-4297-a338-d09714ad8b57   ext4                                     
/dev/sda7        b2c066b6-fb5e-4056-9e81-ca7762527c95   swap                                     
/dev/sda8        d3f093d0-c583-4d78-8e37-2b540a3b90a8   ext4                                     
/dev/sda9        928c40f2-f671-47ca-ba05-c4f0631ba106   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        3f349741-954f-46c9-9467-67f8a3abd277   ext4                                     
/dev/sdb3        e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2   ext4                                     
/dev/sdb5        594a1856-3e11-4728-9293-72e85b43ffe5   swap                                     
/dev/sdb6        6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb   ext4                                     
/dev/sdb7        5f1485be-ef78-4354-bde5-61b4454e113a   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
insmod tga
if background_image /usr/share/images/grub/B-1B_over_the_pacific_ocean.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
set linux_gfx_mode=1920x1200
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	echo	'Loading Linux 2.6.38-3-generic ...'
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-3-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 24AFF28A10C76E23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=bbc193e8-8fa3-4297-a338-d09714ad8b57 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  83.0GB: boot/grub/core.img
  90.1GB: boot/grub/grub.cfg
  92.5GB: boot/initrd.img-2.6.38-3-generic
  92.4GB: boot/vmlinuz-2.6.38-3-generic
  92.5GB: initrd.img
  92.4GB: vmlinuz

=========================== sda8/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
insmod tga
if background_image /usr/share/images/grub/Moraine_Lake_17092005.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
set linux_gfx_mode=1920x1200
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	echo	'Loading Linux 2.6.38-3-generic ...'
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-3-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 24AFF28A10C76E23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sdb8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sdb8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=928c40f2-f671-47ca-ba05-c4f0631ba106 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 165.4GB: boot/grub/core.img
 169.9GB: boot/grub/grub.cfg
 173.3GB: boot/initrd.img-2.6.38-3-generic
 168.6GB: boot/vmlinuz-2.6.38-3-generic
 173.3GB: initrd.img
 168.6GB: vmlinuz

=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1920x1200
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 24aff28a10c76e23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=5f1485be-ef78-4354-bde5-61b4454e113a /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


  85.2GB: boot/grub/core.img
  85.5GB: boot/grub/grub.cfg
  85.5GB: boot/initrd.img-2.6.32-28-generic
  85.4GB: boot/vmlinuz-2.6.32-28-generic
  85.5GB: initrd.img
  85.4GB: vmlinuz

=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Maverick, with Linux 2.6.35-25' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1920x1200
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 24aff28a10c76e23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=3f349741-954f-46c9-9467-67f8a3abd277 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


   9.5GB: boot/grub/core.img
  12.6GB: boot/grub/grub.cfg
   5.8GB: boot/initrd.img-2.6.35-25-generic
   9.8GB: boot/vmlinuz-2.6.35-25-generic
   5.8GB: initrd.img
   9.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  41 00 00 30 78 43 30 30  35 30 30 37 42 00 00 30  |A..0xC005007B..0|
00000010  78 43 30 30 35 30 30 37  43 00 00 30 78 43 30 30  |xC005007C..0xC00|
00000020  35 30 30 37 44 00 00 30  78 43 30 30 35 30 30 37  |5007D..0xC005007|
00000030  45 00 00 30 78 43 30 30  35 30 30 37 46 00 00 56  |E..0xC005007F..V|
00000040  41 4c 49 44 41 54 49 4f  4e 5f 42 49 54 53 00 15  |ALIDATION_BITS..|
00000050  00 00 00 0a 00 2b 00 00  00 05 00 00 00 2b 00 00  |.....+.......+..|
00000060  00 0a 00 00 80 03 08 00  00 00 8c 12 00 00 94 12  |................|
00000070  00 00 00 03 00 00 00 07  00 00 00 9f 12 00 00 00  |................|
00000080  08 20 00 00 a7 12 00 00  00 75 69 6e 74 36 34 00  |. .......uint64.|
00000090  00 57 6d 69 44 61 74 61  49 64 00 00 42 69 74 4d  |.WmiDataId..BitM|
000000a0  61 70 00 0a 00 00 00 d3  12 00 00 d6 12 00 00 d9  |ap..............|
000000b0  12 00 00 dc 12 00 00 df  12 00 00 e2 12 00 00 e5  |................|
000000c0  12 00 00 e8 12 00 00 eb  12 00 00 ee 12 00 00 00  |................|
000000d0  30 00 00 31 00 00 32 00  00 33 00 00 34 00 00 35  |0..1..2..3..4..5|
000000e0  00 00 36 00 00 37 00 00  38 00 00 39 00 0c 00 00  |..6..7..8..9....|
000000f0  00 00 00 00 00 00 00 00  80 06 00 00 00 4d 00 53  |.............M.S|
00000100  00 4e 00 64 00 69 00 73  00 a9 b4 9e df 7e fe c6  |.N.d.i.s.....~..|
00000110  01 c8 01 00 00 00 00 00  00 00 09 00 00 00 10 00  |................|
00000120  00 00 00 4d 53 4e 64 69  73 00 08 00 00 00 41 00  |...MSNdis.....A.|
00000130  00 00 16 00 00 00 00 0b  00 00 00 ff ff 07 00 00  |................|
00000140  80 01 0b 00 00 00 ff ff  06 00 00 80 00 08 00 00  |................|
00000150  00 1b 00 00 00 24 00 00  00 00 08 00 00 00 2a 00  |.....$........*.|
00000160  00 00 52 00 00 00 00 03  00 00 00 01 00 00 00 03  |..R.............|
00000170  00 00 00 5e 00 00 00 66  00 00 00 99 00 00 00 a7  |...^...f........|
00000180  00 00 00 e4 00 00 00 f7  00 00 00 55 ff ff ff ff  |...........U....|
00000190  ff ff ff ff 41 01 00 80  00 4d 53 4e 64 69 73 5f  |....A....MSNdis_|
000001a0  44 72 69 76 65 72 56 65  72 73 69 6f 6e 00 00 57  |DriverVersion..W|
000001b0  4d 49 00 00 57 4d 49 50  72 6f 76 00 00 67 00 fe  |MI..WMIProv..g..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 bf 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 08  bf 01 00 28 91 07 00 00  |...........(....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by kansasnoob on 2011-02-11
I need to post some info for the BIS devs and due to my visual impairment I'm posting it here so my head doesn't explode :D

Regarding mawk and gawk (aka:GNU Awk) , most recent version of Ubuntu first:

Natty/11.04 Alpha2
mawk 1.3.3 is installed
GNU Awk 3.1.7 is installed

Maverick/10.10
mawk 1.3.3 is installed
GNU Awk 3.1.7 is installed

Lucid/10.04 LTS
mawk 1.3.3 is installed
GNU Awk 3.1.6 is installed

Karmic/9.10
mawk 1.3.3 is installed
**The program 'gawk' is currently not installed.** Installation warning highlighted:
```
lance@lance-desktop:~$ sudo apt-get install gawk
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gawk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 525kB of archives.
After this operation, 2,122kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com karmic/main gawk 1:3.1.6.dfsg-0ubuntu2 [525kB]
Fetched 525kB in 2s (235kB/s)
Selecting previously deselected package gawk.
(Reading database ... 155258 files and directories currently installed.)
Unpacking gawk (from .../gawk_1%3a3.1.6.dfsg-0ubuntu2_i386.deb) ...
Processing triggers for install-info ...
**[COLOR="Red"]install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'[/COLOR]**
Processing triggers for man-db ...
Setting up gawk (1:3.1.6.dfsg-0ubuntu2) ...
```

Hardy/8.04 LTS
mawk 1.3.3 is installed
**The program 'gawk' is currently not installed.** Installation appears to go OK:
```
lance@lance-desktop:~$ sudo apt-get install gawk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-26-generic linux-headers-2.6.24-26
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gawk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 500kB of archives.
After this operation, 2060kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/main gawk 1:3.1.6.dfsg-0ubuntu1 [500kB]
Fetched 500kB in 2s (215kB/s)
Selecting previously deselected package gawk.
(Reading database ... 113974 files and directories currently installed.)
Unpacking gawk (from .../gawk_1%3a3.1.6.dfsg-0ubuntu1_i386.deb) ...
Setting up gawk (1:3.1.6.dfsg-0ubuntu1) ...
```

NOTE: I'm concentrating on desktop versions and both 9.10 and 8.04 reach end-of-life this April, but the 8.04 server version is supported until April 2013. Regardless read on about BIS results in 8.04:

This is what the MBR info looks like with the newest version of the script run from 8.04:

>  => Grub Legacy  is installed in the MBR of /dev/sda and [B][COLOR="Red"]looks on boot drive 
    #-128[/COLOR][/B] in partition #12 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #14 for /boot/grub.
 => Syslinux MBR is installed in the MBR of /dev/sdc.

With the older version of the script it looks like this:

> => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #12 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #14 for gnak.
 => Syslinux is installed in the MBR of /dev/sdc

Regardless there are problems in both regarding the ability of the kernel to "read" ext4 partitions, etc.

The old script results are here:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #12 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #14 for gnak.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 12587135 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 169853109 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda14: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda15: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda16: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''

sda17: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda18: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type 'ext4'

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a6391

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    84,646,484    84,646,422  83 Linux
/dev/sda2          84,646,485   168,313,004    83,666,520  83 Linux
/dev/sda3         168,313,005   252,349,019    84,036,015  83 Linux
/dev/sda4         252,349,020   976,768,064   724,419,045   5 Extended
/dev/sda5         631,209,978   738,861,479   107,651,502  83 Linux
/dev/sda6         738,861,543   843,637,409   104,775,867  83 Linux
/dev/sda7         843,637,473   950,919,479   107,282,007  83 Linux
/dev/sda8         950,919,543   971,852,174    20,932,632  83 Linux
/dev/sda9         971,852,238   976,768,064     4,915,827  82 Linux swap / Solaris
/dev/sda10        588,637,728   631,209,914    42,572,187  83 Linux
/dev/sda11        546,161,868   588,637,664    42,475,797  83 Linux
/dev/sda12        503,878,788   546,161,804    42,283,017  83 Linux
/dev/sda13        460,904,913   503,878,724    42,973,812  83 Linux
/dev/sda14        295,001,721   336,144,059    41,142,339  83 Linux
/dev/sda15        336,144,123   377,318,654    41,174,532  83 Linux
/dev/sda16        377,318,718   419,119,784    41,801,067  83 Linux
/dev/sda17        419,119,848   460,904,849    41,785,002  83 Linux
/dev/sda18        252,350,464   295,000,063    42,649,600  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002c729

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    17,816,084    17,816,022  83 Linux
/dev/sdb2          17,816,085   156,296,384   138,480,300   5 Extended
/dev/sdb5          17,816,148   151,316,234   133,500,087  83 Linux
/dev/sdb6         151,316,298   156,296,384     4,980,087  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000563a8

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048     4,948,019     4,945,972   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       6114df72-5fec-467a-b6cf-bfb49b76def1   ext4       Mint Julia                    
/dev/sda11       ed0bdce8-0af8-4cce-9933-cbac8389fe4d   ext4       Squeeze                       
/dev/sda12       96bef601-3776-4e41-bf5a-ca81d3e5058d   ext3       Hardy                         
/dev/sda13       720d719e-e571-4bdd-aac9-718f0ffe2266   ext4       Peppermint                    
/dev/sda14       8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079   ext4       MM to NN A2                   
/dev/sda15       22eefad4-870e-4191-87c9-57f4e756411d   ext4       LMDE                          
/dev/sda1        b7a0df33-53e4-4f0d-856b-0da92ff0d743   ext3       Maverick                      
/dev/sda2        1332b9d0-cf18-4299-9094-12acbdac91ad   ext3       Karmic                        
/dev/sda3        d252929b-949d-432e-a18c-18f9ae770d28   ext3       Lucid                         
/dev/sda5        594c3d40-2791-4c0a-8644-d9812545da2d   ext3       Backups                       
/dev/sda6        8a3f6c83-cb52-4caf-96b8-5faf2c830453   ext3       Pictures                      
/dev/sda7        05289ee4-d681-4806-b6fd-aefd784f9323   ext3       Downloads                     
/dev/sda8        571cfad8-68c7-4703-883e-c0baa2a381d4   ext3       Documents                     
/dev/sda9        80627269-1ccd-4774-b4ea-a5ef8824ffaa   swap                                     
/dev/sdb1        04d890c5-9f08-4cfe-ac93-c31dc8fe7e07   ext4                                     
/dev/sdb5        b9aab6d9-b9a9-44c6-abc5-63e2edcfc84d   ext4                                     
/dev/sdb6        ae8fa315-50cc-4dc8-8edd-d3b9c28ebb7d   swap                                     
/dev/sdc1        0E23-8903                              vfat       DATA                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda12       /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdc1        /media/DATA              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=60
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-26-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	echo	'Loading Linux 2.6.35-26-generic ...'
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set 8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set 8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda16)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set 7a90aa0c-2377-48e4-97ad-20283c962abc
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=7a90aa0c-2377-48e4-97ad-20283c962abc ro vga=792 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda16)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set 7a90aa0c-2377-48e4-97ad-20283c962abc
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=7a90aa0c-2377-48e4-97ad-20283c962abc ro single vga=792
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda18)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos18)'
	search --no-floppy --fs-uuid --set ff93a40e-f9a6-4864-b3f2-0f357263f689
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff93a40e-f9a6-4864-b3f2-0f357263f689 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda18)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos18)'
	search --no-floppy --fs-uuid --set ff93a40e-f9a6-4864-b3f2-0f357263f689
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff93a40e-f9a6-4864-b3f2-0f357263f689 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sda3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=d252929b-949d-432e-a18c-18f9ae770d28 ro quiet splash
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sda3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=d252929b-949d-432e-a18c-18f9ae770d28 ro single
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda10) (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 6114df72-5fec-467a-b6cf-bfb49b76def1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6114df72-5fec-467a-b6cf-bfb49b76def1 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda10) -- recovery mode (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 6114df72-5fec-467a-b6cf-bfb49b76def1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6114df72-5fec-467a-b6cf-bfb49b76def1 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set ed0bdce8-0af8-4cce-9933-cbac8389fe4d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=ed0bdce8-0af8-4cce-9933-cbac8389fe4d ro quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set ed0bdce8-0af8-4cce-9933-cbac8389fe4d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=ed0bdce8-0af8-4cce-9933-cbac8389fe4d ro single
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Lubuntu 10.10, kernel 2.6.35-24-generic (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 9b5de705-ccb3-4cb4-b692-75b0ebfcb276
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b5de705-ccb3-4cb4-b692-75b0ebfcb276 ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Lubuntu 10.10, kernel 2.6.35-24-generic (recovery mode) (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 9b5de705-ccb3-4cb4-b692-75b0ebfcb276
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b5de705-ccb3-4cb4-b692-75b0ebfcb276 ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Peppermint, 2.6.32-24-generic (/dev/sda13) (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set 720d719e-e571-4bdd-aac9-718f0ffe2266
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=720d719e-e571-4bdd-aac9-718f0ffe2266 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Peppermint, 2.6.32-24-generic (/dev/sda13) -- recovery mode (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set 720d719e-e571-4bdd-aac9-718f0ffe2266
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=720d719e-e571-4bdd-aac9-718f0ffe2266 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda15)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos15)'
	search --no-floppy --fs-uuid --set 22eefad4-870e-4191-87c9-57f4e756411d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=22eefad4-870e-4191-87c9-57f4e756411d ro splash quiet quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda15)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos15)'
	search --no-floppy --fs-uuid --set 22eefad4-870e-4191-87c9-57f4e756411d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=22eefad4-870e-4191-87c9-57f4e756411d ro single splash quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda17)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos17)'
	search --no-floppy --fs-uuid --set d70bbade-c57d-4c81-84e1-7674021673d6
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d70bbade-c57d-4c81-84e1-7674021673d6 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda17)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos17)'
	search --no-floppy --fs-uuid --set d70bbade-c57d-4c81-84e1-7674021673d6
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d70bbade-c57d-4c81-84e1-7674021673d6 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 1332b9d0-cf18-4299-9094-12acbdac91ad
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 1332b9d0-cf18-4299-9094-12acbdac91ad
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
# swap is on /dev/sda9
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw                0       0
#/dev/sda5    /mnt/sda5 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda5       ext3    defaults          0       2
#/dev/sda6    /mnt/sda6 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda6       ext3    defaults          0       2     
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda8       ext3    defaults          0       2

=================== sda1: Location of files loaded by Grub: ===================


   6.5GB: boot/grub/core.img
   6.5GB: boot/grub/grub.cfg
   6.4GB: boot/initrd.img-2.6.35-22-generic
   6.3GB: boot/initrd.img-2.6.35-23-generic
   6.3GB: boot/initrd.img-2.6.35-24-generic
   6.4GB: boot/initrd.img-2.6.35-25-generic
   6.4GB: boot/initrd.img-2.6.35-26-generic
   6.3GB: boot/vmlinuz-2.6.35-22-generic
   6.3GB: boot/vmlinuz-2.6.35-23-generic
   6.3GB: boot/vmlinuz-2.6.35-24-generic
   6.3GB: boot/vmlinuz-2.6.35-25-generic
   6.4GB: boot/vmlinuz-2.6.35-26-generic
   6.4GB: initrd.img
   6.4GB: initrd.img.old
   6.4GB: vmlinuz
   6.3GB: vmlinuz.old

=========================== sda2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1332b9d0-cf18-4299-9094-12acbdac91ad

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-22-generic
uuid		1332b9d0-cf18-4299-9094-12acbdac91ad
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid		1332b9d0-cf18-4299-9094-12acbdac91ad
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=1332b9d0-cf18-4299-9094-12acbdac91ad /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw                0       0
#/dev/sda5    /mnt/sda5 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda5       ext3    defaults          0       2
#/dev/sda6    /mnt/sda6 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda6       ext3    defaults          0       2     
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda8       ext3    defaults          0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  56.0GB: boot/grub/menu.lst
  56.0GB: boot/initrd.img-2.6.31-21-generic
  56.0GB: boot/initrd.img-2.6.31-22-generic
  56.0GB: boot/vmlinuz-2.6.31-21-generic
  56.0GB: boot/vmlinuz-2.6.31-22-generic
  56.0GB: initrd.img.old
  56.0GB: vmlinuz.old

=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=40
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-29-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=d252929b-949d-432e-a18c-18f9ae770d28 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=d252929b-949d-432e-a18c-18f9ae770d28 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda10) (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 6114df72-5fec-467a-b6cf-bfb49b76def1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6114df72-5fec-467a-b6cf-bfb49b76def1 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda10) -- recovery mode (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 6114df72-5fec-467a-b6cf-bfb49b76def1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6114df72-5fec-467a-b6cf-bfb49b76def1 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda11)" {
	insmod ext2
	set root='(hd0,11)'
	search --no-floppy --fs-uuid --set ed0bdce8-0af8-4cce-9933-cbac8389fe4d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=ed0bdce8-0af8-4cce-9933-cbac8389fe4d ro quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda11)" {
	insmod ext2
	set root='(hd0,11)'
	search --no-floppy --fs-uuid --set ed0bdce8-0af8-4cce-9933-cbac8389fe4d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=ed0bdce8-0af8-4cce-9933-cbac8389fe4d ro single
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Lubuntu 10.10, kernel 2.6.35-24-generic (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set 9b5de705-ccb3-4cb4-b692-75b0ebfcb276
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b5de705-ccb3-4cb4-b692-75b0ebfcb276 ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Lubuntu 10.10, kernel 2.6.35-24-generic (recovery mode) (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set 9b5de705-ccb3-4cb4-b692-75b0ebfcb276
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b5de705-ccb3-4cb4-b692-75b0ebfcb276 ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Peppermint, 2.6.32-24-generic (/dev/sda13) (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,13)'
	search --no-floppy --fs-uuid --set 720d719e-e571-4bdd-aac9-718f0ffe2266
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=720d719e-e571-4bdd-aac9-718f0ffe2266 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Peppermint, 2.6.32-24-generic (/dev/sda13) -- recovery mode (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,13)'
	search --no-floppy --fs-uuid --set 720d719e-e571-4bdd-aac9-718f0ffe2266
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=720d719e-e571-4bdd-aac9-718f0ffe2266 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda14)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set 8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda14)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set 8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda15)" {
	insmod ext2
	set root='(hd0,15)'
	search --no-floppy --fs-uuid --set 22eefad4-870e-4191-87c9-57f4e756411d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=22eefad4-870e-4191-87c9-57f4e756411d ro splash quiet quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda15)" {
	insmod ext2
	set root='(hd0,15)'
	search --no-floppy --fs-uuid --set 22eefad4-870e-4191-87c9-57f4e756411d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=22eefad4-870e-4191-87c9-57f4e756411d ro single splash quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda16)" {
	insmod ext2
	set root='(hd0,16)'
	search --no-floppy --fs-uuid --set 7a90aa0c-2377-48e4-97ad-20283c962abc
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=7a90aa0c-2377-48e4-97ad-20283c962abc ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda16)" {
	insmod ext2
	set root='(hd0,16)'
	search --no-floppy --fs-uuid --set 7a90aa0c-2377-48e4-97ad-20283c962abc
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=7a90aa0c-2377-48e4-97ad-20283c962abc ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda17)" {
	insmod ext2
	set root='(hd0,17)'
	search --no-floppy --fs-uuid --set d70bbade-c57d-4c81-84e1-7674021673d6
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d70bbade-c57d-4c81-84e1-7674021673d6 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda17)" {
	insmod ext2
	set root='(hd0,17)'
	search --no-floppy --fs-uuid --set d70bbade-c57d-4c81-84e1-7674021673d6
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d70bbade-c57d-4c81-84e1-7674021673d6 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda18)" {
	insmod ext2
	set root='(hd0,18)'
	search --no-floppy --fs-uuid --set ff93a40e-f9a6-4864-b3f2-0f357263f689
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff93a40e-f9a6-4864-b3f2-0f357263f689 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda18)" {
	insmod ext2
	set root='(hd0,18)'
	search --no-floppy --fs-uuid --set ff93a40e-f9a6-4864-b3f2-0f357263f689
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff93a40e-f9a6-4864-b3f2-0f357263f689 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 1332b9d0-cf18-4299-9094-12acbdac91ad
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 1332b9d0-cf18-4299-9094-12acbdac91ad
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=d252929b-949d-432e-a18c-18f9ae770d28 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw                0       0
#/dev/sda5    /mnt/sda5 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda5       ext3    defaults          0       2
#/dev/sda6    /mnt/sda6 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda6       ext3    defaults          0       2     
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda8       ext3    defaults          0       2

=================== sda3: Location of files loaded by Grub: ===================


  86.8GB: boot/grub/core.img
  86.9GB: boot/grub/grub.cfg
  86.2GB: boot/initrd.img-2.6.32-25-generic
  86.3GB: boot/initrd.img-2.6.32-26-generic
  86.3GB: boot/initrd.img-2.6.32-27-generic
  86.4GB: boot/initrd.img-2.6.32-28-generic
  86.4GB: boot/initrd.img-2.6.32-29-generic
  86.3GB: boot/vmlinuz-2.6.32-25-generic
  86.3GB: boot/vmlinuz-2.6.32-26-generic
  86.3GB: boot/vmlinuz-2.6.32-27-generic
  86.3GB: boot/vmlinuz-2.6.32-28-generic
  86.4GB: boot/vmlinuz-2.6.32-29-generic
  86.4GB: initrd.img
  86.4GB: initrd.img.old
  86.4GB: vmlinuz
  86.3GB: vmlinuz.old

========================== sda12/boot/grub/menu.lst: ==========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,11)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro quiet splash
initrd		/boot/initrd.img-2.6.24-28-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro single
initrd		/boot/initrd.img-2.6.24-28-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,11)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-23-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-24-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-25-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-26-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro single 
initrd		/boot/initrd.img-2.6.31-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-25-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-27-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-27-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-28-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-28-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-29-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-29-generic
savedefault
boot


=============================== sda12/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda12
UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda12: Location of files loaded by Grub: ===================


 259.8GB: boot/grub/menu.lst
 259.8GB: boot/grub/stage2
 259.7GB: boot/initrd.img-2.6.24-26-generic
 259.8GB: boot/initrd.img-2.6.24-28-generic
 259.7GB: boot/initrd.img-2.6.24-28-generic.bak
 259.8GB: boot/vmlinuz-2.6.24-26-generic
 259.8GB: boot/vmlinuz-2.6.24-28-generic
 259.8GB: initrd.img
 259.7GB: initrd.img.old
 259.8GB: vmlinuz
 259.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4


Unknown BootLoader  on sda14

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 a9 6f 19 13  |.............o..|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 24 12  |...<.u........$.|
000001c0  0f 09 00 be bd 7d 31 c0  cd 13 46 8a 0c 80 f9 00  |.....}1...F.....|
000001d0  75 0f be da 7d e8 da ff  eb a4 46 6c 6f 70 70 79  |u...}.....Floppy|
000001e0  00 bb 00 70 8e c3 31 db  b8 01 02 b5 00 b6 00 cd  |...p..1.........|
000001f0  13 72 d3 b6 01 b5 4f e9  ff fe 00 00 00 00 55 aa  |.r....O.......U.|
00000200

Unknown BootLoader  on sda16


Unknown BootLoader  on sda17


Unknown BootLoader  on sda18



=============================== StdErr Messages: ===============================

hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda16: No such file or directory
hexdump: /dev/sda16: No such file or directory
hexdump: /dev/sda17: No such file or directory
hexdump: /dev/sda17: No such file or directory
hexdump: /dev/sda18: No such file or directory
hexdump: /dev/sda18: No such file or directory
```

And the new script results are here:

```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy  is installed in the MBR of /dev/sda and looks on boot drive 
    #-128 in partition #12 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #14 for /boot/grub.
 => Syslinux MBR is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97 - 1.98
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 12587135 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97 - 1.98
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 169853109 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda11: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda12: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda13: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda14: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 1.99
    Boot sector info:  Grub 2 is installed in the boot sector of sda14 and 
                       looks at sector 320434089 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda15: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda16: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''

sda17: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda18: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type 'ext4'

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a6391

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    84,646,484    84,646,422  83 Linux
/dev/sda2          84,646,485   168,313,004    83,666,520  83 Linux
/dev/sda3         168,313,005   252,349,019    84,036,015  83 Linux
/dev/sda4         252,349,020   976,768,064   724,419,045   5 Extended
/dev/sda5         631,209,978   738,861,479   107,651,502  83 Linux
/dev/sda6         738,861,543   843,637,409   104,775,867  83 Linux
/dev/sda7         843,637,473   950,919,479   107,282,007  83 Linux
/dev/sda8         950,919,543   971,852,174    20,932,632  83 Linux
/dev/sda9         971,852,238   976,768,064     4,915,827  82 Linux swap / Solaris
/dev/sda10        588,637,728   631,209,914    42,572,187  83 Linux
/dev/sda11        546,161,868   588,637,664    42,475,797  83 Linux
/dev/sda12        503,878,788   546,161,804    42,283,017  83 Linux
/dev/sda13        460,904,913   503,878,724    42,973,812  83 Linux
/dev/sda14        295,001,721   336,144,059    41,142,339  83 Linux
/dev/sda15        336,144,123   377,318,654    41,174,532  83 Linux
/dev/sda16        377,318,718   419,119,784    41,801,067  83 Linux
/dev/sda17        419,119,848   460,904,849    41,785,002  83 Linux
/dev/sda18        252,350,464   295,000,063    42,649,600  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002c729

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    17,816,084    17,816,022  83 Linux
/dev/sdb2          17,816,085   156,296,384   138,480,300   5 Extended
/dev/sdb5          17,816,148   151,316,234   133,500,087  83 Linux
/dev/sdb6         151,316,298   156,296,384     4,980,087  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000563a8

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048     4,948,019     4,945,972   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        b7a0df33-53e4-4f0d-856b-0da92ff0d743   ext3       Maverick
/dev/sda10       6114df72-5fec-467a-b6cf-bfb49b76def1   ext4       Mint Julia
/dev/sda11       ed0bdce8-0af8-4cce-9933-cbac8389fe4d   ext4       Squeeze
/dev/sda12       96bef601-3776-4e41-bf5a-ca81d3e5058d   ext3       Hardy
/dev/sda13       720d719e-e571-4bdd-aac9-718f0ffe2266   ext4       Peppermint
/dev/sda14       8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079   ext4       MM to NN A2
/dev/sda15       22eefad4-870e-4191-87c9-57f4e756411d   ext4       LMDE
/dev/sda2        1332b9d0-cf18-4299-9094-12acbdac91ad   ext3       Karmic
/dev/sda3        d252929b-949d-432e-a18c-18f9ae770d28   ext3       Lucid
/dev/sda5        594c3d40-2791-4c0a-8644-d9812545da2d   ext3       Backups
/dev/sda6        8a3f6c83-cb52-4caf-96b8-5faf2c830453   ext3       Pictures
/dev/sda7        05289ee4-d681-4806-b6fd-aefd784f9323   ext3       Downloads
/dev/sda8        571cfad8-68c7-4703-883e-c0baa2a381d4   ext3       Documents
/dev/sda9        80627269-1ccd-4774-b4ea-a5ef8824ffaa   swap       
/dev/sdb1        04d890c5-9f08-4cfe-ac93-c31dc8fe7e07   ext4       
/dev/sdb5        b9aab6d9-b9a9-44c6-abc5-63e2edcfc84d   ext4       
/dev/sdb6        ae8fa315-50cc-4dc8-8edd-d3b9c28ebb7d   swap       
/dev/sdc1        0E23-8903                              vfat       DATA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda12       /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=60
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-26-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	echo	'Loading Linux 2.6.35-26-generic ...'
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set 8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set 8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda16)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set 7a90aa0c-2377-48e4-97ad-20283c962abc
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=7a90aa0c-2377-48e4-97ad-20283c962abc ro vga=792 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda16)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set 7a90aa0c-2377-48e4-97ad-20283c962abc
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=7a90aa0c-2377-48e4-97ad-20283c962abc ro single vga=792
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda18)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos18)'
	search --no-floppy --fs-uuid --set ff93a40e-f9a6-4864-b3f2-0f357263f689
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff93a40e-f9a6-4864-b3f2-0f357263f689 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda18)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos18)'
	search --no-floppy --fs-uuid --set ff93a40e-f9a6-4864-b3f2-0f357263f689
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff93a40e-f9a6-4864-b3f2-0f357263f689 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sda3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=d252929b-949d-432e-a18c-18f9ae770d28 ro quiet splash
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sda3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=d252929b-949d-432e-a18c-18f9ae770d28 ro single
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda10) (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 6114df72-5fec-467a-b6cf-bfb49b76def1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6114df72-5fec-467a-b6cf-bfb49b76def1 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda10) -- recovery mode (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 6114df72-5fec-467a-b6cf-bfb49b76def1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6114df72-5fec-467a-b6cf-bfb49b76def1 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set ed0bdce8-0af8-4cce-9933-cbac8389fe4d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=ed0bdce8-0af8-4cce-9933-cbac8389fe4d ro quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set ed0bdce8-0af8-4cce-9933-cbac8389fe4d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=ed0bdce8-0af8-4cce-9933-cbac8389fe4d ro single
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Lubuntu 10.10, kernel 2.6.35-24-generic (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 9b5de705-ccb3-4cb4-b692-75b0ebfcb276
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b5de705-ccb3-4cb4-b692-75b0ebfcb276 ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Lubuntu 10.10, kernel 2.6.35-24-generic (recovery mode) (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 9b5de705-ccb3-4cb4-b692-75b0ebfcb276
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b5de705-ccb3-4cb4-b692-75b0ebfcb276 ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Peppermint, 2.6.32-24-generic (/dev/sda13) (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set 720d719e-e571-4bdd-aac9-718f0ffe2266
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=720d719e-e571-4bdd-aac9-718f0ffe2266 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Peppermint, 2.6.32-24-generic (/dev/sda13) -- recovery mode (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set 720d719e-e571-4bdd-aac9-718f0ffe2266
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=720d719e-e571-4bdd-aac9-718f0ffe2266 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda15)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos15)'
	search --no-floppy --fs-uuid --set 22eefad4-870e-4191-87c9-57f4e756411d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=22eefad4-870e-4191-87c9-57f4e756411d ro splash quiet quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda15)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos15)'
	search --no-floppy --fs-uuid --set 22eefad4-870e-4191-87c9-57f4e756411d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=22eefad4-870e-4191-87c9-57f4e756411d ro single splash quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda17)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos17)'
	search --no-floppy --fs-uuid --set d70bbade-c57d-4c81-84e1-7674021673d6
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d70bbade-c57d-4c81-84e1-7674021673d6 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda17)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos17)'
	search --no-floppy --fs-uuid --set d70bbade-c57d-4c81-84e1-7674021673d6
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d70bbade-c57d-4c81-84e1-7674021673d6 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 1332b9d0-cf18-4299-9094-12acbdac91ad
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 1332b9d0-cf18-4299-9094-12acbdac91ad
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
# swap is on /dev/sda9
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw                0       0
#/dev/sda5    /mnt/sda5 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda5       ext3    defaults          0       2
#/dev/sda6    /mnt/sda6 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda6       ext3    defaults          0       2     
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda8       ext3    defaults          0       2
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img
            ?? = ??             boot/grub/grub.cfg
            ?? = ??             boot/initrd.img-2.6.35-22-generic
            ?? = ??             boot/initrd.img-2.6.35-23-generic
            ?? = ??             boot/initrd.img-2.6.35-24-generic
            ?? = ??             boot/initrd.img-2.6.35-25-generic
            ?? = ??             boot/initrd.img-2.6.35-26-generic
            ?? = ??             boot/vmlinuz-2.6.35-22-generic
            ?? = ??             boot/vmlinuz-2.6.35-23-generic
            ?? = ??             boot/vmlinuz-2.6.35-24-generic
            ?? = ??             boot/vmlinuz-2.6.35-25-generic
            ?? = ??             boot/vmlinuz-2.6.35-26-generic
            ?? = ??             initrd.img
            ?? = ??             initrd.img.old
            ?? = ??             vmlinuz
            ?? = ??             vmlinuz.old

=========================== sda2/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1332b9d0-cf18-4299-9094-12acbdac91ad

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-22-generic
uuid		1332b9d0-cf18-4299-9094-12acbdac91ad
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid		1332b9d0-cf18-4299-9094-12acbdac91ad
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=1332b9d0-cf18-4299-9094-12acbdac91ad /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw                0       0
#/dev/sda5    /mnt/sda5 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda5       ext3    defaults          0       2
#/dev/sda6    /mnt/sda6 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda6       ext3    defaults          0       2     
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda8       ext3    defaults          0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/menu.lst
            ?? = ??             boot/initrd.img-2.6.31-21-generic
            ?? = ??             boot/initrd.img-2.6.31-22-generic
            ?? = ??             boot/vmlinuz-2.6.31-21-generic
            ?? = ??             boot/vmlinuz-2.6.31-22-generic
            ?? = ??             initrd.img.old
            ?? = ??             vmlinuz.old

=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=40
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-29-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=d252929b-949d-432e-a18c-18f9ae770d28 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=d252929b-949d-432e-a18c-18f9ae770d28 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda10) (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 6114df72-5fec-467a-b6cf-bfb49b76def1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6114df72-5fec-467a-b6cf-bfb49b76def1 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda10) -- recovery mode (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 6114df72-5fec-467a-b6cf-bfb49b76def1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6114df72-5fec-467a-b6cf-bfb49b76def1 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda11)" {
	insmod ext2
	set root='(hd0,11)'
	search --no-floppy --fs-uuid --set ed0bdce8-0af8-4cce-9933-cbac8389fe4d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=ed0bdce8-0af8-4cce-9933-cbac8389fe4d ro quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda11)" {
	insmod ext2
	set root='(hd0,11)'
	search --no-floppy --fs-uuid --set ed0bdce8-0af8-4cce-9933-cbac8389fe4d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=ed0bdce8-0af8-4cce-9933-cbac8389fe4d ro single
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Lubuntu 10.10, kernel 2.6.35-24-generic (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set 9b5de705-ccb3-4cb4-b692-75b0ebfcb276
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b5de705-ccb3-4cb4-b692-75b0ebfcb276 ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Lubuntu 10.10, kernel 2.6.35-24-generic (recovery mode) (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set 9b5de705-ccb3-4cb4-b692-75b0ebfcb276
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b5de705-ccb3-4cb4-b692-75b0ebfcb276 ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Peppermint, 2.6.32-24-generic (/dev/sda13) (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,13)'
	search --no-floppy --fs-uuid --set 720d719e-e571-4bdd-aac9-718f0ffe2266
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=720d719e-e571-4bdd-aac9-718f0ffe2266 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Peppermint, 2.6.32-24-generic (/dev/sda13) -- recovery mode (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,13)'
	search --no-floppy --fs-uuid --set 720d719e-e571-4bdd-aac9-718f0ffe2266
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=720d719e-e571-4bdd-aac9-718f0ffe2266 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda14)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set 8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda14)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set 8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda15)" {
	insmod ext2
	set root='(hd0,15)'
	search --no-floppy --fs-uuid --set 22eefad4-870e-4191-87c9-57f4e756411d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=22eefad4-870e-4191-87c9-57f4e756411d ro splash quiet quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda15)" {
	insmod ext2
	set root='(hd0,15)'
	search --no-floppy --fs-uuid --set 22eefad4-870e-4191-87c9-57f4e756411d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=22eefad4-870e-4191-87c9-57f4e756411d ro single splash quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda16)" {
	insmod ext2
	set root='(hd0,16)'
	search --no-floppy --fs-uuid --set 7a90aa0c-2377-48e4-97ad-20283c962abc
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=7a90aa0c-2377-48e4-97ad-20283c962abc ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda16)" {
	insmod ext2
	set root='(hd0,16)'
	search --no-floppy --fs-uuid --set 7a90aa0c-2377-48e4-97ad-20283c962abc
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=7a90aa0c-2377-48e4-97ad-20283c962abc ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda17)" {
	insmod ext2
	set root='(hd0,17)'
	search --no-floppy --fs-uuid --set d70bbade-c57d-4c81-84e1-7674021673d6
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d70bbade-c57d-4c81-84e1-7674021673d6 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda17)" {
	insmod ext2
	set root='(hd0,17)'
	search --no-floppy --fs-uuid --set d70bbade-c57d-4c81-84e1-7674021673d6
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d70bbade-c57d-4c81-84e1-7674021673d6 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda18)" {
	insmod ext2
	set root='(hd0,18)'
	search --no-floppy --fs-uuid --set ff93a40e-f9a6-4864-b3f2-0f357263f689
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff93a40e-f9a6-4864-b3f2-0f357263f689 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda18)" {
	insmod ext2
	set root='(hd0,18)'
	search --no-floppy --fs-uuid --set ff93a40e-f9a6-4864-b3f2-0f357263f689
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff93a40e-f9a6-4864-b3f2-0f357263f689 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 1332b9d0-cf18-4299-9094-12acbdac91ad
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 1332b9d0-cf18-4299-9094-12acbdac91ad
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=d252929b-949d-432e-a18c-18f9ae770d28 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw                0       0
#/dev/sda5    /mnt/sda5 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda5       ext3    defaults          0       2
#/dev/sda6    /mnt/sda6 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda6       ext3    defaults          0       2     
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda8       ext3    defaults          0       2
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img
            ?? = ??             boot/grub/grub.cfg
            ?? = ??             boot/initrd.img-2.6.32-25-generic
            ?? = ??             boot/initrd.img-2.6.32-26-generic
            ?? = ??             boot/initrd.img-2.6.32-27-generic
            ?? = ??             boot/initrd.img-2.6.32-28-generic
            ?? = ??             boot/initrd.img-2.6.32-29-generic
            ?? = ??             boot/vmlinuz-2.6.32-25-generic
            ?? = ??             boot/vmlinuz-2.6.32-26-generic
            ?? = ??             boot/vmlinuz-2.6.32-27-generic
            ?? = ??             boot/vmlinuz-2.6.32-28-generic
            ?? = ??             boot/vmlinuz-2.6.32-29-generic
            ?? = ??             initrd.img
            ?? = ??             initrd.img.old
            ?? = ??             vmlinuz
            ?? = ??             vmlinuz.old

========================== sda12/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,11)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro quiet splash
initrd		/boot/initrd.img-2.6.24-28-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro single
initrd		/boot/initrd.img-2.6.24-28-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,11)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-23-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-24-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-25-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-26-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro single 
initrd		/boot/initrd.img-2.6.31-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-25-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-27-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-27-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-28-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-28-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-29-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-29-generic
savedefault
boot

--------------------------------------------------------------------------------

=============================== sda12/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda12
UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda12: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/menu.lst
            ?? = ??             boot/grub/stage2
            ?? = ??             boot/initrd.img-2.6.24-26-generic
            ?? = ??             boot/initrd.img-2.6.24-28-generic
            ?? = ??             boot/initrd.img-2.6.24-28-generic.bak
            ?? = ??             boot/vmlinuz-2.6.24-26-generic
            ?? = ??             boot/vmlinuz-2.6.24-28-generic
            ?? = ??             initrd.img
            ?? = ??             initrd.img.old
            ?? = ??             vmlinuz
            ?? = ??             vmlinuz.old

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4


Unknown BootLoader on sda16


Unknown BootLoader on sda17


Unknown BootLoader on sda18



=============================== StdErr Messages: ===============================

hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda16: No such file or directory
hexdump: /dev/sda16: No such file or directory
hexdump: /dev/sda17: No such file or directory
hexdump: /dev/sda17: No such file or directory
hexdump: /dev/sda18: No such file or directory
hexdump: /dev/sda18: No such file or directory
```

ATM I'm too tired to make much sense of anything else so I'll get back to this when I can.

---

### Post by cariboo on 2011-02-12
Come back when you're ready, kansasnoob, we don't want your head to explode. :)

---

### Post by drs305 on 2011-02-12
Ran both in Natty. gawk had to be installed and was the only thing that generated a message when running the new script.

If in the final product the user has to install something not on a default installation I think it would be good for the script to check if gawk is installed and if it isn't, install it automatically. Of course there should be reference to this in the instructions so the user knows something may be installed.

Original 055:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for :em.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda14: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda15: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  CentOS release 5.5 (Final) 
                       Kernel on an
    Boot files/dirs:   /etc/fstab

sdb8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    31,471,334    31,471,272  83 Linux
/dev/sda2          31,471,335    62,235,809    30,764,475  83 Linux
/dev/sda3          62,235,810   167,108,129   104,872,320  83 Linux
/dev/sda4         167,108,254   625,141,759   458,033,506   f W95 Ext d (LBA)
/dev/sda5         167,108,256   177,759,224    10,650,969  83 Linux
/dev/sda6         177,759,288   186,032,699     8,273,412  82 Linux swap / Solaris
/dev/sda7         186,032,763   217,343,384    31,310,622  83 Linux
/dev/sda8         217,343,448   238,324,274    20,980,827  83 Linux
/dev/sda9         238,324,338   260,510,039    22,185,702  83 Linux
/dev/sda10        260,510,103   281,651,579    21,141,477  83 Linux
/dev/sda11        281,655,296   303,724,543    22,069,248  83 Linux
/dev/sda12        303,726,592   319,356,927    15,630,336  83 Linux
/dev/sda13        319,358,976   341,465,087    22,106,112  83 Linux
/dev/sda14        341,467,136   346,464,255     4,997,120  83 Linux
/dev/sda15        346,466,304   625,141,759   278,675,456   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   205,037,594   205,037,532  83 Linux
/dev/sdb2         205,037,595 1,250,258,624 1,045,221,030   5 Extended
/dev/sdb5         205,037,658   857,774,609   652,736,952  83 Linux
/dev/sdb6         857,774,673 1,229,064,191   371,289,519  83 Linux
/dev/sdb7    *  1,229,066,240 1,248,010,239    18,944,000  83 Linux
/dev/sdb8       1,248,012,288 1,250,256,895     2,244,608  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       727222f8-f24a-4b1e-b1bd-023c7be6e78b   ext4       mint                          
/dev/sda11       b34b528a-26b2-4577-8d16-08b11df49182   ext4       mav32                         
/dev/sda12       7266aac5-e357-40a8-8813-3fb2906add98   ext4       mavmain                       
/dev/sda13       c9101109-b746-464e-b9ec-5c62d9958c8d   ext4       nattymain                     
/dev/sda14       53d33f36-01b4-4f50-8f52-9abecf8a19ff   ext4       nattyhome                     
/dev/sda15       0BB66F87210FE0E6                       ntfs                                     
/dev/sda1        c5163c70-4f77-4034-a218-5dae03b07eed   ext4       lucid                         
/dev/sda2        0e074399-7e68-4483-87ee-a63d92f9073d   ext4                                     
/dev/sda3        57b87dbc-07ce-45d6-bbbf-301d8315e3f7   ext4       av                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        fd116a38-5d14-404e-b642-2917ff3011d2   ext4       lucidhome                     
/dev/sda6        2b7d27d5-37eb-4ee4-b5ea-71bec80838ec   swap                                     
/dev/sda7        8144779b-ad38-4c1c-aa45-35065ad289e5   ext4       data                          
/dev/sda8        1c4adc10-a208-4373-b842-9851a8421da9   ext4       maverick                      
/dev/sda9        56efcec8-787a-4d42-a01b-a48d2fe2f805   ext4       lucid32                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2c8a15c5-ee8f-4092-8dec-b97ab8d0e6ea   ext4       sdb1.97                       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        5f501d9e-b138-4989-b134-1f3330f74ba5   ext4       vm                            
/dev/sdb6        5a58bb38-62bb-495d-92db-6f80aa63f01a   ext4       bi                            
/dev/sdb7        88c9acad-ee8d-48a7-9102-02d84bb65e35   ext3       centoss                       
/dev/sdb8        31f0f246-dbe3-45f3-93d5-dbc0ac382862   ext3       centosboot                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda13       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb6        /mnt/bi                  ext4       (rw,noexec,nosuid,nodev,commit=0)
/dev/sda14       /home                    ext4       (rw,commit=0)
/dev/sda7        /mnt/data                ext4       (rw,nosuid,nodev,commit=0)
/dev/sdb5        /mnt/vm                  ext4       (rw,nosuid,nodev,commit=0)
/dev/sda3        /mnt/av                  ext4       (rw,noexec,nosuid,nodev,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=800x600
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 8144779b-ad38-4c1c-aa45-35065ad289e5
insmod png
if background_image /docs2/computer/backgrounds/grub.backgrounds/bg_earth.800x600.scaled.sda1.png ; then
  set color_normal=light-gray/black
  set color_highlight=yellow/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'blah blah' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10) (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda14)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set c0a41613-0d26-4583-88cc-f7171768be40
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda14)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set c0a41613-0d26-4583-88cc-f7171768be40
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-11-generic (on /dev/sda14)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set c0a41613-0d26-4583-88cc-f7171768be40
	linux /boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-11-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-11-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-11-generic
}
menuentry "Maverick 8 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # ipv6.disable=1
	initrd /initrd.img
}
menuentry "Natty 14 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro vt.handoff=7 quiet splash
	initrd /initrd.img
}
menuentry "Lucid 1 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro
	initrd /initrd.img
}
menuentry "Maverick 8 on Natty (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # vt.handoff=7
	initrd /initrd.img
}
menuentry "Natty 14 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro # vt.handoff=7 quiet splash
	initrd /initrd.img
}
menuentry "Mint 10 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b
	initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sda9 ro quiet splash
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda9 ro quiet splash
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 31f0f246-dbe3-45f3-93d5-dbc0ac382862
	linux /vmlinuz-2.6.18-194.el5 root=/dev/sdb7
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc2)" {
	insmod ntfs
	set root='(/dev/sdc,2)'
	search --no-floppy --fs-uuid --set d2e80495e80479cd
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic-pae (on /dev/sdc5)" {
	insmod ext2
	set root='(/dev/sdc,5)'
	search --no-floppy --fs-uuid --set c15f174d-0ce6-4d3b-87a8-6defdc96dbfd
	linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=c15f174d-0ce6-4d3b-87a8-6defdc96dbfd ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode) (on /dev/sdc5)" {
	insmod ext2
	set root='(/dev/sdc,5)'
	search --no-floppy --fs-uuid --set c15f174d-0ce6-4d3b-87a8-6defdc96dbfd
	linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=c15f174d-0ce6-4d3b-87a8-6defdc96dbfd ro single
	initrd /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/39_custom ###
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


menuentry " "                       {
insmod ext2
}
menuentry "39_custom Entries:"      {
insmod ext2
}
menuentry " "                       {
insmod ext2
}

menuentry "Maverick (on sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash acpi_enforce_resources=lax
	initrd /initrd.img
}


menuentry 'Lucid (on sda1)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux	/vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro acpi_enforce_resources=lax  quiet splash
	initrd	/initrd.img
}


menuentry "Lucid 32 (hd0,10)"                               {
        recordfail
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=56efcec8-787a-4d42-a01b-a48d2fe2f805 ro   quiet splash acpi_enforce_resources=lax
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}


menuentry "ISO Lucid in home os_backup (hd0,5)"                          {
loopback loop (hd0,5)/drs64/os_backup/ubuntu-10.04.1-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/drs64/os_backup/ubuntu-10.04.1-desktop-i386.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}


menuentry "ISO SystemRescue (hd1,5 - vm)"                   {
loopback loop (hd1,5)/systemrescuecd-x86-1.5.8.iso
linux (loop)/isolinux/rescue64 setkmap=us isoloop=/systemrescuecd-x86-1.5.8.iso
initrd (loop)/isolinux/initram.igz
}


menuentry "ISO Parted Magic  (hd1,6)"                        {
set root=(hd1,6)
loopback loop (hd1,6)/iso/pmagic-5.2.iso
linux (loop)/pmagic/bzImage iso_filename=/iso/pmagic-5.2.iso boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt 
initrd (loop)/pmagic/initramfs
}


menuentry "ISO Lucid.1 64 (hd1,6)"                          {
loopback loop (hd1,6)/iso/ubuntu-10.04.1-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-10.04.1-desktop-amd64.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}


menuentry "ISO Karmic 64 (hd1,6)"                           {
loopback loop (hd1,6)/iso/ubuntu-9.10-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-9.10-desktop-amd64.iso noprompt quiet splash
initrd (loop)/casper/initrd.lz
}


menuentry "ISO Kubuntu Karmic 64 (hd1,6)"                   {
 loopback loop (hd1,6)/iso/kubuntu-9.10-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/kubuntu-9.10-desktop-amd64.iso noprompt quiet splash
 initrd (loop)/casper/initrd.lz
}


menuentry "Gparted live (hd1,6)"                            {
loopback loop (hd1,6)/iso/gparted-live-0.6.1-2.iso
linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia findiso=/iso/gparted-live-0.6.1-2.iso  toram=filesystem.squashfs 
initrd (loop)/live/initrd.img
}



### END /etc/grub.d/39_custom ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# / was on /dev/sdb1 during installation
UUID=c5163c70-4f77-4034-a218-5dae03b07eed /               ext4    errors=remount-ro 0       1


# /home was on /dev/sdb5 during installation
UUID=fd116a38-5d14-404e-b642-2917ff3011d2 /home           ext4    defaults,rw        0       2

# swap was on /dev/sdb6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0

#UUID=ba83d184-705e-4115-9d42-0823c698a757 /mnt/intrepid ext3 user,noauto,rw,sync 0 0
LABEL=av /mnt/av ext4 users,defaults 0 2
LABEL=bi /mnt/bi ext4 defaults,auto,users 0 2
LABEL=data /mnt/data ext4 defaults,users,exec 0 2
LABEL=vm /mnt/vm ext4 defaults,users 0 2
LABEL=lucid32 /mnt/lucid32 ext4 defaults,users 0 2
LABEL=maverick /mnt/maverick ext4 defaults,users,exec 0 2


# LABEL=images /mnt/images ext3 defaults,auto,users 0 2
#LABEL=srcd /mnt/srcd ext3 defaults,users,exec 0 2
#LABEL=data2 /mnt/data2 ext4 defaults,users 0 2
#LABEL=data.sync /mnt/data.sync ext4 defaults,users 0 2
#LABEL=lucid_old /mnt/lucid_old ext4 defaults,users 0 2

#/dev/sda9  /mnt/share  ntfs   utf8,umask=007,uid=1000,gid=1000 0 2


=================== sda1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
  13.2GB: boot/grub/grub.cfg
  14.3GB: boot/initrd.img-2.6.32-27-generic
  14.3GB: boot/vmlinuz-2.6.32-27-generic
  14.3GB: initrd.img
  14.3GB: vmlinuz

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos14)'
search --no-floppy --fs-uuid --set=root c0a41613-0d26-4583-88cc-f7171768be40
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 8144779b-ad38-4c1c-aa45-35065ad289e5
insmod png
background_image -m stretch /docs2/computer/backgrounds/grub.backgrounds/bg_earth.800x600.scaled.sda14.png
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos14)'
search --no-floppy --fs-uuid --set=root c0a41613-0d26-4583-88cc-f7171768be40
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
play 480 440 .75
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 8144779b-ad38-4c1c-aa45-35065ad289e5
insmod png
if background_image /docs2/computer/backgrounds/grub.backgrounds/bg_earth.800x600.scaled.sda14.png; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.37-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos14)'
	search --no-floppy --fs-uuid --set=root c0a41613-0d26-4583-88cc-f7171768be40
	linux	/boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.37-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.37-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos14)'
	search --no-floppy --fs-uuid --set=root c0a41613-0d26-4583-88cc-f7171768be40
	linux	/boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.37-11-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda15 during installation
UUID=0e074399-7e68-4483-87ee-a63d92f9073d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda16 during installation
UUID=53d33f36-01b4-4f50-8f52-9abecf8a19ff /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0

#LABEL=data /mnt/data ext4 defaults,user 0 2

LABEL=av 		/mnt/av 	ext4 	users,defaults 	0 2 
LABEL=bi 		/mnt/bi 	ext4 	defaults,users	0 2 
LABEL=data 		/mnt/data 	ext4 	users,exec 	0 2 
LABEL=vm		/mnt/vm 	ext4 	users,exec 	0 2 
LABEL=lucid 		/mnt/lucid 	ext4    users,exec 	0 2 
LABEL=maverick		/mnt/maverick 	ext4 	users,exec 	0 2 

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
LABEL=av 		/mnt/av 	ext4 	users,defaults 	0 2
LABEL=bi 		/mnt/bi 	ext4 	defaults,users	0 2
LABEL=data 	/mnt/data 	ext4 	users,exec 	0 2
LABEL=vm		/mnt/vm 	ext4 	users,exec 	0 2
LABEL=maverick	/mnt/maverick 	ext4 	users,exec 	0 2

=================== sda2: Location of files loaded by Grub: ===================


  16.2GB: boot/grub/core.img
  22.7GB: boot/grub/grub.cfg
  26.0GB: boot/initrd.img-2.6.37-11-generic
  19.3GB: boot/initrd.img-2.6.37-12-generic
  16.8GB: boot/vmlinuz-2.6.37-11-generic
  17.6GB: boot/vmlinuz-2.6.37-12-generic
  19.3GB: initrd.img
  26.0GB: initrd.img.old
  17.6GB: vmlinuz
  16.8GB: vmlinuz.old

=========================== sda8/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1600x1200
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
play 480 440 .75
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 8144779b-ad38-4c1c-aa45-35065ad289e5
insmod png
if background_image /docs2/computer/backgrounds/grub.backgrounds/bg_earth.800x600.scaled.sda8.png ; then
  set color_normal=light-gray/black
  set color_highlight=yellow/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_custom ###
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

#if [ "x${timeout}" != "x-1" ]; then
#  if keystatus; then
#    if keystatus --shift; then
#      set timeout=-1
#    else
#      set timeout=${GRUB_TIMEOUT}
#    fi
#  else
#    if sleep --interruptible 3 ; then
#      set timeout=0
#    fi
#  fi
#fi

set linux_gfx_mode=keep
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi


menuentry "Maverick 8" {
	recordfail
	savedefault
#	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux	/vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # ipv6.disable=1
	initrd	/initrd.img
}

menuentry "Mav32  16" {
	recordfail
	savedefault
#	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	linux	/vmlinuz root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro # ipv6.disable=1
	initrd	/initrd.img
}


menuentry 'Natty 13' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d 
	linux	/vmlinuz root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro   vt.handoff=7 quiet splash
	initrd	/initrd.img
}

menuentry "Lucid 1" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro
	initrd /initrd.img
}

menuentry "Maverick 8 on Natty" {
	recordfail
	savedefault
#	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux	/vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro  # vt.handoff=7 
	initrd	/initrd.img
}

menuentry "Natty 14" {
	recordfail
	savedefault
#	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos15)'
	search --no-floppy --fs-uuid --set=rootc9101109-b746-464e-b9ec-5c62d9958c8d 
	linux /vmlinuz root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro # vt.handoff=7 quiet splash
	initrd /initrd.img
}



menuentry 'Mint 10'                        {
	savedefault
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /vmlinuz root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b
	initrd /initrd.img
}

menuentry " "                        {
	insmod ext2
}

# Other Menu
menuentry "Other OS's"  {
        configfile (hd0,7)/docs2/computer/grub.drs/OtherOS_custom.cfg
}

menuentry " "                        {
	insmod ext2
}

# ISO Menu
menuentry "ISO Config         sda7" {
        configfile (hd0,7)/docs2/computer/grub.drs/ISO_custom.cfg
}

menuentry " "                        {
	insmod ext2
}

# Change the colors.
menuentry "Change the colors" {
	set menu_color_normal=yellow/black
	set menu_color_highlight=light-gray/black
}
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "blah blah (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Maverick (on sda9) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash acpi_enforce_resources=lax
	initrd /initrd.img
}
menuentry "Lucid (on sda1) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro acpi_enforce_resources=lax quiet splash
	initrd /initrd.img
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10) (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (on /dev/sda11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode) (on /dev/sda11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro single
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set c9101109-b746-464e-b9ec-5c62d9958c8d
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set c9101109-b746-464e-b9ec-5c62d9958c8d
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set c9101109-b746-464e-b9ec-5c62d9958c8d
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set c9101109-b746-464e-b9ec-5c62d9958c8d
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-11-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-11-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sda9 ro quiet splash
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda9 ro quiet splash
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set 31f0f246-dbe3-45f3-93d5-dbc0ac382862
	linux /vmlinuz-2.6.18-194.el5 root=/dev/sdb7
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

### BEGIN /etc/grub.d/ISO_custom.cfg ###

menuentry 'ISO SystemRescue   sdb5-vm'                     {
loopback loop (hd1,5)/systemrescuecd-x86-2.0.0.iso
linux (loop)/isolinux/rescue64 setkmap=us isoloop=/systemrescuecd-x86-2.0.0.iso
initrd (loop)/isolinux/initram.igz
}


menuentry 'ISO Natty        sda6'                        {
loopback loop (hd1,6)/iso/natty-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/natty-desktop-amd64.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}


menuentry 'ISO Maverick 64     sdb6'                        {
loopback loop (hd1,6)/iso/ubuntu-10.10-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-10.10-desktop-amd64.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}


menuentry 'ISO Lucid.1 64     sdb6'                        {
loopback loop (hd1,6)/iso/ubuntu-10.04.1-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-10.04.1-desktop-amd64.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}


menuentry 'ISO Karmic 64      sdb6'                        {
loopback loop (hd1,6)/iso/ubuntu-9.10-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-9.10-desktop-amd64.iso noprompt quiet splash
initrd (loop)/casper/initrd.lz
}


menuentry 'ISO Ku Karmic 64   sdb6'                        {
 loopback loop (hd1,6)/iso/kubuntu-9.10-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/kubuntu-9.10-desktop-amd64.iso noprompt quiet splash
 initrd (loop)/casper/initrd.lz
}


menuentry 'ISO Mint 9         sdb6'                        {
 loopback loop (hd1,6)/iso/linuxmint-9-gnome-cd-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/linuxmint-9-gnome-cd-amd64.iso noprompt quiet splash
 initrd (loop)/casper/initrd.lz
}


menuentry 'Puppy              sdb6'                        {
 loopback loop (hd1,6)/iso/lupu-511.iso
 linux (loop)/vmlinuz  iso_filename=/iso/lupu-511.iso boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt 
initrd (loop)/initrd.gz
}


menuentry 'ISO Lubuntu        sda6'                        {
loopback loop (hd1,6)/iso/lubuntu-10.04.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/lubuntu-10.04.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}


menuentry 'ISO Centos         sda6'                        {
loopback loop (hd1,6)/iso/CentOS-5.5-x86_64-LiveCD.iso
linux (loop)/isolinux/vmlinuz0 isoloop=/iso/CentOS-5.5-x86_64-LiveCD.iso
initrd (loop)/isolinux/initrd0.img
}


menuentry 'ISO Parted Magic   sdb6'                        {
set root=(hd1,6)
loopback loop (hd1,6)/iso/pmagic-5.2.iso
linux (loop)/pmagic/bzImage iso_filename=/iso/pmagic-5.2.iso boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt 
initrd (loop)/pmagic/initramfs
}


menuentry "freebsd 8.0" {
	set root=(hd0,2,a)
	chainloaderer +1
}


menuentry "Windows" {
insmod iso9660
loopback loop (hd1,6)/iso/winxp.iso
chainloader +1
}


menuentry 'ISO grub-rescue-remix      sda6'                        {
loopback loop (hd1,6)/iso/ubuntu-rescue-remix-10-10.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-rescue-remix-10-10.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}

menuentry 'Debian Install      sda6'                        {
loopback loop (hd1,6)/iso/debian-6.0.0-amd64-netinst.iso
linux (loop)/install.amd/vmlinuz boot=/install.amd iso-scan/filename=/iso/debian-6.0.0-amd64-netinst.iso noprompt noeject video=vesa:ywrap,mtrr vga=788
initrd (loop)/install.amd/gtk/initrd.gz
}

### END /etc/grub.d/ISO_custom.cfg ###

=============================== sda8/etc/fstab: ===============================

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=1c4adc10-a208-4373-b842-9851a8421da9 /               ext4    errors=remount-ro 0       1
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0
LABEL=lucid  /mnt/lucid  ext4  defaults,users,exec,noauto  0 2
LABEL=lucidhome  /mnt/lucidhome ext4  defaults,users,exec,noauto 0 2
LABEL=nattymain  /mnt/nattymain  ext4  defaults,users,exec,noauto 0 2
LABEL=nattyhome  /mnt/nattyhome  ext4  defaults,users,exec,noauto 0 2
LABEL=mav32  /mnt/mav32  ext4  defaults,users,exec,noauto  0 2
LABEL=lucid32  /mnt/lucid32  ext4  defaults,users,exec,noauto  0 2
LABEL=av   /mnt/av  ext4  users,defaults   0 2 
LABEL=bi   /mnt/bi  ext4  defaults,users  0 2 
LABEL=data   /mnt/data  ext4  users,exec   0 2 
LABEL=vm  /mnt/vm  ext4  users,exec  0 2

=================== sda8: Location of files loaded by Grub: ===================


 117.8GB: boot/grub/core.img
 112.5GB: boot/grub/grub.cfg
 118.2GB: boot/initrd.img-2.6.32-23-generic
 118.4GB: boot/initrd.img-2.6.35-23-generic
 118.6GB: boot/initrd.img-2.6.35-24-generic
 118.9GB: boot/initrd.img-2.6.35-25-generic
 118.2GB: boot/initrd.img-akk
 118.7GB: boot/initrd.img-initrd.img-2.6.35-22-generic
 118.2GB: boot/initrd.img-initrd.img-2.6.35-23-generic
 118.4GB: boot/vmlinuz-2.6.35-23-generic
 118.4GB: boot/vmlinuz-2.6.35-24-generic
 119.0GB: boot/vmlinuz-2.6.35-25-generic
 118.9GB: initrd.img
 118.6GB: initrd.img.old
 119.0GB: vmlinuz
 118.4GB: vmlinuz.old

=========================== sda9/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sda9 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux	/boot/vmlinuz-2.6.32-26-generic root=/dev/sda9 ro   quiet splash
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-26-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-26-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro single
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro single
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro single
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10) (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.37-8-generic (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set fc46e770-f848-4485-8650-3f291b9dd1e1
	linux /boot/vmlinuz-2.6.37-8-generic root=UUID=fc46e770-f848-4485-8650-3f291b9dd1e1 ro quiet splash
	initrd /boot/initrd.img-2.6.37-8-generic
}
menuentry "Ubuntu, with Linux 2.6.37-8-generic (recovery mode) (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set fc46e770-f848-4485-8650-3f291b9dd1e1
	linux /boot/vmlinuz-2.6.37-8-generic root=UUID=fc46e770-f848-4485-8650-3f291b9dd1e1 ro single
	initrd /boot/initrd.img-2.6.37-8-generic
}
menuentry "Ubuntu, with Linux 2.6.37-6-generic (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set fc46e770-f848-4485-8650-3f291b9dd1e1
	linux /boot/vmlinuz-2.6.37-6-generic root=UUID=fc46e770-f848-4485-8650-3f291b9dd1e1 ro quiet splash
	initrd /boot/initrd.img-2.6.37-6-generic
}
menuentry "Ubuntu, with Linux 2.6.37-6-generic (recovery mode) (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set fc46e770-f848-4485-8650-3f291b9dd1e1
	linux /boot/vmlinuz-2.6.37-6-generic root=UUID=fc46e770-f848-4485-8650-3f291b9dd1e1 ro single
	initrd /boot/initrd.img-2.6.37-6-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set f3ec8e37-1383-4df6-a199-f2cd17283a07
	linux /vmlinuz-2.6.35-23-generic root=UUID=7266aac5-e357-40a8-8813-3fb2906add98 ro quiet splash
	initrd /initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set f3ec8e37-1383-4df6-a199-f2cd17283a07
	linux /vmlinuz-2.6.35-22-generic root=UUID=7266aac5-e357-40a8-8813-3fb2906add98 ro quiet splash
	initrd /initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu 2.6.35-23-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu 2.6.35-22-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "  (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Lucid sda1 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /initrd.img
}
menuentry "Mint sda10 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b
	initrd /initrd.img
}
menuentry "Puppy sda11 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=d91b5fd5-a61a-42d8-9cb0-cec9d871b634 pmedia=atahd
	initrd /initrd.gz
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 31f0f246-dbe3-45f3-93d5-dbc0ac382862
	linux /vmlinuz-2.6.18-194.el5 root=/dev/sdb7
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=56efcec8-787a-4d42-a01b-a48d2fe2f805 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

LABEL=av 		/mnt/av 	ext4 	defaults,auto,users,defaults 	0 2 
LABEL=bi 		/mnt/bi 	ext4 	defaults,auto,defaults,users	0 2 
LABEL=data 		/mnt/data 	ext4 	defaults,auto,users,exec 	0 2 
LABEL=vm		/mnt/vm 	ext4 	defaults,auto,users,exec 	0 2

=================== sda9: Location of files loaded by Grub: ===================


 130.7GB: boot/grub/core.img
 130.9GB: boot/grub/grub.cfg
 131.1GB: boot/initrd.img-2.6.32-25-generic
 131.1GB: boot/initrd.img-2.6.32-25-generic-pae
 131.1GB: boot/initrd.img-2.6.32-26-generic
 131.2GB: boot/initrd.img-2.6.32-26-generic-pae
 131.0GB: boot/vmlinuz-2.6.32-25-generic
 131.0GB: boot/vmlinuz-2.6.32-25-generic-pae
 131.0GB: boot/vmlinuz-2.6.32-26-generic
 131.1GB: boot/vmlinuz-2.6.32-26-generic-pae
 131.2GB: initrd.img
 131.1GB: initrd.img.old
 131.1GB: vmlinuz
 131.0GB: vmlinuz.old

========================== sda10/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,10)'
search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,10)'
search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,10)'
search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntuu, with Linux 2.6.32-25-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro acpi_enforce_resources=lax quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set f3ec8e37-1383-4df6-a199-f2cd17283a07
	linux /vmlinuz-2.6.35-23-generic root=UUID=7266aac5-e357-40a8-8813-3fb2906add98 ro quiet splash
	initrd /initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set f3ec8e37-1383-4df6-a199-f2cd17283a07
	linux /vmlinuz-2.6.35-22-generic root=UUID=7266aac5-e357-40a8-8813-3fb2906add98 ro quiet splash
	initrd /initrd.img-2.6.35-22-generic
}
menuentry "maverick 23-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "maverick 22-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Custom  (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Mint sda10 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b
	initrd /initrd.img
}
menuentry "Puppy sda11 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=d91b5fd5-a61a-42d8-9cb0-cec9d871b634 pmedia=atahd
	initrd /initrd.gz
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=56efcec8-787a-4d42-a01b-a48d2fe2f805 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=56efcec8-787a-4d42-a01b-a48d2fe2f805 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda13 during installation
UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda10: Location of files loaded by Grub: ===================


 133.7GB: boot/grub/core.img
 135.7GB: boot/grub/grub.cfg
 134.9GB: boot/initrd.img-2.6.32-21-generic
 134.8GB: boot/vmlinuz-2.6.32-21-generic
 134.9GB: initrd.img
 134.8GB: vmlinuz

========================== sda11/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos16)'
search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos16)'
search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro single
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Maverick (on sda9) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash acpi_enforce_resources=lax
	initrd /initrd.img
}
menuentry "Lucid (on sda1) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro acpi_enforce_resources=lax quiet splash
	initrd /initrd.img
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10) (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set c0a41613-0d26-4583-88cc-f7171768be40
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set c0a41613-0d26-4583-88cc-f7171768be40
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-11-generic (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set c0a41613-0d26-4583-88cc-f7171768be40
	linux /boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-11-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-11-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-11-generic
}
menuentry "Maverick 8 (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # ipv6.disable=1
	initrd /initrd.img
}
menuentry "Natty 14 (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro vt.handoff=7 quiet splash
	initrd /initrd.img
}
menuentry "Lucid 1 (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro
	initrd /initrd.img
}
menuentry "Maverick 8 on Natty (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # vt.handoff=7
	initrd /initrd.img
}
menuentry "Natty 14 (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro # vt.handoff=7 quiet splash
	initrd /initrd.img
}
menuentry "Mint 10 (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b
	initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sda9 ro quiet splash
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda9 ro quiet splash
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set 31f0f246-dbe3-45f3-93d5-dbc0ac382862
	linux /vmlinuz-2.6.18-194.el5 root=/dev/sdb7
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda16 during installation
UUID=b34b528a-26b2-4577-8d16-08b11df49182 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

UUID=8144779b-ad38-4c1c-aa45-35065ad289e5 /mnt/data ext4 defaults,users,exec 0 2


=================== sda11: Location of files loaded by Grub: ===================


 150.9GB: boot/grub/core.img
 153.8GB: boot/grub/grub.cfg
 153.9GB: boot/initrd.img-2.6.35-25-generic-pae
 150.9GB: boot/vmlinuz-2.6.35-25-generic-pae
 153.9GB: initrd.img
 150.9GB: vmlinuz

========================== sda12/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
}

if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10) (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=56efcec8-787a-4d42-a01b-a48d2fe2f805 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=56efcec8-787a-4d42-a01b-a48d2fe2f805 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda12/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda13 during installation
UUID=7266aac5-e357-40a8-8813-3fb2906add98 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda14 during installation
UUID=f3ec8e37-1383-4df6-a199-f2cd17283a07 /boot           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

UUID=8144779b-ad38-4c1c-aa45-35065ad289e5  /mnt/data ext4 defaults,users,exec 0 2

=================== sda12: Location of files loaded by Grub: ===================


 160.4GB: boot/grub/grub.cfg

========================== sda13/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos13)'
search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos13)'
search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	echo	'Loading Linux 2.6.38-3-generic ...'
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-3-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-2-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	linux	/boot/vmlinuz-2.6.38-2-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-2-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-2-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	echo	'Loading Linux 2.6.38-2-generic ...'
	linux	/boot/vmlinuz-2.6.38-2-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-2-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-1-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	linux	/boot/vmlinuz-2.6.38-1-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-1-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-1-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	echo	'Loading Linux 2.6.38-1-generic ...'
	linux	/boot/vmlinuz-2.6.38-1-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-1-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "blah blah (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Maverick (on sda9) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash acpi_enforce_resources=lax
	initrd /initrd.img
}
menuentry "Lucid (on sda1) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro acpi_enforce_resources=lax quiet splash
	initrd /initrd.img
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos10)'
	search --no-floppy --fs-uuid --set=root 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos11)'
	search --no-floppy --fs-uuid --set=root b34b528a-26b2-4577-8d16-08b11df49182
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos11)'
	search --no-floppy --fs-uuid --set=root b34b528a-26b2-4577-8d16-08b11df49182
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro single
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-11-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-11-generic
}
menuentry "Maverick 8 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # ipv6.disable=1
	initrd /initrd.img
}
menuentry "Mav32 16 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro # ipv6.disable=1
	initrd /initrd.img
}
menuentry "Natty 13 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro vt.handoff=7 quiet splash
	initrd /initrd.img
}
menuentry "Lucid 1 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro
	initrd /initrd.img
}
menuentry "Maverick 8 on Natty (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # vt.handoff=7
	initrd /initrd.img
}
menuentry "Natty 14 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro # vt.handoff=7 quiet splash
	initrd /initrd.img
}
menuentry "Mint 10 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b
	initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Puppy sdb6 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz iso_filename=/iso/lupu-511.iso boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt
	initrd /initrd.gz
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sda9 ro quiet splash
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda9 ro quiet splash
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 31f0f246-dbe3-45f3-93d5-dbc0ac382862
	linux /vmlinuz-2.6.18-194.el5 root=/dev/sdb7
	initrd /initrd-2.6.18-194.el5.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda13/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda14 during installation
UUID=c9101109-b746-464e-b9ec-5c62d9958c8d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda15 during installation
UUID=53d33f36-01b4-4f50-8f52-9abecf8a19ff /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=8144779b-ad38-4c1c-aa45-35065ad289e5 /mnt/data 	ext4 defaults,users,exec 	0 2

LABEL=av 	/mnt/av 	ext4 	users,defaults 	0 2
LABEL=bi 	/mnt/bi 	ext4 	defaults,users	0 2
LABEL=data 	/mnt/data 	ext4 	users,exec 	0 2
LABEL=vm	/mnt/vm 	ext4 	users,exec 	0 2
LABEL=maverick	/mnt/maverick 	ext4 	users,exec,noauto  0 2


=================== sda13: Location of files loaded by Grub: ===================


 170.2GB: boot/grub/core.img
 168.1GB: boot/grub/grub.cfg
 169.8GB: boot/initrd.img-2.6.38-1-generic
 165.1GB: boot/initrd.img-2.6.38-2-generic
 165.2GB: boot/initrd.img-2.6.38-3-generic
 170.3GB: boot/vmlinuz-2.6.38-1-generic
 164.2GB: boot/vmlinuz-2.6.38-2-generic
 165.2GB: boot/vmlinuz-2.6.38-3-generic
 165.2GB: initrd.img
 165.1GB: initrd.img.old
 165.2GB: vmlinuz
 164.2GB: vmlinuz.old

=============================== sdb7/etc/fstab: ===============================

LABEL=centos            /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sda6               swap                    swap    defaults        0 0
/dev/sdb8 		/boot			ext3 	defaults,exec   0 0

============================= sdb8/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd1,6)
#          kernel /boot/vmlinuz-version ro root=/dev/sdb7
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd1,6)/boot/grub/splash.xpm.gz
hiddenmenu
title CentOS-menu.lst (2.6.18-194.el5)
	root (hd1,6)
	kernel /boot/vmlinuz-2.6.18-194.el5 ro root=LABEL=centos rhgb quiet
	initrd /boot/initrd-2.6.18-194.el5.img

=================== sdb8: Location of files loaded by Grub: ===================


 640.0GB: grub/grub.conf
 640.0GB: grub/menu.lst
 639.9GB: grub/stage2
 639.0GB: initrd-2.6.18-194.el5.img
 639.0GB: vmlinuz-2.6.18-194.el5
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  fc 31 c0 8e d0 31 e4 8e  d8 8e c0 be 00 7c bf 00  |.1...1.......|..|
00000010  06 b9 00 01 f3 a5 be ee  07 b0 08 ea 20 06 00 00  |............ ...|
00000020  80 3e b3 07 ff 75 04 88  16 b3 07 80 3c 00 74 04  |.>...u......<.t.|
00000030  08 06 af 07 83 ee 10 d0  e8 73 f0 90 90 90 90 90  |.........s......|
00000040  90 90 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |................|
*
00000070  90 90 90 90 90 90 90 90  90 90 90 90 90 90 be be  |................|
00000080  07 b0 00 b9 04 00 80 3c  00 75 6e fe c0 83 c6 10  |.......<.un.....|
00000090  e2 f4 31 db b4 0e be 9d  07 8a 0e af 07 ac d0 e9  |..1.............|
000000a0  73 02 cd 10 08 c9 75 f5  b0 3a cd 10 31 c0 cd 16  |s.....u..:..1...|
000000b0  3c 00 74 f8 be 8b 07 b9  02 00 e8 ba 00 3c 0d 74  |<.t..........<.t|
000000c0  b4 3c 61 72 06 3c 7a 77  02 2c 20 88 c3 be 9d 07  |.<ar.<zw., .....|
000000d0  8a 0e af 07 ac d0 e9 73  04 38 c3 74 06 08 c9 75  |.......s.8.t...u|
000000e0  f3 eb af b8 0d 0e 31 db  cd 10 8d 84 62 00 3c 07  |......1.....b.<.|
000000f0  75 07 b0 1f a2 af 07 eb  99 31 d2 b9 01 00 3c 04  |u........1....<.|
00000100  74 11 73 f3 30 e4 b1 04  d2 e0 be be 07 01 c6 8a  |t.s.0...........|
00000110  16 b3 07 bf 05 00 56 f6  c2 80 74 31 b4 41 bb aa  |......V...t1.A..|
00000120  55 52 cd 13 5a 5e 56 72  1e 81 fb 55 aa 75 18 f6  |UR..Z^Vr...U.u..|
00000130  c1 01 74 13 8b 44 08 8b  5c 0a be 8d 07 89 44 08  |..t..D..\.....D.|
00000140  89 5c 0a b4 42 eb 0c 8a  74 01 8b 4c 02 b8 01 02  |.\..B...t..L....|
00000150  bb 00 7c 50 c6 06 8f 07  01 cd 13 58 5e 73 05 4f  |..|P.......X^s.O|
00000160  75 b4 eb 93 81 3e fe 7d  55 aa 75 f6 ea 00 7c 00  |u....>.}U.u...|.|
00000170  00 be 83 07 b9 0a 00 50  b4 0e 31 db ac cd 10 e2  |.......P..1.....|
00000180  fb 58 c3 54 65 73 74 44  69 73 6b 0d 0a 10 00 01  |.X.TestDisk.....|
00000190  00 00 7c 00 00 00 00 00  00 00 00 00 00 31 32 33  |..|..........123|
000001a0  34 46 00 00 41 4e 44 54  6d 62 72 00 02 02 02 1f  |4F..ANDTmbr.....|
000001b0  c7 00 00 80 00 00 00 00  00 00 00 00 a5 01 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  fc 31 c0 8e d0 31 e4 8e  d8 8e c0 be 00 7c bf 00  |.1...1.......|..|
00000010  06 b9 00 01 f3 a5 be ee  07 b0 08 ea 20 06 00 00  |............ ...|
00000020  80 3e b3 07 ff 75 04 88  16 b3 07 80 3c 00 74 04  |.>...u......<.t.|
00000030  08 06 af 07 83 ee 10 d0  e8 73 f0 90 90 90 90 90  |.........s......|
00000040  90 90 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |................|
*
00000070  90 90 90 90 90 90 90 90  90 90 90 90 90 90 be be  |................|
00000080  07 b0 00 b9 04 00 80 3c  00 75 6e fe c0 83 c6 10  |.......<.un.....|
00000090  e2 f4 31 db b4 0e be 9d  07 8a 0e af 07 ac d0 e9  |..1.............|
000000a0  73 02 cd 10 08 c9 75 f5  b0 3a cd 10 31 c0 cd 16  |s.....u..:..1...|
000000b0  3c 00 74 f8 be 8b 07 b9  02 00 e8 ba 00 3c 0d 74  |<.t..........<.t|
000000c0  b4 3c 61 72 06 3c 7a 77  02 2c 20 88 c3 be 9d 07  |.<ar.<zw., .....|
000000d0  8a 0e af 07 ac d0 e9 73  04 38 c3 74 06 08 c9 75  |.......s.8.t...u|
000000e0  f3 eb af b8 0d 0e 31 db  cd 10 8d 84 62 00 3c 07  |......1.....b.<.|
000000f0  75 07 b0 1f a2 af 07 eb  99 31 d2 b9 01 00 3c 04  |u........1....<.|
00000100  74 11 73 f3 30 e4 b1 04  d2 e0 be be 07 01 c6 8a  |t.s.0...........|
00000110  16 b3 07 bf 05 00 56 f6  c2 80 74 31 b4 41 bb aa  |......V...t1.A..|
00000120  55 52 cd 13 5a 5e 56 72  1e 81 fb 55 aa 75 18 f6  |UR..Z^Vr...U.u..|
00000130  c1 01 74 13 8b 44 08 8b  5c 0a be 8d 07 89 44 08  |..t..D..\.....D.|
00000140  89 5c 0a b4 42 eb 0c 8a  74 01 8b 4c 02 b8 01 02  |.\..B...t..L....|
00000150  bb 00 7c 50 c6 06 8f 07  01 cd 13 58 5e 73 05 4f  |..|P.......X^s.O|
00000160  75 b4 eb 93 81 3e fe 7d  55 aa 75 f6 ea 00 7c 00  |u....>.}U.u...|.|
00000170  00 be 83 07 b9 0a 00 50  b4 0e 31 db ac cd 10 e2  |.......P..1.....|
00000180  fb 58 c3 54 65 73 74 44  69 73 6b 0d 0a 10 00 01  |.X.TestDisk.....|
00000190  00 00 7c 00 00 00 00 00  00 00 00 00 00 31 32 33  |..|..........123|
000001a0  34 46 00 00 41 4e 44 54  6d 62 72 00 02 02 02 1f  |4F..ANDTmbr.....|
000001b0  c7 00 00 80 00 00 00 00  00 00 00 00 a5 01 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

Version 056 :

```

                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (,msdos13)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda13: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda14: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda15: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  CentOS release 5.5 (Final) 
                       Kernel on an
    Boot files:        /etc/fstab

sdb8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    31,471,334    31,471,272  83 Linux
/dev/sda2          31,471,335    62,235,809    30,764,475  83 Linux
/dev/sda3          62,235,810   167,108,129   104,872,320  83 Linux
/dev/sda4         167,108,254   625,141,759   458,033,506   f W95 Extended (LBA)
/dev/sda5         167,108,256   177,759,224    10,650,969  83 Linux
/dev/sda6         177,759,288   186,032,699     8,273,412  82 Linux swap / Solaris
/dev/sda7         186,032,763   217,343,384    31,310,622  83 Linux
/dev/sda8         217,343,448   238,324,274    20,980,827  83 Linux
/dev/sda9         238,324,338   260,510,039    22,185,702  83 Linux
/dev/sda10        260,510,103   281,651,579    21,141,477  83 Linux
/dev/sda11        281,655,296   303,724,543    22,069,248  83 Linux
/dev/sda12        303,726,592   319,356,927    15,630,336  83 Linux
/dev/sda13        319,358,976   341,465,087    22,106,112  83 Linux
/dev/sda14        341,467,136   346,464,255     4,997,120  83 Linux
/dev/sda15        346,466,304   625,141,759   278,675,456   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   205,037,594   205,037,532  83 Linux
/dev/sdb2         205,037,595 1,250,258,624 1,045,221,030   5 Extended
/dev/sdb5         205,037,658   857,774,609   652,736,952  83 Linux
/dev/sdb6         857,774,673 1,229,064,191   371,289,519  83 Linux
/dev/sdb7    *  1,229,066,240 1,248,010,239    18,944,000  83 Linux
/dev/sdb8       1,248,012,288 1,250,256,895     2,244,608  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        c5163c70-4f77-4034-a218-5dae03b07eed   ext4       lucid
/dev/sda10       727222f8-f24a-4b1e-b1bd-023c7be6e78b   ext4       mint
/dev/sda11       b34b528a-26b2-4577-8d16-08b11df49182   ext4       mav32
/dev/sda12       7266aac5-e357-40a8-8813-3fb2906add98   ext4       mavmain
/dev/sda13       c9101109-b746-464e-b9ec-5c62d9958c8d   ext4       nattymain
/dev/sda14       53d33f36-01b4-4f50-8f52-9abecf8a19ff   ext4       nattyhome
/dev/sda15       0BB66F87210FE0E6                       ntfs       
/dev/sda2        0e074399-7e68-4483-87ee-a63d92f9073d   ext4       
/dev/sda3        57b87dbc-07ce-45d6-bbbf-301d8315e3f7   ext4       av
/dev/sda5        fd116a38-5d14-404e-b642-2917ff3011d2   ext4       lucidhome
/dev/sda6        2b7d27d5-37eb-4ee4-b5ea-71bec80838ec   swap       
/dev/sda7        8144779b-ad38-4c1c-aa45-35065ad289e5   ext4       data
/dev/sda8        1c4adc10-a208-4373-b842-9851a8421da9   ext4       maverick
/dev/sda9        56efcec8-787a-4d42-a01b-a48d2fe2f805   ext4       lucid32
/dev/sdb1        2c8a15c5-ee8f-4092-8dec-b97ab8d0e6ea   ext4       sdb1.97
/dev/sdb5        5f501d9e-b138-4989-b134-1f3330f74ba5   ext4       vm
/dev/sdb6        5a58bb38-62bb-495d-92db-6f80aa63f01a   ext4       bi
/dev/sdb7        88c9acad-ee8d-48a7-9102-02d84bb65e35   ext3       centoss
/dev/sdb8        31f0f246-dbe3-45f3-93d5-dbc0ac382862   ext3       centosboot

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda13       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda14       /home                    ext4       (rw,commit=0)
/dev/sda3        /mnt/av                  ext4       (rw,noexec,nosuid,nodev,commit=0)
/dev/sda7        /mnt/data                ext4       (rw,nosuid,nodev,commit=0)
/dev/sdb5        /mnt/vm                  ext4       (rw,nosuid,nodev,commit=0)
/dev/sdb6        /mnt/bi                  ext4       (rw,noexec,nosuid,nodev,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=800x600
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 8144779b-ad38-4c1c-aa45-35065ad289e5
insmod png
if background_image /docs2/computer/backgrounds/grub.backgrounds/bg_earth.800x600.scaled.sda1.png ; then
  set color_normal=light-gray/black
  set color_highlight=yellow/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'blah blah' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10) (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda14)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set c0a41613-0d26-4583-88cc-f7171768be40
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda14)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set c0a41613-0d26-4583-88cc-f7171768be40
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-11-generic (on /dev/sda14)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set c0a41613-0d26-4583-88cc-f7171768be40
	linux /boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-11-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-11-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-11-generic
}
menuentry "Maverick 8 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # ipv6.disable=1
	initrd /initrd.img
}
menuentry "Natty 14 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro vt.handoff=7 quiet splash
	initrd /initrd.img
}
menuentry "Lucid 1 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro
	initrd /initrd.img
}
menuentry "Maverick 8 on Natty (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # vt.handoff=7
	initrd /initrd.img
}
menuentry "Natty 14 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro # vt.handoff=7 quiet splash
	initrd /initrd.img
}
menuentry "Mint 10 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b
	initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sda9 ro quiet splash
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda9 ro quiet splash
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 31f0f246-dbe3-45f3-93d5-dbc0ac382862
	linux /vmlinuz-2.6.18-194.el5 root=/dev/sdb7
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc2)" {
	insmod ntfs
	set root='(/dev/sdc,2)'
	search --no-floppy --fs-uuid --set d2e80495e80479cd
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic-pae (on /dev/sdc5)" {
	insmod ext2
	set root='(/dev/sdc,5)'
	search --no-floppy --fs-uuid --set c15f174d-0ce6-4d3b-87a8-6defdc96dbfd
	linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=c15f174d-0ce6-4d3b-87a8-6defdc96dbfd ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode) (on /dev/sdc5)" {
	insmod ext2
	set root='(/dev/sdc,5)'
	search --no-floppy --fs-uuid --set c15f174d-0ce6-4d3b-87a8-6defdc96dbfd
	linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=c15f174d-0ce6-4d3b-87a8-6defdc96dbfd ro single
	initrd /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# / was on /dev/sdb1 during installation
UUID=c5163c70-4f77-4034-a218-5dae03b07eed /               ext4    errors=remount-ro 0       1


# /home was on /dev/sdb5 during installation
UUID=fd116a38-5d14-404e-b642-2917ff3011d2 /home           ext4    defaults,rw        0       2

# swap was on /dev/sdb6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0

#UUID=ba83d184-705e-4115-9d42-0823c698a757 /mnt/intrepid ext3 user,noauto,rw,sync 0 0
LABEL=av /mnt/av ext4 users,defaults 0 2
LABEL=bi /mnt/bi ext4 defaults,auto,users 0 2
LABEL=data /mnt/data ext4 defaults,users,exec 0 2
LABEL=vm /mnt/vm ext4 defaults,users 0 2
LABEL=lucid32 /mnt/lucid32 ext4 defaults,users 0 2
LABEL=maverick /mnt/maverick ext4 defaults,users,exec 0 2


# LABEL=images /mnt/images ext3 defaults,auto,users 0 2
#LABEL=srcd /mnt/srcd ext3 defaults,users,exec 0 2
#LABEL=data2 /mnt/data2 ext4 defaults,users 0 2
#LABEL=data.sync /mnt/data.sync ext4 defaults,users 0 2
#LABEL=lucid_old /mnt/lucid_old ext4 defaults,users 0 2

#/dev/sda9  /mnt/share  ntfs   utf8,umask=007,uid=1000,gid=1000 0 2

--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  12.155646801 = 13.052026368   boot/grub/core.img                             1
  12.378959179 = 13.291806208   boot/grub/grub.cfg                             1
  13.386096478 = 14.373211648   boot/initrd.img-2.6.32-27-generic              1
  13.323970318 = 14.306504192   boot/vmlinuz-2.6.32-27-generic                 1
  13.386096478 = 14.373211648   initrd.img                                     1
  13.323970318 = 14.306504192   vmlinuz                                        1

=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos14)'
search --no-floppy --fs-uuid --set=root c0a41613-0d26-4583-88cc-f7171768be40
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 8144779b-ad38-4c1c-aa45-35065ad289e5
insmod png
background_image -m stretch /docs2/computer/backgrounds/grub.backgrounds/bg_earth.800x600.scaled.sda14.png
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos14)'
search --no-floppy --fs-uuid --set=root c0a41613-0d26-4583-88cc-f7171768be40
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
play 480 440 .75
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 8144779b-ad38-4c1c-aa45-35065ad289e5
insmod png
if background_image /docs2/computer/backgrounds/grub.backgrounds/bg_earth.800x600.scaled.sda14.png; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.37-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos14)'
	search --no-floppy --fs-uuid --set=root c0a41613-0d26-4583-88cc-f7171768be40
	linux	/boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.37-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.37-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos14)'
	search --no-floppy --fs-uuid --set=root c0a41613-0d26-4583-88cc-f7171768be40
	linux	/boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.37-11-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda15 during installation
UUID=0e074399-7e68-4483-87ee-a63d92f9073d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda16 during installation
UUID=53d33f36-01b4-4f50-8f52-9abecf8a19ff /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0

#LABEL=data /mnt/data ext4 defaults,user 0 2

LABEL=av 		/mnt/av 	ext4 	users,defaults 	0 2 
LABEL=bi 		/mnt/bi 	ext4 	defaults,users	0 2 
LABEL=data 		/mnt/data 	ext4 	users,exec 	0 2 
LABEL=vm		/mnt/vm 	ext4 	users,exec 	0 2 
LABEL=lucid 		/mnt/lucid 	ext4    users,exec 	0 2 
LABEL=maverick		/mnt/maverick 	ext4 	users,exec 	0 2 

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
LABEL=av 		/mnt/av 	ext4 	users,defaults 	0 2
LABEL=bi 		/mnt/bi 	ext4 	defaults,users	0 2
LABEL=data 	/mnt/data 	ext4 	users,exec 	0 2
LABEL=vm		/mnt/vm 	ext4 	users,exec 	0 2
LABEL=maverick	/mnt/maverick 	ext4 	users,exec 	0 2
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  15.161525249 = 16.279563776   boot/grub/core.img                             1
  21.233577251 = 22.799379968   boot/grub/grub.cfg                             1
  24.276553631 = 26.066750976   boot/initrd.img-2.6.37-11-generic              1
  18.065627575 = 19.397819904   boot/initrd.img-2.6.37-12-generic              1
  15.676768780 = 16.832802304   boot/vmlinuz-2.6.37-11-generic                 1
  16.444457531 = 17.657101824   boot/vmlinuz-2.6.37-12-generic                 1
  18.065627575 = 19.397819904   initrd.img                                     1
  24.276553631 = 26.066750976   initrd.img.old                                 1
  16.444457531 = 17.657101824   vmlinuz                                        1
  15.676768780 = 16.832802304   vmlinuz.old                                    1

=========================== sda8/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1600x1200
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
play 480 440 .75
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 8144779b-ad38-4c1c-aa45-35065ad289e5
insmod png
if background_image /docs2/computer/backgrounds/grub.backgrounds/bg_earth.800x600.scaled.sda8.png ; then
  set color_normal=light-gray/black
  set color_highlight=yellow/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_custom ###
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

#if [ "x${timeout}" != "x-1" ]; then
#  if keystatus; then
#    if keystatus --shift; then
#      set timeout=-1
#    else
#      set timeout=${GRUB_TIMEOUT}
#    fi
#  else
#    if sleep --interruptible 3 ; then
#      set timeout=0
#    fi
#  fi
#fi

set linux_gfx_mode=keep
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi


menuentry "Maverick 8" {
	recordfail
	savedefault
#	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux	/vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # ipv6.disable=1
	initrd	/initrd.img
}

menuentry "Mav32  16" {
	recordfail
	savedefault
#	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	linux	/vmlinuz root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro # ipv6.disable=1
	initrd	/initrd.img
}


menuentry 'Natty 13' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d 
	linux	/vmlinuz root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro   vt.handoff=7 quiet splash
	initrd	/initrd.img
}

menuentry "Lucid 1" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro
	initrd /initrd.img
}

menuentry "Maverick 8 on Natty" {
	recordfail
	savedefault
#	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux	/vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro  # vt.handoff=7 
	initrd	/initrd.img
}

menuentry "Natty 14" {
	recordfail
	savedefault
#	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos15)'
	search --no-floppy --fs-uuid --set=rootc9101109-b746-464e-b9ec-5c62d9958c8d 
	linux /vmlinuz root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro # vt.handoff=7 quiet splash
	initrd /initrd.img
}



menuentry 'Mint 10'                        {
	savedefault
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /vmlinuz root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b
	initrd /initrd.img
}

menuentry " "                        {
	insmod ext2
}

# Other Menu
menuentry "Other OS's"  {
        configfile (hd0,7)/docs2/computer/grub.drs/OtherOS_custom.cfg
}

menuentry " "                        {
	insmod ext2
}

# ISO Menu
menuentry "ISO Config         sda7" {
        configfile (hd0,7)/docs2/computer/grub.drs/ISO_custom.cfg
}

menuentry " "                        {
	insmod ext2
}

# Change the colors.
menuentry "Change the colors" {
	set menu_color_normal=yellow/black
	set menu_color_highlight=light-gray/black
}
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Maverick (on sda9) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash acpi_enforce_resources=lax
	initrd /initrd.img
}
menuentry "Lucid (on sda1) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro acpi_enforce_resources=lax quiet splash
	initrd /initrd.img
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10) (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (on /dev/sda11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode) (on /dev/sda11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro single
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set c9101109-b746-464e-b9ec-5c62d9958c8d
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set c9101109-b746-464e-b9ec-5c62d9958c8d
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set c9101109-b746-464e-b9ec-5c62d9958c8d
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set c9101109-b746-464e-b9ec-5c62d9958c8d
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-11-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-11-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sda9 ro quiet splash
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda9 ro quiet splash
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set 31f0f246-dbe3-45f3-93d5-dbc0ac382862
	linux /vmlinuz-2.6.18-194.el5 root=/dev/sdb7
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

### BEGIN /etc/grub.d/ISO_custom.cfg ###

menuentry 'ISO SystemRescue   sdb5-vm'                     {
loopback loop (hd1,5)/systemrescuecd-x86-2.0.0.iso
linux (loop)/isolinux/rescue64 setkmap=us isoloop=/systemrescuecd-x86-2.0.0.iso
initrd (loop)/isolinux/initram.igz
}


menuentry 'ISO Natty        sda6'                        {
loopback loop (hd1,6)/iso/natty-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/natty-desktop-amd64.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}


menuentry 'ISO Maverick 64     sdb6'                        {
loopback loop (hd1,6)/iso/ubuntu-10.10-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-10.10-desktop-amd64.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}


menuentry 'ISO Lucid.1 64     sdb6'                        {
loopback loop (hd1,6)/iso/ubuntu-10.04.1-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-10.04.1-desktop-amd64.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}


menuentry 'ISO Karmic 64      sdb6'                        {
loopback loop (hd1,6)/iso/ubuntu-9.10-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-9.10-desktop-amd64.iso noprompt quiet splash
initrd (loop)/casper/initrd.lz
}


menuentry 'ISO Ku Karmic 64   sdb6'                        {
 loopback loop (hd1,6)/iso/kubuntu-9.10-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/kubuntu-9.10-desktop-amd64.iso noprompt quiet splash
 initrd (loop)/casper/initrd.lz
}


menuentry 'ISO Mint 9         sdb6'                        {
 loopback loop (hd1,6)/iso/linuxmint-9-gnome-cd-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/linuxmint-9-gnome-cd-amd64.iso noprompt quiet splash
 initrd (loop)/casper/initrd.lz
}


menuentry 'Puppy              sdb6'                        {
 loopback loop (hd1,6)/iso/lupu-511.iso
 linux (loop)/vmlinuz  iso_filename=/iso/lupu-511.iso boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt 
initrd (loop)/initrd.gz
}


menuentry 'ISO Lubuntu        sda6'                        {
loopback loop (hd1,6)/iso/lubuntu-10.04.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/lubuntu-10.04.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}


menuentry 'ISO Centos         sda6'                        {
loopback loop (hd1,6)/iso/CentOS-5.5-x86_64-LiveCD.iso
linux (loop)/isolinux/vmlinuz0 isoloop=/iso/CentOS-5.5-x86_64-LiveCD.iso
initrd (loop)/isolinux/initrd0.img
}


menuentry 'ISO Parted Magic   sdb6'                        {
set root=(hd1,6)
loopback loop (hd1,6)/iso/pmagic-5.2.iso
linux (loop)/pmagic/bzImage iso_filename=/iso/pmagic-5.2.iso boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt 
initrd (loop)/pmagic/initramfs
}


menuentry "freebsd 8.0" {
	set root=(hd0,2,a)
	chainloaderer +1
}


menuentry "Windows" {
insmod iso9660
loopback loop (hd1,6)/iso/winxp.iso
chainloader +1
}


menuentry 'ISO grub-rescue-remix      sda6'                        {
loopback loop (hd1,6)/iso/ubuntu-rescue-remix-10-10.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-rescue-remix-10-10.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}

menuentry 'Debian Install      sda6'                        {
loopback loop (hd1,6)/iso/debian-6.0.0-amd64-netinst.iso
linux (loop)/install.amd/vmlinuz boot=/install.amd iso-scan/filename=/iso/debian-6.0.0-amd64-netinst.iso noprompt noeject video=vesa:ywrap,mtrr vga=788
initrd (loop)/install.amd/gtk/initrd.gz
}

### END /etc/grub.d/ISO_custom.cfg ###
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=1c4adc10-a208-4373-b842-9851a8421da9 /               ext4    errors=remount-ro 0       1
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0
LABEL=lucid  /mnt/lucid  ext4  defaults,users,exec,noauto  0 2
LABEL=lucidhome  /mnt/lucidhome ext4  defaults,users,exec,noauto 0 2
LABEL=nattymain  /mnt/nattymain  ext4  defaults,users,exec,noauto 0 2
LABEL=nattyhome  /mnt/nattyhome  ext4  defaults,users,exec,noauto 0 2
LABEL=mav32  /mnt/mav32  ext4  defaults,users,exec,noauto  0 2
LABEL=lucid32  /mnt/lucid32  ext4  defaults,users,exec,noauto  0 2
LABEL=av   /mnt/av  ext4  users,defaults   0 2 
LABEL=bi   /mnt/bi  ext4  defaults,users  0 2 
LABEL=data   /mnt/data  ext4  users,exec   0 2 
LABEL=vm  /mnt/vm  ext4  users,exec  0 2
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 109.799236298 = 117.896032256  boot/grub/core.img                             1
 110.498985291 = 118.647382016  boot/grub/grub.cfg                             3
 110.131267548 = 118.252548096  boot/initrd.img-2.6.32-23-generic              1
 110.358680725 = 118.496731136  boot/initrd.img-2.6.35-23-generic              1
 110.514930725 = 118.664503296  boot/initrd.img-2.6.35-24-generic              2
 110.803997040 = 118.974885888  boot/initrd.img-2.6.35-25-generic              1
 110.126361847 = 118.247280640  boot/initrd.img-akk                            1
 110.643138885 = 118.802165760  boot/initrd.img-initrd.img-2.6.35-22-generic   1
 110.128814697 = 118.249914368  boot/initrd.img-initrd.img-2.6.35-23-generic   1
 110.282642365 = 118.415085568  boot/vmlinuz-2.6.35-23-generic                 1
 110.311569214 = 118.446145536  boot/vmlinuz-2.6.35-24-generic                 1
 110.840461731 = 119.014039552  boot/vmlinuz-2.6.35-25-generic                 1
 110.803997040 = 118.974885888  initrd.img                                     1
 110.514930725 = 118.664503296  initrd.img.old                                 2
 110.840461731 = 119.014039552  vmlinuz                                        1
 110.311569214 = 118.446145536  vmlinuz.old                                    1

=========================== sda9/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux	/boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sda9 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux	/boot/vmlinuz-2.6.32-26-generic root=/dev/sda9 ro   quiet splash
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-26-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-26-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro single
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro single
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro single
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10) (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.37-8-generic (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set fc46e770-f848-4485-8650-3f291b9dd1e1
	linux /boot/vmlinuz-2.6.37-8-generic root=UUID=fc46e770-f848-4485-8650-3f291b9dd1e1 ro quiet splash
	initrd /boot/initrd.img-2.6.37-8-generic
}
menuentry "Ubuntu, with Linux 2.6.37-8-generic (recovery mode) (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set fc46e770-f848-4485-8650-3f291b9dd1e1
	linux /boot/vmlinuz-2.6.37-8-generic root=UUID=fc46e770-f848-4485-8650-3f291b9dd1e1 ro single
	initrd /boot/initrd.img-2.6.37-8-generic
}
menuentry "Ubuntu, with Linux 2.6.37-6-generic (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set fc46e770-f848-4485-8650-3f291b9dd1e1
	linux /boot/vmlinuz-2.6.37-6-generic root=UUID=fc46e770-f848-4485-8650-3f291b9dd1e1 ro quiet splash
	initrd /boot/initrd.img-2.6.37-6-generic
}
menuentry "Ubuntu, with Linux 2.6.37-6-generic (recovery mode) (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set fc46e770-f848-4485-8650-3f291b9dd1e1
	linux /boot/vmlinuz-2.6.37-6-generic root=UUID=fc46e770-f848-4485-8650-3f291b9dd1e1 ro single
	initrd /boot/initrd.img-2.6.37-6-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set f3ec8e37-1383-4df6-a199-f2cd17283a07
	linux /vmlinuz-2.6.35-23-generic root=UUID=7266aac5-e357-40a8-8813-3fb2906add98 ro quiet splash
	initrd /initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set f3ec8e37-1383-4df6-a199-f2cd17283a07
	linux /vmlinuz-2.6.35-22-generic root=UUID=7266aac5-e357-40a8-8813-3fb2906add98 ro quiet splash
	initrd /initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu 2.6.35-23-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu 2.6.35-22-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "  (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Lucid sda1 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /initrd.img
}
menuentry "Mint sda10 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b
	initrd /initrd.img
}
menuentry "Puppy sda11 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=d91b5fd5-a61a-42d8-9cb0-cec9d871b634 pmedia=atahd
	initrd /initrd.gz
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb7)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 31f0f246-dbe3-45f3-93d5-dbc0ac382862
	linux /vmlinuz-2.6.18-194.el5 root=/dev/sdb7
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=56efcec8-787a-4d42-a01b-a48d2fe2f805 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

LABEL=av 		/mnt/av 	ext4 	defaults,auto,users,defaults 	0 2 
LABEL=bi 		/mnt/bi 	ext4 	defaults,auto,defaults,users	0 2 
LABEL=data 		/mnt/data 	ext4 	defaults,auto,users,exec 	0 2 
LABEL=vm		/mnt/vm 	ext4 	defaults,auto,users,exec 	0 2
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 121.806569099 = 130.788807680  boot/grub/core.img                             1
 121.915349007 = 130.905609216  boot/grub/grub.cfg                             1
 122.188290596 = 131.198678016  boot/initrd.img-2.6.32-25-generic              1
 122.149281502 = 131.156792320  boot/initrd.img-2.6.32-25-generic-pae          1
 122.172715187 = 131.181954048  boot/initrd.img-2.6.32-26-generic              1
 122.239953041 = 131.254150144  boot/initrd.img-2.6.32-26-generic-pae          1
 122.059678078 = 131.060581376  boot/vmlinuz-2.6.32-25-generic                 1
 122.028607368 = 131.027219456  boot/vmlinuz-2.6.32-25-generic-pae             1
 122.020661354 = 131.018687488  boot/vmlinuz-2.6.32-26-generic                 1
 122.177033424 = 131.186590720  boot/vmlinuz-2.6.32-26-generic-pae             1
 122.239953041 = 131.254150144  initrd.img                                     1
 122.172715187 = 131.181954048  initrd.img.old                                 1
 122.177033424 = 131.186590720  vmlinuz                                        1
 122.020661354 = 131.018687488  vmlinuz.old                                    1

========================== sda10/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,10)'
search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,10)'
search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,10)'
search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntuu, with Linux 2.6.32-25-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro acpi_enforce_resources=lax quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set f3ec8e37-1383-4df6-a199-f2cd17283a07
	linux /vmlinuz-2.6.35-23-generic root=UUID=7266aac5-e357-40a8-8813-3fb2906add98 ro quiet splash
	initrd /initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set f3ec8e37-1383-4df6-a199-f2cd17283a07
	linux /vmlinuz-2.6.35-22-generic root=UUID=7266aac5-e357-40a8-8813-3fb2906add98 ro quiet splash
	initrd /initrd.img-2.6.35-22-generic
}
menuentry "maverick 23-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "maverick 22-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Custom  (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Mint sda10 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b
	initrd /initrd.img
}
menuentry "Puppy sda11 (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=d91b5fd5-a61a-42d8-9cb0-cec9d871b634 pmedia=atahd
	initrd /initrd.gz
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=56efcec8-787a-4d42-a01b-a48d2fe2f805 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=56efcec8-787a-4d42-a01b-a48d2fe2f805 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda13 during installation
UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 124.541900158 = 133.725847040  boot/grub/core.img                             1
 126.457919598 = 135.783157248  boot/grub/grub.cfg                             1
 125.642611980 = 134.907727360  boot/initrd.img-2.6.32-21-generic              1
 125.623301983 = 134.886993408  boot/vmlinuz-2.6.32-21-generic                 1
 125.642611980 = 134.907727360  initrd.img                                     1
 125.623301983 = 134.886993408  vmlinuz                                        1

========================== sda11/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos16)'
search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos16)'
search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set b34b528a-26b2-4577-8d16-08b11df49182
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro single
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Maverick (on sda9) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash acpi_enforce_resources=lax
	initrd /initrd.img
}
menuentry "Lucid (on sda1) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro acpi_enforce_resources=lax quiet splash
	initrd /initrd.img
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10) (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set c0a41613-0d26-4583-88cc-f7171768be40
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set c0a41613-0d26-4583-88cc-f7171768be40
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-11-generic (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set c0a41613-0d26-4583-88cc-f7171768be40
	linux /boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-11-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-11-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-11-generic
}
menuentry "Maverick 8 (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # ipv6.disable=1
	initrd /initrd.img
}
menuentry "Natty 14 (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro vt.handoff=7 quiet splash
	initrd /initrd.img
}
menuentry "Lucid 1 (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro
	initrd /initrd.img
}
menuentry "Maverick 8 on Natty (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # vt.handoff=7
	initrd /initrd.img
}
menuentry "Natty 14 (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro # vt.handoff=7 quiet splash
	initrd /initrd.img
}
menuentry "Mint 10 (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b
	initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sda9 ro quiet splash
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda9 ro quiet splash
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set 31f0f246-dbe3-45f3-93d5-dbc0ac382862
	linux /vmlinuz-2.6.18-194.el5 root=/dev/sdb7
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda11/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda16 during installation
UUID=b34b528a-26b2-4577-8d16-08b11df49182 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

UUID=8144779b-ad38-4c1c-aa45-35065ad289e5 /mnt/data ext4 defaults,users,exec 0 2

--------------------------------------------------------------------------------

=================== sda11: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 140.555633545 = 150.920462336  boot/grub/core.img                             1
 143.271343231 = 153.836433408  boot/grub/grub.cfg                             1
 143.395458221 = 153.969700864  boot/initrd.img-2.6.35-25-generic-pae          2
 140.603416443 = 150.971768832  boot/vmlinuz-2.6.35-25-generic-pae             1
 143.395458221 = 153.969700864  initrd.img                                     2
 140.603416443 = 150.971768832  vmlinuz                                        1

========================== sda12/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
}

if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10) (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=56efcec8-787a-4d42-a01b-a48d2fe2f805 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda9)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=56efcec8-787a-4d42-a01b-a48d2fe2f805 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda12/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda13 during installation
UUID=7266aac5-e357-40a8-8813-3fb2906add98 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda14 during installation
UUID=f3ec8e37-1383-4df6-a199-f2cd17283a07 /boot           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

UUID=8144779b-ad38-4c1c-aa45-35065ad289e5  /mnt/data ext4 defaults,users,exec 0 2
--------------------------------------------------------------------------------

=================== sda12: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 149.458988190 = 160.480366592  boot/grub/grub.cfg                             1

========================== sda13/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos13)'
search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos13)'
search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	echo	'Loading Linux 2.6.38-3-generic ...'
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-3-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-2-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	linux	/boot/vmlinuz-2.6.38-2-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-2-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-2-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	echo	'Loading Linux 2.6.38-2-generic ...'
	linux	/boot/vmlinuz-2.6.38-2-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-2-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-1-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	linux	/boot/vmlinuz-2.6.38-1-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-1-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-1-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	echo	'Loading Linux 2.6.38-1-generic ...'
	linux	/boot/vmlinuz-2.6.38-1-generic root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-1-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos13)'
	search --no-floppy --fs-uuid --set=root c9101109-b746-464e-b9ec-5c62d9958c8d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root c5163c70-4f77-4034-a218-5dae03b07eed
	linux /boot/vmlinuz-2.6.32-27-generic root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro quiet splash
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Maverick (on sda9) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash acpi_enforce_resources=lax
	initrd /initrd.img
}
menuentry "Lucid (on sda1) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root c5163c70-4f77-4034-a218-5dae03b07eed
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro acpi_enforce_resources=lax quiet splash
	initrd /initrd.img
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda10) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos10)'
	search --no-floppy --fs-uuid --set=root 727222f8-f24a-4b1e-b1bd-023c7be6e78b
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos11)'
	search --no-floppy --fs-uuid --set=root b34b528a-26b2-4577-8d16-08b11df49182
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos11)'
	search --no-floppy --fs-uuid --set=root b34b528a-26b2-4577-8d16-08b11df49182
	linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro single
	initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-11-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 0e074399-7e68-4483-87ee-a63d92f9073d
	linux /boot/vmlinuz-2.6.37-11-generic root=UUID=c0a41613-0d26-4583-88cc-f7171768be40 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-11-generic
}
menuentry "Maverick 8 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # ipv6.disable=1
	initrd /initrd.img
}
menuentry "Mav32 16 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=b34b528a-26b2-4577-8d16-08b11df49182 ro # ipv6.disable=1
	initrd /initrd.img
}
menuentry "Natty 13 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro vt.handoff=7 quiet splash
	initrd /initrd.img
}
menuentry "Lucid 1 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c5163c70-4f77-4034-a218-5dae03b07eed ro
	initrd /initrd.img
}
menuentry "Maverick 8 on Natty (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro # vt.handoff=7
	initrd /initrd.img
}
menuentry "Natty 14 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro # vt.handoff=7 quiet splash
	initrd /initrd.img
}
menuentry "Mint 10 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz root=UUID=727222f8-f24a-4b1e-b1bd-023c7be6e78b
	initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Puppy sdb6 (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 1c4adc10-a208-4373-b842-9851a8421da9
	linux /vmlinuz iso_filename=/iso/lupu-511.iso boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt
	initrd /initrd.gz
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sda9 ro quiet splash
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 56efcec8-787a-4d42-a01b-a48d2fe2f805
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda9 ro quiet splash
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 31f0f246-dbe3-45f3-93d5-dbc0ac382862
	linux /vmlinuz-2.6.18-194.el5 root=/dev/sdb7
	initrd /initrd-2.6.18-194.el5.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda13/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda14 during installation
UUID=c9101109-b746-464e-b9ec-5c62d9958c8d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda15 during installation
UUID=53d33f36-01b4-4f50-8f52-9abecf8a19ff /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=2b7d27d5-37eb-4ee4-b5ea-71bec80838ec none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=8144779b-ad38-4c1c-aa45-35065ad289e5 /mnt/data 	ext4 defaults,users,exec 	0 2

LABEL=av 	/mnt/av 	ext4 	users,defaults 	0 2
LABEL=bi 	/mnt/bi 	ext4 	defaults,users	0 2
LABEL=data 	/mnt/data 	ext4 	users,exec 	0 2
LABEL=vm	/mnt/vm 	ext4 	users,exec 	0 2
LABEL=maverick	/mnt/maverick 	ext4 	users,exec,noauto  0 2

--------------------------------------------------------------------------------

=================== sda13: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 158.512893677 = 170.201923584  boot/grub/core.img                             1
 160.805335999 = 172.663414784  boot/grub/grub.cfg                             3
 158.164798737 = 169.828159488  boot/initrd.img-2.6.38-1-generic               2
 153.790100098 = 165.130862592  boot/initrd.img-2.6.38-2-generic               2
 153.938476562 = 165.290180608  boot/initrd.img-2.6.38-3-generic               2
 158.679313660 = 170.380615680  boot/vmlinuz-2.6.38-1-generic                  1
 152.946556091 = 164.225114112  boot/vmlinuz-2.6.38-2-generic                  1
 153.868453979 = 165.214994432  boot/vmlinuz-2.6.38-3-generic                  1
 153.938476562 = 165.290180608  initrd.img                                     2
 153.790100098 = 165.130862592  initrd.img.old                                 2
 153.868453979 = 165.214994432  vmlinuz                                        1
 152.946556091 = 164.225114112  vmlinuz.old                                    1

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
LABEL=centos            /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sda6               swap                    swap    defaults        0 0
/dev/sdb8 		/boot			ext3 	defaults,exec   0 0
--------------------------------------------------------------------------------

============================= sdb8/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd1,6)
#          kernel /boot/vmlinuz-version ro root=/dev/sdb7
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd1,6)/boot/grub/splash.xpm.gz
hiddenmenu
title CentOS-menu.lst (2.6.18-194.el5)
	root (hd1,6)
	kernel /boot/vmlinuz-2.6.18-194.el5 ro root=LABEL=centos rhgb quiet
	initrd /boot/initrd-2.6.18-194.el5.img
--------------------------------------------------------------------------------

=================== sdb8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 596.075199127 = 640.030871552  grub/grub.conf                                 1
 596.075199127 = 640.030871552  grub/menu.lst                                  1
 596.036308289 = 639.989112832  grub/stage2                                    2
 595.163612366 = 639.052062720  initrd-2.6.18-194.el5.img                      2
 595.165550232 = 639.054143488  vmlinuz-2.6.18-194.el5                         2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  fc 31 c0 8e d0 31 e4 8e  d8 8e c0 be 00 7c bf 00  |.1...1.......|..|
00000010  06 b9 00 01 f3 a5 be ee  07 b0 08 ea 20 06 00 00  |............ ...|
00000020  80 3e b3 07 ff 75 04 88  16 b3 07 80 3c 00 74 04  |.>...u......<.t.|
00000030  08 06 af 07 83 ee 10 d0  e8 73 f0 90 90 90 90 90  |.........s......|
00000040  90 90 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |................|
*
00000070  90 90 90 90 90 90 90 90  90 90 90 90 90 90 be be  |................|
00000080  07 b0 00 b9 04 00 80 3c  00 75 6e fe c0 83 c6 10  |.......<.un.....|
00000090  e2 f4 31 db b4 0e be 9d  07 8a 0e af 07 ac d0 e9  |..1.............|
000000a0  73 02 cd 10 08 c9 75 f5  b0 3a cd 10 31 c0 cd 16  |s.....u..:..1...|
000000b0  3c 00 74 f8 be 8b 07 b9  02 00 e8 ba 00 3c 0d 74  |<.t..........<.t|
000000c0  b4 3c 61 72 06 3c 7a 77  02 2c 20 88 c3 be 9d 07  |.<ar.<zw., .....|
000000d0  8a 0e af 07 ac d0 e9 73  04 38 c3 74 06 08 c9 75  |.......s.8.t...u|
000000e0  f3 eb af b8 0d 0e 31 db  cd 10 8d 84 62 00 3c 07  |......1.....b.<.|
000000f0  75 07 b0 1f a2 af 07 eb  99 31 d2 b9 01 00 3c 04  |u........1....<.|
00000100  74 11 73 f3 30 e4 b1 04  d2 e0 be be 07 01 c6 8a  |t.s.0...........|
00000110  16 b3 07 bf 05 00 56 f6  c2 80 74 31 b4 41 bb aa  |......V...t1.A..|
00000120  55 52 cd 13 5a 5e 56 72  1e 81 fb 55 aa 75 18 f6  |UR..Z^Vr...U.u..|
00000130  c1 01 74 13 8b 44 08 8b  5c 0a be 8d 07 89 44 08  |..t..D..\.....D.|
00000140  89 5c 0a b4 42 eb 0c 8a  74 01 8b 4c 02 b8 01 02  |.\..B...t..L....|
00000150  bb 00 7c 50 c6 06 8f 07  01 cd 13 58 5e 73 05 4f  |..|P.......X^s.O|
00000160  75 b4 eb 93 81 3e fe 7d  55 aa 75 f6 ea 00 7c 00  |u....>.}U.u...|.|
00000170  00 be 83 07 b9 0a 00 50  b4 0e 31 db ac cd 10 e2  |.......P..1.....|
00000180  fb 58 c3 54 65 73 74 44  69 73 6b 0d 0a 10 00 01  |.X.TestDisk.....|
00000190  00 00 7c 00 00 00 00 00  00 00 00 00 00 31 32 33  |..|..........123|
000001a0  34 46 00 00 41 4e 44 54  6d 62 72 00 02 02 02 1f  |4F..ANDTmbr.....|
000001b0  c7 00 00 80 00 00 00 00  00 00 00 00 a5 01 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb1

00000000  fc 31 c0 8e d0 31 e4 8e  d8 8e c0 be 00 7c bf 00  |.1...1.......|..|
00000010  06 b9 00 01 f3 a5 be ee  07 b0 08 ea 20 06 00 00  |............ ...|
00000020  80 3e b3 07 ff 75 04 88  16 b3 07 80 3c 00 74 04  |.>...u......<.t.|
00000030  08 06 af 07 83 ee 10 d0  e8 73 f0 90 90 90 90 90  |.........s......|
00000040  90 90 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |................|
*
00000070  90 90 90 90 90 90 90 90  90 90 90 90 90 90 be be  |................|
00000080  07 b0 00 b9 04 00 80 3c  00 75 6e fe c0 83 c6 10  |.......<.un.....|
00000090  e2 f4 31 db b4 0e be 9d  07 8a 0e af 07 ac d0 e9  |..1.............|
000000a0  73 02 cd 10 08 c9 75 f5  b0 3a cd 10 31 c0 cd 16  |s.....u..:..1...|
000000b0  3c 00 74 f8 be 8b 07 b9  02 00 e8 ba 00 3c 0d 74  |<.t..........<.t|
000000c0  b4 3c 61 72 06 3c 7a 77  02 2c 20 88 c3 be 9d 07  |.<ar.<zw., .....|
000000d0  8a 0e af 07 ac d0 e9 73  04 38 c3 74 06 08 c9 75  |.......s.8.t...u|
000000e0  f3 eb af b8 0d 0e 31 db  cd 10 8d 84 62 00 3c 07  |......1.....b.<.|
000000f0  75 07 b0 1f a2 af 07 eb  99 31 d2 b9 01 00 3c 04  |u........1....<.|
00000100  74 11 73 f3 30 e4 b1 04  d2 e0 be be 07 01 c6 8a  |t.s.0...........|
00000110  16 b3 07 bf 05 00 56 f6  c2 80 74 31 b4 41 bb aa  |......V...t1.A..|
00000120  55 52 cd 13 5a 5e 56 72  1e 81 fb 55 aa 75 18 f6  |UR..Z^Vr...U.u..|
00000130  c1 01 74 13 8b 44 08 8b  5c 0a be 8d 07 89 44 08  |..t..D..\.....D.|
00000140  89 5c 0a b4 42 eb 0c 8a  74 01 8b 4c 02 b8 01 02  |.\..B...t..L....|
00000150  bb 00 7c 50 c6 06 8f 07  01 cd 13 58 5e 73 05 4f  |..|P.......X^s.O|
00000160  75 b4 eb 93 81 3e fe 7d  55 aa 75 f6 ea 00 7c 00  |u....>.}U.u...|.|
00000170  00 be 83 07 b9 0a 00 50  b4 0e 31 db ac cd 10 e2  |.......P..1.....|
00000180  fb 58 c3 54 65 73 74 44  69 73 6b 0d 0a 10 00 01  |.X.TestDisk.....|
00000190  00 00 7c 00 00 00 00 00  00 00 00 00 00 31 32 33  |..|..........123|
000001a0  34 46 00 00 41 4e 44 54  6d 62 72 00 02 02 02 1f  |4F..ANDTmbr.....|
000001b0  c7 00 00 80 00 00 00 00  00 00 00 00 a5 01 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by kansasnoob on 2011-02-12
I guess I didn't mention that we're trying to get mawk upgraded, I began with a comment at this old bug which is confirmed:

[https://bugs.launchpad.net/ubuntu/+source/mawk/+bug/69724](https://bugs.launchpad.net/ubuntu/+source/mawk/+bug/69724)

Then Gert filed a new bug report:

[https://bugs.launchpad.net/ubuntu/+source/mawk/+bug/716920](https://bugs.launchpad.net/ubuntu/+source/mawk/+bug/716920)

I intend to check other distros for their current version of mawk, starting with Puppy.

I'd very much appreciate it if anyone that's multi-booting with anything Red Hat based would let me know the OS and the versions of mawk and gawk installed, or if they're installed :D

---

### Post by kansasnoob on 2011-02-12
Hmmm, I just checked Fedora 14, PCLinuxOS, and two different versions of Puppy. None had mawk installed or even available through the repos. I'm thinking gawk is becoming the only game in town :lolflag:

Now I have another bug to follow up on:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/711965](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/711965)

What did you do on your day off :D

---

### Post by Gert Hulselmans on 2011-02-12
Some (maybe) useful tricks:

Now you can give the output file another name than RESULTS.txt:
```
sudo bash boot_info_script.sh bis056_run_from_natty.txt
```BIS now displays a short help text when '-h', -help', '--help' or an invalid parameter is passed to the script.
```

$ bash boot_info_script.sh --help

Usage boot_info_script:
-----------------------

  Run the script as sudoer:

    sudo bash boot_info_script.sh <outputfile>

  or if your operating system does not use sudo:

    su -
    bash boot_info_script.sh <outputfile>


  When running the script, without specifying an output file, all the output
  is written to the file "RESULTS.txt" in the same folder as the script.

  But when run from /bin, /sbin, /usr/bin, or another system folder, the file
  "RESULTS.txt" is written to the home directory of the user.

  When the file "RESULTS.txt" already exists, the results will be written to
  "RESULTS1.txt". If "RESULTS1.txt" exists, the results will be written to
  "RESULTS2.txt", ...


  To get version number and last editing date of this script, use:
    (no root rights needed)

    bash boot_info_script.sh -v
    bash boot_info_script.sh -V
    bash boot_info_script.sh --version

  To get this help text, use (no root rights needed):

    bash boot_info_script.sh -h
    bash boot_info_script.sh -help
    bash boot_info_script.sh --help

  To automatically gzip a copy of the output file, use (root rights needed):

    bash boot_info_script.sh -g <outputfile>
    bash boot_info_script.sh --gzip <outputfile>

  If multiple versions of boot_info_script are detected in the same directory,
  boot_info_script will list all versions found.
  In that case you need to force boot_info_script to run a certain version,
  by adding "--this" as first argument (root rights needed):

    bash boot_info_script.sh --this <outputfile>


```Get last development version of Boot Info Script:
```
wget -O boot_info_script.sh  'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
```To compare the output **differences **between v055 and v056, it is also usefull to post the output of the following command:
```
diff -u RESULTS-v055.txt RESULTS-v056.txt
```@ Quackers
The last report you posted, isn't the last developpment version of BIS.
The "Location of iles loaded by Grub" section has hugely different values. I only compared a few ones with the first report, where you used a much more recent version of BIS.
There the values seem to match more (only checked a few), but not all the same files are reported.
Can you run 055 and the last development version again?

@ kansasnoob
As far as I hear, only Debian and Ubuntu have mawk by default.

Can you upload the first 63 sectors of this disk?
```
=> Grub Legacy  is installed in the MBR of /dev/sda and looks on boot drive 
    #-128 in partition #12 for /boot/grub/stage2 and /boot/grub/menu.lst.

``````
dd if=/dev/sda of=sda_63sectors_grublegacy.bin bs=512 count=63
```Can you also run the 2 versions on the same PC/VM from a much more recent version to see if the output is correct in that case?

---

### Post by Quackers on 2011-02-13
oops, sorry ( I get them mixed up :-) )
Thanks for all your work Gert!

Here is the output from 055
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for Bem.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   157,645,844   157,645,782   7 HPFS/NTFS
/dev/sda2         157,646,846   488,396,799   330,749,954   5 Extended
/dev/sda5         157,646,848   186,943,487    29,296,640  83 Linux
/dev/sda6         186,945,536   313,896,959   126,951,424  83 Linux
/dev/sda7         313,899,008   318,584,831     4,685,824  82 Linux swap / Solaris
/dev/sda8         318,586,880   343,975,935    25,389,056  83 Linux
/dev/sda9         343,977,984   488,396,799   144,418,816  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         153,147,706   488,396,799   335,249,094   5 Extended
/dev/sdb5         153,147,708   157,453,064     4,305,357  82 Linux swap / Solaris
/dev/sdb6         157,453,128   179,976,194    22,523,067  83 Linux
/dev/sdb7         179,976,258   302,857,379   122,881,122  83 Linux
/dev/sdb2    *      5,859,328    30,273,535    24,414,208  83 Linux
/dev/sdb3          30,282,525   153,147,644   122,865,120  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        24AFF28A10C76E23                       ntfs       New Volume                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1ee3d06b-96cd-446f-a38d-277f6643d173   ext4                                     
/dev/sda6        bbc193e8-8fa3-4297-a338-d09714ad8b57   ext4                                     
/dev/sda7        b2c066b6-fb5e-4056-9e81-ca7762527c95   swap                                     
/dev/sda8        d3f093d0-c583-4d78-8e37-2b540a3b90a8   ext4                                     
/dev/sda9        928c40f2-f671-47ca-ba05-c4f0631ba106   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        3f349741-954f-46c9-9467-67f8a3abd277   ext4                                     
/dev/sdb3        e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2   ext4                                     
/dev/sdb5        594a1856-3e11-4728-9293-72e85b43ffe5   swap                                     
/dev/sdb6        6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb   ext4                                     
/dev/sdb7        5f1485be-ef78-4354-bde5-61b4454e113a   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
insmod tga
if background_image /usr/share/images/grub/B-1B_over_the_pacific_ocean.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
set linux_gfx_mode=1920x1200
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	echo	'Loading Linux 2.6.38-3-generic ...'
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-3-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 24AFF28A10C76E23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=bbc193e8-8fa3-4297-a338-d09714ad8b57 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  83.0GB: boot/grub/core.img
  90.1GB: boot/grub/grub.cfg
  86.1GB: boot/initrd.img-2.6.38-3-generic
  92.4GB: boot/vmlinuz-2.6.38-3-generic
  86.1GB: initrd.img
  92.4GB: vmlinuz

=========================== sda8/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
insmod tga
if background_image /usr/share/images/grub/Moraine_Lake_17092005.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
set linux_gfx_mode=1920x1200
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	echo	'Loading Linux 2.6.38-3-generic ...'
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-3-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 24AFF28A10C76E23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sdb8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sdb8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=928c40f2-f671-47ca-ba05-c4f0631ba106 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 165.4GB: boot/grub/core.img
 169.9GB: boot/grub/grub.cfg
 173.3GB: boot/initrd.img-2.6.38-3-generic
 168.6GB: boot/vmlinuz-2.6.38-3-generic
 173.3GB: initrd.img
 168.6GB: vmlinuz

=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1920x1200
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 24aff28a10c76e23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=5f1485be-ef78-4354-bde5-61b4454e113a /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


  85.2GB: boot/grub/core.img
  85.5GB: boot/grub/grub.cfg
  85.5GB: boot/initrd.img-2.6.32-28-generic
  85.4GB: boot/vmlinuz-2.6.32-28-generic
  85.5GB: initrd.img
  85.4GB: vmlinuz

=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Maverick, with Linux 2.6.35-25' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1920x1200
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 24aff28a10c76e23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=3f349741-954f-46c9-9467-67f8a3abd277 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


   9.5GB: boot/grub/core.img
  12.6GB: boot/grub/grub.cfg
   5.8GB: boot/initrd.img-2.6.35-25-generic
   9.8GB: boot/vmlinuz-2.6.35-25-generic
   5.8GB: initrd.img
   9.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  41 00 00 30 78 43 30 30  35 30 30 37 42 00 00 30  |A..0xC005007B..0|
00000010  78 43 30 30 35 30 30 37  43 00 00 30 78 43 30 30  |xC005007C..0xC00|
00000020  35 30 30 37 44 00 00 30  78 43 30 30 35 30 30 37  |5007D..0xC005007|
00000030  45 00 00 30 78 43 30 30  35 30 30 37 46 00 00 56  |E..0xC005007F..V|
00000040  41 4c 49 44 41 54 49 4f  4e 5f 42 49 54 53 00 15  |ALIDATION_BITS..|
00000050  00 00 00 0a 00 2b 00 00  00 05 00 00 00 2b 00 00  |.....+.......+..|
00000060  00 0a 00 00 80 03 08 00  00 00 8c 12 00 00 94 12  |................|
00000070  00 00 00 03 00 00 00 07  00 00 00 9f 12 00 00 00  |................|
00000080  08 20 00 00 a7 12 00 00  00 75 69 6e 74 36 34 00  |. .......uint64.|
00000090  00 57 6d 69 44 61 74 61  49 64 00 00 42 69 74 4d  |.WmiDataId..BitM|
000000a0  61 70 00 0a 00 00 00 d3  12 00 00 d6 12 00 00 d9  |ap..............|
000000b0  12 00 00 dc 12 00 00 df  12 00 00 e2 12 00 00 e5  |................|
000000c0  12 00 00 e8 12 00 00 eb  12 00 00 ee 12 00 00 00  |................|
000000d0  30 00 00 31 00 00 32 00  00 33 00 00 34 00 00 35  |0..1..2..3..4..5|
000000e0  00 00 36 00 00 37 00 00  38 00 00 39 00 0c 00 00  |..6..7..8..9....|
000000f0  00 00 00 00 00 00 00 00  80 06 00 00 00 4d 00 53  |.............M.S|
00000100  00 4e 00 64 00 69 00 73  00 a9 b4 9e df 7e fe c6  |.N.d.i.s.....~..|
00000110  01 c8 01 00 00 00 00 00  00 00 09 00 00 00 10 00  |................|
00000120  00 00 00 4d 53 4e 64 69  73 00 08 00 00 00 41 00  |...MSNdis.....A.|
00000130  00 00 16 00 00 00 00 0b  00 00 00 ff ff 07 00 00  |................|
00000140  80 01 0b 00 00 00 ff ff  06 00 00 80 00 08 00 00  |................|
00000150  00 1b 00 00 00 24 00 00  00 00 08 00 00 00 2a 00  |.....$........*.|
00000160  00 00 52 00 00 00 00 03  00 00 00 01 00 00 00 03  |..R.............|
00000170  00 00 00 5e 00 00 00 66  00 00 00 99 00 00 00 a7  |...^...f........|
00000180  00 00 00 e4 00 00 00 f7  00 00 00 55 ff ff ff ff  |...........U....|
00000190  ff ff ff ff 41 01 00 80  00 4d 53 4e 64 69 73 5f  |....A....MSNdis_|
000001a0  44 72 69 76 65 72 56 65  72 73 69 6f 6e 00 00 57  |DriverVersion..W|
000001b0  4d 49 00 00 57 4d 49 50  72 6f 76 00 00 67 00 fe  |MI..WMIProv..g..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 bf 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 08  bf 01 00 28 91 07 00 00  |...........(....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

And the output from the latest development version
```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   157,645,844   157,645,782   7 NTFS / exFAT / HPFS
/dev/sda2         157,646,846   488,396,799   330,749,954   5 Extended
/dev/sda5         157,646,848   186,943,487    29,296,640  83 Linux
/dev/sda6         186,945,536   313,896,959   126,951,424  83 Linux
/dev/sda7         313,899,008   318,584,831     4,685,824  82 Linux swap / Solaris
/dev/sda8         318,586,880   343,975,935    25,389,056  83 Linux
/dev/sda9         343,977,984   488,396,799   144,418,816  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1         153,147,706   488,396,799   335,249,094   5 Extended
/dev/sdb5         153,147,708   157,453,064     4,305,357  82 Linux swap / Solaris
/dev/sdb6         157,453,128   179,976,194    22,523,067  83 Linux
/dev/sdb7         179,976,258   302,857,379   122,881,122  83 Linux
/dev/sdb2    *      5,859,328    30,273,535    24,414,208  83 Linux
/dev/sdb3          30,282,525   153,147,644   122,865,120  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        24AFF28A10C76E23                       ntfs       New Volume
/dev/sda5        1ee3d06b-96cd-446f-a38d-277f6643d173   ext4       
/dev/sda6        bbc193e8-8fa3-4297-a338-d09714ad8b57   ext4       
/dev/sda7        b2c066b6-fb5e-4056-9e81-ca7762527c95   swap       
/dev/sda8        d3f093d0-c583-4d78-8e37-2b540a3b90a8   ext4       
/dev/sda9        928c40f2-f671-47ca-ba05-c4f0631ba106   ext4       
/dev/sdb2        3f349741-954f-46c9-9467-67f8a3abd277   ext4       
/dev/sdb3        e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2   ext4       
/dev/sdb5        594a1856-3e11-4728-9293-72e85b43ffe5   swap       
/dev/sdb6        6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb   ext4       
/dev/sdb7        5f1485be-ef78-4354-bde5-61b4454e113a   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
insmod tga
if background_image /usr/share/images/grub/B-1B_over_the_pacific_ocean.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
set linux_gfx_mode=1920x1200
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	echo	'Loading Linux 2.6.38-3-generic ...'
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-3-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 24AFF28A10C76E23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=bbc193e8-8fa3-4297-a338-d09714ad8b57 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  77.317836761 = 83.019395072   boot/grub/core.img                             1
  83.986557007 = 90.179878912   boot/grub/grub.cfg                             1
  80.191871643 = 86.105366528   boot/initrd.img-2.6.38-3-generic               2
  86.101852417 = 92.451160064   boot/vmlinuz-2.6.38-3-generic                  1
  80.191871643 = 86.105366528   initrd.img                                     2
  86.101852417 = 92.451160064   vmlinuz                                        1

=========================== sda8/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
insmod tga
if background_image /usr/share/images/grub/Moraine_Lake_17092005.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
set linux_gfx_mode=1920x1200
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root d3f093d0-c583-4d78-8e37-2b540a3b90a8
	echo	'Loading Linux 2.6.38-3-generic ...'
	linux	/boot/vmlinuz-2.6.38-3-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-3-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 24AFF28A10C76E23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sdb8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sdb8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos8)'
	search --no-floppy --fs-uuid --set=root 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=928c40f2-f671-47ca-ba05-c4f0631ba106 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 154.044582367 = 165.404110848  boot/grub/core.img                             1
 158.320610046 = 169.995460608  boot/grub/grub.cfg                             1
 161.424705505 = 173.328457728  boot/initrd.img-2.6.38-3-generic               2
 157.054977417 = 168.636497920  boot/vmlinuz-2.6.38-3-generic                  1
 161.424705505 = 173.328457728  initrd.img                                     2
 157.054977417 = 168.636497920  vmlinuz                                        1

=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1920x1200
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 24aff28a10c76e23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Maverick, with Linux 2.6.35-25 (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro single
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sdb8)" {
	insmod ext2
	set root='(hd1,8)'
	search --no-floppy --fs-uuid --set 3639199d-deb5-445a-a5b9-0ff3a6e35a17
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=3639199d-deb5-445a-a5b9-0ff3a6e35a17 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=5f1485be-ef78-4354-bde5-61b4454e113a /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  79.348979950 = 85.200318464   boot/grub/core.img                             1
  79.651866913 = 85.525540864   boot/grub/grub.cfg                             1
  79.665321350 = 85.539987456   boot/initrd.img-2.6.32-28-generic              1
  79.601364136 = 85.471313920   boot/vmlinuz-2.6.32-28-generic                 1
  79.665321350 = 85.539987456   initrd.img                                     1
  79.601364136 = 85.471313920   vmlinuz                                        1

=========================== sdb2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Maverick, with Linux 2.6.35-25' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=1920x1200
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 3f349741-954f-46c9-9467-67f8a3abd277
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=3f349741-954f-46c9-9467-67f8a3abd277 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 24aff28a10c76e23
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1ee3d06b-96cd-446f-a38d-277f6643d173
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=1ee3d06b-96cd-446f-a38d-277f6643d173 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda8)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set d3f093d0-c583-4d78-8e37-2b540a3b90a8
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d3f093d0-c583-4d78-8e37-2b540a3b90a8 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set 6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb
	linux /boot/vmlinuz-2.6.32-28-generic root=UUID=6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb ro quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=3f349741-954f-46c9-9467-67f8a3abd277 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.927371979 = 9.585692672    boot/grub/core.img                             1
  11.788204193 = 12.657487872   boot/grub/grub.cfg                             2
   5.520507812 = 5.927600128    boot/initrd.img-2.6.35-25-generic              2
   9.207931519 = 9.886941184    boot/vmlinuz-2.6.35-25-generic                 1
   5.520507812 = 5.927600128    initrd.img                                     2
   9.207931519 = 9.886941184    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  41 00 00 30 78 43 30 30  35 30 30 37 42 00 00 30  |A..0xC005007B..0|
00000010  78 43 30 30 35 30 30 37  43 00 00 30 78 43 30 30  |xC005007C..0xC00|
00000020  35 30 30 37 44 00 00 30  78 43 30 30 35 30 30 37  |5007D..0xC005007|
00000030  45 00 00 30 78 43 30 30  35 30 30 37 46 00 00 56  |E..0xC005007F..V|
00000040  41 4c 49 44 41 54 49 4f  4e 5f 42 49 54 53 00 15  |ALIDATION_BITS..|
00000050  00 00 00 0a 00 2b 00 00  00 05 00 00 00 2b 00 00  |.....+.......+..|
00000060  00 0a 00 00 80 03 08 00  00 00 8c 12 00 00 94 12  |................|
00000070  00 00 00 03 00 00 00 07  00 00 00 9f 12 00 00 00  |................|
00000080  08 20 00 00 a7 12 00 00  00 75 69 6e 74 36 34 00  |. .......uint64.|
00000090  00 57 6d 69 44 61 74 61  49 64 00 00 42 69 74 4d  |.WmiDataId..BitM|
000000a0  61 70 00 0a 00 00 00 d3  12 00 00 d6 12 00 00 d9  |ap..............|
000000b0  12 00 00 dc 12 00 00 df  12 00 00 e2 12 00 00 e5  |................|
000000c0  12 00 00 e8 12 00 00 eb  12 00 00 ee 12 00 00 00  |................|
000000d0  30 00 00 31 00 00 32 00  00 33 00 00 34 00 00 35  |0..1..2..3..4..5|
000000e0  00 00 36 00 00 37 00 00  38 00 00 39 00 0c 00 00  |..6..7..8..9....|
000000f0  00 00 00 00 00 00 00 00  80 06 00 00 00 4d 00 53  |.............M.S|
00000100  00 4e 00 64 00 69 00 73  00 a9 b4 9e df 7e fe c6  |.N.d.i.s.....~..|
00000110  01 c8 01 00 00 00 00 00  00 00 09 00 00 00 10 00  |................|
00000120  00 00 00 4d 53 4e 64 69  73 00 08 00 00 00 41 00  |...MSNdis.....A.|
00000130  00 00 16 00 00 00 00 0b  00 00 00 ff ff 07 00 00  |................|
00000140  80 01 0b 00 00 00 ff ff  06 00 00 80 00 08 00 00  |................|
00000150  00 1b 00 00 00 24 00 00  00 00 08 00 00 00 2a 00  |.....$........*.|
00000160  00 00 52 00 00 00 00 03  00 00 00 01 00 00 00 03  |..R.............|
00000170  00 00 00 5e 00 00 00 66  00 00 00 99 00 00 00 a7  |...^...f........|
00000180  00 00 00 e4 00 00 00 f7  00 00 00 55 ff ff ff ff  |...........U....|
00000190  ff ff ff ff 41 01 00 80  00 4d 53 4e 64 69 73 5f  |....A....MSNdis_|
000001a0  44 72 69 76 65 72 56 65  72 73 69 6f 6e 00 00 57  |DriverVersion..W|
000001b0  4d 49 00 00 57 4d 49 50  72 6f 76 00 00 67 00 fe  |MI..WMIProv..g..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 bf 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 08  bf 01 00 28 91 07 00 00  |...........(....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

And the results of the comparison
```
nattyalpha@nattyalpha-VGN-AR51SU:~$ diff -u RESULTS.txt RESULTS3.txt
--- RESULTS.txt	2011-02-13 12:22:28.273259600 +0000
+++ RESULTS3.txt	2011-02-13 12:19:12.000000000 +0000
@@ -1,123 +1,121 @@
-                Boot Info Script 0.56    from 8 February 2011
+                Boot Info Script 0.55    dated February 15th, 2010                    
 
+============================= Boot Info Summary: ==============================
 
-============================= Boot Info Summary: ===============================
-
- => Grub 2 is installed in the MBR of /dev/sda and looks for 
-    (,msdos5)/boot/grub.
+ => Grub 2 is installed in the MBR of /dev/sda and looks for Bem.
  => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
     partition #2 for (,msdos2)/boot/grub.
 
-sda1: __________________________________________________________________________
+sda1: _________________________________________________________________________
 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  Windows 7
-    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
+    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
 
-sda2: __________________________________________________________________________
+sda2: _________________________________________________________________________
 
     File system:       Extended Partition
     Boot sector type:  Unknown
     Boot sector info:  
 
-sda5: __________________________________________________________________________
+sda5: _________________________________________________________________________
 
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
     Operating System:  Ubuntu natty (development 
                        branch)
-    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
+    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
 
-sda6: __________________________________________________________________________
+sda6: _________________________________________________________________________
 
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
     Operating System:  
-    Boot files:        
+    Boot files/dirs:   
 
-sda7: __________________________________________________________________________
+sda7: _________________________________________________________________________
 
     File system:       swap
     Boot sector type:  -
     Boot sector info:  
 
-sda8: __________________________________________________________________________
+sda8: _________________________________________________________________________
 
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
     Operating System:  Ubuntu natty (development 
                        branch)
-    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
+    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
 
-sda9: __________________________________________________________________________
+sda9: _________________________________________________________________________
 
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
     Operating System:  
-    Boot files:        
+    Boot files/dirs:   
 
-sdb1: __________________________________________________________________________
+sdb1: _________________________________________________________________________
 
     File system:       Extended Partition
     Boot sector type:  -
     Boot sector info:  
 
-sdb5: __________________________________________________________________________
+sdb5: _________________________________________________________________________
 
     File system:       swap
     Boot sector type:  -
     Boot sector info:  
 
-sdb6: __________________________________________________________________________
+sdb6: _________________________________________________________________________
 
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
     Operating System:  Ubuntu 10.04.2 LTS
-    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
+    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
 
-sdb7: __________________________________________________________________________
+sdb7: _________________________________________________________________________
 
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
     Operating System:  
-    Boot files:        
+    Boot files/dirs:   
 
-sdb2: __________________________________________________________________________
+sdb2: _________________________________________________________________________
 
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
     Operating System:  Ubuntu 10.10
-    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
+    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
 
-sdb3: __________________________________________________________________________
+sdb3: _________________________________________________________________________
 
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
     Operating System:  
-    Boot files:        
+    Boot files/dirs:   
 
-============================ Drive/Partition Info: =============================
+=========================== Drive/Partition Info: =============================
 
-Drive: sda _____________________________________________________________________
+Drive: sda ___________________ _____________________________________________________
 
 Disk /dev/sda: 250.1 GB, 250059350016 bytes
 255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 
-Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
+Partition  Boot         Start           End          Size  Id System
 
-/dev/sda1    *             63   157,645,844   157,645,782   7 NTFS / exFAT / HPFS
+/dev/sda1    *             63   157,645,844   157,645,782   7 HPFS/NTFS
 /dev/sda2         157,646,846   488,396,799   330,749,954   5 Extended
 /dev/sda5         157,646,848   186,943,487    29,296,640  83 Linux
 /dev/sda6         186,945,536   313,896,959   126,951,424  83 Linux
@@ -126,14 +124,14 @@
 /dev/sda9         343,977,984   488,396,799   144,418,816  83 Linux
 
 
-Drive: sdb _____________________________________________________________________
+Drive: sdb ___________________ _____________________________________________________
 
 Disk /dev/sdb: 250.1 GB, 250059350016 bytes
 255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 
-Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
+Partition  Boot         Start           End          Size  Id System
 
 /dev/sdb1         153,147,706   488,396,799   335,249,094   5 Extended
 /dev/sdb5         153,147,708   157,453,064     4,305,357  82 Linux swap / Solaris
@@ -143,23 +141,27 @@
 /dev/sdb3          30,282,525   153,147,644   122,865,120  83 Linux
 
 
-"blkid" output: ________________________________________________________________
+blkid -c /dev/null: ____________________________________________________________
 
-Device           UUID                                   TYPE       LABEL
+Device           UUID                                   TYPE       LABEL                         
 
-/dev/sda1        24AFF28A10C76E23                       ntfs       New Volume
-/dev/sda5        1ee3d06b-96cd-446f-a38d-277f6643d173   ext4       
-/dev/sda6        bbc193e8-8fa3-4297-a338-d09714ad8b57   ext4       
-/dev/sda7        b2c066b6-fb5e-4056-9e81-ca7762527c95   swap       
-/dev/sda8        d3f093d0-c583-4d78-8e37-2b540a3b90a8   ext4       
-/dev/sda9        928c40f2-f671-47ca-ba05-c4f0631ba106   ext4       
-/dev/sdb2        3f349741-954f-46c9-9467-67f8a3abd277   ext4       
-/dev/sdb3        e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2   ext4       
-/dev/sdb5        594a1856-3e11-4728-9293-72e85b43ffe5   swap       
-/dev/sdb6        6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb   ext4       
-/dev/sdb7        5f1485be-ef78-4354-bde5-61b4454e113a   ext4       
+/dev/sda1        24AFF28A10C76E23                       ntfs       New Volume                    
+/dev/sda2: PTTYPE="dos" 
+/dev/sda5        1ee3d06b-96cd-446f-a38d-277f6643d173   ext4                                     
+/dev/sda6        bbc193e8-8fa3-4297-a338-d09714ad8b57   ext4                                     
+/dev/sda7        b2c066b6-fb5e-4056-9e81-ca7762527c95   swap                                     
+/dev/sda8        d3f093d0-c583-4d78-8e37-2b540a3b90a8   ext4                                     
+/dev/sda9        928c40f2-f671-47ca-ba05-c4f0631ba106   ext4                                     
+/dev/sda: PTTYPE="dos" 
+/dev/sdb1: PTTYPE="dos" 
+/dev/sdb2        3f349741-954f-46c9-9467-67f8a3abd277   ext4                                     
+/dev/sdb3        e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2   ext4                                     
+/dev/sdb5        594a1856-3e11-4728-9293-72e85b43ffe5   swap                                     
+/dev/sdb6        6d173d67-aa9f-4bb4-b5d9-d457c30ab2eb   ext4                                     
+/dev/sdb7        5f1485be-ef78-4354-bde5-61b4454e113a   ext4                                     
+/dev/sdb: PTTYPE="dos" 
 
-================================ Mount points: =================================
+============================ "mount | grep ^/dev  output: ===========================
 
 Device           Mount_Point              Type       Options
 
@@ -169,7 +171,6 @@
 
 =========================== sda5/boot/grub/grub.cfg: ===========================
 
---------------------------------------------------------------------------------
 #
 # DO NOT EDIT THIS FILE
 #
@@ -333,11 +334,9 @@
   source $prefix/custom.cfg;
 fi
 ### END /etc/grub.d/41_custom ###
---------------------------------------------------------------------------------
 
-=============================== sda5/etc/fstab: ================================
+=============================== sda5/etc/fstab: ===============================
 
---------------------------------------------------------------------------------
 # /etc/fstab: static file system information.
 #
 # Use 'blkid -o value -s UUID' to print the universally unique identifier
@@ -354,22 +353,19 @@
 UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
 # swap was on /dev/sdb5 during installation
 UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
---------------------------------------------------------------------------------
 
-=================== sda5: Location of files loaded by Grub: ====================
+=================== sda5: Location of files loaded by Grub: ===================
 
-           GiB - GB             File                                 Fragment(s)
 
-  77.317836761 = 83.019395072   boot/grub/core.img                             1
-  83.986557007 = 90.179878912   boot/grub/grub.cfg                             1
-  80.191871643 = 86.105366528   boot/initrd.img-2.6.38-3-generic               2
-  86.101852417 = 92.451160064   boot/vmlinuz-2.6.38-3-generic                  1
-  80.191871643 = 86.105366528   initrd.img                                     2
-  86.101852417 = 92.451160064   vmlinuz                                        1
+  83.0GB: boot/grub/core.img
+  90.1GB: boot/grub/grub.cfg
+  86.1GB: boot/initrd.img-2.6.38-3-generic
+  92.4GB: boot/vmlinuz-2.6.38-3-generic
+  86.1GB: initrd.img
+  92.4GB: vmlinuz
 
 =========================== sda8/boot/grub/grub.cfg: ===========================
 
---------------------------------------------------------------------------------
 #
 # DO NOT EDIT THIS FILE
 #
@@ -565,11 +561,9 @@
   source $prefix/custom.cfg;
 fi
 ### END /etc/grub.d/41_custom ###
---------------------------------------------------------------------------------
 
-=============================== sda8/etc/fstab: ================================
+=============================== sda8/etc/fstab: ===============================
 
---------------------------------------------------------------------------------
 # /etc/fstab: static file system information.
 #
 # Use 'blkid -o value -s UUID' to print the universally unique identifier
@@ -586,22 +580,19 @@
 UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
 # swap was on /dev/sdb5 during installation
 UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
---------------------------------------------------------------------------------
 
-=================== sda8: Location of files loaded by Grub: ====================
+=================== sda8: Location of files loaded by Grub: ===================
 
-           GiB - GB             File                                 Fragment(s)
 
- 154.044582367 = 165.404110848  boot/grub/core.img                             1
- 158.320610046 = 169.995460608  boot/grub/grub.cfg                             1
- 161.424705505 = 173.328457728  boot/initrd.img-2.6.38-3-generic               2
- 157.054977417 = 168.636497920  boot/vmlinuz-2.6.38-3-generic                  1
- 161.424705505 = 173.328457728  initrd.img                                     2
- 157.054977417 = 168.636497920  vmlinuz                                        1
+ 165.4GB: boot/grub/core.img
+ 169.9GB: boot/grub/grub.cfg
+ 173.3GB: boot/initrd.img-2.6.38-3-generic
+ 168.6GB: boot/vmlinuz-2.6.38-3-generic
+ 173.3GB: initrd.img
+ 168.6GB: vmlinuz
 
 =========================== sdb6/boot/grub/grub.cfg: ===========================
 
---------------------------------------------------------------------------------
 #
 # DO NOT EDIT THIS FILE
 #
@@ -753,11 +744,9 @@
 # menu entries you want to add after this comment.  Be careful not to change
 # the 'exec tail' line above.
 ### END /etc/grub.d/40_custom ###
---------------------------------------------------------------------------------
 
-=============================== sdb6/etc/fstab: ================================
+=============================== sdb6/etc/fstab: ===============================
 
---------------------------------------------------------------------------------
 # /etc/fstab: static file system information.
 #
 # Use 'blkid -o value -s UUID' to print the universally unique identifier
@@ -774,22 +763,19 @@
 UUID=b2c066b6-fb5e-4056-9e81-ca7762527c95 none            swap    sw              0       0
 # swap was on /dev/sdb5 during installation
 UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
---------------------------------------------------------------------------------
 
-=================== sdb6: Location of files loaded by Grub: ====================
+=================== sdb6: Location of files loaded by Grub: ===================
 
-           GiB - GB             File                                 Fragment(s)
 
-  79.348979950 = 85.200318464   boot/grub/core.img                             1
-  79.651866913 = 85.525540864   boot/grub/grub.cfg                             1
-  79.665321350 = 85.539987456   boot/initrd.img-2.6.32-28-generic              1
-  79.601364136 = 85.471313920   boot/vmlinuz-2.6.32-28-generic                 1
-  79.665321350 = 85.539987456   initrd.img                                     1
-  79.601364136 = 85.471313920   vmlinuz                                        1
+  85.2GB: boot/grub/core.img
+  85.5GB: boot/grub/grub.cfg
+  85.5GB: boot/initrd.img-2.6.32-28-generic
+  85.4GB: boot/vmlinuz-2.6.32-28-generic
+  85.5GB: initrd.img
+  85.4GB: vmlinuz
 
 =========================== sdb2/boot/grub/grub.cfg: ===========================
 
---------------------------------------------------------------------------------
 #
 # DO NOT EDIT THIS FILE
 #
@@ -966,11 +952,9 @@
   source $prefix/custom.cfg;
 fi
 ### END /etc/grub.d/41_custom ###
---------------------------------------------------------------------------------
 
-=============================== sdb2/etc/fstab: ================================
+=============================== sdb2/etc/fstab: ===============================
 
---------------------------------------------------------------------------------
 # /etc/fstab: static file system information.
 #
 # Use 'blkid -o value -s UUID' to print the universally unique identifier
@@ -985,22 +969,19 @@
 UUID=e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2 /home           ext4    defaults        0       2
 # swap was on /dev/sdb5 during installation
 UUID=594a1856-3e11-4728-9293-72e85b43ffe5 none            swap    sw              0       0
---------------------------------------------------------------------------------
-
-=================== sdb2: Location of files loaded by Grub: ====================
 
-           GiB - GB             File                                 Fragment(s)
+=================== sdb2: Location of files loaded by Grub: ===================
 
-   8.927371979 = 9.585692672    boot/grub/core.img                             1
-  11.788204193 = 12.657487872   boot/grub/grub.cfg                             2
-   5.520507812 = 5.927600128    boot/initrd.img-2.6.35-25-generic              2
-   9.207931519 = 9.886941184    boot/vmlinuz-2.6.35-25-generic                 1
-   5.520507812 = 5.927600128    initrd.img                                     2
-   9.207931519 = 9.886941184    vmlinuz                                        1
 
-======================== Unknown MBRs/Boot Sectors/etc: ========================
+   9.5GB: boot/grub/core.img
+  12.6GB: boot/grub/grub.cfg
+   5.8GB: boot/initrd.img-2.6.35-25-generic
+   9.8GB: boot/vmlinuz-2.6.35-25-generic
+   5.8GB: initrd.img
+   9.8GB: vmlinuz
+=========================== Unknown MBRs/Boot Sectors/etc =======================
 
-Unknown BootLoader on sda2
+Unknown BootLoader  on sda2
 
 00000000  41 00 00 30 78 43 30 30  35 30 30 37 42 00 00 30  |A..0xC005007B..0|
 00000010  78 43 30 30 35 30 30 37  43 00 00 30 78 43 30 30  |xC005007C..0xC00|

```

I haven't compared yet. I'm looking now :-)
If I did anything wrong, or if anything else is needed, just holler :-)
Thanks again.

---

### Post by kansasnoob on 2011-02-13
Just snooping about in 8.04.4/Hardy again this AM and I'm fairly sure the major problems are a result of the kernel and/or parted to read ext4 partitions and possibly some other things. For instance parted shows all partitions as ext3 but I know some are ext4:

```
lance@lance-desktop:~$ sudo parted /dev/sda print

Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  43.3GB  43.3GB  primary   ext3         boot 
 2      43.3GB  86.2GB  42.8GB  primary   ext3              
 3      86.2GB  129GB   43.0GB  primary   ext3              
 4      129GB   500GB   371GB   extended                    
18      129GB   151GB   21.8GB  logical   ext3              
14      151GB   172GB   21.1GB  logical   ext3              
15      172GB   193GB   21.1GB  logical   ext3              
16      193GB   215GB   21.4GB  logical   ext3              
17      215GB   236GB   21.4GB  logical   ext3              
13      236GB   258GB   22.0GB  logical   ext3              
12      258GB   280GB   21.6GB  logical   ext3              
11      280GB   301GB   21.7GB  logical   ext3              
10      301GB   323GB   21.8GB  logical   ext3              
 5      323GB   378GB   55.1GB  logical   ext3              
 6      378GB   432GB   53.6GB  logical   ext3              
 7      432GB   487GB   54.9GB  logical   ext3              
 8      487GB   498GB   10.7GB  logical   ext3              
 9      498GB   500GB   2517MB  logical   linux-swap        

```

I also decided to install it's legacy grub to it's root partitions PBR but there is no significant difference between BIS versions regarding that:

```
-sda12: _________________________________________________________________________
+sda12: __________________________________________________________________________
 
     File system:       ext3
     Boot sector type:  Grub
@@ -108,9 +109,9 @@
                        /dev/sda. Stage2 looks on partition #12 for 
                        /boot/grub/menu.lst.
     Operating System:  Ubuntu 8.04.4 LTS
-    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab
+    Boot files:        /boot/grub/menu.lst /etc/fstab
```

Since color makes the .diff text so much easier to read I'm just attaching them all as tar.gz's.

[ATTACH]183360[/ATTACH]

[ATTACH]183361[/ATTACH]

[ATTACH]183362[/ATTACH]

[ATTACH]183363[/ATTACH]

I'll follow up checking the difference of BIS when run from either Maverick or Lucid with Hardy's legacy grub still installed to the MBR of sda.

Let me know if I need to repeat any of that. I'd expect to be upgrading this Hardy to Lucid as part of upgrade testing very soon, probably no later than the 15th, but it'll still be legacy grub (until I change it anyway).

---

### Post by kansasnoob on 2011-02-13
The only real surprise running this from Maverick is that the diff.txt lacks the color that makes it easier to read :D

```
-                Boot Info Script 0.55    dated February 15th, 2010                    
+                Boot Info Script 0.56    from 8 February 2011
 
-============================= Boot Info Summary: ==============================
 
- => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
-    in partition #12 for /boot/grub/stage2 and /boot/grub/menu.lst.
+============================= Boot Info Summary: ===============================
+
+ => Grub Legacy  is installed in the MBR of /dev/sda and looks on boot drive 
+    #-128 in partition #12 for /boot/grub/stage2 and /boot/grub/menu.lst.
  => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
-    partition #14 for gnak.
+    partition #14 for /boot/grub.
```

[ATTACH]183365[/ATTACH]

[ATTACH]183366[/ATTACH]

[ATTACH]183367[/ATTACH]

I'll now see how it reads from Natty. After installing Hardy I noticed that it's grub failed to detect any OS with a kernel beyond 2.6.35* so I'll just install Natty's grub to the MBR of sdb and change boot priority in BIOS. That way Hardy's legacy grub will still be installed to the MBR of sda and it's root PBR.

---

### Post by kansasnoob on 2011-02-13
No notable changes running this from Natty:

```
-                Boot Info Script 0.55    dated February 15th, 2010                    
+                Boot Info Script 0.56    from 8 February 2011
 
-============================= Boot Info Summary: ==============================
 
- => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
-    in partition #12 for /boot/grub/stage2 and /boot/grub/menu.lst.
+============================= Boot Info Summary: ===============================
+
+ => Grub Legacy  is installed in the MBR of /dev/sda and looks on boot drive 
+    #-128 in partition #12 for /boot/grub/stage2 and /boot/grub/menu.lst.
  => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
-    partition #14 for gnak.
+    partition #14 for /boot/grub.
```

[ATTACH]183368[/ATTACH]

[ATTACH]183369[/ATTACH]

[ATTACH]183370[/ATTACH]

---

### Post by Gert Hulselmans on 2011-02-13
@ kansasnoob
Grub Legacy boot drive reporting is fixed (or should be :)).

@ Quackers
The output seems to be fine :).

---

### Post by Quackers on 2011-02-13
Thanks again for all your work, Gert.
Some of us would be lost without the BIS :-)

---

### Post by VMC on 2011-02-13
> **Quackers said:**
> Thanks again for all your work, Gert.
Some of us would be lost without the BIS :-)

Agreed! One of the most useful scripts around.

---

### Post by Gert Hulselmans on 2011-02-13
Grub 1.97-1.97 vs 1.99 detection added to the MBR detection (instead of the more general Grub2).

You can track all changes at:
      [http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=log](http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=log)

So when something new is added, it would be nice if some tests it (if it is relevant to your setup).

---

### Post by drs305 on 2011-02-14
First, I too would like to add my thanks for your work on the BIS. :-)

The general version (1.98 vs 1.99) shows up fine for me with the new script. There can be differences between even the minor revisions of G2, but adding the specific Ubuntu version (such as 1.98+20100804-5ubuntu3) might be overkill in most cases.

Maverick:
> 
[noparse]
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub 1.97-1.98 is installed in the MBR of /dev/sda and looks on the same 
    drive in partition #8 for (,msdos8)/boot/grub.
 => Grub 1.97-1.98 is installed in the MBR of /dev/sdb and looks on the same 
    drive in partition #8 for (,msdos8)/boot/grub.
[/noparse]


Natty:
> 
[noparse]
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub 1.99 is installed in the MBR of /dev/sda and looks for 
    (,msdos1)/boot/grub.
[/noparse]


---

### Post by kansasnoob on 2011-02-14
> **Gert Hulselmans said:**
> Grub 1.97-1.97 vs 1.99 detection added to the MBR detection (instead of the more general Grub2).

You can track all changes at:
      [http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=log](http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=log)

So when something new is added, it would be nice if some tests it (if it is relevant to your setup).

Just clearing the fog from my noggen this AM and I noticed this in my mail:

[https://bugs.launchpad.net/ubuntu/+source/mawk/+bug/716920/comments/1](https://bugs.launchpad.net/ubuntu/+source/mawk/+bug/716920/comments/1)

And the 'wget' for the new version of the script appears slightly different than that above:

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=0c8e808eba272af5ef8b5f4df4654f350526d17b'
```

Does that make any difference?

I know the version I just downloaded using the link you posted here did show changes because I renamed the BIS version I was using yesterday to "boot_info_script056.sh" before downloading and used 'diff -u' to compare:

```
--- boot_info_script.sh	2011-02-14 05:26:47.000000000 -0600
+++ boot_info_script056.sh	2011-02-11 19:00:40.000000000 -0600
@@ -1485,8 +1485,8 @@
 stage2_loc () {
   local stage1="$1" HI;
 
-  offset=$(hexdump -v -s 68 -n 4 -e '4 "%u"' "${stage1}");
-  dr=$(hexdump -v -s 64 -n 1 -e '1/1 "%u"' "${stage1}");
+  offset=$(hexdump -v -s 68 -n 4 -e '4 "%u"' "${stage1}" 2>> ${Trash});
+  dr=$(hexdump -v -s 64 -n 1 -e '"%d"' "${stage1}" 2>> ${Trash});
   pa='T';
   Grub_Version='';
 
@@ -1617,7 +1617,7 @@
 
      # Calcutate the exact offset to the embedded menu.
      offset_menu=$(( ( ${offset_menu%:*} / 2 ) + 16 ));
-	 dd if="${source}" count=1 skip=1 bs=${offset_menu} 2>> ${Trash} | gawk 'BEGIN { RS="\0" } { if (NR == 1) print $0 }' >> "${Log1}";
+     dd if="${source}" count=1 skip=1 bs=${offset_menu} 2>> ${Trash} | gawk -F '\0' '{print $1}' >> "${Log1}";
 
      echo '--------------------------------------------------------------------------------' >> "${Log1}";
   fi
@@ -1834,7 +1834,7 @@
 	48b4) BST='Grub 1.96';    
 	      core_loc ${part} '1.96';
 	      BSI="${BSI} Grub 1.96 is installed in the boot sector of ${name} and ${Core_Msg}";;
-	7c3c) BST='Grub 1.97-1.98';    
+	7c3c) BST='Grub 1.97 - 1.98';    
 	      core_loc ${part} '1.97';
 	      BSI="${BSI} Grub 2 is installed in the boot sector of ${name} and ${Core_Msg}";;
 	0020) BST='Grub 1.99';
@@ -2354,28 +2354,18 @@
   drive="${HDName[${HI}]}";
   Message="is installed in the MBR of ${drive}";
 
-  # Read the whole MBR in hexadecimal format.
-  MBR_512=$(hexdump -v -n 512 -e '/1 "%02x"' ${drive});
-
   ## Look at the first 2-4 bytes of the hard drive to identify the boot code installed in the MBR. ##
   #
   #   If it is not enough, look at more bytes.
 
-  MBR_sig4="${MBR_512:0:8}";
-  MBR_sig3="${MBR_512:0:6}";
-  MBR_sig2="${MBR_512:0:4}";
-
-  ## Bytes 0x80-0x81 of the MBR. ##
-  #
-  #   Use it to differentiate between different versions of the same bootloader.
-
-  MBR_bytes80to81="${MBR_512:256:4}";
-
+  MBR_sig4=$(hexdump -v -n 4 -e '/1 "%02x"' ${drive});
+  MBR_sig3="${MBR_sig4:0:6}";
+  MBR_sig2="${MBR_sig4:0:4}";
 
   case ${MBR_sig2} in
 
     eb48) ## Grub Legacy is in the MBR. ##
-	  BL="Grub Legacy";
+	  BL="Grub Legacy ${Grub_Version}";
 
 	  # 0x44 contains the offset to the next stage.
 	  offset=$(hexdump -v -s 68 -n 4 -e '"%u"' ${drive});
@@ -2388,9 +2378,6 @@
 	     # Grub is installed with stage1.5 files.
 	     Grub_String=$(hexdump -v -s 1042 -n 94 -e '"%_u"' ${drive});
 	     Grub_Version="${Grub_String%%nul*}";
-
-	     BL="Grub Legacy ${Grub_Version}";
-
 	     tmp="/${Grub_String#*/}";
 	     tmp="${tmp%%nul*}";
 
@@ -2399,7 +2386,7 @@
 	     [[ x"$menu" = x'' ]] || stage="${stage} and ${menu}";
 
 	     part_info=$((1045 + ${#Grub_Version}));
-	     eval $(hexdump -v -s ${part_info} -n 2 -e '1/1 "pa=%u; " 1/1 "dr=%u"' ${drive});
+	     eval $(hexdump -v -s ${part_info} -n 2 -e '1/1 "pa=%d; " 1/1 "dr=%d"' ${drive});
 	     
 	     dr=$(( ${dr} - 127 ));
 	     pa=$(( ${pa} + 1 ));
@@ -2438,50 +2425,46 @@
 	  fi;;
 
     eb63) ## Grub 2 is in the MBR. ##
-	  case ${MBR_bytes80to81} in
-		7c3c) grub2_version='1.97'; BL='Grub 1.97-1.98';;
-		0020) grub2_version='1.99'; BL='Grub 1.99';;
-	  esac
+	  BL='Grub 2';
 
 	  # 0x5c contains the offset to the Core.
 	  offset=$(hexdump -v -s 92 -n 4 -e '"%u"' ${drive});
 
 	  if [ "${offset}" -ne 1 ] ; then
 	     # Grub2 is installed without embedded Core.
-	     core_loc ${drive} ${grub2_version};
+	     core_loc ${drive} 1.97;
 	     Message="${Message} and ${Core_Msg}";
 	  else
 	     # Grub2 is installed with embedded Core.
 
-	     if [ ${grub2_version} = '1.99' ] ; then
-
-		# For Grub v1.99, the Core_Dir is just at the beginning of the compressed part of core.img
-		# 
-		# Get grub_core_uncompressed    : byte 0x208-0x20b of embedded core.img ==> byte 520+512 = 1032
-		# Get grub_modules_uncompressed : byte 0x20c-0x20f of embedded core.img ==> byte 524+512 = 1036
-		# Get grub_core_compressed      : byte 0x210-0x213 of embedded core.img ==> byte 528+512 = 1040
-		# Get grub_install_dos_part     : byte 0x214-0x218 of embedded core.img ==> byte 532+512 = 1044 --> only 1 byte needed
+	     # For Grub 2 (v1.99), the Core_Dir is just at the beginning of the compressed part of core.img
+	     # 
+	     # Get grub_core_uncompressed    : byte 0x208-0x20b of embedded core.img ==> byte 520+512 = 1032
+	     # Get grub_modules_uncompressed : byte 0x20c-0x20f of embedded core.img ==> byte 524+512 = 1036
+	     # Get grub_core_compressed      : byte 0x210-0x213 of embedded core.img ==> byte 528+512 = 1040
+	     # Get grub_install_dos_part     : byte 0x214-0x218 of embedded core.img ==> byte 532+512 = 1044 --> only 1 byte needed
 
-		eval $(hexdump -v -s $((0x208 + 512)) -n 13 -e '1/4 "core_uncompressed=" "%x; " 1/4 "modules_uncompressed=%x; core_compressed=" 4/1 "#x%02x" 1/1 "; install_dos_part=%d; "' ${drive});
+	     eval $(hexdump -v -s $((0x208 + 512)) -n 13 -e '1/4 "core_uncompressed=" "%x; " 1/4 "modules_uncompressed=%x; core_compressed=" 4/1 "#x%02x" 1/1 "; install_dos_part=%d; "' ${drive});
 
-		# Scan for "d1 e9 df fe ff ff 00 00": last 8 bytes of lzma_decode to find the offset of the lzma_stream.
-		eval $(hexdump -v -s 512 -n $((0x${core_uncompressed})) -e '1/1 "%02x"' ${drive} | \
+	     # Scan for "d1 e9 df fe ff ff 00 00": last 8 bytes of lzma_decode to find the offset of the lzma_stream.
+	     eval $(hexdump -v -s 512 -n $((0x${core_uncompressed})) -e '1/1 "%02x"' ${drive} | \
 		   gawk '{ found_at=match($0, "d1e9dffeffff0000" ); if (found_at == "0") { print "offset_lzma=0" } \
 			else { print "offset_lzma=" ((found_at - 1 ) / 2 ) + 8 + 512 } }');
 
-		if [ ${offset_lzma} -ne 0 ] ; then
+	     if [ ${offset_lzma} -ne 0 ] ; then
+		# if The offset of lzma is after 4096 bytes assume it is the version with the lzma encoded cor dir string
+		if [ ${offset_lzma} -gt 4096 ] ; then
 		   # Make lzma header (13 bytes) and add lzma_stream:
 		   printf "\x5d\x00\x00\x01\x00${core_compressed//#/\\}\x00\x00\x00\x00" > ${Tmp_Log}
 		   Core_Dir=$(dd if=${drive} bs=${offset_lzma} skip=1 count=$((0x${core_uncompressed} / ${offset_lzma} + 1)) 2>> ${Trash} | cat ${Tmp_Log} - | unlzma | hexdump -v -n 64 -e '"%_u"' | sed 's/nul[^$]*//');
+		else
+		      Core_Dir=$(hexdump -v -s 1052 -n 64 -e '"%_u"' ${drive} | sed 's/nul[^$]*//');
 		fi
+#	     fi
 
-	     else
-		# Grub v1.97-1.98.
-		Core_Dir=$(hexdump -v -s 1052 -n 64 -e '"%_u"' ${drive} | sed 's/nul[^$]*//');
-	     fi
-
-	     pa=$(hexdump -v -s 1044 -n 1 -e '"%d"' ${drive});
-	     dr=$(hexdump -v -s 77 -n 1 -e '"%d"' ${drive});
+	#     Core_Dir=$(echo  ${Grub_String} | sed s/nul[^$]*//);
+	     pa=$(hexdump -v -s 1044  -n 1 -e '"%d"' ${drive});
+	     dr=$(hexdump -v -s 77  -n 1 -e '"%d"' ${drive});
 	     dr=$(( ${dr} - 127 ));
 	     pa=$(( ${pa} + 1 ));
 
@@ -2490,7 +2473,8 @@
 	     else
 	        Message="${Message} and looks on the same drive in partition #${pa} for ${Core_Dir}";
 	     fi
-	  fi;;
+	fi # fix
+	    fi;;
 
     0ebe) BL='ThinkPad';;
     31c0) BL='Acer 3';;
@@ -2498,13 +2482,9 @@
 	  case ${MBR_sig3} in
 	    33c08e) BL='Windows';;
 	    33c090) BL='DiskCryptor';;
-	    33c0fa) BL='Syslinux MBR (4.04 and higher)';;			
-	  esac;;
-    33ed) # Look at bytes 0x80-0x81 to be more specific about the Syslinux variant/version.
-	  case ${MBR_bytes80to81} in
-	    407c) BL='ISOhybrid (Syslinux 4.04 and higher)';;
-	    83e1) BL='ISOhybrid with partition support (Syslinux 4.04 and higher)';;
+	    33c0fa) BL='Syslinux MBR';;
 	  esac;;
+    33ed) BL='ISOhybrid (Syslinux)';;
     33ff) BL='HP/Gateway';;
     b800) BL='Plop';;
     ea05) BL='XOSL';;
@@ -2521,25 +2501,8 @@
 	  esac;;
     fa31) # Look at the first 3 bytes of the hard drive to identify the boot code installed in the MBR.
 	  case ${MBR_sig3} in
-	    fa31c0) # Look at bytes 0x80-0x81 to be more specific about the Syslinux variant/version.
-		    case ${MBR_bytes80to81} in
-		      0069) BL='ISOhybrid (Syslinux 3.72-3.73)';;
-		      7c66) BL='Syslinux MBR (3.61-4.03)';;
-		      7cb8) BL='Syslinux MBR (3.36-3.51)';;
-		      b442) BL='Syslinux MBR (3.00-3.35)';;
-		      bb00) BL='Syslinux MBR (3.52-3.60)';;
-		      e879) BL='ISOhybrid (Syslinux 3.74-3.80)';;
-		    esac;;
+	    fa31c0) BL='Syslinux MBR';;
 	    fa31c9) BL='Master Boot LoaDeR';;   
-	    fa31ed) # Look at bytes 0x80-0x81 to be more specific about the Syslinux variant/version.
-		    case ${MBR_bytes80to81} in
-		      0069) BL='ISOhybrid (Syslinux 3.72-3.73)';;
-		      0fb6) BL='ISOhybrid with partition support (Syslinux 3.82-3.86)';;
-		      407c) BL='ISOhybrid (Syslinux 3.82-4.03)';;
-		      83e1) BL='ISOhybrid with partition support (Syslinux 4.00-4.03)';;
-		      b6c6) BL='ISOhybrid with partition support (Syslinux 3.81)';;
-		      fbc0) BL='ISOhybrid (Syslinux 3.81)';;
-		    esac;;
 	  esac;;
     fa33) BL='MS-DOS 3.30 through Windows 95 (A)';;
     fab8) # Look at the first 4 bytes of the hard drive to identify the boot code installed in the MBR.
```

I guess the only difference between the two DL locations is:

"hb=0c8e808eba272af5ef8b5f4df4654f350526d17b"
"hb=HEAD'"

I'm guessing 'HEAD' always gets the newest whereas the checksum forces the version you were testing when you reported that bug. Sorry to be a bit on the dense side :redface:

I'd also like to thank you and Meierfra for maintaining this script. It's truly invaluable in many cases, some even beyond dealing with the bootloader.

Last dumb question of the morning, if I hadn't renamed the old BIS would the new one just replace the old one if the names matched? I think you already addressed that in post #22 here:

[http://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900](http://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900)

I just like to be absolutely certain I'm doing the right thing ;)

---

### Post by kansasnoob on 2011-02-14
Regarding a favicon for BIS, I've been thinking, but I really stink at graphics :(

But I'm thinking along the lines of an animated/cartoonish investigator (think Sherlock Holmes, inspector Clouseau from the Pink Panther, etc) looking through a magnifying glass at either a computer or a script of sorts.

Does anyone here know someone that's good with graphics? I have thought I could make a mention at Ayatana, but I've really pressed my luck there regarding ubiquity problems, so I'm about as popular as a turd in a punch bowl among that crowd ATM :D

---

### Post by kansasnoob on 2011-02-14
I think the "modified timestamp" here answers one of my dumb questions:

[ATTACH]183453[/ATTACH]

I'll run the new script now and post the results.

---

### Post by kansasnoob on 2011-02-14
From what I can see things look fine here:

```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy 0.97 is installed in the MBR of /dev/sda and looks on the same 
    drive in partition #12 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 1.99 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #14 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97-1.98
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 12587135 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 1.97-1.98
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 169853109 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda11: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda12: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda12 and 
                       looks at sector 507466884 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #12 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda13: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda14: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 1.99
    Boot sector info:  Grub 2 is installed in the boot sector of sda14 and 
                       looks at sector 320434089 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda15: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda16: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''

sda17: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda18: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type 'ext4'

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a6391

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    84,646,484    84,646,422  83 Linux
/dev/sda2          84,646,485   168,313,004    83,666,520  83 Linux
/dev/sda3         168,313,005   252,349,019    84,036,015  83 Linux
/dev/sda4         252,349,020   976,768,064   724,419,045   5 Extended
/dev/sda5         631,209,978   738,861,479   107,651,502  83 Linux
/dev/sda6         738,861,543   843,637,409   104,775,867  83 Linux
/dev/sda7         843,637,473   950,919,479   107,282,007  83 Linux
/dev/sda8         950,919,543   971,852,174    20,932,632  83 Linux
/dev/sda9         971,852,238   976,768,064     4,915,827  82 Linux swap / Solaris
/dev/sda10        588,637,728   631,209,914    42,572,187  83 Linux
/dev/sda11        546,161,868   588,637,664    42,475,797  83 Linux
/dev/sda12        503,878,788   546,161,804    42,283,017  83 Linux
/dev/sda13        460,904,913   503,878,724    42,973,812  83 Linux
/dev/sda14        295,001,721   336,144,059    41,142,339  83 Linux
/dev/sda15        336,144,123   377,318,654    41,174,532  83 Linux
/dev/sda16        377,318,718   419,119,784    41,801,067  83 Linux
/dev/sda17        419,119,848   460,904,849    41,785,002  83 Linux
/dev/sda18        252,350,464   295,000,063    42,649,600  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002c729

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    17,816,084    17,816,022  83 Linux
/dev/sdb2          17,816,085   156,296,384   138,480,300   5 Extended
/dev/sdb5          17,816,148   151,316,234   133,500,087  83 Linux
/dev/sdb6         151,316,298   156,296,384     4,980,087  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        b7a0df33-53e4-4f0d-856b-0da92ff0d743   ext3       Maverick
/dev/sda10       6114df72-5fec-467a-b6cf-bfb49b76def1   ext4       Mint Julia
/dev/sda11       ed0bdce8-0af8-4cce-9933-cbac8389fe4d   ext4       Squeeze
/dev/sda12       96bef601-3776-4e41-bf5a-ca81d3e5058d   ext3       Hardy
/dev/sda13       720d719e-e571-4bdd-aac9-718f0ffe2266   ext4       Peppermint
/dev/sda14       8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079   ext4       MM to NN A2
/dev/sda15       22eefad4-870e-4191-87c9-57f4e756411d   ext4       LMDE
/dev/sda2        1332b9d0-cf18-4299-9094-12acbdac91ad   ext3       Karmic
/dev/sda3        d252929b-949d-432e-a18c-18f9ae770d28   ext3       Lucid
/dev/sda5        594c3d40-2791-4c0a-8644-d9812545da2d   ext3       Backups
/dev/sda6        8a3f6c83-cb52-4caf-96b8-5faf2c830453   ext3       Pictures
/dev/sda7        05289ee4-d681-4806-b6fd-aefd784f9323   ext3       Downloads
/dev/sda8        571cfad8-68c7-4703-883e-c0baa2a381d4   ext3       Documents
/dev/sda9        80627269-1ccd-4774-b4ea-a5ef8824ffaa   swap       
/dev/sdb1        04d890c5-9f08-4cfe-ac93-c31dc8fe7e07   ext4       
/dev/sdb5        b9aab6d9-b9a9-44c6-abc5-63e2edcfc84d   ext4       
/dev/sdb6        ae8fa315-50cc-4dc8-8edd-d3b9c28ebb7d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda12       /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=60
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-26-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro   
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	echo	'Loading Linux 2.6.35-26-generic ...'
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-26-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set 8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda14)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos14)'
	search --no-floppy --fs-uuid --set 8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079
	linux /boot/vmlinuz-2.6.38-3-generic root=UUID=8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079 ro single
	initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 96bef601-3776-4e41-bf5a-ca81d3e5058d
	linux /boot/vmlinuz-2.6.24-28-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro quiet splash
	initrd /boot/initrd.img-2.6.24-28-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode) (on /dev/sda12)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set 96bef601-3776-4e41-bf5a-ca81d3e5058d
	linux /boot/vmlinuz-2.6.24-28-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro single
	initrd /boot/initrd.img-2.6.24-28-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (on /dev/sda16)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set 7a90aa0c-2377-48e4-97ad-20283c962abc
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=7a90aa0c-2377-48e4-97ad-20283c962abc ro vga=792 quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.38-2-generic (recovery mode) (on /dev/sda16)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos16)'
	search --no-floppy --fs-uuid --set 7a90aa0c-2377-48e4-97ad-20283c962abc
	linux /boot/vmlinuz-2.6.38-2-generic root=UUID=7a90aa0c-2377-48e4-97ad-20283c962abc ro single vga=792
	initrd /boot/initrd.img-2.6.38-2-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda18)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos18)'
	search --no-floppy --fs-uuid --set ff93a40e-f9a6-4864-b3f2-0f357263f689
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff93a40e-f9a6-4864-b3f2-0f357263f689 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda18)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos18)'
	search --no-floppy --fs-uuid --set ff93a40e-f9a6-4864-b3f2-0f357263f689
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff93a40e-f9a6-4864-b3f2-0f357263f689 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sda3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=d252929b-949d-432e-a18c-18f9ae770d28 ro quiet splash
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sda3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
	linux /boot/vmlinuz-2.6.32-29-generic root=UUID=d252929b-949d-432e-a18c-18f9ae770d28 ro single
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda10) (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 6114df72-5fec-467a-b6cf-bfb49b76def1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6114df72-5fec-467a-b6cf-bfb49b76def1 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda10) -- recovery mode (on /dev/sda10)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set 6114df72-5fec-467a-b6cf-bfb49b76def1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6114df72-5fec-467a-b6cf-bfb49b76def1 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set ed0bdce8-0af8-4cce-9933-cbac8389fe4d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=ed0bdce8-0af8-4cce-9933-cbac8389fe4d ro quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda11)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set ed0bdce8-0af8-4cce-9933-cbac8389fe4d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=ed0bdce8-0af8-4cce-9933-cbac8389fe4d ro single
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Peppermint, 2.6.32-24-generic (/dev/sda13) (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set 720d719e-e571-4bdd-aac9-718f0ffe2266
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=720d719e-e571-4bdd-aac9-718f0ffe2266 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Peppermint, 2.6.32-24-generic (/dev/sda13) -- recovery mode (on /dev/sda13)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos13)'
	search --no-floppy --fs-uuid --set 720d719e-e571-4bdd-aac9-718f0ffe2266
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=720d719e-e571-4bdd-aac9-718f0ffe2266 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda15)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos15)'
	search --no-floppy --fs-uuid --set 22eefad4-870e-4191-87c9-57f4e756411d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=22eefad4-870e-4191-87c9-57f4e756411d ro splash quiet quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda15)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos15)'
	search --no-floppy --fs-uuid --set 22eefad4-870e-4191-87c9-57f4e756411d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=22eefad4-870e-4191-87c9-57f4e756411d ro single splash quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda17)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos17)'
	search --no-floppy --fs-uuid --set d70bbade-c57d-4c81-84e1-7674021673d6
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d70bbade-c57d-4c81-84e1-7674021673d6 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda17)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos17)'
	search --no-floppy --fs-uuid --set d70bbade-c57d-4c81-84e1-7674021673d6
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d70bbade-c57d-4c81-84e1-7674021673d6 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 1332b9d0-cf18-4299-9094-12acbdac91ad
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 1332b9d0-cf18-4299-9094-12acbdac91ad
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
# swap is on /dev/sda9
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw                0       0
#/dev/sda5    /mnt/sda5 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda5       ext3    defaults          0       2
#/dev/sda6    /mnt/sda6 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda6       ext3    defaults          0       2     
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda8       ext3    defaults          0       2
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img
            ?? = ??             boot/grub/grub.cfg
            ?? = ??             boot/initrd.img-2.6.35-22-generic
            ?? = ??             boot/initrd.img-2.6.35-23-generic
            ?? = ??             boot/initrd.img-2.6.35-24-generic
            ?? = ??             boot/initrd.img-2.6.35-25-generic
            ?? = ??             boot/initrd.img-2.6.35-26-generic
            ?? = ??             boot/vmlinuz-2.6.35-22-generic
            ?? = ??             boot/vmlinuz-2.6.35-23-generic
            ?? = ??             boot/vmlinuz-2.6.35-24-generic
            ?? = ??             boot/vmlinuz-2.6.35-25-generic
            ?? = ??             boot/vmlinuz-2.6.35-26-generic
            ?? = ??             initrd.img
            ?? = ??             initrd.img.old
            ?? = ??             vmlinuz
            ?? = ??             vmlinuz.old

=========================== sda2/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1332b9d0-cf18-4299-9094-12acbdac91ad

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-22-generic
uuid		1332b9d0-cf18-4299-9094-12acbdac91ad
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid		1332b9d0-cf18-4299-9094-12acbdac91ad
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=1332b9d0-cf18-4299-9094-12acbdac91ad /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw                0       0
#/dev/sda5    /mnt/sda5 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda5       ext3    defaults          0       2
#/dev/sda6    /mnt/sda6 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda6       ext3    defaults          0       2     
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda8       ext3    defaults          0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/menu.lst
            ?? = ??             boot/initrd.img-2.6.31-21-generic
            ?? = ??             boot/initrd.img-2.6.31-22-generic
            ?? = ??             boot/vmlinuz-2.6.31-21-generic
            ?? = ??             boot/vmlinuz-2.6.31-22-generic
            ?? = ??             initrd.img.old
            ?? = ??             vmlinuz.old

=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=40
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-29-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=d252929b-949d-432e-a18c-18f9ae770d28 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set d252929b-949d-432e-a18c-18f9ae770d28
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=d252929b-949d-432e-a18c-18f9ae770d28 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda10) (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 6114df72-5fec-467a-b6cf-bfb49b76def1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6114df72-5fec-467a-b6cf-bfb49b76def1 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda10) -- recovery mode (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 6114df72-5fec-467a-b6cf-bfb49b76def1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6114df72-5fec-467a-b6cf-bfb49b76def1 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda11)" {
	insmod ext2
	set root='(hd0,11)'
	search --no-floppy --fs-uuid --set ed0bdce8-0af8-4cce-9933-cbac8389fe4d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=ed0bdce8-0af8-4cce-9933-cbac8389fe4d ro quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda11)" {
	insmod ext2
	set root='(hd0,11)'
	search --no-floppy --fs-uuid --set ed0bdce8-0af8-4cce-9933-cbac8389fe4d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=ed0bdce8-0af8-4cce-9933-cbac8389fe4d ro single
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Lubuntu 10.10, kernel 2.6.35-24-generic (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set 9b5de705-ccb3-4cb4-b692-75b0ebfcb276
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b5de705-ccb3-4cb4-b692-75b0ebfcb276 ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Lubuntu 10.10, kernel 2.6.35-24-generic (recovery mode) (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set 9b5de705-ccb3-4cb4-b692-75b0ebfcb276
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b5de705-ccb3-4cb4-b692-75b0ebfcb276 ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Peppermint, 2.6.32-24-generic (/dev/sda13) (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,13)'
	search --no-floppy --fs-uuid --set 720d719e-e571-4bdd-aac9-718f0ffe2266
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=720d719e-e571-4bdd-aac9-718f0ffe2266 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Peppermint, 2.6.32-24-generic (/dev/sda13) -- recovery mode (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,13)'
	search --no-floppy --fs-uuid --set 720d719e-e571-4bdd-aac9-718f0ffe2266
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=720d719e-e571-4bdd-aac9-718f0ffe2266 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda14)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set 8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda14)" {
	insmod ext2
	set root='(hd0,14)'
	search --no-floppy --fs-uuid --set 8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079 ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda15)" {
	insmod ext2
	set root='(hd0,15)'
	search --no-floppy --fs-uuid --set 22eefad4-870e-4191-87c9-57f4e756411d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=22eefad4-870e-4191-87c9-57f4e756411d ro splash quiet quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda15)" {
	insmod ext2
	set root='(hd0,15)'
	search --no-floppy --fs-uuid --set 22eefad4-870e-4191-87c9-57f4e756411d
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=22eefad4-870e-4191-87c9-57f4e756411d ro single splash quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda16)" {
	insmod ext2
	set root='(hd0,16)'
	search --no-floppy --fs-uuid --set 7a90aa0c-2377-48e4-97ad-20283c962abc
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=7a90aa0c-2377-48e4-97ad-20283c962abc ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda16)" {
	insmod ext2
	set root='(hd0,16)'
	search --no-floppy --fs-uuid --set 7a90aa0c-2377-48e4-97ad-20283c962abc
	linux /boot/vmlinuz-2.6.38-1-generic root=UUID=7a90aa0c-2377-48e4-97ad-20283c962abc ro single
	initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda17)" {
	insmod ext2
	set root='(hd0,17)'
	search --no-floppy --fs-uuid --set d70bbade-c57d-4c81-84e1-7674021673d6
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d70bbade-c57d-4c81-84e1-7674021673d6 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda17)" {
	insmod ext2
	set root='(hd0,17)'
	search --no-floppy --fs-uuid --set d70bbade-c57d-4c81-84e1-7674021673d6
	linux /boot/vmlinuz-2.6.37-12-generic root=UUID=d70bbade-c57d-4c81-84e1-7674021673d6 ro single
	initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda18)" {
	insmod ext2
	set root='(hd0,18)'
	search --no-floppy --fs-uuid --set ff93a40e-f9a6-4864-b3f2-0f357263f689
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff93a40e-f9a6-4864-b3f2-0f357263f689 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda18)" {
	insmod ext2
	set root='(hd0,18)'
	search --no-floppy --fs-uuid --set ff93a40e-f9a6-4864-b3f2-0f357263f689
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff93a40e-f9a6-4864-b3f2-0f357263f689 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 1332b9d0-cf18-4299-9094-12acbdac91ad
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 1332b9d0-cf18-4299-9094-12acbdac91ad
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro single
	initrd /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=d252929b-949d-432e-a18c-18f9ae770d28 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw                0       0
#/dev/sda5    /mnt/sda5 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda5       ext3    defaults          0       2
#/dev/sda6    /mnt/sda6 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda6       ext3    defaults          0       2     
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda8       ext3    defaults          0       2
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img
            ?? = ??             boot/grub/grub.cfg
            ?? = ??             boot/initrd.img-2.6.32-25-generic
            ?? = ??             boot/initrd.img-2.6.32-26-generic
            ?? = ??             boot/initrd.img-2.6.32-27-generic
            ?? = ??             boot/initrd.img-2.6.32-28-generic
            ?? = ??             boot/initrd.img-2.6.32-29-generic
            ?? = ??             boot/vmlinuz-2.6.32-25-generic
            ?? = ??             boot/vmlinuz-2.6.32-26-generic
            ?? = ??             boot/vmlinuz-2.6.32-27-generic
            ?? = ??             boot/vmlinuz-2.6.32-28-generic
            ?? = ??             boot/vmlinuz-2.6.32-29-generic
            ?? = ??             initrd.img
            ?? = ??             initrd.img.old
            ?? = ??             vmlinuz
            ?? = ??             vmlinuz.old

========================== sda12/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,11)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro quiet splash
initrd		/boot/initrd.img-2.6.24-28-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro single
initrd		/boot/initrd.img-2.6.24-28-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,11)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-23-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-24-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-25-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 10.10 (10.10) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-26-generic root=/dev/sda1 
initrd		/boot/initrd.img-2.6.35-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 9.10, kernel 2.6.31-22-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=1332b9d0-cf18-4299-9094-12acbdac91ad ro single 
initrd		/boot/initrd.img-2.6.31-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-25-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-27-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-27-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-28-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-28-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 10.04.2 LTS (10.04) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-29-generic root=/dev/sda3 
initrd		/boot/initrd.img-2.6.32-29-generic
savedefault
boot

--------------------------------------------------------------------------------

=============================== sda12/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda12
UUID=96bef601-3776-4e41-bf5a-ca81d3e5058d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=80627269-1ccd-4774-b4ea-a5ef8824ffaa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda12: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/menu.lst
            ?? = ??             boot/grub/stage2
            ?? = ??             boot/initrd.img-2.6.24-26-generic
            ?? = ??             boot/initrd.img-2.6.24-28-generic
            ?? = ??             boot/initrd.img-2.6.24-28-generic.bak
            ?? = ??             boot/vmlinuz-2.6.24-26-generic
            ?? = ??             boot/vmlinuz-2.6.24-28-generic
            ?? = ??             initrd.img
            ?? = ??             initrd.img.old
            ?? = ??             vmlinuz
            ?? = ??             vmlinuz.old

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda16


Unknown BootLoader on sda17


Unknown BootLoader on sda18



=============================== StdErr Messages: ===============================

hexdump: /dev/sda16: No such file or directory
hexdump: /dev/sda16: No such file or directory
hexdump: /dev/sda17: No such file or directory
hexdump: /dev/sda17: No such file or directory
hexdump: /dev/sda18: No such file or directory
hexdump: /dev/sda18: No such file or directory
```

diff -u tells the story better than I can:

[ATTACH]183454[/ATTACH]

I will of course test this for regression with newer versions of Ubuntu. You truly amaze me :D

I did just get the official 8.04.4 > 10.04.2 upgrade testing notification and I'm going to give that top priority since the desktop version of 8.04 reaches end-of-life in April. So I'll not have an installed 8.04.4 available for testing real soon, but if needed I'll be glad to install a copy at a future date.

My greatest concern with the 8.04.4 > 10.04.2 upgrade is if the release notes need to be changed regarding grub :D

---

### Post by Gert Hulselmans on 2011-02-14
@ kansasnoob
I provided that second link (older version), because the problem with mawk, might not be that clear with the last development version (mawk and gawk output is still not the same, but the embedded grub4dos menu.lst seems to be extracted right, (is missing some newlines at the end)).

This will always overwrite the boot_info_script.sh file:
```

wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=0c8e808eba272af5ef8b5f4df4654f350526d17b'
```If you don't want this, change the filename after the "-O" parameter.

This will add the current date to the filename:
```
wget -O boot_info_script_$(date "+%m-%d-%Y").sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
```The check for existing BIS files only happens when you have:
```
boot_info_script.sh
boot_info_script(1).sh
boot_info_script(2).sh
...
```in the same directory. This warns you when you downloaded BIS with Firefox or Chromium and you forgot that you already had an old copy in the same directory.

Can you run the last version on the PC/VM with Grub Legacy? The problem you reported, should be fixed.

---

### Post by kansasnoob on 2011-02-14
> Can you run the last version on the PC/VM with Grub Legacy? The problem you reported, should be fixed.

It is. We've become used to posting the full RESULTS.txt here on the forums in code tags. I guess some people are scared to open a tar.gz. But what I posted in post #50 is correct and it was run from Hardy before I began the upgrade to 10.04.2. And it was run from the newest version of the BIS.

The truly pertinent part is in the BIS.diff.txt attachment there:

```
--- RESULTS_056.txt	2011-02-13 10:16:15.000000000 -0600
+++ RESULTS.txt	2011-02-14 10:20:43.000000000 -0600
@@ -3,15 +3,15 @@
 
 ============================= Boot Info Summary: ===============================
 
- => Grub Legacy  is installed in the MBR of /dev/sda and looks on boot drive 
-    #-128 in partition #12 for /boot/grub/stage2 and /boot/grub/menu.lst.
- => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
-    partition #14 for /boot/grub.
+ => Grub Legacy 0.97 is installed in the MBR of /dev/sda and looks on the same 
+    drive in partition #12 for /boot/grub/stage2 and /boot/grub/menu.lst.
+ => Grub 1.99 is installed in the MBR of /dev/sdb and looks on the same drive 
+    in partition #14 for /boot/grub.
 
 sda1: __________________________________________________________________________
 
     File system:       ext3
-    Boot sector type:  Grub 1.97 - 1.98
+    Boot sector type:  Grub 1.97-1.98
     Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                        looks at sector 12587135 of the same hard drive for 
                        core.img, but core.img can not be found at this 
@@ -30,7 +30,7 @@
 sda3: __________________________________________________________________________
 
     File system:       ext3
-    Boot sector type:  Grub 1.97 - 1.98
+    Boot sector type:  Grub 1.97-1.98
     Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                        looks at sector 169853109 of the same hard drive for 
                        core.img, but core.img can not be found at this 
@@ -386,7 +386,7 @@
 	insmod ext2
 	set root='(hd0,msdos1)'
 	search --no-floppy --fs-uuid --set b7a0df33-53e4-4f0d-856b-0da92ff0d743
-	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro   quiet splash
+	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=b7a0df33-53e4-4f0d-856b-0da92ff0d743 ro   
 	initrd	/boot/initrd.img-2.6.35-26-generic
 }
 menuentry "Ubuntu, with Linux 2.6.35-26-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
```

---

### Post by Gert Hulselmans on 2011-02-14
@ kansasnoob
I didn't saw your post #50, when I started with my post.
It took me to long to figure out the syntax for the "date" command :sad:.

I still don't have a copy of grub2 (v1.99) installed in the partition boot sector (or I lost it).

---

### Post by kansasnoob on 2011-02-15
> **Gert Hulselmans said:**
> @ kansasnoob
I didn't saw your post #50, when I started with my post.
It took me to long to figure out the syntax for the "date" command :sad:.

I still don't have a copy of grub2 (v1.99) installed in the partition boot sector (or I lost it).

Just to be clear, you need the output of:

```
sudo dd if=/dev/sdXY of=sdXY_63sectors.bin count=63 bs=512
```

Where "XY" are the proper disc/partition designations of the partition the latest version of grub2 is installed in? 

I plan on retesting everything one last time anyway with Natty, Maverick, and Lucid just to be sure the changes we made to accommodate older versions had no unexpected consequences that I've overlooked.

I'll be out for a while but I'll then check back on this.

---

### Post by Gert Hulselmans on 2011-02-15
> **kansasnoob said:**
> Just to be clear, you need the output of:

```
sudo dd if=/dev/sdXY of=sdXY_63sectors.bin count=63 bs=512
```Where "XY" are the proper disc/partition designations of the partition the latest version of grub2 is installed in? 

Yes

---

### Post by oldfred on 2011-02-15
The new boot_info_script still does not quite see gpt partitions correctly. I am not home to test, but I got one user to run both versions with a gpt drive and it gives this 

```
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1167360 of the same hard drive for core.img, but core.img can not be found 
    at this location..

```

But 1167360 is the start of the bios_boot partition. I think this is not the scripts issue, but the current tools available, as they do not see the gpt partition correctly.


[http://ubuntuforums.org/showthread.php?t=1686184](http://ubuntuforums.org/showthread.php?t=1686184)

---

### Post by Gert Hulselmans on 2011-02-15
@ kansasnoob

Can you run the last version of boot info script and compare the output with your previous run?
```
 sda1: __________________________________________________________________________
 
     File system:       ext3
-    Boot sector type:  Grub 1.97 - 1.98
+    Boot sector type:  Grub 1.97-1.98
     Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                        looks at sector 12587135 of the same hard drive for 
                        core.img, but core.img can not be found at this 
```I think the new version will show you the grub2 directory and partition for grub2, installed in a partition.

@ oldfred
It is a script issue.
It should be solved now (same problem as shown above).

---

### Post by kansasnoob on 2011-02-16
Sorry for the long delay. Here's the prior info requested in post #53:

[ATTACH]183632[/ATTACH]

This is the pertinent info for my sda14 (which I'm booted into now):

```
lance@lance-desktop:~$ grub-install -v
grub-install (GRUB) 1.99~rc1-2ubuntu1
lance@lance-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu natty (development branch)
Release:	11.04
Codename:	natty

```

I'll be back with more soon.

---

### Post by Rubi1200 on 2011-02-16
I just want to say thanks to Gert for all the hard work with these changes/improvements :-)

Quick question:

**must** gawk be installed for this to work?

I don't mind installing it, but are we to ask new users to do the same?

> "gawk" could not be found.

Please install the missing program(s) and run boot_info_script again.Thanks.

---

### Post by Gert Hulselmans on 2011-02-16
@ Rubi1200
yes, gawk is required.
mawk has bugs and as long as Ubuntu doesn't update to the last version, it is very unreliable:
[https://bugs.launchpad.net/ubuntu/source/mawk/+bug/716920/](https://bugs.launchpad.net/ubuntu/source/mawk/+bug/716920/)

---

### Post by oldfred on 2011-02-16
While my gpt drive is home, I had forgotten I had a full install of Maverick on my gpt flash drive. I just installed Natty to it. Not everything is fully set up on the flash drive to be optimal for a flash drive yet, but it boots. Script was run from Natty with gpt partitions on sdb, the flash drive.


```

                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #5 for (,msdos5)/boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 2048 
    of the same hard drive for core.img, core.img is at this location on 
    /dev/sdb and looks for 8ae..

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Grub2's core.img
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   113,595,614   113,595,552   7 NTFS / exFAT / HPFS
/dev/sda2         113,595,615   175,028,174    61,432,560   7 NTFS / exFAT / HPFS
/dev/sda3         175,028,236   312,062,624   137,034,389   5 Extended
/dev/sda5         175,028,238   205,744,454    30,716,217  83 Linux
/dev/sda6         205,744,518   211,881,284     6,136,767  82 Linux swap / Solaris
/dev/sda7         211,881,348   312,062,624   100,181,277  83 Linux
/dev/sda4         312,062,625   312,576,704       514,080  88 Linux plaintext


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.1 GB, 16064184320 bytes
255 heads, 63 sectors/track, 1953 cylinders, total 31375360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1    31,375,359    31,375,359  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048         4,095         2,048 BIOS Boot partition
/dev/sdb2           4,096    14,749,695    14,745,600 Data partition (Windows/Linux)
/dev/sdb3      14,749,696    31,373,311    16,623,616 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        D0782DE7782DCCD2                       ntfs       SQ004224P01
/dev/sda2        2A87EC53669130A9                       ntfs       shared
/dev/sda5        f2e3d649-d0cf-4ac8-b617-b7842dcbc011   ext4       
/dev/sda6        305abe8d-52fd-4ef1-be0a-9dedc417a1be   swap       
/dev/sda7        defec4d7-3e36-4938-b5de-b2016b2dee27   ext3       data
/dev/sdb2        0c3d1ba0-bf7d-40be-9cb4-db9d2572b34c   ext4       
/dev/sdb3        4215f5b3-ce4c-4ef8-bc1a-0daac816fb75   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /media/f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7        /media/data              ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb3        /media/4215f5b3-ce4c-4ef8-bc1a-0daac816fb75 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set f2e3d649-d0cf-4ac8-b617-b7842dcbc011
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set f2e3d649-d0cf-4ac8-b617-b7842dcbc011
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d0782de7782dccd2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.34-5-generic (on /dev/sdb2)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt2)'
    search --no-floppy --fs-uuid --set df55e8d0-c6c1-4a57-a283-73d7c07a927d
    linux /boot/vmlinuz-2.6.34-5-generic root=UUID=df55e8d0-c6c1-4a57-a283-73d7c07a927d ro quiet splash
    initrd /boot/initrd.img-2.6.34-5-generic
}
menuentry "Ubuntu, with Linux 2.6.34-5-generic (recovery mode) (on /dev/sdb2)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt2)'
    search --no-floppy --fs-uuid --set df55e8d0-c6c1-4a57-a283-73d7c07a927d
    linux /boot/vmlinuz-2.6.34-5-generic root=UUID=df55e8d0-c6c1-4a57-a283-73d7c07a927d ro single
    initrd /boot/initrd.img-2.6.34-5-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Ubuntu 11.04 Natty 64bit" {
    set isofile="/mnt/data/ISO/natty-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=305abe8d-52fd-4ef1-be0a-9dedc417a1be none            swap    sw              0       0
# Entry for /dev/sda7 :
UUID=defec4d7-3e36-4938-b5de-b2016b2dee27 /mnt/data ext3 auto,users,rw,relatime 0 2
# Entry for /dev/sda1 :
UUID=D0782DE7782DCCD2 /mnt/cdrive ntfs-3g defaults 0 0
# Entry for /dev/sda2 :
UUID=2A87EC53669130A9 /mnt/shared ntfs-3g defaults 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  96.301455498 = 103.402900480  boot/grub/core.img                             1
  88.484351158 = 95.009348608   boot/grub/grub.cfg                             1
  84.349814415 = 90.569923584   boot/initrd.img-2.6.35-22-generic              2
  86.841208458 = 93.245037568   boot/initrd.img-2.6.35-23-generic              2
  84.989966393 = 91.257281536   boot/initrd.img-2.6.35-24-generic              2
  89.229121208 = 95.809039360   boot/initrd.img-2.6.35-25-generic              2
  96.339007378 = 103.443221504  boot/vmlinuz-2.6.35-22-generic                 1
  96.343047142 = 103.447559168  boot/vmlinuz-2.6.35-23-generic                 1
  97.655459404 = 104.856751104  boot/vmlinuz-2.6.35-24-generic                 1
  96.549769402 = 103.669525504  boot/vmlinuz-2.6.35-25-generic                 1
  89.229121208 = 95.809039360   initrd.img                                     2
  84.989966393 = 91.257281536   initrd.img.old                                 2
  96.549769402 = 103.669525504  vmlinuz                                        1
  97.655459404 = 104.856751104  vmlinuz.old                                    1

=========================== sdb2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt2)'
search --no-floppy --fs-uuid --set=root 0c3d1ba0-bf7d-40be-9cb4-db9d2572b34c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sdb,gpt2)'
search --no-floppy --fs-uuid --set=root 0c3d1ba0-bf7d-40be-9cb4-db9d2572b34c
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt2)'
    search --no-floppy --fs-uuid --set=root 0c3d1ba0-bf7d-40be-9cb4-db9d2572b34c
    linux    /boot/vmlinuz-2.6.38-3-generic root=UUID=0c3d1ba0-bf7d-40be-9cb4-db9d2572b34c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt2)'
    search --no-floppy --fs-uuid --set=root 0c3d1ba0-bf7d-40be-9cb4-db9d2572b34c
    echo    'Loading Linux 2.6.38-3-generic ...'
    linux    /boot/vmlinuz-2.6.38-3-generic root=UUID=0c3d1ba0-bf7d-40be-9cb4-db9d2572b34c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-3-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt2)'
    search --no-floppy --fs-uuid --set=root 0c3d1ba0-bf7d-40be-9cb4-db9d2572b34c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sdb,gpt2)'
    search --no-floppy --fs-uuid --set=root 0c3d1ba0-bf7d-40be-9cb4-db9d2572b34c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root D0782DE7782DCCD2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f2e3d649-d0cf-4ac8-b617-b7842dcbc011
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=0c3d1ba0-bf7d-40be-9cb4-db9d2572b34c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=305abe8d-52fd-4ef1-be0a-9dedc417a1be none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   1.140407562 = 1.224503296    boot/grub/core.img                             1
   1.141120911 = 1.225269248    boot/grub/grub.cfg                             1
   3.158073425 = 3.390955520    boot/initrd.img-2.6.38-3-generic               2
   1.170211792 = 1.256505344    boot/vmlinuz-2.6.38-3-generic                  1
   3.158073425 = 3.390955520    initrd.img                                     2
   1.170211792 = 1.256505344    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  34 f4 7d f6 fb 21 3d 82  cc 33 0b 4c 1f 94 ca fd  |4.}..!=..3.L....|
00000010  c1 dc f2 61 cc 75 82 93  99 66 cb f1 6a cc 3a 66  |...a.u...f..j.:f|
00000020  b4 52 10 3f 46 02 12 10  9a e3 ec 96 2b 4e b8 e2  |.R.?F.......+N..|
00000030  0b 75 0c b3 20 fd 31 ca  f9 23 4c 78 d0 9c f0 53  |.u.. .1..#Lx...S|
00000040  92 a2 9d fd 89 94 64 58  ee 79 31 f3 06 4f 13 d5  |......dX.y1..O..|
00000050  a0 4e 4b ba cc de 2e a5  b2 02 03 b5 a2 56 e1 bb  |.NK..........V..|
00000060  bf b6 58 96 5d bb c5 48  78 bb e1 76 58 3a 6f 73  |..X.]..Hx..vX:os|
00000070  0d 51 5a d5 e6 3d 20 af  9f 6f c8 04 fc f1 82 33  |.QZ..= ..o.....3|
00000080  fe f5 cc b0 41 34 89 57  cb 01 20 11 6c 30 2a d7  |....A4.W.. .l0*.|
00000090  bc a3 0a 60 13 b7 18 6a  21 24 a6 8a ca 7e c6 21  |...`...j!$...~.!|
000000a0  bd 6f c0 0b f2 99 f3 0d  3a 82 a4 20 85 72 ec c4  |.o......:.. .r..|
000000b0  b2 32 23 04 16 34 ef 08  51 12 c3 9a 8f 33 4e 31  |.2#..4..Q....3N1|
000000c0  7c 1c 70 2c 79 fa c8 c3  58 65 78 37 f0 47 1f 11  ||.p,y...Xex7.G..|
000000d0  94 86 fe ba 02 90 d8 b4  2a 0c 6f 94 2f f8 94 6c  |........*.o./..l|
000000e0  11 41 a0 f4 02 f8 a5 e3  6d 66 ca c9 49 c5 77 cb  |.A......mf..I.w.|
000000f0  d3 4c 66 bf 52 0d 4a 8d  b7 17 c3 49 5b 27 16 43  |.Lf.R.J....I['.C|
00000100  bb d4 16 4a 06 88 f7 70  a2 41 a0 43 66 e1 fe 83  |...J...p.A.Cf...|
00000110  59 87 ed 22 a8 88 13 d5  02 b4 4c 8a 6d f6 cb c6  |Y.."......L.m...|
00000120  2d ec de fe d5 a9 68 6f  01 de 74 68 01 d7 03 ad  |-.....ho..th....|
00000130  df 8b 38 50 f5 b3 6d 4d  65 e8 02 80 27 03 54 35  |..8P..mMe...'.T5|
00000140  17 64 77 18 33 da 36 b2  9b 54 8f 03 85 20 76 20  |.dw.3.6..T... v |
00000150  0d 0d ad 76 94 10 07 c9  36 60 a5 89 7c 98 c0 0b  |...v....6`..|...|
00000160  c5 2f 59 6d eb 21 ff 04  c6 f5 24 ab 0f 85 be a5  |./Ym.!....$.....|
00000170  28 eb fa 83 8d e0 e9 63  b0 50 7f 3f 55 2d f7 e1  |(......c.P.?U-..|
00000180  18 31 44 b0 e4 af ec 98  72 04 83 1f c2 d8 70 e3  |.1D.....r.....p.|
00000190  38 66 dd 79 0f 7a 97 8e  ee 1b a9 a0 d7 fe 07 37  |8f.y.z.........7|
000001a0  e1 70 f3 77 9b c3 f5 fd  4c 5f a3 21 38 8b 19 73  |.p.w....L_.!8..s|
000001b0  3e b3 9b 0e 6c 9c 50 31  eb ef a9 0f d4 5e 00 fe  |>...l.P1.....^..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 39 b1 d4 01 00 fe  |..........9.....|
000001d0  ff ff 05 fe ff ff 3b b1  d4 01 fe a3 5d 00 00 00  |......;.....]...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda4

00000000  26 0d 43 41 a0 4b e1 72  f2 27 f3 20 e9 64 e5 61  |&.CA.K.r.'. .d.a|
00000010  cd 45 d3 41 a0 4b e1 72  f2 27 f3 20 e9 64 e5 61  |.E.A.K.r.'. .d.a|
*
00000030  cd 45 d3 41 a0 4b e1 72  f2 27 f3 20 e9 64 e6 63  |.E.A.K.r.'. .d.c|
00000040  32 45 d3 61 41 31 41 76  f2 25 09 a0 23 e4 0f 32  |2E.aA1Av.%..#..2|
00000050  b1 45 d3 70 60 c5 39 fc  22 9b f3 00 12 c4 a5 1d  |.E.p`.9.".......|
00000060  f1 ba a7 43 28 89 b3 84  30 a7 87 74 5d 25 5e cb  |...C(...0..t]%^.|
00000070  98 88 c0 1b f2 39 a8 f3  09 72 59 55 aa c4 a4 1d  |.....9...rYU....|
00000080  49 85 a6 44 23 aa e0 06  c5 41 78 6c f9 da e0 1d  |I..D#....Axl....|
00000090  0b 01 2c 40 c6 c0 ff 36  8e e0 f7 30 e9 a3 a1 63  |..,@...6...0...c|
000000a0  cc 45 b5 c8 fc 43 26 36  f4 27 83 46 d8 a4 6c 25  |.E...C&6.'.F..l%|
000000b0  c9 23 5a 05 ac ff a3 bf  e1 55 f6 9b e9 14 0e 1c  |.#Z......U......|
000000c0  79 4d 1e 52 d3 41 17 b0  72 28 77 d6 e9 8d 62 61  |yM.R.A..r(w...ba|
000000d0  73 40 af 87 e4 b4 e1 14  c3 e7 7b d0 a9 02 6c 25  |s@........{...l%|
000000e0  c9 74 01 c9 6a 8a 03 70  7a cf 7b d4 a9 ed a1 69  |.t..j..pz.{....i|
000000f0  fc 85 5b 91 60 a3 e3 14  7b 23 95 81 ad 18 83 50  |..[.`...{#.....P|
00000100  1f 23 24 75 28 1f eb 14  c3 f5 95 d7 9d 60 6d 35  |.#$u(........`m5|
00000110  c6 cc 97 4d 9b 0f e9 0f  ce ad a7 2d 29 86 e3 eb  |...M.......-)...|
00000120  81 4f 2d 80 a8 9a 6b 1e  fe 7d 79 54 e2 df e5 11  |.O-...k..}yT....|
00000130  43 86 e2 9a 18 4a e3 bf  e1 55 ed ac 2a ea e3 29  |C....J...U..*..)|
00000140  b1 25 cd f8 a0 4a 6f a9  c3 d1 c2 df 15 97 40 7e  |.%...Jo.......@~|
00000150  ac ba f5 03 dc a0 e3 99  f2 cc 0d 67 bb 31 a7 41  |...........g.1.A|
00000160  cd 02 b6 2e cd 4b a9 13  80 43 d3 64 80 17 8e 61  |.....K...C.d...a|
00000170  9f 20 b2 25 a0 6b a4 00  80 48 81 20 45 58 e5 14  |. .%.k...H. EX..|
00000180  36 86 d3 41 a0 4b e1 72  f2 27 f3 20 e9 64 e5 61  |6..A.K.r.'. .d.a|
00000190  cd 45 d3 41 a0 4b e1 72  f2 27 f3 20 e9 64 e5 61  |.E.A.K.r.'. .d.a|
*
000001f0  cd 45 d3 41 a0 4b e1 72  f2 27 f3 20 e9 64 b0 cb  |.E.A.K.r.'. .d..|
00000200



```

---

### Post by Rubi1200 on 2011-02-16
Thanks Gert.

Keep up the good work; it is much appreciated :-)

---

### Post by kansasnoob on 2011-02-16
This is the only thing I see not 100% correct with the newest version:

```
sda12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:  **[COLOR="Red"]Grub Legacy (v)[/COLOR]** is installed in the boot sector of 
                       sda12 and looks at sector 507466884 of the same hard 
                       drive for the stage2 file, but no stage2 files can be 
                       found at this location.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

```

And that's the Hardy to Lucid upgrade I just performed which still has legacy grub. I'll have to get back to you about the specific version of legacy grub. As far I'm concerned that's very minor.

I had a bit of a problem finding the last "new" version I used but it's properties show it was last updated, "Mon 14 Feb 2011 05:26:47 AM CST". That brings me to a request that would make things a bit easier for me while we're working with this.

Would it be possible to change this without altering the function of the script:

```
#!/bin/bash
VERSION='**[COLOR="Red"]0.56[/COLOR]**';
DATE='8 February 2011';
```

To something like this:

```
#!/bin/bash
VERSION='**[COLOR="Red"]0.56.1[/COLOR]**';
DATE='8 February 2011';
```

Notice I just added a ".1" so we testers and you could more easily communicate which version we're testing/comparing. So if the next version said 0.56.1 and each version beyond that "jumped" it would be easier to understand while we're testing. Then when we're done the last digit could be dropped altogether and if more changes are needed we could then jump to 0.57, does that make sense :)

Regardless here are the latest results:

[ATTACH]183645[/ATTACH]

[ATTACH]183646[/ATTACH]

[ATTACH]183647[/ATTACH]

The only changes I see were created by me. I needed to relabel to differentiate between installations while using Nautilus:

```
--- RESULTS_0214_056.txt	2011-02-16 14:48:53.893824219 -0600
+++ RESULTS_newest_056.txt	2011-02-16 12:14:53.977827150 -0600
@@ -244,7 +244,7 @@
 
 Device           UUID                                   TYPE       LABEL
 
-/dev/sda1        b7a0df33-53e4-4f0d-856b-0da92ff0d743   ext3       Maverick-sda1
+/dev/sda1        b7a0df33-53e4-4f0d-856b-0da92ff0d743   ext3       Maverick
 /dev/sda10       6114df72-5fec-467a-b6cf-bfb49b76def1   ext4       Mint Julia
 /dev/sda11       ed0bdce8-0af8-4cce-9933-cbac8389fe4d   ext4       Squeeze
 /dev/sda12       96bef601-3776-4e41-bf5a-ca81d3e5058d   ext3       HH to LL
@@ -253,7 +253,7 @@
 /dev/sda15       22eefad4-870e-4191-87c9-57f4e756411d   ext4       LMDE
 /dev/sda16       7a90aa0c-2377-48e4-97ad-20283c962abc   ext4       Natty
 /dev/sda17       d70bbade-c57d-4c81-84e1-7674021673d6   ext4       MM to NN A1
-/dev/sda18       ff93a40e-f9a6-4864-b3f2-0f357263f689   ext4       Maverick-sda18
+/dev/sda18       ff93a40e-f9a6-4864-b3f2-0f357263f689   ext4       Maverick
 /dev/sda2        1332b9d0-cf18-4299-9094-12acbdac91ad   ext3       KK to LL
 /dev/sda3        d252929b-949d-432e-a18c-18f9ae770d28   ext3       Lucid
 /dev/sda5        594c3d40-2791-4c0a-8644-d9812545da2d   ext3       Backups
```

---

### Post by kansasnoob on 2011-02-16
@ oldfred,

Glad to see you join the party :D

I don't have anything "gpt" to test.

---

### Post by VMC on 2011-02-16
> **Gert Hulselmans said:**
> @ Rubi1200
yes, gawk is required.
mawk has bugs and as long as Ubuntu doesn't update to the last version, it is very unreliable:
[https://bugs.launchpad.net/ubuntu/source/mawk/+bug/716920/](https://bugs.launchpad.net/ubuntu/source/mawk/+bug/716920/)

Have you tried using busybox's awk? If it works you can just link to it through busybox.

---

### Post by Gert Hulselmans on 2011-02-16
@ kansasnoob
Can you post the output of:
```
filefrag -v /media/sda1/boot/grub/core.img
filefrag -v /media/sda3/boot/grub/core.img
```
(Just want to be sure that the grub2 install on those partitions is indeed broken.)

Can you post the bootsector of sda12?

@ oldfred
BIOS Boot partition detection check is fixed. Can you post the diff between your last report and a new report?
```
diff -u RESULTS-old.txt RESULTS-new.txt
```

---

### Post by kansasnoob on 2011-02-16
Since last posting I booted into my Maverick/10.10 to get some work done and I applied these updates:

```
Commit Log for Tue Feb 15 01:56:29 2011


Upgraded the following packages:
libgssapi-krb5-2 (1.8.1+dfsg-5ubuntu0.2) to 1.8.1+dfsg-5ubuntu0.4
libk5crypto3 (1.8.1+dfsg-5ubuntu0.2) to 1.8.1+dfsg-5ubuntu0.4
libkrb5-3 (1.8.1+dfsg-5ubuntu0.2) to 1.8.1+dfsg-5ubuntu0.4
libkrb5support0 (1.8.1+dfsg-5ubuntu0.2) to 1.8.1+dfsg-5ubuntu0.4
tzdata (2010o-0ubuntu0.10.10) to 2011b-0ubuntu0.10.10
tzdata-java (2010o-0ubuntu0.10.10) to 2011b-0ubuntu0.10.10

```

Not sure what effect that might have but I'm now running those commands from my updated Maverick on sda1:

```
lance@lance-desktop:~$ filefrag -v /media/sda1/boot/grub/core.img
open: No such file or directory
lance@lance-desktop:~$ filefrag -v /media/sda3/boot/grub/core.img
open: No such file or directory

```

[ATTACH]183657[/ATTACH]

---

### Post by Gert Hulselmans on 2011-02-16
@ kansasnoob
Replace /media/sda1/ with the path where sda1 is mounted: probably /media/Maverick-sda1/.
Similar for sda3.

---

### Post by oldfred on 2011-02-16
Glad I can help with testing on a gpt partitioned drive. I also really appreciate Gert's work on the script as I have learned to rely on it for solving boot & some other issues.

I have three results. The first one posted above. A second one based on the couple of lines of changes, & a third where I downloaded a new copy of boot info script.

Diff of original to minor edits in script:

```

fred@fred-Satellite-A105:~$ diff -u RESULTS.txt RESULTS1.txt
--- RESULTS.txt    2011-02-16 14:22:00.289525038 -0500
+++ RESULTS1.txt    2011-02-16 17:00:58.284009435 -0500
@@ -11,6 +11,7 @@
 
 sda1: __________________________________________________________________________
 
+    System:            NTFS / exFAT / HPFS
     File system:       ntfs
     Boot sector type:  Windows XP
     Boot sector info:  No errors found in the Boot Parameter Block.
@@ -19,6 +20,7 @@
 
 sda2: __________________________________________________________________________
 
+    System:            NTFS / exFAT / HPFS
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
@@ -27,12 +29,14 @@
 
 sda3: __________________________________________________________________________
 
+    System:            Extended
     File system:       Extended Partition
     Boot sector type:  Unknown
     Boot sector info:  
 
 sda5: __________________________________________________________________________
 
+    System:            Linux
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
@@ -41,12 +45,14 @@
 
 sda6: __________________________________________________________________________
 
+    System:            Linux swap / Solaris
     File system:       swap
     Boot sector type:  -
     Boot sector info:  
 
 sda7: __________________________________________________________________________
 
+    System:            Linux
     File system:       ext3
     Boot sector type:  -
     Boot sector info:  
@@ -55,6 +61,7 @@
 
 sda4: __________________________________________________________________________
 
+    System:            Linux plaintext
     File system:       
     Boot sector type:  Unknown
     Boot sector info:  
@@ -62,6 +69,7 @@
 
 sdb1: __________________________________________________________________________
 
+    System:            BIOS Boot partition
     File system:       
     Boot sector type:  Grub2's core.img
     Boot sector info:  
@@ -70,6 +78,7 @@
 
 sdb2: __________________________________________________________________________
 
+    System:            Data partition (Windows/Linux)
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
@@ -79,6 +88,7 @@
 
 sdb3: __________________________________________________________________________
 
+    System:            Data partition (Windows/Linux)
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
@@ -134,16 +144,14 @@
 /dev/sda6        305abe8d-52fd-4ef1-be0a-9dedc417a1be   swap       
 /dev/sda7        defec4d7-3e36-4938-b5de-b2016b2dee27   ext3       data
 /dev/sdb2        0c3d1ba0-bf7d-40be-9cb4-db9d2572b34c   ext4       
-/dev/sdb3        4215f5b3-ce4c-4ef8-bc1a-0daac816fb75   ext4       
+/dev/sdb3        4215f5b3-ce4c-4ef8-bc1a-0daac816fb75   ext4       KingstonData
 
 ================================ Mount points: =================================
 
 Device           Mount_Point              Type       Options
 
-/dev/sda5        /media/f2e3d649-d0cf-4ac8-b617-b7842dcbc011 ext4       (rw,nosuid,nodev,uhelper=udisks)
-/dev/sda7        /media/data              ext3       (rw,nosuid,nodev,uhelper=udisks)
-/dev/sdb2        /                        ext4       (rw,errors=remount-ro,commit=0)
-/dev/sdb3        /media/4215f5b3-ce4c-4ef8-bc1a-0daac816fb75 ext4       (rw,nosuid,nodev,uhelper=udisks)
+/dev/sdb2        /                        ext4       (rw,noatime,errors=remount-ro,commit=0)
+/dev/sdb3        /media/KingstonData      ext4       (rw,nosuid,nodev,uhelper=udisks)
 
 
 ================================ sda1/boot.ini: ================================
@@ -657,9 +665,10 @@
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc            /proc           proc    nodev,noexec,nosuid 0       0
 # / was on /dev/sdb2 during installation
-UUID=0c3d1ba0-bf7d-40be-9cb4-db9d2572b34c /               ext4    errors=remount-ro 0       1
+UUID=0c3d1ba0-bf7d-40be-9cb4-db9d2572b34c /               ext4    noatime,errors=remount-ro 0       1
 # swap was on /dev/sda6 during installation
 UUID=305abe8d-52fd-4ef1-be0a-9dedc417a1be none            swap    sw              0       0
+#LABEL=KingstonData /mnt/KingstonData ext4 auto,users,rw,noatime 0 02
 --------------------------------------------------------------------------------


```Diff of results with minor edit and one based on most recent download:
```

fred@fred-Satellite-A105:~$ diff -u RESULTS1.txt RESULTS2.txt--- RESULTS1.txt    2011-02-16 17:00:58.284009435 -0500
+++ RESULTS2.txt    2011-02-16 17:12:21.585011621 -0500
@@ -11,7 +11,6 @@
 
 sda1: __________________________________________________________________________
 
-    System:            NTFS / exFAT / HPFS
     File system:       ntfs
     Boot sector type:  Windows XP
     Boot sector info:  No errors found in the Boot Parameter Block.
@@ -20,7 +19,6 @@
 
 sda2: __________________________________________________________________________
 
-    System:            NTFS / exFAT / HPFS
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
@@ -29,14 +27,12 @@
 
 sda3: __________________________________________________________________________
 
-    System:            Extended
     File system:       Extended Partition
     Boot sector type:  Unknown
     Boot sector info:  
 
 sda5: __________________________________________________________________________
 
-    System:            Linux
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
@@ -45,14 +41,12 @@
 
 sda6: __________________________________________________________________________
 
-    System:            Linux swap / Solaris
     File system:       swap
     Boot sector type:  -
     Boot sector info:  
 
 sda7: __________________________________________________________________________
 
-    System:            Linux
     File system:       ext3
     Boot sector type:  -
     Boot sector info:  
@@ -61,7 +55,6 @@
 
 sda4: __________________________________________________________________________
 
-    System:            Linux plaintext
     File system:       
     Boot sector type:  Unknown
     Boot sector info:  
@@ -69,16 +62,12 @@
 
 sdb1: __________________________________________________________________________
 
-    System:            BIOS Boot partition
-    File system:       
+    File system:       BIOS Boot partition
     Boot sector type:  Grub2's core.img
     Boot sector info:  
-    Mounting failed:   mount: unknown filesystem type ''
-mount: unknown filesystem type ''
 
 sdb2: __________________________________________________________________________
 
-    System:            Data partition (Windows/Linux)
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
@@ -88,7 +77,6 @@
 
 sdb3: __________________________________________________________________________
 
-    System:            Data partition (Windows/Linux)
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
fred@fred-Satellite-A105:~$ 



```

---

### Post by kansasnoob on 2011-02-16
I think I already told you I'm not the sharpest tool in the drawer ;)

```
lance@lance-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             41657636   5104184  34437172  13% /
none                   1019588       300   1019288   1% /dev
none                   1025192       128   1025064   1% /dev/shm
none                   1025192        92   1025100   1% /var/run
none                   1025192         0   1025192   0% /var/lock
/dev/sda5             52980472   2426280  47862936   5% /mnt/sda5
/dev/sda6             51565272    895720  48050184   2% /mnt/sda6
/dev/sda7             52797780  35123328  14992412  71% /mnt/sda7
/dev/sda8             10305924     99756   9682872   2% /mnt/sda8
lance@lance-desktop:~$ filefrag -v /sda1/boot/grub/core.img
open: No such file or directory
lance@lance-desktop:~$ filefrag -v /boot/grub/core.img
Filesystem type is: ef53
Filesystem cylinder groups is approximately 318
File size of /boot/grub/core.img is 23817 (6 blocks, blocksize 4096)
 ext logical physical expected length flags
   0       0  1587248               3 merged
   1       3  1587856  1587250      3 merged,eof
/boot/grub/core.img: 2 extents found, perfection would be 1 extent

```

I'll do sda3 next.

---

### Post by kansasnoob on 2011-02-16
Hope this works:

```
lance@lance-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             41657636   5104768  34436588  13% /
none                   1019588       300   1019288   1% /dev
none                   1025192       176   1025016   1% /dev/shm
none                   1025192        92   1025100   1% /var/run
none                   1025192         0   1025192   0% /var/lock
/dev/sda5             52980472   2426280  47862936   5% /mnt/sda5
/dev/sda6             51565272    895720  48050184   2% /mnt/sda6
/dev/sda7             52797780  35123328  14992412  71% /mnt/sda7
/dev/sda8             10305924     99756   9682872   2% /mnt/sda8
**/dev/sda3             41357836   5152556  34104388  14% [COLOR="Red"]/media/Lucid[/COLOR]**
lance@lance-desktop:~$ filefrag -v /media/Lucid/boot/grub/core.img
Filesystem type is: ef53
Filesystem cylinder groups is approximately 316
File size of /media/Lucid/boot/grub/core.img is 23817 (6 blocks, blocksize 4096)
 ext logical physical expected length flags
   0       0   172032               5 merged
   1       5   172037               1 merged,eof
/media/Lucid/boot/grub/core.img: 1 extent found

```

---

### Post by Gert Hulselmans on 2011-02-16
@ kansasnoob
Grub2 (v1.97-1.98) is broken for sda1 and sda3, so the script works correctly.

@ oldfred
Output is fine now.

---

### Post by kansasnoob on 2011-02-16
I don't doubt that it's "broken". I fiddle a lot, but it does work to boot with.

I've been playing with things in both Lucid on sda3 and Maverick on sda1 to work-around what I think are either plymouth or ureadahead problems.

---

### Post by Gert Hulselmans on 2011-02-16
@ kansasnoob:
```
sudo dd if=/dev/sda of=floating_core-1.98.bin skip=12587135 bs=512 count=63
```

---

### Post by srs5694 on 2011-02-16
If you're collecting data on your script's ability to parse GPT data, here are three examples.

First, here's what I get on a Gentoo system with a single GPT disk:

```

                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    976768065 of the same hard drive for core.img, but core.img can not be 
    found at this location..

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Boot file info:      Grub Legacy (v) in the file /hdb.mbr looks at sector 
                       1 on boot drive #1 for the stage2 file, but no stage2 
                       files can be found at this location.
    Operating System:  
    Boot files:        /grub/menu.lst /boot/grub/menu.lst /grub/grub.cfg 
                       /boot/grub/grub.cfg /grub/grub.conf 
                       /boot/grub/grub.conf /grub/core.img /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Boot file info:      Grub Legacy (v0.97) in the file /sda-gpt.img looks at 
                       sector 1126836 of the same hard drive for the stage2 
                       file.  A stage2 file is at this location on /dev/sda.  
                       Stage2 looks on partition #3 for /grub/menu.lst. Grub 
                       Legacy (v0.97) in the file /sda-mbr.img looks at 
                       sector 1126836 of the same hard drive for the stage2 
                       file.  A stage2 file is at this location on /dev/sda.  
                       Stage2 looks on partition #3 for /grub/menu.lst.
    Operating System:  
    Boot files:        /grub/menu.lst

sda4: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub 2's core.img
    Boot sector info:  

nessus-root': __________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

nessus-usr': ___________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

nessus-usrlocal': ______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

nessus-opt': ___________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

nessus-swap': __________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

nessus-home': __________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

nessus-emu': ___________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

nessus-g_root': ________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

nessus-g_opt': _________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

nessus-g_usr': _________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       390,625       390,592 Data partition (Windows/Linux)
/dev/sda2         390,626       803,249       412,624 Data partition (Windows/Linux)
/dev/sda3         803,250     1,212,850       409,601 Data partition (Windows/Linux)
/dev/sda4       1,212,851   976,768,064   975,555,214 Logical Volume Manager (LVM) partition (Linux)
/dev/sda5     976,768,065   976,768,464           400 BIOS Boot partition

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/nessus-emu dcb71faa-ed88-467c-abbf-3d8b3d1e0849   reiserfs   
/dev/mapper/nessus-g_opt 85f3f363-781e-494d-beec-c45fe0309a17   reiserfs   
/dev/mapper/nessus-g_root 5f96cafa-e0a7-4057-b18f-fa709db5b837   reiserfs   
/dev/mapper/nessus-g_usr 580d3322-2ff8-4692-a964-be996c2e9929   reiserfs   
/dev/mapper/nessus-home 3a00a023-c58b-4dff-963a-365e399b5982   reiserfs   
/dev/mapper/nessus-opt 1ba43617-67ac-4858-8147-935ce8e172f5   ext3       
/dev/mapper/nessus-root 5edf77b1-6008-4a08-98a2-c2af7cf1dd87   reiserfs   
/dev/mapper/nessus-swap 90dfc155-fd37-4e73-a112-472ce434096c   swap       
/dev/mapper/nessus-usr 1d6a7af6-dc42-4aa0-8ce3-e78cb0036682   reiserfs   
/dev/mapper/nessus-usrlocal a139b90e-2f94-4378-bf66-fe7669808dbe   ext3       
/dev/sda1        f12ca6d0-40f1-416c-86fd-b65c934cc750   ext2       spare1
/dev/sda2        c607bd95-8edf-4eb1-aa93-12db8f0e66a2   ext2       spare2
/dev/sda3        e6683da7-bb14-451a-89f9-3636860d6da1   ext2       boot
/dev/sda4        F0FYTX-mtb3-b8Kw-WZ3I-AhB6-JG3l-yCXWkA LVM2_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
nessus-emu
nessus-g_opt
nessus-g_root
nessus-g_usr
nessus-home
nessus-opt
nessus-root
nessus-swap
nessus-usr
nessus-usrlocal

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/nessus-emu /other/emu               reiserfs   (rw,noatime)
/dev/mapper/nessus-g_opt /opt                     reiserfs   (rw,noatime)
/dev/mapper/nessus-g_root /                        reiserfs   (rw,noatime)
/dev/mapper/nessus-g_usr /usr                     reiserfs   (rw,noatime)
/dev/mapper/nessus-home /home                    reiserfs   (rw,noatime)
/dev/mapper/nessus-usrlocal /usr/local               ext3       (rw,noatime)
/dev/sda2        /boot                    ext2       (rw,noatime)


============================= sda2/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
insmod lvm
insmod reiserfs
set root='(nessus-g_usr)'
search --no-floppy --fs-uuid --set 580d3322-2ff8-4692-a964-be996c2e9929
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,2)'
search --no-floppy --fs-uuid --set c607bd95-8edf-4eb1-aa93-12db8f0e66a2
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Gentoo (2.6.37)" {
   set root=(hd0,2)
   linux /bzImage-2.6.37 ro root=/dev/mapper/nessus-g_root dolvm
   initrd /initramfs-genkernel-x86_64-2.6.37
}

menuentry "Gentoo (2.6.35.5)" {
   set root=(hd0,2)
   linux /bzImage-2.6.35.5 ro root=/dev/mapper/nessus-g_root dolvm
   initrd /initramfs-genkernel-x86_64-2.6.35.5
}

menuentry "Gentoo (2.6.32.3_fglrx)" {
   set root=(hd0,2)
   linux /bzImage-2.6.32.3_fglrx ro root=/dev/mapper/nessus-g_root dolvm
   initrd /initramfs-genkernel-x86_64-2.6.32.3_fglrx
}
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
insmod lvm
insmod reiserfs
set root='(nessus-g_usr)'
search --no-floppy --fs-uuid --set 580d3322-2ff8-4692-a964-be996c2e9929
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,2)'
search --no-floppy --fs-uuid --set c607bd95-8edf-4eb1-aa93-12db8f0e66a2
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Gentoo (2.6.37)" {
   set root=(hd0,2)
   linux /bzImage-2.6.37 ro root=/dev/mapper/nessus-g_root dolvm
   initrd /initramfs-genkernel-x86_64-2.6.37
}

menuentry "Gentoo (2.6.35.5)" {
   set root=(hd0,2)
   linux /bzImage-2.6.35.5 ro root=/dev/mapper/nessus-g_root dolvm
   initrd /initramfs-genkernel-x86_64-2.6.35.5
}

menuentry "Gentoo (2.6.32.3_fglrx)" {
   set root=(hd0,2)
   linux /bzImage-2.6.32.3_fglrx ro root=/dev/mapper/nessus-g_root dolvm
   initrd /initramfs-genkernel-x86_64-2.6.32.3_fglrx
}
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

============================= sda2/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# This is a sample grub.conf for use with Genkernel, per the Gentoo handbook
# http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2
# If you are not using Genkernel and you need help creating this file, you
# should consult the handbook. Alternatively, consult the grub.conf.sample that
# is included with the Grub documentation.

default 0
timeout 30
#splashimage=(hd0,0)/boot/grub/splash.xpm.gz

#title Gentoo Linux 2.6.24-r5
#root (hd0,0)
#kernel /boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/ram0 real_root=/dev/sda3
#initrd /boot/initramfs-genkernel-x86-2.6.24-gentoo-r5

# vim:ft=conf:
--------------------------------------------------------------------------------

========================== sda2/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# This is a sample grub.conf for use with Genkernel, per the Gentoo handbook
# http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2
# If you are not using Genkernel and you need help creating this file, you
# should consult the handbook. Alternatively, consult the grub.conf.sample that
# is included with the Grub documentation.

default 0
timeout 30
#splashimage=(hd0,0)/boot/grub/splash.xpm.gz

#title Gentoo Linux 2.6.24-r5
#root (hd0,0)
#kernel /boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/ram0 real_root=/dev/sda3
#initrd /boot/initramfs-genkernel-x86-2.6.24-gentoo-r5

# vim:ft=conf:
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.355725288 = 0.381957120    boot/grub/core.img                             2
   0.225819588 = 0.242471936    boot/grub/grub.cfg                             1
   0.246477127 = 0.264652800    boot/grub/grub.conf                            1
   0.246477127 = 0.264652800    boot/grub/menu.lst                             1
   0.227690697 = 0.244481024    boot/grub/stage2                               2
   0.216363907 = 0.232318976    boot/initramfs-genkernel-x86_64-2.6.27-gentoo-r7 88
   0.235127449 = 0.252466176    boot/initramfs-genkernel-x86_64-2.6.32.2      13
   0.265854836 = 0.285459456    boot/initramfs-genkernel-x86_64-2.6.35.4      17
   0.247988701 = 0.266275840    boot/initramfs-genkernel-x86_64-2.6.35.5      15
   0.225219727 = 0.241827840    boot/initramfs-genkernel-x86_64-2.6.37        14
   0.190713882 = 0.204777472    boot/initrd-2.6.27-gentoo-r7.img               5
   0.232145309 = 0.249264128    boot/initrd-2.6.32.2.img                       6
   0.355725288 = 0.381957120    grub/core.img                                  2
   0.225819588 = 0.242471936    grub/grub.cfg                                  1
   0.246477127 = 0.264652800    grub/grub.conf                                 1
   0.246477127 = 0.264652800    grub/menu.lst                                  1
   0.227690697 = 0.244481024    grub/stage2                                    2
   0.216363907 = 0.232318976    initramfs-genkernel-x86_64-2.6.27-gentoo-r7   88
   0.235127449 = 0.252466176    initramfs-genkernel-x86_64-2.6.32.2           13
   0.265854836 = 0.285459456    initramfs-genkernel-x86_64-2.6.35.4           17
   0.247988701 = 0.266275840    initramfs-genkernel-x86_64-2.6.35.5           15
   0.225219727 = 0.241827840    initramfs-genkernel-x86_64-2.6.37             14
   0.190713882 = 0.204777472    initrd-2.6.27-gentoo-r7.img                    5
   0.232145309 = 0.249264128    initrd-2.6.32.2.img                            6

============================= sda3/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

default        0
timeout        15

title        Gentoo, kernel 2.6.32.3_fglrx
root        (hd0,1)
kernel        /bzImage-2.6.32.3_fglrx root=/dev/mapper/nessus-g_root ro quiet splash dolvm
initrd        /initramfs-genkernel-x86_64-2.6.32.3_fglrx
quiet

title        Gentoo, kernel 2.6.32.3
root        (hd0,1)
kernel        /bzImage-2.6.32.3 root=/dev/mapper/nessus-g_root ro quiet splash dolvm
initrd        /initramfs-genkernel-x86_64-2.6.32.3
quiet

title        Ubuntu 8.04, kernel 2.6.30
root        (hd0,2)
kernel        /bzImage-2.6.30 root=/dev/mapper/nessus-root ro quiet splash
initrd        /initrd.img-2.6.30
quiet

title        Xen (Ubuntu 8.04, kernel 2.6.30)
root        (hd0,2)
kernel        /xen-3.2.gz dom0_mem=2097152 noreboot
module        /vmlinux-2.6.30 root=/dev/mapper/nessus-root ro quiet splash
module        /initrd.img-2.6.30
quiet

title        Ubuntu 8.04, kernel 2.6.28sb700
root        (hd0,2)
kernel        /bzImage-2.6.28sb700 root=/dev/mapper/nessus-root ro quiet splash
initrd        /initrd.img-2.6.28sb700
quiet

title        Ubuntu 8.04, kernel 2.6.28
root        (hd0,2)
kernel        /bzImage-2.6.28 root=/dev/mapper/nessus-root ro quiet splash vga=0x31a
initrd        /initrd.img-2.6.28
quiet

title        Ubuntu 8.04, kernel 2.6.25.2
root        (hd0,2)
kernel        /bzImage-2.6.25.2 root=/dev/mapper/nessus-root ro quiet splash
initrd        /initrd.img-2.6.25.2
quiet

title        Ubuntu 8.04, kernel 2.6.24-19-server
root        (hd0,2)
kernel        /vmlinuz-2.6.24-19-server root=/dev/mapper/nessus-root ro quiet splash
initrd        /initrd.img-2.6.24-19-server
quiet

title        Ubuntu 8.04, kernel 2.6.24-19-server (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.24-19-server root=/dev/mapper/nessus-root ro single
initrd        /initrd.img-2.6.24-19-server

title        Ubuntu 8.04, kernel 2.6.24-16-server
root        (hd0,2)
kernel        /vmlinuz-2.6.24-16-server root=/dev/mapper/nessus-root ro quiet splash
initrd        /initrd.img-2.6.24-16-server
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-server (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.24-16-server root=/dev/mapper/nessus-root ro single
initrd        /initrd.img-2.6.24-16-server

title        Ubuntu 8.04, memtest86+
root        (hd0,2)
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f3678608-6b77-4a9f-85d5-39277ec00af5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.465458870 = 0.499782656    grub/menu.lst                                  1
   0.537416458 = 0.577046528    grub/stage2                                    2
   0.455123901 = 0.488685568    initrd.img-2.6.24-22-server                   36
   0.409949303 = 0.440179712    initrd.img-2.6.24-22-server.bak               36
   0.476089478 = 0.511197184    initrd.img-2.6.24-23-server                   41
   0.478692055 = 0.513991680    initrd.img-2.6.24-23-server.bak               40
   0.546137810 = 0.586411008    initrd.img-2.6.24-24-server                   47
   0.533832550 = 0.573198336    initrd.img-2.6.24-24-server.bak               42
   0.572981834 = 0.615234560    initrd.img-2.6.24-26-server                   36
   0.578331947 = 0.620979200    initrd.img-2.6.24-26-server.bak               38
   0.431459427 = 0.463276032    initrd.img-2.6.25.2                           88
   0.436525345 = 0.468715520    initrd.img-2.6.28                             22
   0.465449333 = 0.499772416    initrd.img-2.6.28foo                          23
   0.441686630 = 0.474257408    initrd.img-2.6.28sb700                        27
   0.521818161 = 0.560297984    initrd.img-2.6.30                             22
   0.553030968 = 0.593812480    initrd.img-2.6.31.5                           20
   0.446518898 = 0.479446016    vmlinuz-2.6.24-22-server                      10
   0.385822296 = 0.414273536    vmlinuz-2.6.24-23-server                       9
   0.525212288 = 0.563942400    vmlinuz-2.6.24-24-server                      10
   0.554463387 = 0.595350528    vmlinuz-2.6.24-26-server                      10

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on nessus-root'


Unknown BootLoader on nessus-usr'


Unknown BootLoader on nessus-usrlocal'


Unknown BootLoader on nessus-opt'


Unknown BootLoader on nessus-swap'


Unknown BootLoader on nessus-home'


Unknown BootLoader on nessus-emu'


Unknown BootLoader on nessus-g_root'


Unknown BootLoader on nessus-g_opt'


Unknown BootLoader on nessus-g_usr'



========= Devices which don't seem to have a corresponding hard drive: =========

sdb No RAID disks 

=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/nessus-root': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/nessus-root': No such file or directory
hexdump: /dev/mapper/nessus-root': Bad file descriptor
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/nessus-usr': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/nessus-usr': No such file or directory
hexdump: /dev/mapper/nessus-usr': Bad file descriptor
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/nessus-usrlocal': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/nessus-usrlocal': No such file or directory
hexdump: /dev/mapper/nessus-usrlocal': Bad file descriptor
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/nessus-opt': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/nessus-opt': No such file or directory
hexdump: /dev/mapper/nessus-opt': Bad file descriptor
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/nessus-swap': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/nessus-swap': No such file or directory
hexdump: /dev/mapper/nessus-swap': Bad file descriptor
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/nessus-home': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/nessus-home': No such file or directory
hexdump: /dev/mapper/nessus-home': Bad file descriptor
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/nessus-emu': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/nessus-emu': No such file or directory
hexdump: /dev/mapper/nessus-emu': Bad file descriptor
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/nessus-g_root': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/nessus-g_root': No such file or directory
hexdump: /dev/mapper/nessus-g_root': Bad file descriptor
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/nessus-g_opt': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/nessus-g_opt': No such file or directory
hexdump: /dev/mapper/nessus-g_opt': Bad file descriptor
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/nessus-g_usr': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/nessus-g_usr': No such file or directory
hexdump: /dev/mapper/nessus-g_usr': Bad file descriptor
mdadm: No arrays found in config file or automatically

```

Next up is an Ubuntu 9.10 system with a GPT /dev/sda and an MBR /dev/sdb:

```

                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    40 of the same hard drive for core.img, but core.img can not be found at 
    this location..
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #1 for /grub.

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub 2's core.img
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 440.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

seeker-mythtv': ________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

seeker-ma_log': ________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

seeker-ubuntu910_root': ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

seeker-ubuntu910_usr': _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

seeker-ubuntu910_var': _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

seeker-swap': __________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              40           439           400 BIOS Boot partition
/dev/sda2             440       410,039       409,600 EFI System partition
/dev/sda3         410,040       819,639       409,600 Data partition (Windows/Linux)
/dev/sda4         819,640     1,229,239       409,600 Data partition (Windows/Linux)
/dev/sda5       1,229,240 1,953,525,134 1,952,295,895 Logical Volume Manager (LVM) partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00022117

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63       192,779       192,717  83 Linux
/dev/sdb2           1,012,095   625,137,344   624,125,250  8e Linux LVM
/dev/sdb3             192,780     1,012,094       819,315  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/seeker-ma_log 28058c9f-a6fe-4089-8abd-bd41854267cc   reiserfs   
/dev/mapper/seeker-mythtv 284c14ab-c87f-4180-87a6-7332f412f2bf   xfs        
/dev/mapper/seeker-swap 3a057e10-ce78-4bc1-a7a9-e465119b9021   swap       
/dev/mapper/seeker-ubuntu910_root e238fbcf-0943-404c-98ab-da5d210f8acb   reiserfs   u910_root
/dev/mapper/seeker-ubuntu910_usr d6b00e86-b7c8-4c89-b54a-365343977f9e   reiserfs   u910_usr
/dev/mapper/seeker-ubuntu910_var 740ec23a-bb47-4e6b-8476-b7889d94150e   reiserfs   u910_var
/dev/sda2        FF27-F452                              vfat       
/dev/sda3        9cf98420-a472-431d-a63b-148b7006d86f   ext2       
/dev/sda4        4f21e042-a309-4b21-b85b-a1b7150e9514   ext2       
/dev/sda5        YeWTij-fcYg-R890-TrA1-VTAu-Jfis-SlYnNp LVM2_member 
/dev/sdb1        1445adc8-3145-4fcb-86df-701f0f711943   ext2       u910_boot
/dev/sdb2        Da0P8C-cO0N-v0Qd-f20L-bhfH-9im2-OP2Osd LVM2_member 
/dev/sdb3        9c71c5a7-97bd-45fd-b9a5-b377ee636972   swap       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
seeker-ma_log
seeker-mythtv
seeker-swap
seeker-ubuntu910_root
seeker-ubuntu910_usr
seeker-ubuntu910_var

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/seeker-ma_log /home/mythtv/archive/logs reiserfs   (rw)
/dev/mapper/seeker-mythtv /home/mythtv             xfs        (rw,allocsize=512m)
/dev/mapper/seeker-ubuntu910_root /                        reiserfs   (rw)
/dev/mapper/seeker-ubuntu910_usr /usr                     reiserfs   (rw)
/dev/mapper/seeker-ubuntu910_var /var                     reiserfs   (rw)
/dev/sdb1        /boot                    ext2       (rw)


============================= sdb1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod lvm
insmod reiserfs
set root=(seeker-ubuntu910_usr)
search --no-floppy --fs-uuid --set d6b00e86-b7c8-4c89-b54a-365343977f9e
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
    linux    /vmlinuz-2.6.31-22-generic root=/dev/mapper/seeker-ubuntu910_root ro   quiet splash
    initrd    /initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
    linux    /vmlinuz-2.6.31-22-generic root=/dev/mapper/seeker-ubuntu910_root ro single 
    initrd    /initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
    linux    /vmlinuz-2.6.31-16-generic root=/dev/mapper/seeker-ubuntu910_root ro   quiet splash
    initrd    /initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
    linux    /vmlinuz-2.6.31-16-generic root=/dev/mapper/seeker-ubuntu910_root ro single 
    initrd    /initrd.img-2.6.31-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Ubuntu 9.10, locally-compiled 2.6.31.5 kernel (old FireWire)" {
        insmod ext2
        set root=(hd1,1)
        search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
        linux /bzImage-2.6.31.5-intel root=/dev/mapper/seeker-ubuntu910_root ro
        initrd /initrd.img-2.6.31.5-intel
}

menuentry "Ubuntu 9.10, locally-compiled 2.6.32.2 kernel (new FireWire)" {
        insmod ext2
        set root=(hd1,1)
        search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
        linux /bzImage-2.6.32.2-intel root=/dev/mapper/seeker-ubuntu910_root ro
        initrd /initrd.img-2.6.32.2-intel
}

menuentry "Ubuntu 9.10, locally-compiled 2.6.37 kernel (old FireWire)" {
        insmod ext2
        set root=(hd1,1)
        search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
        linux /bzImage-2.6.37 root=/dev/mapper/seeker-ubuntu910_root ro
        initrd /initrd.img-2.6.37
}

### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.030898571 = 0.033177088    grub/core.img                                  2
   0.024076939 = 0.025852416    grub/grub.cfg                                  2
   0.014526844 = 0.015598080    initrd.img-2.6.31-16-generic                  17
   0.046909809 = 0.050369024    initrd.img-2.6.31-22-generic                  24
   0.022274494 = 0.023917056    initrd.img-2.6.31.5-intel                     16
   0.025280476 = 0.027144704    initrd.img-2.6.32.2-intel                     19
   0.019152164 = 0.020564480    initrd.img-2.6.37                             16
   0.043557644 = 0.046769664    vmlinuz-2.6.31-16-generic                     18
   0.034281254 = 0.036809216    vmlinuz-2.6.31-22-generic                     24

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on seeker-mythtv'


Unknown BootLoader on seeker-ma_log'


Unknown BootLoader on seeker-ubuntu910_root'


Unknown BootLoader on seeker-ubuntu910_usr'


Unknown BootLoader on seeker-ubuntu910_var'


Unknown BootLoader on seeker-swap'



=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/seeker-mythtv': No such file or directory
hexdump: /dev/mapper/seeker-mythtv': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/seeker-ma_log': No such file or directory
hexdump: /dev/mapper/seeker-ma_log': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/seeker-ubuntu910_root': No such file or directory
hexdump: /dev/mapper/seeker-ubuntu910_root': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/seeker-ubuntu910_usr': No such file or directory
hexdump: /dev/mapper/seeker-ubuntu910_usr': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/seeker-ubuntu910_var': No such file or directory
hexdump: /dev/mapper/seeker-ubuntu910_var': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/seeker-swap': No such file or directory
hexdump: /dev/mapper/seeker-swap': No such file or directory

```

Finally, and most unusually, is a VirtualBox machine running Fedora 14 and booting via EFI rather than BIOS:

```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/grub.conf

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 14 (Laughlin) 
                       Kernel on an ()
    Boot files:        /boot/grub/grub.cfg /boot/grub/grub.conf /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 32.4 GB, 32443990016 bytes
255 heads, 63 sectors/track, 3944 cylinders, total 63367168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1    63,367,167    63,367,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       411,647       409,600 EFI System partition
/dev/sda2         411,648     1,435,647     1,024,000 Data partition (Windows/Linux)
/dev/sda3       1,435,648     5,629,951     4,194,304 Swap partition (Linux)
/dev/sda4       5,629,952    63,365,119    57,735,168 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        564B-DC21                              vfat       ESP
/dev/sda2        520ed0bf-aaf4-4db9-9336-4394962095c1   ext2       boot
/dev/sda3        fe888a78-57cf-4f6a-8793-d6e0b2248bf5   swap       swap
/dev/sda4        e3ca8158-5af0-41cd-a8b8-44ce81a7250e   ext4       root

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw,umask=0077,shortname=winnt)
/dev/sda2        /boot                    ext4       (rw)
/dev/sda4        /                        ext4       (rw)
/dev/sr0         /media/GRMCEULXFRER_EN_DVD udf        (ro,nosuid,nodev,uhelper=udisks,uid=500,gid=100,iocharset=utf8,umask=0077)


============================= sda2/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /usr/local/etc/grub.d and settings from /usr/local/etc/default/grub
#

### BEGIN /usr/local/etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="2"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function load_video {
  insmod efi_gop
  insmod efi_uga
}

set timeout=5
### END /usr/local/etc/grub.d/00_header ###

### BEGIN /usr/local/etc/grub.d/10_linux ###
menuentry 'GNU/Linux, with Linux 2.6.35.10-74.fc14.x86_64' --class gnu-linux --class gnu --class os {
    load_video
#    set gfxpayload=keep
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 520ed0bf-aaf4-4db9-9336-4394962095c1
    echo    'Loading Linux 2.6.35.10-74.fc14.x86_64 ...'
    linux    /vmlinuz-2.6.35.10-74.fc14.x86_64 root=UUID=e3ca8158-5af0-41cd-a8b8-44ce81a7250e ro
    echo    'Loading initial ramdisk ...'
    initrd    /initramfs-2.6.35.10-74.fc14.x86_64.img
}
menuentry 'GNU/Linux, with Linux 2.6.35.10-74.fc14.x86_64 (recovery mode)' --class gnu-linux --class gnu --class os {
    load_video
#    set gfxpayload=keep
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 520ed0bf-aaf4-4db9-9336-4394962095c1
    echo    'Loading Linux 2.6.35.10-74.fc14.x86_64 ...'
    linux    /vmlinuz-2.6.35.10-74.fc14.x86_64 root=UUID=e3ca8158-5af0-41cd-a8b8-44ce81a7250e ro single
    echo    'Loading initial ramdisk ...'
    initrd    /initramfs-2.6.35.10-74.fc14.x86_64.img
}
### END /usr/local/etc/grub.d/10_linux ###

### BEGIN /usr/local/etc/grub.d/20_linux_xen ###
### END /usr/local/etc/grub.d/20_linux_xen ###

### BEGIN /usr/local/etc/grub.d/30_os-prober ###
### END /usr/local/etc/grub.d/30_os-prober ###

### BEGIN /usr/local/etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Fedora 14 with Linux 2.6.36.2local' {
    load_video
#    set gfxpayload=keep
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 520ed0bf-aaf4-4db9-9336-4394962095c1
    echo    'Loading Linux 2.6.35.10-74.fc14.x86_64 ...'
    linux    /bzImage-2.6.36.2local root=UUID=e3ca8158-5af0-41cd-a8b8-44ce81a7250e ro
    echo    'Loading initial ramdisk ...'
    initrd    /initramfs-2.6.36.2local.img
}
### END /usr/local/etc/grub.d/40_custom ###

### BEGIN /usr/local/etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /usr/local/etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sda2/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,1)
#          kernel /vmlinuz-version ro root=/dev/mapper/VolGroup-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda1
device (hd0) HD(1,800,64000,071b8514-d869-4a67-a052-3d541dbc3b77)
default=0
timeout=0
splashimage=(hd0,1)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.10-74.fc14.x86_64)
    root (hd0,1)
    kernel /vmlinuz-2.6.35.10-74.fc14.x86_64 ro root=/dev/mapper/VolGroup-lv_root rd_LVM_LV=VolGroup/lv_root rd_LVM_LV=VolGroup/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.35.10-74.fc14.x86_64.img
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.548343658 = 0.588779520    grub/grub.cfg                                  1
   0.549872398 = 0.590420992    grub/grub.conf                                 1
   0.214258194 = 0.230057984    initramfs-2.6.35.10-74.fc14.x86_64.img        43
   0.223603249 = 0.240092160    initramfs-2.6.36.2local.img                   24
   0.217798233 = 0.233859072    vmlinuz-2.6.35.10-74.fc14.x86_64              16

=========================== sda4/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /usr/local/etc/grub.d and settings from /usr/local/etc/default/grub
#

### BEGIN /usr/local/etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="2"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function load_video {
  insmod efi_gop
  insmod efi_uga
}

set timeout=5
### END /usr/local/etc/grub.d/00_header ###

### BEGIN /usr/local/etc/grub.d/10_linux ###
menuentry 'GNU/Linux, with Linux 2.6.35.10-74.fc14.x86_64' --class gnu-linux --class gnu --class os {
    load_video
#    set gfxpayload=keep
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 520ed0bf-aaf4-4db9-9336-4394962095c1
    echo    'Loading Linux 2.6.35.10-74.fc14.x86_64 ...'
    linux    /vmlinuz-2.6.35.10-74.fc14.x86_64 root=UUID=e3ca8158-5af0-41cd-a8b8-44ce81a7250e ro
    echo    'Loading initial ramdisk ...'
    initrd    /initramfs-2.6.35.10-74.fc14.x86_64.img
}
menuentry 'GNU/Linux, with Linux 2.6.35.10-74.fc14.x86_64 (recovery mode)' --class gnu-linux --class gnu --class os {
    load_video
#    set gfxpayload=keep
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 520ed0bf-aaf4-4db9-9336-4394962095c1
    echo    'Loading Linux 2.6.35.10-74.fc14.x86_64 ...'
    linux    /vmlinuz-2.6.35.10-74.fc14.x86_64 root=UUID=e3ca8158-5af0-41cd-a8b8-44ce81a7250e ro single
    echo    'Loading initial ramdisk ...'
    initrd    /initramfs-2.6.35.10-74.fc14.x86_64.img
}
### END /usr/local/etc/grub.d/10_linux ###

### BEGIN /usr/local/etc/grub.d/20_linux_xen ###
### END /usr/local/etc/grub.d/20_linux_xen ###

### BEGIN /usr/local/etc/grub.d/30_os-prober ###
### END /usr/local/etc/grub.d/30_os-prober ###

### BEGIN /usr/local/etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Fedora 14 with Linux 2.6.36.2local' {
    load_video
#    set gfxpayload=keep
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 520ed0bf-aaf4-4db9-9336-4394962095c1
    echo    'Loading Linux 2.6.35.10-74.fc14.x86_64 ...'
    linux    /bzImage-2.6.36.2local root=UUID=e3ca8158-5af0-41cd-a8b8-44ce81a7250e ro
    echo    'Loading initial ramdisk ...'
    initrd    /initramfs-2.6.36.2local.img
}
### END /usr/local/etc/grub.d/40_custom ###

### BEGIN /usr/local/etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /usr/local/etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

========================== sda4/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,1)
#          kernel /vmlinuz-version ro root=/dev/mapper/VolGroup-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda1
device (hd0) HD(1,800,64000,071b8514-d869-4a67-a052-3d541dbc3b77)
default=0
timeout=0
splashimage=(hd0,1)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.10-74.fc14.x86_64)
    root (hd0,1)
    kernel /vmlinuz-2.6.35.10-74.fc14.x86_64 ro root=/dev/mapper/VolGroup-lv_root rd_LVM_LV=VolGroup/lv_root rd_LVM_LV=VolGroup/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.35.10-74.fc14.x86_64.img
--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Fri Jan 21 01:50:51 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=e3ca8158-5af0-41cd-a8b8-44ce81a7250e /                       ext4    defaults        1 1
UUID=520ed0bf-aaf4-4db9-9336-4394962095c1 /boot                   ext4    defaults        1 2
UUID=564B-DC21                            /boot/efi               vfat    umask=0077,shortname=winnt 0 0
UUID=fe888a78-57cf-4f6a-8793-d6e0b2248bf5 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

nessus:/home/rodsmith   /other/nessus           nfs     defaults        0 0
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   3.036624908 = 3.260551168    boot/grub/grub.cfg                             1
   3.038153648 = 3.262192640    boot/grub/grub.conf                            1
   2.702539444 = 2.901829632    boot/initramfs-2.6.35.10-74.fc14.x86_64.img   43
   2.711884499 = 2.911863808    boot/initramfs-2.6.36.2local.img              24
   2.706079483 = 2.905630720    boot/vmlinuz-2.6.35.10-74.fc14.x86_64         16

=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically

```

The script seems to be missing the presence of the boot code in the BIOS Boot Partition on the first two systems, as well as identifying filesystems in logical volumes.

EFI-based systems will likely become more prevalent in a few months, since manufacturers seem poised to move in that direction. (Several models were introduced and then temporarily withdrawn because of the recent Intel chipset fiasco.) Identifying and tracing the activities of EFI boot loaders will therefore become important at some point.

---

### Post by Gert Hulselmans on 2011-02-16
@ srs5694
Can you run boot_info_script_055.sh too on those samples?

Also attach the first few sectors of the BIOS Boot Partitions:
```
sudo dd if=/dev/sda5 of=biosbootpart.bin count=63 bs=512
```

---

### Post by srs5694 on 2011-02-16
OK. Here's the 0.55 information for the three systems:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 976768065 
    of the same hard drive for core.img, core.img is at this location on 
    /dev/sda and looks on partition #2 for /grub.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub in the file /hdb.mbr looks at sector 1 on boot 
                       drive #1 for the stage2 file, but no stage2 files can 
                       be found at this location.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /grub/menu.lst /grub/grub.cfg 
                       /boot/grub/grub.cfg /boot/grub/grub.conf 
                       /grub/grub.conf /grub/core.img /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub 0.97 in the file /sda-gpt.img looks at sector 
                       1126836 of the same hard drive for the stage2 file. A 
                       stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #3 for /grub/menu.lst. Grub 0.97 in 
                       the file /sda-mbr.img looks at sector 1126836 of the 
                       same hard drive for the stage2 file. A stage2 file is 
                       at this location on /dev/sda. Stage2 looks on 
                       partition #3 for /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda4: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Grub 2's core.img
    Boot sector info:  

nessus-root: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /etc/fstab

nessus-usr: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

nessus-usrlocal: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

nessus-opt: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

nessus-swap: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

nessus-home: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

nessus-emu: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

nessus-g_root: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /etc/fstab

nessus-g_opt: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

nessus-g_usr: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34       390,625       390,592 Linux or Data
/dev/sda2         390,626       803,249       412,624 Linux or Data
/dev/sda3         803,250     1,212,850       409,601 Linux or Data
/dev/sda4       1,212,851   976,768,064   975,555,214 LVM
/dev/sda5     976,768,065   976,768,464           400 Bios Boot Partition

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/nessus-emu dcb71faa-ed88-467c-abbf-3d8b3d1e0849   reiserfs                                 
/dev/mapper/nessus-g_opt 85f3f363-781e-494d-beec-c45fe0309a17   reiserfs                                 
/dev/mapper/nessus-g_root 5f96cafa-e0a7-4057-b18f-fa709db5b837   reiserfs                                 
/dev/mapper/nessus-g_usr 580d3322-2ff8-4692-a964-be996c2e9929   reiserfs                                 
/dev/mapper/nessus-home 3a00a023-c58b-4dff-963a-365e399b5982   reiserfs                                 
/dev/mapper/nessus-opt 1ba43617-67ac-4858-8147-935ce8e172f5   ext3                                     
/dev/mapper/nessus-root 5edf77b1-6008-4a08-98a2-c2af7cf1dd87   reiserfs                                 
/dev/mapper/nessus-swap 90dfc155-fd37-4e73-a112-472ce434096c   swap                                     
/dev/mapper/nessus-usr 1d6a7af6-dc42-4aa0-8ce3-e78cb0036682   reiserfs                                 
/dev/mapper/nessus-usrlocal a139b90e-2f94-4378-bf66-fe7669808dbe   ext3                                     
/dev/sda1        f12ca6d0-40f1-416c-86fd-b65c934cc750   ext2       spare1                        
/dev/sda2        c607bd95-8edf-4eb1-aa93-12db8f0e66a2   ext2       spare2                        
/dev/sda3        e6683da7-bb14-451a-89f9-3636860d6da1   ext2       boot                          
/dev/sda4        F0FYTX-mtb3-b8Kw-WZ3I-AhB6-JG3l-yCXWkA LVM2_member                               
/dev/sda: PTTYPE="gpt" 
error: /dev/mapper/No: No such file or directory
error: /dev/sdb: No medium found
error: disks: No such file or directory
error: RAID: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
nessus-emu
nessus-g_opt
nessus-g_root
nessus-g_usr
nessus-home
nessus-opt
nessus-root
nessus-swap
nessus-usr
nessus-usrlocal

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/nessus-g_root /                        reiserfs   (rw,noatime)
/dev/sda2        /boot                    ext2       (rw,noatime)
/dev/mapper/nessus-g_usr /usr                     reiserfs   (rw,noatime)
/dev/mapper/nessus-usrlocal /usr/local               ext3       (rw,noatime)
/dev/mapper/nessus-g_opt /opt                     reiserfs   (rw,noatime)
/dev/mapper/nessus-home /home                    reiserfs   (rw,noatime)
/dev/mapper/nessus-emu /other/emu               reiserfs   (rw,noatime)


============================= sda2/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
insmod lvm
insmod reiserfs
set root='(nessus-g_usr)'
search --no-floppy --fs-uuid --set 580d3322-2ff8-4692-a964-be996c2e9929
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,2)'
search --no-floppy --fs-uuid --set c607bd95-8edf-4eb1-aa93-12db8f0e66a2
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Gentoo (2.6.37)" {
   set root=(hd0,2)
   linux /bzImage-2.6.37 ro root=/dev/mapper/nessus-g_root dolvm
   initrd /initramfs-genkernel-x86_64-2.6.37
}

menuentry "Gentoo (2.6.35.5)" {
   set root=(hd0,2)
   linux /bzImage-2.6.35.5 ro root=/dev/mapper/nessus-g_root dolvm
   initrd /initramfs-genkernel-x86_64-2.6.35.5
}

menuentry "Gentoo (2.6.32.3_fglrx)" {
   set root=(hd0,2)
   linux /bzImage-2.6.32.3_fglrx ro root=/dev/mapper/nessus-g_root dolvm
   initrd /initramfs-genkernel-x86_64-2.6.32.3_fglrx
}
### END /etc/grub.d/40_custom ###

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
insmod lvm
insmod reiserfs
set root='(nessus-g_usr)'
search --no-floppy --fs-uuid --set 580d3322-2ff8-4692-a964-be996c2e9929
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,2)'
search --no-floppy --fs-uuid --set c607bd95-8edf-4eb1-aa93-12db8f0e66a2
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Gentoo (2.6.37)" {
   set root=(hd0,2)
   linux /bzImage-2.6.37 ro root=/dev/mapper/nessus-g_root dolvm
   initrd /initramfs-genkernel-x86_64-2.6.37
}

menuentry "Gentoo (2.6.35.5)" {
   set root=(hd0,2)
   linux /bzImage-2.6.35.5 ro root=/dev/mapper/nessus-g_root dolvm
   initrd /initramfs-genkernel-x86_64-2.6.35.5
}

menuentry "Gentoo (2.6.32.3_fglrx)" {
   set root=(hd0,2)
   linux /bzImage-2.6.32.3_fglrx ro root=/dev/mapper/nessus-g_root dolvm
   initrd /initramfs-genkernel-x86_64-2.6.32.3_fglrx
}
### END /etc/grub.d/40_custom ###

========================== sda2/boot/grub/grub.conf: ==========================

# This is a sample grub.conf for use with Genkernel, per the Gentoo handbook
# http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2
# If you are not using Genkernel and you need help creating this file, you
# should consult the handbook. Alternatively, consult the grub.conf.sample that
# is included with the Grub documentation.

default 0
timeout 30
#splashimage=(hd0,0)/boot/grub/splash.xpm.gz

#title Gentoo Linux 2.6.24-r5
#root (hd0,0)
#kernel /boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/ram0 real_root=/dev/sda3
#initrd /boot/initramfs-genkernel-x86-2.6.24-gentoo-r5

# vim:ft=conf:

============================= sda2/grub/grub.conf: =============================

# This is a sample grub.conf for use with Genkernel, per the Gentoo handbook
# http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2
# If you are not using Genkernel and you need help creating this file, you
# should consult the handbook. Alternatively, consult the grub.conf.sample that
# is included with the Grub documentation.

default 0
timeout 30
#splashimage=(hd0,0)/boot/grub/splash.xpm.gz

#title Gentoo Linux 2.6.24-r5
#root (hd0,0)
#kernel /boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/ram0 real_root=/dev/sda3
#initrd /boot/initramfs-genkernel-x86-2.6.24-gentoo-r5

# vim:ft=conf:

=================== sda2: Location of files loaded by Grub: ===================


    .3GB: boot/grub/core.img
    .2GB: boot/grub/grub.cfg
    .2GB: boot/grub/grub.conf
    .2GB: boot/grub/menu.lst
    .2GB: boot/grub/stage2
    .2GB: boot/initramfs-genkernel-x86_64-2.6.27-gentoo-r7
    .2GB: boot/initramfs-genkernel-x86_64-2.6.32.2
    .2GB: boot/initramfs-genkernel-x86_64-2.6.35.4
    .2GB: boot/initramfs-genkernel-x86_64-2.6.35.5
    .2GB: boot/initramfs-genkernel-x86_64-2.6.37
    .2GB: boot/initrd-2.6.27-gentoo-r7.img
    .2GB: boot/initrd-2.6.32.2.img
    .3GB: grub/core.img
    .2GB: grub/grub.cfg
    .2GB: grub/grub.conf
    .2GB: grub/menu.lst
    .2GB: grub/stage2
    .2GB: initramfs-genkernel-x86_64-2.6.27-gentoo-r7
    .2GB: initramfs-genkernel-x86_64-2.6.32.2
    .2GB: initramfs-genkernel-x86_64-2.6.35.4
    .2GB: initramfs-genkernel-x86_64-2.6.35.5
    .2GB: initramfs-genkernel-x86_64-2.6.37
    .2GB: initrd-2.6.27-gentoo-r7.img
    .2GB: initrd-2.6.32.2.img

============================= sda3/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

default        0
timeout        15

title        Gentoo, kernel 2.6.32.3_fglrx
root        (hd0,1)
kernel        /bzImage-2.6.32.3_fglrx root=/dev/mapper/nessus-g_root ro quiet splash dolvm
initrd        /initramfs-genkernel-x86_64-2.6.32.3_fglrx
quiet

title        Gentoo, kernel 2.6.32.3
root        (hd0,1)
kernel        /bzImage-2.6.32.3 root=/dev/mapper/nessus-g_root ro quiet splash dolvm
initrd        /initramfs-genkernel-x86_64-2.6.32.3
quiet

title        Ubuntu 8.04, kernel 2.6.30
root        (hd0,2)
kernel        /bzImage-2.6.30 root=/dev/mapper/nessus-root ro quiet splash
initrd        /initrd.img-2.6.30
quiet

title        Xen (Ubuntu 8.04, kernel 2.6.30)
root        (hd0,2)
kernel        /xen-3.2.gz dom0_mem=2097152 noreboot
module        /vmlinux-2.6.30 root=/dev/mapper/nessus-root ro quiet splash
module        /initrd.img-2.6.30
quiet

title        Ubuntu 8.04, kernel 2.6.28sb700
root        (hd0,2)
kernel        /bzImage-2.6.28sb700 root=/dev/mapper/nessus-root ro quiet splash
initrd        /initrd.img-2.6.28sb700
quiet

title        Ubuntu 8.04, kernel 2.6.28
root        (hd0,2)
kernel        /bzImage-2.6.28 root=/dev/mapper/nessus-root ro quiet splash vga=0x31a
initrd        /initrd.img-2.6.28
quiet

title        Ubuntu 8.04, kernel 2.6.25.2
root        (hd0,2)
kernel        /bzImage-2.6.25.2 root=/dev/mapper/nessus-root ro quiet splash
initrd        /initrd.img-2.6.25.2
quiet

title        Ubuntu 8.04, kernel 2.6.24-19-server
root        (hd0,2)
kernel        /vmlinuz-2.6.24-19-server root=/dev/mapper/nessus-root ro quiet splash
initrd        /initrd.img-2.6.24-19-server
quiet

title        Ubuntu 8.04, kernel 2.6.24-19-server (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.24-19-server root=/dev/mapper/nessus-root ro single
initrd        /initrd.img-2.6.24-19-server

title        Ubuntu 8.04, kernel 2.6.24-16-server
root        (hd0,2)
kernel        /vmlinuz-2.6.24-16-server root=/dev/mapper/nessus-root ro quiet splash
initrd        /initrd.img-2.6.24-16-server
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-server (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.24-16-server root=/dev/mapper/nessus-root ro single
initrd        /initrd.img-2.6.24-16-server

title        Ubuntu 8.04, memtest86+
root        (hd0,2)
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f3678608-6b77-4a9f-85d5-39277ec00af5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##


=================== sda3: Location of files loaded by Grub: ===================


    .4GB: grub/menu.lst
    .5GB: grub/stage2
    .4GB: initrd.img-2.6.24-22-server
    .4GB: initrd.img-2.6.24-22-server.bak
    .5GB: initrd.img-2.6.24-23-server
    .5GB: initrd.img-2.6.24-23-server.bak
    .5GB: initrd.img-2.6.24-24-server
    .5GB: initrd.img-2.6.24-24-server.bak
    .6GB: initrd.img-2.6.24-26-server
    .5GB: initrd.img-2.6.24-26-server.bak
    .4GB: initrd.img-2.6.25.2
    .4GB: initrd.img-2.6.28
    .4GB: initrd.img-2.6.28foo
    .4GB: initrd.img-2.6.28sb700
    .5GB: initrd.img-2.6.30
    .5GB: initrd.img-2.6.31.5
    .4GB: vmlinuz-2.6.24-22-server
    .4GB: vmlinuz-2.6.24-23-server
    .5GB: vmlinuz-2.6.24-24-server
    .5GB: vmlinuz-2.6.24-26-server

============================ nessus-root/etc/fstab: ============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                /proc           proc    defaults        0       0
/dev/mapper/nessus-root    /               reiserfs relatime        0       1
/dev/sda3        /boot           ext2     relatime        0     2
/dev/mapper/nessus-home /home           reiserfs relatime        0     0
/dev/mapper/nessus-opt    /opt            ext3     relatime        0     2
/dev/mapper/nessus-usr    /usr            reiserfs relatime        0       0
/dev/mapper/nessus-usrlocal /usr/local    ext3     relatime        0     2
/dev/mapper/nessus-emu    /other/emu    reiserfs relatime    0 0

/dev/mapper/nessus-swap none            swap    sw              0       0

/dev/scd0       /mnt/cdrom      auto    users,noauto,exec,utf8 0       0
/dev/fd0        /mnt/floppy     auto    rw,user,noauto,exec,utf8 0       0

/dev/sdc1       /mnt/usb        auto    noauto,users      0  0
/dev/sdb1       /mnt/cf         auto    noauto,users,fmask=0111,dmask=0000  0 0

seeker:/home/mythtv  /home/mythtv         nfs  hard  0 0
# Note: Below doesn't work well because mythcommflag flakes out.
#//seeker/mythtv /home/mythtv        cifs users,creds=/etc/samba/creds-m,uid=108,gid=113,file_mode=0666,dir_mode=0777 0 0
#speaker:/home        /other/speaker/home  nfs  defaults  0 0
prill:/home          /other/prill         nfs  noauto,users  0 0

curlftpfs#RodSmith:to4Koa@ftp.sybex.com/editorial/ISBN/9780470503843  /mnt/sybex fuse rw,uid=500,umask=0022,user,noauto 0 0
curlftpfs#rodsb3:Ty9eeXp3vN@ftp.rodsbooks.com  /mnt/rodsbooks fuse rw,uid=500,umask=0022,user,noauto 0 0

=========================== nessus-g_root/etc/fstab: ===========================

# /etc/fstab: static file system information.
#
# noatime turns off atimes for increased performance (atimes normally aren't 
# needed; notail increases performance of ReiserFS (at the expense of storage 
# efficiency).  It's safe to drop the noatime options if you want and to 
# switch between notail / tail freely.
#
# The root filesystem should have a pass number of either 0 or 1.
# All other filesystems should have a pass number of 0 or greater than 1.
#
# See the manpage fstab(5) for more information.
#

# <fs>            <mountpoint>    <type>        <opts>        <dump/pass>

# NOTE: If your BOOT partition is ReiserFS, add the notail option to opts.
/dev/sda2            /boot    ext2        noatime            1 2
/dev/mapper/nessus-g_root    /    reiserfs           noatime        0 1
/dev/mapper/nessus-g_usr    /usr    reiserfs           noatime        0 2
/dev/mapper/nessus-usrlocal    /usr/local    ext3    noatime        0 2
/dev/mapper/nessus-g_opt    /opt    reiserfs    noatime        0 2
/dev/mapper/nessus-home        /home    reiserfs           noatime        0 2
/dev/mapper/nessus-emu        /other/emu    reiserfs    noatime        0 2

/dev/mapper/nessus-root    /other/ubuntu    reiserfs    noauto,users  0 0
/dev/mapper/nessus-opt    /other/ubuntu/opt ext3        noauto,users  0 0

/dev/mapper/nessus-swap    none        swap        sw        0 0

/dev/cdrom        /mnt/cdrom    iso9660        noauto,users,ro    0 0
#/dev/fd0        /mnt/floppy    auto        noauto        0 0
/dev/sdc1        /mnt/usb    auto        noauto,users    0 0
/dev/sdb1        /mnt/cf        auto        noauto,users    0 0

seeker:/home/mythtv    /home/mythtv    nfs        nolock,users    0 0

# glibc 2.2 and above expects tmpfs to be mounted at /dev/shm for 
# POSIX shared memory (shm_open, shm_unlink).
# (tmpfs is a dynamically expandable/shrinkable ramdisk, and will
#  use almost no memory if not populated with files)
shm            /dev/shm    tmpfs        nodev,nosuid,noexec    0 0
=======Devices which don't seem to have a corresponding hard drive==============

sdb No RAID disks 
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

```

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 40 of the 
    same hard drive for core.img, core.img is at this location on /dev/sda and 
    looks for (UUID=1445adc8-3145-4fcb-86df-701f0f711943)/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Grub 2's core.img
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 440.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda5: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

seeker-mythtv: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

seeker-ma_log: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

seeker-ubuntu910_root: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /grub.cfg /etc/fstab

seeker-ubuntu910_usr: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

seeker-ubuntu910_var: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

seeker-swap: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40           439           400 Bios Boot Partition
/dev/sda2             440       410,039       409,600 System/Boot Partition
/dev/sda3         410,040       819,639       409,600 Linux or Data
/dev/sda4         819,640     1,229,239       409,600 Linux or Data
/dev/sda5       1,229,240 1,953,525,134 1,952,295,895 LVM

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00022117

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       192,779       192,717  83 Linux
/dev/sdb2           1,012,095   625,137,344   624,125,250  8e Linux LVM
/dev/sdb3             192,780     1,012,094       819,315  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/seeker-ma_log 28058c9f-a6fe-4089-8abd-bd41854267cc   reiserfs                                 
/dev/mapper/seeker-mythtv 284c14ab-c87f-4180-87a6-7332f412f2bf   xfs                                      
/dev/mapper/seeker-swap 3a057e10-ce78-4bc1-a7a9-e465119b9021   swap                                     
/dev/mapper/seeker-ubuntu910_root e238fbcf-0943-404c-98ab-da5d210f8acb   reiserfs   u910_root                     
/dev/mapper/seeker-ubuntu910_usr d6b00e86-b7c8-4c89-b54a-365343977f9e   reiserfs   u910_usr                      
/dev/mapper/seeker-ubuntu910_var 740ec23a-bb47-4e6b-8476-b7889d94150e   reiserfs   u910_var                      
/dev/sda2        FF27-F452                              vfat                                     
/dev/sda3        9cf98420-a472-431d-a63b-148b7006d86f   ext2                                     
/dev/sda4        4f21e042-a309-4b21-b85b-a1b7150e9514   ext2                                     
/dev/sda5        YeWTij-fcYg-R890-TrA1-VTAu-Jfis-SlYnNp LVM2_member                               
/dev/sdb1        1445adc8-3145-4fcb-86df-701f0f711943   ext2       u910_boot                     
/dev/sdb2        Da0P8C-cO0N-v0Qd-f20L-bhfH-9im2-OP2Osd LVM2_member                               
/dev/sdb3        9c71c5a7-97bd-45fd-b9a5-b377ee636972   swap                                     

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
seeker-ma_log
seeker-mythtv
seeker-swap
seeker-ubuntu910_root
seeker-ubuntu910_usr
seeker-ubuntu910_var

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/seeker-ubuntu910_root /                        reiserfs   (rw)
/dev/mapper/seeker-ubuntu910_usr /usr                     reiserfs   (rw)
/dev/mapper/seeker-ubuntu910_var /var                     reiserfs   (rw)
/dev/sdb1        /boot                    ext2       (rw)
/dev/mapper/seeker-mythtv /home/mythtv             xfs        (rw,allocsize=512m)
/dev/mapper/seeker-ma_log /home/mythtv/archive/logs reiserfs   (rw)


============================= sdb1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod lvm
insmod reiserfs
set root=(seeker-ubuntu910_usr)
search --no-floppy --fs-uuid --set d6b00e86-b7c8-4c89-b54a-365343977f9e
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
    linux    /vmlinuz-2.6.31-22-generic root=/dev/mapper/seeker-ubuntu910_root ro   quiet splash
    initrd    /initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
    linux    /vmlinuz-2.6.31-22-generic root=/dev/mapper/seeker-ubuntu910_root ro single 
    initrd    /initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
    linux    /vmlinuz-2.6.31-16-generic root=/dev/mapper/seeker-ubuntu910_root ro   quiet splash
    initrd    /initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
    linux    /vmlinuz-2.6.31-16-generic root=/dev/mapper/seeker-ubuntu910_root ro single 
    initrd    /initrd.img-2.6.31-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Ubuntu 9.10, locally-compiled 2.6.31.5 kernel (old FireWire)" {
        insmod ext2
        set root=(hd1,1)
        search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
        linux /bzImage-2.6.31.5-intel root=/dev/mapper/seeker-ubuntu910_root ro
        initrd /initrd.img-2.6.31.5-intel
}

menuentry "Ubuntu 9.10, locally-compiled 2.6.32.2 kernel (new FireWire)" {
        insmod ext2
        set root=(hd1,1)
        search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
        linux /bzImage-2.6.32.2-intel root=/dev/mapper/seeker-ubuntu910_root ro
        initrd /initrd.img-2.6.32.2-intel
}

menuentry "Ubuntu 9.10, locally-compiled 2.6.37 kernel (old FireWire)" {
        insmod ext2
        set root=(hd1,1)
        search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
        linux /bzImage-2.6.37 root=/dev/mapper/seeker-ubuntu910_root ro
        initrd /initrd.img-2.6.37
}

### END /etc/grub.d/40_custom ###

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-16-generic
    .0GB: initrd.img-2.6.31-22-generic
    .0GB: initrd.img-2.6.31.5-intel
    .0GB: initrd.img-2.6.32.2-intel
    .0GB: initrd.img-2.6.37
    .0GB: vmlinuz-2.6.31-16-generic
    .0GB: vmlinuz-2.6.31-22-generic

======================= seeker-ubuntu910_root/grub.cfg: =======================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="3"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod lvm
insmod reiserfs
insmod ext2
set root=(seeker-ubuntu910_usr)
search --no-floppy --fs-uuid --set d6b00e86-b7c8-4c89-b54a-365343977f9e
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
    linux    /vmlinuz-2.6.31-16-generic root=/dev/mapper/seeker-ubuntu910_root ro   quiet splash
    initrd    /initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1445adc8-3145-4fcb-86df-701f0f711943
    linux    /vmlinuz-2.6.31-16-generic root=/dev/mapper/seeker-ubuntu910_root ro single 
    initrd    /initrd.img-2.6.31-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Ubuntu 9.10, locally-compiled 2.6.31.5 kernel (old FireWire stack)" {
    insmod ext2
    set root=(hd1,1)
    linux /bzImage-2.6.31.5-intel root=/dev/mapper/seeker-ubuntu910_root ro
    initrd /initrd.img-2.6.31.5-intel
}

menuentry "Ubuntu 9.10, locally-compiled 2.6.32.2 kernel (new FireWire stack)" {
    insmod ext2
    set root=(hd1,1)
    linux /bzImage-2.6.32.2-intel root=/dev/mapper/seeker-ubuntu910_root ro
    initrd /initrd.img-2.6.32.2-intel
}

### END /etc/grub.d/40_custom ###

======================= seeker-ubuntu910_root/etc/fstab: =======================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/seeker-ubuntu910_root /               reiserfs defaults       0       0
# /boot was on /dev/sdb1 during installation
UUID=1445adc8-3145-4fcb-86df-701f0f711943 /boot           ext2    defaults        0       2
/dev/mapper/seeker-ubuntu910_usr /usr            reiserfs defaults        0       0
/dev/mapper/seeker-ubuntu910_var /var            reiserfs defaults        0       0

/dev/seeker/mythtv   /home/mythtv    xfs  allocsize=512m      0  2
/dev/seeker/ma_log   /home/mythtv/archive/logs  reiserfs  defaults      0  0

# swap was on /dev/sda6 during installation
#UUID=07ed5fde-41eb-4f69-b431-a64b8ffb6c28 none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=9c71c5a7-97bd-45fd-b9a5-b377ee636972 none            swap    sw              0       0
/dev/seeker/swap     none        swap  sw   0 0

/dev/dvd       /media/cdrom   udf,iso9660 user,noauto,exec,utf8 0       0

# Network mounts
nessus:/home   /other/nessus  nfs    noauto,users   0 0

=========== seeker-ubuntu910_root: Location of files loaded by Grub: ===========


    ??GB: grub.cfg
    .0GB: initrd.img
    .0GB: vmlinuz

```

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/grub.conf

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 14 (Laughlin) 
                       Kernel on an ()
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 32.4 GB, 32443990016 bytes
255 heads, 63 sectors/track, 3944 cylinders, total 63367168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1    63,367,167    63,367,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048       411,647       409,600 System/Boot Partition
/dev/sda2         411,648     1,435,647     1,024,000 Linux or Data
/dev/sda3       1,435,648     5,629,951     4,194,304 Linux Swap
/dev/sda4       5,629,952    63,365,119    57,735,168 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        564B-DC21                              vfat       ESP                           
/dev/sda2        520ed0bf-aaf4-4db9-9336-4394962095c1   ext2       boot                          
/dev/sda3        fe888a78-57cf-4f6a-8793-d6e0b2248bf5   swap       swap                          
/dev/sda4        e3ca8158-5af0-41cd-a8b8-44ce81a7250e   ext4       root                          
/dev/sda: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw)
/dev/sda2        /boot                    ext4       (rw)
/dev/sda1        /boot/efi                vfat       (rw,umask=0077,shortname=winnt)
/dev/sr0         /media/GRMCEULXFRER_EN_DVD udf        (ro,nosuid,nodev,uhelper=udisks,uid=500,gid=100,iocharset=utf8,umask=0077)


============================= sda2/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /usr/local/etc/grub.d and settings from /usr/local/etc/default/grub
#

### BEGIN /usr/local/etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="2"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function load_video {
  insmod efi_gop
  insmod efi_uga
}

set timeout=5
### END /usr/local/etc/grub.d/00_header ###

### BEGIN /usr/local/etc/grub.d/10_linux ###
menuentry 'GNU/Linux, with Linux 2.6.35.10-74.fc14.x86_64' --class gnu-linux --class gnu --class os {
    load_video
#    set gfxpayload=keep
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 520ed0bf-aaf4-4db9-9336-4394962095c1
    echo    'Loading Linux 2.6.35.10-74.fc14.x86_64 ...'
    linux    /vmlinuz-2.6.35.10-74.fc14.x86_64 root=UUID=e3ca8158-5af0-41cd-a8b8-44ce81a7250e ro
    echo    'Loading initial ramdisk ...'
    initrd    /initramfs-2.6.35.10-74.fc14.x86_64.img
}
menuentry 'GNU/Linux, with Linux 2.6.35.10-74.fc14.x86_64 (recovery mode)' --class gnu-linux --class gnu --class os {
    load_video
#    set gfxpayload=keep
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 520ed0bf-aaf4-4db9-9336-4394962095c1
    echo    'Loading Linux 2.6.35.10-74.fc14.x86_64 ...'
    linux    /vmlinuz-2.6.35.10-74.fc14.x86_64 root=UUID=e3ca8158-5af0-41cd-a8b8-44ce81a7250e ro single
    echo    'Loading initial ramdisk ...'
    initrd    /initramfs-2.6.35.10-74.fc14.x86_64.img
}
### END /usr/local/etc/grub.d/10_linux ###

### BEGIN /usr/local/etc/grub.d/20_linux_xen ###
### END /usr/local/etc/grub.d/20_linux_xen ###

### BEGIN /usr/local/etc/grub.d/30_os-prober ###
### END /usr/local/etc/grub.d/30_os-prober ###

### BEGIN /usr/local/etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Fedora 14 with Linux 2.6.36.2local' {
    load_video
#    set gfxpayload=keep
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 520ed0bf-aaf4-4db9-9336-4394962095c1
    echo    'Loading Linux 2.6.35.10-74.fc14.x86_64 ...'
    linux    /bzImage-2.6.36.2local root=UUID=e3ca8158-5af0-41cd-a8b8-44ce81a7250e ro
    echo    'Loading initial ramdisk ...'
    initrd    /initramfs-2.6.36.2local.img
}
### END /usr/local/etc/grub.d/40_custom ###

### BEGIN /usr/local/etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /usr/local/etc/grub.d/41_custom ###

============================= sda2/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,1)
#          kernel /vmlinuz-version ro root=/dev/mapper/VolGroup-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda1
device (hd0) HD(1,800,64000,071b8514-d869-4a67-a052-3d541dbc3b77)
default=0
timeout=0
splashimage=(hd0,1)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.10-74.fc14.x86_64)
    root (hd0,1)
    kernel /vmlinuz-2.6.35.10-74.fc14.x86_64 ro root=/dev/mapper/VolGroup-lv_root rd_LVM_LV=VolGroup/lv_root rd_LVM_LV=VolGroup/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.35.10-74.fc14.x86_64.img

=================== sda2: Location of files loaded by Grub: ===================


    .5GB: grub/grub.cfg
    .5GB: grub/grub.conf
    .2GB: initramfs-2.6.35.10-74.fc14.x86_64.img
    .2GB: initramfs-2.6.36.2local.img
    .2GB: vmlinuz-2.6.35.10-74.fc14.x86_64

=============================== sda4/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Fri Jan 21 01:50:51 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=e3ca8158-5af0-41cd-a8b8-44ce81a7250e /                       ext4    defaults        1 1
UUID=520ed0bf-aaf4-4db9-9336-4394962095c1 /boot                   ext4    defaults        1 2
UUID=564B-DC21                            /boot/efi               vfat    umask=0077,shortname=winnt 0 0
UUID=fe888a78-57cf-4f6a-8793-d6e0b2248bf5 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

nessus:/home/rodsmith   /other/nessus           nfs     defaults        0 0
=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically

```

The attachment tool is refusing to let me upload the BIOS Boot Partition code, so I've put that up on my personal Web site:

[http://www.rodsbooks.com/biosbootpart1.bin](http://www.rodsbooks.com/biosbootpart1.bin)
[http://www.rodsbooks.com/biosbootpart2.bin](http://www.rodsbooks.com/biosbootpart2.bin)

Those are for the first two systems, of course; the EFI-based system has no BIOS Boot Partition; instead, it's got a .efi file in the EFI System Partition.

---

### Post by kansasnoob on 2011-02-17
I had to catch some shut-eye. This AM I happened to think, when Natty was almost too unstable to test I used the .debs to test some of the earlier versions of grub-pc and grub-common in my Lucid on sda3 and Maverick on sda1.

This is from Lucid's apt/history on sda3:

> Start-Date: 2011-01-31  00:46:51
Remove: grub-customizer (2.1-0ubuntu1~ppa1l)
Purge: grub-pc (1.99~20101126-1ubuntu3), grub-common (1.99~20101126-1ubuntu3)
End-Date: 2011-01-31  00:47:15

Start-Date: 2011-01-31  00:48:12
Install: grub-pc (1.98-1ubuntu10), grub-common (1.98-1ubuntu10)
End-Date: 2011-01-31  00:48:48

So I'll bet that accounts for why things look odd in those two operating systems, regardless here's what you requested:

[ATTACH]183691[/ATTACH]

---

### Post by Gert Hulselmans on 2011-02-17
I did a major rewrite and restructuring of the grub2 detection and reporting code.
Everything is now in one place and not scattered over the whole script. So it should be easier to maintain now.

The old "grub2 core.img" detection magic is added again (BIOS Boot Partition).
@ srs5694
This should fix the: "but core.img can not be found at this location."

The Grub2 directory for grub v1.99 installed in a partition should now also be displayed correctly.

Due the major rewrite, it is possible that I missed something, so some testing is appreciated.

Attach the 3 result files in a gzip file.
```

sudo bash boot_info_script055.sh
==> rename RESULTS.TXT to BIS_055.txt

# BIS v056 before rewrite:
wget -O boot_info_script056-before.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=54f43e26686fd81503a190d5efc7742b6ee4658a'

sudo bash  boot_info_script056-before.sh BIS_056_before.txt

# BIS v056 after rewrite:
wget -O boot_info_script056-after.sh 
'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

sudo bash  boot_info_script056-after.sh BIS_056_after.txt
```

@ kansasnoob
To know which version you have tested, when you download the last version, go to the change log link in my signature and copy the first line of the last commit:
> Major rewrite and restructuring of the grub2 detection and reporting code.

---

### Post by drs305 on 2011-02-18
Here you go. Thanks.

---

### Post by Gert Hulselmans on 2011-02-18
@ drs305
Thanks. The output looks good.

---

### Post by kansasnoob on 2011-02-18
Unless stated otherwise I'm beginning each test by running 'dpkg-reconfigure grub-pc', then installing grub to the MBR of both drives and the PBR of that OS's root partition. Each will be labeled to indicate device designation and version of OS used to run the BIS.

[ATTACH]183801[/ATTACH]

---

### Post by Gert Hulselmans on 2011-02-18
@ kansasnoob
```
sudo dd if=/dev/sda of=sda_1.99.bin count=63 bs=512
sudo dd if=/dev/sdb of=sdb_1.99.bin count=63 bs=512
sudo dd if=/dev/sda14 of=sda14_1.99.bin count=63 bs=512
sudo dd if=/dev/sda16 of=sda16_1.99.bin count=63 bs=512
```

---

### Post by kansasnoob on 2011-02-18
[attach]183804[/attach]

---

### Post by kansasnoob on 2011-02-18
I'm not quite sure where we're at with this but I need to do something else ATM so I went ahead and used the three downloads and did this in my Maverick on sda1:

sudo dpkg-reconfigure grub-pc
# selected both MBR's and the PBR of sda1
sudo bash boot_info_script055.sh
sudo -k
mv RESULTS.txt BIS_055.txt
sudo bash  boot_info_script056-before.sh BIS_056_before.txt
sudo bash  boot_info_script056-after.sh BIS_056_after.txt

The results:

[ATTACH]183821[/ATTACH]

---

### Post by kansasnoob on 2011-02-19
I'm just bumping this because I'm not sure what to do next. I'm tempted to install Hardy since it's server version is supported until April 2013 but I'm just not sure where we're at with this :)

---

### Post by kansasnoob on 2011-02-21
I ran across something slightly interesting yesterday:

[http://ubuntuforums.org/showthread.php?t=1691844](http://ubuntuforums.org/showthread.php?t=1691844)

Basically the old BIS run from BackTrack 4 R2 fails to detect Maverick:

```
sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

```

But I'm kind of questioning whether we should even be concerned about these sorts of anomalies. I sort of feel that it's OK to specify that a certain version of BIS is known to work with certain live or installed media.

As it turned out there I'd seen enough to proceed anyway but I think it would have been reasonable to ask the OP to rerun the BIS using a 10.10 Live CD/USB, eh?

I know that even with Hardy there are problems with either the kernel or parted not being able to read ext4 partitions, etc.

Sorry for rambling, I'm just thinking out loud here :)

---

### Post by oldfred on 2011-02-21
I bet it is because Backtrack does not see ext4 partitions.  Same issue may happen with some of the new types of partitions.

Older distributions and even Ubuntu's grub 0.97 before 9.04 did not work with ext4 partitions.

---

### Post by drs305 on 2011-02-21
I don't want to take this thread too far off track, but in another thread a user was trying to get BT4 ISO to boot from G2. After too much time, I extracted the contents of the files and found that the BT4-r2 ISO still uses Grub legacy and won't mount from the G2 menu as currently constructed.

And now back to the BIS thread ...

---

### Post by Gert Hulselmans on 2011-02-21
@ kansasnoob
>  => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location on BIOS 
    drive 1 (0x80) and looks in partition -1 for (,msdos14)/boot/grub.Fixed.

Can you upload core.img of sda14 and sda16?

And the following:
```
dd if=/dev/sda of=core-1.99_sda14_embedded.bin skip=320439737 count=100 bs=512
dd if=/dev/sda of=core-1.99_sda16_embedded.bin skip=390182206 count=100 bs=512
```@ all
Last version of BIS is able to use "busybox awk". I only tested it on Ubuntu 10.10 and for my configuration, there was no difference between BIS with "gawk" and BIS with "busybox awk", except for the extraction of the embedded config file of grub4dos.

How to test:
- Download the last development version of BIS
- Uninstall gawk if installed and run BIS:
```
sudo bash boot_info_script.sh BIS_busybox_awk.txt
```- Install gawk if installed and run BIS:
```
sudo bash boot_info_script.sh BIS_gawk.txt
```- Make the diff:
```
diff -u BIS_busybox_awk.txt BIS_gawk.txt
```If "busybox awk" is reliable, "diff" shouldn't give any output.

---

### Post by kansasnoob on 2011-02-22
I'm somewhat embroiled in something else ATM but I will get back to this ASAP! Probably no later than tomorrow in the AM, sooner if possible. Sorry for the delay.

---

### Post by kansasnoob on 2011-02-23
Sorry for the long delay, here's the first bit of that:

[ATTACH]184241[/ATTACH]

[ATTACH]184242[/ATTACH]

I'll post more briefly.

---

### Post by kansasnoob on 2011-02-23
I did as suggested, and just as a double-check I added "> BIS.diff.txt" which created a blank file:

[ATTACH]184251[/ATTACH]

[ATTACH]184252[/ATTACH]

[ATTACH]184253[/ATTACH]

Those were all run using my Maverick on sda1. At a quick glance I see nothing really wrong there. I'll soon try this with Hardy which I recently installed on sdb1 for some unrelated testing.

---

### Post by kansasnoob on 2011-02-24
Testing this from Hardy/8.04.4 now and gawk is not installed:

```
lance@lance-desktop:~$ gawk -W version
The program 'gawk' is currently not installed.  You can install it by typing:
sudo apt-get install gawk
bash: gawk: command not found

```

You can see I have BIS in home:

```
lance@lance-desktop:~$ ls
**boot_info_script.sh**  Documents  Music     Public     Videos
Desktop              Examples   Pictures  Templates

```

But then I get this:

```
lance@lance-desktop:~$ sudo bash boot_info_script.sh BIS_busybox_awk.txt

boot_info_script version: 0.56        [8 February 2011]

"gawk" could not be found.

Please install the missing program(s) and run boot_info_script again.

```

But after installing gawk it runs OK:

[ATTACH]184375[/ATTACH]

---

### Post by Gert Hulselmans on 2011-02-24
busybox's awk is probably not installed on Ubuntu 8.04.

On Ubuntu 10.10, I get the following when gawk is not installed:
```
$ sudo bash ./boot_info_script.sh

boot_info_script version: 0.56        [8 February 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/username/boot_info_script/bootinfoscript/".
```
What is the output of:
```
type busybox
which busybox
```
Thanks for the files.

---

### Post by kansasnoob on 2011-02-24
I hope this helps:

```
lance@lance-desktop:~$ type busybox
bash: type: busybox: not found
lance@lance-desktop:~$ which busybox
lance@lance-desktop:~$ aptitude show busybox
Package: busybox
State: not installed
Version: 1:1.1.3-5ubuntu12
Priority: optional
Section: universe/utils
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 524k
Depends: libc6 (>= 2.7-1)
Conflicts: busybox-static
Replaces: busybox-static
Description: Tiny utilities for small and embedded systems
 BusyBox combines tiny versions of many common UNIX utilities into a single
 small executable. It provides minimalist replacements for the most common
 utilities you would usually find on your desktop system (i.e., ls, cp, mv,
 mount, tar, etc.). The utilities in BusyBox generally have fewer options than
 their full-featured GNU cousins; however, the options that are included provide
 the expected functionality and behave very much like their GNU counterparts. 
 
 This package installs the BusyBox binary but does not install symlinks for any
 of the supported utilities. You can use /bin/busybox --install to install
 BusyBox to the current directory (you do not want to do this in / on your
 Debian system!).

```

Sorry to be a pain but I needed to do something else Hardy related and think it would be nice, although not necessary, to have BIS run with Hardy since the server version is supported until April 2013. The desktop version reaches end-of-life this April, along with Karmic.

---

### Post by VMC on 2011-02-24
> **Gert Hulselmans said:**
> ...@ all
Last version of BIS is able to use "busybox awk". I only tested it on Ubuntu 10.10 and for my configuration, there was no difference between BIS with "gawk" and BIS with "busybox awk", except for the extraction of the embedded config file of grub4dos.

How to test:
- Download the last development version of BIS
- Uninstall gawk if installed and run BIS:
```
sudo bash boot_info_script.sh BIS_busybox_awk.txt
```- Install gawk if installed and run BIS:
```
sudo bash boot_info_script.sh BIS_gawk.txt
```- Make the diff:
```
diff -u BIS_busybox_awk.txt BIS_gawk.txt
```If "busybox awk" is reliable, "diff" shouldn't give any output.


Lucid busybox installed:

```
$ busybox
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) multi-call binary
```


**_EDIT2_**:

Alls well now after downloading the correct bis file. I tried to be cute and replace gawk with awk in an older bis file, testing then reversing the process:

Results: diff -u BIS_busybox_awk.txt BIS_gawk.txt or

md5sum BIS_busybox_awk.txt BIS_gawk.txt
b7a9f1302c85de176db4315ec4f29e53  BIS_busybox_awk.txt
b7a9f1302c85de176db4315ec4f29e53  BIS_gawk.txt

---

### Post by Gert Hulselmans on 2011-02-24
@ VMC
Did you need to install busybox or not?

---

### Post by VMC on 2011-02-24
> **Gert Hulselmans said:**
> @ VMC
Did you need to install busybox or not?

No, that's why I listed it above. You must have missed it with all my edits:

LUCID

$ busybox
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) multi-call binary

EDIT again: I edit my previous posts above to reflect correct info

---

### Post by VMC on 2011-02-24
In regards to Kansas busybox errors. Here's what I found using my released 8.04 LTS CD:

```
ubuntu@ubuntu:~$ busybox
The program 'busybox' can be found in the following packages:
 * busybox (You will have to enable component called 'universe')
 * busybox-static (You will have to enable component called 'universe')
Try: sudo apt-get install <selected package>
bash: busybox: command not found
ubuntu@ubuntu:~$ **locate busybox**
*/usr/lib/initramfs-tools/bin/busybox*
/usr/share/doc/busybox-initramfs
/usr/share/doc/busybox-initramfs/changelog.Debian.gz
/usr/share/doc/busybox-initramfs/copyright
/var/cache/apt/archives/busybox-initramfs_1%3a1.1.3-5ubuntu12_i386.deb
/var/lib/dpkg/info/busybox-initramfs.list
/var/lib/dpkg/info/busybox-initramfs.md5sums
==============================
ubuntu@ubuntu:~$ /usr/lib/initramfs-tools/bin/busybox
**BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) multi-call binary**


```

So busybox is there just hidden.

---

### Post by Gert Hulselmans on 2011-02-24
> **kansasnoob said:**
> Sorry to be a pain but I needed to do something else Hardy related and think it would be nice, although not necessary, to have BIS run with Hardy since the server version is supported until April 2013.
If the Ubuntu devs won't update mawk to the last version (which is very unlikely), Hardy users will need to install gawk.

I confirmed some other mawk 1.33 bugs on launchpad (that are fixed in the last mawk 1.34 version). I hope it will help.

@ VMC, can you test if the hidden busybox version works?
*Test by changing "busybox" to **"/usr/lib/initramfs-tools/bin/busybox*" and running the diff with gawk installed again.
```
sed -e 's|*busybox*|*/usr/lib/initramfs-tools/bin/busybox*|g' boot_info_script.sh > boot_info_script-busybox-awk-hidden.sh
```
**Edit: ***"/usr/lib/initramfs-tools/bin/busybox*" of Ubuntu 10.10 doesn't work:
```
Math support is not compiled in
```

---

### Post by VMC on 2011-02-24
> **Gert Hulselmans said:**
> If the Ubuntu devs won't update mawk to the last version (which is very unlikely), Hardy users will need to install gawk.

I confirmed some other mawk 1.33 bugs on launchpad (that are fixed in the last mawk 1.34 version). I hope it will help.

@ VMC, can you test if the hidden busybox version works?
*Test by changing "busybox" to **"/usr/lib/initramfs-tools/bin/busybox*" and running the diff with gawk installed again.
```
sed -e 's|*busybox*|*/usr/lib/initramfs-tools/bin/busybox*|g' boot_info_script.sh > boot_info_script-busybox-awk-hidden.sh
```**...**

Yes, it works on Ubuntu 8.04 LTS!:

```
$ sudo bash boot_info_script-busybox-awk-hidden.sh BIS_busybox_awk.txt

boot_info_script version: 0.56        [8 February 2011]


"gawk" could not be found, using "/usr/lib/initramfs-tools/bin/busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdc...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sdc1 for information... 

Finished. The results are in the file "BIS_busybox_awk.txt"
located in "/home/ubuntu/".

```

---

### Post by Gert Hulselmans on 2011-02-24
Don't you get the following in your output file?
```
=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```
In you don't get it, can you do a diff between the gawk verson and this version?

---

### Post by VMC on 2011-02-24
> **Gert Hulselmans said:**
> Don't you get the following in your output file?
```
=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```In you don't get it, can you do a diff between the gawk verson and this version?

No it works using 8.04. gawk is not installed. Installing gawk then running bis using gawk. I get the following differences, between using "hidden busybox" and "gawk":

```
ubuntu@ubuntu:~$ diff -u BIS_busybox_awk.txt BIS_gawk.txt
--- BIS_busybox_awk.txt    2011-02-24 21:44:22.958771128 +0000
+++ BIS_gawk.txt    2011-02-24 21:44:58.166771198 +0000
@@ -96,11 +96,12 @@
 sdd1: __________________________________________________________________________
 
     File system:       vfat
-    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
+    Boot sector type:  Syslinux 3.53-3.86
     Boot sector info:  Syslinux looks at sector 2837548 of /dev/sdd1 for its 
-                       second stage. According to the info in the boot 
-                       sector, sdd1 starts at sector 0. But according to the 
-                       info from fdisk, sdd1 starts at sector 63.
+                       second stage. Integrity check of Syslinux failed. 
+                       According to the info in the boot sector, sdd1 starts 
+                       at sector 0. But according to the info from fdisk, 
+                       sdd1 starts at sector 63.
     Operating System:  
     Boot files:        /syslinux/syslinux.cfg /ldlinux.sys
 
@@ -289,7 +290,4 @@
 
 sdb 
 
-=============================== StdErr Messages: ===============================
-
-boot_info_script-busybox-awk-hidden.sh: line 1463: [: 4.24306e+09: integer expression expected

```

---

### Post by Gert Hulselmans on 2011-02-24
> **VMC said:**
> No it works using 8.04. gawk is not installed.
:D

Can you upload ldlinux.sys of sdd1?
And sdd1_ldlinux_sys.bin:
```
sudo dd if=/dev/sdd1 of=sdd1_ldlinux_sys.bin skip=2837548 bs=512 count=500
```

Last version should try *"/usr/lib/initramfs-tools/bin/busybox*" after the "busybox" in the $PATH. Can you test it that it works out of the box in 8.04 (and other versions)?

---

### Post by VMC on 2011-02-24
> **Gert Hulselmans said:**
> :D

Can you upload ldlinux.sys of sdd1?
And sdd1_ldlinux_sys.bin:
```
sudo dd if=/dev/sdd1 of=sdd1_ldlinux_sys.bin skip=2837548 bs=512 count=500
```

 I remember, that sdd1 is a Windows created XP install. I think the program that created the syslinux was called "WinSetupFromUSB_1-0-beta7". It doesn't have ldlinux:
$ ls -a
.  ..  boot.ini  $LDR$  ntdetect.com  ntldr  .Trash-999  txtsetup.sif  $WIN_NT$.~BT  $WIN_NT$.~LS


At any rate here is the compressed dd file per your request.

---

### Post by Gert Hulselmans on 2011-02-24
Now sdd is probably another disk (like sdc).

In your previous report, BIS found on sdd1 the following boot files:
```
Boot files:        /syslinux/syslinux.cfg /ldlinux.sys
```It should have detected boot.ini ntldr and ntdetect.com too, if it was really the same partition.

The file you uploaded was completely filled with zeros, which doesn't correspond with both BIS outputs.

---

### Post by VMC on 2011-02-24
I'll have to rern the busybox & gawk bis. I somewhere along the way got off track.

Ubuntu 8.04 CD was taking so long to boot I made a usb boot drive. I will start that again test. I think I had some usb stick in there at one point.

---

### Post by VMC on 2011-02-24
@Gert,

Ubuntu 8.04 LTS is booting off of sdc1 USB hard drive:
```
/dev/sda1: UUID="D8C0EF8FC0EF7264" LABEL="HP" TYPE="ntfs" 
/dev/sda2: UUID="C8C08EAFC08EA374" LABEL="NTFS" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="ef49d6c0-b094-4deb-9805-52707a9cd12b" 
/dev/sda6: LABEL="Kubuntu" UUID="debfdd2e-50ec-4933-b709-88f708449e5e" TYPE="ext4" 
/dev/sda7: UUID="baacd97d-de32-4cc4-a0a7-0204225b7fe0" TYPE="ext4" 
/dev/sda8: LABEL="Lucid" UUID="03568d9f-8220-4f89-b1d2-4930cb038fd1" TYPE="ext4" 
/dev/sda9: LABEL="Mint" UUID="f82f2019-fe3c-413b-8f7b-b5569462f33f" TYPE="ext4" 
/dev/sda10: LABEL="Lucid2" UUID="47e63f77-5e78-4777-a1e4-420088742cf3" TYPE="ext4" 
/dev/**sdc1**: LABEL="BOOT" UUID="CD0A-BA06" TYPE="vfat" 
/dev/sdc2: UUID="1E5B6E554ECC15BB" LABEL="usb-ntfs" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

```Here's the results of the busybox and gawk output:
```
=== BUSYBOX =========================================================
$ sudo bash boot_info_script-busybox-awk-hidden.sh BIS_busybox_awk.txt

boot_info_script version: 0.56        [8 February 2011]


"gawk" could not be found, using "/usr/lib/initramfs-tools/bin/busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdc...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sdc1 for information... 
Searching sdc2 for information... 

Finished. The results are in the file "BIS_busybox_awk.txt"
located in "/home/ubuntu/".
=== GAWK =====================================
~$ sudo bash boot_info_script.sh BIS_gawk.txt

boot_info_script version: 0.56        [8 February 2011]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdc...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sdc1 for information... 
Searching sdc2 for information... 

Finished. The results are in the file "BIS_gawk.txt"
located in "/home/ubuntu/".
=== diff -u ==============================
$ diff -u BIS_busybox_awk.txt BIS_gawk.txt
--- BIS_busybox_awk.txt    2011-02-25 03:12:27.288554482 +0000
+++ BIS_gawk.txt    2011-02-25 03:18:49.989547489 +0000
@@ -96,11 +96,12 @@
 sdc1: __________________________________________________________________________
 
     File system:       vfat
-    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
+    Boot sector type:  Syslinux 3.53-3.86
     Boot sector info:  Syslinux looks at sector 2837548 of /dev/[COLOR=Red]**sdc1**[/COLOR] for its 
-                       second stage. According to the info in the boot 
-                       sector, sdc1 starts at sector 0. But according to the 
-                       info from fdisk, sdc1 starts at sector 63.
+                       second stage. Integrity check of Syslinux failed. 
+                       According to the info in the boot sector, sdc1 starts 
+                       at sector 0. But according to the info from fdisk, 
+                       sdc1 starts at sector 63.
     Operating System:  
     Boot files:        /syslinux/syslinux.cfg /ldlinux.sys
 
@@ -289,7 +290,4 @@
 
 sdb 
 
-=============================== StdErr Messages: ===============================
-
-boot_info_script-busybox-awk-hidden.sh: line 1463: [: 4.24306e+09: integer expression expected

```Do you need me to dump mbr of the sdc1 as before?

---

### Post by Gert Hulselmans on 2011-02-25
Not the MBR but ldlinux.sys and the output file of the dd command.

---

### Post by VMC on 2011-02-25
> **Gert Hulselmans said:**
> Not the MBR but ldlinux.sys and the output file of the dd command.

Ubuntu 8.04 LTS is now on "sdb1", so the bin file is from this output:
```
sudo dd if=/dev/sdb1 of=sdb1_ldlinux_sys.bin skip=2837548 bs=512 count=500
```

Both .sys and .bin attached in compressed file.

---

### Post by kansasnoob on 2011-02-25
Going back to post #90 I did as explained there in a testing 10.04.2 on my sdb3:

[ATTACH]184470[/ATTACH]

[ATTACH]184471[/ATTACH]

[ATTACH]184472[/ATTACH]

FYI term.txt shows just exactly what I did in terminal.

Oops, failed to mention that looks fine to me.

I don't think we should be too concerned about this working with older versions of Ubuntu. That is, I think it's reasonable to ask that the BIS be run from certain media, as long as it's a fairly wide range of media.

I am curious if I should test this with any other specific operating systems? If so it'll likely be after the 3rd due to iso-testing, but I'm more than willing.

---

### Post by kansasnoob on 2011-02-25
I hadn't booted into Natty in a few days and this evening I noticed there were updates to both grub-common and grub-pc so I ran the BIS both with and w/o gawk:

[ATTACH]184508[/ATTACH]

[ATTACH]184509[/ATTACH]

No difference and the only "oddities" I notice are:

```
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location on BIOS 
    drive 1 (0x80) and looks in partition 14 for /boot/grub.
```

But that's an old issue.

```
======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  cf b4 ac 97 a5 ba e0 b2  d4 2e a9 8b e7 67 ed 0e  |.............g..|
00000010  69 48 4c 36 f2 b9 9c a6  3c f9 54 89 b0 ea 5f 5e  |iHL6....<.T..._^|
00000020  0f 85 09 3f dc e1 61 2f  0b c7 64 85 8f 89 64 cc  |...?..a/..d...d.|
00000030  18 d8 db 30 9b 32 b2 ab  d0 67 c3 dc fd fd bd ff  |...0.2...g......|
00000040  97 4b c3 4f 3e 1c 21 2f  d3 7b b2 22 14 49 1b d5  |.K.O>.!/.{.".I..|
00000050  bc 7a ff ca 51 c9 d2 06  2c 23 d3 38 07 6c 46 85  |.z..Q...,#.8.lF.|
00000060  c8 87 83 10 61 56 a4 bf  02 02 64 65 a4 cf d6 71  |....aV....de...q|
00000070  39 0d 1f d2 73 e1 9d 83  9a b1 28 93 1d 09 e3 a1  |9...s.....(.....|
00000080  f8 70 80 c5 ad 31 ce 73  9f 6d ee c3 d8 8e 0e 36  |.p...1.s.m.....6|
00000090  77 6b 7b 6f 3d 84 16 95  b7 5b 60 51 67 cd be 3f  |wk{o=....[`Qg..?|
000000a0  33 b3 23 00 ca 21 30 6c  6d 92 14 7c 71 7a 79 71  |3.#..!0lm..|qzyq|
000000b0  28 95 1e d5 68 dc 9d e8  1d 10 8e f0 2d 2c 5e b6  |(...h.......-,^.|
000000c0  38 d3 e8 9f 42 0e 18 24  ff 5d bb 0a bb 01 a3 94  |8...B..$.]......|
000000d0  0a f3 3c ce 52 19 f6 76  36 fa 16 d5 98 7d 2d 65  |..<.R..v6....}-e|
000000e0  ae 6d 3b 91 cc 87 bb 02  98 ed 2e 18 b8 f2 64 6e  |.m;...........dn|
000000f0  cc d9 75 14 76 43 c1 bf  15 e6 70 00 08 da 19 c4  |..u.vC....p.....|
00000100  34 f6 c9 ea d2 59 3c 8b  2b 68 e7 b8 c2 ca 9f e8  |4....Y<.+h......|
00000110  84 b1 54 c5 99 ee ef ef  0b 67 d4 c9 05 b8 66 23  |..T......g....f#|
00000120  73 8d d0 23 8e bd 07 d4  8a cd be 48 bf b4 c4 95  |s..#.......H....|
00000130  df 9f cc ce 88 75 e6 bb  85 36 51 f7 36 af 60 dd  |.....u...6Q.6.`.|
00000140  08 06 26 2f 03 c5 38 5f  0b 46 2e 84 af 77 65 d1  |..&/..8_.F...we.|
00000150  10 80 84 10 d8 9f bc 92  1c 4d 1e fd 37 df 52 3e  |.........M..7.R>|
00000160  4f a6 1d 27 84 f0 94 1c  a0 33 d5 92 c4 d8 ae c8  |O..'.....3......|
00000170  89 54 68 75 d3 a2 46 ed  7a bb fe b5 89 e0 f9 21  |.Thu..F.z......!|
00000180  79 58 24 01 d0 db e8 63  37 dd 80 7f a7 93 a0 90  |yX$....c7.......|
00000190  da ee 5d 2a 24 40 e3 fe  62 e6 a9 80 f8 e6 d7 91  |..]*$@..b.......|
000001a0  b4 a4 92 cf c3 78 22 c8  b1 b6 0f 4e a4 2a 83 fc  |.....x"....N.*..|
000001b0  f3 d7 08 c0 e6 41 c5 70  6f 92 a2 18 88 77 00 fe  |.....A.po....w..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 d3 8a 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

That I don't really understand at all. I'd performed a default Hardy install on sdb (with sdb1 as /, sdb2 as extended, and sdb5 as SWAP), then shrunk sdb1, created an sdb3, and used it as / for a Lucid install. I'm fairly certain that I just accepted the default location (sda1) for grub installation, so I don't know why there'd be any bootloader on sdb2 :confused:

Edit: I don't anticipate changing anything on sdb until about Tuesday when I'd expect iso-testing for Alpha 3 to begin in case you need more info from sdb2.

---

### Post by oldfred on 2011-02-26
You see the unknown boot loader a lot, especially now that partitioning starts at sector 2048 instead of 63. The script had signatures for many boot loaders but not all, so if it does not see zeros it posts the unknown. But the partitioning software does not erase data in the partition boot sector. So what you are seeing is old data that was on the drive and was moved. But the new partition boot sector did not have to be overwritten so it still has all that old data.

---

### Post by Quackers on 2011-02-26
I get the unknown bootloader for both my extended partitions. I assumed that it's normal. I've seen it a lot anyway :-)

---

### Post by VMC on 2011-02-26
I wonder how the newer "green 512-byte sectors to 4096-byte-byte sector drive.sectors" drives are effected. 
I have a "normal" 512-byte sata drive.

---

### Post by Gert Hulselmans on 2011-02-26
@ VMC
Thanks for the files.

@ kansasnoob
Can you do:
```
sudo dd if=/dev/sdb of=sdb_possible_bootloader.bin bs=512 count=63
```
The bytes at offset 0x1FE-0x1FF (0x55aa) suggest that there is a boot loader on this partition.

---

### Post by kansasnoob on 2011-02-27
Thanks Gert:

sudo dd if=/dev/sdb of=sdb_possible_bootloader.bin bs=512 count=63

It's not a big deal but I wonder why I'd have ended up with a bootloader on the extended partition without specifically telling it to do so :confused:

---

### Post by Gert Hulselmans on 2011-02-28
@ kansasnoob
Oops, I meant:
```
sudo dd if=/dev/sdb2 of=sdb2_possible_bootloader.bin bs=512 count=63
```

---

### Post by kansasnoob on 2011-02-28
I hadn't changed anything yet on that drive so that's cool :)

[ATTACH]184729[/ATTACH]

I'd bet Natty Alpha 3 iso testing will begin either tomorrow or the next day so I'd then wipe my sdb drive.

I just want to stress how thankful I am that you've dedicated so much time to this project. Thank you for helping so much.

---

### Post by Quackers on 2011-02-28
> **kansasnoob said:**
> I just want to stress how thankful I am that you've dedicated so much time to this project. Thank you for helping so much.

I'd agree 100% with that! Many thanks indeed :-)

---

### Post by VMC on 2011-03-03
@Gert,

I couldn't use an attachment using private mail so here is the latest RESULTS.txt file.
Interestingly natty doesn't have gawk install, but using busybox instead.

I have that Ubuntu 8.04.1 installed on the USB harddrive. Let me know if I need to upload further files.

---

### Post by Gert Hulselmans on 2011-03-03
@ VMC
The new Syslinux is installed correctly.
But I am not sure if Syslinux of Ubuntu 8.04.1 has "SYSLINUX 4.02 debian-20101016" (I though it had SYSLINUX 3.63). or did you install it from another version?

Can you also run BIS v055 for all the grub2 MBR/PBR files? In the last test versions, BIS will only look for core.img on the same hard disk as where the boot file is located.
Probably, most of those MBR/PBR files are broken anyway (grub2 is updated and core.img moved to another location).

---

### Post by VMC on 2011-03-03
> **Gert Hulselmans said:**
> @ VMC
The new Syslinux is installed correctly.
But I am not sure if Syslinux of Ubuntu 8.04.1 has "SYSLINUX 4.02 debian-20101016" (I though it had SYSLINUX 3.63). or did you install it from another version?

Can you also run BIS v055 for all the grub2 MBR/PBR files? In the last test versions, BIS will only look for core.img on the same hard disk as where the boot file is located.
Probably, most of those MBR/PBR files are broken anyway (grub2 is updated and core.img moved to another location).

Here it is...

---

### Post by Gert Hulselmans on 2011-03-03
@ VMC
They seem all broken too :D.

@ all
Last version supports (at least it should) displaying embedded config files of core.img.
Embedded config files are for example used for cross-drive installs.
Currently it will only work with Grub2 v1.99, unless somebody gives me the neseccary images for  Grub2 v1.98.

---

### Post by VMC on 2011-03-03
> **Gert Hulselmans said:**
> @ VMC
The new Syslinux is installed correctly.
But I am not sure if Syslinux of Ubuntu 8.04.1 has "SYSLINUX 4.02 debian-20101016" (I though it had SYSLINUX 3.63). or did you install it from another version?

...Yes, I did install it from natty's Startup Disk Creator.
That's why.

---

### Post by kansasnoob on 2011-03-03
Just returning to this now that iso/upgrade testing is complete. I'm attaching the BIS output of my current setup using the latest BIS:

[ATTACH]185009[/ATTACH]

I see a few additions like:

```
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location on BIOS 
    drive 1 (0x80) and [B][COLOR="Red"]uses an embedded config file:
    
    ---------------------------------------------------------------------------
    -----
    search.fs_uuid 6dc455ef-6844-4d31-846a-d2ff4a9c256f root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.[/COLOR][/B]
 => No boot loader is installed in the MBR of /dev/sdb.
```

And:

```
sda16: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda16 
                       and looks at sector 390182206 of the same hard drive 
                       for core.img. core.img is at this location on BIOS 
                       drive 1 (0x80) and [B][COLOR="Red"]uses an embedded config file: 
                       -------------------------------------------------------
                       ------------------------- search.fs_uuid 
                       7a90aa0c-2377-48e4-97ad-20283c962abc root set 
                       prefix=($root)/boot/grub-------------------------------
                       -------------------------------------------------.[/COLOR][/B]
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```

---

### Post by Gert Hulselmans on 2011-03-04
@ kansasnoob
Thanks.

The content of the embedded config file looks correct although it still needs to be formatted properly.

---

### Post by kansasnoob on 2011-03-05
**Recognizable progress I think** \\:D/

The best way to test something is always when something is broke, eh? Yesterday I decided to install PureOS since they recently released a Gnome version. After doing so it, and everything else, failed to boot but I got busy with other things so I just restored boot to my Maverick on sda2 and everything but PureOS booted fine.

I should probably mention that PureOS recognized my drive designations in the opposite order. That is Ubuntu, and so far every other OS I've tried, has recognized my 500GB SATA drive as sda and my 80GB IDE drive as sdb. PureOS recognized the 80GB drive as sda and the 500GB drive as sdb. While I'd never encountered that on my own hardware before I was aware of that happening even with Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1659542](http://ubuntuforums.org/showthread.php?t=1659542)

BTW I suspect a large part of the problem is PureOS's fstab:

```
=============================== sda17/etc/fstab: ===============================

--------------------------------------------------------------------------------
/dev/sdb17 / auto defaults 1 1
aufs / aufs defaults 0 0 # AutoUpdate
proc /proc proc defaults 0 0 # AutoUpdate
sysfs /sys sysfs defaults 0 0 # AutoUpdate
devpts /dev/pts devpts gid=5,mode=620 0 0 # AutoUpdate
tmpfs /dev/shm tmpfs defaults 0 0 # AutoUpdate
/dev/sr0 /media/sr0 iso9660 auto,noatime,users,suid,dev,exec,ro,iocharset=utf8 0 0 # AutoUpdate
/dev/sda1 /mnt/sda1 ext4 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sda5 none swap auto,defaults,pri=1 0 0 # AutoUpdate
/dev/sdb1 /mnt/sdb1 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb2 /mnt/sdb2 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb3 /mnt/sdb3 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb5 /mnt/sdb5 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb6 /mnt/sdb6 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb7 /mnt/sdb7 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb8 /mnt/sdb8 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb9 none swap auto,defaults,pri=1 0 0 # AutoUpdate
/dev/sdb10 /mnt/sdb10 ext4 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb11 /mnt/sdb11 ext4 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb12 /mnt/sdb12 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb13 /mnt/sdb13 ext4 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb14 /mnt/sdb14 ext4 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb15 /mnt/sdb15 ext4 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb16 /mnt/sdb16 ext4 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb18 /mnt/sdb18 ext4 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
--------------------------------------------------------------------------------
```

Yuck in many ways, I'm almost glad it didn't boot ;)

Anyway just ignore my personal boot dilemma. I just want you to know what I actually started with when I ran the BIS. I began by running 'dpkg-reconfigure grub-pc' in my Maverick on sda2 and chose to install grub to sda, sdb, and sda2. I then tried booting the PureOS entry which failed so I next edited the kernel parameter with "single" to try and troubleshoot the problem.

NOTE: It's very important here to remember that PureOS recognizes the drives in the opposite order.

So while I was in the PureOS tty I updated it's grub (it had failed to find any other OS's during installation) and after seeing that it did now find the other OS's I ran 'grub-install /dev/sdb' after being certain that it still recognized the 500GB drive as sdb. It still failed to boot but everything else in it's grub menu did :D

Anyway I booted back into Maverick on sda2 and downloaded the latest BIS. I know for a fact that it's grub was installed to the MBR of sdb and it's own PBR. The MBR of sda I know is "assigned" to PureOS on sda17. This is where I think the improvement becomes apparent:

```
=> Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location on 
    BIOS drive 1 (0x80) and looks in partition 17 for (,msdos17)/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location on 
    BIOS drive 1 (0x80) and looks in partition 2 for (,msdos2)/boot/grub.
```

The sda data looks perfect, but look closely at the sdb data. 

```
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location on 
    **[COLOR="Red"]BIOS drive 1[/COLOR]** (0x80) and looks in partition 2 for (,msdos2)/boot/grub.
```

Now remember I ran the BIS from sda2 so BIOS drive 1 should be sda, eh? If so I think that's definite progress. I'm attaching the results just so you can see. I'll likely use nano in a chroot to replace that awful fstab when I have time but I need some fresh air ATM.

Hats off to Gert Hulselmans. You're amazing :guitar:

---

### Post by kansasnoob on 2011-03-05
Before heading outside I decided to try the old BIS:

```
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #17 for (,msdos17)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
```

I also forgot to attach the newer BIS results, give me a few minutes.

---

### Post by kansasnoob on 2011-03-05
Here we go. I also ran a diff -u:

[ATTACH]185171[/ATTACH]

[ATTACH]185172[/ATTACH]

[ATTACH]185173[/ATTACH]

The really interesting part to me is this:

```
-============================= Boot Info Summary: ==============================
 
- => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
-    partition #17 for (,msdos17)/boot/grub.
- => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
-    partition #2 for (,msdos2)/boot/grub.
+============================= Boot Info Summary: ===============================
 
-sda1: _________________________________________________________________________
+ => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
+    1 of the same hard drive for core.img. core.img is at this location on 
+    BIOS drive 1 (0x80) and looks in partition 17 for (,msdos17)/boot/grub.
+ => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
+    1 of the same hard drive for core.img. core.img is at this location on 
+    **[COLOR="Red"]BIOS drive 1[/COLOR]** (0x80) and looks in partition 2 for (,msdos2)/boot/grub.
```

Awesome!

---

### Post by Gert Hulselmans on 2011-03-05
BIS just reads out the BIOS drive number stored in core.img itself. I think Grub2 normally will use the BIOS drive number passed by the BIOS.

The grub2 (v1.97-1.98 ) install on sdb2, doesn't load the config file from sdb2, but from sda2:
```
sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  
```I am not sure if grub2 (v1.97-1.98 ) uses the the embedded BIOS drive number or not, or that is also uses an embedded config file.

Can you attach the first 63 sectors of sdb?

It would be an interesting test to install grub2 (v1.97-1.98 ) to sdb and to let it search for its config file on sdb1.

The output might look like this:
```
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector
      1 of the same hard drive for core.img. core.img is at this location on
      BIOS drive 2 (0x81) and looks in partition 1 for (,msdos1)/boot/grub.
```Installing grub2 (v1.97-1.98 ) to sdb1, would be a nice test case too.

BTW, to generate gzipped output files, you can run:
```
sudo bash boot_info_script.sh -g RESULTS_NEW.txt
sudo bash boot_info_script.sh --gzip RESULTS_NEW.txt
```This will create 2 files:

[LIST]
[*]RESULTS_NEW.txt ==> uncompressed output file
[*]RESULTS_NEW.txt.gz ==> gzipped output file
[/LIST]
Thanks for all the testing.

---

### Post by kansasnoob on 2011-03-06
Before making any other changes here's the first 63 sectors of sdb:

[ATTACH]185250[/ATTACH]

BTW thats with Maverick's grub2 installed to sdb, which is 1.98+20100804-5ubuntu3.1.

I'll be in and out quite a bit for the next couple of days, so apologies in advance for the long delays between posts.

---

### Post by kansasnoob on 2011-03-06
No time to do more testing today but I need to add one comment in case someone performs a forum search for "PureOS". I'd already noted that the fstab was a mess, but during installation it says:

[ATTACH]185288[/ATTACH]

But the PureOS installation process also does not format the selected partition :)

So I had a conglomeration of both Natty and PureOS files on the same partition :P

Even after performing a fresh install of PureOS it still wouldn't boot due to the crazy fstab but that was easy to fix.

Again, I'm only mentioning this so those who perform a search in the forums get decent results :)

---

### Post by kansasnoob on 2011-03-07
I'm not quite sure what to do here :)

Back in post #132 you said:

> It would be an interesting test to install grub2 (v1.97-1.98 ) to sdb and to let it search for its config file on sdb1.


And more :confused:

Anyway I'm taking a break from being wet and slightly cold so I booted into my Lucid on sda3 which uses '(GNU GRUB 1.98-1ubuntu10)'.

As usual I ran "dpkg-reconfigure grub-pc" and selected sda, sdb, and sda3 (since those are the default options) and I think the results look good. Particularly this:

```
=> Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location on 
    BIOS drive 1 (0x80) and looks in partition 3 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location on 
    BIOS drive 1 (0x80) and looks in partition 3 for /boot/grub.
```

Now, if I'm reading that properly there is a discrepancy regarding sdb. I know that grub on sda3 is installed to the mbr of sdb but it shows:

> Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img.

But just after that it shows:

> core.img is at this location on 
    **[COLOR="Red"]BIOS drive 1[/COLOR]** (0x80) and looks in partition 3 for /boot/grub.

I would think clearly that "the same drive" and "BIOS drive 1" are two different things in that scenario. I'm curious what would happen if we tried to "drop" the earlier part of that for all drives?

I'm attaching the full output, the lazy way :)

[ATTACH]185384[/ATTACH]

---

### Post by Gert Hulselmans on 2011-03-07
I meant, boot sdb1 (Ubuntu natty (development branch)) and install grub2 (v1.98 ) to sdb and sdb1.

---

### Post by kansasnoob on 2011-03-08
Sorry to take so long. In this test case I left grub on sda1/Natty installed to the MBR of sda, booted into sdb1/Natty and installed it's grub (1.99~rc1-3ubuntu3) to both sdb and sdb1. You might find this interesting:

```
lance@lance-desktop:~$ sudo bash boot_info_script.sh --gzip RESULTS.txt
[sudo] password for lance: 

boot_info_script version: 0.56        [8 February 2011]


[B][COLOR="Red"]"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.
[/COLOR][/B]
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sda11 for information... 
Searching sda12 for information... 
Searching sda13 for information... 
Searching sda14 for information... 
Searching sda15 for information... 
Searching sda16 for information... 
Searching sda17 for information... 
Searching sda18 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/lance/".

```

Note: this particular Natty has had almost no additional packages installed.

Now I can see why you wanted to see this:

```
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location on BIOS 
    drive 1 (0x80) and looks for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location on BIOS 
    drive 1 (0x80) and looks for (,msdos1)/boot/grub on this drive.
```

The sda data is correct but I suppose the sdb data is not totally correct, that is this bit would be correct:

```
Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img
```

But the part following that says:

```
core.img is at this location on BIOS 
    drive 1 (0x80) and looks for (,msdos1)/boot/grub on this drive.
```

I would think to be totally correct is should say BIOS drive 2, eh :confused:

I suppose likewise here:

```
sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 50626024 of the same hard drive 
                       for core.img. core.img is at this location on BIOS 
                       drive 1 (0x80) and looks for (,msdos1)/boot/grub on 
                       this drive.
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

```

[ATTACH]185469[/ATTACH]

Or maybe I don't know what I'm doing :D

---

### Post by kansasnoob on 2011-03-08
Just as a sanity check I installed qawk, reran the BIS, performed a diff -u between the results (w/> diff.txt) and the diff.txt is blank so we're cool there :)

---

### Post by kansasnoob on 2011-03-16
Not sure where we're at with this, and I've had very little time to play the past week or so, but I'd once mentioned the benefit of also seeing the output of "parted -l" along with the fdisk output provided by the BIS. The following thread shows a good example:

[http://ubuntuforums.org/showthread.php?t=1706662](http://ubuntuforums.org/showthread.php?t=1706662)

Before going any further I should mention that the "-l" option in parted was added in Ubuntu sometime after Hardy. Prior to that it was necessary to use "parted /dev/sdX print" :)

Anyway from that example the fdisk output in BIS shows:

> Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 * 16,126 488,409,087 488,392,962 f W95 Ext d (LBA)
/dev/sda5 16,128 281,567,891 281,551,764 7 HPFS/NTFS
/dev/sda6 281,569,280 479,909,887 198,340,608 83 Linux
/dev/sda7 479,911,936 488,409,087 8,497,152 82 Linux swap / Solaris
/dev/sda2 488,409,088 976,769,023 488,359,936 7 HPFS/NTFS


Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdb1 * 2,048 206,847 204,800 7 HPFS/NTFS
/dev/sdb2 206,848 266,102,528 265,895,681 7 HPFS/NTFS
/dev/sdb3 266,102,782 488,396,799 222,294,018 5 Extended
/dev/sdb5 266,102,784 488,394,751 222,291,968 7 HPFS/NTFS

And the parted -l output:

> Model: ATA ST3500418AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 8257kB 250GB 250GB extended boot, lba
5 8258kB 144GB 144GB logical ntfs
6 144GB 246GB 102GB logical ext4
7 246GB 250GB 4351MB logical linux-swap(v1)
2 250GB 500GB 250GB primary ntfs


Model: ATA ST3250318AS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 106MB 105MB primary ntfs boot
2 106MB 136GB 136GB primary ntfs
3 136GB 250GB 114GB extended
5 136GB 250GB 114GB logical ntfs


Sorry for the scrambling due to not using code tags but the OP on that thread failed to use them and I was too lazy to correct it, but what's the difference?

Well, parted lists things in their actual order. Yes, that can be parsed through anyway by looking at partition sizes, and in that example it makes no difference but on my own machine it's obvious:

```
lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6391

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5269    42323211   83  Linux
/dev/sda2            5270       10477    41833260   83  Linux
/dev/sda3           10478       15708    42018007+  83  Linux
/dev/sda4           15709       60801   362208801+   5  Extended
/dev/sda5           39292       45992    53825751   83  Linux
/dev/sda6           45993       52514    52387933+  83  Linux
/dev/sda7           52515       59192    53641003+  83  Linux
/dev/sda8           59193       60495    10466316   83  Linux
/dev/sda9           60496       60801     2457913+  82  Linux swap / Solaris
/dev/sda10          36642       39291    21286093+  83  Linux
/dev/sda11          33998       36641    21237898+  83  Linux
/dev/sda12          31366       33997    21141508+  83  Linux
/dev/sda13          28691       31365    21486906   83  Linux
/dev/sda14          18364       20924    20571169+  83  Linux
/dev/sda15          20925       23487    20587266   83  Linux
/dev/sda16          23488       26089    20900533+  83  Linux
/dev/sda17          26090       28690    20892501   83  Linux
/dev/sda18          15709       18363    21324800   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009614a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6781    54460416   83  Linux
/dev/sdb2            9470        9730     2085889    5  Extended
/dev/sdb5            9470        9730     2085888   82  Linux swap / Solaris
lance@lance-desktop:~$ sudo parted -l
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  43.3GB  43.3GB  primary   ext3            boot
 2      43.3GB  86.2GB  42.8GB  primary   ext3
 3      86.2GB  129GB   43.0GB  primary   ext3
 4      129GB   500GB   371GB   extended
18      129GB   151GB   21.8GB  logical   ext4
14      151GB   172GB   21.1GB  logical   ext4
15      172GB   193GB   21.1GB  logical   ext4
16      193GB   215GB   21.4GB  logical   ext4
17      215GB   236GB   21.4GB  logical   ext4
13      236GB   258GB   22.0GB  logical   ext4
12      258GB   280GB   21.6GB  logical   ext3
11      280GB   301GB   21.7GB  logical   ext4
10      301GB   323GB   21.8GB  logical   ext4
 5      323GB   378GB   55.1GB  logical   ext3
 6      378GB   432GB   53.6GB  logical   ext3
 7      432GB   487GB   54.9GB  logical   ext3
 8      487GB   498GB   10.7GB  logical   ext3
 9      498GB   500GB   2517MB  logical   linux-swap(v1)


Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  55.8GB  55.8GB  primary   ext4
 2      77.9GB  80.0GB  2136MB  extended
 5      77.9GB  80.0GB  2136MB  logical   linux-swap(v1)

```

Also partition sizes are more "human readable", but most importantly are the drive specs. For instance from that thread:

Model: ATA ST3500418AS (scsi)
Model: ATA ST3250318AS (scsi)

Or from my machine:

Model: ATA WDC WD5000AAKS-0 (scsi)
Model: ATA WDC WD800JB-00JJ (scsi)

That makes it pretty easy to Google "ST3500418AS" or "WD800JB-00JJ" and see if you're dealing with a SATA or IDE drive, etc ;)

Just a thought, and I'm not suggesting one replace or take precedence over the other, but both would be nice :D

OTOH it's not at all difficult to ask someone for the output of one additional command ;)

---

### Post by kansasnoob on 2011-03-22
Regarding this, I received the following PM:

> BIS development will be frozen for a month at least, due the lack of time.

So, if Gert is not able to do any more before Natty releases we need to use the latest BIS version in his sig using wget.

It should work as well as it ever did, that is it'll supply enough info to provide a starting point :)

I'm a bit burned out ATM and I'm trying to resume fixing things that have kept getting side-lined for about three years, like the lack of a kitchen :)

---

