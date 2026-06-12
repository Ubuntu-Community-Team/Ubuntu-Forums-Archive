---
title: "\\:D/ Love Mythtv/Edgy; still serious outstanding issues in install of both"
date: 2006-11-09
forum: Multimedia &amp; Video
---

### Post by wgaprotest on 2006-11-09
This is the furthest I've gotten in 3 mths of struggle with various Linux distros for my HTPC. I credit Edgy's ability to download and compile the ivtv drivers through the repos for most of my success, as well as this howto: [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop). That howto still needs some work, and I'd do it myself if I knew how to edit wiki pages and was a bit more experienced with Linux itself. One thing at a time. :) Certainly I've tried many tv apps, but nothing has worked so far, and most of them say right in their doucmentaiton that they support bttv drivers, and thus do not support the ivtv drivers needed by my card. The list of ones I've tried include xawtv, kdetv, tvtime, motv, vdr...

The errors when I start the mythbackend are below, although I'm not worried about the lirc issue (for now) or the Session Management error, as according to my searches this last bit is normal. I certainly have to start the backend with the command "mythbackend" or "mythbackend -d" (I have put in a line for it in my /etc/rc.local file, but it's commented out for the moment until I can get other issues resolved.)

Points to keep in mind if any of your are kind enough to take the time and help me diagnose and.or fix any of these issues:

1. I need to be able to watch live tv, at least on channel 3, first. I know my Hauppauge wintv250 card and ivtvdrivers work because i do have great audio and live tv video if I type in a terminal:
[INDENT]ivtv-tune -c 3
mplayer /dev/video0[/INDENT]
I can also watch avi movies and listen to my music on other local drives on this pc with Mythtv. All of Myth is, so far, on this one pc.

2. The very last error that I get when I start the mythbackend daemon is very problematic and only appeared today:
[INDENT]2006-11-09 00:35:03.406 Enabled verbose msgs:  important general
/media/MythVid/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/media/MythVid/recordings' exists and that both
the directory and that file are writeable by this user.[/INDENT]
I didn't have nfs on my system when it  appeared (I do now in the hope that I'll be able to unlock it). I would have rather use the user management module in System settings to add Mythtv as a user of that partition, but I can't because that module has an error I can't seem to fix with any of the common methods (dpkg -f <package> reinstall, & others i've tried: "The module User Management can not be loaded...Dignostics...<neither of 2 suggestions apply; I had this identical problem with a different system settings module when the clean installation was less than 24 hours old; I fixed that one by fixing a bad edit I'd made to the issue file). 

I know very well that the error-specified directory exists; I've chowned it, I've shared it via NFS and Samba, edited fstab entry for the parition...nothing works. I consider this one to be the most serious problem because, before today, I could at least get black static from tying to watch tv through myth; the backend and frontend were connecting with each other, but now I can't get the backend to wake up at all. I know I've tried running mythtv-setup again; It doesn't help, getting rid of the error message or starting mythbackend.


3. MySql Server, Appache2, the download of the DataDirect EPG, and phpmyadmin are also working well, as I did fix a few smaller issues with them already.

4. The TVRec error about not being able to initialize the channels. I haven't even begun to focus on that one...it's also a new error,..I think.

Here are the terminal results when I try to start the mythbackend, and thanks again in advance for any help that anyone can give me:

---------------------------------------------------------------------
<reg username>@htpc:/media/Winmedia/Films$ mythbackend -d
<reg username>@htpc:/media/Winmedia/Films$ 2006-11-09 02:14:43.884 Using runtime prefix = /usr
2006-11-09 02:14:43.936 New DB connection, total: 1
2006-11-09 02:14:43.945 Connected to database 'mythconverg' at host: localhost
2006-11-09 02:14:43.951 Current Schema Version: 1160
Starting up as the master server.
2006-11-09 02:14:43.963 New DB connection, total: 2
2006-11-09 02:14:43.964 Connected to database 'mythconverg' at host: localhost
2006-11-09 02:14:43.966 EITHelper: localtime offset -5:00:00
2006-11-09 02:14:43.971 New DB connection, total: 3
2006-11-09 02:14:43.972 Connected to database 'mythconverg' at host: localhost
sh: change-channel-lirc.pl: Permission denied
2006-11-09 02:14:45.561 ret_pid(6774) child(6774) status(0x7e00)
2006-11-09 02:14:45.561 ChannelBase: external tuning program exited with error 126
sh: change-channel-lirc.pl: Permission denied
2006-11-09 02:14:46.573 ret_pid(6776) child(6776) status(0x7e00)
2006-11-09 02:14:46.573 ChannelBase: external tuning program exited with error 126
2006-11-09 02:14:46.573 TVRec(1) Error: Setting start channel '3' failed,
                        and backup '1' failed as well.
2006-11-09 02:14:46.583 New DB scheduler connection
2006-11-09 02:14:46.583 Connected to database 'mythconverg' at host: localhost
2006-11-09 02:14:46.586 Main::Starting HttpServer
2006-11-09 02:14:46.592 Main::Registering HttpStatus Extension
2006-11-09 02:14:46.601 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2006-11-09 02:14:46.601 Enabled verbose msgs:  important general
/media/MythVid/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/media/MythVid/recordings' exists and that both
the directory and that file are writeable by this user.
-----------------------------------------------------------------

Cheers!

Dennister

P.S. I used the ubuntu-server clean-install method, then installed kubuntu-desktop. My system is: amd x2 3800+; Asus SLI deluxe mobo, 2G ram, nvidia-chip 7800GT video card, 2x300G hdd's (1 sata, 1 ide where k/ubuntu is installed), the hauppauge, cable modem/router, SA Explorer cable setop box, flat panel lcd monitor, sundry other stuff not too important to this post.

---

### Post by wgaprotest on 2006-11-09
chmoding the directory in cli to my username got the mythbackend to start without the error message in #2 in regards to mythtv (user) not having access to the recordings directory.

this time i got directions in cli to change my decoders, and once i do that, perhaps i'll get the same kind of picture with mythtv that i get using the ivtv-tune/mplayer commands

a million thank-yous to Hawkwind in the #kubuntu irc channel, and all the other wonderful people there! it's a wonderful channel

---

### Post by superm1 on 2006-11-09
Normally,

the "mythtv" user will have ownership and write rights to your recordings directory.  If you are starting from the init script (/etc/init.d/mythtv-backend start), then make sure that "mythtv" owns it and can write to it.  If you are deciding to start from the command line as a regular user (IMHO, not recommended since you lose process tracking and restarting the process cleanly), then make sure that whatever user you launch myth as controls the directory.

I'd gladly accept some help with the wiki page, I've written most of it.  I've had several eyes looking at it and helping catch typos and grammatical errors, but another set of eyes definitely helps.  Right now you can't see it unless you look at raw pages, but I'm changing it's internal structure to be modular with lots of include statements.  This will allow me to take it and use a lot of it for dapper pages and feisty pages.  PM me with what your interested in helping document, update or what not.

---

