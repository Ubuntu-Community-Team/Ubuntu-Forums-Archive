---
title: "Install Natty over an existing Ubuntu version"
date: 2010-10-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Steel-Bunz on 2010-10-14
In the last couple of weeks, a common request from my friends was to install 10.10 over an existing 10.04 install on _dual boot_ systems. They are fairly tech savvy, but, are worried about potential upgrade issues.
 
I googled and learned how to do it with manuall partitioning. Wouldn't it be great if it is offered as an option by the Installer?
 
Or, the option is already there and I am stupid enough to miss it?
 
Would love to know your thoughts.

---

### Post by cecilpierce on 2010-10-14
> **Steel-Bunz said:**
> In the last couple of weeks, a common request from my friends was to install 10.10 over an existing 10.04 install on _dual boot_ systems. They are fairly tech savvy, but, are worried about potential upgrade issues.
 
I googled and learned how to do it with manuall partitioning. Wouldn't it be great if it is offered as an option by the Installer?
 
Or, the option is already there and I am stupid enough to miss it?
 
Would love to know your thoughts.

You could try System>Administration>Update Manager, I think it asks if you want to upgrade, cant hurt to look !

---

### Post by xebian on 2010-10-14
> **Steel-Bunz said:**
> In the last couple of weeks, a common request from my friends was to install 10.10 over an existing 10.04 install on _dual boot_ systems. They are fairly tech savvy, but, are worried about potential upgrade issues.

Thanks for the chuckle.  

> **Steel-Bunz said:**
> 
I googled and learned how to do it with manuall partitioning. Wouldn't it be great if it is offered as an option by the Installer?
 
Or, the option is already there and I am stupid enough to miss it?
 
Would love to know your thoughts.

IIRC the installer offers you 3 options

It does it by itself automatically
or Guided
or you do it manually yourself.

Take the manual partitioning.

---

### Post by cariboo on 2010-10-14
If you choose manual partitioning and don't mark the partitions for formatting, you shouldn't have a problem. 

I doubt if we'll see and automatic option to do it, as it is basically the same as running:

```
update-manager -d
```

The only difference is one method uses the CD, the other uses a internet connection.

---

### Post by ssam on 2010-10-14
> **cariboo907 said:**
> If you choose manual partitioning and don't mark the partitions for formatting, you shouldn't have a problem. 

I doubt if we'll see and automatic option to do it, as it is basically the same as running:

```
update-manager -d
```

The only difference is one method uses the CD, the other uses a internet connection.

not really the same.

update-manager uses dpkg to update each package that is installed, and run their install scripts.

using the installer, but not formatting, deletes all the system folders (/usr, /lib ...), and then unpacks the live cd image onto the disk, then does a cleanup.

update-manager method is slow, but means you keep the same packages installed. the installer is fast but takes you back to the default package set.

---

### Post by keypox on 2010-10-15
> **cariboo907 said:**
> If you choose manual partitioning and don't mark the partitions for formatting, you shouldn't have a problem. 

I doubt if we'll see and automatic option to do it, as it is basically the same as running:

```
update-manager -d
```

The only difference is one method uses the CD, the other uses a internet connection.

This is so wrong you should really delete this post... your ubuntu staff? 

> **ssam said:**
> not really the same.

update-manager uses dpkg to update each package that is installed, and run their install scripts.

using the installer, but not formatting, deletes all the system folders (/usr, /lib ...), and then unpacks the live cd image onto the disk, then does a cleanup.

update-manager method is slow, but means you keep the same packages installed. the installer is fast but takes you back to the default package set.

---

### Post by cariboo on 2010-10-15
> **keypox said:**
> This is so wrong you should really delete this post... your ubuntu staff?

So according to you I should edit the thread to make myself look better? This just proves that I'm human too, and sometimes I do make mistakes.

---

### Post by nystire on 2010-10-15
> **cariboo907 said:**
> So according to you I should edit the thread to make myself look better? This just proves that I'm human too, and sometimes I do make mistakes.

*GASP* There are humans here???

Seriously though, we all make mistakes. We shouldn't be trying to go back and change the facts to make ourselves look better. Rather, make sure that the thread points out the problematic statment(s) as being incorrect and then giving the correct information in a clear and concise manner.

---

### Post by meborc on 2010-10-15
> **cariboo907 said:**
> So according to you I should edit the thread to make myself look better? This just proves that I'm human too, and sometimes I do make mistakes.

half of my posts on ubuntuforums are giving advice, the other half is apologizing for them being wrong :D

---

### Post by Steel-Bunz on 2010-10-15
> **cecilpierce said:**
> You could try System>Administration>Update Manager, I think it asks if you want to upgrade, cant hurt to look !
 
Sorry if I didn't make it clear. They don't want to do upgrade; looks like they did some googling and somehow came away with an impression that a clean install is better than upgrade. Agree with them or not, it doesn't hurt to have an option, does it?
 
Now that I am convinced that there is no clear option to do this in the installer, let me see if I can request this as a feature.
 
Most of the new laptops don't come with Windows Install discs, so, folks are worried about messing up things through manual partitioning.

---

### Post by zika on 2010-10-15
> **Steel-Bunz said:**
> Sorry if I didn't make it clear. They don't want to do upgrade; looks like they did some googling and somehow came away with an impression that a clean install is better than upgrade. Agree with them or not, it doesn't hurt to have an option, does it?
 
Now that I am convinced that there is no clear option to do this in the installer, let me see if I can request this as a feature.
 
Most of the new laptops don't come with Windows Install discs, so, folks are worried about messing up things through manual partitioning.In that case they surely do not want to install NN...?

---

### Post by Steel-Bunz on 2010-10-15
> **zika said:**
> In that case they surely do not want to install NN...?
 
Not sure I understand; you mean install NN right now?
 
No, certainly not. I just want to avoild similar clean install requests by the time 11.04 comes around:).

---

### Post by zika on 2010-10-15
> **Steel-Bunz said:**
> Not sure I understand; you mean install NN right now?
 
No, certainly not. I just want to avoild similar clean install requests by the time 11.04 comes around:).I'm not sure I, really, do follow You...
Avoid what...?

---

### Post by Steel-Bunz on 2010-10-15
> **zika said:**
> I'm not sure I, really, do follow You...
Avoid what...?
 
They want to do a clean install of 10.10 over an existing 10.04 install (dual boot systems with Windows); don't want to upgrade. I did it through manual partitioning.
 
I am hoping for a direct option in the Ubuntu Installer in 11.04 to install it by replacing older Ubuntu installations.

---

### Post by cariboo on 2010-10-15
All laptops I've seen lately come with a utility to backup the restore partition to DVD drive. If your friend is worried, why not get them to run the utility, before doing a new install, this assumes of course that they have a dvd burner. 

When I got my netbook, the first thing I did was run the backup utility, using a 8Gb thumb drive to do the backup, then put it away in a safe place. I really have no intention of ever using it, but you never know.

---

### Post by Longinus00 on 2010-10-15
> **cariboo907 said:**
> All laptops I've seen lately come with a utility to backup the restore partition to DVD drive. If your friend is worried, why not get them to run the utility, before doing a new install, this assumes of course that they have a dvd burner. 

When I got my netbook, the first thing I did was run the backup utility, using a 8Gb thumb drive to do the backup, then put it away in a safe place. I really have no intention of ever using it, but you never know.

He doesn't want to overwrite the restore partition, he just wants to overwrite the ubuntu partition.

A better idea is to just install ubuntu with a separate home/ partition so doing clean installs is super easy.

---

### Post by cariboo on 2010-10-15
I realize he doesn't want to overwrite the restore partition, backing it up is only for safety just in case something goes wrong. No matter how confident you are in your abilities, there are things that can go wrong that you have no control over.

Doing backups can save a lot of time and headaches.

---

### Post by jerrylamos on 2010-10-15
> **cariboo907 said:**
> I realize he doesn't want to overwrite the restore partition, backing it up is only for safety just in case something goes wrong. No matter how confident you are in your abilities, there are things that can go wrong that you have no control over.

Amen!  Even late in Maverick testing, at Beta time, I lost two installs from the "dread update".  I do multiboot on each of my 4 test systems so I didn't lose any data.  

Have fun, Jerry

---

### Post by seeker5528 on 2010-10-15
> **Steel-Bunz said:**
> Now that I am convinced that there is no clear option to do this in the installer, let me see if I can request this as a feature.

Don't know what you are expecting out of the installer. The installer won't give you the option to install a different version of the OS than what it is included on the disk with.  It doesn't seem like an option that will be added to the installer either. 

If you want a clean install, before a development release reaches Alpha, just do a clean install of the current stable release, then update that. 

Not sure how soon they start with the daily builds, that's also an option.

Doing a minimal install, changing the sources.list and updating before installing additional software, then installing the relevant X/K/L/Ubuntu desktop package is also an option.

Later, Seeker

---

### Post by Longinus00 on 2010-10-16
> **cariboo907 said:**
> I realize he doesn't want to overwrite the restore partition, backing it up is only for safety just in case something goes wrong. No matter how confident you are in your abilities, there are things that can go wrong that you have no control over.

Doing backups can save a lot of time and headaches.

All that backup does is backup the restore partition, not the ubuntu partition or the windows partition. That's not useful at all unless you manage to hose the whole disk or want to reclaim some space.

---

### Post by kansasnoob on 2010-10-17
Actually, while I've seen no blueprints indicating we'd go in that direction, it would be kind of cool if that were an option. I multi-boot a lot trying different distros, testing silly things, etc:

```
/dev/sda1: LABEL="**Maverick**" UUID="b7a0df33-53e4-4f0d-856b-0da92ff0d743" TYPE="ext3" 
/dev/sda2: LABEL="**Karmic**" UUID="1332b9d0-cf18-4299-9094-12acbdac91ad" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: LABEL="**Lucid**" UUID="d252929b-949d-432e-a18c-18f9ae770d28" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: LABEL="Backups" UUID="594c3d40-2791-4c0a-8644-d9812545da2d" TYPE="ext3" 
/dev/sda6: LABEL="Pictures" UUID="8a3f6c83-cb52-4caf-96b8-5faf2c830453" TYPE="ext3" 
/dev/sda7: LABEL="Downloads" UUID="05289ee4-d681-4806-b6fd-aefd784f9323" TYPE="ext3" 
/dev/sda8: LABEL="Documents" UUID="571cfad8-68c7-4703-883e-c0baa2a381d4" TYPE="ext3" 
/dev/sda9: UUID="80627269-1ccd-4774-b4ea-a5ef8824ffaa" TYPE="swap" 
/dev/sda10: LABEL="**Isadora**" UUID="f223fe5d-3acb-4d96-950c-62661ad8714b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="**Squeeze**" UUID="0eec2831-7805-437e-a06e-e18ab3268e6a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda12: LABEL="**Pure Gnome**" UUID="f6062e12-09f1-4f19-b6c2-ad58812d6794" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: LABEL="**Peppermint**" UUID="720d719e-e571-4bdd-aac9-718f0ffe2266" TYPE="ext4" 
/dev/sda14: LABEL="**LL to MM final**" UUID="8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079" TYPE="ext4" 
/dev/sda15: LABEL="**LMDE**" UUID="22eefad4-870e-4191-87c9-57f4e756411d" TYPE="ext4" 
/dev/sda16: LABEL="**LL to MM RC**" UUID="7a90aa0c-2377-48e4-97ad-20283c962abc" TYPE="ext4" 
/dev/sda17: LABEL="**Maverick test**" UUID="fad5d0d5-79d1-405c-9e9c-1dd714d39b8b" TYPE="ext4" 

```

Wouldn't it be kind of cool if the Live CD recognized all of that and offered to replace a specific OS?

I no longer use a separate /home for my installs and they all share the same SWAP, but that's something that can be determined by fdisk, parted, blkid, etc.

So I think it's possible that a future version of either ubiquity or the Debian installer (or a new installer) could possibly identify all existing compatible OS's and offer an option to replace any one of those.

I think it's one of the greatest brainstorm ideas I've heard in a long, long time :)

Just because it doesn't currently exist is no reason to "poo-poo" the thought behind it.

---

### Post by Steel-Bunz on 2010-10-18
Thank you kansasnoob. Finally I got someone who agrees with me. :-) I am yet to raise a brainstorm idea; will do so soon.

---

### Post by xebian on 2010-10-18
Can we just please KISS it?  Making it more complex just adds more problems/bugs.  You know your system so why can't you just go to manual and tell the installer which partition(s) to install to?  Instead of sloowing down the installer trying to probe/detect/select systems which may come up to be not what you wanted.  A little homework here and there goes a long way.

---

### Post by Steel-Bunz on 2010-10-18
> **xebian said:**
> Can we just please KISS it? Making it more complex just adds more problems/bugs. You know your system so why can't you just go to manual and tell the installer which partition(s) to install to? Instead of sloowing down the installer trying to probe/detect/select systems which may come up to be not what you wanted. A little homework here and there goes a long way.
 
Xebian,
 
A valid argument. Trouble is more and more non-techy people are into Ubuntu nowadays and many of them bound to have dual boot systems (Windows + Ubuntu). As I have said in my first post, it seems fairly common for somone to replace existing Ubuntu install when a new version comes out. To do that you either use Update Manager or go with manual partitioning.
 
If someone doesn't know want to "Update" and doesn't know what partitioning is, it would be great to have an easy option in the installer. It already recognizes the existing OS installs and offers to install the new system alongside the existing systems. So, it shouldn't be too hard to include the new option.

---

### Post by Longinus00 on 2010-10-18
> **Steel-Bunz said:**
> Xebian,
 
A valid argument. Trouble is more and more non-techy people are into Ubuntu nowadays and many of them bound to have dual boot systems (Windows + Ubuntu). As I have said in my first post, it seems fairly common for somone to replace existing Ubuntu install when a new version comes out. To do that you either use Update Manager or go with manual partitioning.
 
If someone doesn't know want to "Update" and doesn't know what partitioning is, it would be great to have an easy option in the installer. It already recognizes the existing OS installs and offers to install the new system alongside the existing systems. So, it shouldn't be too hard to include the new option.

I assuming that you're recommending installing over a previous installation without formatting the disk? That's a terrible idea because you'll have all sorts of leftover crud on your disk; good luck figuring out what's part of your current install and what isn't. Is this a common practice in windows or something?

An ordinary desktop user should upgrade via upgrade-manager, all the other forms of upgrading are not common. The only sane way to do fresh installs every cycle is to keep /home on its own partition, like I've recommended earlier in the thread.

---

### Post by kansasnoob on 2010-10-18
> **xebian said:**
> **[COLOR="Red"]Can we just please KISS it?[/COLOR]**  Making it more complex just adds more problems/bugs.  You know your system so why can't you just go to manual and tell the installer which partition(s) to install to?  Instead of sloowing down the installer trying to probe/detect/select systems which may come up to be not what you wanted.  A little homework here and there goes a long way.

I hope not :)

Nothing can just stand still. A project will always move either forwards or backwards. Minor tweaks only take a project so far.

I really do think it's a brilliant idea to offer to replace an existing compatible OS. No doubt very complicated for the devs but I think it would be super cool.

If every project followed KISS would we now have jets or would we still be stuck with propellers?

Helicopters or balloons?

Would SABDFL have gone to space?

---

### Post by cariboo on 2010-10-18
I personally don't think it's a very good idea,  but in order to get the devs to even consider it, someone is going to have to come up with a very good reason, along with use cases to prove that it's needed.

---

### Post by LKjell on 2010-10-18
> **Longinus00 said:**
> I assuming that you're recommending installing over a previous installation without formatting the disk? That's a terrible idea because you'll have all sorts of leftover crud on your disk; good luck figuring out what's part of your current install and what isn't. Is this a common practice in windows or something?

An ordinary desktop user should upgrade via upgrade-manager, all the other forms of upgrading are not common. The only sane way to do fresh installs every cycle is to keep /home on its own partition, like I've recommended earlier in the thread.

We can always learn something from Windows. Right now on win7 if you install over the same partition that the old windows is, it will move all the old files to windows.old .

---

### Post by Longinus00 on 2010-10-19
> **LKjell said:**
> We can always learn something from Windows. Right now on win7 if you install over the same partition that the old windows is, it will move all the old files to windows.old .

Does it create a Program Files.old, Users.old, and ProgramData.old? Just because windows does it doesn't make it a good idea. Maybe we should follow windows some more and move the window buttons to the right?

---

### Post by LKjell on 2010-10-19
Everything from the old install will be put to Windows.old . That include programs and user settings.

Windows button displacement is subjective. I have them on the right side since I cannot have them on the left side.

---

### Post by cariboo on 2010-10-19
The windows way works well if you have enough hard drive space, the last upgrade from Vista to Win 7, I did for a customer left only 1Gb of free space on the hard drive, then it was a matter of going through the windows.old directory and picking what to delete to give the owner enough free space to make the system usable. It probably added another hour to the upgrade time.

---

### Post by VinDSL on 2010-10-19
> **LKjell said:**
> Everything from the old install will be put to **Windows.old**Rather ironic renaming, no?  :D

---

### Post by kansasnoob on 2010-10-19
> **cariboo907 said:**
> I personally don't think it's a very good idea,  but in order to get the devs to even consider it, someone is going to have to come up with a very good reason, along with use cases to prove that it's needed.

+1!

It's a brainstorm thing:

[http://brainstorm.ubuntu.com/faq/](http://brainstorm.ubuntu.com/faq/)

My major focus is on getting existing "stuff" fixed, so I focus more on Launchpad, and occasionally Ayatana if I can even remotely tie the problem to the UI.

I think it's a cool idea but that does not address how feasible such an approach would be.

I have too much on my plate already.

---

### Post by cariboo on 2010-10-19
It's probably to late to create anything on Brainstorm for inclusion to UDS-N, as Whiprush usually does a digest of the ideas and distributes them to the devs.

---

### Post by snoopy-2009 on 2011-03-09
about suggesting ubuntu team add in a partitioning tool..im unsure why it seemed you overlooked the post on the 1st page, made by someone else, since still at the bottom of page 1, you said you were "convinced" the installer doesnt have a partitioning tool built-in? im not sure if youve caught on yet or not, since u were mainly focused on the other matter.. but i just wanted to double check..because i KNOW the ubuntu installer (atleast 10.10 did, i dont imagine they removed this feature, its fairly essential imo) DOES have a manual partitioning tool built in, early on in the installer. that you can choose to format specific partitions, or even create an entire new partition table.. just wanted to clarify for you, you wernt thinking of just running off the live cd, were you? i you choose to install to your system, and use the installer, its there.

---

