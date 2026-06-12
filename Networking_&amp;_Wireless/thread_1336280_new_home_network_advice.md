---
title: "new home network advice"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by alladnsane on 2009-11-24
I know a lot of this has already been covered but I was hoping I could get some comprehensive help from start to finish. I am relative good with pc's, ubuntu and winxp but have never done any networking.  I am now looking to set up a home network with to accomplish the following:

1) dedicated file server, able to be remotely controlled from main family pc and to serve media content (video, music, photos) to several other computers (and possibly an xbox 360 in the near future) and tv

2) dedicated torrent machine - able to be remotely controlled from main pc and save completed downloads on the file server.

3) main family pc (dual boot ubuntu / winxp) able to watch movies, listen to music , access files stored on file server for all users. As well as selectively (only me) control file server and torrent box.

4) laptop running winxp access and play media files on server

5) play movies on tv (tv has vga input) from server but would need to be controlled from main pc (which is also in living room)(and if santa is good to me then stream the movies to the tv thru xbox360)(and possibly serve media to original xbox running xbmc to second tv in near future)

6) internet access to main pc and laptop (and torrent box :)

-The PC i have for the server is celeron D 1.6, 2gb ram, built in intel 950 video and onboard 6 channel s/pdif output audio, lots of hard drive space. 
-the pc for torrentbox is an old pIII currently running ubuntu 7.10
-both of these are in basement directly below tv (maybe 10ft)
-everything will be connected wired thru linksys router for the moment and possibly wireless in future.
-don't have a lot of money to buy anything new 
-presently all video media is on 2 1TB sata drives ext3 format. so if winxp laptop cant access them i can live with that.  Music is all on 250 gb ntfs drive. 
 
I need to be walked through everything right from the ground up ie. 
- what os and software to put on the file server. (was thinking mythbuntu???)
- what to run on torrent box
- best way to connect audio and video to tv 
- everything else 

I know I am asking a lot but am in desparate need.  don't have cable or anything so right now am watching all movies/ tv on main pc which means i cant do anything on it most of the time and I have a perfectly good lcd tv sitting unused.

Thanks

---

### Post by Lord_ on 2009-11-24
Setting up the file server shouldn't be too difficult. I would keep it on Ubuntu and set up sharing with Samba. Assuming you are giving all the machines static IP you can setup some crude (but probably effective) access control to these shares based on the IPs.

As for the content streaming I think setting up Samba shares will allow the content to be shared on the network without having to worry that it is ultimately saved on an ext2 partition. You should be able to open a video on the Fileserver by opening it via its smb share. If you need to stream from the fileserver out I think VLC will do this nicely, although its not something I have played with a great deal.

---

### Post by alladnsane on 2009-11-24
The pc for the file server/media server has no os on it at all right now. So would you recommend ubuntu server or regular ubuntu??

how would i set up static ips?

That would be good news if the laptop could access files on ext3 partition through the network!!

---

### Post by sabre2th on 2009-11-24
I currently have an Ubuntu server, running Ubuntu Server (Jaunty) :). My files are all in an ext2 or ext3 (can't remember) partition, shared with Samba. On other computers, I just mount the samba share in Ubuntu/Windows/wherever and access the files directly with whatever program I want.  It's nice and straightforward

I use the same username on all of my computers, making setup changes easy.  I ssh into the server using the terminal (or Putty in Windows).  I don't currently have other users, but if/when I do, they simply don't have user accounts on my server or Myth box, so they can't make changes.

I've contemplated adding torrent functionality to my server and, depending on how many people you're serving, I'm not sure you need a dedicated box for it.

As far as Ubuntu Server vs. Desktop.  Server will handle server-type activities a bit better, but there won't be much of a difference for relatively light loads.  From my perspective, it really boils down to how comfortable you are configuring things from the command line.

Mythbuntu is basically DVR software, so I wouldn't bother with it unless you want a DVR.  If that is what you want, keep in mind that tuning/recording HD content with Linux is hairy at best right now.  It generally requires the provider's cable box and there's no good way to output to Myth.  Firewire is supposed to be the way, but it's apparently not working for a lot of major providers right now.  (Since you don't have cable now, that might not be an issue, but just pointing it out for the future)

Edit: I just reread your post and I see that you want to serve media to your TV.  MythTV is a relatively painless way to do this.  It allows easy setup of a remote and reasonably automatic access to your shared files.  If you want to watch your Myth-recorded media on other computers, it is possible to install MythTV in a regular Ubuntu desktop installation, but there isn't a great solution for Windows right now (just a VM install of Mythbuntu, etc).

Wired vs. wireless... I would keep everything wired if it's not too much hassle.  If wiring is hard, keep your server/myth/torrent boxes wired at the very least and let the users be wireless.  It makes things run a lot more smoothly.

Sorry, I know this post is not terribly organized but I figure it's better than nothing.  (I'm at work and typing it in between other tasks as a distraction).  Feel free to ask lots of questions.  I've dealt with most of this stuff fairly recently, so I should be able to get you going in the right direction.

Edit: Static IPs are straightforward to set up in network manager if you're at all familiar with networking (or people here can walk you through it).  It's a touch harder from the command line (ie. for Ubuntu Server), but still not difficult (just edit a file or two, though I don't recall the names of them at this moment).

---

### Post by Iowan on 2009-11-24
> **alladnsane said:**
> The pc for the file server/media server has no os on it at all right now. So would you recommend ubuntu server or regular ubuntu?The server comes without desktop. Are you comfortable using CLI for configuration? 
An alternative to static addresses is a static lease - this would require setting up the DHCP server (router?) to issue "fixed address" based on MAC address.

---

### Post by alladnsane on 2009-11-24
> **sabre2th said:**
>   I don't currently have other users, but if/when I do, they simply don't have user accounts on my server or Myth box, so they can't make changes.
does this mean only you would have access to the files as well???

> I've contemplated adding torrent functionality to my server and, depending on how many people you're serving, I'm not sure you need a dedicated box for it.
i want the dedicated torrentbox so it is the only one with a constantly open port!!


>  want to serve media to your TV.  MythTV is a relatively painless way to do this.  It allows easy setup of a remote and reasonably automatic access to your shared files.  If you want to watch your Myth-recorded media on other computers, it is possible to install MythTV in a regular Ubuntu desktop installation, but there isn't a great solution for Windows right now (just a VM install of Mythbuntu, etc).
I wouldn't care about serving to the windows machine as long as I could still access files on the server manually. Can the same file server run mythtv for serving to the TV? or would it need to be separate??

> Sorry, I know this post is not terribly organized but I figure it's better than nothing. 
I really appreciate any and all help/advice.  I really am networking illiterate. 

 > Static IPs are straightforward to set up in network manager if you're at all familiar with networking 
I am not a networking guy at all, but I am pretty sure I just got static IP set-up on my main pc.


> **Iowan said:**
> The server comes without desktop. Are you comfortable using CLI for configuration? 
An alternative to static addresses is a static lease - this would require setting up the DHCP server (router?) to issue "fixed address" based on MAC address.
I am comfortable with CLI, I just am not sure what commands to use :)

Is it possible to add a minimal gui to the server if I needed?? and is the performance that much better from the server than the desktop??  Also would I be better off with 64 or 32 bit server if I went that way??

---

### Post by sabre2th on 2009-11-25
> **alladnsane said:**
> does this mean only you would have access to the files as well???
It all depends on how you set it up.  You can set up Samba to allow anyone to access the files without a password.  You can also have fine-grained per-user control if you like.

> i want the dedicated torrentbox so it is the only one with a constantly open port!!I don't think this is anything you have to worry about, but of course it's your choice.

> I wouldn't care about serving to the windows machine as long as I could still access files on the server manually. Can the same file server run mythtv for serving to the TV? or would it need to be separate??You can definitely have Myth and your fileserver on the same box.  Myth does require a GUI to setup, which does make setting up a fileserver easier.  The only issue with that would be if you wanted a headless, GUI-less server, but it doesn't sound like you're worried about that.

 > I am not a networking guy at all, but I am pretty sure I just got static IP set-up on my main pc.Glad to hear it  :)

> I am comfortable with CLI, I just am not sure what commands to use :)There are lots of tutorials and walkthroughs floating around, but I've found there isn't a single one that gets you 100% of the way there.  Setting up a server will require you to pull bits and pieces from various places.  It took me a couple of tries to get it exactly where I wanted it (of course, I haven't had to do anything but install security updates since then...)

> Is it possible to add a minimal gui to the server if I needed?? and is the performance that much better from the server than the desktop??  Also would I be better off with 64 or 32 bit server if I went that way??> I really appreciate any and all help/advice.  I really am networking illiterate. As far as 32/64... I go with 64 bit whenever the hardware supports it.  Functionally, there really isn't any difference between the two these days.  For home use, there really shouldn't be a noticeable difference between server and desktop versions of Ubuntu.

Other people may think differently but it sounds to me like your best bet is to set up Mythbuntu on a Myth/server box.  It provides a nice GUI for accessing media on the TV and uses the Xfce window manager, which is reasonably lightweight.  It will make your server setup easier, as well.

Mythbuntu  can sometimes be a bit finicky to set up, but works pretty well in my experience.  I would recommend a cheapish (~$25-30) Windows Media Center remote (make sure it comes with a USB sensor) to use with the TV.  I have an Anyware remote from Newegg that does the job nicely, though it can't turn the TV on and off.  If you install a supported TV tuner card, you can also get the DVR functionality I mentioned.

---

