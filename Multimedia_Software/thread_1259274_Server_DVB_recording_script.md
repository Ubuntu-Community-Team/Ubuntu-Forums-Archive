---
title: "Server DVB recording script"
date: 2009-09-06
forum: Multimedia Software
---

### Post by diddy1234 on 2009-09-06
Hi All

I wanted to make a DVB recording script that would work on a Ubuntu / Kubuntu server over SSH connection with a minimal GUI.

How it works :-
The script will reside in the users home directory under a folder called recorder.
performing ./menu.sh will run the menu system allowing the user to select a channel from a list and then the user can input a duration to record TV for.
Once this is done TV is recorded and on the fly encoded to XVID and saved into the users home/Videos folder.

The advantage to minimal GUI is that the user can run the script thorugh a shell or through SSH connection to the server so the user does not have to be at the server itself, they can even be at work and SSH intot he home server and set a recording. 

What is needed for the script to work :-
Mencoder
Mplayer
Scan (part of dvb-utils package)
M32codecs (not too sure if this is needed but will help)
A working channels.conf (in the .mplayer folder)but one is supplied
A reasonbly powerful pc (dual core helps to keep the system responsive)

Steps to get functioning :-
Download the attached script and unzip to your home directory(should create a recorder folder)
Make all sh scripts executable (Chmod +x *.sh)
Copy the provided channels.conf to ./mplayer folder (note this is for the Astra 28.2 DVB-S satellite for the U.K.)
edit the menu.sh file and change the default saving location to your home/<YOUR USERNAME>/Videos folder (but can be anything you want really)
execute the menu.sh (by ./menu.sh) and enjoy

Note: you can create a different channels.conf (if you have a DVB-T card for example) from the script but you may have to edit the channels.conf afterwards for duplicate channels.

Things id like to do but have not had time / knowledge
1. add a timed recording that sets a cron job to record a program at a set time.
2. managed scheduled recording and have the ability to remove set recordings.
3. dynamic build of channel list in the menu.sh script to be reading the channel names in the channels.conf

I would then be able to set a timed recording and then close out of the SSH connection and the recording will happen at the desired time without me being logged into the server.

benefits I have found 
I have been able to start a recording and then from a client pc connect the my home directory and start playing the currently recording file (a sort of cheap streaming), therefore i can watch a TV channel on my laptop over wifi connection.

Also the XVID format is compatible with playing straight in M$ media player (so many hoops to jump through to get this to work)

Have fun and please feel free to change update or advise of better workings.

(UPDATE) : use the script near the end of this page as this is the revised version

Rich

---

### Post by lovinglinux on 2009-09-06
You could try my media center extension for Firefox, called [FoxMediaCenter]("http://fmc.isgreat.org"). Not exactly a script, but can be controlled via Firefox ssh forwarding.

Since I don't own a dvb card, I'm not sure it will work with your setup, but it uses mencoder for TV recording and can schedule single programme recordings or weekly series.

Any feeback would be much appreciated, so I can improve it and expand the compatibility with dvb cards.

---

### Post by diddy1234 on 2009-09-06
lovinglinux, thanks for the link.

That's just what I was after.

never thought of using a web browser.

I will check out this add on and report back

RD

---

### Post by lovinglinux on 2009-09-06
> **diddy1234 said:**
> lovinglinux, thanks for the link.

That's just what I was after.

never thought of using a web browser.

I will check out this add on and report back

RD

Keep in mind that while the extension is experimental, you won't get any automatic updates. So visit the download section at least once a month to get new versions. I will release a new version soon, which has some improvements in the xmltv import feature and adds Windows compatibility.

---

### Post by diddy1234 on 2009-09-06
It looks a realy good tool

I have not set this up yet but the you tube videos appear if foxmediacenter is running on the server pc.

What limitations are there running the foxmediacenter on a client pc ?

IE ubuntu server and a ubuntu client connects using this plugin ?

I suspect the client pc could not watch any video but can set recordings and view the epg guide am I right ?

---

### Post by lovinglinux on 2009-09-06
> **diddy1234 said:**
> It looks a realy good tool

Thank you.

> **diddy1234 said:**
> I have not set this up yet but the you tube videos appear if foxmediacenter is running on the server pc.

I don't understand the question. 

> **diddy1234 said:**
> What limitations are there running the foxmediacenter on a client pc ?

For instance, Firefox must be running to get reminders and automatically record TV with the scheduler. So, it's not very practical for a server. I never tried to use this feature over ssh tho. It might work. 

The rest of the functionality is basically database driven, so it will work regardless of the machine running it. Just keep in mind that each installation will have it's own database and settings.

> **diddy1234 said:**
> IE ubuntu server and a ubuntu client connects using this plugin ?

Is not designed to do that. There isn't any client-server functionality on the extension, but this is something to think about for future releases.

> **diddy1234 said:**
> I suspect the client pc could not watch any video but can set recordings and view the epg guide am I right ?

I'm not sure if ssh forwarding would allow to watch videos on the remote. Nevertheless, you could mount the server media folders locally and run a local instance of Firefox with FoxMediaCenter, configuring the media folder paths in the extension to use the remote folders. When you scan the media folders it will list the remote files, so you can watch them on the local machine.

---

### Post by diddy1234 on 2009-09-06
I suspect this could work if the user had mapped drives to the recording folders.

Regarding the you tube videos, There are examples of how to use and how to set up the plugin in firefox.
What I was previously asking was that it appears that the plugin HAS to work on the pc with the TV card.
Am I correct ?

Still a very good add on and worth investigating.

---

### Post by lovinglinux on 2009-09-06
> **diddy1234 said:**
> What I was previously asking was that it appears that the plugin HAS to work on the pc with the TV card.
Am I correct ?

Yes, you are correct. The extension should be installed and running in the machine with the TV card.

---

### Post by diddy1234 on 2009-09-19
This latest script is now updated and complete as far as I can go (I am not a developer).

A script has been attached for DVB-T channels in the U.K.

The completed script will now schedule jobs using 'at' tasks.
The user can now tune channels for Asta 28.2 DVB-S, Crystal Palace DVB-T or Sandy Heath DVB-T.

But with modification the script can tune for any satellite or DVB-T, DVB-C channels as long as the transponders exist in a file (and script changed to look at the new list).

So how does it work :-

The user runs ./menu.sh and are presented with a list of channels and the option to retune the channels (good for DVB-T in the U.K. as they seem to change often).

Selecting any channel will then ask for a start time to record.
Once done the user is asked to set a duration to record for.

Once this has been set a small script will be generated (<channel name>.sh) and then an automated task is set (to run the small script) at a set time.

So what is the advantage using this script ?
Well for one you don't have to be at the pc in question to run the script.
You can be anywhere in the world with internet access and remote into the pc (via SSH and putty for example) and set recordings.

You can set a recording and then log out of the pc and the recordings are done on a scheduled basis.

Things I would like to do :-
Make the channel list auto generated from the ~/.mplayer/channels.conf file
Automaticly set the channel name from the channel.conf when building the recording script.
Set timed recordings via email (I could then email the pc where this script would exist and set timed recordings), but it looks like a nightmare to do.


Well this is as far as I can take scripting with my limited knowledge but have a play and feel free to modify / improve on it.

---

