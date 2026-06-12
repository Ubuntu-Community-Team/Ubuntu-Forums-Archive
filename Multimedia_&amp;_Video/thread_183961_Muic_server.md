---
title: "Muic server"
date: 2006-05-29
forum: Multimedia &amp; Video
---

### Post by J.J Morrison on 2006-05-29
I have downloaded  Banshee Media Player to play my mp3 files cause the other media players said they needed a plugin for mp3 files and I didn't know where to find those plugins. But anyway all my music is on my music server but it won't let me set that folder as my music library because it isn't a local file. Anybody know anyway i can get around this or if any other players let you use networked folders as your music library.

Thanks for all your Help

---

### Post by Randomskk on 2006-05-29
The best thing to do would be mounting the network drive as a local drive.
What type is it? FTP? NFS? Windows Share?

---

### Post by J.J Morrison on 2006-05-29
Windows Share How do I mount it as a local drive

---

### Post by syntek on 2006-05-29
im gonna assume youve already got samba working and can browse the windows share from your dapper box, if not, getting samba working is your first step.

once you can mount and browse the smb share, simply create a directory like /music or /media/music and add that to your /etc/fstab

then just point banshee to that directory. let us know if you need more detailed instructions on any of those steps, and where you're getting hung up at.

---

### Post by J.J Morrison on 2006-05-30
[QUOTE=syntek]once you can mount and browse the smb share, simply create a directory like /music or /media/music and add that to your /etc/fstab[/QUOTE]



Ok I made the music folder now what do i add to /etc/fstab

---

### Post by syntek on 2006-05-30
something like this will do```
//servername/sharename /media/music smbfs username=windowsuserename,password=windowspassword 0 0
```
obviously you'll have to change things to reflect your setup..

---

### Post by J.J Morrison on 2006-05-30
Ok you just lost me.

What goes in the place of server name, share name, windowshare name,username, windowspassword, password?

---

### Post by denkedran on 2006-05-30
banshee music player has daap capabilities.
if your music-server is a windows-box you could install itunes on it and share it over daap to the network. your windowsbox will automatically be found by banshee and will be accessable through an icon in the sidepane
By the way the mp3-plugin you search for is in gstreamer0.10-plugins-ugly. a simple ```
sudo apt-get install gstreamer0.10-plugins-ugly
```
or an install via synaptic will solve your lack of mp3 support
look here for more infos about restricted multimedia formats [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

rhythmbox ( the standard music player for ubuntu is also daap-capable )

**edit:** for daap-support of banshee it is necessary to install bansee-daap```
sudo apt-get install banshee-daap
```

---

### Post by syntek on 2006-05-30
[QUOTE=J.J Morrison]Ok you just lost me.

What goes in the place of server name, share name, windowshare name,username, windowspassword, password?[/QUOTE]
the server name is the name of your windows computer (right-click my computer and go to computer name) or its IP address. the share name is what you called the folder in the sharing properties. the username and password are the username and password for your windows machine.

the problem with using the IP address of the windows box in your fstab is that if youre using DHCP, then the address might change over time. you could always go into network settings and set a static IP address of the windows box, but its unnecessary if you can just use it's name.

---

### Post by J.J Morrison on 2006-05-30
Thanks for all of your help I downloaded the daap thingy for banshee and it worked!!!!

---

### Post by denkedran on 2006-05-30
I'm glad i could help you. Enjoy your music. 8)

---

