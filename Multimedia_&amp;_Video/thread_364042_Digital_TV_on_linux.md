---
title: "Digital TV on linux?"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by Russty of Oz on 2007-02-17
Hi all! :) 

I am fed up with trying to get my DVICO Fusion DVB-T card to work on Ubuntu, sometimes it finds "A" channel, yes only ONE, and not always the same ONE!!   Then when I open Kaffeine again another time it wont work at all!  

So I was wondering if there are any HDTV cards that have a good reputation of working all the time on Ubuntu?  Now I realize that there are probably some brands that are only available in certain countries, and I am in Australia, so anyone who has had experience with the "main" brands, i.e. Happauge, Leadtek Winfast, etc, or particularly anyone in Australia, I would appreciate any feedback.

Russty.:cool:

---

### Post by Erlander on 2007-02-17
Hi Again Russty,

My Dvico USB is still working well and now with Mythtv as well as Kaffiene.  I notice from the Dvico website it is no longer a current model being apparently replaced by the Nano.

You might still be able to find one though.

I don't know much about the Nano though.

Rob

---

### Post by Russty of Oz on 2007-02-17
> **Erlander said:**
> Hi Again Russty,

My Dvico USB is still working well and now with Mythtv as well as Kaffiene.  I notice from the Dvico website it is no longer a current model being apparently replaced by the Nano.

You might still be able to find one though.

I don't know much about the Nano though.

Rob

**SO YOU GOT MYTHTV TO WORK?????**  I can't get anywhere with that.  I just keep getting the set up page and I have no idea how to get it to work.

Well I guess seeing as you have found the firmware for the usb one, I should give that some serious consideration.

Thanks Rob :)

---

### Post by Jose Catre-Vandis on 2007-02-17
Have you tried installing the latest v4l-dvb via mercurial, and set the tuner number correctly, checked the tuner number in dmesg, and run a scan using dvb-utils.

Post your dmesg which gives plenty of help here. I am pretty certain your card is supported:

[http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/)

[http://www.users.on.net/~jani/dvico-mythtv-5.html](http://www.users.on.net/~jani/dvico-mythtv-5.html)

[http://www.linuxtv.org/pipermail/linux-dvb/2006-September/012639.html](http://www.linuxtv.org/pipermail/linux-dvb/2006-September/012639.html)

[http://forums.dvbowners.com/index.php?showtopic=6942](http://forums.dvbowners.com/index.php?showtopic=6942)

Should keep you going for a while :-)

---

### Post by Russty of Oz on 2007-02-17
Yes, it looks as though that will keep me going for a while!  I will read through it all and see if I can make this thing work.  I am not sure about the latest V4L via mercurial, I just used Kaffeine and the V4L that was installed.   A quick look at the first link you provided looks like my card should be able to work, so perhaps I just haven't done all the right things yet.  

I will go through them and see.

Thanks :)

---

### Post by Erlander on 2007-02-18
> **Russty of Oz said:**
> **SO YOU GOT MYTHTV TO WORK?????**  I can't get anywhere with that.  I just keep getting the set up page and I have no idea how to get it to work.


Try giving the mythtv user a password and logging as mythtv then running mythtv-setup.

sudo passwd mythtv

In addition to the Official Ubuntu guide I also found the ParKer guide helpful when I wasn't sure and from [http://www.lemis.com/grog/videorecorder/mythsetup-sep-2006.html](http://www.lemis.com/grog/videorecorder/mythsetup-sep-2006.html) I was able to understand what was needed for Video Sources and Input Connections.

Rob

---

### Post by Russty of Oz on 2007-02-18
> **Erlander said:**
> Try giving the mythtv user a password and logging as mythtv then running mythtv-setup.

sudo passwd mythtv

In addition to the Official Ubuntu guide I also found the ParKer guide helpful when I wasn't sure and from [http://www.lemis.com/grog/videorecorder/mythsetup-sep-2006.html](http://www.lemis.com/grog/videorecorder/mythsetup-sep-2006.html) I was able to understand what was needed for Video Sources and Input Connections.

Rob

AHH!  now that sounds interesting!   I found in Jose Catre-Vandis post a link to how to install the drivers for the Fusion HDTV DVB-T card and experimented with installing it (on my other Ubuntu machine as the one with fusion in it was busy doing other things at the time).   So tomorrow I will try installing it on this machine.  Then with the drivers installed I will try your suggestion with mythtv.  

It sounds like I could get this thing working without having to buy another TV card!!:) 

Will let you all know how it all turns out.  

Russty

---

### Post by Erlander on 2007-02-18
Sounds good.

Rob

---

### Post by Jose Catre-Vandis on 2007-02-18
To do the latest v4l-dvb do as follows:


```
sudo apt-get install mercurial
```

```
hg clone http://linuxtv.org/hg/~mrechberger/v4l-dvb
 cd v4l-dvb 
sudo make clean 
sudo make distclean 
sudo make ( error message like leaving directory /2.6.15-23 etc..) 
sudo make install 
sudo make reload
```

You may need firmware in /lib/firmware ?

---

### Post by Russty of Oz on 2007-02-20
> **Erlander said:**
> Try giving the mythtv user a password and logging as mythtv then running mythtv-setup.

sudo passwd mythtv

In addition to the Official Ubuntu guide I also found the ParKer guide helpful when I wasn't sure and from [http://www.lemis.com/grog/videorecorder/mythsetup-sep-2006.html](http://www.lemis.com/grog/videorecorder/mythsetup-sep-2006.html) I was able to understand what was needed for Video Sources and Input Connections.

Rob

Hi again Rob,

I did the sudo passwd thing but I still just get the setup page on mythtv.   Is there something I have to do in the  [B]Host name
                                 Database
                                 User
                                 Password
                                 Database type[/B]



I just keep getting this every time I try to open mythtv

Russty.

---

### Post by Erlander on 2007-02-20
Hi Russty,

That is the same problem I had several times.  I think it is a mysql password thing.

have a look at /etc/mythtv/mysql.txt and the line DBPassword.

I wouldn't change it there but I would use that password to get into myth.  It seems that if when setting up Mythtv you leave the password blank that it generates a random one as in mysql.txt.  If I have to re-install again I will try having the mythtv password in the mythtv setup as I deleted it there thinking I had to have it the same as I'd set in mysql.

I'm not sure but the password may be stored in other places as well and if so this may not fix it.

I finished up doing a fresh install of Ubuntu and Mythtv several times before I finally got it right.

I have just remembered that this thread [http://ubuntuforums.org/showthread.php?t=362732](http://ubuntuforums.org/showthread.php?t=362732)
dealt with this very problem and it might be a better way to go than what I've said above.  Anyway this gives you 2 things to try.

Rob

---

### Post by Russty of Oz on 2007-02-21
"have a look at /etc/mythtv/mysql.txt and the line DBPassword."

When I try to see this by sudo /etc/........., it says "command not found"

I looked in the File system and there is a mysql.txt file there but it has a X next to it and it won't open!

That other link didn't help either.   All I get is this initial settings page, I never get into mythtv itself.

I must be missing something here!

---

### Post by Erlander on 2007-02-21
2 possible ways to look at /etc/mythtv/mysql.txt

1.   login as mythtv and then try

2.   I changed my permissions as recommended by Gary Parker at [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
The bit that says:
It also makes sense to grant access rights to the mythtv user. To do this, edit the file /etc/group and mythtv to all groups that your original user is in. This will allow him to use sudo, access the cdrom etc. For example:

.
admin:x:106:garry,mythtv
.
Good luck.

Rob

---

### Post by Erlander on 2007-02-21
Or from the Ubuntu guide:

Add yourself and any other users you want to have access to mythtv to the mythtv group.

    *

      To add yourself to the mythtv group, use this command:
          o

            sudo usermod -a -G mythtv USERNAME

      Where USERNAME is the name of the user you are adding to the mythtv group.


Rob

---

### Post by Russty of Oz on 2007-02-21
**Login as mythtv????**??

---

### Post by Erlander on 2007-02-21
sudo passwd mythtv

will allow you to set a password for the user mythtv.

Then restart the pc and when the login screen comes up the user is mythtv and you use the password you just set.

Rob

---

### Post by Russty of Oz on 2007-02-21
OK, I am starting afresh on my other computer with fusion and mythtv!

Now, I have just used synaptic to install mythtv and it wants me to do something but I don't understand?   I have to run mythtv setup as the mythtv user  :confused: 

AND!!

I have to "login to an X session"  :confused: 

So how do I get through this stage?

Russty.

---

### Post by Erlander on 2007-02-21
To login as the mythtv user you have to first set a password for that user.  See earlier post for that code.

Having done that you can shutdown Ubuntu and re-start.

When you get to the login screen do not login as yourself but rather use the user name "mythtv" and the password you just setup.

Then in terminal you can run mythtv-setup.

Rob

---

### Post by Russty of Oz on 2007-02-22
AT LAST SOME SUCCESS! :) 

**BUT!**

Having got into it now, I have been through the set up but I keep getting this error message:

"Could not connect to the master backend server -- is it running?  Is the IP address set for it in the setup program correct?"

Well, I ran the code for the mythtv-backend start and it said it is already running.   As for the IP address, I just can't find any reference to an IP anywhere!  Where is it?  Why do we need an IP address for the tv?   :-k 

So it looks like I am ALMOST there! :roll: 

Russty.

---

### Post by Erlander on 2007-02-22
Well Done.

The IP address is used for when you have the backend and frontend on different pc's or when you have multiple frontends.

You set it on the first General screen on the backend setup.  The default is 127.0.0.1 which is local host and works well when you have the backend and frontend on the same pc.

See Attachement 1.  Note that its in 2 places on this screen.

Then it has to be set on the first General screen of the frontend setup.  See Attachement 2.
I could have probably set this as 127.0.0.1 too but its working this way so I'm not changing it yet.  Note that on the backend it asks fro the address but on the frontend it asks for the name!!!!

I have changed the theme which is why it looks different.

Good luck.

Rob

---

### Post by Russty of Oz on 2007-02-22
Hi again!

I just cant find the screen "Host Address Backend Setup"

I know you say it is on the first general screen, but I must either be looking in the wrong places or just PLAIN THICK!!  (I think you will all agree with the latter :razz: )

So when I run mythtv do I go to "utilities/setup"  then "General" and were to then?   I can't find that "Host Address Backend Setup".

Russty.

---

### Post by Erlander on 2007-02-22
No not thick.  I had 5 or 6 attempts.  Its just complicated, there are so many options.

mythtv-setup

will get you into the backend although it was at this stage that I had to give the user mythtv a password and login as mythtv.

I expect to be around most of this afternoon.  Its too warm to do much else.

Rob

---

### Post by Russty of Oz on 2007-02-22
I just did the mythtv setup from a terminal while logged in to mythtv and I got this:

$ mythtv setup
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-02-23 13:55:24.633 Using runtime prefix = /usr
2007-02-23 13:55:24.646 Gnome-Screensaver support enabled
2007-02-23 13:55:24.647 DPMS is active.
2007-02-23 13:55:24.686 New DB connection, total: 1
2007-02-23 13:55:24.692 Connected to database 'mythconverg' at host: localhost
2007-02-23 13:55:24.695 Total desktop dim: 1280x1024, with 1 screen[s].
2007-02-23 13:55:24.699 Using screen 0, 1280x1024 at 0,0
2007-02-23 13:55:24.745 max_width: 1280 max_height: 1024
2007-02-23 13:55:24.746 Total desktop dim: 1280x1024, with 1 screen[s].
2007-02-23 13:55:24.748 Using screen 0, 1280x1024 at 0,0
2007-02-23 13:55:24.749 Switching to square mode (G.A.N.T.)
2007-02-23 13:55:24.773 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-02-23 13:55:25.351 Joystick disabled.
2007-02-23 13:55:25.723 New DB connection, total: 2
2007-02-23 13:55:25.723 Connected to database 'mythconverg' at host: localhost
2007-02-23 13:55:25.770 TV: Attempting to change from None to WatchingPreRecorded
2007-02-23 13:55:25.771 RingBuf(setup): OpenFile(setup, 12)
2007-02-23 13:55:32.278 RingBuf(setup): Could not open setup.
2007-02-23 13:55:32.278 RingBuf(setup): CalcReadAheadThresh(4000 KB)
                         -> threshhold(146 KB) min read(32 KB) blk size(64 KB)
$ 



Hmmmmmm, does this mean there is something wrong or should I have logged out of mythtv and logged in as myself to do it?   After I send this I will log out and try it the other way.

---

### Post by Russty of Oz on 2007-02-22
NOPE!  logging in as myself and doing the mythtv setup just gave me the other pages, not the one with the IP things. :( 

I will have some lunch now and see if that helps!  :popcorn: 

It is hot here too!

Russty.

---

### Post by Erlander on 2007-02-22
Here is the code I get when I run mythtv-setup:

rob@ubuntu:~$ mythtv-setup
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-02-23 14:33:43.264 Using runtime prefix = /usr
2007-02-23 14:33:43.332 Gnome-Screensaver support enabled
2007-02-23 14:33:43.333 DPMS is active.
2007-02-23 14:33:43.387 New DB connection, total: 1
2007-02-23 14:33:43.393 Connected to database 'mythconverg' at host: localhost
2007-02-23 14:33:43.410 Total desktop dim: 1024x768, with 1 screen[s].
2007-02-23 14:33:43.414 Using screen 0, 1024x768 at 0,0
2007-02-23 14:33:43.531 Current Schema Version: 1160
2007-02-23 14:33:43.580 Total desktop dim: 1024x768, with 1 screen[s].
2007-02-23 14:33:43.581 Using screen 0, 1024x768 at 0,0
2007-02-23 14:33:43.583 Switching to square mode (Retro)
2007-02-23 14:33:43.795 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-02-23 14:33:44.477 Joystick disabled.
2007-02-23 14:33:44.645 Loading from: /usr/share/mythtv/themes/default/base.xml
rob@ubuntu:~$ 

The initial errors I get are I believe associated with my remote as I've not set it up correctly yet and have only limited functionality.

There is also the problem that the backend is running.

I think you have 2 problems:

1.   the backend is running already and will make adjusting settings difficult.  Use:
sudo /etc/init.d/mythtv-backend stop

2.   You should get a screen like the one under "Initial configuration page" at [https://help.ubuntu.com/community/MythTV_mythtvsetup](https://help.ubuntu.com/community/MythTV_mythtvsetup)

If instead of the grey background screen shown you are getting a blue followed by about 2 others then I think it is your password.  Which colour is it?

Rob

---

### Post by Erlander on 2007-02-22
The last few lines of your code seem to suggest that setup is not opening:

2007-02-23 13:55:25.770 TV: Attempting to change from None to WatchingPreRecorded
2007-02-23 13:55:25.771 RingBuf(setup): OpenFile(setup, 12)
2007-02-23 13:55:32.278 RingBuf(setup): Could not open setup.
2007-02-23 13:55:32.278 RingBuf(setup): CalcReadAheadThresh(4000 KB)
-> threshhold(146 KB) min read(32 KB) blk size(64 KB)

Have a look at the password in the Frontend Setup:

Code:
mythfrontend

Utilities/Setup/Setup/General

then escape out of there and close the frontend.

Make sure the password you get on the bluescreen when you start the backend is the same as the frontend one.  Change the backend one if necessary but not the frontend.

Hopefully that will do it.

Rob

---

### Post by Russty of Oz on 2007-02-22
AH!  As soon as I saw what your output was I could see immediately what I did wrong, I just put "mythtv setup" instead of "mythtv-setup" :oops: 

Now I am into the setup stage.  Will let you know what happens!

Russty

---

### Post by Russty of Oz on 2007-02-23
I think we are almost there.  [-o< 

but there is always something else!   I changed the password in the blue screen and that worked.  now what does the attached message mean?

---

### Post by Erlander on 2007-02-23
I think it means that the backend is running and recording a channel.

Have a look in /var/lib/mythtv assuming you have used the default.

I have sent you a private message but you may not need that now.

Rob

---

### Post by Russty of Oz on 2007-02-23
well in var/lib/mythtv  there is only one file called   nsflockfile.lock

I haven't told it to record anything yet, I haven't seen any channels.   I will go through your screenshots you sent and compare them with mine and see where I have gone wrong.  I have no doubt go a wrong setting somewhere.   

This mythtv has to be one of, if not the most difficult things to get working in Ubuntu.  Still it looks like it is almost done!  

Russty

---

### Post by Erlander on 2007-02-23
Have a look at Backend Sources.  You have to make a new one.  I called mine TV

and Backend Connections.

The official guide didn't help me on this (maybe I didn't read it properly)

Anyhow the TV I set in one turned up in the next and was needed.

If you get that right you can scan for channels in Connections.

Rob

---

### Post by Russty of Oz on 2007-02-23
I have gone through your screenshots and all is ok except that I cant find in mine, the pages for Capture Cards and Channel Editor.  Do you know how I find them in the setup area?

Russty

Oh, and I cant find the Backend sources or Backend connections pages either!  Sigh!

---

### Post by Erlander on 2007-02-23
Capture Cards:  click on "New" and select "DVB DTV Capture Card (v3.x)"

Under video source again select New.  

you need to give it a name like "TV" that I used.
However this page doesn't do much for me as it relates to online TV Guides which we don't seem to have in Australia.

In Input Connections you select the name "TV" that you entered in Sources and it is here that if everything else is Ok that you can scan for Channels.

Channel Editor comes later.

Rob

---

### Post by Russty of Oz on 2007-02-23
I really appreciate the fact that you are spending so much time helping me with this Rob, but I still can't  find the sections for Capture cards or Input connections.   They just don't seems to be there.  Do I access them from the setup section in mythtv?  I can't find them anywhere in there. :( 

Russty

---

### Post by Erlander on 2007-02-23
When I go into the backend setup (mythtv-setup) I get a menu which lists:

General
Capture Cards
Video Sources
Input Connections
Channel Editor

I access them from this menu.

Will post some more screen shots including one of this menu in a minute or two.

Rob

---

### Post by Erlander on 2007-02-23
Now have a screen-shot of the Backend menu and 3 more screen-shots in Backend-Connections up on my web-site.

Rob

---

### Post by Russty of Oz on 2007-02-23
Well of course silly me wasn't doing the mythtv-setup in the terminal!  So now I have got in there and all my settings seem to be the same as yours, but when I do the channel scan it doesn't find anything!  (see attachment)  Now I wonder if this could have something to do with the firmware thing?   

I will have to give this a break for today, I am told I have other important things to do rather than "playing" with the computer!!!  

I will have another go tomorrow and will see if I can find a firmware file.  

Thanks again for all the help! :) 

Russty.

---

### Post by Russty of Oz on 2007-03-03
[SIZE="5"]**SOME SUCCESS AT LAST!!!**[/SIZE] :guitar: 

I have purchased a Leadtek Winfast DVT 1000  (it was only $99 and has a loop through to connect the antenna to my Fusion DVB-T card on the other computer).  In fact even on Windows it seems to be a pretty cool TV card, even with Direct Burn to DVD!

Still, I digress.  The thing is that I have had Kaffeine installed on this computer and for the past few days it hasn't shown up the Digital TV section, but for some unknown reason, tonight when I opened Kaffeine, the Digital TV was there!:shock:    So I tried to scan for channels, something that wouldn't work with my Fusion card, and to my surprise, IT WORKED!  \\:D/   It found all the local channels and with 100% signal strength.  FANTASTIC!!!:lol: 

So I can now watch and record Digital TV with Ubuntu, and of course I now know how to make them into DVD files and even make menus with QDVDAuthor.   

It is almost time to say BYE BYE to Windows, I just have to work out how to configure my router  to enable my webcam to work.  

Please forgive me for raving on about this but I am so excited I have finally got TV working on Ubuntu, I have been struggling with this for so long.  Thanks to everyone who has suggested things, especially Erlander, who has been more helpful that I would have expected.

I'M HAAAAAPPPPPPPYYYYYY  :lol:

Russty.:popcorn:

---

### Post by Erlander on 2007-03-03
And we are happy for you too.

Rob

---

