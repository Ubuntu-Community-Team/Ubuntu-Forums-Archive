---
title: "Problem with Xbox 360 connecting to ushare"
date: 2008-08-28
forum: Multimedia Software
---

### Post by Saiing on 2008-08-28
So I downloaded ushare, configured it, ran it.  My Xbox 360 can see it in it's 'computers' list, but when I click I just get the "connecting..." message which times out after about 20 seconds.

I had exactly the same problem with twonky media.  The Xbox could see the server, but couldn't connect to it.  Just timed out.

I really can't figure out what's wrong.  Most other threads I see on the subject seem to suggest that most people just download, install and it magically starts working.

(I also have connect 360 running on my Mac which sits next to the Ubuntu box, and is plugged into the same router, but works like a dream, so it's not a problem with the 360).

Can anyone offer any advice?  When I start up ushare I get an error about eth0 (which is working fine because I'm running a private web server on this machine):

Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.0.4:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/rich/Videos
Found 2 files and subdirectories.

---

### Post by nhasian on 2008-09-02
Hello Saiing,

i've been very happy with ushare.  after installing it i had to edit the file /etc/ushare.conf

you need to specify which interface to use (wlan0 for me), what directory you would like to use (no spaces in directory names), and finally set the xbox360 switch to YES.

my only issue with ushare is that even though i see the ushare start successfully on bootup, it doesnt work until i manually start it with the command 
```
sudo /etc/init.d/ushare start
```

its probably some permission thing.  i'm such a noob :)

---

### Post by Saiing on 2008-09-03
Yep already done all that (you can more or less tell from the startup messages) but thanks for the reply.  What I'm struggling to understand is why the Xbox can see ushare (it shows up in the list of available media capable computers on the 360) but can't connect to it.  Sounds like a networking issue, but there's nothing I can see on my network that would be causing it.  I'm still leaning toward the "eth0 is down" message being somehow related (even though it's working perfectly).

---

### Post by Slowspeed on 2009-01-17
> **Saiing said:**
> Yep already done all that (you can more or less tell from the startup messages) but thanks for the reply.  What I'm struggling to understand is why the Xbox can see ushare (it shows up in the list of available media capable computers on the 360) but can't connect to it.  Sounds like a networking issue, but there's nothing I can see on my network that would be causing it.  I'm still leaning toward the "eth0 is down" message being somehow related (even though it's working perfectly).


Saiing,

I actually have the video streaming from ushare to my xbox 360.
My setup is as follows:

1. Ubuntu v.8.10 - gnome desktop
2. Ushare v 1.1a from the Ubuntu repository I just used apt to install the package. I did not compile source code like some other people were recommending.
3. xbox 360 with the latest software.

UShare.conf
I followed different instructions but after several changes it worked on the following:
my ushare.conf file:
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49153

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/user/Videos,/home/user/Music

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=

#EOF

As you can see I removed the ethernet interface variable. 

Next. I started ushare with the following command:

ushare -x

I also verified that UFW is not loaded.

It then reported as usual that my ethernet interface was down, but it kept going and started.

Then I went and turned on my xbox and there it was listed as Ushare.
I am streaming an avi and it is working well.

[/LIST]

---

### Post by nealien on 2009-01-30
i was having this same problem.  i copied ure conf file and followed ure instructions and i got it working.  my only problem now is that it cannot see my media.  i have all my files saved on a different hard drive that has an ntfs partition.  in the conf file i put the media location as

 /media/noobaliciousstorage_

no joy

then i thought since it was my g: drive i would just put that.  but g: didn't work either.  how do i list the media location?

don't make fun of my storage drives name lol  ;)

---

### Post by nealien on 2009-01-30
bump!  :)

---

### Post by hexdsl on 2009-01-30
1 wtf does 'bump' have to do with anything? 
2 have done this but need way to start it with session.
3 thanks for all teh help, even though its not sorted im well on the way, i can feel it

---

### Post by canuck_1987 on 2009-01-30
Hey i was having problems with uShare to until I came accross this post. I used the same set-up as Slowspeed but as i'm using eth1 i kept that part in, and it worked :D. Thanks for your help (config below for details).


/etc/ushare.conf:
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=**uShare**

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=**eth1**

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=**49153**

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
**EDIT**
USHARE_DIR=//home/tb227/Desktop/uShare

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
ENABLE_WEB=**yes**

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=**yes**

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=**yes**


Then i used **ushare -x** & to start the server up, i still got the:
'Interface eth1 is down.
Recheck uShare's configuration and try again !'

message but it seems to be working still
 

Basically I think the problem I was have was the network port, most of the rest is the same as i used before (apart from lowercase 'yes').
Sorry its a bit incoherent I'm tired :), hope this helps...

//EDIT//
Also I don't think the config file allows quotes of any kind - I just get a no such directory message.

---

### Post by nealien on 2009-01-30
canuck,

the problem i'm having is that it when it searches the directory for media it says that it can't find anything.  i don't understand why cus i know it's there.  i noticed in your config file u have 

//media/sda3/ftp

this confuses me.  first, the two //.  do i need two slashes?  second, the sda3 thing bothers me too.  is that how it's supposed to be written?  i have three hard drives in my comp.  i have my c: drive which is my windows drive, z: which is my linux drive, and g: which is my storage drive.  so what do i write there?  i have everything else working, just no media making it the 360.

---

### Post by canuck_1987 on 2009-01-30
Before I start I must mention I've updated my script since then..
The line:
"USHARE_DIR=//media/sda3/ftp,"
is now:
"USHARE_DIR=//home/tb227/Desktop/uShare" (explained later)

First off the two slashes indicate thats the address of the directory from the root folder (the base of the Linux file system)- this might not be needed but I wanted to make sure that the script was trying to load the right folder.

Secondly from my understanding the C:/ Z:/ etc. are the names of the drives under windows? (could very well be mistaken) and under Ubuntu they're listed by their connection to your motherboard (I think mine is sda3 because it uses a the 3rd SATA port in SATA port bank A)

What I'd suggest is firstly go into the 'media' folder ('//media/') < this is where all of the CDROMs HDDs etc. are mounted (is the equivalent of My Computer in Windows). Once there find out where your files are in relation to the root directory you can use that as the address in 'USHARE_DIR='.

Mine is '//media/sda3/ftp' which in Windows is F:/ftp (so //media/sda3/ is equivalent to F:/ - in my case).

Finally as a side note I've also noticed that the script (again from my experience) doesn't seem to like more then one argument in **'USHARE_DIR='** and also won't acknowledge any address with spaces in it - you just get the message  **"scandir: No such file or directory"**. 

The way I got round this was to put create a link to the folders I wanted to my XBox 360 to have access to (right click on the folder and click 'Make Link') and then copied all the links into a folder in my home directory (**//user/user_name/folder_name**). This enables you to change what folders the XBox has access to without changing the script every time by just adding or removing the link files. This should enable your XBox  to have access to those folders (even ones with spaces in the directory address) as links open just like folders do. This also means you can separate out your media into different folders, like have one link to music, video, movies, a TV show, etc.) 
 
So basically I have a folder on the desktop of my Ubuntu machine (Address://home/tb227/Desktop/uShare) which has a series of link files in it that link to the media. Then in the script I use the line "USHARE_DIR=//home/tb227/Desktop/uShare" to point to that folder, and so can link to the media I want.
Its a round about way of doing it, but it seems to work (I've been watching things on my Xbox most of the night).

I hope this helps, and that I've explained it well enough.

BTW If this doesn't work the first thing to check will be that the script is pointing to the correct folder. The second thing will be that the links themselves work, after that ask and I'll see what I can do.

PS. (If anyone knows any better please correct me, I'm not 100% with Ubuntu yet (still a windows person mostly I'm afraid).

---

### Post by nealien on 2009-01-31
thank you for your help.  i just can't seem to get it working no matter what i do to the conf file.  it works but it doesn't see the directories.  I KNOW i'm typing it in right.  i even put a movie in a different folder on my linux drive and pointed it to that, and it still doesn't work.  i'm giving up on ushare in favor of something else.  i just dunno what else there is besides this and twonky.

---

### Post by Slowspeed on 2009-02-02
> **nealien said:**
> thank you for your help.  i just can't seem to get it working no matter what i do to the conf file.  it works but it doesn't see the directories.  I KNOW i'm typing it in right.  i even put a movie in a different folder on my linux drive and pointed it to that, and it still doesn't work.  i'm giving up on ushare in favor of something else.  i just dunno what else there is besides this and twonky.

Nealien,
I am not sure why your path name is not working correctly in your .conf file. However, I found another alternative to Ushare. I have been using
Vuze ver. 4.1 to download media for about a week. I downloaded and installed from [http://www.vuze.com/app](http://www.vuze.com/app)
Vuze used to be called Azureus. The version in the Ubuntu repository is version 3.1 so I went with the newer version and found that it has a built in Upnp server.

I am not I repeat not an expert using Vuze.
The steps I did were pretty straightforward.

1. Downloaded package from the [http://www.vuze.com/app](http://www.vuze.com/app) link.

2. Unpacked in my Home folder. 

3. Click on the Vuze.bin and it will prompt if you want to run say yes.

4. Vuze puts an Azureus folder in you home directory. This is where it stores the files that you download.

5. From the Vuze menu select "Tools" then select "Plugins" you will see UPnp listed. Select it and click on enable UPnp server. It also provides a Wiki for your reference.

After, this I turned on my xbox360 and Vuze was truly plug and play.

Hope this helps give you an alternative.
Slowspeed.

---

### Post by smcmulli on 2010-06-14
I know this is a very basic step, but it worked for me as I was having the same issues as others have explained earlier in this thread, after I made changes to my ushare.conf file I had to stop uShare and then start it again, and then it worked fine and I was able to connect to my 360.

```
sudo /etc/init.d/ushare stop
sudo /etc/init.d/ushare start
```

---

### Post by Snoman314 on 2010-06-14
> **smcmulli said:**
> I know this is a very basic step, but it worked for me as I was having the same issues as others have explained earlier in this thread, after I made changes to my ushare.conf file I had to stop uShare and then start it again, and then it worked fine and I was able to connect to my 360.

```
sudo /etc/init.d/ushare stop
sudo /etc/init.d/ushare start
```

What version of ubuntu are you using? I've seen others suggesting that there is something with 10.4 that has broken ushare.

---

### Post by skript_teaze on 2010-07-13
This might be a dumb question...

I installed ushare via apt and created a config with the auto config tool. I ran this script to start it automatically at boot:
update-rc.d ushare defaultsI then edited the config by creating a GKSudo loader and going to the file in the etc. folder. This is the content of the .conf file....

# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=wlan0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=yes


As you can see I am trying to share the Home folder to my 360. (I will change the folder to a specially set up share folder with links once I get ushare working.)

I am trying to use Ushare to Xbox 360 over wireless, all of the instructions I have found refer to using a wired connection, will this make any difference?

On my Xbox all I can see in my file browser is the old share setup from my Windows Vista PC. Should Ushare appear alongside this? Am I missing some configuration or setup steps?

**OK I Figured it out, I forgot to add the exception rule to my firewall.... durrrr and I also noticed I had DLNA set to yes.**

---

### Post by tk1269 on 2011-01-07
Saiing,
    Not sure if you are still monitoring this thread, or if you have figured out your problem.  I am currently dealing with the same issue or ushare not starting.  When I go to the terminal to run the program (sudo etc/init.d/ushare start) it all goes as it usually does.  But I cannot access the files on my xbox.  Then I go to stop the program, and I get the same error '. . .unable to kill: no such process '.  I'll give you some background and what I've discovered about my problem.

I am currently running Ubuntu 11.04, and have been using uShare since 8.04.  When I first started using it, it went relatively smoothly.  I vaguely remember having to edit the .conf file, but it must have gone well because I do not recall having this much trouble.  I have been on Ubuntu for, I dunno, 5 years now, but I am by no means an expert.  In fact, I would still classify myself in the noob category, even though I have managed to find a solution to my problems thanks to these forums.  Anyways. . .

I have been using uShare since about October of 2009, when I got my xbox.  I had it running through my laptop which was stuck on Ubuntu 9.04 (thats a whole nother story. . .).  Got it up and running just fine, linked to my /home/thomas folder and provided links to my external hard drive.  I had tried directly linking to the hard drive, but couldn't get the directory location to be recognized, so I stuck with this method.  It didn't actually work for music, but I wasn't too concerned about that, I've got plenty of other ways to play tunes.  Worked great other than the fact that I didn't know about the 'stop' command, leaving me to restart my computer every time i changed anything in the directory.

I just moved last month and am no longer using my laptop.  I spent the month of december transferring files and settings over to a desktop that I picked up and rebuilt.  I finally got that all set up, but the external was still connected to my laptop, and I didn't bother with that at the old place.  Now I'm only using the desktop with the external connected to it and set everything up last night to watch a movie.  After a little tinkering, I finally got it working.  Here is my .conf file:

# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=Desktop


# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth1

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49153

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=1337

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/thomas

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=yes

# Enable Web interface (yes/no)
ENABLE_WEB=no

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=no


I had to try a few different settings to get it to work (like the USHARE_IFACE=eth1, apparently eth1 is what you should use for a landline, eth0 for wireless), but finally got it going so my girlfriend could watch Harry Potter.  Two and a half somewhat boring hours later, I went to bed.

Now its today.  I got home from work and the first thing my girlfriend says to me is, "Can you get the computer thing going so I can watch the next Harry Potter?"  So I come over to my computer which has been turned off and on since last night, fire up the terminal, and start uShare.  Good.  She fires up the xbox, and goes to access the 'Desktop' directory (see .conf file, USHARE_NAME=Desktop), but it won't load.  So I come back to my computer, go into terminal to stop uShare, but when I type in the command, it tells me ". . . .no such process"  WTF?

Since running the program last night, I had not made any changes to the .conf file or any other as far as uShare is concerned.  While setting it up, I did have this problem at one point, but I changed a few random things and got it started but I know/remember which was the one that fixed the problem.  I think maybe it was the USHARE_IFACE changed to eth1 though.

Now what I do know is that the reason you can see 'uShare' in your xbox video library, is because it was there the last time xbox looked and it sticks around apaprently.  I know this because it was there from my laptop, which hasn't been connected to it in weeks.  But when I finally got it connected to the desktop last night, 'Desktop' replaced 'uShare' in the library menu.  So, just because you can see it there, does not mean the xbox is actually connected to it.

Ok, I know this is a long post to basically say, "I hear ya, I'm having the same problem," but I'm a long-winded kind of guy, so for that I'm sorry.  In any case, I'm going to dink around with it some more right now and if I can figure out what the problem is, I will post my solution.

---

### Post by tk1269 on 2011-01-07
Not a complete solution but one step further.

I had my .conf file setup for USHARE_IFACE=eth1, because last night while setting up, I checked my network manager, and eth1 was the connection that was sending/receiving, while eth0 and lo were both inactive.  Today, the two options in the network manager are eth0-eth1 and lo, where eth0-eth1 is the active connection.  So, I modified the .conf file to reflect that (leaving the USHARE_IFACE argument blank did not work), and got uShare to run.  At least when I go to stop it, it stops it instead of telling me "no such process."

Now I have another problem.  While trying to access the uShare link 'Desktop' on my xbox, I get this error:

Cannot connect to the PC.  A firewall may be blocking the connection

I do not have any firewalls set up, and the one on the router is disabled, so I do not think that is the problem.

AAAGH, I know this works, it did last night, and it is killing me today!  More coming if I can figure out the problem.  Maybe this step will help someone.

---

### Post by kai5263499 on 2011-02-17
It looks like the problem is with the [recent update to libupnp]("https://bugs.archlinux.org/task/22355").

---

### Post by tk1269 on 2011-02-23
Ok, that would make sense, but unfortunately, I have no idea what I have to do to fix the problem.  I followed the link (thank you), read the description, but to my noob brain it doesn't mean much.  Can anyone please give me some direction.  I am currently using uShare through my ps3 but would rather use the xbox, or at least have the option.  Thanks for any help!

---

### Post by devind25 on 2011-05-14
I'm in the same boat you are tk1269. I downloaded the patch but have no clue what to do next. Can anyone help??

---

### Post by BoomShaka on 2011-05-15
This probably isn't related to the issue you guys are having, but I'll put it here just in case.
I was able to see my share on my xbox, but opening the share showed no videos. I changed the path from ~/Public to /home/boomshaka/Public and now it works fine.
I installed ushare via apt, and did not install any patches.

** side note: it works, but I get that annoying "buffer every 20 seconds" nonsense. That said, I had it when I was sharing from Win7 too, so it may just be network related.

---

### Post by devind25 on 2011-05-15
I don't think that will fix my problem because I have tried everything when it comes to changing the way I type the folder I want to share in the selected area. I would like to start from scratch with ushare but when I remove it completely using synaptic I don't think it does completely because when I reinstall everything is still there from my .config file. Any suggestions?

---

### Post by devind25 on 2011-05-17
Anyone have any other suggestions??

---

