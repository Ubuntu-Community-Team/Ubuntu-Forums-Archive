---
title: "Problem with Vuze"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by sandy0594 on 2011-04-14
Can i know why downloads in vuze is not starting at all..when i try to download the same file in Transmission bit torrent client,it is going well..

But,in vuze it is always trying to locate the seeds and peers..Why is it like that?

---

### Post by nitstorm on 2011-04-14
Have you checked whether the port that Vuze uses is blocked or something? Or try changing the port in Vuze and see if that helps. 

On a different yet personal note, i love using rtorrent. ( u can install it with the following cmd: *sudo apt-get install rtorrent *  ) It's simply amazing and super light-weight. Check it out [here]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/") if you not intimated by a little CLI :P

---

### Post by sandy0594 on 2011-04-14
Installed rtorrent but couldn't find it in my applications menu
Where to find it?

---

### Post by nitstorm on 2011-04-14
Follow the instructions on the link in the previous post. You will not be able to find rtorrent in the applications menu, its run from the terminal and you will have to interact with the application using just the terminal....

---

### Post by sandy0594 on 2011-04-14
See this,i have installed it but i couldn't find it in my applications menu

> 

sandy@ubuntu:~$ sudo apt-get install rtorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rtorrent is already the newest version.
The following packages were automatically installed and are no longer required:
  libswt-cairo-gtk-3.5-jni libswt-gtk-3.5-jni liblog4j1.2-java
  libswt-mozilla-gtk-3.5-jni libcommons-cli-java libcommons-lang-java
  libswt-gnome-gtk-3.5-jni libswt-gtk-3.5-java java-wrappers
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



---

### Post by nitstorm on 2011-04-14
you will not find it in the applications menu. It can only be run from the terminal.  It's one of those CLI tools .

Open up a terminal and put in ```
rtorrent
``` Read [the link]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/") fully and then you should be able to use a super light-weight & super fast torrent client

---

### Post by sandy0594 on 2011-04-14
Oh!  my bad..how to use that..i am very new to this Linux

---

### Post by sandy0594 on 2011-04-14
how to interact with it..
> 
                  *** rTorrent 0.8.6/0.12.6 - ubuntu:4183 ***
[View: main]





















[Throttle off/off KB] [Rate   0.0/  0.0 KB] [Port: 6931] [U 0/0] [D 0/0] [H 0/3



---

### Post by nitstorm on 2011-04-14
Don't worry about it man. [Click here and read this link here]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/"), it's a complete guide to using rtorrent. 

Welcome to Linux brother :) 



P.S.: Windowski compare chesthey Linux chala chala better. Firstlo koncham differentuga untundhi kaani koncham familiar aiyina tharavatha Linux loney kurchuntavu. Naaku ipudu adhey ayindhile :)  Enjoy cheyi :) And once again welcome to Linux :)

---

### Post by sandy0594 on 2011-04-14
I hit **return **to navigate a file /media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads/[isoHunt] The.Curious.Case.Of.Benjamin.Button.2008.DvDRip-FxM.torrent

but,back in terminal there is nothing going on

> 
( 1:08:54) Tracker group list not a list
( 1:09:27) Command type mis-match.
[Throttle off/off KB] [Rate   0.0/  0.0 KB] [Port: 6931] [U 0/0] [D 0/0] [H 0/3




---

### Post by nitstorm on 2011-04-14
Okay, try this. Press **CtrlQ** , you are back at the shell prompt.

Step 1: ```
cd /media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads/ 
```
That changes the working directory to the directory where the torrent file is stored
Step 2: ```
rtorrent
```
That opens rtorrent
Step 3: Hit **return** and type [isoHunt] The.Curious.Case.Of.Benjamin.Button.2008.DvDRip-FxM.torrent

---

### Post by sandy0594 on 2011-04-14
No luck to browse through the files

> 

sandy@ubuntu:~$ cd /media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads/
bash: cd: /media/18D80590D8056CF6/Documents: No such file or directory
sandy@ubuntu:~$ sudo cd /media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads/
[sudo] password for sandy: 
sudo: cd: command not found




---

### Post by nitstorm on 2011-04-14
You don't need to cd with sudo .

Anyways , try this

cd /media/18 (Hit Tab for auto-completion)/Docum (Hit Tab for auto-completion) / Sand(Hit Tab for auto-completion) /My (Hit Tab for auto-completion)Docu(Hit Tab for auto-completion)/Down(Hit Tab for auto-completion) 

that should get u in the particular directory . Whenever u hit tab key, it automatically fills the file/directory name based on the files/dirs in the particular directory. Linux reads spaces in file and directory names differently ...... so best and easy is the auto completion by using the TAB key....

---

### Post by sandy0594 on 2011-04-14
It's looking like I need to configure something as per the link i followed 

[http://ubuntuforums.org/showthread.php?t=1652105](http://ubuntuforums.org/showthread.php?t=1652105)

Anyhow,thanks for ur prompt replies,i will keep u posted after my prob gets solved

---

### Post by nitstorm on 2011-04-14
But looks like it wont work on 10.10 (Maverick Meerkat), 

If it doesn't,  try to use the link from my previous posts. I setup rtorrent using that....

No problemo :) Good luck bro :)

---

### Post by sandy0594 on 2011-04-14
Now,i am getting some stupid error message
> 
sandy@ubuntu:~$ rtorrent
rtorrent: Error in option file: ~/.rtorrent.rc:110: Could not prepare socket for listening: Address already in use



Anyhow,i will look after it tomorrow..thanks for ur replies

Catch u later

---

### Post by nitstorm on 2011-04-14
Close the other torrent clients before using rtorrent. 
Try this,
```
cp /usr/share/doc/rtorrent/examples/rtorrent.rc ~/.rtorrent.rc 
```

---

### Post by sandy0594 on 2011-04-15
U sorted out the error message..but downloads are not happening
```

sandy@ubuntu:~$ cp /usr/share/doc/rtorrent/examples/rtorrent.rc ~/.rtorrent.rc
sandy@ubuntu:~$ rtorrent
sandy@ubuntu:~$ cd '/media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads' 



```

---

### Post by sandy0594 on 2011-04-15
See the attachment

---

### Post by nitstorm on 2011-04-15
Now hit enter, the first few letters of the torrent file and use tabkey for auto-completion. And after that, press the down arrow-key and once stars appear next to the torrent, press **CtrlS** to start the torrents and **CtrlD** to stop the torrents. Please read the link that I've posted earlier. It's the best rtorrent guide you'll find on the internet.

---

### Post by sandy0594 on 2011-04-15
See this..
In the first one i am adding the torrent and in the second attachment as u see,there is nothing visible in the window with my file name

---

### Post by sandy0594 on 2011-04-15
I even copied rtorrent.rc file into my home directory..

```

# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 100

# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 10
#max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
#max_uploads = 15

# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 0
#upload_rate = 0

# Default directory to save the downloaded torrents.
#directory = ./

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
#session = ./session

# Watch a directory for new torrents, and stop those that have been
# deleted.
#schedule = watch_directory,5,5,load_start=./watch/*.torrent
#schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no

# Port range to use for listening.
#port_range = 6890-6999

# Start opening ports at a random position within the port range.
#port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
#use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
# encryption = allow_incoming,enable_retry,prefer_plaintext

# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined.
# 
# dht = auto

# UDP port to use for DHT. 
# 
# dht_port = 6881

# Enable peer exchange (for torrents not marked private)
#
# peer_exchange = yes

#
# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
#hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
#hash_interval = 100

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
#hash_max_tries = 10


```

---

### Post by nitstorm on 2011-04-16
No idea what the problem is, but can u try copying the torrent file to the home folder and try rtorrent there, plus it makes it easier for rtorrent when files are on Ext4 Filesystem and not on NTFS ( I had corrupted files when i downloaded to NTFS because NTFS employs some sort of compression thing.. )

---

### Post by sandy0594 on 2011-04-16
Same old problem even if i am downloading a file from my home directory..I think i am not up for it

---

### Post by nitstorm on 2011-04-20
[http://code.google.com/p/rutorrent/](http://code.google.com/p/rutorrent/)

This is a WEB UI for rtorrent, maybe this will make things easier for u?

---

### Post by sandy0594 on 2011-04-20
Installed it with the help of this link

[http://www.howtoforge.com/how-to-compile-coloured-rtorrent-from-svn-in-ubuntu-10.10-maverick-meerkat-debian-6-squeeze-with-rutorrent](http://www.howtoforge.com/how-to-compile-coloured-rtorrent-from-svn-in-ubuntu-10.10-maverick-meerkat-debian-6-squeeze-with-rutorrent)

But,still i can't download from rtorrent

Today it's horrible,even the page is not displaying..the day when i installed it at least i could see it

---

