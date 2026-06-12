---
title: "[SOLVED] Install Guide LIED"
date: 2008-01-04
forum: Mythbuntu
---

### Post by jeverettk on 2008-01-04
On page 16 of the mythbuntu installation manual it states:
"Feel free to explore around the disk.  No changes will be made to your system unless you proceed with Install Mythbuntu."

Actual experience:
- Ran Live CD - a little slow on the startup, but I figure it's initializing services to run MythTV from the get go, so that's nice.  
- Very attractive and simple interface - the docs say it's xfce, but in verbose mode it reported starting gnome - no biggie, someone probably just didn't change the dialog text.
- Menu's very intuitive 
- True to the docs, nothing unnecessary for MythTV - nice and lean - I like it.
- Took a look at MCC - great looking tool.
- At this point I was completely impressed and I probably will still go ahead and use this distro for my HTPC.

BUT
I removed the disc and restarted and the following occurred:
I opened my already completely setup MythTV test system on my currently installed distro, and it didn't work.
I went to re-run mythbackend from the terminal and what the hey? 
"[myusername@ubuntu ~]$ " pops up!!  Okay, that's not right.  I mean I can fix that, but that shouldn't be happening in the first place. 

Well, whatever... so, I type in mythbackend and get this response:
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.

At this point I swallowed hard.  Then I opened MythTV setup to find that my entire setup was completely reverted.  I mean crap that took a lot of work to set up- granted you guys have done a fantastic job of making a complex app work almost straight out of the box - but for almost any other distro, MythTV setup can flat out suck, and now I have to do it again!!!

At any rate, a few things obviously happened that should not be in a LiveCD

1. My existing partitions were mounted without me giving the go-ahead.  
2. Why in the world should my localhost name have been changed?
3. My existing MythTV setup was completely rewritten without my OK.
4. All of this happened with no warning in the docs - I mean I know "You take a risk every time you boot from disk." - it rhymes and it's easy to remember, but I thought I could take it for granted when the docs said nothing would be changed unless I did 'x'.

Hey, this isn't a total rant. You guys have done some great work here, but please toss a warning or disclaimer or something either in the install guide or a series of dialog boxes prior to making changes or something that reminds me not to act like a complete noob just because everything is so beautifully packaged.

Best of luck to you guys, and I think this may absolute best MythTV distro!  Just please make sure that you check and double check and re check statements like "No changes will be made to your system..."

---

### Post by superm1 on 2008-01-04
> **jeverettk said:**
> On page 16 of the mythbuntu installation manual it states:
"Feel free to explore around the disk.  No changes will be made to your system unless you proceed with Install Mythbuntu."

Actual experience:
- Ran Live CD - a little slow on the startup, but I figure it's initializing services to run MythTV from the get go, so that's nice.  
- Very attractive and simple interface - the docs say it's xfce, but in verbose mode it reported starting gnome - no biggie, someone probably just didn't change the dialog text.
- Menu's very intuitive 
- True to the docs, nothing unnecessary for MythTV - nice and lean - I like it.
- Took a look at MCC - great looking tool.
- At this point I was completely impressed and I probably will still go ahead and use this distro for my HTPC.

BUT
I removed the disc and restarted and the following occurred:
I opened my already completely setup MythTV test system on my currently installed distro, and it didn't work.
I went to re-run mythbackend from the terminal and what the hey? 
"[myusername@ubuntu ~]$ " pops up!!  Okay, that's not right.  I mean I can fix that, but that shouldn't be happening in the first place. 

Well, whatever... so, I type in mythbackend and get this response:
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.

At this point I swallowed hard.  Then I opened MythTV setup to find that my entire setup was completely reverted.  I mean crap that took a lot of work to set up- granted you guys have done a fantastic job of making a complex app work almost straight out of the box - but for almost any other distro, MythTV setup can flat out suck, and now I have to do it again!!!

At any rate, a few things obviously happened that should not be in a LiveCD

1. My existing partitions were mounted without me giving the go-ahead.  
2. Why in the world should my localhost name have been changed?
3. My existing MythTV setup was completely rewritten without my OK.
4. All of this happened with no warning in the docs - I mean I know "You take a risk every time you boot from disk." - it rhymes and it's easy to remember, but I thought I could take it for granted when the docs said nothing would be changed unless I did 'x'.

Hey, this isn't a total rant. You guys have done some great work here, but please toss a warning or disclaimer or something either in the install guide or a series of dialog boxes prior to making changes or something that reminds me not to act like a complete noob just because everything is so beautifully packaged.

Best of luck to you guys, and I think this may absolute best MythTV distro!  Just please make sure that you check and double check and re check statements like "No changes will be made to your system..."
don't start the backend like that.

```
sudo /etc/init.d/mythtv-backend restart
```

Nothing should have been modified on your machine.  This sounds coincidental to me...

If after running that command, the backend still isn't running, see 
/var/log/mythtv/mythbackend.log

---

### Post by jeverettk on 2008-01-04
I appreciate the support offer, but it's not needed.  I'm just writing to urge your devs to recheck their docs.  

Coincidental?  

Okay, I'm running PCLOS.  I've never previously run any ubuntu derivative on this machine and now, instead of localhost, when I boot up PCLOS, I'm somehow on a machine named ubuntu.  How is that coincidental?  I promise my non-ubuntu distro didn't somehow randomly rename the host.  

But you have a good point about the log.  I'll check it out.

---

### Post by superm1 on 2008-01-04
> **jeverettk said:**
> I appreciate the support offer, but it's not needed.  I'm just writing to urge your devs to recheck their docs.  

Coincidental?  

Okay, I'm running PCLOS.  I've never previously run any ubuntu derivative on this machine and now, instead of localhost, when I boot up PCLOS, I'm somehow on a machine named ubuntu.  How is that coincidental?  I promise my non-ubuntu distro didn't somehow randomly rename the host.  

But you have a good point about the log.  I'll check it out.
Well here is the thing though.  When in live mode, your hard drive is only mounted if you choose to follow through with the installer.  The hostname is changed while in live mode.  

All very odd...  Does this happen with standard ubuntu live disks too?

---

### Post by jeverettk on 2008-01-04
Okay, I'm wondering if the hostname could be the only problem

I checked in the log and saw again what I had seen before:
"No setting found for this machine's BackendServerIP."

That makes me think it's just not finding my database now that the hostname changed.  Then in the event of not having a database to look at, mythtv is just showing off its default settings.

Does that sound about right?  Still how did it rename my host without mounting something?

---

### Post by jeverettk on 2008-01-05
Okay, weirder still - I checked my /etc/hosts file and it doesn't list ubuntu.  This means my plan for fixing the hostname is at a loss, so please disregard the arrogant guy who pretended to be me refusing assistance.

PCLOS also runs/installs as a single LiveCD.  I'm wondering if there's a conflict created by a file that both LiveCDs use but delete on install.  Do you know where to look for the file that the LiveCD would use to store the default hostname?

---

### Post by jeverettk on 2008-01-05
Superm1,

Below is the result of 'find -newer /home/jason/Desktop/mythbuntu-7.10-i386.iso' from /etc

.
./mtab
./modprobe.conf
./printcap
./hotplug
./hotplug/blacklist
./issue.net
./issue
./lvm/.cache
./udev/rules.d
./sysconfig/system
./X11/gdm/gdm.conf
./adjtime
./asound.state
./resolv.conf

  These are all the files that have been modified since I downloaded the iso.  I know this is all off of a different system, but anything here stand out as a file that might be used by a LiveCD to effect a temporary default hostname?

---

### Post by superm1 on 2008-01-05
The file that controls the hostname

is /etc/hostname

---

### Post by jeverettk on 2008-01-05
No such file on my box. Are you sure the LiveCD uses the same...

Wait, thanks for your help by the way, but I didn't think to ask if you're work is specific to mythbuntu or how familiar you are with the LIveCD in general?  

I wouldn't keep bugging you, but I'm not used to dealing with an issue between two distros like this.  If you'd prefer I bark up another tree, I'd definitely appreciate a referral to a more appropriate source.

Any way, if you know, does the LiveCD use that same file to set the hostname or maybe something else?

I did find a number of kde socket related files with ubuntu all over them that seem to have popped up right after I ran mythbuntu.  But I don't know that that's the answer to fixing this or just another symptom.

Thanks for any leads you can give.  Meantime I'll be bugging some PCLOS devs for their perspective.  Cheers and happy new year.

---

### Post by ubnewbie2 on 2008-01-06
I had an experience which might be a clue here.   Having had a Mandriva distribution installed on a laptop, I then wiped it out and installed Ubuntu.

However, the machine still appeared as having the old hostname on the network (I know because I named it Mandriva-laptop - or something similar)

The only connection, I think, was that both installations used the same network card (obviously) with the same mac address to request an IP from the DHCP server on our network.  I think that the DHCP server learnt the Mandriva hostname somehow, and when the Ubuntu install requested an IP, the DHCP server assumed it was the same machine (true) and therefore same host (not true due toing a completely new operating system installed)

Someone who knows more about DHCP, ip address leases, etc may be able to confirm that this can happen, and hostnames persist.

---

### Post by superm1 on 2008-01-06
> **ubnewbie2 said:**
> I had an experience which might be a clue here.   Having had a Mandriva distribution installed on a laptop, I then wiped it out and installed Ubuntu.

However, the machine still appeared as having the old hostname on the network (I know because I named it Mandriva-laptop - or something similar)

The only connection, I think, was that both installations used the same network card (obviously) with the same mac address to request an IP from the DHCP server on our network.  I think that the DHCP server learnt the Mandriva hostname somehow, and when the Ubuntu install requested an IP, the DHCP server assumed it was the same machine (true) and therefore same host (not true due toing a completely new operating system installed)

Someone who knows more about DHCP, ip address leases, etc may be able to confirm that this can happen, and hostnames persist.
This is very much so the case.

Ubuntu's network manager (as of 7.10) will provide a hostname to the DHCP server if the DHCP server supports asking for it.  Some distros will set the hostname via a dhcp variable if it is provided from the DHCP server.

Odds are your other distro doesn't support telling the DHCP server what your hostname is, however it supports learning a hostname from the DHCP server.

---

### Post by superm1 on 2008-01-06
> **jeverettk said:**
> No such file on my box. Are you sure the LiveCD uses the same...

Wait, thanks for your help by the way, but I didn't think to ask if you're work is specific to mythbuntu or how familiar you are with the LIveCD in general?  
I lead development on Mythbuntu.  I am very familiar with how the live cd works internally, and custom wrote the script that builds it.

> 

I wouldn't keep bugging you, but I'm not used to dealing with an issue between two distros like this.  If you'd prefer I bark up another tree, I'd definitely appreciate a referral to a more appropriate source.

Any way, if you know, does the LiveCD use that same file to set the hostname or maybe something else?

As in my other response, I suspect the true cause was from the DHCP server.  The live cd will not mount the drive unless you ask it to.  Furthermore, if you do choose to mount the drive, nothing will be changed on the file system unless you chroot into it, hand modify items, or perform an installation into the mounted area.

> 
I did find a number of kde socket related files with ubuntu all over them that seem to have popped up right after I ran mythbuntu.  But I don't know that that's the answer to fixing this or just another symptom.

These may have popped up due to the changed hostname.  I would suspect they are in /tmp.

> 
Thanks for any leads you can give.  Meantime I'll be bugging some PCLOS devs for their perspective.  Cheers and happy new year.

No prob, hopefully this gets sorted out.

---

### Post by jeverettk on 2008-07-17
It looks like that was the case.  A simple reset and reboot on my router, and the hostname was restored to localhost.

Thanks, superm1!

---

