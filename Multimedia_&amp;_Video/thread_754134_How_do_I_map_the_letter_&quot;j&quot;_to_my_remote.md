---
title: "How do I map the letter &quot;j&quot; to my remote with lirc?"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by doubledouce on 2008-04-13
Hi!

I'm setting up a freevo entertainment system and almost everything is working out well. But I have one problem. To change subtitles while I watch a movie (using mplayer as video player) I have to press "j" on my keyboard. How can I map the keystroke "j" to a button on my remote using lirc??

I'm using a microsoft mce remote and the normal mapping is working fine. Using lircrc I've mapped all of the functions I need, but it doesn't give me the ability to map individual key on the keyboard.

And if anyone knows... how do I launch freevo with a button on the remote?? :p

---

### Post by doubledouce on 2008-04-14
Bump, anyone?

---

### Post by doubledouce on 2008-04-14
Ok, I managed to fix the problem with subtitles by adding some EVENTS.

Now I'm working on starting freevo using a button on my remote and I came across this in the OS dir mail archive:

------------------------------------------------------------
Subject: 	Re: Shutdown freevo with a lirc command

stephan wezel wrote:

    Hi,

Hi.


    can I shutdown freevo through one lirc event/command without selecting the 
    shutdown menu point ?

Yes!


    and if how ??

Well, I am not sure if you can bind a Freevo event to shutdown but the way I do it is with irexec. Irexec is a command that comes with lirc that you can have it run a command per button press based on configuration. In my /etc/init.d/freevo system start/stop script I have:

case "$1" in
  start)
        if [ "`ps -ef | grep irexec | grep -v grep`" = '' ]
        then
          /usr/local/bin/irexec -d /etc/freevo/irexec.conf
        fi


Ok, so that't not the cleanest but upon startup it looks for a running irexec process and runs it if none is found. In /etc/freevo/irexec.conf I have:

begin
        remote = hauppauge_pvr
        button = Power
        prog   = irexec
        repeat = 0
        config = /etc/freevo/onoff_switch
end


So, every time that I press the power button the onoff_switch gets executed. That is a very messy shell script that decides if Freevo is running or not then starts or stops it. The contents of that file are:

#!/bin/bash


TEST=`ps -ef | grep freevo | grep -v grep | grep -v irexec | grep -v onoff | grep -v "less " | grep -v "vi " | grep -v "cron" | grep -v "tail " | grep -v recordserver | grep -v bitch | grep -v webserver | grep -v tv_grab`

if [ "$TEST" = "" ]
then
  echo Freevo is off, starting.
  /etc/init.d/freevo start
else
  echo Freevo is on, stopping.
  /opt/freevo/freevo stop
fi


Ok, the TEST line is horrible I know. ;) I made that before adding pid file support to Freevo and need to fix it. Actually, perhaps I will add a 'switch' option to my /etc/init.d/freevo and commit it to CVS.

Would others find this useful? I can use the power button on my remote to startup and shutdown Freevo with no issues.

-Rob
---------------------------------------------------

Can anyone help me with how to use this script? Do I add the first code to a bash file and autostart it upon startup?? :confused:

---

