---
title: "uShare streaming to PS3 howto."
date: 2009-07-09
forum: Multimedia Software
---

### Post by HolyRoses on 2009-07-09
Well today is the first time I have ever had a PS3 on my lan and I set out to get it working.  This method also works for xbox360.

To make it work with ps3 or 360 using uShare do the following:

apt-get install ushare

now edit /etc/ushare.conf and the following parameter:

USHARE_ENABLE_XBOX=yes

you will also need to edit

USHARE_DIR=

to have the value you want shared.

Regarding the /etc/ushare.conf file, this file is owned by root so you will need to edit it with root or change the permissions via sudo chmod 666 /etc/ushare.conf .  You should change them back when done by sudo chmod 644 /etc/ushare.conf 

The USHARE_DIR= cannot contain dirs with spaces, encapsulate your directories that have spaces with quotes, example: "/data/videos/my directory"

Another gotcha you might have is USHARE_IFACE=  If your machine has multiple nics or you are on a laptop you may need to modify this from whatever it defaulted to.  For instance on a laptop you may have eth0 (ethernet port 0) and wifi0 (wifi port 0).  If you have a laptop you may have a wlan0 and a eth0, etc.  You can get a list of your interfaces by typing: ifconfig -a  Then just edit the file to use the interface you are currently using.

The value USHARE_ENABLE_DLNA doesn't seem to work properly with the PS3 so don't mess with it. *odd*

The only problem I experience was scene selection would error out, but fast forward and rewind seemed to be alright.  Copying and multiple copy seemed to work good too.  So I suppose if you want scene selection to work well then just select copy.

Every time you modify the directory you are sharing (add or remove files) you should stop and start the ushare process (or reboot!).  Do this by /etc/init.d/ushare stop ; /etc/init.d/ushare start.  You could make a cron job just to do this daily if you are constantly updating your files.  If you want to test your changes to the config file and actually see the results of the program then just run ushare on the command line, do not run the /etc/init.d/ushare scripts.  When ushare is working properly then just press control C to return your prompt and start it normally via the /etc/init.d/ushare script.  (these scripts run automatically at boot time)

The /etc/ushare.conf that ships with the ubuntu package has outdated variables and they are not parsed correctly by the application.  The correct list of variables is:

USHARE_NAME=
USHARE_IFACE=
USHARE_PORT=
USHARE_TELNET_PORT=
USHARE_DIR=
USHARE_OVERRIDE_ICONV_ERR=
USHARE_ENABLE_WEB=
USHARE_ENABLE_TELNET=
USHARE_ENABLE_XBOX=
USHARE_ENABLE_DLNA=

I tested with PS3 firmware 2.8. Oh, also your MP4 movies need to be .m4v not .mp4 to be recognized correctly (rename them if need be).  Also for some reason it takes like 5 seconds for the video to actually start playing on the ps3 once you select it, perhaps it is buffering.

uShare supported formats list:

[http://ushare.geexbox.org/#Supported_File_Formats_List]("http://ushare.geexbox.org/#Supported_File_Formats_List")

-HR

---

### Post by sugargenius on 2009-08-14
all of my movies are x264-encoded with .mp4 extension.  I can see them from xbox but they have a slashed circle next to them and I can't play them.  Xbox will play them fine from thumbdrive, so it must be Ushare.

I had ushare on my old fileserver and the same files worked fine.

Is there some configuration I need to change in Ushare to make them playable?

---

### Post by HolyRoses on 2009-08-14
rename them to .m4v and restart ushare.

---

### Post by lie07 on 2009-11-24
i will have to try this out..

---

