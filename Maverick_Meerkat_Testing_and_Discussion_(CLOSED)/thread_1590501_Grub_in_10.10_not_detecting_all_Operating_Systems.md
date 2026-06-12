---
title: "Grub in 10.10 not detecting all Operating Systems"
date: 2010-10-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by DeadlyWolf on 2010-10-07
On multi boot systems the grub in 10.10 does not detect all the installs, yet other installations of grub do. For example Mint 9 and Mint Debian the grub detects all the operating systems when grub is installed and updated. Anyone else noticed this ?.

---

### Post by ranch hand on 2010-10-07
So, you have run;
```

sudo update-grub

```
and;
```

sudo grub-mkconfig

```
while in 10.10 and it is not detecting the other OS' even then?

---

### Post by aisajib on 2010-10-07
Open up terminal and type the following.

> sudo update-grub

Hit enter and you will be prompted to enter password. Your grub should be updated and include all other OSes.

---

### Post by DeadlyWolf on 2010-10-08
I have replaced the grub 10.10 installed with grub2 from another distro, so I will reinstall grub from 10.10 later and get back to you. But when the updates install a fresh grub it should automatically detect all the installs and they should be showing at the next reboot. I have 1 windows install and 5 linux and it misses 1 of the linux installs , last time it was Mint Debian.

---

### Post by 23dornot23d on 2010-10-08
I have noticed the same thing too ..... why it misses mint out I do not know .....

I use Mint Grub 2   .... as it picks up nearly everything correctly - Mandriva is always picked up .... but it will never work straight off .... 

Ubuntu Grub 2 is a lot better than it was though ...... 

I also now have a separate drive with the old Grub on just to make sure I can run Mandriva 2010 now .

---

### Post by cariboo on 2010-10-08
I have a quintuple boot system,  Windows XP, Fedora 13, openSUSE 11.3 and Maverick are all detected properly and are even labeled properly, for some reason PCLOS is detected, but is only labeled as Linux.

Does anyone know where the label info comes from? I ran strings on initrd.img-2.6.35-22-generic and vmlinuz-2.6.35-22-generic , but could find any reference to the versions.

---

### Post by 23dornot23d on 2010-10-08
I have no idea ..... but this is what mine does pick up .... think this is a mint Grub 2
as it seems to pick up most of them ...... 
I used to have elive - kanotix and knoppix but they got upgraded at some point in time. 

root@keith-laptop:/home/keith# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
grep: /etc/linuxmint/info: No such file or directory
grep: /etc/linuxmint/info: No such file or directory
Found memtest86+ image: /boot/memtest86+.bin
Found Mandriva Linux 2010.0 (2010.0) on /dev/sda10
Found Ubuntu maverick (development branch) (10.10) on /dev/sda12
Found Ubuntu maverick (development branch) (10.10) on /dev/sda2
Found Ubuntu maverick (development branch) (10.10) on /dev/sda6
Found Ubuntu 9.10 (9.10) on /dev/sda7
Found Ubuntu 8.10 (8.10) on /dev/sda8
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda9
Found Linux Mint 9 Isadora (9) on /dev/sdb1
Found Ubuntu maverick (development branch) (10.10) on /dev/sdb10
Found Ubuntu maverick (development branch) (10.10) on /dev/sdb11
Found Gentoo Base System release 2.0.1 on /dev/sdb12
Found openSUSE 11.3 (i586) on /dev/sdb3
Found Linux Mint 9 Isadora (9) on /dev/sdb5
Found Linux Mint 9 Isadora (9) on /dev/sdb6
Found Linux Mint 9 Isadora (9) on /dev/sdb8
Found Fedora release 13 (Goddard) on /dev/sdb9
Found Ubuntu jaunty (development branch) (9.04) on /dev/sdc10
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sdc11
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sdc3
Found Ubuntu jaunty (development branch) (9.04) on /dev/sdc4
Found Mandriva Linux 2010.0 (2010.0) on /dev/sdc5
Found Ubuntu maverick (development branch) (10.10) on /dev/sdc7
Found Debian GNU/Linux (squeeze/sid) on /dev/sdc8
Found Ubuntu 9.04 (9.04) on /dev/sdd2
Found Ubuntu maverick (development branch) (10.10) on /dev/sdd4
Found Linux Mint 9 Isadora (9) on /dev/sdd5
Found Linux Mint 8 Helena - Main Edition (8) on /dev/sdd7
Found Linux Mint 9 Isadora (9) on /dev/sdd8
done
root@keith-laptop:/home/keith#

---

### Post by tokyobadger on 2010-10-08
grub2 doesn't pick up FreeBSD. grub-legacy was quite easy to use for *BSDs; I'm being lazy at the mo' and just hitting c at the grub prompt whenever I want to use FreeBSD, guess I'll fix it some time but would rather grub2 did...

---

### Post by drs305 on 2010-10-08
> **cariboo907 said:**
> 
Does anyone know where the label info comes from? I ran strings on initrd.img-2.6.35-22-generic and vmlinuz-2.6.35-22-generic , but could find any reference to the versions.

Caution to others (but not *cariboo907*: Geek Alert !

I haven't tracked it down fully, but at least some of the names are extracted by linux-boot-prober, which runs via 30_os-prober and provides input to the LINUXPROBED string. 

One thing it does is extract information from the 10_linux entries of other linux partitions. As a test, running Ubuntu on sda1, I changed the titles of the entries in my sda10 Ubuntu grub.cfg files. I even added a completely bogus entry into the 10_linux section.  After running sda1's update-grub, the newly revised sda10 entries, including the completely fictional one, were included in the sda1 30_os-prober section of grub.cfg.

So now if inclined the question redirects focus on what generates the 10_linux entries, but I've had enough for one day.  ;-)

---

### Post by VMC on 2010-10-08
Look at "/etc/grub.d/30_os-prober" Line #137 = LABEL
It picks the label up from the output of os-prober.

The for loop starting on line#134 is where LABEL gets created:
```
for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"
...

```
If you go up to Line#76 you see where OSPROBED is created from the command os-prober.

You can run those commands by hand. My os-prober for example is:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda6:Ubuntu 10.10 (10.10):Ubuntu:linux
/dev/sda7:Ubuntu 10.04.1 LTS (10.04):Ubuntu1:linux
/dev/sda9:Ubuntu 10.10 (10.10):Ubuntu2:linux

Using the 'tr' and 'paste' it becomes"

/dev/sda1:Windows^7^(loader):Windows:chain /dev/sda6:Ubuntu^10.10^(10.10):Ubuntu:linux /dev/sda7:Ubuntu^10.04.1^LTS^(10.04):Ubuntu1:linux /dev/sda9:Ubuntu^10.10^(10.10):Ubuntu2:linux

Therefor the whitespace " " is used inside the for loop and cut out when LABEL comes along:

So my first one is "Windows" as:
sudo os-prober | tr ' ' '^' | paste -s -d ' '| cut -d ':' -f 3 
Windows

Then the for loop goes back picking up the next iteration picking up the rest until completion

---

### Post by cariboo on 2010-10-08
I got that from looking at 30_os_prober, I'm just curious were it gets the distro name and version from, because I can't see anywhere in the scripts where it gets it from.

---

### Post by 23dornot23d on 2010-10-08
Its interesting - as the versions that I run include 

Zorin 
PinguyOS 
Ultimate-Edition

But none are identified by those names ..... they are all identified by the kernel .....
is it looking at the kernel files to work out what name to use .......

As that is what the first few entries in the menu seem to show .......

---

### Post by drs305 on 2010-10-08
> **23dornot23d said:**
> Its interesting - as the versions that I run include 

Zorin 
PinguyOS 
Ultimate-Edition

But none are identified by those names ..... they are all identified by the kernel .....
is it looking at the kernel files to work out what name to use .......

As that is what the first few entries in the menu seem to show .......

The way G2 finds things is truly a mystery to me. You mention the first few entries, but they may be located by an entirely different process (in the 10_linux section) than the 30_os-prober section (or they may not). 

os-prober calls a script called common.sh, etc; there is a linux-boot-prober, and more. And as I discovered, it appears to also lift text directly from other grub.cfg files on the computer.

I've decided it's beyond my comprehension, so I've resigned myself just to understand what the full strings in the /etc/grub.d files are before they are truncated. That's all I've needed to alter titles, limit which partitions display in grub.cfg, etc.

Where's *ranch hand* to jump in and proclaim the superiority of custom menus when you need him?

---

### Post by 23dornot23d on 2010-10-08
I must admit .... 

I created a custom menu once after ranch hand and yourself had shown me how to do this - but the odd line from that ( that I had entered manually ) got pulled into some other Grub 2 menus that I had running at the time ( after grub-updates ) the grub 2 menus were on different drives as far as I remember ......

At the time I thought it was strange ... and just put it down to being a glitch ....

It would be nice if it could identify them ..... maybe if we had one file in each boot folder
just with the identification string in it ..... the system could then easily go get them ....

OSNAME.txt .......... and in it .........  ZORIN 3 ( or whatever the OS happens to be )

Then it would just be a case of ..... if that file exists ...... use its contents as a Menu Option ....

Which directory is this in ? common.sh (got it)

[IMG]http://img163.imageshack.us/img163/2739/1screenshot1.jpg[/IMG]

---

### Post by DeadlyWolf on 2010-10-08
Okay, in 10.10

```
sudo grub-install /dev/sda
``````
sudo update-grub
```and this time it worked.

:confused:

---

### Post by 23dornot23d on 2010-10-08
Good to know you are sorted ..... its interesting now to know where the names are picked up from !!! :)

[IMG]http://img824.imageshack.us/img824/2008/screenshot2ym.jpg[/IMG]

---

### Post by drs305 on 2010-10-08
> **DeadlyWolf said:**
> Okay in 10.10

```
sudo grub-install /dev/sda
``````
sudo update-grub
```and this time it worked.

:confused:


Glad you have this fixed, and my sincerest apologies for us hijacking your thread. We will take it elsewhere if we want to continue geek-speak.

---

### Post by 23dornot23d on 2010-10-08
Same here sorry about hijacking this thread too ..... will start another on where the Grub 2 naming comes from !!!

---

