---
title: "Problems Accessing Vista Shared folder - Possible Solution"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by ramblinche81 on 2010-01-31
This might not be a root cause solution to those with problems mounting/accessing WinVista SHARED folders via SAMBA from Ubuntu OS, but it worked for me on my small three machine home network. It could be burdensome for a large scale enterprise, but it could be a clue what is going wrong with Vista allowing access to Shared folder via SAMBA from Ubuntu OS.

_**Summary Solution**_
Create user name with password on WinVista OS machine to match user name(s) on Ubuntu OS machines and assign WinVista Shared folder to new user name(s) with co-owner rights. Oversimplified, tell Vista users with name other than blank want access to Shared folder. 

**_Problem Background:_** 
Desktop running 9.10 Karmic for about one month on a wireless secure home network with two other MS Win based machines, XP and Vista. I was intrigued by Ubuntu and wanted to give it a try and it has been very trouble FREE except for file sharing on the home network.

From 9.10 Karmic machine I had folder/file visibility or access on network to......[INDENT]XP desktop - full access to Shared folders/files/subfolders , no problems.
[/INDENT][INDENT]Vista laptop - visibility of some folder names, Shared folders no file access and frequent error message indicating failure to mount etc etc. Public folders full file access. Subfolders no access intermittently.
[/INDENT]The Vista machine had a single user name (my daughter) log in (different than Karmic machine user name, me), and from Karmic I could SEE the Vista machine's varous shared/public folders.  Notably, "Users" folder with two subfolders ;Default and Public. Public was accessible at file level, but Default had no access (as expected ???). The laptop's single user "NAME" was not visible as a sub folder in Users folder. This becomes noteworthy later.

Since I had functionality of shared files on XP machine, I perceived problem as related to Vista file sharing or general setup.

**_Karmic Solution steps_**
I previously installed fixes 1 and 2 on thread below to synchronize Workgroup and machine names on network...about ten minutes to handle.
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

_**Vista Solution steps**_
I created a new user name on the WinVista machine to match the user name on the Karmic machine. Vista's Shared folder has the matching Karmic user name assigned as co-owner of Vista Shared file.

[U][B]Karmic Results
[/B][/U]When I start file access from Karmic (Places/Network/Windows Share/machine name) Karmic prompts via dialogue box after machine name is chosen.[INDENT]User - default is current KARMIC user (which now matches Vista machine Shared folder co-owner username)
Domain - I enter my Workgroup name
Password - VISTA machine password for user name above

[/INDENT]Now I have full access to Public and Shared flagged folders, AND most notably, when I access Users on the WinVista machine, it shows[INDENT]Default - still no folder/file access
Public - normal access
Active User Name (folder NOT previously visible)

NEWLY ADDED USER NAME is NOT visible which is expected since WinVista machine is running under original owner User Name (daughter) noted above.

Open subfolder for username, and SHARED folder is visible and accessible.

[/INDENT][U][B]Other issues
[/B][/U][INDENT]As other users noted, sometimes there is a hang up and no folders are displayed, blank window, or the processing icon keeps rotating.  Backing all the way out seems to reset the network path to a functioning path.

The problem above APPEARS to be related when I attempt to access a folder which is NOT share flagged and the appropriate file access denied message occurs. 

That is a separate problem to be solved another day based on help from people much more proficient than I for Ubuntu OS.
[/INDENT]Good luck.

---

