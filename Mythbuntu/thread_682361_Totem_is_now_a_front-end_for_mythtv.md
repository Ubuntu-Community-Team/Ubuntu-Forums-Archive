---
title: "Totem is now a front-end for mythtv?"
date: 2008-01-29
forum: Mythbuntu
---

### Post by ubnewbie2 on 2008-01-29
I just read  about Gnome 2.22's new features and a new plugin for Totem.  Could be useful?

```
Totem Makes Friends With MythTV, YouTube: 
While GNOME's movie player, Totem, is far from being a 
new project, in GNOME 2.22 are several enticing additions. 
Totem 2.22 features plugins for YouTube and MythTV.
 The YouTube plug-in allows you to search and browse 
YouTube.com video files all within Totem. The MythTV 
plugin for GNOME allows you to view recordings from a
 MythTV server as well as view live TV. We have 
especially enjoyed the MythTV plug-in and look forward to
 its continued development. Two other new Totem 
plug-ins are Publish and Tracker, which allows you to
 share your current playlist via HTTP and search for
 videos, respectively. The Totem 2.21/2.22 branch 
also contains other improvements and fixes for this
 movie player.
```

See [http://www.phoronix.com/scan.php?page=article&item=980&num=1](http://www.phoronix.com/scan.php?page=article&item=980&num=1)

---

### Post by superm1 on 2008-01-30
There are still a few requirements that need to be implemented for this to happen before Hardy.  In the current implementation, they are not all feasible due to licensing, but I'm talking with upstream about it.

Sounds pretty neat though eh? :)

---

### Post by ubnewbie2 on 2008-01-30
> **superm1 said:**
> There are still a few requirements that need to be implemented for this to happen before Hardy.  In the current implementation, they are not all feasible due to licensing, but I'm talking with upstream about it.

Sounds pretty neat though eh? :)

Yep =D>

---

### Post by McQuaid on 2008-02-02
I was under the impression that this is in for 2.20 so I was going to compile hardy's totem 2.21.90 for gutsy just to check this out.  So it's not currently in hardy but it is in current development version of gnome or neither?

First heard mention of it here, also mentions youtube functionality.

Saw the youtube plugin here:
[http://tecnocode.co.uk/?page=blog&action=view_item&id=63](http://tecnocode.co.uk/?page=blog&action=view_item&id=63)

Btw, is there any screens of totem using a mythbackend?  Does it behave like a normal frontend?  I'd be nice to see some pics to see it in action.

 [http://www.phoronix.com/scan.php?page=article&item=980&num=3](http://www.phoronix.com/scan.php?page=article&item=980&num=3)

---

### Post by superm1 on 2008-02-02
> **McQuaid said:**
> I was under the impression that this is in for 2.20 so I was going to compile hardy's totem 2.21.90 for gutsy just to check this out.  So it's not currently in hardy but it is in current development version of gnome or neither?

First heard mention of it here, also mentions youtube functionality.

Saw the youtube plugin here:
[http://tecnocode.co.uk/?page=blog&action=view_item&id=63](http://tecnocode.co.uk/?page=blog&action=view_item&id=63)

Btw, is there any screens of totem using a mythbackend?  Does it behave like a normal frontend?  I'd be nice to see some pics to see it in action.

 [http://www.phoronix.com/scan.php?page=article&item=980&num=3](http://www.phoronix.com/scan.php?page=article&item=980&num=3)

This isn't in hardy *yet.* gmyth  just entered NEW today.  [https://edge.launchpad.net/ubuntu/hardy/+queue](https://edge.launchpad.net/ubuntu/hardy/+queue)
After it is accepted by archive admins, gstreamer0.10-plugins-bad needs to be rebuilt against it (which the upload is in dependency wait for gmyth as I write this).
After that, gmyth has to be promoted to main, and then lastly totem can be built against it.

If you want to try it for gutsy, pull the source package from NEW, pull the upload that is in dep wait for the gstreamer plugins, and then pull totem, and add libgmyth-dev to the build dependencies.

I'll try to take some screenshots of what it looks like, but its basically a list of recordings on the right side.  When you open one up, it goes into streaming mode off the backend.  Skipping functionality isn't in it yet, so no comm skips or anything fun like that.

No GUI that I can see yet for controlling live tv other than giving it URLs that are myth://

---

### Post by superm1 on 2008-02-03
[http://mythbuntu.org/image/tid/9](http://mythbuntu.org/image/tid/9)
Screenshots ^

---

### Post by ubnewbie2 on 2008-02-03
Nice.    Look forward to it.

---

### Post by superm1 on 2008-02-19
The updates hit hardy as of today.  I'm working on getting them into debian too, so this should trickle around everywhere soon.

---

### Post by Lem on 2008-02-27
Does this plugin require an 8.04 mythbuntu backend? (rather than 7.10)

---

### Post by pHr34kY on 2008-03-14
> **Lem said:**
> Does this plugin require an 8.04 mythbuntu backend? (rather than 7.10)

I got it running off my 7.10 backend. Works a treat.

All I had to do was jump into gconf-editor and specify the IP address and password here:
[IMG]http://mythbuntu.org/files/images/gconf_editor_totem.preview.png[/IMG]

The automatic codec installer worked a treat. Correctly identified the required codec packages and installed them without issue.

The only problems I see are:
 - Video/Audio sync is off
 - No seeking
 - Deinterlace does not work
However I think these are more problems with the codec than the plugin (same problems when I play the mpg file directory from my recordings directory).

Also, I think the 'Configure' button in the 'Configure Plugins' dialog of Totem would be good place to add a GUI to configure backend login details so we don't need to use gconf.

---

### Post by funkydan2 on 2008-04-27
I've been trying to get this to work since updating to Hardy.

I have a mythtv frontend+backend box that I want to connect to.

I can connect to that box with mythtv-frontend on my laptop (and also using MythTVPlayer on some Windows machines).  However, I can't connect to it using the totem-plugin.  I've put in the IP address of the mythtv box through gconf-editor and the same username and password from the mysql.txt file on the laptop, but when I click the "Refresh" button in Totem, no programs show up.

I'm a little confused as to what the totem plugin is trying to connect to.  Is it trying to connect to the mysql database, or the mythtv backend?  The reason for the confusion is that the information in gconf seems to be referring to the mysql database (wanting to know database name, username & password) but I thought that port 6543 was the port for the MythTV backend, not the MySQL DB.

---

### Post by teet on 2008-04-27
What are the advantages of this totem plugin as compared to a regular mythfrontend?  Why wouldn't you just use mythfrontend?

-teet

---

### Post by funkydan2 on 2008-04-27
There's probably lots of reasons why you might use this, but for me it's the ease of having some recorded TV (like a music video show) playing in a small window whilst I do other stuff on my PC.

---

### Post by superm1 on 2008-04-27
The port it is referring to is for MySQL not the mythbackend port.

---

### Post by funkydan2 on 2008-04-27
So should the mythtv plugin be configured to connect to port 3306 (which is the port that mysql is running on on my myth box)?

The error I get when I run totem from the command line is:
```
** (totem:21683): WARNING **: [gmyth_scheduler_connect_with_timeout] Error while connecting to db
** Message: Couldn't connect to scheduler
```

---

### Post by superm1 on 2008-04-27
> **funkydan2 said:**
> So should the mythtv plugin be configured to connect to port 3306 (which is the port that mysql is running on on my myth box)?

The error I get when I run totem from the command line is:
```
** (totem:21683): WARNING **: [gmyth_scheduler_connect_with_timeout] Error while connecting to db
** Message: Couldn't connect to scheduler
```
Actually that was a pre-emptive naive response.  My mistake.

It is indeed the port it reads the recordings from.  It makes an implicit assumption then too that your MySQL is on 3306 and that you can remotely connect to it.

---

### Post by smbm on 2008-04-30
> **funkydan2 said:**
> So should the mythtv plugin be configured to connect to port 3306 (which is the port that mysql is running on on my myth box)?

The error I get when I run totem from the command line is:
```
** (totem:21683): WARNING **: [gmyth_scheduler_connect_with_timeout] Error while connecting to db
** Message: Couldn't connect to scheduler
```

Did you ever manage to fix this?

I'm getting the same error!

Anyone, any ideas?

---

### Post by funkydan2 on 2008-05-01
Nope.

Still not working, and I haven't got any leads.

Funny thing is, is that I had the totem-mythtv plugin working on an older laptop running the beta of hardy a month ago, but I've since given that computer away.  I wonder if something's broken in the totem package since then?

---

### Post by sceo on 2008-05-02
Yes I have the same problem.  My mythtv user who logs in to the frontend is named "cwells," so I've used the same password and granted that user access from all hosts in mysql.  I can connect as that user remotely directly to the database, but Totem is giving me the same error as above.  
> 
** (totem:22778): WARNING **: [gmyth_scheduler_connect_with_timeout] Error while connecting to db
** Message: Couldn't connect to scheduler


When I connect to the DB it takes a few second, and this "timeout" error pops up seemingly quicker.  Is there a way to increase the timeout value?  Maybe I just need to bump it up to 10-15 seconds, but I have no idea where I might do this.  

Incidentally I'm an 8.04 desktop running Totem, connecting to a Mythbuntu 7.10 frontend/backend box.  Also like mentioned above, the full-on frontend works fine... though I want, as superm1 mentions, to watch the recordings in a little window while I do other stuff on my computer.

If there are any logs I can provide, etc - let me know, I'm just not sure where to begin.

---

### Post by funkydan2 on 2008-05-02
> **sceo said:**
> Incidentally I'm an 8.04 desktop running Totem, connecting to a Mythbuntu 7.10 frontend/backend box.

I'm not sure, but does anyone know which version(s) of mythtv the totem plugin can connect to?

sceo, there is a chance that totem is only compatible with mythtv 0.21.  Gutsy had 0.20 in the repositories (though 0.21 is in backports).  Maybe you could see what happens if you upgrade mythtv to 0.21?

(Alternatively the opposite might be true as well, that the plugin is only compatible with 0.20!)

---

### Post by sceo on 2008-05-02
> **funkydan2 said:**
> sceo, there is a chance that totem is only compatible with mythtv 0.21

If so, then it's the opposite - because I have already upgraded to .21.

---

### Post by superm1 on 2008-05-03
> **funkydan2 said:**
> I'm not sure, but does anyone know which version(s) of mythtv the totem plugin can connect to?

sceo, there is a chance that totem is only compatible with mythtv 0.21.  Gutsy had 0.20 in the repositories (though 0.21 is in backports).  Maybe you could see what happens if you upgrade mythtv to 0.21?

(Alternatively the opposite might be true as well, that the plugin is only compatible with 0.20!)
It works with 0.21.  I've used it  for that :)

---

### Post by dakota34 on 2008-05-03
I can confirm that the myth plugin works with .20.  Just input the server IP and username and password via gconf-editor and it immediately showed me all my recordings after hitting refresh.  Totally awesome.  The Youtube plugin is great as well.  Automatic codec downloading as well.  Never was keen on totem but these features have made me reverse field.  Great stuff.:)

---

### Post by ahood on 2008-05-06
Unfortunately, this isn't working for me. I have a Mythbuntu system running on Hardy (Myth 0.21). I just upgraded my client workstation to Hardy as well. 

I have installed the totem-myth plugin and can select the Mythtv option from the dropdown list in totem. However, no recording show up.

I have configured the gconf-editor with the correct mythtv plugin information. Strangely, in gconfig-editor I don't see the "active" at the top of the totem --> myth plugin option. However, this plugin is active in totem. At least I think it is.

I have libgmyth0 installed but not libgmyth-dev if this makes a difference.

If anyone can point me in the right direction to get this working, I would be grateful.

Al

---

### Post by sceo on 2008-05-06
@ahood - are you getting the same error as the rest of us?  if you run totem from the command line and then select "MythTV Recordings" from the sidebar and hit "refresh," does console show you:
```

 WARNING **: [gmyth_scheduler_connect_with_timeout] Error while connecting to db
** Message: Couldn't connect to scheduler

```

---

### Post by ahood on 2008-05-06
Thanks for the quick reply. This is the output I get in the terminal when I click on the Refresh button and MythTV Recordings is clicked.

> ** (totem:7023): DEBUG: Init of Python module
** (totem:7023): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:7023): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:7023): DEBUG: Creating Python plugin instance


The above output occurs when I run totem as a plain user.

However, the output below appears when I run 'sudo totem'.

> 
** (totem:7064): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
** (totem:7064): DEBUG: Init of Python module
** (totem:7064): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:7064): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:7064): DEBUG: Creating Python plugin instance

** (totem:7064): WARNING **: [gmyth_scheduler_connect_with_timeout] Error while connecting to db
** Message: Couldn't connect to scheduler

** (totem:7064): WARNING **: [gmyth_scheduler_connect_with_timeout] Error while connecting to db
** Message: Couldn't connect to scheduler
** (totem:7064): DEBUG: Finalizing Python plugin instance


In the configuration editor for totem --> plugins --> totem_myttv, I have the following options...

> address  192.168.0.123
database mythconverg
password
port     6543
user     mythtv


The option 'active' with a checkmark does not appear in the configuration editor.

It isn't exactly clear whether the password should be the mysql database password or user password. However, it doesn't matter because it doesn't work using either password.

> **sceo said:**
> @ahood - are you getting the same error as the rest of us?  if you run totem from the command line and then select "MythTV Recordings" from the sidebar and hit "refresh," does console show you:
```

 WARNING **: [gmyth_scheduler_connect_with_timeout] Error while connecting to db
** Message: Couldn't connect to scheduler

```

---

### Post by ianc on 2008-05-08
@ahood - I had the same or similar issue - have you looked at this:

[http://ubuntuforums.org/showthread.php?p=4904470](http://ubuntuforums.org/showthread.php?p=4904470)

That fixed it for me.


At least, it fixed it to the extent that I'm now seeing the same "Couldn't connect to scheduler" error as other posters. But I suppose it's progress of a sort...

---

### Post by BatPenguin on 2008-05-10
What codecs do you have to have installed for this to work? I see my recordings but I get a "Totem could not handle the file XXXX.nuv, There is no input plugin to handle the location of this movie" error. I'm using totem xine. 

I've had a lot of problems with Totem previously (mainly with Dolby sound etc. sound issues and codec things) so I thought I'd ask before messing everything up with trying to install every codec I find...

Edit: Using Hardy, of course, no problems with seeing recordings in the list or watching them under Myth.

---

### Post by funkydan2 on 2008-05-10
@BatPenguin - when I had this working (in a pre-release version of hardy on a different computer) I was running totem with the gstreamer backend and it automatically noticed the lack of the codec and prompted to install it.  Is there any reason why you're using totem-xine and not totem-gstreamer?

---

### Post by BatPenguin on 2008-05-11
> **funkydan2 said:**
> @BatPenguin - when I had this working (in a pre-release version of hardy on a different computer) I was running totem with the gstreamer backend and it automatically noticed the lack of the codec and prompted to install it.  Is there any reason why you're using totem-xine and not totem-gstreamer?

Thanks for the reply. Yes, there is actually a reason: I've been having problems with Totem-gstreamer ever since Gutsy, and it still doesn't seem to work. The problem is that when playing files (specifically, using Xv which is needed for smooth playback), the colors get all messed up...everything turns to purple. There's some bug reports about simlar things (although with ATI cards, I have an Nvidia) but I haven't been able to solve it - but since totem-xine works just fine, I've actually not given much thought to this and I just use totem-xine.

So yes, if anybody is using this with totem-xine, I'd like to hear how they get .nuv files to show in Totem? I gave totem-gstreamer a quick try last night and saw the files playing in glorious purple hues so I guess I'll dive into solving that one if it seems like totem-xine can't be used for this. I always thought it's pretty much the same whether you use gstreamer or xine and both would support all codecs but I guess not.

---

### Post by BatPenguin on 2008-05-11
Alright, just a follow-up: I did end up doing a reinstall of totem-gstreamer and unistall of totem-xine, and somewhere during that uninstallation it seems like I managed to get rid of the purple hues problem finally. So now it works....or "works", I'm getting buffering pauses even with buffering set to 20 seconds in gconf-editor. Anybody else have buffering problems watching the Myth recordings? Seems very odd, this machine has both backend and frontend so there's no network issues or anything...very strange.

---

### Post by Dilligaf on 2008-05-11
I get the same pauses every 20 seconds, strange thing is if I browse to the file and play it that way it plays fine.

Mike

---

### Post by Nikas on 2008-05-14
I can't select the plugin in totem. Its not in the list.
I can see the settings in gconf-editor but not in totem... what can i do?

---

### Post by funkydan2 on 2008-05-14
@Nikas

You need to install 'totem-plugins-extras' through your favourite package manager (synaptic, aptitude ...)

---

### Post by Nikas on 2008-05-14
> **funkydan2 said:**
> @Nikas

You need to install 'totem-plugins-extras' through your favourite package manager (synaptic, aptitude ...)

Thanks. The name was "totem-plugins-extra" and now it works.

---

### Post by funkydan2 on 2008-05-17
I just got a update to the package 'libtotem-plparser10' (it came through the hardy-updates repository I think, v 2.22.3-0ubuntu2) and now it works!

---

### Post by sceo on 2008-05-18
> **funkydan2 said:**
> I just got a update to the package 'libtotem-plparser10' (it came through the hardy-updates repository I think, v 2.22.3-0ubuntu2) and now it works!

I just got the same update, but it still doesn't work... which user are you using in gconf-editor... your user or user "mythtv?"

---

### Post by ubnewbie2 on 2008-05-18
Has anyone found the definitive fix for the error :-

```
** (totem:15410): WARNING **: [gmyth_scheduler_connect_with_timeout] Error while connecting to db
** Message: Couldn't connect to scheduler

```

I am still getting this

---

### Post by smbm on 2008-05-18
> **funkydan2 said:**
> I just got a update to the package 'libtotem-plparser10' (it came through the hardy-updates repository I think, v 2.22.3-0ubuntu2) and now it works!

It didn't work for me either.

I am no longer getting this though:

```
** (totem:15410): WARNING **: [gmyth_scheduler_connect_with_timeout] Error while connecting to db
** Message: Couldn't connect to scheduler

```

---

### Post by funkydan2 on 2008-05-18
> **sceo said:**
> I just got the same update, but it still doesn't work... which user are you using in gconf-editor... your user or user "mythtv?"

I think the user is the **database user** for the mysql database.  By default I think that it is 'mythtv'.

---

### Post by sceo on 2008-05-18
Hey all -

I was getting pretty frustrated, so I rolled up my sleeves.  What did I learn?  Trust your gut.  My hunch was that simply the database connection was timing out.  IT WAS.

From Synaptic I installed libgmyth0-dev (and all the dependencies it wanted), then I went to sourceforge, and downloaded the source code for gmyth.  I waded through the code trying to find a #define for the timeout value.  I couldn't seem to find it, so went with a little brute force, and in gmyth_query_connect_with_timeout (gmyth/gmyth_query.c) I overrode the "guint timeout" parameter by setting a higher timeout (30 seconds instead of somewhere in the world where I thought I saw a default of 10).

```

gmyth_query_connect_with_timeout(GMythQuery * gmyth_query,
                                 GMythBackendInfo * backend_info,
                                 guint timeout)
{
    timeout = 30;
...
}

```

I rebuilt gmyth with "./configure --enable-debug --prefix=/usr" and while it initially still wasn't working, that was because I was getting "access denied" DB errors (as it turns out, in all my mucking with the gconf-editor settings, I set the wrong password.  I can now officially confirm that YES, it's looking for the DATABASE user name and password, found in your "general settings" from your mythtv frontend).

SO...

I guess at least MY solution to the connection timeout error is to increase the timeout.  (1) is it possible to make the default timeout longer?  (2) is it possible to add another gconf-editor option to allow a user to specify the db timeout?  

Is this outside of the realm of these developers?  I'm lost at where to go next with this info, so I'm hoping someone else in the forum can take it from here or provide me with the know-how to move this forward.

---

### Post by smbm on 2008-05-25
I finally got the plugin working.

When I try and play something back though I don't get any sound.

I've installed **all** the gstreamer plugins.

Any ideas?

---

### Post by axelsvag on 2008-05-30
Has someone found a solution to the 20 s buffering problem?

---

### Post by smbm on 2008-06-02
> **smbm said:**
> I finally got the plugin working.

When I try and play something back though I don't get any sound.

I've installed **all** the gstreamer plugins.

Any ideas?

Anyone?

Any help at all?

Does it work for you?

---

### Post by nickrout on 2008-06-23
> **axelsvag said:**
> Has someone found a solution to the 20 s buffering problem?

I got this working last night, but I too have this buffering  problem. I had put it down to my dodgy wireless network, so will try it wired tonight.

And for the record, it is clearly the database user and password that the config wants. Those can be found in a working front end from ~user/.mythtv/mysql.txt (where user is the user that runs mythfrontend).

And if you want to watch mythtv in a window there are other ways besides this. mythtfrontend will run in a window. You can also access recorded TV via uPnP so you could run djmount and then play the files from there.

---

### Post by sceo on 2008-06-23
> **nickrout said:**
> And if you want to watch mythtv in a window there are other ways besides this. 

Also, the illustrious MythWeb!

---

