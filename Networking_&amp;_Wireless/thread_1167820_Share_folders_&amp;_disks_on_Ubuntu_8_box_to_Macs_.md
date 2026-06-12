---
title: "Share folders &amp; disks on Ubuntu 8 box to Macs &amp; PCs?"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by rumplestilts on 2009-05-23
Here's the situation: I am considering the use of an Ubuntu box to act as a "file server" for a network of Macs and PCs. We don't need major security as everything is behind a router. All network users just need to reach the folders and disks connected to the server in order to copy files to their local machines, manipulate the data (using Photoshop, Illustrator, Word, whatever), and then push the file(s) back to the server where (if the users have not renamed their files) the new files will overwrite the old files. It is probable that new files created by the users on their local machines will also be pushed back to the server when completed.

In other words: This is just a file server to which all users will need read/write access.

Do I need to install a "server" version of Ubuntu in order to accomplish this? I've tried sharing a folder and an attached USB disk over the network from my Ubuntu box (not server) and, while the folder and disk did appear on my Mac, I was unable to log in and actually mount the volumes even if I used the admin username and password from the Ubuntu box. (I followed the sharing instructions in the Help file as best I could; do I need to do something about authorizing a "host" in shares-admin?)

Advice welcomed. If there's a link to some documentation, that would also be helpful.

Thanks!

---

### Post by rumplestilts on 2009-05-23
I tried adding a samba user using "sudo smbpasswd -a artist" and then was prompted for a new password and confirmation of the password. I then restarted. Then I used shares-admin to specify which folder I wanted to share and that I unchecked the "read only" box. Then I right-clicked on the shares folder and selected "Sharing options"; I configured that to share, as well (but not to guests). I can "Connect to Server...", provide the proper smb IP address, get the login dialog, have that login accepted, see the share point, click on it and try to mount it, but I get a dialog that says the volume failed to mount.

I saw a video on Youtube where a guy simply enabled sharing for a folder and permitted guest access. That worked for him but it doesn't seem to work for me. Perhaps because he's on v8 and I'm on v9?

Any help gratefully accepted.

---

### Post by rumplestilts on 2009-05-23
*sigh* This is strange.:redface:

I did manage to get it working but everything I pushed to the server volume *sounded* like it arrived (that "plunk" sound OSX provides when a file copy has completed) but the file would immediately disappear from the share and, when looking inside the folder (from the Ubuntu box), nothing was there.

So I unmounted the volume and logged in again. This time it's all working.

I do note that it seems you have to log in using the "Connect to Server..." menu item and use the "smb" address. If I try to log in by clicking on the computer name that appears in the OSX Finder sidebar, mounting will always fail.

I'll do some more tests and see if there's anything consistent I can find about how I managed to get this darn thing working. :confused:

---

### Post by rumplestilts on 2009-05-23
:D Okay! This was an interesting journey through various Linux websites and not one seemed to really have the complete package documented so I'll do it right here.

If you want to share your Ubuntu 9.04 ("Jaunty") folders to a Mac or PC client, -AND- find a way to permit >2GB file sizes, here's how I did it.

1. Assuming you don't mind starting from scratch, re-install Ubuntu and use the "Guided" partitioning method. Alter the main "ext3" filesystem (suggested by the installer) to "ext4". This uses a 48-bit filesystem (rather than 32-bit) and effectively removes the file size limitations. (I say "effectively" as I don't have any disc image larger than 9GB so I'm covered.) I setup the install as simply a "Desktop Ubuntu" workstation and selected nothing else in that initial list (like "Server") as I've had that type of install fail three times (100%). (I'm using the minimal installer CD so maybe this is a problem with the US servers?)

2. Okay; after the reboot, log in. Now launch Accessories>Terminal and type "shares-admin" (no quotes) and hit Enter. You'll be prompted to permit the installation of some necessary components. Do it. When the Shared Folders app comes up, unlock with your password and "Add" a folder to share. I used my Documents folder. Share the folder through SMB (probably already selected). UNCHECK "Read only" (unless that's what you want) to permit read/write access to that folder. Decide what name you'd like that folder to have on the network; this is optional but probably a good idea to use a name other than Documents so users aren't confused - maybe "SharedDocs" or "NetworkDocs" is a better choice. Click the "Share" button and close the Shared Folders app. Quit Terminal.

[I][COLOR=Blue]2.5. In Terminal, type the following command:
sudo smbpasswd -a username
(where you substitute your real username)

It will ask for your existing smb password (which is the same as your normal password). Provide it. Then enter the same password twice more when requested.[/COLOR][/I]

3. No, we're not done. I originally thought I was and what I ended up with was a share that I could log into from my Mac (via smb) and I could drop files into that folder where the "plunk" of a completed copy would sound for each file -but- *the files vanished the moment they appeared in the share!* So the next step is to open a file browser window into your home folder (it was my Documents folder I was sharing, remember?). Then right-click on the Documents folder and select "Sharing Options". Enable the "Share this folder" checkbox and close the dialog.[I][COLOR=Blue]
[/COLOR][/I] 
Head over to the client machine and log in via samba (smb://192.168.1.77 or whatever the IP address is - might want to make this a static IP if you intend to use this as a file server for more than just the current session). The Mac will ask you to log in; do so with the username and password of the Ubuntu user you used when you logged in to the Ubuntu machine. (I know; *security!* but we'll discuss this later.) The Mac will present a dialog with the active shares on the Ubuntu machine so select the share and mount it.

You're done.

If you're using a Windoze client, add the name of the sharepoint to the IP (IIRC), like "\\192.168.1.77\Documents" (assuming that's the share name you used when you set it up in Ubuntu).

Why not _***just***_ change the "Sharing Options" of the desired sharepoint in the file browser? It doesn't work. It mounts (maybe) but you can't write to it *even though you're logged in as the owner of that folder.*

Now, on to the security issue of giving clients on your network the ability to log into the shared folder(s) using the admin user's name and password: So what? As long as the server is in a secure location and you're not sharing any folders that contain information that shouldn't be shared, what's the harm? I may have missed it but I don't see any SSH services turned on. (If it's there please tell me!).

I figure this process (and the end result) would work nicely in an art department where users need access to files and you never know which artist might need access to which file(s). By the way, I'm assuming that the normal *copy-the-file-to-your-desktop-first* rule would hold true here (as it does in all the agencies who are my clients), then the file is modified and saved, then copied back to the server either overwriting the existing file or (more likely) with a versioned name (like myFile-052309.psd).

You might be asking, "Why not give guest access to the files?" To that I would answer, "It doesn't work." I couldn't get guest access to work no matter what I did and, in fact, found many posts about how this is a bug (although in 8.x, not necessarily in 9.x) in various forums.

If you examined the dialogs for sharing folders, you would have seen the checkbox "Allow other people to write in this folder". Frankly, although I was able to get this working with some terminal code to create a new samba user, it created more problems than it solves. Consider a situation where network access is disabled for some reason and you have to unlock the door to the server room in order to sit at the server and copy files to other media. If you logged into the server (via samba) as someone other than the currently logged in user, you will not have read/write capabilities for those files as they are not owned by you. (I'll spare you the PITA I had deleting files with the Terminal using "sudo...")

By the way, I mentioned 2GB+ files are okay now that the filesystem is ext4. I copied, over the network, a 4.26GB DVD disc image without a hiccup. I'm connected via 100mb ethernet through a switch and the write speed was about 9.45MB/second (MB, not Mb) which is about what I've seen using a Mac server with Mac clients.

The next test is to drop this Ubuntu server into a client's office and ask each of the artists to dump a few hundred MB at once into the shared folder. That should be a fair test for speed and robustness. I figure as long as I use good quality equipment with a UPS, I might have a reasonable alternative to a Mac server (as long as I can get backup going in a proper manner, right? That's another story...)

):P

---

### Post by rumplestilts on 2009-05-25
The journey continues. I finally figured out how to partition my HD so /home would be on its own partition which (if I've been properly informed) should let me do a clean install without hosing my user account(s). I'll play with that another time.

Right now, however, I'm using an old Dell Dimension 2400 box that I've set up as an Ubuntu file share. Managed to use ext4 for both the /root and /home partitions so it looks like large file support is happening.

More to post later...

---

### Post by dmizer on 2009-05-25
How about using FTP instead of Samba. There's no file limitation. See the 5th link in my sig for a good howto.

---

### Post by rumplestilts on 2009-05-25
As your instructions say: *OS X natively supports connecting to FTP through the Finder. _The only drawback is that mounted shares are read only._*

Read-only shares don't cut it. If I did FTP, my clients would have to learn another app in order to write the apps back to the server.

The limitation in file size doesn't seem to be a samba issue; rather, it's ext3 that doesn't permit it (without some extra code relating to samba access). Once the share is ext4, however, normal samba access works fine. I just transferred a 4.16GB file without a hiccup.

In another thread, there was some mention of Jaunty + ext4 freezing. I did have this issue with my notebook but, after I set the Power settings to never turn off the screen, the problem seemed to have disappeared (even though the screen -still- goes dark after a period of time).

I set my Dell desktop's Power management for the screen to "never" and, here again, the screen does go dark eventually but no freezing.

I have both "/" and "/home" partitions as ext4. I did the separate partition as advised by another in order to preserve my /home data should it ever be necessary to do a "clean" install. OSX knows how to do this without a separate partition; not sure why Ubuntu can't do it...but that's another thread.

I do thank you for your reply. As I indicated, all suggestions are welcomed.

---

### Post by dmizer on 2009-05-25
Sorry about the finder issue. Though most FTP clients are fairly easy to use, I understand your desire to avoid another piece of software.

The file size limitation is indeed a Samba issue, or rather a gvfs issue. Using ext4 only fixes the issue because it supports 64bit file handling.

If you mount with CIFS as indicated in the second link in my signature, you can avoid the 2GB file size limit without having to reformat as ext4.

---

### Post by rumplestilts on 2009-05-26
I checked out your "#2" link. I think you'll agree your solution involves quite a bit more complexity than mine; My instructions (which are quite verbose) take up only one screen.

I get the feeling there's a hesitancy among Ubuntu users to move to ext4 due to some deficiency - perhaps *immaturity* may be a better word? As a long-time Mac user, the move to large file support happened about eight or nine years ago with HFS+ so we (well, I) expected it to be here when I dropped in on Ubuntu a few weeks ago.

I keep forgetting that this is a *community-supported* operating system in the sense that releases that never would see the light of day (if this were Apple's product) must, of necessity, be out there in order to get enough testing done. That's why it's *free software, *right? Snow Leopard reached the beta stage (IIRC) before Apple released it to the developer community; I guess Jaunty Jackalope is now in that stage, right? So we're having to clean up some of the mess. :)

I've got to admit that Ubuntu (with Gnome) feels very much like OSX for geeks (and I mean that as a compliment). Once ext4 has proven itself robust (and there are tools to repair/recover?), I think I might have a good alternative to a Mac file server.

---

### Post by dmizer on 2009-05-26
> **rumplestilts said:**
> I checked out your "#2" link. I think you'll agree your solution involves quite a bit more complexity than mine; My instructions (which are quite verbose) take up only one screen.

Yes well, I also give two options for mounting and each with three different solutions depending on server configuration. Also, some of the prework is not essential. While it does appear to be more complex, it's really only:
1) install smbfs
2) create mountpoint
3) make credentials file (if necessary)
4) edit fstab (if using the permanent mount option)
5) insert mount line

Complexity comes from having to know the exact mountpoint from the server, and knowing how to manipulate the mount command according to your environment. Having supported that thread for several years now, I do recognize that subject alone is complex enough to deter most beginners.

> **rumplestilts said:**
> I get the feeling there's a hesitancy among Ubuntu users to move to ext4 due to some deficiency - perhaps immaturity may be a better word?
Yes, ext4 support is fairly fresh, and does have its share of [problems](http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892) and [bugs](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781). However, there's really only a small percentage of users who will experience any advantage with ext4. Specifically, users like yourself who deal with large file sizes.

You know that [MAC supports NFS](http://mactechnotes.blogspot.com/2005/08/mac-os-x-as-nfs-client_31.html)? There's also an NFS tutorial in my sig. It's significantly easier than Samba. You can also add NFS support for PCs: [http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx](http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx)

---

### Post by rumplestilts on 2009-05-27
Again, I see much complexity in the 2 (or 3, if you include having PCs as clients) procedures necessary to get NFS running on both server and client(s). Samba is already there on the clients and the server installation requires only four steps to share the folders out to the network.

I'm sure there's something not very kosher about using the admin account and password for client login to the shared folders but I'll address that down the road.

Thanks

---

### Post by rumplestilts on 2009-05-28
Wow! I think I just found my ultimate solution: It turns out that I can share an HFS+ formatted hard drive connected via USB (or, presumably, FireWire) to the Ubuntu box over the network to a Mac client that connects via SMB. [COLOR=Magenta](Not an original discovery; I was searching Google for something else and it came up.)[/COLOR] I'm running some tests with 4GB files to see if anything crashes or freezes.

If it all works, then dmizer's advice to stay clear of ext4 until the freezing bug has been eradicated is easy to follow as I can install Ubuntu on the internal HD with ext3 partitions and connect HDs (already initialized as HFS+ on a Mac) via FireWire, and share these drives out to the LAN. (Thank you, dmizer.)

The beauty of this is that, if necessary, I can unmount any of the shared drives and bring them over to a Mac where the requisite disk- and data recovery tools with which I am familiar are available.

This actually simplifies things (although my procedure for sharing and mounting now requires an additional command in the Terminal:

$ chown -R username:username /media/drivelabel

(where "username" is my login username and "drivelabel" is the actual name of the volume)

This needs to be done right after the drive is connected and mounted but before the "shares-admin" step. It changes the ownership of the newly mounted hard drive from "root" to me (so I may setup the sharing).

As I write this, I'm copying over a 5.29GB file (just for grins) to the Ubunto box via 100mb Ethernet. If it copies properly (and I have to believe it will given that the volume is HFS+ and can handle large files with ease), then I think I'll be setting up some Ubuntu file servers in town. :D

I'll still play around to see if guest access can be enabled just for these external drives. More to do tomorrow.

---

### Post by dmizer on 2009-05-28
To avoid the chown, you could add an explict mount command in /etc/fstab for the drive. To work something up for you though, I'd need to see the output of (with the drive connected):
```
sudo blkid
```
and
```
df -Th
```

---

### Post by rumplestilts on 2009-05-28
It looks like I only have to do the 'chown' command once for each drive just so it's set for R/W for both me and the clients logging in over the LAN (who are logging in as me).

As I understand it, when a drive is first initialized by Gparted, it's owned by 'root' so I have to 'chown' it to make it accessible by me.

Is there another username I could use that would make the drive R/W accessible by everyone (guests)?

Thanks!

PS - I'll post the output of those two commands later this evening. I'm in between consultations at the moment.

---

