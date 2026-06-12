---
title: "Wireless card problem..... pls help"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by gtkourounis on 2006-02-28
I just bought a Acer Aspire 5002WLMi, and i installed ubuntu in it. Everything runs smoothly except for one thing. I cant get ubuntu to find my wireless card (integrated) and i therefore i cant communicate with my internet without an E-net wire. I read something about ndiswrapper or something similar but i didnt really undertand what to do. I searched for which wireless card i have and i think i have a Acer InviLink 802.11b/g wireless LAN. If you could help me out pls do. and by the way ubuntu rox. 10000 better then windows or mac.

thanx in advance.


EDIT - the name of the card is..... Broadcom Corporation BCM4318 802.11 b/g and i got the .inf files for the driver from the acer cd that came with the laptop. 

I am also a total noob in these things so the more simple the instructions the better for me. Thank you.

---

### Post by ltmon on 2006-02-28
Firstly, the next version of Ubuntu (Dapper) should contain native support for Broadcom cards... so no need to use ndiswrapper.  I know this doesn't solve yuor current problem, but at least it's something to look forward to ;)

For the moment I believe you _will_ have to use ndiswrapper.  It is simply a wrapper around your windows drivers that will allow Linux to use them.  A good starting point is: [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

Have a go at following those instructions, and post back if/when you get stuck.

L.

---

### Post by gtkourounis on 2006-02-28
what does make a deb mean? pls check the 5th step (in the very beginning)and if you could pls explain i would be more then thankfull.

here is the link

[https://wiki.ubuntu.com/HowtoUseNdiswrapperOnAmd64Ubuntu?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowtoUseNdiswrapperOnAmd64Ubuntu?highlight=%28ndiswrapper%29)

---

### Post by ltmon on 2006-03-01
Ok, you're unlucky to be on AMD64 because it requires a whole lot of extra steps it seems.  Make sure you are on an AMD64 platform and have installed the 64 bit version of Ubuntu before following the steps in the link you sent me.

"make deb" means the command to make a binary package (a ".deb" file on ubuntu) that can be installed using normal tools.  It's badly explained (glossed over) in the wiki page.

Basically (in this case) to make the package you need to open a terminal, go into the directory:
```
cd ndiswrapper-version
```
Then type the command:
```
make deb
```
This will cause a file called 'ndiswrapper-version-amd64.deb' (or something similar) to be created.  It will take a few minutes.
Then type:
```
sudo dpkg -i ndiswrapper-version-amd64.deb
```
Which will cause the package to be installed.

That's the end of step 5.

L.

---

### Post by gtkourounis on 2006-03-01
i have a problem on the first step this is the code

> gtkourounis@gtkourounis:~$ cd ndiswrapper-1.10
bash: cd: ndiswrapper-1.10: No such file or directory

---

### Post by ltmon on 2006-03-01
Where did you extract the ndiswrapper source code to?  This is where you need to 'cd' to.

In bash (the command prompt) you can use 'ls' to list all files and directories in the current directory to look for it.  Or open the normal graphical file browser and see if you can find it using that.

L.

---

### Post by gtkourounis on 2006-03-01
ok so if mine is in Home ----> WiFi ---> ndiswrapper-1.10 then what code should i instert?

home/WiFi/ndiswrapper-1.10 

?????

---

### Post by ltmon on 2006-03-01
```

cd /home/WiFi/ndiswrapper-1.10
make deb
sudo dpkg -i ndiswrapper-1.10-amd64.deb

```

This should do it.  A couple of notes: 
- make sure you've also followed steps 1-4 in the original link you gave me (i.e. edit the files).
- The name of the actual package could be slightly different, I'm not sure.  You should be able to see and recognize it though.

L.

---

### Post by gtkourounis on 2006-03-01
why do i need the cd in front of the first code if i dont have the files in a cd and in my HDD? i still dont get it i am sorry for this. and when i run the ls commans i get this code:

> gtkourounis@gtkourounis:~$ sudo ls
Azureus_2.4.0.0_linux.tar.bz2           My Pix
Desktop                                ndiswrapper-1.10.tar.gz
Firefox_wallpaper.png                        Shared
Incomplete                                   Tango-Icon_Unofficial-0.7.0.tar.bz2
LimeWireOther.zip                         **WiFi**
My Music                                         xmms-wma_1.0.4-2_i386.deb

and then i have all my files and drivers for the wireless internet in the folder WiFi so then i instert this code and this is what comes up:

> gtkourounis@gtkourounis:~$ sudo ls WiFi
BCMLogo.gif               bcmwl5.inf               **ndiswrapper-1.10**
bcmwl5a.inf                bcmwl5.sys              ndiswrapper-1.10.tar.gz
gtkourounis@gtkourounis:~$

and then when i try to modify the code that you gave me (which is probably modified incorrectly) and this is what comes up:

> gtkourounis@gtkourounis:~$ /home/WiFi/ndiswrapper-1.10
bash: /home/WiFi/ndiswrapper-1.10: No such file or directory
gtkourounis@gtkourounis:~$

i am sorry for being such a pain in the *** :( but i really want to get this to work and get to know ubuntu without being hooked to my router. (if not i guess i will have to wait until the Dapper Drake comes out, \\:D/ ).


EDIT: i bolded the names of WiFi and ndiswrapper they dont appear like that on the terminal.


and also thanx for the help and patience.

---

### Post by ltmon on 2006-03-03
No problem .... everyone has to learn :).  And sorry I didn't answer sooner, I was offline for all of yesterday.

This is a bit of a hard thing to do, by the way.  You are in the deep end very early.

Ok...

1. You don't have to "sudo" everything.  Only things that need administrator access.  The only thing you need to do with "sudo" for this install is the final "dpkg -i" command.

2. The directory you want to go to with "cd" ("cd" stands for "change directory") is "/home/gtkourounis/WiFi/ndiswrapper-1.10".  We had that wrong last time ::-#. 

Just an aside about home directories, the ~ (tilde) is shortcut for "/home/<youruser>".  So the prompt "gtkourounis@gtkourounis:~" means you are user "gtkourounis" on computer "gtkourounis" and inside your own home directory "~".

3. Based on the new information I got you need to do the following:

```

cd ~/WiFi/ndiswrapper-1.10

```

This will change you to be inside the directory containing the ndiswrapper source code.

```

make deb

```

This will compile the source code into a binary driver, and then package the driver into a ".deb" file, ready for installing.

```

sudo dpkg -i ndiswrapper-1.10-amd64.deb

```

This will put you into administrator mode ("sudo") and then install the driver.

Unfortunately it doesn't finish here.  You still have to load the driver, set it up to load on boot, and install the windows drivers (remembering that ndiswrapper simply wraps Windows drivers).  I won't tell you how to do those steps now, but post back if you get past the installation step.

Cheers,

L.

---

### Post by gtkourounis on 2006-03-03
still having some troubles. lol this is endless. anyways here they are:

even though i follow the steps at the beginning of the other site (1 to 4) when i insert make deb some problem with the amd86 occurs. here is the code, maybe you will be able to read it.

> gtkourounis@gtkourounis:~$ cd ~/WiFi/ndiswrapper-1.10
gtkourounis@gtkourounis:~/WiFi/ndiswrapper-1.10$ make deb
make[1]: Entering directory `/home/gtkourounis/WiFi/ndiswrapper-1.10'
make -f debian/rules binary-utils
make[2]: Entering directory `/home/gtkourounis/WiFi/ndiswrapper-1.10'
sed -e 's/-#KVERS#//g' \
-e 's/#DRIVER_VERSION#/1.10/g' \
-e 's/#UTILS_VERSION#/1.7/g' \
-e 's/#DATE#/'"`date --rfc-822`"'/g' \
        -e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
        debian/changelog.utils > debian/changelog
sed -e 's/#DRIVER_VERSION#/1.10/' \
-e 's/#UTILS_VERSION#/1.7/' \
-e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
debian/control.utils > debian/control
echo "utils/loadndisdriver /sbin" > debian/ndiswrapper-utils.install
echo "utils/ndiswrapper /usr/sbin" >> debian/ndiswrapper-utils.install
echo "utils/ndiswrapper-buginfo /usr/sbin" >> \
        debian/ndiswrapper-utils.install
cp debian/dirs.utils debian/dirs
dh_testdir
dh_testroot
dh_installchangelogs ChangeLog
dh_installchangelogs: Compatibility levels before 3 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 3 are deprecated.
dh_installexamples
dh_installexamples: Compatibility levels before 3 are deprecated.
dh_installdebconf
dh_installdebconf: Compatibility levels before 3 are deprecated.
export DH_OPTIONS='-i'
dh_installman ndiswrapper.8
dh_installman: Compatibility levels before 3 are deprecated.
make -C utils
make[3]: Entering directory `/home/gtkourounis/WiFi/ndiswrapper-1.10/utils'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/gtkourounis/WiFi/ndiswrapper-1.10/utils'
dh_install
dh_install: Compatibility levels before 3 are deprecated.
dh_link
dh_link: Compatibility levels before 3 are deprecated.
dh_strip
dh_strip: Compatibility levels before 3 are deprecated.
dh_compress
dh_compress: Compatibility levels before 3 are deprecated.
dh_fixperms
dh_fixperms: Compatibility levels before 3 are deprecated.
dh_perl
dh_perl: Compatibility levels before 3 are deprecated.
dh_makeshlibs
dh_makeshlibs: Compatibility levels before 3 are deprecated.
dh_installdeb
dh_installdeb: Compatibility levels before 3 are deprecated.
dh_shlibdeps
dh_shlibdeps: Compatibility levels before 3 are deprecated.
dh_gencontrol
dh_gencontrol: Compatibility levels before 3 are deprecated.
dpkg-gencontrol: error: current build architecture i386 does not appear in package's list (amd64)
dh_gencontrol: command returned error code 65280
make[2]: *** [common-epilog] Error 1
make[2]: Leaving directory `/home/gtkourounis/WiFi/ndiswrapper-1.10'
make[1]: *** [binary] Error 2
make[1]: Leaving directory `/home/gtkourounis/WiFi/ndiswrapper-1.10'
make: *** [deb] Error 2
gtkourounis@gtkourounis:~/WiFi/ndiswrapper-1.10$ sudo dpkg -i ndiswrapper-1.10-amd64.deb
Password:
dpkg: error processing ndiswrapper-1.10-amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndiswrapper-1.10-amd64.deb
gtkourounis@gtkourounis:~/WiFi/ndiswrapper-1.10$

i dont know is that normal? should i proceed with the next steps?

and again thanks for the help ltmon.

---

### Post by ltmon on 2006-03-03
Hi again,

The step "make deb" is what failed.  It seems to think that you are building of i386 architecture instead of AMD64 architecture.

Can you:

1. Make sure you have done step 4 on the page: [https://wiki.ubuntu.com/HowtoUseNdiswrapperOnAmd64Ubuntu](https://wiki.ubuntu.com/HowtoUseNdiswrapperOnAmd64Ubuntu)

2. If you have already done this, please post the output of this command:
```

uname -a

```

Cheers,

L.

---

### Post by gtkourounis on 2006-03-03
I have followed the other steps on that page for sure, i even went through them again right now. 

this is the code that comes from the comand that you gave me (i have the strange feeling that the i686 is no good news):

> gtkourounis@gtkourounis:~$ uname -a
Linux gtkourounis 2.6.12-10-386 #1 Mon Feb 13 12:13:15 UTC 2006 i686 GNU/Linux
gtkourounis@gtkourounis:~$

and just so that we dont get confused about the type of CPU that i have, i have a AMD Turion64 mobile technology (acer aspire 5002WLMi) and i installed the ubuntu cd that was mailed to me by ubuntu and on the back of the cd it says:

This PC Edition will run on Intel x86-based systems (including the Intel Pentium and AMD Athlon).

and just for the record i have actually installed ubuntu and i am not using the live cd from the two cds that were mailed to me.

---

### Post by ltmon on 2006-03-03
OK OK OK :)

You don't have the 64 bit version of Ubuntu installed!!  Basically what the CD meant was that the 386 version is compatable with the AMD64.... but it isn't actually 64 bit itself.  The AMD 64 is backwards compatable with 386 systems, which is why you could install this version without a problem.

In short this means 2 things:
1. You aren't getting quite as much performance out of your computer as you would if you were using the _real_ 64 bit version
2. Everything else just got a whole lot easier :)

I would suggest you just keep your current version.  It works, and unless you are an absolute performance measuring obsessive you probably won't notice the difference between the 386 and the 64 bit versions.

Now to get your wireless card installed:

1. Delete all the ndiswrapper stuff you already downloaded.  You could still use it, but there's no point unless you want to do things the hard way.

2. If you have a wired connection working in Ubuntu, open Synaptic and install the two packages: ndiswrapper-utils and ndisgtk.  Then skip to step 4.

3. If you don't have a wired connection, reboot to windows and visit the two addresses
```

http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils
http://packages.ubuntu.com/breezy/net/ndisgtk

```
and download the i386 versions of each package onto a CD/USB key/Other drive available to Ubuntu.

Then type from the location where you downloaded the packages (when booted into Ubuntu):
```

sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb
sudo dpkg -i ndisgtk_0.5-1ubuntu1_all.deb

```
which will install the downloded packages.

4. Now follow the instructions at: [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto) starting from set "2.2 Set up and install drivers"

This should get you most of the way there.

Cheers,

L.

---

### Post by gtkourounis on 2006-03-03
well i got my card recognised and it shows up when i insert wlan0 but it doesnt have any signals. the weird this is that it says signal strength 100% and status is idle. I go to its properties and i changed all its confugurations to the ones that my router has but still nothing seems to be responding. i am lost, lol. i dont know if you have any idea what might be the problem.

anyways worst case scenario isnt that bad. (being connected to the internet for 2 more months until daper drake comes out).

i have also tried the dhclient comand

---

### Post by ltmon on 2006-03-03
Hi,

Well we're getting somewhere in any case... can't give up now :)

Can you go to the "Networking" menu item under your Gnome system menu.

A screenshot of what mine looks like is attached, after I've clicked "properties" on ra0 (which is the same as your wlan0).  See if your's looks pretty much the same (with your SSID of course).

Make sure you aren't set up to use WPA encryption on your wireless access point for the moment, it just makes debugging harder.

Make sure you've clicked the "activate" button.

L.

---

### Post by gtkourounis on 2006-03-03
i am doing this imidiatly

for some reason its taking a little bit of time to load my network....



ya everything is looking good same as yours, let me host the image and i will show it to you.(screenshot)

[[IMG]http://img118.imageshack.us/img118/9563/wlan01sl.th.jpg[/IMG]](http://img118.imageshack.us/my.php?image=wlan01sl.jpg)

oops the one before was too big, this one does the work better...

---

### Post by ltmon on 2006-03-03
Check your private messages.

L.

---

### Post by otake-tux on 2006-03-04
hello, I'm having the exact same problem as the author of this thread.

I own an Acer 5004WLMi  ,  I have the broadcom driver and I have ndiswrapper installed.   The machine does seem to detect wireless access points but she cannot connect to them, be they open or not.  Right now I'm at a hotel with an open dhcp connection and the card will see the network but she wont connect.  Same thing happened at a cafe I was at earlier and at my home.  

plz help.

---

### Post by ltmon on 2006-03-04
Hi,

I tried to help out gtkorounis on IRC, but we didn't get it working.

I think there may have been a problem with his WEP key, so I suggest you check that, but otherwise we didn't have any luck so far.

You might post the output to the following 2 commands:
```

sudo ifdown wlan0 && sudo ifup wlan0

```
and:
```

cat /etc/network/interfaces

```

I'll check and see if anything stands out.

L.

---

### Post by otake-tux on 2006-03-05
It's not my wep key.  another machine had ubuntu on it and it could connect to wireless just fine.

Again, my machine can see the networks she just cant connect.  Also the wireless light doesn't even blink.


I'll post the output of those two commands when I get back to my machine.  Thanks for your help.

---

### Post by Monkeh on 2006-03-05
Try updating your kernel. I have a 3003WLMi and the wireless didn't work until I updated to 2.6.15 (I'm using Gentoo on it).

---

### Post by otake-tux on 2006-03-05
fixed it.  the problem was the network  manager gui.

to solve it I just entered the correct information in 
etc/network/interfaces

should anyone need help  with this, pm me.

---

### Post by gtkourounis on 2006-03-05
so wait what was wrong there? and oh ya sorry for me not responding but i had a bunch of band rehearsals and there is a gig coming up so... i was busy the last couple of days.

---

### Post by gtkourounis on 2006-03-05
and by the way that file for me is blank there is nothing in there.... is it just me or do i have to write something there?

---

### Post by ltmon on 2006-03-05
[QUOTE=gtkourounis]and by the way that file for me is blank there is nothing in there.... is it just me or do i have to write something there?[/QUOTE]

What file?

You posted /etc/network/interfaces to me whilst on IRC if you remember rightly, and it wasn't blank.

Cheers,

L.

---

### Post by gtkourounis on 2006-03-06
hey,
sorry ltmon but i have a lot of tests and projects due this week so i will probably not be going on my computer to try to fix my wireless for quite some time. I will probably update you on this topic this thursday. Thanx for the help so far and i hope the progress will continue after this thursday. if i get the time i will update you sooner.

l8er guys.

---

### Post by SBFC on 2006-03-07
I started following along with the link provided in one of the first posts. I was going to install the ndiswrapper packages...but, do you need to be running the 2.6.12 kernel to do so?

---

### Post by ltmon on 2006-03-07
[QUOTE=SBFC]I started following along with the link provided in one of the first posts. I was going to install the ndiswrapper packages...but, do you need to be running the 2.6.12 kernel to do so?[/QUOTE]

Hi,

You shouldn't have to be running any special kernel, just the default Breezy kernel.

Are you compiling ndiswrapper or are you installing it from the repositories?

L.

---

### Post by SBFC on 2006-03-07
Turns out I was still using Hoary. All is well now though, upgraded. :P

Can you install it from the repositories? Doesn´t that just download the src, but you still have to compile it? At this point I was just gonna follow those instructions. :P

---

### Post by ltmon on 2006-03-07
No, you don't have to compile.

In a standard Breezy installation:

sudo apt-get install ndiswrapper

Will install it.

You should then follow the wiki instructions to load it and install your card drivers.

L.

---

### Post by fmax on 2006-03-09
When I try to load the module I get this error:

max@Coffee:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-amd64-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

And dmesg:

[ 1158.169405] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[ 1158.171218] ndiswrapper (wrapper_init:1534): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'

Can you help me?

Does somebody have a problem with the battery?
I can't use it.

The notebook:
Acer Aspire 5002 WLMI


Thanks.

---

### Post by dpickle on 2006-03-11
Hey guys i have the same problem.....except now i went and bought a 50 dollar linksys card to see if that would work....but it didnt because the linksys made by cisco has a broadcom component in it.........bummer ive tried the ndiswrapper thing over and over and by the way what would the linksys card be under wlan1? its on the side in the remote slot of my hp dv1207us it powers up but cant get it configured and does the ndiswrapper work with linksys wpc54g  ...iget the light to work on wlano after wrapping its driver and i get a 100% signal but no internet.   the linksys card powers  up but its not recognized as wlan1 2 3   or eth1 cant find it havent tried sit o
so now both cards dont work and i can only use my wireless in windows.


:evil:   i really like this os and truly want it to work so i can get rid of windows once and for all! sincerely dpickle

p.s. HELP!?

---

### Post by gtkourounis on 2006-03-12
well i got back to my linux and i thought i should show the results from the two comnads that ltmon gave me a long time ago....

here they are 


> gtkourounis@gtkourounis:~$ sudo ifdown wlan0 && sudo ifup wlan0
Password:
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6335
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:14:a4:4d:90:7b
Sending on   LPF/wlan0/00:14:a4:4d:90:7b
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:14:a4:4d:90:7b
Sending on   LPF/wlan0/00:14:a4:4d:90:7b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
gtkourounis@gtkourounis:~$



and


> gtkourounis@gtkourounis:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Inferno
wireless-key 2101199013

auto wlan0

auto eth0
gtkourounis@gtkourounis:~$


---

### Post by ltmon on 2006-03-15
Well, unfortunately I haven't gotten any further with this problem either... I'm fresh out of ideas for what could be going wrong.

For what it's worth try the following command also:
```

iwconfig

```

and print out the result.

L.

---

### Post by jadaz87 on 2006-03-15
hello guys i am having the same problem i have a Broadcom 4306 in my HP Pavilion ze5500 desktop replacement laptop. here are the results for issuing those four commands. i can see wireless networks i just cannot connect to them :(

**also i was wondering how to i upgrade the kernel on here?

sudo ifdown wlan0 && sudo ifup wlan0:
```
 There is already a pid file /var/run/dhclient.wlan0.pid with pid 8017
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:45:e4:0a
Sending on   LPF/wlan0/00:90:4b:45:e4:0a
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:45:e4:0a
Sending on   LPF/wlan0/00:90:4b:45:e4:0a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping. 
```

cat /etc/network/interfaces:
```
 # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0


iface wlan0 inet dhcp
wireless-essid 04Z410225287
wireless-key s:xxxxx

auto wlan0 
```

iwconfig:
```
 lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6970   Missed beacon:0

sit0      no wireless extensions. 
```

---

### Post by jadaz87 on 2006-03-15
HEY GUYS I GOT IT TO WORK!!! HUZZAH!!!

do not use the Network configuration for wireless it does not work on Broadcom/ndiswrapper go to add application>internet>more programs>wifi-radar

you are going to need to plug up to lan in order to install it
then once you have it installed
click the network you want to connect to it will ask you whether you want to create a new profile and click yes
fill out the information and click ok
then click connect
Working.....Getting IP.....Got IP!!! :-)

---

### Post by gtkourounis on 2006-03-15
as weird as it may sound it didnt work for me, but i want to ask if i should upgrade to the beta version of dapper drake or if i should wait untill ubuntu publishes the actuall version of it? ltmon you are using dapper drake so i was wondering if you could tell me if thats a good idea.

---

### Post by ltmon on 2006-03-15
I found the upgade a bit of a pain, but once it was upgraded it has run smoothly for me ever since.  I would recommend not using Synaptic for upgrading, but rather doing the terminal command:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

This is after you have modified the file /etc/apt/sources.list to include all the Dapper drake sources.

Alternatively you can just reinstall from the Dapper Flight 5 CD.

Be aware that things are changing quickly, and the main result of this is that I seem to have another 50Meg of updates to apply whenever I get home at night.  If you have a slow connection or one with a low bandwidth limit this will be a pain.

Of course it's not even guaranteed to fix your problem ;) but I've heard tell that Broadcom cards are better supported in Dapper.

L.

---

### Post by gtkourounis on 2006-03-15
how do you change the /etc/apt/sources.list?

i downloaded the cd but i cant get it to work, that means i start the computer but it wont boot from it.

---

### Post by ltmon on 2006-03-15
This thread should help: [http://ubuntuforums.org/showthread.php?t=144465](http://ubuntuforums.org/showthread.php?t=144465)
This one is probably better: [http://ubuntuforums.org/showthread.php?t=135811](http://ubuntuforums.org/showthread.php?t=135811)

---

### Post by ltmon on 2006-03-16
Stop everything :)

I just found a wiki page which is probably going to help without the pain of updating to an unstable version of Ubuntu.

I didn't find this before, because it is classified under the driver name (bcm43xx) rather than something simple like "Broadcom".

It's really well written and contains a few extra tweaks that apparently need to be followed if you want your card to work.

[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)

Cheers,

L.

---

### Post by gtkourounis on 2006-03-16
amazingly enough even this page didnt solve my problems. lol, i dont know whats wrong with my computer and ubuntu. Not only the wireless but it wont uprgade me to dapper drake lol. I change the file that i have to change but the graphics stay the same, i restart my computer and i am still in breezy badger. I also downloaded the CD for dapper drake but for some reason it wont work, i guess i have to make it a bootalble cd but unfortunately i dont know how to do that. lol. well i guess i will have to wait untill the actuall dapper drake comes out. Ltmon if you have any idea on how to help me pls tell me lol. And again thanx for the help so far. i appreciate it. l8er


PS: i made one of my friends use ubuntu also. LOL, ubuntu is going to go worldwide soon....

---

