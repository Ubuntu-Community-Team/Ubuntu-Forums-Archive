---
title: "Plex Server can't find files?"
date: 2012-07-16
forum: Multimedia Software
---

### Post by Blacksheep01 on 2012-07-16
Hey all, I've been an Ubuntu user for a while now, and while I have learned a bit, I still feel as though I am a beginner and thus need things explained like I'm 5 at times lol.

Anyway, my problem is with Plex Server (the most current version) on Ubuntu 12.04 32-bit desktop edition, basically it cannot find my TV Shows or other media on my NAS device. I point it at the correct server folders and Plex never populates.

To eliminate other problems I will explain my set up. I have Plex Server running on a Windows 7 PC presently, it is grabbing my files from a NAS I have on my network and serving those files out to an LG TV and a Roku box without a hitch. However, I want to change my Plex server over to my Ubuntu desktop and now I've hit snags.

I installed Plex just fine in Ubuntu and by default it will not find anything on my NAS. In looking up solutions I found that my "user" needed to be added to my Plex group, which I did successfully with a "sudo" command as gpasswd -a plex did not work. Doing this did not solve the problem.

I then read that NAS folders need to be permanently mounted in Ubuntu as I have them mounted in Windows. However, the explanation of how to do this in Ubuntu was confusing to me with some config file/cmd lines that weren't explained well. To top it off, I'm not certain if that is even the solution?

Can anyone help? If the problem is simply mounting the server folders permanently in Ubuntu, can someone point me toward an easy tutorial that will explain every last detail like where I find files to edit, where I add that info etc?

Thanks:guitar:

---

### Post by Blacksheep01 on 2012-07-16
I solved this and I'm a total newb, so I will post what I did for other newbs.

Anyway, after four days of web searches I found this tutorial [http://www.liberiangeek.net/2012/04/create-and-automatically-mount-windows-7-shares-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/create-and-automatically-mount-windows-7-shares-in-ubuntu-12-04-precise-pangolin/)

Skip the Windows part, I went straight down to Ubuntu as I have my files on a server and had not interest in whatever they were doing in windows.

The key were these steps copied from the site to make it easier (with some of my commentary): 

Step 1 - Open terminal, type in: 
sudo apt-get install smbfs

Step 2:
Create a Windows folder in your home directory by running the commands below. (Note you can name this directory anything /Movies or /CatParty etc.

 mkdir ~/Windows 

Step 3: 
 Run the commands below to open fstab config file.
 sudo gedit /etc/fstab 

Step 4:
At the bottom of that fstab file add the following text

//Windows_Computer/Share /home/[COLOR=#0000ff]<[/COLOR][COLOR=#800000]Ubuntu username[/COLOR][COLOR=#0000ff]>[/COLOR]/<Name of folder you created above /Movies etc> cifs uid=[COLOR=#0000ff]<[/COLOR][COLOR=#800000]ubuntu[/COLOR][COLOR=#ff0000]_username[/COLOR][COLOR=#0000ff]>[/COLOR],user=[COLOR=#0000ff]<[/COLOR][COLOR=#800000]Windows[/COLOR][COLOR=#ff0000]_username[/COLOR][COLOR=#0000ff](or server username)>[/COLOR],password=[COLOR=#0000ff]<[/COLOR][COLOR=#800000]Windows[/COLOR][COLOR=#ff0000]_Password[/COLOR][COLOR=#0000ff]>[/COLOR] 0 0

Because examples like I typed above confuse the hell out of me, here is what mine actually looked like, passwords removed of course

//lg-nas.local/TV_Series /home/trap/Windows cifs uid=<trap,user=xxxx,password=xxxx 0 0



Step 5: Reboot and the drives are mounted and can be easily added in Plex.

---

### Post by Blacksheep01 on 2012-07-16
Also, I'm not sure of protocol here, but it would be great if this process were easier in future editions of Ubuntu. A simple "map network drive" that allowed you to permanently mount drives Ubuntu can already see, would make this process take only 1 minute.

---

### Post by teranine on 2013-01-03
Thanks for the tip.  Not much of a community here and people hardly show their appreciation for other's efforts.

Trying to figure out why plex is not seeing my video files on the PS3 at the moment.  Not using NAS and just strictly ubuntu. Have been using PMS for years successfully but am trying a different server now that I have a roku also. Will find the answer eventually...

---

### Post by zalloy on 2013-03-31
I'm having a similar issue. I recently installed Ubuntu as a dual-boot with Win7. I have my Plex movies in a directory on an external hard drive. The movies are all visible and accessible when using the Windows Plex server, however when I boot into Ubuntu and use the Linux Plex server, it only sees the top level directory. So, for example, if the movies are all in L:\Plex Shares\Movies, it only sees the Plex Shares directory, and nothing below it. 

I'll try the tips suggested here, and see if it corrects the issue.

---

### Post by aria2 on 2013-04-22
[http://ubuntuforums.org/showthread.php?t=2087341](http://ubuntuforums.org/showthread.php?t=2087341)

+/-: [http://ubuntuforums.org/showthread.php?t=2107245&highlight=plex](http://ubuntuforums.org/showthread.php?t=2107245&highlight=plex)

---

