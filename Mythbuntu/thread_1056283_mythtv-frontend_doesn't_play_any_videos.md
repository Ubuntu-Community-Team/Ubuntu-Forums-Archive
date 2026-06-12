---
title: "mythtv-frontend doesn't play any videos"
date: 2009-01-31
forum: Mythbuntu
---

### Post by lime4x4 on 2009-01-31
Running mythubuntu on one box both frt and backend servers on 8.10
installed mythtv-frontend on a ubuntu 8.10 box.I got the mythtv-frontend box to connect to the mythubuntu box but when i select a video to play the screen goes blank then comes right back to where i selected the video. Any ideas?

---

### Post by My Name on 2009-02-03
make doubly sure you have mplayer installed.
I did a fresh install of ubuntu then mythtv and it took me a while to work out that mplayer was not installed ;)

---

### Post by lime4x4 on 2009-02-03
john@john-desktop:~$ sudo apt-get install mplayer
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mplayer is already the newest version.
mplayer set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@john-desktop:~$

---

### Post by joho500 on 2009-02-04
OK if I understand you right you can see the video in Mythbuntu and select one? So you have a connection with the database on the remote backend but the player can't find the actual video file. Did you set up the right paths? You need to mount the network drive e.g. //backend-IP/videos to a local folder that you have set up in the local frontend. There is a maual somewhere on the forum.

Cheers,
Joost

---

### Post by lime4x4 on 2009-02-04
i tried setting it to //192.168.1.100/john-mythtv/videos now when i go to videos nothing shows up at all

---

### Post by newlinux on 2009-02-04
you should **mount** them in the same location as they are specified on your original mythbuntu box. so if they are located @

/mnt/videos on your original box they should be mounted as

/mnt/videos on all of your remote frontends.

This will greatly simplify things and save you headaches. Once you've done this do a scan with video manager and then you should see them... Or you can set mythvideo to browse the directory without having the need to scan first.

there are a number of tutorials on mounting network NFS (or you can use CIFS/SAMBA or fuse/sshfs if you'd like) shares in Linux and ubuntu. Let us know if you need help...

---

### Post by lime4x4 on 2009-02-04
ok i'm lost here...lol
On my mythyubuntu box which runs a frt-end and back-end mythtv the videos are located in /var/lib/mythtv/videos
on my intrepid box which runs a mythtv frt-end only it was set to
/var/lib/mythtv/videos which didn't work i could select which video but couldn't play it.

---

### Post by newlinux on 2009-02-04
so you need to mount /var/lib/mythtv/videos on your backend to /var/lib/mythtv/videos on your remote frontends. For some reason, mythvideo looks in your local filesystem to find videos - so you have to mount them on remote frontends. It couldn't play them because those videos aren't on your remote frontends.

---

### Post by lime4x4 on 2009-02-04
do i also have to install the mytv back-end on my front-end machine?

---

### Post by newlinux on 2009-02-04
> **lime4x4 said:**
> do i also have to install the mytv back-end on my front-end machine?

nope. You just have to mount the share - similar to a network share in windows...

---

### Post by newlinux on 2009-02-04
> **newlinux said:**
> nope. You just have to mount the share - similar to a network share in windows...

I think this is very non-intuitive - especially given you do not have to do thsi for recordings, but it is because myth uses its own streaming protocol for recordings, and doesn't use any streaming protocol for mythvideo, mythmusic, or mythgallery...

---

### Post by lime4x4 on 2009-02-04
so what would be the best way to mount that share. I assume your talking about mounting /var/lib/mythtv/videos (from the mythubuntu) unto the intrepid computer and having the mythtv frt-end machine pointing to that share/mount?

---

### Post by newlinux on 2009-02-04
There are a lot of guides out there. I personally use SAMBA/CIFS because I have non linux machines on my network. Some use NFS.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I think there may be some mythbuntu specific howtos somewhere in this forum.

---

### Post by lime4x4 on 2009-02-04
after mounting the video folder onto my intrepid install i can now play videos.. Thanks for all the help

---

### Post by lime4x4 on 2009-02-04
by the way i used samba thru the fstab file to auto mount the folder. I can now play videos but i seem to have 2 other issues now
1 i get no listings of my recordings from the mythtv front-end machine
2 now when i exit i get an error about not being able to connect to the master back-end server

---

### Post by newlinux on 2009-02-04
> **lime4x4 said:**
> by the way i used samba thru the fstab file to auto mount the folder. I can now play videos but i seem to have 2 other issues now
1 i get no listings of my recordings from the mythtv front-end machine
2 now when i exit i get an error about not being able to connect to the master back-end server

1 is because of 2 - so they are really the same error, your frontend isn't connecting to your backend. Did it connect before? Have you verified your backend is running? Do your other frontends work?

---

### Post by lime4x4 on 2009-02-04
yes the mythubuntu box front-end works fine but that box also has the back-end server running as well.Just odd that it did connect before.I didn't specify a port i just used the ip addy of the myth box

---

### Post by lime4x4 on 2009-02-04
it seems my front-end only box is trying to connect to the back-end server on 127.0.0.1

2009-02-04 23:20:13.473 New DB connection, total: 2
2009-02-04 23:20:13.474 Connected to database 'mythconverg' at host: 192.168.1.100
2009-02-04 23:20:13.568 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-04 23:20:13.568 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-04 23:20:17.180 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-04 23:20:17.180 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-04 23:20:22.850 TV Error: Failed to get recording show list

---

### Post by lime4x4 on 2009-02-04
I fixed it. I never set the ip addy of the master back-end server on the mythubuntu box. It was set to 127.0.0.1 changed it to the actual address of the box and all is working

---

### Post by newlinux on 2009-02-05
that was going to be my next suggestion - look at your logs and see how it is trying to connect. Glad you have it all figured out...

---

