---
title: "sharing music over network"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by nathang1392 on 2009-11-24
hi,
i have an ubuntu desktop and a windows vista laptop. im constantly downloading different music on each computer. the desktop is wired through a router that routes signal to my laptop. im just wondering if there is anyway i can make a shared folder and keep my music in one common folder that i can update from either computer. if more info is needed just let me know. thanks guys.

---

### Post by Lord_ on 2009-11-24
Samba should do this nicely on a home network. I have used it a few times and its not too difficult to set up.

here is an example guide, I haven't read it right through but it seems to contain the basics. If you get stuck let me know.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by nathang1392 on 2009-11-24
im just having a little trouble. i made my music folders on both computers shared. i installed samba, as i was prompted in ubuntu. at this point i am just trying to figure out how to access each the folder from the other computer...

im not exactly pro with networks so im not assuming any knowledge. if anyone can help it is appreciated.

i read the guide but i got the feeling that it was mostly geared to ubuntu to ubuntu situations, and maybe a little much for my scenario.

---

### Post by bertmanphx on 2009-11-25
hello,
Just a thought, but you could put all of the music on one machine, and install Firefly, and "iTunes" compatible DAAP streaming music server.  I have a spare drive on my server with all of the music on it.  Any of the machines on the network can play music from Firefly.

[I used the tutorial here.]("http://www.zaphu.com/2008/04/29/ubuntu-guide-configure-a-firefly-mt-daapd-streaming-media-server-for-itunes-and-front-row/")

bertmanphx

---

### Post by Lord_ on 2009-11-25
If you do want to go the samba route, you need to create the folder which you would like to share, set your permissions on it. In a home network "chmod 777 {foldername}" should be fine. If you want to be more secure then you can create a user maybe "smbuser" and chown the directory to this user and tighten it.

Then you want to add in the folder to the smb.conf file.

On my CentOS box it is located in /etc/samba/, i expect it will be the same for you. below is an example of adding in a shared folder. Add this at the bottom of the smb.conf file.

[music]
	comment = "Music Share"
	path = /home/username/music
	writeable = yes
;	browseable = yes
	guest ok = yes


A bit further up in the file, you might need to uncomment the lines. the username can just be your normal user, or if you setup a sambe user, use this instead

	guest ok = yes
	guest account = username


once you have done all this, restart the smb service. I think on the newer versions of Ubuntu, you can just use:

service smb restart

good luck.

---

