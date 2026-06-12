---
title: "mythtv networked drive help"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by JMuffin on 2007-06-03
I have mythtv installed on a spare computer in my living room, but I cannot for the life of me figure out how to access the video files on my desktop with it. I installed mythvideo, and in the general settings tab there is a section labeled "Directory that holds videos." What do I have to enter in that space for the mythbox to look on my desktops hard drive for video files? Or is there something else I have to do?

---

### Post by rhpot1991 on 2007-06-04
Need some more information before I can help out here.  Are both of the boxes running linux and mythtv, and where the files recorded in mythtv?

---

### Post by fenian on 2007-06-04
You should have set up the myth frontend as described [here.]("https://help.ubuntu.com/community/MythTV_Feisty_Frontend?highlight=%28mythtv%29")If not I would remove mythtv and reinstall following that guide.After you have done that (or if that's the way you set it up) you should be able to watch live tv using the tuner on the backend as well as watch any material that was recorded by mythtv.Mythtv does not share the directories for the plugins (Mythvideo,Mythmusic,Mythgallery,etc...) the same way , these need to be accessed locally.I set up those directories with NFS sharing on the backend , to install NFS server on the backend machine do this...
> 
sudo apt-get install nfs-kernel-server nfs-common portmap
When configuring portmap do =not= bind loopback. If you do you can either edit /etc/default/portmap by hand or run:
> sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart


Then go to the folder you want to share, right click and choose share folders ,in the windo that pops up choose share through unix networks (NFS),another window will open click the add button and enter this...
> 
192.168.1.1/24

Click ok.This allows all the computers connected to your router to access those files.

Next on the frontend machine install the NFS client packages like this...
> 
sudo apt-get install portmap nfs-common


Next create the mount point for the shared folder,in this case we will mount it to /vids, do this...
> 
cd /
sudo mkdir vids

Now mount the share manually,you will need the ip address of the backend  on my backend the address is 192.168.1.100 yours may well be different(Run the command ifconfig in a terminal on the backend if you dont know what the address is).To mount the share do this...

> sudo mount ip.adress.of.backend:/path.to.video.folder /vids

this should have mounted the video folder from your backend int the vids folder in the filesystem directory of your frontend.If it did you can then point mythvideo to /vids from the general settings screen in mythfrontend.

Now you probably want to automatically mount that every time you boot the frontend to do this adityour fstab like this

> gksudo gedit /etc/fstab

in the text fiile add this line (change the settings as needed)

> ip.adress.of.backend:/path.to.video.folder /vids     * nfs rsize=8192,wsize=8192,timeo=14,intr

Your video folder from the backend should mout on he frontend when you reboot.

---

