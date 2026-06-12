---
title: "DVD Ripping Solutions: Ubuntu 7.10 Gutsy"
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by dcrooke on 2008-04-19
I've been playing with this for the last few days, and I found that a lot of the advice available online, while good, was often outdated, so I thought I'd post my findings.

Background: I've been playing with this kind of stuff a while - before DVD burners were affordable, I used to burn Video-CD format and convert NTSC and PAL video using homegrown shell scripts and tools like transcode and ffmpeg under Red Hat 7.2 ... now, I was just looking for an easy solution for the classic problem of backing up a commercial dual layer 9GB DVD and burning to single layer 4.7GB DVD-R.

Here's what I found:

Many modern DVDs have copy protection, not just in the sense of CSS encryption, but also by having lots of non-standard formatting - micro-cells that aren't used, enhanced region coding where the disk marks itself as multiple region types, etc. etc. Most of the Linux ripping tools are scripts / GUIs which run in front of video editing software like transcode, which is designed for - ahem - more legitimate purposes and has trouble with these funny formats.

[dvd::rip]("https://help.ubuntu.com/community/DVD::Rip") installs cleanly in Ubuntu 7.10, but its ripping process is a bit flaky and does not work on many modern commercial disks.

The most comprehensive "pure Linux" tool appears to be [k9copy]("https://help.ubuntu.com/community/K9Copy") but it also has limitations with modern DVDs and can be a bit flaky (e.g. when I tried to turn on OpenGL, it crashed and I needed to manually edit the config file under .kde/share to get it working again)

Alas, the best comprehensive tools are those available as MS-Windows binaries, in particular the pairing of [DVD Decrypter]("http://www.dvddecrypter.org.uk/") and [DVD Shrink]("http://www.afterdawn.com/software/video_software/dvd_rippers/dvd_shrink.cfm"). I have tried these under both (a) Wine and (b) Windows XP under VMWare, and while they work well on both, on my system using Wine is more than 3x faster (which is not unexpected if you think about how Wine and VMWare work). These Windows programs are, of course, technically illegal in certain countries, and so can be hard to find, but the preceding links were working as of April 2008.

The site mrbass.org has [pretty good documentation]("http://www.mrbass.org/linux/ubuntu/dvdshrink/") out there for getting these working on older versions of Wine and Ubuntu, but some minor adjustments are needed for the Wine 0.9.46 version that is loaded with Gutsy. 

I made the following changes:

1. Ignore the following stuff in the mrbass.org instructions:

a. there is no need to mess with hdparm ... Gutsy maps your IDE DVD drive as the SCSI device /dev/scd0
b. there is no need to edit the wine config files to set the Windows version ... Wine 0.9.46 defaults to Windows 2000 which is fine 
c. the dll.zip install is not required

Simply run **winecfg** either from the command line or the GUI (Applications -> Wine -> Configure Wine) and make sure the DVD drive is mapped (/media/cdrom0). I also recommend mapping your home directory to a suitable letter (e.g. H:\) so you can put the DVD data files there for ease of burning.

2. To work, DVD Decrypter needs access to the physical drive itself, not to a filesystem mounted under Linux. Wine uses soft links in the directory ~/.wine/dosdevices to map Windows drive letters to Linux directories, with the syntax **x:** and you can use the syntax **x::** (note the double colon) to map a physical drive. This does not appear to be configurable from the **winecfg** GUI, so you'll need to open a command shell and do the following:
[B]
$ cd ~/.wine/dosdevices
$ ls -l[/B]
total 0
lrwxrwxrwx 1 dave dave 14 2008-04-15 23:57 a: -> /media/floppy0
lrwxrwxrwx 1 dave dave 10 2008-04-15 23:42 c: -> ../drive_c
lrwxrwxrwx 1 dave dave 13 2008-04-19 15:41 d: -> /media/cdrom0
lrwxrwxrwx 1 dave dave 10 2008-04-15 23:57 h: -> /home/dave

Find the drive letter linking to the DVD drive file system, which will be linked to /media/cdrom0 ... in the example above it's d: ... and create a second soft link from **d::** to /dev/scd0 and verify it, as follows:
[B]
$ ln -s /dev/scd0 d::
$ ls -l[/B]
total 0
lrwxrwxrwx 1 dave dave 14 2008-04-15 23:57 a: -> /media/floppy0
lrwxrwxrwx 1 dave dave 10 2008-04-15 23:42 c: -> ../drive_c
lrwxrwxrwx 1 dave dave 13 2008-04-19 15:41 d: -> /media/cdrom0
lrwxrwxrwx 1 dave dave  9 2008-04-19 15:41 d:: -> /dev/scd0
lrwxrwxrwx 1 dave dave 10 2008-04-15 23:57 h: -> /home/dave

3. The mrbass.org instructions for creating Gnome menu entries to run the tools use an out-of-date directory path ... instead, I used the following:
[B]
$ sudo gedit /usr/share/applications/dvdshrink.desktop
[/B]
[Desktop Entry]
Name=DVD Shrink (Step 2)
Exec=wine .wine/drive_c/Program\ Files/DVD\ Shrink/DVD\ Shrink\ 3.2.exe
Icon=gnome-dev-dvd.png
Type=Application
Categories=Application;AudioVideo
[B]
$ sudo gedit /usr/share/applications/dvddecrypter.desktop
[/B]
[Desktop Entry]
Name=DVD Decrypter (Step 1)
Exec=wine .wine/drive_c/Program\ Files/DVD\ Decrypter/DVDDecrypter.exe
Icon=gnome-dev-cdrom.png
Type=Application
Categories=Application;AudioVideo 


**Two-Step Ripping Process**

The generally recommended process for people using these tools on Windows is a two step one:

1. Use DVD Decrypter to rip the disk and remove the CSS encryption, writing it to an (unencrypted) ISO image or to a DVD-like file system. 

2. Use DVD Shrink to resize it to fit on a 4.7GB single layer disc.

This is because on Windows, DVD Decrypter is much faster at reading CSS-encrypted disks. I also use the above to step method, and indeed, found it to be necessary, as DVD Shrink seems unable to read encrypted disks under Wine. I prefer to rip to a file system, but that is probably my own prejudice since I used to master DVD iso images this way in the old days. 

As per mrbass.org, I recommend turning off the automatic burning feature in DVD Shrink, and instead burning the resulting ISO images with the regular Linux burning software (Nautilus) by right clicking on the .iso files.

---

### Post by SlappyPappy on 2008-04-23
Hey buddy, thanks for posting your info. I'm trying your suggestions right now. I tried getting K3b to rip but the thing is a hunk o'junk.

I've got decrypter going right now and I'll be trying DVDShrink in a bit. 

So far, so good!  :)

---

