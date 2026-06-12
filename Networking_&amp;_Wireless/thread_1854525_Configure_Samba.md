---
title: "Configure Samba"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by YaKillaCJ on 2011-10-04
How do I setup Samba. Im no linux newbie but I just cant figure out how to do this right. So please dumb it down for me. I mean DUMB (Step by Step). Or at least point me in the right direction.

I want to create a windows share. I have it configured on win7 nicely.
The kinda setup I want is simple I think.

Music Folder (Everyone on same network can Read/Access it. No1 can Write in it without my Login/Pass)
Video Folder (Requires my login to Access it)
Download Folder (Requires my login to Access it)

I would prefer if all folders can be seen. Again thanx in advance.

I wanna use it for various things. Other Computers, Xbox, Android Phone (ES File Manager App to be specific).

Ubuntu 11.04 64Bit

---

### Post by garvinrick4 on 2011-10-04
Install a GUI app for samba as per below. (IN all examples I am rick use your own user name)
If you want to make your music directory  a share:
/home/rick/Music 
if you want to make another directory in /home lets say Shared in your /home directory.
```
sudo mkdir /home/rick/Shared
```Then you can make it a samba share.
To give rick permissions for that directory:
```
sudo chown -R rick:rick /home/rick/Shared
```is the path, always use the file system path and will share. All shares you make in GUI tool
will show up on bottom of the Samba config file.
```
gedit /etc/samba/smb.cfg
```to see in a text editor.

Here is GUI app to install samba shares.
```
sudo apt-get install system-config-samba
```In network will be under "Windows Workgroup" so must set your Windows shares up
to see from Ubuntu.
Samba works out of box in Ubuntu to see Windows workgroup and windows shares.
Setting up Samba shares is so other boxes may see your Shares in Ubuntu box.
[COLOR=Red]##There is a pdf book in my signature worth downloading and reading and keeping handy is free.[/COLOR]
> Music Folder (Everyone on same network can Read/Access it. No1 can Write in it without my Login/Pass)
Video Folder (Requires my login to Access it)
Download Folder (Requires my login to Access it)
I would prefer if all folders can be seen. Again thanx in advance.
 You set permissions in when you make your shares.

---

### Post by jerrylamos on 2011-10-04
Tried system-config-samba and got:

```
(system-config-samba:3032): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 44, in <module>
    import mainWindow
  File "/usr/share/system-config-samba/mainWindow.py", line 30, in <module>
    import gtk.glade
ImportError: No module named glade
jerry@Aspire-5253:~$ 

```
Narwhal shares home fine with other pc's on my home network.
Ocelot has never been able to access files on other pc's.
Narwhal can see Ocelot O.K.

I wrote a launchpad bug on this way back when.

?

Thanks, Jerry

Jerry

---

### Post by garvinrick4 on 2011-10-04
> Narwhal shares home fine with other pc's on my home network.
Ocelot has never been able to access files on other pc's.
Narwhal can see Ocelot O.K.
I wrote a launchpad bug on this way back when.
 
Your problem is a 11.10 Oneiric bug a Beta version of Ubuntu is that correct. So others using Ubuntu not as a Oneiric tester can ignore your post is that correct?

---

### Post by jerrylamos on 2011-10-04
> **garvinrick4 said:**
> Your problem is a 11.10 Oneiric bug a Beta version of Ubuntu is that correct. So others using Ubuntu not as a Oneiric tester can ignore your post is that correct?

This is a Oneiric Ocelot version updated as of Oct 4.  Do note it is scheduled for release on Oct 13.  My opinion, no chance of a fix.  Keep Narwhal partition around, it works.

Jerry

---

### Post by capscrew on 2011-10-05
> **jerrylamos said:**
> This is a Oneiric Ocelot version updated as of Oct 4.  Do note it is scheduled for release on Oct 13.  My opinion, no chance of a fix.  Keep Narwhal partition around, it works.

Jerry

Actually you (Jerry) have asked this before and it has been explained. You need to provide name services for consistent browsing of shares.  This has always been this way.  Configure a netbios name and set the name resolve order to use bcast first.  

There is no "bug" with Samba or Ubuntu.  You are just muddying the water. BTW -- Until the version is released it is beta.  Even if the release is tomorrow.

---

### Post by capscrew on 2011-10-05
> **jerrylamos said:**
> Tried system-config-samba and got:

```
(system-config-samba:3032): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 44, in <module>
    import mainWindow
  File "/usr/share/system-config-samba/mainWindow.py", line 30, in <module>
    import gtk.glade
ImportError: No module named glade
jerry@Aspire-5253:~$ 

```
Narwhal shares home fine with other pc's on my home network.
Ocelot has never been able to access files on other pc's.
Narwhal can see Ocelot O.K.

I wrote a launchpad bug on this way back when.

?

Thanks, Jerry

Jerry

This is a **system-config-samba** problem.  This is nothing more than a python script.  It has nothing to do with Samba or Ubuntu.  Specifically this is a missing Python module (Glade)```
ImportError: No module named glade
```

---

### Post by jerrylamos on 2011-10-05
> **capscrew said:**
> Actually you (Jerry) have asked this before and it has been explained. You need to provide name services for consistent browsing of shares.  This has always been this way.  Configure a netbios name and set the name resolve order to use bcast first.  

There is no "bug" with Samba or Ubuntu.  You are just muddying the water. BTW -- Until the version is released it is beta.  Even if the release is tomorrow.

Well, capscrew, Narwhal, Maverick, Lynx, ... share fine.  I didn't have to do a "Configure a netbios name and set the name resolve order to use bcast first." on any of the previous Ubuntu's I've run all the way back to Dapper Drake Beta.

Now if you don't like feedback from us, just ignore comments on Alpha's and Beta's from anyone but developers....us users do share helpful info between ourselves on this forums...

Jerry

---

### Post by capscrew on 2011-10-05
> **jerrylamos said:**
> Well, capscrew, Narwhal, Maverick, Lynx, ... share fine.  I didn't have to do a "Configure a netbios name and set the name resolve order to use bcast first." on any of the previous Ubuntu's I've run all the way back to Dapper Drake Beta.

Now if you don't like feedback from us, just ignore comments on Alpha's and Beta's from anyone but developers....us users do share helpful info between ourselves on this forums...

Jerry

I believe there is a section for Alpha and Beta testing.  This is not it.  I don't see how complaining is (as you say) *helpful*.

---

### Post by garvinrick4 on 2011-10-05
> I believe there is a section for Alpha and Beta testing.+1 with capscrew:
@ jerrylamos
 I was attempting to help a user with Samba shares how could your post's
in anyway contribute to this Thread. Your post certainly belonged in development
release Oneiric 11.10 and not in this thread. Being considerate of others is part
of the Ubuntu Code on Conduct, I believe you have failed in this instance and have
nothing more than attempted to confuse Newcomers reading this Thread to our distribution and Forum.
Not a moderator, just one users opinion.

---

### Post by jerrylamos on 2011-10-05
Found the problem as suggested by capscrew.

Narwhal, Meerkat, Lynx, ... all default to 
```
name resolve order =  bcast .......
```
while Ocelot defaults to what I don't know.  Searches for minutes, never triest bcast, and fails to find anything.

So the workaround is to set bcast first in the name resolve order and remove the ; from the beginning of the line.  

Ocelot fails same way on netbook, notebook, tower.  Previous Ubuntu's no problem.

I'm fine, but my opinion is the new user won't find this fix - no help if the object is to increase Ubuntu penetration.

I'll add a comment to the launchpad bug when I next start the tower.

Jerry

---

### Post by capscrew on 2011-10-05
> **jerrylamos said:**
> Found the problem as suggested by capscrew.

Narwhal, Meerkat, Lynx, ... all default to 
```
name resolve order =  bcast .......
```
while Ocelot defaults to what I don't know.  Searches for minutes, never triest bcast, and fails to find anything.

So the workaround is to set bcast first in the name resolve order and remove the ; from the beginning of the line.  

Ocelot fails same way on netbook, notebook, tower.  Previous Ubuntu's no problem.

I'm fine, but my opinion is the new user won't find this fix - no help if the object is to increase Ubuntu penetration.

I'll add a comment to the launchpad bug when I next start the tower.

Jerry

As I have said many times:  The basic name services for a LAN should be in place BEFORE you configure Samba.  If they are not set then one needs to configure each Samba host individually.

The Samba default has always been```
name resolve order = lmhosts host wins bcast 
```If your earlier Ubuntu installs now have *bcast *first then you have modified them some time in the past.  These are not workarounds -- Samba is flexible enough to fit into most environments.  All we are doing here is creating what Windows calls a B-node.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://support.microsoft.com/kb/119493") for more info.

The new  user usually ends up here, asking for help.  And we are glad to help.  I believe  @garvinrick4 and my opinion is the same:  Hijacking a thread to provide useless information is not valuable in any sense.  Opinions are great in some contexts  -- not here.  The OP was asking for expertise not complaints.

If you want help making your network hosts have consistent name services, then start a new thread.  If it has the word *samba* or *smb* or *cifs*, I'll find it and try to help.

---

### Post by jerrylamos on 2011-10-05
I install frequently from USB or CD and do not modify samba lines such as:

: name resolve order = hoast lmhosts wins bcast

which as you can see starts with a semicolon.  

With or without the semicolon Ocelot doesn't ever complete name resolve order successfully.

Whatever Narwhal, Meerkat, Lynx LTS do with that line as is, starting with a semicolon, works fine.  I presume these Ubuntu's have some internal default.

Ocelot fails with exactly the same "as is out of the box" setup on my notebook, netbook, tower.

If I put bcast first on Ocelot, then it works.  This was not necessary in Narwhal, Meerkat, Lynx LTS, ... all of which required no changes.

Absolutely the only change I do on Samba or smb.conf or samba setup in any way is to change the WORKGROUP name to my local one, and add home folder sharing at the very bottom of smb.conf.

Jerry

---

### Post by capscrew on 2011-10-05
We are way OT here, If you want to discuss this in detail, open a new post or PM me.

I will respond on last time to this post.

> **jerrylamos said:**
> I install frequently from USB or CD and do not modify samba lines such as:

: name resolve order = hoast lmhosts wins bcast

which as you can see starts with a semicolon.
The semicolon comments out the line.  At this point Samba uses its own internal default which is: *name resolve order = lmhosts host wins bcast*> 

With or without the semicolon Ocelot doesn't ever complete name resolve order successfully.
Uh huh...> 

Whatever Narwhal, Meerkat, Lynx LTS do with that line as is, starting with a semicolon, works fine.  I presume these Ubuntu's have some internal default.
Ubuntu (as a disto) has no defaults for Samba.  The package manager (most probably from Debian) may have added the semicolon commented line though.> 

Ocelot fails with exactly the same "as is out of the box" setup on my notebook, netbook, tower.

If I put bcast first on Ocelot, then it works.  This was not necessary in Narwhal, Meerkat, Lynx LTS, ... all of which required no changes.
So what does you comment here really mean?  Are you misquoting yourself?> [B][COLOR="Magenta"]Narwhal, Meerkat, Lynx, ... all default to[/COLOR]
```
name resolve order =  bcast .......
```

[/B]> 

Absolutely the only change I do on Samba or smb.conf or samba setup in any way is to change the WORKGROUP name to my local one, and add home folder sharing at the very bottom of smb.conf.

Jerry
Arguing won't make it any better.  You can do as you like.

---

