---
title: "HOWTO Use Ubuntu As A Mac OS X Time Capsule"
date: 2013-01-16
forum: Networking &amp; Wireless
---

### Post by N00b-un-2 on 2013-01-16
Preface:

In past versions of Mac OS X, the built in backup tool, [Time Machine]("http://en.wikipedia.org/wiki/Time_Machine_(Mac_OS)") was a lot less picky about where you back up your files to.  You could even back up to a Samba file share if you enabled the "unsupported volumes" hack.

```
 defaults write com.apple.systempreferences TMShowUnsupportedNetworkVolumes 1

```

But that ended with Snow Leopard.  Starting with the release of OSX 10.7 Lion, Apple started cinching down on where you could back up your system to, ostensibly for security reasons.  Now, with Mac OS X 10.8 "Mountain Lion", it's gotten to the point where essentially the only places you can back up your system using Time Machine are either on another Mac OS X File Server or on an Apple Time Capsule.  My assumption is that their intent is merely to bolster their hardware sales.

I don't know too many people who stay exclusively within the "walled garden" for all their computing needs.  Certainly people with a lot more money to burn than me.  But for a much more economical approach than shelling out around $300 for an over-glorified USB drive, you could just follow this guide to set up your Ubuntu file server to look and behave exactly like Time Machine would expect a real Time Capsule or Mac to.

**Step 1: Install Netatalk**

installing Netatalk, the open source Apple Filing Protocol (AFP) implementation is easy!  The packages are already in the repos, which makes me wonder why it's not enabled by default.

Install the following packages:

```
sudo apt-get install netatalk libc6-dev avahi-daemon libnss-mdns
```

**Step 2: Configure  /etc/nsswitch.conf**

Once those packages are installed, there are actually 4 configuration files that need to be edited in order for the Macs on your network to access your AFP shares properly.

```
sudo nano /etc/nsswitch.conf
```
locate the line that reads

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

and add *'mdns'* to it so it now reads

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 mdns
```

press ctrl+o to save and ctrl+x to exit.

**Step 3: /etc/avahi/services/afpd.service**

```
sudo nano /etc/avahi/services/afpd.service
```

paste the following code

```

<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
    <name replace-wildcards="yes">%h</name>
    <service>
        <type>_afpovertcp._tcp</type>
        <port>548</port>
    </service>
    <service>
        <type>_device-info._tcp</type>
        <port>0</port>
        <txt-record>model=TimeCapsule</txt-record>
    </service>
</service-group>

```

NOTE:  Just for fun you can change the string "<txt-record>model=TimeCapsule</txt-record>" to the following devices to change how they appear in Finder on OSX:

[LIST]
[*]MacBook
[*]Laptop
[*]MacBook4,1,Black 
[*]MacBookPro 
[*]MacBookAir
[*]MacPro
[*]iMac
[*]Macmini
[*]AppleTV
[*]iPhone
[*]iPodTouch
[*]iPad
[*]Xserve
[*]RackMac
[*]TimeCapsule
[*]PowerBook
[*]PowerMac
[*]AppleTV1
[*]AppleTV2
[*]AirPort
[/LIST]
Type them exactly as I have typed them.  They are case sensitive.  If you type the model name in wrong, your AFP share will show up as a Cinema Display in Finder.  There are actually dozens more.  Too many to list actually, but if you're interested you can find the name strings in /System/Library/CoreServices/CoreTypes.bundle/Contents/Info.plist

**Step 4: /etc/netatalk/AppleVolumes.default**

This is where you actually declare your shared file.

```
sudo nano /etc/netatalk/AppleVolumes.default
```

scroll down to the bottom and find the section that reads
```

# The line below sets some DEFAULT, starting with Netatalk 2.1.
:DEFAULT: options:upriv,usedots

# By default all users have access to their home directories.
~/                      "Home Directory"

# End of File

```

change the path "~/" (which points to /home/username) to the directory you want to share.  For me I created a separate partition mounted at /TimeCapsule.

IMPORTANT!!! You would be able to access the share from a Mac, but if you plan to use this share for Time Machine backup, you need to add *'tm'* to options:upriv,usedots
like this:

```

# The line below sets some DEFAULT, starting with Netatalk 2.1.
:DEFAULT: cnidscheme:dbd options:upriv,usedots,tm

# By default all users have access to their home directories.
/TimeCapsule                       "Time Capsule"

# End of File

```

press ctrl+o to save and ctrl+x to exit.

**Step 5: /etc/default/netatalk**

this is the last file that you need to edit.  Edit with

```
sudo nano /etc/default/netatalk
```


find the section that looks like this

```

#### Set which legacy daemons to run.
#### If you need AppleTalk, run atalkd.
#### papd, timelord and a2boot are dependent upon atalkd.
ATALKD_RUN=no
PAPD_RUN=no
TIMELORD_RUN=no
A2BOOT_RUN=no

```

and edit it so it looks like this:
```

#### Set which legacy daemons to run.
#### If you need AppleTalk, run atalkd.
#### papd, timelord and a2boot are dependent upon atalkd.
ATALKD_RUN=no
PAPD_RUN=no
CNID_METAD_RUN=yes
AFPD_RUN=yes
TIMELORD_RUN=no
A2BOOT_RUN=no

```

That is all.  Now you can enjoy making incremental backups with Time Machine without the hassle of manually mounting disks.  I actually did this on my Windows 8 HTPC/Mediaserver using a very stripped down headless Debian virtualbox installation that runs at boot as a background service and uses only 64MB of RAM and paravirtualized bridged ethernet.

[[IMG]http://img846.imageshack.us/img846/1334/screenshot20130116at925.png[/IMG]](http://imageshack.us/photo/my-images/846/screenshot20130116at925.png/)


Screenshot of my Mac backing up to the Debian virtual machine on my Windows 8 box.

---

### Post by N00b-un-2 on 2013-01-17
Just in case anyone is interested, here is the complete list of icons and how to make your Ubuntu AFP shares take on that image.  On OSX 10.7 and 10.8, there are only 8 monochromatic icons used (Laptop, Macmini, MacPro, iTouch, iPhone, iPad, iMac and Time Capsule) but if you use a hack like "Side Effects" on Lion or Mountain Lion, or if you are still on Snow Leopard  or before, any of these icons will work for you.  It's probably safe to assume that on Tiger or Leopard which are already past EOL there probably isn't support for a lot of the newer icons.

[[IMG]http://img850.imageshack.us/img850/5656/screenshot20130117at124.png[/IMG]](http://imageshack.us/photo/my-images/850/screenshot20130117at124.png/)

Apple Cinema Display = Any invalid or blank string

Airport Express = AirPort4 AirPort4,102 AirPort4,107

Airport Extreme = AirPort Airpor5 AirPort5,104 AirPort5,105 AirPort5,108 AirPort5,114 AirPort5,117

AppleTV = AppleTV AppleTV1,1

eMac = PowerMac4,4 PowerMac6,4

iBook G4 = PowerBook6,3 PowerBook6,5 PowerBook6,7

Aluminum 20" iMac = iMac7,1 iMac8,1

Aluminum 24" iMac = iMac9,1

"Flower Pot" G4 iMac 15" = PowerMac4,2

"Flower Pot" G4 iMac 17" = PowerMac4,5 PowerMac6,1

"Flower Pot" G4 iMac 20" = PowerMac6,3

Unibody G5 iMac 17" = PowerMac8,1 PowerMac8,2

Unibody G5 iMac 17" w/ iSight = PowerMac12,1

iMac 24" = iMac4,1 iMac4,2

Unibody iMac 21" = iMac11,2 iMac12,1

Unibody iMac 27" = iMac10,1 iMac11,1 iMac11,3 iMac12,2

iPad = iPad iPad1,1

iPhone = M68AP iPhone1,1

iPhone3G = N82AP iPhone1,2

iPhone4 = N90AP iPhone iPhone3,1

iPodTouch = N45AP iPod1,1

iPod Touch 2 = N72AP iPod2,1

iPod Touch 4 = N81AP iPod4,1

Black MacBook = MacBook1,1,Black MacBook2,1,Black MacBook3,1,Black MacBook4,1,Black

White Unibody MacBook = MacBook6,1 MacBook7,1

Aluminum Unibody MacBook = MacBook5,1

White MacBook = MacBook1,1 Macbook2,1 MacBook3,1 MacBook4,1 MacBook5,2 MacBook1,1,White MacBook2,1,White MacBook3,1,White MacBook4,1,White

MacBook Air = MacBookAir1,1 MacBookAir2,1

MacBook Air Unibody 11" = MacBookAir3,1 MacBookAir4,1 MacBookAir5,1

MacBook Air Unibody 13" = MacBookAir3,2 MacBookAir4,2 MacBookAir5,2

MacBook Pro 13" = MacBookPro5,5 MacBookPro7,1 MacBookPro8,1 MacBookPro9,1

Retina MacBook Pro 15" = MacBookPro

Unibody MacBook Pro 15" = MacBookPro5,1 MacBookPro5,3 MacBookPro5,4 MacBookPro6,2 MacBookPro8,2 MacBookPro9,2

Unibody Macbook Pro 17"  = MacBookPro5,2 MacBookPro6,1 MacBookPro8,3

Silver MacBook Pro = Laptop

Mac Mini w/o Disk Drive = Macmini Macmini5,1 Macmini5,2 Macmini5,3

Mac Mini w/ Disk Drive = Macmini4,1

Old Mac Mini = PowerMac10,1 PowerMac10,2

MacPro = MacPro MacPro1,1 MacPro2,1 MacPro3,1 MacPro4,1 MacPro5,1

PowerBook G4 12" = PowerBook6,1 PowerBook6,2 PowerBook6,4 PowerBook6,8

PowerBook G4 15" = PowerBook5,2 PowerBook5,4 PowerBook5,6 PowerBook5,8

PowerBook G4 17" = PowerBook5,1 PowerBook5,3 PowerBook5,5 PowerBook5,7 PowerBook5,9

Titanium PowerBook = PowerBook3,2 PowerBook3,3 PowerBook3,4 PowerBook3,5

Graphite G4 PowerMac = PowerMac

Quicksilver G4 PowerMac = PowerMac3,5

Time Capsule = AirPort6 AirPort6,106 TimeCapsule TimeCapsule6 TimeCapsule6,106 TimeCapsule6,109 TimeCapsule6,113 TimeCapsule6,116

XServe = RackMac RackMac1,1 RackMac1,2 RackMac3,1 Xserve Xserve1,1 Xserve2,1 Xserve3,1

---

### Post by PartisanEntity on 2014-11-18
For anyone interested in this How To, I can confirm that it is working on Ubuntu Server 14.04 LTS.

---

### Post by peartaa on 2014-11-22
I've used this how-to before on a different machine and it worked fine,  but I'm now doing it on a new machine, but with the same disk that  contained the backup file from the old machine.

after following  the instructions, I tried to reboot my computer and it hung on the  xubuntu splash screen indefinitely - would not boot

I booted into a live cd and (on a hunch) tried renaming the file 
/etc/avahi/services/afpd.service

to afpd.service.old.

I was then able to boot, and saw "Time Capsule" from my mac, but when I tried connecting, I got this error "Unable to connect" (link to screenshot): [https://www.dropbox.com/s/9yjpsniuhpy7rwc/Screenshot%202014-11-22%2020.46.04.png?dl=0](https://www.dropbox.com/s/9yjpsniuhpy7rwc/Screenshot%202014-11-22%2020.46.04.png?dl=0)

and an error showed up on my Xubuntu box as well, "System program problem detected" and it wanted to submit a bug report.

I'll continue working on it and post updates.  Of course, I'll welcome any insight or help of any kind :)

---

### Post by melat0nin on 2014-12-15
Thanks for the guide!

I followed the steps exactly but although I can see the server in Finder I can't see it as a disk option in Time Machine (Yosemite, and Ubuntu Server 14.04). Any thoughts why this is? I also have Samba set up through Webmin, if that makes any difference.

---

### Post by melat0nin on 2014-12-16
> **melat0nin said:**
> Thanks for the guide!

I followed the steps exactly but although I can see the server in Finder I can't see it as a disk option in Time Machine (Yosemite, and Ubuntu Server 14.04). Any thoughts why this is? I also have Samba set up through Webmin, if that makes any difference.

I managed to get it working using the guide here: [http://d43.me/blog/1660/concisest-guide-to-setting-up-time-machine-server-on-ubuntu-server-12-04/](http://d43.me/blog/1660/concisest-guide-to-setting-up-time-machine-server-on-ubuntu-server-12-04/)

The main difference is the share definition in /etc/netatalk/AppleVolumes.default, and using a separate user account with its own home folder to contain the Time Capsule files.

---

### Post by ThomasNovin on 2015-03-31
> **melat0nin said:**
> I managed to get it working using the guide here: [http://d43.me/blog/1660/concisest-guide-to-setting-up-time-machine-server-on-ubuntu-server-12-04/](http://d43.me/blog/1660/concisest-guide-to-setting-up-time-machine-server-on-ubuntu-server-12-04/)

The main difference is the share definition in /etc/netatalk/AppleVolumes.default, and using a separate user account with its own home folder to contain the Time Capsule files.

Thanks for that, great post. Worked fine for me.

---

### Post by Abadie_Pierre on 2015-06-04
Hello Everybody,
First, sorry for my english, i come frome France (Marseille).....
I'm a beginner in ubuntu. I think is awesome! I've got a question:
I have a fresh install of ubuntu 14.10. I installed netatalk and avahi packages for afp sharing. The home directory is shared. It working great.But:
I would to share a folder who are on another disk, identified by /dev/sdb1/film
So, what is the command line in the /etc/netatalk/AppleVolumes.default
You said:

# The line below sets some DEFAULT, starting with Netatalk 2.1.
:DEFAULT: options:upriv,usedots
# By default all users have access to their home directories.
~/                      "Home Directory"
# End of File

That working great but i would like to replace  "Home Directory" by /dev/sdb1/film. ( I tryed but not worked).

Thanks a lot and I send at every body heat of southern France
:cool:

---

### Post by N00b-un-2 on 2015-06-05
the solution is simple.  /dev/sdb1 needs to be mounted at boot.  You can add a permanent mount point by creating a folder somewhere (/mnt/ or /media/ are good choices, ex; /mnt/data) and then add /dev/sdb1 to /etc/fstab.  eg 


/dev/sdb1 /mnt/data   ext4  0 0

reboot your computer and your should now see the contents of /dev/sdb1 mounted to /mnt/data

Then edit AppleVolumes.default to share /mnt/data/film

---

### Post by Abadie_Pierre on 2015-06-08
Thank you N00b-un-2!

You give a good idea.

This Is what i whrote in etc/netatalk/ApplesVolumes.default

/media/pierre/dd2/film             "film"

IT WORK!

Thx

---

### Post by izurdo on 2015-06-21
Hi all,

I did install successfully netatalk etc, and I could connect to the server home users directories from our Macs. The issue is that I tried to add another share (/Volumenes/tera "tera") as per below:

[COLOR=#4329D4][FONT=Courier] The line below sets some DEFAULT, starting with Netatalk 2.1.[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]:DEFAULT: options:upriv,usedots[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#4329D4][FONT=Courier]# By default all users have access to their home directories.[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]~/                      [COLOR=#b12512]"Home Directory"[/COLOR][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]/Volumenes/tera         [COLOR=#b12512]"tera"[/COLOR][/FONT][/COLOR]
[COLOR=#4329D4][FONT=Courier]# End of File[/FONT][/COLOR]



It did not work, but also even after removing the new line I entered, Netatalk is not working properly. When I try to connect the server again it says that it is an old non compatible version. I don't get it as it was working before and I left the file as it was when it was working.
Obviously I restarted netatalk after every change but did not work, even restarting the whole server did not help at all.

The server is Ubuntu Server 14.04 and the Mac clients are Yosemite.

Any idea?

Many thanks in advance.

---

### Post by Dan_Streeter on 2015-07-15
Hi All,

I've got this working on my Ubuntu 12.04 Xen Guest and it was working great for ages, I haven't done anything to the guest that I am aware of, and then all of a sudden - it starts showing me this screen every time I join my network:
([I followed this guide, which from a quick scan over is the same as the on here]("http://www.danstreeter.co.uk/hosted-globals/ubuntuforums.org-showthread-php-t=2105755-Guide.pdf"))

[IMG]http://danstreeter.co.uk/hosted-globals/ubuntuforums.org-showthread-php-t=2105755-TimeMachineFail.png[/IMG]
Pressing 'Start New Backup' causes - as you'd expect an entire new backup of my entire computer and looses the old one.
Then I go to work, come home, plug in and it pops up again.

I'm not sure where to start looking to debug this =(

Drive is not full:
```
/dev/xvda2      931G  271G  614G  31% /timemachine
```

This is the entire of my syslog:
```
Jul 15 07:35:04 timemachine anacron[2136]: Job `cron.daily' terminated (mailing output)Jul 15 07:35:04 timemachine anacron[2136]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Jul 15 07:35:04 timemachine anacron[2136]: Normal exit (1 job run)
Jul 15 08:17:01 timemachine CRON[2840]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 09:17:01 timemachine CRON[3564]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 10:17:01 timemachine CRON[4261]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 11:17:01 timemachine CRON[4985]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 12:17:01 timemachine CRON[5709]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 13:17:01 timemachine CRON[6475]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 14:17:01 timemachine CRON[7172]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 15:17:01 timemachine CRON[7896]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 16:17:01 timemachine CRON[8620]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 17:17:01 timemachine CRON[9344]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 18:17:01 timemachine CRON[10041]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 19:17:02 timemachine CRON[10807]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 19:39:16 timemachine afpd[11078]: AFP3.3 Login by timemachine
Jul 15 19:40:20 timemachine afpd[11078]: AFP logout by timemachine
Jul 15 19:40:20 timemachine afpd[11078]: AFP statistics: 5.82 KB read, 5.83 KB written
Jul 15 19:40:20 timemachine afpd[11078]: done
Jul 15 19:41:36 timemachine crontab[11254]: (root) BEGIN EDIT (root)
Jul 15 19:41:42 timemachine crontab[11254]: (root) END EDIT (root)
Jul 15 19:52:28 timemachine afpd[11407]: AFP statistics: 0.52 KB read, 0.38 KB written
Jul 15 19:52:30 timemachine afpd[11408]: AFP3.3 Login by timemachine
Jul 15 19:52:31 timemachine afpd[11408]: AFP logout by timemachine
Jul 15 19:52:31 timemachine afpd[11408]: AFP statistics: 2.11 KB read, 3.50 KB written
Jul 15 19:52:31 timemachine afpd[11408]: done
Jul 15 19:56:46 timemachine afpd[11511]: AFP3.3 Login by timemachine
Jul 15 19:57:38 timemachine afpd[11511]: AFP logout by timemachine
Jul 15 19:57:38 timemachine afpd[11511]: AFP statistics: 5.84 KB read, 5.69 KB written
Jul 15 19:57:38 timemachine afpd[11511]: done
Jul 15 20:05:51 timemachine crontab[11656]: (timemachine) BEGIN EDIT (timemachine)
Jul 15 20:05:58 timemachine crontab[11656]: (timemachine) END EDIT (timemachine)
```

There is nothing of note in dmesg, the last entry was at 148 seconds and the system has been 'up' for 57 days so far (scheduled reboot 57 days ago, problem was present before then)

The system is a dedicated 'timemachine' guest node - and has NOTHING but the vanilla Ubunu 12.04 Server install, and the guide as per the link at the top (which is taken from here anyway).

Any help would be greatly appreciated.

Thanks

---

### Post by susi-loma on 2015-10-05
@[**[COLOR=#000000]Dan_Streeter[/COLOR]**]("http://ubuntuforums.org/member.php?u=1991379"):
Sorry but i am not able help you. I have this message only one time in the past, and aftet creating a new Backup there was no problem until now.

Now i updated to 10.11 and i am not able to mount a volume with afp. With samba i am able to mount, but TimeMachine does not work. Maybe apple change something about it, but not sure.

Does someone also have the problem with osx 10.11 and avahi/netatalk? And is there a solution?

Cheers

---

### Post by bild85 on 2015-10-08
> **Dan_Streeter said:**
> Hi All,

all of a sudden - it starts showing me this screen every time I join my network:
[snip]
Wish I had the answer Dan. I also get this once in a while (maybe every six months?) but haven't looked into it.
But I will say that I don't take my laptop different places. You don't have TimeMachine set up at the other network you use also, right? I know you can't have two TimeMachine backups.

---

### Post by johannes12 on 2015-12-09
It worked for me after I appended* options:tm *to the Line with my filesystem in /etc/netatalk/AppleVolumes.default :

[FONT=courier new]/data/backup/apple    "MyTimeCapsule"    options:tm[/FONT]

Regards,
Johannes

---

### Post by nevertellanyone on 2016-03-02
Hi, I did this, and it is working. The only problem is the mac keeps asking for the Ubuntu (Time Machine) login and password? If I put in the Ubuntu computer's main login and pw, the Mac will do the Time Machine backup.
How do I get it to just do the backup without asking for the login and password for the Ubuntu computer?
Thanks!
P.S. Mac is Mt. Lion 10.8.5 and Ubuntu is 14.04 LTS

---

