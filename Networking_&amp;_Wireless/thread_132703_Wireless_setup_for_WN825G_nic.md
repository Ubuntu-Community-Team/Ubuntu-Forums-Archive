---
title: "Wireless setup for WN825G nic"
date: 2006-02-18
forum: Networking &amp; Wireless
---

### Post by LinuxnutPete on 2006-02-18
Greetings all!
This is my first post.
I just got done installing ubuntu 5.10 on a HP Evo N610 C.
It's been one of the easiest linux distro's I've run into, and I think this one will be a keeper.
I'm a off and on linux user from Red Hat 5.0, and a former SCO Unix sysadmin, now mostly working on XP due to short sighted managemt. But I digress.
Ive been reading the networking posts since last evening, and found many flks has issus with getting the motorola WN825G to work.
So just to give back to the community, her''s how I got it to work.
1. Downloaded and unsipped the LATEST VERSION for the driver from Motorola.
#unzip <filename.exe>
this creates a directory with the .inf file you will need to install called bcmwl5.inf

2. download ndiswrapper-utils,  libunsheld and unshield from:
[http://packages.ubuntu.com/breezy/libs/libunshield](http://packages.ubuntu.com/breezy/libs/libunshield)
[http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils](http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils)
[http://tinyurl.com/82ko9](http://tinyurl.com/82ko9) <is for unshield just shortened the url
NOTE: found you dont need to install ndiswrapper as it's already compiled into the kernel, you just need the utilities.
install them all:
#dpkg -i libunshield* <enter>
#dpkg -i unshield* <enter>
<is you get and error, add sudo before dpkg as in #sudo dpkg>
#sudo dpkg -i ndiswrapper* <enter>

3. install the motorola nic driver. CD into the uncomplessed directory.
#sudo ndiswrapper -i bcmwl5.inf

you should see "installing" and will see 4 more files installed.

#sudo ndiswrapper -l <that's an L key>
which will show bcmwl5 driver present, and hardware present 

#sudo ndiswrapper -m
NOTE: put the nic into the slot
#sudo modprobe ndiswrapper
NOTE: light on nic will turn on

#sudo vi /etc/network/interfaces
go to the bottom of the file, use the i key to insert text, and the escape key when donw. So hit the i key when your on the last letter in that file, cursor over to the right one space, hit enter to start a new line and copy and paste the following

iface wlan0 inet dhcp
wireless-essid YOUR_ROUTER_NAME
wireless-key YOUR_ROUTER_KEY
wireless-mode Managed
auto wlan0

don't change the file directly thinking you should enter your router hostname or essid here. You will do that later from the Tool. Save what you did by hitting the colon key [:], so it will look like this
:!wq <enter>
close the file, check your handywork by reading the file
cat /etc/network/interfaces
if you still see all the test you entered, you're done, if not, it didn't save, so do it again.
NOTE: normally in vi, to save a file, you only need to hit :wq, short for write and quit. Sonce you are vi'ing the file as a sudo superuser, and not as root, [aka GOD] you need to hit the ! key first, as in :!wq <enter>

4. #sudo ifup wlan0
will cause the system to try grabbing a IP address from your DHCP server.
If you don't have WEP set up, it will get you an IP at this point and you're done.
Of course if it does, that also means either you are on a secure LAN behind a firewall, OR you did not implement any security on your WIFI router, called BAD.
If you did inplement WEP, then the above command will time out without getting you an IP, next you need to go to:
SYSTEM > ADMINISTRTION > NETWORKING
do a properties on your wilreless card, and enter the name of your router and it's WEP key, save it, and run # sudo ifup wlan0

then see what IP address you got:
#ifconfig wlan0 <enter>

ping your router and if that worked, you're done.

I hope this helps someone. Feel free to email me with questions, I will help as best as I can.

Keep the faith! Use Linux.

Pete

---

### Post by maximizer on 2007-08-09
Pete,

were you able to get it to work with WPA?  I can make it work with no encryption or with WEP, but I don't even see WPA option in settings.  Any ideas?  Thanks.

---

