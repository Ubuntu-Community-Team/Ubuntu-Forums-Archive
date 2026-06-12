---
title: "Viewing Media with an LG Infinia 42LE8900"
date: 2010-11-25
forum: Multimedia Software
---

### Post by Jonners59 on 2010-11-25
I have just bought an LG Infinia 42LE8900 Tv.  It has a LAN port and has a built in capability to search and display media on the LAN.
 
I have a PC running Ubuntu 10.10 that I store all my media on and is kept on perminently for that purpose.
 
When using the Tv, I can not find this or any of the PCs or Laptops running Ubuntu.  It can find a Windows 7 virtual machine, but that is not used for media and nor does it have any media within it.
 
Does anyone know how to make the Ubuntu media visible to the Tv?  Seems everything is geared to Microsoft.

---

### Post by efflandt on 2010-11-25
You may need to install samba to do Windows like file sharing.  By default just the smbclient is installed.  Then you may need to edit /etc/samba/smb.conf (using **gksu gedit** or **sudo nano**).

---

### Post by Jonners59 on 2010-11-25
> **efflandt said:**
> You may need to install samba to do Windows like file sharing.  By default just the smbclient is installed.  Then you may need to edit /etc/samba/smb.conf (using **gksu gedit** or **sudo nano**).

Sorry, how do you mean?  I'm not too smart on this stuff.

---

### Post by gordintoronto on 2010-11-25
Select a folder, right-click on it, select "sharing options." If it prompts you to install software, do that and start over. Then, select "share this folder" and give it a name, also select "guest access."

---

### Post by Jonners59 on 2010-11-26
> **gordintoronto said:**
> Select a folder, right-click on it, select "sharing options." If it prompts you to install software, do that and start over. Then, select "share this folder" and give it a name, also select "guest access."

Ah, I'm with you.  No, I have done that some time ago.  I had a reply from LG, they state it needs something called DLNA....  Does that mean anything to you?

---

### Post by gordintoronto on 2010-11-26
> **Jonners59 said:**
> Ah, I'm with you.  No, I have done that some time ago.  I had a reply from LG, they state it needs something called DLNA....  Does that mean anything to you?

Today was the first time I have seen the term "DLNA." However, Google has lots of information. You might try installing mediatomb from Synaptic -- but you will need to spend some time reading about its setup. Another potential DLNA server is a program called Rygel. And you might also explore XBMC. Sorry, my TV has no ethernet port, so I can't try any of this.

---

### Post by Bone Down on 2010-11-26
try out miniDLNA from all the research I did trying to get my Maverick server to work with my setup miniDLNA was the easiest to get working. Rygel is the only one I have not tried yet, but I didn't feel the need to go any further once miniDLNA started to work for me.

[http://ubuntuforums.org/showpost.php?p=10167714&postcount=3](http://ubuntuforums.org/showpost.php?p=10167714&postcount=3)

---

### Post by Jonners59 on 2010-11-27
> **gordintoronto said:**
> Today was the first time I have seen the term "DLNA." However, Google has lots of information. You might try installing mediatomb from Synaptic -- but you will need to spend some time reading about its setup. Another potential DLNA server is a program called Rygel. And you might also explore XBMC. Sorry, my TV has no ethernet port, so I can't try any of this.

Thanks gordino...  appreciate.  I have tried some of these and it wiped out my SMB configs and now the machines (server) is discoverable, but can not get access.  This, like most Ubuntu things is never straight out of the box and simple.  I am some-what fedup and tired of all this, I must admit.  I have several threads on various subjects, getting no-where.


> **Bone Down said:**
> try out miniDLNA from all the research I did trying to get my Maverick  server to work with my setup miniDLNA was the easiest to get working.  Rygel is the only one I have not tried yet, but I didn't feel the need  to go any further once miniDLNA started to work for me.

[http://ubuntuforums.org/showpost.php...14&postcount=3]("http://ubuntuforums.org/showpost.php?p=10167714&postcount=3").

Thanks for this.  I did try miniDLNA, but got stuck and it killed my SMB.  But will try again.  I am not a techie and need step by step help.  The below:

I have extracted the config files from the download with these in and put them in the corresponding directories.

I have extracted the other folder and it now sits in; HOME/server/src/minidlna

How do I install it...?

---

### Post by Jonners59 on 2010-12-01
OK, sorted.
After trying the miniDNLA which did kill all SMB on the machine, it did however create the DNLA I was after.  However the server/PC I was trying to access via the Tv could not see the contents.  All I got ion the list of available networked media was "DNLA server:root".
 
The solution was to install:
[[COLOR=#444444]DNSMasq[/COLOR]]("https://help.ubuntu.com/community/Dnsmasq") and follwo the instructions....  WORKS GREAT

---

### Post by Jonners59 on 2010-12-22
> **klyndt said:**
> I do automount my drive using fstab at bootup.   I'm not sure what your setup is, but my fstab mount line is:
```
# /Data was on /dev/sda1 during installation
UUID=AAB8DA98B8DA61FD /Data           ntfs    defaults,umask=000,gid=46 0        0
```The problem was the umask.  It was 007 which kept the  DLNA devices from having permission on the folders on that drive (where  my media is).  I changed it to 000 and all is good now.  It was easy to  see the affect. When I did a 
ls -la
at first I could see the user group had no rwx permission. After this  change all files now have rwx in the last group. My guess is that the  umask doesn't have to be 000. It will work with 003 maybe. But since I  don't care that much.... :smile:

No, sadly that did not work either...

On the Tv I get "Shared_Media" come up, which is the name I gave the  server, so the DNLA is working, but I can not see anything in there.  It  says the folders are empty on the Tv.

Any other ideas guys, please?

---

### Post by Jonners59 on 2010-12-22
A new install that works very well, but don't forget the auto start script or you will have to manually start DNLA everty time you reboot.



[http://www.richtechnologies.com/?p=206](http://www.richtechnologies.com/?p=206)

[HTML] This is what I did to share my MythTV media with the Sony BDP-S570:
  Add the unofficial MiniDLNA Ubuntu PPA:
        sudo add-apt-repository ppa:stedy6/stedy-minidna
Update the APT package index:
        sudo apt-get update
Install MiniDLNA:
        sudo apt-get install minidlna
Edit the /etc/minidlna.conf file:
        sudo vi /etc/minidlna.conf port=8200
network_interface=eth0
media_dir=A,/var/lib/mythtv/music
media_dir=P,/var/lib/mythtv/pictures
media_dir=V,/var/lib/mythtv/videos
media_dir=V,/var/lib/mythtv/recordings
friendly_name=MythTV DLNA Server
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg
inotify=yes
enable_tivo=no
strict_dlna=no
notify_interval=900
serial=12345678
model_number=1
 
Restart the MiniDLNA server, removing the existing media list:
        sudo /etc/init.d/minidlna stop
                   sudo rm -r /tmp/minidlna
                   sudo /etc/init.d/minidlna start [/HTML]

---

### Post by tipiglen on 2011-01-04
Thanks to all who've been working these things out.

I've tried media tomb with mixed success, and serviio too.

Now trying minidlna, which works for all my photos and music, but says my home videos are 'invalid'  I reckon the solution is in transcoding or assigning mappings, but don't see any way in minidlna.

Any ideas?  (using LG 32ld490 through wired ethernet with computer connected wirelessly - server is visible fine.

Seasonal greetings to all

---

### Post by Jonners59 on 2011-01-04
tipiglen
I'm not techie, but it sounds like there is no codec for the format you use...  there are a number of converters in Ubntu SW centre (Applications tab) that convert.  install one and try it on one file...  see if it plays.  if it does do the rest

I too have found that some of my files are incompatible...
good luck

---

