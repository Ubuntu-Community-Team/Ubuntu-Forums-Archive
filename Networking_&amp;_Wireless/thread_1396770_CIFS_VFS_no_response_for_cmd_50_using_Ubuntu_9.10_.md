---
title: "CIFS VFS no response for cmd 50 using Ubuntu 9.10 Karmic Koala"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by solbot on 2010-02-02
I was also having a problem with the Shutdown / Reboot sequence taking ages due to using WiFi, WPA2 and mounting SMB shares.
I wasted about 4 hours digging around before I finally realised that the solution involved Upstart.

1. Open a terminal and enter:
```
sudo gedit /etc/init/network-manager.conf 
```

2. Just below the description line add the following:
```
pre-stop script
   /etc/init.d/umountnfs.sh
end script
```

3. Save the script and attempt a restart.

I don't know if this will work for everyone, or even what version of Upstart you need for it to work, but it cuts my shutdown time from about 2 mins to about 30 seconds.

*Note:* This has been working for me about 90% of the time.
Occasionally though I see that the script ends prematurely due to the TERM signal and I end up with the 2 minute wait again.
I've added the following to the /etc/init/network-manager.conf file:
```
pre-stop script
   trap "Caught TERM Signal" TERM
   /etc/init.d/umountnfs.sh
   trap - TERM
end script
```

Not sure if it works, but I haven't seen the TERM error yet.

---

### Post by bi0hazard on 2010-02-04
Yup, this worked for me! Thx! :D

---

### Post by ^_Pepe_^ on 2010-02-05
Yessssssssssssssss!

You rock!!

:guitar:

Thank you so much!

---

### Post by MrEgg on 2010-02-13
This worked for me too! Thanks!!

---

### Post by roalt on 2010-02-19
Have the same problem, but adding the script doesn't help. Look like the script is not executed when I do a shutdown. Any ideas?

---

### Post by solbot on 2010-02-19
What version of Ubuntu are you using?

---

### Post by slackware_user on 2010-02-20
All of this is related to mounting samba/cifs shares via fstab and using networkmanager to manage the wireless connections.  It is still possible to use nautilus mounts.  You can find them by issuing cat /etc/mtab and finding the hidden mount points for the shares.  The system can then umount them and shutdown is fine.  

But it is much nicer to have them mounted in a normal, consistent location!

There had been a workaround prior to my latest upgrade to 9.10.  Now the old fix, to rename the sysv rcX.d umountnfs shutdown scripts to K00umountnfs.sh, no longer works. Something to do with upstart?

This pre-stop script thing sounded reasonable, but no cigar.

The funny thing is that all of this nonsense would take 2 mins to fix in slackware.  So far, my experience with ubuntu is that it is very easy to get almost working, but very hard to get finally right.

I think my best bet, before finally blowing ubuntu away and going back to slack, is to try to bypass network-manager and configure the interface via /etc/network/interfaces. (This is so the interface will stay connected long enough to allow the umount).  So far, I have not been able to accomplish this, or even to get the interface (ath5k netgear wg511T) to connect via ifconfig and iwconfig commands that I know work with this interface in a slackware box.  Maybe uninstall networkmanager and try again?

This is starting to try my patience.

---

### Post by roalt on 2010-02-20
> **solbot said:**
> What version of Ubuntu are you using?

As the topic says: Karmic 9.10

Just like @slackware_user says: I also had a similiar solution for pre-Karmic Ubuntu to do the unmounting, but this does not work anymore as no /etc/rc*.d/K scripts are used any more by Upstart.

I do not understand why a mainstrean release like Ubuntu cannot handle the automatic mounting of shares on a server in combination with wireless/Network manager.

---

### Post by solbot on 2010-02-20
I don't understand why it won't either but I'll keep trying to come up with solutions until either I get it working perfectly or the devs fix the problem.

To Slackware_User, it's true you could do this pretty quickly with Slackware. You could do it with Gentoo or Fedora fairly rapidly too, but if we keep doing the same old thing all the time then eventually we'll fall behind and MS will win.

The Network Manager makes it almost as easy for new users to set up their networking as in Windows, and that's a good thing.

The bad part of it, for us that actually know how to edit things like fstab to mount shares, is when we try something that used to work but now doesn't.

It's basically a trade off between ease of use and power.
Upstart is such a massive change from the old SysV init scripts that I'm suprised there haven't been more glitches like this.

Anyway, I'll see if I can think of an alternate solution to your problem and get back to you.

---

### Post by a3101 on 2010-03-02
Doesn't work for me either.. Ubuntu, fits for all.. yeah right...

ver 9.10,My file looks like this:

```

# network-manager - network connection manager
#
# The Network Manager daemon manages the system's network connections,
# automatically switching between the best available.

description    "network connection manager"

pre-stop script
   /etc/init.d/umountnfs.sh
   trap - TERM
end script

start on (local-filesystems
      and started dbus)
stop on stopping dbus

expect fork
respawn

exec NetworkManager

```

---

### Post by betchern0t on 2010-03-03
This is actually a very very old bug in which ubuntu shutsdown the network before unmounting the shares. Something to do with cifs being a userspace driver. I had some hope that this was solved in 9.10 since it got a complete workup on launchpad for 9.04.

this thread is marked as solved, but from reading isn't. Does someone have a solution?

Cheers Paul

---

### Post by Darti on 2010-04-01
I was having the same problem for a long time, its not really a error its just annoying. Anyway after looking around and trying various things I have done the following which seems to work well.

My solution:

When restarting or shutting down Ubuntu will take down the system in the following order:

K01gdm
K02usplash
K19samba
K20exim4
K20winbind
K25hwclock.sh
K50alsa-utils
K63mountoverflowtmp
K74bluetooth
K99laptop-mode
README
S01linux-restricted-modules-common
**S15wpa-ifupdown**
S20sendsigs
S30urandom
**S31umountnfs.sh**
S35networking
S40umountfs
S60umountroot
S89casper
S90halt

As seen above the wireless interface is taken down **before** the umountnfs.sh is run. So from my understanding the script is not able to take the mount offline as the network interface is already down.

For my fix is simply renamed S31umountnfs.sh to S10umountnfs.sh in both the shutdown (rc0.d) and restart (rc6.d)

[B]cd /etc/rc0.d
sudo mv S31umountnfs.sh S10umountnfs.sh[/B]

[B]cd /etc/rc6.d
sudo mv S31umountnfs.sh S10umountnfs.sh[/B]

Dont know if others will have the same luck. [COLOR="Red"]**Also please be careful when changing the scripts as it can cause big problems**[/COLOR], also if anyone with better knowledge of the rc scripts can explain why the order was interface then umount ?? :confused:

---

### Post by lsutiger on 2010-05-06
I have been having the same error, but not when shutting down. It happens randomly while the computer is running.
This is quite a problem for me as the computer runs scripts to save files on the network shares over night. It's very aggravating when I working with a file and then I can not save it....

There are ton's of information on this error when logging of or restarting, but I haven't found on to fix while running.

Please help!!!

---

### Post by Radipon on 2010-05-09
I installed 10.04 LTS on my Toshiba Satellite A505 laptop, connecting through a wireless interface and requiring access to shares on a Windows 7 machine. 

I have tried all of the solutions outlined and none of them seem to work. My suspicion is that networkmanager is getting forcibly killed before umountnfs.sh can be invoked, which in turn disables the network connection before networking proper is taken down. That's my best guess to the scenario, and I'm not sure where to begin fixing it.

---

### Post by lsutiger on 2010-05-14
Darmok and Jalad at Tanagra!

I believe I have found the solution. I put together a couple of threads in order to make this go away.

1) I have the RTL8111/8168B PCI Express GB Ethernet Adapter on my board. This card is unreliable with the standard drivers from the kernel. If you have this card [URL="http://ubuntuforums.org/showthread.php?t=1022411&highlight=slow+browsing"]follow this link to update the driver from the manufacturer.
[/URL]

I noticed that my browsing speed increased after that update, but I would still have the CIFS VFS error in the log and my network shares were not consistently connected.

2) Then I ran across this blog:
[http://blog.dhampir.no/content/cifs-vfs-no-response-for-cmd-n-mid](http://blog.dhampir.no/content/cifs-vfs-no-response-for-cmd-n-mid)

You have to do the folllowing as sudo.
create a file with the following instructions```
# cifs client workaround
modprobe cifs
echo 0 > /proc/fs/cifs/OplockEnabled
```
Save the file in the /etc/init.d folder. Then make it executable
```
 chmod +x <scriptname>.
```
I then ran :
```
update-rc.d <scriptname> defaults 
``` and rebooted.

Haven't had a problem since...it has only been 3+ hours, but the problem usually shows it's face instantly.

Will follow up during the weekend...wish me luck :)

---

### Post by lsutiger on 2010-05-14
5 hours 25 minutes.
thats all...it shows it's face again :mad:
:sad::sad:

---

### Post by isolationism on 2010-05-23
For what it's worth, Darti's solution worked for me. I seem to recall this having worked in the past for me, then it stopped working for some time -- maybe because I was mounting mixed NFS/Samba share types. Now that I mount everything via NFS and moved all the NFS shares over everything is fixed.

I cannot, for the life of me, understand why this hasn't been fixed in a release yet. It's a trivial change and is a huge deal for mobile users as it means your laptop effectively fails to turn off; what gives?

---

### Post by lsutiger on 2011-06-22
Need to revive because it is still an issue! I receive the error when moving files to the share, not when booting or shutdown.

---

