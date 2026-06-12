---
title: "Plex movie files on Ub 14.04"
date: 2016-08-28
forum: Multimedia Software
---

### Post by Robbyx on 2016-08-28
Has anyone experience of setting up plex on a Lan? I am using the Roku (Now TV) as the receiver of the videos, but having reinstalled Ubuntu I can not set up the plex server to see any of the files I wish to stream. 

I have tried:

Going to the external HD where the files are located and creating a link into the home directory.
Changing the permissions on the link and the Ext HD drive to 777 (I don't think the drive ownership changed). The link in the  home director to the ext HD   can not be seen in plex as an entry in the home directory. 

Pointing plex to the actual directory within the Ext HD drive. The HD can be seen, but  not the directory with the files for streaming. 

Has anyone got round this problem?

---

### Post by TheFu on 2016-08-28
I've run plex MS for a few years. There are many guides for plex which explain the required permissions and ownership for the media files.  A common mistake is using NTFS formatted drives for media and not setting the mount permissions correctly.  The other is using non-permanent storage and expecting Plex to be happy when the storage is missing.  There are ways to work around each of these. [https://support.plex.tv/hc/en-us/articles/200288596-Linux-Permissions-Guide](https://support.plex.tv/hc/en-us/articles/200288596-Linux-Permissions-Guide) explains.  [NTFS]("https://askubuntu.com/questions/620363/plex-media-manager-sees-external-ntfs-drive-but-doesnt-see-directories")   [More NTFS]("https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux")

Another thing to know is that Plex and Kodi and XBMC have very specific directory structure requirements for media files to be seen at all. [https://support.plex.tv/hc/en-us/categories/200028098-Media-Preparation](https://support.plex.tv/hc/en-us/categories/200028098-Media-Preparation) - it basically comes down to putting each movie into a separate directory under the "Movie" directory.  Putting each TV series into 1 or by-season directories under the "TV" directory and something similar for Music.  Having a single directory for all Movies or all TV shows doesn't work.

There is **Never** a good reason to use 777 permissions, IMHO.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) and [https://www.linux.com/learn/understanding-linux-file-permissions](https://www.linux.com/learn/understanding-linux-file-permissions) .  Plex runs as userid plex, so that user needs at least read access to the directories and media files.

So ... if the above doesn't help, let us know which file system is being used, how the media storage is mounted, what the mount options are and an **ls -al** for each of the Movie, TV, Music, and other directories.

---

### Post by Robbyx on 2016-09-10
SInce your reply I have been failing to see anything on my TV via Plex/ Roku.

The drives are Ext 4 not NTFS.

Today I made some progress:

I registered the handset with Plex.tv, and entered the code. Provided the **gufw firewall** is set to allow all incoming traffic the videos are showing in the plex app on the TV screen. The app linked with the plex.tv  account successfully.

I have tried and failed to port forward within the firewall and so when the incoming is set to deny traffic,  no videos appear on the TV screen.

I using the Sky version of Roku.

I have no understanding of how to set up the firewall with port forwarding for the plex. I am unclear what the from address is ie is it plex.tv or the roku handset?

According to an article on the Plex web site the Ports required to be forwarded are 

TCP: 32400 (for access to the Plex Media Server) [required]

UDP: 1900 (for access to the Plex DLNA Server)

TCP: 8324 (for controlling Plex for Roku via Plex Companion)
TCP: 32469 (for access to the Plex DLNA Server)

*[https://support.plex.tv/hc/en-us/articles/201543147-What-network-ports-do-I-need-to-allow-through-my-firewall](https://support.plex.tv/hc/en-us/articles/201543147-What-network-ports-do-I-need-to-allow-through-my-firewall)*

Assuming my main computer is 192.168.1.4 and the Roku is 192.168.1.7 which of the above ports  need rules and can you please give me an example of how it should they be set out?

The following port forwarding  approach to all the above ports  does not work and no streaming takes place on the TV
eg:
From: 192.168.1.7 Port 32400
To 192.168.1.4 Port 32400
TCP

Can you help on the port forwarding settings?

---

### Post by TheFu on 2016-09-10
I don't use plex the same way you do, it seems.
My entertainment subnet is open between all the systems on it. No firewall rules in the way between the Plex MS, multiple Kodi machines, TV Recording VM and network TV tuners.

I don't use plex accounts. Don't have one. No need for a Plex account if you only access content on the LAN.
I don't use plex apps to view content. Only use Kodi + PlexBMC addon running on a R-Pi v2.  Once in a while, I'll watch content using a web browser.

Plex is a media SERVER, not a media PLAYER, at least on my network. 

Plex isn't open to the WAN here. It hosts local content (Movies, TV, Music, Photos) only.  No firewall rules needed here, since only LAN systems can access the Plex machine.

I have a roku, but have barely used it with the Plex Server. We use the Roku only to access APV. No ports are open from the WAN to the roku either.

Sorry, I'm not any help with firewall stuff.

At to you not seeing your media, why is that?  Does the Plex userid have read access to all the files and directories?  Are the files and directories in the require structure to be scanned?  Did you select the correct library "type" and "scanner" for each "type" of media in the media server web-gui?

---

### Post by Robbyx on 2016-09-11
It seems to have corrected itself and is now working.

Thank you very much for your help and support. Greatly appreciated.

R

---

