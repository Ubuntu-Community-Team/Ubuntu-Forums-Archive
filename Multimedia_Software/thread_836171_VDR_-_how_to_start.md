---
title: "VDR - how to start"
date: 2008-06-21
forum: Multimedia Software
---

### Post by Boexli on 2008-06-21
Hi all,

I have a working DVB device and VDR is installed. However everytime I start VDR nothing happens. Since I dont know if there is any logfile or a verbose mode I am totally lost at this point.

Any hint how I can access any logs - the message file does not show anything at all.

Thanks a lot for your help / Nick

---

### Post by steefjeqv on 2008-06-23
Hi,

First of all you'll need to edit this file :

sudo gedit /etc/default/vdr

Make sure that the first two lines are set to 1, enabling VDR to startup itself and shutdown your computer. Save and close the file.

To start VDR, type in terminal :

sudo /etc/init.d/vdr start

Now you'll have a running VDR, but if you have a budget DVB-card then you'll need a plugin to put the images on your screen. You'll need to install the following :

sudo apt-get install vdr-plugin-xineliboutput libxineliboutput-sxfe xineliboutput-sxfe

To get this plugin running, edit the following file :

sudo gedit /etc/vdr/plugins/plugin.xineliboutput.conf

Make sure you have the following lines in there (change local=none to local=sxfe) :

--local=sxfe
--primary   
--display=0.0
--fullscreen
--width=your screens width resolution (like 1024 or 1280,....)
--height=your screens height resolution (like 768,.....)

Save and close the file.

Restart VDR :

sudo /etc/init.d/vdr restart

With any luck you should have "no signal" on your screen.

Please come back to me if you've got any more questions/problems because this is just a basic setup.
You'll probably need more configuring which specifically concerns your hardware and software.

One specific (important) question is : Do you have a remote that comes with your DVB-card ? If yes, then chances are you're going to have to configure this, otherwise VDR possibly won't start.

Greetings,
Steven

---

### Post by asm2000 on 2008-08-06
i did like u told exactly but still nothing however it was like that

root@ymm-desktop:~# sudo /etc/init.d/vdr restart
Restarting Linux Video Disk Recorder: vdr - seems not to be running
Searching for plugins (VDR 1.6.0/1.6.0): osddemo pictures extrecmenu skinsoppalusikka lcdproc skinenigmang mplayer epgsearch skincurses femon epgsync ttxtsubs console xineliboutput spider sky svccli solitaire osdteletext streamdev-client epgsearchonly quickepgsearch freecell prefermenu mp3 remoteosd conflictcheckonly svdrpext svcsvr games live remote weather osdserver dvd fritzbox streamdev-server svdrpdemo status hello sudoku bitstreamout svdrpservice.
root@ymm-desktop:~# 

so plz continue as u r the only one i saw discussing simply from our favorite distro ubuntu.......thanks

---

### Post by steefjeqv on 2008-08-06
Hi,

You seem to have a lot of plugins running.
Either one of them can be the reason why VDR isn't starting up (some need additional configuring).
You can check your /var/log/syslog for any problems related to these plugins.

The idea is that you only install the essential plugins first (vdr-plugin-xineliboutput libxineliboutput-sxfe xineliboutput-sxfe). Then you should see "No Signal" on your screen.
Once VDR is running you can start adding the plugins you like.

You may need to make X available for VDR :

sudo xhost +


Then start VDR with :

sudo /etc/init.d/vdr start


If this doesn't work you can try to start the VDR frontend manually :

sudo vdr-sxfe


If this doesn't work you can try setting up VDR-sxfe as remote. Just change /etc/vdr/plugins/plugin.xineliboutput.conf to :

--local=none
--primary  

 

Greetings,
Steven

---

### Post by lolbot on 2009-11-23
Great and quick how-to. Thanks steefjeqv!

---

### Post by steefjeqv on 2009-11-24
Hi,

There's a nice PPA put together by the VDR-Team.
If you're interested in HDTV and VDPAU then you might like this.
It's based on VDR dev version 1.7.9, but already very stable.

[https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic]("https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic")

Greetings,
Steven

---

