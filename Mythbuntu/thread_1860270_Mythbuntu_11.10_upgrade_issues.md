---
title: "Mythbuntu 11.10 upgrade issues"
date: 2011-10-14
forum: Mythbuntu
---

### Post by colin.mcgregor on 2011-10-14
Small note, Mythbuntu 11.10 is out and I am doing the upgrade on my two MythTV boxes (a living room backend/frontend box and a bedroom frontend only box). Bottom line, issues on boxes....
 
On both boxes, issues getting X to start. After rebooting I can do a <Ctrl>+<Alt>+<F4> log in to a BASH prompt type "startx" and all is well there, but that is not being handled properly automatically.
 
On the frontend only box, there are audio issues (read, no audio) and image quality problems with HD recordings.
 
I'll post more as I get to the bottom of this.
 
 
 
Colin McGregor

---

### Post by thatguruguy on 2011-10-14
What kind of video card do you have?

---

### Post by colin.mcgregor on 2011-10-14
> **thatguruguy said:**
> What kind of video card do you have?

Both are nVidia GeForce cards, one an 8200 the other a 6200.

---

### Post by superm1 on 2011-10-14
> **colin.mcgregor said:**
> Small note, Mythbuntu 11.10 is out and I am doing the upgrade on my two MythTV boxes (a living room backend/frontend box and a bedroom frontend only box). Bottom line, issues on boxes....
 
On both boxes, issues getting X to start. After rebooting I can do a <Ctrl>+<Alt>+<F4> log in to a BASH prompt type "startx" and all is well there, but that is not being handled properly automatically.
 
On the frontend only box, there are audio issues (read, no audio) and image quality problems with HD recordings.
 
I'll post more as I get to the bottom of this.
 
 
 
Colin McGregor

There has been some reports of the lightdm transition not working properly for some people.  Check your logs in /var/log/lightdm/ 

If there are errors about a unity-greeter, please remove the package 'unity-greeter' and make sure 'mythbuntu-lightdm-theme' is installed.

You may have to reconfigure automatic login too (there is no longer a GUI tool).

Here's a sample /etc/lightdm/lightdm.conf if your automatic login needs to be fixed.

```
[SeatDefaults]
autologin-guest=false
autologin-user=supermario
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=mythbuntu
allow-guest=false
```

---

### Post by nickrout on 2011-10-14
> **colin.mcgregor said:**
> Small note, Mythbuntu 11.10 is out and I am doing the upgrade on my two MythTV boxes (a living room backend/frontend box and a bedroom frontend only box). Bottom line, issues on boxes....
 
On both boxes, issues getting X to start. After rebooting I can do a <Ctrl>+<Alt>+<F4> log in to a BASH prompt type "startx" and all is well there, but that is not being handled properly automatically.
 
On the frontend only box, there are audio issues (read, no audio) and image quality problems with HD recordings.
 
I'll post more as I get to the bottom of this.
 
 
 
Colin McGregor

when you go to a terminal don't use startx, try ```
sudo /etc/init.d/gdm start
```

---

### Post by superm1 on 2011-10-14
> **nickrout said:**
> when you go to a terminal don't use startx, try ```
sudo /etc/init.d/gdm start
```

Actually, there was a transition from GDM to LightDM that was supposed to happen automatically for 11.10.  So it should be

sudo start lightdm
or
sudo stop lightdm

To start/stop.

---

### Post by colin.mcgregor on 2011-10-14
> **superm1 said:**
> Actually, there was a transition from GDM to LightDM that was supposed to happen automatically for 11.10.  So it should be

sudo start lightdm
or
sudo stop lightdm

To start/stop.

Interesting. As noted startx works (run as an non-root user). On the other hand:

sudo start lightdm

dies an ugly death. So, what environment variables are different...

---

### Post by ulysses768 on 2011-10-14
I had the same problem as well.  I installed mythbuntu-lightdm-theme and mythbuntu-desktop.  Boots with no problems now.  Unfortunately I now have pink vertical lines running through my playback.  I thought it was a video card issue but I have the same problem with intel, nvidia, and amd/ati cards on local and remote frontends.

---

### Post by superm1 on 2011-10-14
So both of you encountered this problem specifically because you didn't have mythbuntu-desktop installed, correct?

I just want to understand how prevalent this problem is.  

As for your pink lines, that's a bit disconcerting - I haven't encountered that on the NVIDIA boxes I was testing.

---

### Post by ulysses768 on 2011-10-14
I did have installed in 11.04, no other *Ubuntus, few packages added, and no ppas.

---

### Post by slaterson on 2011-10-15
i am having some rather significant issues as well.  everything was working great prior to the upgrade from 11.04 (which was upgraded from 10.10, which was upgraded from 10.04 - all without issue).

**mythtv-backend** is not automatically starting.  i've got to manually start it when restarting the computer.

**audio is not fully functional**.  i have several sound cards installed in the box - an hda-intel, an nvidia hd (via hdmi), two rme96 and a usb mic included from a webcam.  the rme96 cards now fail to be probed with:

```
[   12.618247] cannot find the slot for index 1 (range 0-1), error: -16
[   12.618253] RME Digi96: probe of 0000:02:00.0 failed with error -16
[   12.618257] cannot find the slot for index 1 (range 0-1), error: -16
[   12.618259] RME Digi96: probe of 0000:02:01.0 failed with error -16
```

these were all working perfectly prior to the upgrade, i'm not sure what has gone wrong here.

**auto login is not working**.  i followed the advice above re: lightdm.conf and uninstalling unity-greeter (this solved the big issue of having a blank screen, huge step forward, still a long way to go yet).

i'm kind of frustrated.  i want my fully functional system back, and so does the wife. :)  all help is appreciated!

---

### Post by slaterson on 2011-10-15
small update...  i can start mythtv-backend manually after the system is booted.  checking the logs (after some sleep) some of myth backend config files cannot be read, a good indication of why its not starting automatically.

the reason the config files cannot be read?  they are on a nfs mounted /home partition.  i have tried modifying the 'start on' conditions for mythtv-backend to:

```
start on (local-filesystems **and remote-filesystems and net-device-up IFACE=eth0** and started udev-finish)
```

however no dice yet.  how do i ensure that all remote file systems are mounted prior to starting mythtv-backend?  this was working great in 11.04.  i need to do the same thing with lightdm.  basically, i need as many services as possible to wait until the network is up and all filesystems are mounted.

---

### Post by superm1 on 2011-10-15
> **slaterson said:**
> small update...  i can start mythtv-backend manually after the system is booted.  checking the logs (after some sleep) some of myth backend config files cannot be read, a good indication of why its not starting automatically.

the reason the config files cannot be read?  they are on a nfs mounted /home partition.  i have tried modifying the 'start on' conditions for mythtv-backend to:

```
start on (local-filesystems **and remote-filesystems and net-device-up IFACE=eth0** and started udev-finish)
```

however no dice yet.  how do i ensure that all remote file systems are mounted prior to starting mythtv-backend?  this was working great in 11.04.  i need to do the same thing with lightdm.  basically, i need as many services as possible to wait until the network is up and all filesystems are mounted.
You can try starting on the finish of mountall-net perhaps?

---

### Post by slaterson on 2011-10-15
> **superm1 said:**
> You can try starting on the finish of mountall-net perhaps?

unfortunately that didn't work. :(  i'm stumped at the moment.

---

### Post by ulysses768 on 2011-10-16
> Unfortunately I now have pink vertical lines running through my playback. I thought it was a video card issue but I have the same problem with intel, nvidia, and amd/ati cards on local and remote frontends.

Just in case anyone else had this problem.  The source of the trouble is libmpeg2.  Switching the playback to ffmpeg and xvideo fixed the problem.

---

### Post by colin.mcgregor on 2011-10-17
> **superm1 said:**
> There has been some reports of the lightdm transition not working properly for some people.  Check your logs in /var/log/lightdm/ 

If there are errors about a unity-greeter, please remove the package 'unity-greeter' and make sure 'mythbuntu-lightdm-theme' is installed.

You may have to reconfigure automatic login too (there is no longer a GUI tool).

Here's a sample /etc/lightdm/lightdm.conf if your automatic login needs to be fixed.

```
[SeatDefaults]
autologin-guest=false
autologin-user=supermario
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=mythbuntu
allow-guest=false
```

This is the guts of the solution to the startx issue. In summary:

```
$ sudo su
# apt-get update
# apt-get upgrade
# apt-get remove unity-greeter
# apt-get install lightdm
# cd /etc/lightdm/
# mv lightdm.conf lightdm.conf.old
# pico lightdm.conf
```

In the lightdm.conf file put the following:

```
[SeatDefaults]
autologin-guest=false
autologin-user=<<your mythtv user ID, ie: superm1 or whatever>>
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=mythbuntu
allow-guest=false
```

The above helps a lot, but ... I still am seeing audio issues on my client only box.

---

### Post by superm1 on 2011-10-17
> **colin.mcgregor said:**
> This is the guts of the solution to the startx issue. In summary:

```
$ sudo su
# apt-get update
# apt-get upgrade
# apt-get remove unity-greeter
# apt-get install lightdm
# cd /etc/lightdm/
# mv lightdm.conf lightdm.conf.old
# pico lightdm.conf
```

In the lightdm.conf file put the following:

```
[SeatDefaults]
autologin-guest=false
autologin-user=<<your mythtv user ID, ie: superm1 or whatever>>
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=mythbuntu
allow-guest=false
```

The above helps a lot, but ... I still am seeing audio issues on my client only box.

Can someone who encountered the problems with lightdm please make sure to file an upgrade bug:

```
ubuntu-bug update-manager
```

We need to get to the bottom of why update-manager decided to make these bad decisions in the upgrade, so that will file the logs from the upgrade into a bug report.

Thanks,

---

### Post by colin.mcgregor on 2011-10-17
> **superm1 said:**
> Can someone who encountered the problems with lightdm please make sure to file an upgrade bug:

```
ubuntu-bug update-manager
```

We need to get to the bottom of why update-manager decided to make these bad decisions in the upgrade, so that will file the logs from the upgrade into a bug report.

Thanks,

Done, see: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/876945](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/876945)

---

### Post by straxus on 2011-10-18
> **ulysses768 said:**
> Just in case anyone else had this problem.  The source of the trouble is libmpeg2.  Switching the playback to ffmpeg and xvideo fixed the problem.

I can confirm this behavior.

---

### Post by nickrout on 2011-10-18
> **straxus said:**
> I can confirm this behavior.

Time to change anyway, libmpeg2 will be removed from 0.25.

[http://www.mythtv.org/wiki/Release_Notes_-_0.25](http://www.mythtv.org/wiki/Release_Notes_-_0.25)

---

### Post by markofealing on 2011-10-19
> **colin.mcgregor said:**
> This is the guts of the solution to the startx issue. In summary:

```
$ sudo su
# apt-get update
# apt-get upgrade
# apt-get remove unity-greeter
# apt-get install lightdm
# cd /etc/lightdm/
# mv lightdm.conf lightdm.conf.old
# pico lightdm.conf
```

In the lightdm.conf file put the following:

```
[SeatDefaults]
autologin-guest=false
autologin-user=<<your mythtv user ID, ie: superm1 or whatever>>
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=mythbuntu
allow-guest=false
```


The above resolved my problem of a blank screen after an upgrade. 

I fixed mine by SSHing in to the Mythbuntu server from my laptop and then making the changes, followed by a reboot.

Not sure how this sort of bug got past the testers!

Many thanks.

---

### Post by slaterson on 2011-10-19
> **slaterson said:**
> **mythtv-backend** is not automatically starting.  i've got to manually start it when restarting the computer.

**audio is not fully functional**.  i have several sound cards installed in the box - an hda-intel, an nvidia hd (via hdmi), two rme96 and a usb mic included from a webcam.

**auto login is not working**.  i followed the advice above re: lightdm.conf and uninstalling unity-greeter (this solved the big issue of having a blank screen, huge step forward, still a long way to go yet).

i've made some progress on my issues and wanted to share.  not fully there yet.  i could use some suggestions...

**mythtv-backend** is still not starting automatically.  i've tried adding some dependencies to the service to ensue all remote filesystems are mounted, but that actually made the problem worse (i.e., no login screen at all!).

**audio** - i've got my rme96 cards up and running again.  i ran an update a yesterday, there was a new alsa-utils package and some other packages included (i didn't go through the list carefully) and pow, the cards are now probed and functional.  great, but this exposed another issue...

the group of all devices in /dev/snd/* is being set upon reboot to a group on the local box that doesn't exist in my ldap directory, GID 29.  this is the audio group in mythbuntu, of course.  however, i have been using GID 18 for audio, as this is what the entire rest of my network uses.  so, i deleted the group from the mythbuntu box (groupdel audio), then changed the group of the /dev/snd/* devices to 'audio', which indeed changed them to GID 18 correctly.  bam, the sound works and is accessible by the right users.  now i reboot, the group is reset to root (remember i deleted the local audio group GID 29).  where do i set the GID that the sound devices should or prevent them from being reset upon reboot?

**auto-login still isn't working for me.**  i have tried mucking with this a bit, but haven't dug in deep yet.  i tried the first suggestion on this thread, which got me a functional login screen, just not an auto-login screen.

---

### Post by markofealing on 2011-10-20
My mythtv backend is also not automatically starting after upgrading to 11.10 from 11.04. I also had the display issue you had (now fixed) as per this post.

I can start the backend manually from terminal. I'm using a native Linux file system EXT3, so I do not believe this issue is file system related as you suggest.

Which log files should I be looking at?

Does anyone have any other suggestions?

---

### Post by markofealing on 2011-10-20
I've now done some digging around as to why Mythbackend is not automatically starting:

1. mysql.txt is correctly sym linked and has the right ownership and permissions.

2. I can start mythbackend manually (ALT-F2) or add it in to Application Autostart, although on reboot this gets unticked?!? Using either method Mythbackend works so I think that this is correctly configured.

3. My mythbackend.log file is producing the following when mythbackend fails to start. I'm using a combined front/ backend and a static IP

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2011-10-20 19:20:48.841 Deleting UPnP client...
2011-10-20 19:20:49.555 Failed to init MythContext.
2011-10-20 19:21:04.897 mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431] [www.mythtv.org](www.mythtv.org)
2011-10-20 19:21:04.938 Using runtime prefix = /usr
2011-10-20 19:21:04.971 Using configuration directory = /home/mythtv/.mythtv
2011-10-20 19:21:05.005 Empty LocalHostName.
2011-10-20 19:21:05.039 Using localhost value of mythtvtest
2011-10-20 19:21:05.084 New DB connection, total: 1
2011-10-20 19:21:05.114 Unable to connect to database!
2011-10-20 19:21:05.148 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

................................................................................
2011-10-20 19:21:07.227 UPnPautoconf() - No UPnP backends found
2011-10-20 19:21:07.260 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2011-10-20 19:21:07.505 Deleting UPnP client...
2011-10-20 19:21:08.225 Failed to init MythContext.

If I run mythbackend via ALT-F2, nothing gets written to the log file and MythFrontend works fine.

Any ideas as to what is going on and why is this suddenly happening since the 11.10 upgrade?:(

---

### Post by nickrout on 2011-10-20
Is mythbackend trying to start before mysqld? That's what it looks like.

---

### Post by slaterson on 2011-10-20
> **slaterson said:**
> **mythtv-backend** is still not starting automatically.  i've tried adding some dependencies to the service to ensue all remote filesystems are mounted, but that actually made the problem worse (i.e., no login screen at all!).

**audio** - the group of all devices in /dev/snd/* is being set upon reboot to a group on the local box that doesn't exist in my ldap directory, GID 29.  this is the audio group in mythbuntu, of course.  however, i have been using GID 18 for audio, as this is what the entire rest of my network uses.  so, i deleted the group from the mythbuntu box (groupdel audio), then changed the group of the /dev/snd/* devices to 'audio', which indeed changed them to GID 18 correctly.  bam, the sound works and is accessible by the right users.  now i reboot, the group is reset to root (remember i deleted the local audio group GID 29).  where do i set the GID that the sound devices should or prevent them from being reset upon reboot?

**auto-login still isn't working for me.**  i have tried mucking with this a bit, but haven't dug in deep yet.  i tried the first suggestion on this thread, which got me a functional login screen, just not an auto-login screen.

a bit more progress on the audio piece.  the permissions are set by a udev rule upon startup, /lib/udev/rules.d/50-udev-default.rules.  i just edited this file to use the a group # (18, in my case) instead of the name (audio).  my assumption is that udev is running prior to ldap being available, therefore when udev tries to set the group to 'audio', it doesn't exist.  problem is, when there is an update to udev, it will overwrite my update.

still haven't figured out the mythbackend auto start problem.  i have mysql set as a dependency to mythtv-backend in the start up scripts, but no dice.

---

### Post by GuiGuy on 2011-10-21
> **superm1 said:**
> 
Here's a sample /etc/lightdm/lightdm.conf if your automatic login needs to be fixed.

```
[SeatDefaults]
autologin-guest=false
autologin-user=supermario
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=mythbuntu
allow-guest=false
```


Many thanks. The upgrade just about broke everything for me. Eventually I got it to  boot (ESC wouldn't give me the recovery console :( ) but then went to a black screen and no cursor. The provided code got me past that and at least mythtv is running now and I can see the front end. 

LIRC however is dead as and the Mythbuntu CP hangs when I try to reconfigure the Infrared RC. :(

---

### Post by slaterson on 2011-10-21
i'm considering wiping the hard drive and starting from zero.

do brand new installs of 11.10 work better than upgrading from 11.04?  if so, i've got a reinstall to do this weekend.

---

### Post by markofealing on 2011-10-21
> **nickrout said:**
> Is mythbackend trying to start before mysqld? That's what it looks like.

On boot, if I press a key when I get up the Mythbuntu splash screen, I can see boot progress. This is what is happening:

Stopping userspace boot splash [ok]
Starting Mythbuntu backend [ok]
Waiting for Network configuration
Starting Mythbuntu backend [ok]
Starting Mythbuntu backend [ok]
Starting Mythbuntu backend [ok]
Starting Mythbuntu backend [fail]
Stopping Mythbuntu backend [ok]
Waiting up to 60 more seconds for network configuration

What you suggested and this message "Waiting for Network configuration" got me thinking! My PC has two network cards of which only one is connected and configured.

I checked my /etc/network/interfaces file and found the following:

[I]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

# iface eth0 inet static
# address 192.168.1.112
# netmask 255.255.255.0
# broadcast 192.168.1.255
# gateway 192.168.1.254

auto eth1
# iface eth1 inet dhcp

iface eth1 inet static
address 192.168.1.102
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.254[/I]

Commented out

[I]auto eth0
iface eth0 inet dhcp[/I]

Rebooted and problem solved, message "Waiting for Network configuration" did not come up, Mythbuntu booted up normally and quickly and MythWelcome worked.

This was not a problem before the upgrade, so I assume Ubuntu 11.10 does more rigorous testing of your network interfaces before giving up. Unfortunately this takes nearly 2 minutes which is enough time for mythbackend to time.

Really happy :D and thank you for pointing me in the right direction.

---

### Post by marcovanbeek on 2011-11-05
I have just upgraded to 11:10 and had much the same problems. The box was a frontend only, but I also seemed to have a problem with lcdproc as well.

I also think that the slowness of Network Manager is down to all the extra modules it loads. My logs seemed to indicate it was trying to find bluetooth interfaces on a computer that has never had a bluetooth interface.

I manually configured /etc/network/interfaces, removed network manager and my boots were back to their normal fast speed.

Thanks for the lightdm tip!

Marco.

---

### Post by nwwoods on 2011-11-05
Same issue here, upgrade from 11.04 and no apparent issues, but blank screen.  Putting in a proper lightdm.conf and getting rid of unity-greeter got the screen back and let it go directly to the mythtv frontend.

Audio started working after rebooting with above config set - somehow it properly detected the Intel HDA digital audio.

The pink lines on playback seems to be connected to using libmpeg2 on TV Playback settings.  Choose a setting that doesn't use it (or create a custom one) and playback seems normal.

---

### Post by bluexrider on 2011-11-05
For all the upgrade issues I think I will hang back and let the bugs out the windows

:P

---

### Post by nickrout on 2011-11-05
> **nwwoods said:**
> Same issue here, upgrade from 11.04 and no apparent issues, but blank screen.  Putting in a proper lightdm.conf and getting rid of unity-greeter got the screen back and let it go directly to the mythtv frontend.

Audio started working after rebooting with above config set - somehow it properly detected the Intel HDA digital audio.

The pink lines on playback seems to be connected to using libmpeg2 on TV Playback settings.  Choose a setting that doesn't use it (or create a custom one) and playback seems normal.

libmpeg2 support will be gone in mythtv 0.25 anyway, so it's a good time to get rid of it in preparation :)

---

### Post by pops66 on 2011-11-09
> **colin.mcgregor said:**
> This is the guts of the solution to the startx issue. In summary:

```
$ sudo su
# apt-get update
# apt-get upgrade
# apt-get remove unity-greeter
# apt-get install lightdm
# cd /etc/lightdm/
# mv lightdm.conf lightdm.conf.old
# pico lightdm.conf
```

In the lightdm.conf file put the following:

```
[SeatDefaults]
autologin-guest=false
autologin-user=<<your mythtv user ID, ie: superm1 or whatever>>
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=mythbuntu
allow-guest=false
```




Some people might want to know that I had to remove both .Xauthority and .ICEauthority
```

rm ~/.ICEauthority ~/.Xauthority

```

---

### Post by mart2072 on 2011-11-20
> **bluexrider said:**
> For all the upgrade issues I think I will hang back and let the bugs out the windows

:P

I think you're right. I've tried upgrading today and experienced all the issues mentioned here and I've given up and gone back to my back-up version. I don't think I'll bother trying again!

---

### Post by nickrout on 2011-11-20
Why would anyone upgrade a working system?

---

### Post by mart2072 on 2011-11-20
> **nickrout said:**
> Why would anyone upgrade a working system?
Because you might be under the mistaken belief that it improves the system? Why offer the option to upgrade if there is no point?

---

### Post by nickrout on 2011-11-20
> **mart2072 said:**
> Because you might be under the mistaken belief that it improves the system? Why offer the option to upgrade if there is no point?

Because mythbuntu is part of the ubuntu ecosystem. myth is very sensitive, and it doesn't pay to change what works.

---

### Post by timswait on 2011-12-27
Thank you to supermario and colin mcgregor, that saved me from a blank screen of doom after an upgrade to 11.10 :) Like others I upgraded a working system in the hope that the odd little niggle that wasn't quite right would be improved. Won't be doing that again in a hurry! The previous upgrade from 10.10 to 11.04 was flawless though.
Everything seems to be working fine now except it doesn't auto login, I have to enter a password. Is there any easy fix for this, if not I'll just put up!

---

### Post by tonka256 on 2012-02-17
> **slaterson said:**
> i'm considering wiping the hard drive and starting from zero.

do brand new installs of 11.10 work better than upgrading from 11.04?  if so, i've got a reinstall to do this weekend.


I can confirm... upgrade - nightmare

so bombed and fresh install - 99%correct of the bat.

worth the extra bit...

---

### Post by maszyny on 2012-03-22
Rental of construction machinery is a utility which can be against indubitably in another parts of Bone up on and of surely answerable to conflicting conditions, depending on what our needs and opportunities. Very much a capacious conform of construction firms instead of buying, just renting the motor car, as it is notwithstanding them extremely useful resolution that in the want hoof it reserve you definitely a bit.  
  
Construction machinery [e-maszyny](http://www.e-maszyny.info.pl/) throughout hire, such as cranes, excavators, backhoe or other, are quite expensive to advocate, if we take into account their purchase. Renting them, we basic not upset about their maintenance and garaging, which could also result to be absolutely troublesome. These steps assumes the possessor of the machine.  
  
Rental of construction machinery is workable not alone in the interest of businesses but for people who call to do some slave away in undisclosed construction and fully no require to bribe specialized trappings in spite of tens of thousand. In ordinary, while lending machines must pay a consign, which is every now quite high-class, but is refunded when we throw in the towel the cabal in such a phase in which it had at the beginning. The more days of hire, this is usually lower than the amount on daily manipulate of clear-cut hardware.  
 It's significance it!

---

### Post by kredytac on 2012-03-23
Virtual Birthday card is a fresh genus of payment cards designed exclusively fit the payment card without the employ of the material. They need not suffer with physical riches - often they are simply printed figures including card number, expiry appointment and designate of the owner. Occasionally we rally with a plastic debit card resembling a average counterpart, but it intention not have a attractive complexion or chip. It inclination be contrariwise a carrier of materials that you prerequisite to be sure to be skilful to sake from ekarty.    The utility of this business card is its availability. Substantially everybody who has an account at a bank may try one's hand at to be in vogue it. There are associated with no income requirements, no lack to have fair hold accountable, does not include, nor majority nor profession. Virtual Union card is a specific card that does not make the purchase in a look for or withdraw spondulix at an ATM. This is because it is designed to fulfill orders placed by phone [Karta kredytowa](http://kredytacja.pl/) , mail (called MOTO - Post Fiat & Call up Importance) and e-mail. An illustration would be the pay for of subscriptions to magazines or goods from a shop dealing with mail-order sales. Aloft all, ekarty are fit increasingly everyday because they are the safest work looking for payment at online stores.    Each arrangement performed using a accepted card is subject to authorization. It is not generated PIN. To entire your payment, gladden give card gang, prestige of the holder, expiry age and verification jus gentium 'universal law' or CVC2 or CVV2 (model three digits located on retreat from of anniversary card). Grave conducive to the aegis of a virtual use strategy act openly annals made is also staunch that it has its own account, entirely self-governing of the account on which we agree to your money. That reason, we can delivery the becoming amount once payment (if payments are realizable solitary up to the overwhelmed amount), and after the Finite postal card purchases can be discharged so as not were no funds on it.

---

### Post by netkredyt on 2012-03-30
Economical Poland is not a bank, a fiscal institution of global character. It belongs to the financial party International Personal Assets, which specializes in providing undecorated, credible and open monetary products. Prudent operates in Poland on 15 years.  Shrewd Change advance is characterized by the suddenness of implementation and a small amount of paperwork. Unpretentiously friend a representative by phone or via the website. Signally recommended is the latter form of communication, because thanks to the allowance adding machine you can easily and effectively calculate how much, how and when we are clever to repay. Another advantage is no obscured charges - shows the result indicates the expense of the credit, avocation and use. At one time you decide on the most appropriate mixture for us, austerely send a request online. After a short at the same time association us Prepared consultant. If you give birth to questions or concerns, consultants issue sovereign advice. As looking for required documents, it is a standard lay when taking for all to see the allow - be required to be 18 years [Pilna Pozyczka Bank Millennium](http://net-kredyt.pl/) past it, have a unshakable check-in and automatic income.  Judicious loans have two options - Notes and Unite Bring Package. Be separate in the road of providing bread, but in both cases there is no want to leave the dynasty - in the first variant, the coins provides a representative Provident, the younger is payment on account of the borrower. It is recommended to smoke the Transfer Encase, because operating costs are lop off than as a service to Money Package. The persistence costs are included suitable all charges for facilities associated with the major availability of the loan. It is wholly this behoof sort is so low.  Provident Spondulicks loans - the most prominent info:  - Minimum allow amount is 300 PLN, peak 5 000 zl (for supplemental customers, benefit of people who already had benefited from the bid Wary characters upper class limit is 7 000 zl)

---

