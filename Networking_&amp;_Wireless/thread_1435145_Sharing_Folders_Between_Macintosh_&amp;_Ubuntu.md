---
title: "Sharing Folders Between Macintosh &amp; Ubuntu"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by Xtaris on 2010-03-21
Hello,

I have just discovered Ubuntu over the last few days and have been really impressed with what it can do on just ordinary hardware. I work in a mixed Windows / Macintosh network environment and have been looking to transition the Windows boxes out as Vista has proved to be a complete nightmare in every way... So Ubuntu has been a real fantastic discovery as it works faster on my old Windows boxes than Windows ever did. Anyway I have run into a small problem which i just can't figure out, this may be because I am really a complete beginner with Ubuntu, my problem is as follows:

- How do I setup peer to peer folder sharing between Macintosh computers and Ubuntu? I have tried everything that seems obvious but I have had no luck so far. My Macintosh machines are running Snow Leopard with all the latest patches etc and I am running Ubunru 9.10 on my Ubuntu machines. 

I am intending to switch to Ubuntu servers soon, but right now I just need to get peer to peer folder sharing working between Ubuntu and the Macintosh. Any help much appreciated.

Regards, Xtaris.

---

### Post by Morbius1 on 2010-03-21
After setting up shares on my linux system, my wife's MacBook found them automatically in Finder. Let's take a look at how your shares are set up. You stated you tried a lot of things so please post the output of the following commands. This will tell us how your Ubuntu shares are defined and what method of sharing ( there are two methods ) you're using:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

---

### Post by johnson.d on 2010-03-22
You can use NFS or Samba for having peer to peer file sharing between Macintosh & Ubuntu.

I) NFS Server in Ubuntu:

You can setup NFS using the following steps:

1) Installing NFS

Use the following command to install nfs server

```
$ sudo apt-get install nfs-kernel-server
```

2) Configuration of NFS

For configuring NFS you need to edit the /etc/exports file. You can append the following lines to /etc/exports file to add a share.

```
/<shared-folder> *(rw,sync)
```

3) Restarting the service after configuring

You can use the following command to restart the service

```
$ sudo /etc/init.d/nfs-kernel-server restart
```

II) Samba server in Ubuntu

1) Installing Samba

Samba can be installed in Ubuntu using the following command:

```
$ sudo apt-get install samba
```

2) Configuration of Samba

For configuring Samba you need to edit the file /etc/samba/smb.conf. You can add the following lines to the file
 
```
[<share-name>]
path= /<share-path>
browseable = yes
read only = no
```

3) You can restart the Samba service using the following command:

```
sudo /etc/init.d/samba restart
```

---

### Post by Xtaris on 2010-03-22
Hi, 

Thanks for your help. I have been trying to run the commands in terminal that you listed, but unfortunately I cannot get them to run under Ubuntu. I can get it to run on the Mac but not on Ubuntu. Did you mean run those commands on ubuntu and the Mac? If so ubuntu does not run them :-( 

Regards, Xtaris.

---

### Post by Morbius1 on 2010-03-22
I don't know who you are addressing, me or johnson.d, but in both cases they are Ubuntu commands.

Can you go into Nautilus, right click on /home/your_user_name/Documents and select "Sharing Options"?

If you can,  just select all three boxes, select "Create Share" and see if Finder can ... well ...Find it.

---

### Post by Xtaris on 2010-03-22
Hi,

Sorry was replying to you. Have tried the other stuff but none of those commands seem to work either. I have tried going to Documents and clicking on Sharing Options, but can only switch on two of the options, the other one is greyed out. I get Nautilus needs to add some permissions etc but have done that a number of times but nothing seems to change."Add the permissions Automatically" does not seem to do anything :-( 

I can see my Ubuntu machine from the Mac but cannot connect to it. I get an error message "The server &#8220;emachines-laptop&#8221; may not exist or it is unavailable at this time. Check the server name or IP address, check your network connection, and then try again.". Am lost now, exceeded my technical knowledge, and am getting fed up as have checked all of the above and dont know what to do next ARRRRRRR :-( 

Beginning to think maybe I should just stick with ripping Windows systems out and going with Mac's :-( I just cannot seem to make Ubuntu do anything network related. Have gone round the cycle of trying to add permissions endlessly but nothing seems to happen, change or work. It's beginning to feel like Vista all over again :-(  I am a long term Mac user and this stuff just seems to work with the Mac , maybe I am just too un-technical for this stuff on Ubuntu.

It's actually beginning to look WAY too complicated to make this work on a network with Mac's. I may be wrong. HEY I want to be wrong but I don't need another Windows type nightmare when it comes to doing anything. I am hoping Ubuntu will just work with some level of simplicity with the Mac. 

All I need to know is how to make a folder on Ubuntu show up on a Mac and vice versa; without spending hours working out HOW to make it work. 

I like Ubuntu but it may just be that it's not simple enough for me :-( 

Regards, Xtaries.

---

### Post by Morbius1 on 2010-03-23
First:
> I can see my Ubuntu machine from the Mac but cannot connect to it. I get an error message "The server “[COLOR=Blue]emachines-laptop[/COLOR]” may not exist or it is unavailable at this time. Check the server name or IP address, check your network connection, and then try again."Your machine name is too long. It must be 15 characters or less. To remedy:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

In the [COLOR=Blue][global][/COLOR] section add the following line:
```
netbios name = emach-laptop
```Second,
> I have tried going to Documents and clicking on Sharing Options, but can only switch on two of the options, the other one is greyed out You didn't tell us which one is greyed out. I'll guess that it's "Guest access". To remedy:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Check to see if you have the following line:
```
usershare allow guests = yes
```If you don't have that line then add it to the [COLOR=Blue][global][/COLOR] section of smb.conf.

When you're all done with any changes to smb.conf, save the file and restart samba:

Open **Terminal**
Type **sudo service samba restart**

I hate it when other posters say this type of thing, but it took me literally less than 20 seconds to share a folder to my wife's MacBook. This was in an out of the box install and I did nothing special - no editing - no tweaks. 

The fact that you can't run the following commands:
> Open **Terminal**
Type **net usershare info**
Type **testparm -s**suggests that something is wrong with your install or with samba. The thing about the machine name length is one thing but if "usershare allow guests" is not in your smb.conf file then something is wrong with the samba part of your install, you used a utility to configure samba, or it got corrupted somehow.

---

### Post by whiteman on 2010-03-23
I spend yesterday trying for the 3rd time to get Karmic to work. I  finally got it but no Canon printer. Screw it.
SHARING..I reinstalled Janty and wont go back.
I have a Windze lap(xp)a MBPro with SL..A desktop with Jaunty. ALl commune and print. I can trade files back and forth beween all three..(I forgot I have win7 on my wifes desktop) SO thats 4 in the loop. I spent all day trying to outthink myslef. I was getting this error message when I logged on about home folder, permsissions....etc. I had tried to set up sharing with samba gui and Nutilus.
I use a gksudoNautilus icon on top panel. Very useful. I finally decided to go with the easiest way. I didnt remember how I did it before. I was burnt out on listening to all these geniuses who try to make it complicated....uncomment this line...add these lines to smb.conf...opemn gdm....stand on your head...spit at the moon. I mean really. Heres all I did..and its Purrrrfect.
Gksudoo Nautilus...right click folder...at the top of window...pick share...then  since its sudo it allows me to d what I want. I pick write to etc. In system-Admin-Smaba the only item there is my $print. Thats it. No editing. No sudo.No testparm. NOTHING.Altho testparm is very useful to just see whats goin on.
I have been trying linux since Mandrake days. Gave up/ Came back at 8.04. Im no guru. I deliver pizzas, im retired. Mac is best. No question, but on a PC....I use Ubuntu, a very fine system. Now if I could just get my webcam to work.....

---

### Post by whiteman on 2010-03-23
Im sorry to say this but I never had any luck with 9.10. I tried to install it 3 times. Wiped my HArd drive. Resetup grub. whole 9 yds. I have MBpro and desktop Jaunty(9.04) I created a Nautilus with sudo powers.(gksudo Nautilus) A lotta people look down their noses at this fix. Not elegant enuff. Run Nautilus...pick folder...right click.properties.....share.....Create a share. THATS IT. BTW I found that if I didnt do this with File System(/) I had cups problems. Go figure. You will have to give it a name..(/) is no acceptable for a share. I use "file system" The only thing I edit in smb.conf..is workgroup=mywkgp..where mywkgp is the name of yer workgroup. Now I may be wrong. But this is what I did and its easy to undo. BUT IT WORKS.

---

