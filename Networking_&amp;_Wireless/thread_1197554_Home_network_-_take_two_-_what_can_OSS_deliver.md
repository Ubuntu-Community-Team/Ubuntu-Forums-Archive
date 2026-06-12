---
title: "Home network - take two - what can OSS deliver?"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by deepthink on 2009-06-26
Hello

I'm moving to a new house and that gives me a good reason to take a second look at my home network.

This is what I'd expect from my setup:
[LIST]
[*]A mail server with a good webmail client
[*]A shared home calendar that I can sync with my cellphone (N95) and evolution.
[*]An address book that is kept synchronized between the webmail, evolution and the cellphone.
[*]A picture gallery
[*]Shared file storage
[*]Personal file storage
[*]Automatic backup
[*]Printer sharing
[/LIST]

[FONT="Arial Black"]Shared file storage[/FONT]
[LIST][*]Contains movies, music and pictures
[*]Be able to be streamed to a PS3 and DNLA capable TV
[*]Have secure remote access to the files over the internet from windows and linux
[*]I have not decided if I want everyone to have write access to this – probably not. However I would like a simple way for my wife to add primarily pictures to it.
[*]Backed up to usb disk which I can take with me if I go on a trip.[/LIST]

[FONT="Arial Black"]Personal file storage[/FONT]
[LIST]
[*]Same home folder regardless of where a log in
[*]Synchronized transparently
[*]Access to the documents/files when not on the network/internet
[*]Access to the files from another computer over the internet
[*]Automaticly sync changes when I get back on the lan
[*]Changes backed up every night
[/LIST]

[FONT="Arial Black"]This is the hardware I plan on using[/FONT]
[LIST]
[*]Two laptops (I currently only have one which we share)
[*]One server computer (which doubles as a desktop if the laptop is not home)
[*]PS3
[*]DNLA certified TV from Sony
[*]Nokia cellphone, N95
[/LIST]

I plan to buy two identical laptops so I don't have to worry about different HW setups.

[FONT="Arial Black"]Users[/FONT]
[LIST]
[*]We are currently 5 users
[*]Only two (my wife and I) are on the lan the other three only use the mail/webmail.
[*]One users uploads pictures remotely to the picture gallery
[/LIST]

[FONT="Arial Black"]Current setup[/FONT]
[LIST]
[*]**Mail **– I currently run postfix, dovecot and Horde on top apache of that. It works good enogh for my needs! I should be said that I acutually use apache to host some small webpages as well.
[*]**Calendar **– Horde has a decent calendar with support for SyncML. The syncing does however not work for some reoccurring events which make the entire sync fail leaving it completely useless. I have also tried Chandler which is great but does not sync with evolution or the phone and is a bit on the heavy side. The java processes take up more than 500 Mb of ram as it runs a complete Java EE server.
[*]**Address book** – tried to setup an LDAP server that would work as a personal address book for each of the users. The read part was OK but writing got complicated and I ran out of time. This was two years ago and I have not tried it since.
[*]**Picture gallery** - I currently have gallery2 running which is good for my needs and supports “the publish pictures on the internet”-windows XP extension.
[*]**Shared storage** – currently only stored on the server and accessed through SSH. I have a mediatomb server running so the PS3 can display most of the content. My TV however doesn’t find it. I add content I have to become root on the server and move the files and change the permissions/ownership.
[*]**Personal storage** – unison is automatically run every night to sync the home directories between the laptop and the server. This is not so transparent and a would prefer something else as I see some clear limitations if I have two laptop and a server. The laptops will have enough storage to hold complete copies of the private files of both me and my wife. To access the information from the net I simply use SSH. That however doesn’t from some company networks (I think their proxy only allows outgoing connections to port 80 – I have tried 10 different ports without luck but my webmail works). Therefore I have set up a small webdav share which stores some files that I access regularly. They however have to be owned by the www-data user so I have to access them through the web share even when I am at home.
[*]**Backup** - My backup solution is based on bacula. It is very capable but has some limitations. The main being that the files are backed up to archives which need the bacula tools to restore. I currently sync the home directories between the server and laptop every night. Then both the laptop and the server gets backed up individually.
[*]**Printing** - The printer sharing is done through Samba which works ok.
[/LIST]

[FONT="Arial Black"]Future[/FONT]
My plan is to remove X from the server computer and put it in a closet and instead by a second laptop. I would like to mount the shared data from the server on each laptop. I think Samba or NFS would work great for that when inside the lan and then use SSH to access the data over the internet (I very rarely do that). I could also set up a secure webdav for that as well but I very rarely need to access that from another computer than my own so it would not be worth the security risk. I’ve heard that fuppes might have better luck streaming media to my Sony TV. Has anyone tried?

For the personal data I don’t have a good idea on how to do it. I would like to somehow store everything on the server and then have it synchronize on a frequent and regular basis. I have also looked at networked file systems but I have to be honest and say that I haven’t figured the out entirely yet. Here I can’t use NFS or Samba because that would mean I have no access to the files when I’m off line. My wife would probably like to dual boot. Another reason not to use NFS I guess. Any ideas are welcome.

For the calendar I haven’t found anything that really does what I want it to. All suggestions are welcome. I have outlook at work which I sync with my cell phone so if I sync it again at home I would have both private and work appointments and to-dos in one place which is what I’m after. Ideally with different categories/calendars or whatever to tell them apart.

For the address book LDAP could be an option but I’m not sure which programs will write address data to it and how I could sync it with my phone. I might just have to live with separate address books.

For pictures I’m quite happy with gallery 2 but if I stay with horde I might try Ansel instead – then I only need to run one web-application. I have used f-spot for pictures management but the way that it stores files on disk (based on dates) is not really the way I view my pictures. I view my pictures as albums and for the media sharing to work I need to keep that information in the file structure. I’ll probably switch photo management software. Any suggestions? Preferably something that integrates well with gallery2 or Ansel.

For backups I might just go for some rsync scripts. Especially if I can use some sort of reliable sync between the laptops and the server I only need to backup the server (plus some config on the laptops but that doesn’t change all too often).

I guess that pretty much covers what I like from my home network. As you probably have figured out I’m not a big fan of using online services as I like to have control over my information.

Any thougths on how I can improve any part of this is welcome!

---

### Post by madverb on 2009-06-26
Zimbra can do Email, Calendar and Contacts.
Alfresco can do document management that you can access via website. That means you could access all your files.


For a roaming home directory you can do centralized authentication with Kerberos or LDAP and mount home directories via an NFS share. Could use something like 389 Directory Server but I think most of this would be over the top for a home setup. Might be fun to setup though.

That's my input...

---

### Post by hibliss on 2009-06-27
> **deepthink said:**
> 

[FONT="Arial Black"]Future[/FONT]
My plan is to remove X from the server computer and put it in a closet and instead by a second laptop. I would like to mount the shared data from the server on each laptop. I think Samba or NFS would work great for that when inside the lan and then use SSH to access the data over the internet (I very rarely do that). I could also set up a secure webdav for that as well but I very rarely need to access that from another computer than my own so it would not be worth the security risk. I’ve heard that fuppes might have better luck streaming media to my Sony TV. Has anyone tried?


I use FUPPES to stream videos/music/pictures to the PS3, works great.

---

### Post by tgalati4 on 2009-07-02
Checkout the latest version of conduit for elaborate syncing.  The repos tend to have an older version, and its rapidly evolving.  

I run tracks on a server for tracking todo's.  It uses a browser interface but can also generate RSS feeds and text reports which is handy for cell phones.  You can install it using a bitnami stack or install it natively on the server which is a little tricky but makes for a smaller installation footprint since libraries are not duplicated.

[http://getontracks.org](http://getontracks.org)

---

### Post by deepthink on 2009-07-06
Thanks for the tips.

I found SoGo at [http://www.scalableogo.org/](http://www.scalableogo.org/) which I think I'll give a try for as a calendar solution. That should be able to sync with my cellphone. That means ditching evolution in favor of thunderbird + lightning.

For files I think I'll just set up a few samba shares and then access files remotely through scp or davs.

---

