---
title: "Error with mythfilldatabase"
date: 2013-07-18
forum: Mythbuntu
---

### Post by gga96 on 2013-07-18
Hi,

In Australia we use an excelent tv guide data program called Shepherd to populate the EPG.
By default the data is written to ~/.shepherd/output.xmltv. This file exists and is full of good data.
When I run mythfilldatabase in a terminal it fails with the following extract:
> 
glen@backend-1:~$ mythfilldatabase
2013-07-18 16:20:43.477447 C  mythfilldatabase version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)
2013-07-18 16:20:43.477470 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2013-07-18 16:20:43.477474 N  Enabled verbose msgs:  general
...
2013-07-18 16:20:43.524383 I  Starting IO manager (read)
2013-07-18 16:20:43.525206 I  Starting IO manager (write)
2013-07-18 16:20:43.924944 I  Grabber has capabilities: baseline manualconfig preferredmethod 
2013-07-18 16:20:44.325456 I  Grabber prefers method: allatonce
2013-07-18 16:20:44.325888 I  XMLTV config file is: /home/glen/.mythtv/.xmltv
2013-07-18 16:20:52.135812 E  Error in 1:1: unexpected end of file
2013-07-18 16:20:52.135891 I  IconData: Updating icons for sourceid: 1
2013-07-18 16:20:52.136272 I  No programs found in data.
...

mythfilldatabase fails because file ~/.mythtv/.xmltv does not exist.

To overcome an audio problem I have just re-installed mythbuntu 12.04.1 to get the 3.2 kernel. 
The reason for 12.04.1 is that I have a DigitalNow Quad Tuner, the driver will be part of the 3.7 kernel but for now I have to stay with 3.2 so I can compile the driver. (ref: [https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0#readme](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0#readme))

I do not know what has gone wrong, but I did run Update Manager.
Has there been a change of location for ~/.mythtv/.xmltv or ~/.shepherd/output.xmltv?
Any thoughts on how to fix the error?

Thanks for your help.
Glen.

---

### Post by BicyclerBoy on 2013-07-18
Don't know about shephard..but use something similar here..

When you run mythfilldatabase from terminal it runs that as "user" & looks for xmltv file in /home/"user"/.mythtv/"source-name".xmltv.

The backend runs mythfilldatabase as user "mythtv" & expects to find the xml file in /home/mythtv/.mythtv/etc..

If your shephard script saves the listing xml file in a specific location...then create symlinks in both above directories to point to the  ~/.shepherd/output.xmltv...then you can run mythfilldatabase as user or BE job.

I have the "user" xmltv file symlinked to the actual "mythtv" file.

---

### Post by gga96 on 2013-07-20
Thanks BicyclerBoy for your help. 
 
I tried symlink and some other ideas but discovered more inconsistent behavior and eventually gave up and reinstalled.  This time I ran Update Manager immediately after completing the BE/FE install. It worked ok. 
 
The subsequent operations progressed normally until I tried to connect the existing remote FE without success. 
The following are in place and I thought it should connect: 
- BE Static IP 
- MySQL  "Master Backend Role" enabled 
- Ping BE from remote FE ok 
- Remote FE Setup: static IP and Password entered correctly. 
 
Surely I do not have to re-install the remote FE to get it to connect? 
Have I forgotten something? 
 
Glen

---

### Post by BicyclerBoy on 2013-07-20
MythTV changes the FE-BE protocol version & database schema version quite/very often..
And the version needs to match to be able to connect.
Need to look into the logs (/var/log/mythtv/*.log) to find the version info..

The logs on the remote frontend & logs on the master backend might reveal clues..

FWICR (years ago)
Clean/fresh installs from mythbuntu seem to get silly mysql password setup & silly IP address setup. Both these things cause trouble when adding a remote BE or FE..

Note that in my prev post.."user" would have been "glen" (no quotes).
For the std mythtv/xmltv grabber scripts the "source-name" would be the name given to the video source in mythtv-setup e.g. "FreeviewHD" or similar..
The shephard scripts could be doing something different.
B.

I assume you have read this webpage..
[http://svn.whuffy.com/wiki/Installation](http://svn.whuffy.com/wiki/Installation)

The shephard setup adds its grabber to a video source (in mythtv).. does your video source have a non-blank name? i.e. not equal to "".
Because .xmltv would be a hidden file.

You have configured shephard as per "Auto-configuration" section ?
Did you try this:
tv_grab_au --reoutput-mythtv

Shephard does not seem to use the standard "video-source".xmltv file in normal path but uses the mythfilldatabase with --file option.
Running "mythfilldatabase" just runs the configured grabbers for each video source.

---

### Post by gga96 on 2013-07-20
It would seem to be a version situation, I will study the logs and see what I can find out.
The remote FE has many post install functions added and takes a lot of time to setup, so I hope not to be forced to re-install this remote FE.  

Re "I assume you have...etc" yes I have read and understand shepherd docs, it is an excellent program. The EPG and all the other stuff went without a hitch after the second re-install. My experience is that running Update Manager has unexplained side affects, but on this occasion it has saved the day.

Will report findings here although this thread is somewhat off topic.

---

