---
title: "File Sharing Confusion"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by DrHow on 2009-06-02
I have 3 computers on a LAN: 1 running Windows 98 and 2 running Ubuntu 9.04.  I have not used file sharing before, but I wanted to enable it between the two Ubuntu computers. I followed the advice I found here: [http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/)
That advice is similar to what I found elsewhere.

I tried to set up file sharing by doing the same thing on both Ubuntu computers at the roughly the same time.  Things seemed to proceed as expected.  As I set it up, there was a time when one of the Ubuntu computers could see itself, the other Ubuntu computer, and the Windows computer.  The other could only see itself and the Windows computer.  (This is in the Network File Browser you get when clicking on Network in the Places menu.)  I was actually surprised by that level of success since the installation of Samba had said that I needed to restart my 'session'.  I had hit the "restart" button, but it did not do anything discernible.  I figured I still needed to reboot both computers.  After I did that, neither could see anything but the Windows computer - the sharing I was not even trying to enable!  (It does not work yet, because I have not set it up on the Windows end.)

I made the "Public" folder in my home folder shareable from both computers.  I even put some test files into those shareable folders.  I did the smbpasswd thing for my account on both.  I have checked to see that Samba is enabled in System -> Services.  It is.  However, when I look at my process list, I do not see "samba", or "nmbd", or any "smb*".  If it should appear, then what might be causing it to be absent?

Another thing which concerns me is that I also found advice referring to a "Network Settings" dialogue.  I can't find that.  I have System -> Preferences -> Network Connections; but that does not do much nor does it appear pertinent.  (It is about making a connection, not using one.)  I have System -> Administration -> Network Tools; but those tools seem more relevant on the WAN, and they don't pertain to file sharing directly anyway.  So is "Network Settings" supposed to exist anymore in 9.04?  If so, what is the name of the program that produces that dialogue?  (and why is it not already on my menu?)

After booting up, when I click on "Network" in the Places menu the first time, it takes a very long time for the Network File Browser to get started.  (I'd say on the order of 1 minute.)  Is that normal?  After that it pops up quickly.  When I click "Reload", nothing seems to happen.  (I figured that would cause it to look for other instances of samba that it could connect to.  When I tried to find documentation on what "Reload" is really supposed to do, I was thwarted.  "Help" in the Network File Browser just sends you to the documentation for Nautilus, and I did not see anything about "Reload" there.  When I tried a search on "Reload", I got a uselessly long list of references to the word "reload" anywhere in the whole system - not just Nautilus-relevant.  How are you supposed to narrow such a search to a single document?)

I suspect that the most likely explanation of my woes is that the only time samba was actually running on either machine was immediately after it got installed, and that it is no longer being started after a reboot.  But, since samba appears to be enabled in Services, I don't know what to do about this.  I lack the experience to be much of a detective into this problem.

Any help or pointers would be appreciated.  I did not think this would be hard.

Is this significant?:

```
d@Aida:~$ samba --help
The program 'samba' is currently not installed.  You can install it by typing:
sudo apt-get install samba4
bash: samba: command not found

```

The /etc/samba/ directory certainly exists.

Here is some potentially relevant info:

```

d@Aida:~$ smbtree
WORKGROUP
	\\DELTA          		Delta server (Samba, Ubuntu)
timeout connecting to 208.69.32.132:445
timeout connecting to 208.69.32.132:139
cli_start_connection: failed to connect to DELTA<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
	\\AIDA           		Aida server (Samba, Ubuntu)
		\\AIDA\public         	
		\\AIDA\d              	Home Directories
		\\AIDA\IPC$           	IPC Service (Aida server (Samba, Ubuntu))
		\\AIDA\print$         	Printer Drivers
		\\AIDA\homes          	Home Directories

```

I am reminded that I also enabled my entire home directories via the smb.conf file in /etc/samba.  That was just another try to get things working.  I don't really need that.  When I run smbtree on Delta, I get basically the same report, reversing the roles of Aida and Delta, and including the timeouts.

---

### Post by theDaveTheRave on 2009-06-02
DrHow

have you checked out this [thread]("http://ubuntuforums.org/showthread.php?t=202605") from StormBringer, it got me up and running with samba in no time, and it is ubuntu orientated so should work straight off ;) 

Also that thread will be your best bet for troubleshooting as the "samba guru's" all seem to hang out there!

Very quickly however....

You get the ability to "share folders" automatically from within nautilus (I assume this is how you shared your folders originally), but I'm not sure if you need to have samba or not?

I recall from personal experience that it was a little "problematic" and you need different things if you just want to "view" shared folders, or if you want to server your folders elsewhere.

My suggestions.

If one of your ubuntu boxes has the "big" HDD then use that as your main file share, and point the windows and other ubuntu box to it. You should then only need to install the samba server on that single box, and "viewing" shouldn't be an issue from either.

You could then <mount> that share automatically into your second ubuntu box using fstab (see Bodhi.Zazen's thread on fstab [here]("http://ubuntuforums.org/showthread.php?t=283131")).


hope that helps... if only a little bit!

david

---

### Post by Iowan on 2009-06-02
Ubuntu comes with samba-client already installed, but to share files FROM ubuntu requires installing the server (called simply **samba** in Synaptic).  [Another]("https://help.ubuntu.com/community/SettingUpSamba") help page that may be useful.

---

### Post by dmizer on 2009-06-02
To solve your network browsing issue (places > connect to server), please see the 6th link in my sig.

---

