---
title: "Permanent mount of a Samba Share (Ubuntu 10.10)"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by Nakaleen on 2010-10-10
First off... do not utter the words '***Google it***'

I have sent the last 5 **hours** *(it is now 6am)* and I am in no mood for lazy know-it-all's

Heheheh now THAT is out of the way I have a problem.

I have returned begging and crawling back to Ubuntu (I waited a day for 10.10 to be released) and I have again stumbled across why I go back to Micro$oft's Windows.

All I want to do it have a permanent share to my nas, which is on my Netgear DGND3300.

I can reach it by Place -> Network -> Windows Network -> NAKALEEN -> NAS -> USB_Storage

but for the life of me I can't make it permanent. I need it as all my Movies/TV/eBooks are on this.

I have followed every and I mean ***EVERY*** option I have found on Google with no luck. From the fstab/mount option to the gvfs option (as you can guess both failed)

The reason it is ****$&^%$^&%$*** me off it that Windows can do it with a couple of mouse presses (Map Network drive). Making Ubuntu a joke in this area.

*(I am NOT a Ubuntu/linux hater, I LOVE it. But it is simple things like this that is weighing it down*)

---

### Post by Morbius1 on 2010-10-10
> All I want to do it have a permanent share to my nas, which is on my Netgear DGND3300.

I can reach it by Place -> Network -> Windows Network -> NAKALEEN -> NAS -> USB_Storage

but for the life of me I can't make it permanent. I need it as all my Movies/TV/eBooks are on this.What do yo mean by permanent:

If you use Places > Network it has a mount point at:
> /home/your-user-name/.gvfsIs it not there?

You can Bookmark it once you find it using Bookmarks > Add bookmark

Or by permanent do you mean automount at boot? In the past I've used fstab and then gvfs-mount scripts but now I use a GUI to gvfs-mount called gigolo:
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by jlipoth on 2010-10-13
It is very unfortunate that something that had worked for so long by adding one simple line in fstab, is now seemingly abandoned.  I would have thought there would have been a GUI added instead.... ...anyways.....  I don't completely understand it, but mapping through fstab is not the same as mounting it.  For example, Rhythmbox behaves very well when it thinks the media library is local.  does gigolo only automount, or does it also map the share to a local folder?

BTW - I am having the same problem

---

### Post by Morbius1 on 2010-10-13
> **jlipoth said:**
> does gigolo only automount, or does it also map the share to a local folder?

I don't know about "mapping" the share to a local folder but just as the classic fstab method mounts a remote share to a local folder so does gigolo.

Gigolo is a GUI front end to gvfs-mount ( with some valuable added scripts ). As such it works the same way as Nautilus does when you "browse" to the remote share.

Let's use the following example:

I have a remote share located at Morbius2/Backup. When I browse to that share in Nautilus what is actually happening is the following command is being executed:
```
gvfs-mount smb://Morbius2/Backup
```If I were to issue the above command in a terminal 2 things would happen:

(1) A remote mount icon will be placed on my desktop

(2) A mountpoint will be created at the following location:
> /home/morbius1/.gvfs/Backup on Morbius2If that's what you are calling a "map" then it be mapped.

Gigolo can do the browsing and the mounting. It can also be used to automatically mount the remote share at login. Best of all it can poll the local network and mount the remote share when the remote share becomes available. Handy is the remote box isn't powered on yet.

---

### Post by jlipoth on 2010-10-13
I'm not sure if I am using mapping in it's true context.  I mean that the old fstab text where you mount the share to a folder, so that most programs think the share is local.  This is similar to the "Map Network Drive" feature in Windows.  I've never seen or tried the gvfs method, but it sounds like it might work for me - I'll try it later today.

---

### Post by Morbius1 on 2010-10-13
>  I mean that the old fstab text where you mount the share to a folder, so that most programs think the share is local.
That method still works.

There is a bug introduced in 10.04 where fstab is executed before the network is up so all the fstab entries are basically ignored,  but there's a workaround for that.

You can see if that's the problem by just issuing a "sudo mount -a" after login to see if the remote share is then mounted.

---

### Post by jaeger2000 on 2010-11-02
NOTE: For remote directory.  When using the system name.  I could not get the mount to work when editing the /etc/fstab unless I put the appropriate details in /etc/hosts.
ie.

sudo gedit /etc/hosts


my_network_share     192.168.2.100



kind regards,
Ian Gregory, Sydney.
fyi: Ubuntu 10.10.

---

### Post by vmajor on 2010-12-02
Besides the erratic behaviour with NAS shares (this time to PCI MZK-NAS02SG) where the shares become inaccessible or "lazy" after a short period of time. When clicked an error pops up saying something like "No application that can open "network://" file type".

...I also have a truly major problem.

I cannot attach any file on the NAS shares to emails that I am composing in Gmail.

When I drag and drop them from File Manager (Nautilus) I get "This file is 0 bytes, so it will not be attached." in Chrome and a similar message in Firefox. 

Additionally, the Nautilus file requester/browser that is launched when I click on "Choose file" in Gmail does not see the mounted SMB shares, or bookmarks so there is no way to manually navigate to a shared file in order to attach it.

This is severely limiting the usefulness of my Ubuntu 10.10 installation so I think I will again be forced to go back to Windows where there are no problems with accessing files on the NAS. Ironically the NAS is running a Samba Server on a linux distro of some sort...

Any specific help is highly welcome.

V.

---

### Post by Morbius1 on 2010-12-02
> Additionally, the Nautilus file requester/browser that is launched when I  click on "Choose file" in Gmail does not see the mounted SMB shares, or  bookmarks so there is no way to manually navigate to a shared file in  order to attach it.
Right click an open space in the "Choose File" box and select "Show Hidden Files".

Then migrate to /home/your-user-name/.gvfs

---

### Post by vmajor on 2010-12-02
Ha! That works...but, is there any way to make Ubuntu 10.10 behave "normally" ie. to allow drag and drop from files showing in Nautilus in shared directories mapped from the NAS, or selecting files from the file requester without having to hunt for .gvfs first?

---

