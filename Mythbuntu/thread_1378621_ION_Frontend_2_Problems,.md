---
title: "ION Frontend 2 Problems,"
date: 2010-01-11
forum: Mythbuntu
---

### Post by bgiannes on 2010-01-11
1)  My mythfrontend (upstaires) had two problems, one wireless logs on 1second late, and mythtv goes to its setup mySQL setup page, (just pressing "next") starts mythtv correctly.  Should i delay the mythfrontend just a little?

2)  Can't get the remote to repeat +vol and -vol remote commands, after changing the Lirc config file with a repeat = 1 still no go!?  Is it using a different config file then the one in /home/user/.lirc ?

---

### Post by Eldis on 2010-01-14
> **bgiannes said:**
> 1)  My mythfrontend (upstaires) had two problems, one wireless logs on 1second late, and mythtv goes to its setup mySQL setup page, (just pressing "next") starts mythtv correctly.  Should i delay the mythfrontend just a little?

2)  Can't get the remote to repeat +vol and -vol remote commands, after changing the Lirc config file with a repeat = 1 still no go!?  Is it using a different config file then the one in /home/user/.lirc ?

2) You can see what config file is being used by watching in terminal at the mythfrontend.log
By default it's at /var/log/mythtv/mythfrontend.log
So I would recommend shutdown mythfrontnend open a terminal and do: tail -f /var/log/mythtv/mythfrontend.log
launch mythfrontend and scan for the lirc message. Sometimes the actual config file being used is at: /home/<user>/.mythtv/lircrc or that might be  symbolic link to somewhere else. Or it might be at the location you mentioned. To be honest I don't know which it is so I have all those replaced by a symbolic link to my actual config file.

1) Yes a small delay would be good. I have custom script that will launch mythfrontend and it also checks that irexec is up and does some other things. This script can be launched by a button on my remote and it also replaces the mythfrontend launch that can be found in the startup programs on your desktop enviroment.

My script isn't pretty but it works (this is the stripped down client version of it):

> #!/bin/sh
#mythwatch.sh
#Start mythfrontend and/or lircd on by remote button press from irexec

if [ ! "$(pidof mythfrontend.real)" ]
then
        echo "Mythfrontend is not started. Starting Mythfrontend..."
        DISPLAY=:0 xset -dpms
        DISPLAY=:0 mythfrontend --service &
else
        echo "Mythfrontend is already started."

fi


if [ ! "$(pidof irexec)" ]
then
        echo "Irexec is not started. Starting Irexec..."
        DISPLAY=:0 irexec -d /home/myth/.mythtv/lircrc &
else
        echo "Irexec is already started."
fi

lircrc snip:
> begin
     button = start
     prog = irexec
     repeat = 0
     config = /usr/bin/mythwatch.sh
end


---

### Post by bgiannes on 2010-01-18
1st thank you for your reply.  I like that start-up script, hope to get it setup soon.


1)This weekend i switched to wpa2 on my network, now the wireless logs-on is quicker, so mythtv doesn't go to the setup screen.

2)I was editing the correct lirc config file, but a changed the wrong remotes repeat.  but now i'm on track.

---

