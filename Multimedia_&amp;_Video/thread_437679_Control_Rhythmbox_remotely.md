---
title: "Control Rhythmbox remotely"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by hupp3l on 2007-05-09
Here is my setup: I have my main pc with windows on it and then my laptop with ubuntu feisty. My laptop is connected to an amp and pretty decent sized speakers but it sits out of quick reach to skip a song.

what I need: some plugin for rhythmbox that would allow me to connect to it and skip songs, maybe through a service such as telnet. Really basic I just need to skip a song that I do not want to listen to.

what I used to do: I used to have windows on both machines, and used foobar with foobar control server which just basically allowed me to just type in play in a telnet client and my music would start playing, or next and it would skip the song. 

If you know of any such plugin or you know if it could be made, please let me know. :guitar:

---

### Post by reclusivemonkey on 2007-05-09
> **hupp3l said:**
> Here is my setup: I have my main pc with windows on it and then my laptop with ubuntu feisty. My laptop is connected to an amp and pretty decent sized speakers but it sits out of quick reach to skip a song.

what I need: some plugin for rhythmbox that would allow me to connect to it and skip songs, maybe through a service such as telnet. Really basic I just need to skip a song that I do not want to listen to.

what I used to do: I used to have windows on both machines, and used foobar with foobar control server which just basically allowed me to just type in play in a telnet client and my music would start playing, or next and it would skip the song. 

If you know of any such plugin or you know if it could be made, please let me know. :guitar:

Just ssh into your box and use rhythmbox-client. The man page will tell you all the commands you can use.

---

### Post by reclusivemonkey on 2007-05-09
Just to add; if you are wanting to do this from windows, you can use Putty to log in via ssh.

---

### Post by hupp3l on 2007-05-09
Thank you I am able to connect through ssh and everything looks like it should be working but when I use the rhythmbox-client I get this error

hupp3l@hupp3l-laptop:~$ rhythmbox-client --play

(rhythmbox-client:23390): Rhythmbox-WARNING **: Failed to execute dbus-launch to autolaunch D-Bus session

I get the same no matter if I run it as root or not.

---

### Post by reclusivemonkey on 2007-05-09
Is rhythmbox already running?

---

### Post by hupp3l on 2007-05-09
Yes it is already running, it doesn't matter which command I use either, I get the same error for each of them.

---

### Post by reclusivemonkey on 2007-05-09
> **hupp3l said:**
> Yes it is already running, it doesn't matter which command I use either, I get the same error for each of them.

Sorry I can't help. I've never done what you are asking about I just knew about the rhythmbox-client command. I tried it here at home and get the same result. Maybe you could ask in the rhythmbox IRC channel;

[http://www.gnome.org/projects/rhythmbox/feedback.html](http://www.gnome.org/projects/rhythmbox/feedback.html)

---

### Post by bom28 on 2007-05-09
> **hupp3l said:**
> 
(rhythmbox-client:23390): Rhythmbox-WARNING **: Failed to execute dbus-launch to autolaunch D-Bus session


I would say, it's because it doesn't find the dbus session. Check if the DBUS_SESSION_BUS_ADDRESS environment variable is defined in your ssh session. If it's not you need to somehow export the DBUS_SESSION_BUS_ADDRESS environment variable from your X session to your ssh session. For example by running a script when your graphical session startup that write the DBUS_SESSION_BUS_ADDRESS value in a file. And read this value when your ssh session starts.
A bit complicated, don't know of an easier way. :(

---

### Post by valoun on 2007-05-12
I have found how to deal with it on the internet. What you need is to have the computer on and to be logged in (i.e. have the DBUS session already running)

```

#!/bin/sh

# find PID of any running process (owned by the user), for example notification-daemon (which uses DBUS)
PID=`pgrep -o -U $USER notification-da`

# from the environment of the process we get the DBUS address
DBUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS /proc/$PID/environ 2>/dev/null`

# if it was successfull, then we either print it, or export it or whatever, if we want
if [ "x$DBUS_ADDRESS" != "x" ]; then
    echo $DBUS_ADDRESS
    export $DBUS_ADDRESS
    # and we start using rhythmbox-client
    rhythmbox-client --play-pause
fi


```

---

