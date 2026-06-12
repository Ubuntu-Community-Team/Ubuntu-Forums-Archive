---
title: "Streaming files to iTunes from an NTFS external drive with mt-daapd"
date: 2008-08-06
forum: Multimedia Software
---

### Post by fhsm on 2008-08-06
**Goal**: Stream music off of an external NTFS drive attached to an Ubuntu HH box into Apple iTunes (on both apple and win).

I looked around a bit and decided that I wanted to use [Firefly / mt-daapd]("http://www.fireflymediaserver.org/").  It has an active community with [good support info]("http://www.fireflymediaserver.org/support.php") and I liked the [web interface]("http://www.fireflymediaserver.org/screenshots.php?section=Web_Interface&file=Status_Page.jpg") for the server.

So to install it and put together a little guide along the way:
[B]
1 - Install the server on Ubuntu.[/B]
```

sudo apt-get upgrade
sudo apt-get install mt-daapd
sudo /etc/init.d/mt-daapd stop

```

**2 - Configure the server.**
```
sudo nano /etc/mt-daapd.conf
```
I changed the following in the config file:
```

admin_pw = <set your web interface pw>
mp3_dir = /path/to/your/files 
servername = %h 

```
I wanted to share the music directory in my user folder so I used /home/USER/Music as my mp3_dir.
The servername is the system's name in iTunes.  %h will be the system hostname.  You can set it to whatever you like.
*Important: don't change runas = mt-daapd*
For more info on the config file check out the [firefly wiki]("http://wiki.fireflymediaserver.org/Config_File")

3 - **Link the drive.**
Link the external drive into the folder the firefly media server is looking in (*/home/USER/Music* in my case). 
```
Ln –s /path/to/externaldrive /path/to/your/files
```
In my case it was:
```
ln –s /media/USBDriveLabel /home/USER/Music 
```

At this point you should have firefly (aka: mt-daapd) installed and looking at a folder that is linked to your external drive.

4 - **Start the server.**
```

sudo ufw disable
sudo /etc/init.d/mt-daapd start

```
*important: ufw disable takes down your firewall, don't forget to put it back up (if it was up in the first place).*
If you don't know your servers IP address run *ifconfig -a* to get it.

**5 - Finding your songs and checking the server.  **
From one of the systems running iTunes browse to  http://<serverIP>:3689 (ex: [http://192.168.1.100:3689](http://192.168.1.100:3689)).  You’ll be prompted for your username and password.  Leave the username blank and use the password you set in the mt-daapd.conf file to login.

From the menu on the left select “server status” then click the “start scan” button.  The system will work for a while (a long while if you’ve got a lot of songs) but should finish up and show an appropriate number in the “Songs” field of the status page.

*Troubleshooting (Skip to 6 if "songs" looks right)*
If, after scanning, your system shows 0 songs you have likely stumbled into a permissions gray area.  Start by dismounting, disconnecting, and then reconnecting your external drive.  The user that is currently logged in should have full permissions on the NTFS drive now.  With that drive symbolically linked to (using me as an example) my user music folder (/home/USER/Music) and firefly set to mp3_dir = /home/USER/Music), 
Restart firefly *sudo /etc/init.d/mt-daapd restart*.  From the ubuntu system go to [http://localhost:3689](http://localhost:3689) and run a scan as described previously.  
If you still show zero songs run *sudo chmod 755 /path/to/your/files* (using me as an example /home/USER/Music).  Now run the scan a third time and you should have it.
*Aside*: 
At this point you’ve got to be wondering about the runas option in the conf file.  All I can say is me too.  I tried changing it to solve my permissions problems and it killed the firefly server.  Returning the setting to mt-daapd got it restarted again, so no damage done, but not an obviously useful setting in my case.  

**6 - Test drive. **
Now launch iTunes, your Firefly server should show up as a source in the tray.  Play a song and be sure everything works.  
*Troubleshooting*
If not, open preferences, select the Sharing tab, be sure that “Look for shared libraries” is checked.  Press okay, restart the system and you should be good to go.
If not go back to the Ubuntu server and be sure you can actually play the files on it.

**7 - Getting past UFW. **
Now we need to get’em talking through ufw.  This next bit assumes that you’ve got ufw enabled, that your default is set to deny, and you are running on a 192.168 network.  If this is the first time you are thinking about your firewall it is a topic unto itself.  If you don’t already have ufw enabled it might break a lot of things if you enable it, so [read up]("https://wiki.ubuntu.com/UbuntuFirewall") before proceeding.  Regardless of how you do it you've got to be able to get at tcp/3689 and udp/5353 to get this show off the ground.  These are best guess rules that should work for most people:
```

Sudo ufw allow proto tcp from 192.168.0.0/16 to any port 3689
Sudo ufw allow prot udp from 192.168.0.0/16 to port 5353
Sudo ufw enable

```

Finished. You should be good to go at this point.  You can control the firefly server from any system on your network by going to http://<serverIP>:3689.

**Conclusion**: I’ve found this setup to be quite reliable once it is setup; however, getting firefly to actually see my songs on the external drive was a pain.  Anyone with insight on the permissions front would be appreciated.

Good luck!

---

### Post by MrSootentai on 2008-08-11
This was a great post, and really helped.
But I'm still having a problem. 
When I click 'Start Scan' it finishes really quick and only shows 68 Songs have been found. Even though I have well over 5000. 
Could the problem be that I have my /home on its own partition (did it as a backup procedure)?

---

### Post by mckechan on 2008-08-28
Argh! This sucks. I have set up mt-daapd on my ubuntu box and from my macBook I can access port 3689 through the browser to see the firefly web page.

It shows the correct number of songs and I have no failures in my mt-daapd.log.

However, iTunes absolutely refuses to display the library and obviously I do have the option on that says, 'Look for shared Libraries'.
:mad:


Any ideas what the problem can be?

---

### Post by fhsm on 2008-09-27
> **MrSootentai said:**
> This was a great post, and really helped.
But I'm still having a problem. 
When I click 'Start Scan' it finishes really quick and only shows 68 Songs have been found. Even though I have well over 5000. 
Could the problem be that I have my /home on its own partition (did it as a backup procedure)?

This sounds like a permission problem.  I fought with this for some time when setting up my system.  Double check the directory in your mt-daapd config file and try *temporarily *setting it to 777.  See if that fixes the problem.

Now step down from 777 and see when it stops working.

If you are comfortable running at whatever was one click above broken you are good to go.  If not you'll need to take it up with someone who knows more about permissions.

---

### Post by fhsm on 2008-09-27
> **mckechan said:**
> Argh! This sucks. I have set up mt-daapd on my ubuntu box and from my macBook I can access port 3689 through the browser to see the firefly web page.

It shows the correct number of songs and I have no failures in my mt-daapd.log.

However, iTunes absolutely refuses to display the library and obviously I do have the option on that says, 'Look for shared Libraries'.
:mad:


Any ideas what the problem can be?

Short answer is I fumbled my way to a working solution without and don't really know enough to be of much help.  

Try taking down UFW and see if iTunes can find the library then.  Although it sounds like that won't make a difference.

Failing that try finding the ubuntu server with another iTunes install & finding another library with your macbook's iTunes to narrow down the problem.

---

### Post by buzzbo on 2009-12-21
I'm going to give a bump here because I had some minor permissions issues (SOLVED) with using an NTFS drive (internal) with mt-daapd (Firefly Media Server).

I pointed mp3_dir to my NTFS directory with my tunes, but they did not show up.  When using the web config util, I confirmed no music.  When I tried to set the folder I got this error: [COLOR=Red]Error: 500general:mp3_dir[/COLOR]

So in looking at the directory (ls -lh) my NTFS mount was not readable by "other." So, I took a look at my /etc/fstab, which is all pretty and polished because I recently went with a fresh install of 9.10 on top of 9.04.  Anyhow, I found the umask was set to exclude the "other" category, which seemed odd, i.e. in blue:

```
UUID=168284AD4A623D21 /media/drive_d  ntfs    defaults,nls=utf8,[COLOR=Blue]umask=007[/COLOR],gid=46 0       0

```so I unmounted the NTFS partition and changed the /etc/fstab entry accordingly:

```
UUID=168284AD4A623D21 /media/drive_d  ntfs    defaults,nls=utf8,[COLOR=Blue]umask=022[/COLOR],gid=46 0       0

```After remounting, and restarting the Firefly Music Server daemon and looking at the web config tool, my music showed up.  Hope this helps anyone having a similar problem in 9.10.

Buzz

---

