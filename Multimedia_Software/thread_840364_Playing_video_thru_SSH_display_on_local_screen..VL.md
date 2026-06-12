---
title: "Playing video thru SSH display on local screen..VLC/VLM"
date: 2008-06-25
forum: Multimedia Software
---

### Post by yltv on 2008-06-25
Hi all:

Recently I have become an operations partner for a leased access cable programmer. This operation consists of many Linux video servers which I control through SSH using putty on my Windows machine. The company is small and has had one IT person since it's existence.

The servers run Ubuntu 7 and the media player we use is VLC.

Up until about 2 weeks ago I have never touched Linux. The person who ran this operation before had a working configuration in place, where he controlled the servers remotely, scheduled VLC to play at certain times, and somehow got them to play fullscreen on the video output from a remote terminal. He up and left the operation without leaving any documentation on how any of it works.

The machines are set to autologin, and VLC automatically launches with startup.

The graphics card is an Ndivia Geforce 6100 with TV out. The settings are correct there, the display default to the TV output.  

I have read VLC documentation, scoured the internet, and have decided to actually post something myself in hopes of an answer.

We are losing thousands of dollars daily because I can't figure out how this thing works. 

Anyway let me know what other information you would need for this to make more sense. Thanks in advance.

---

### Post by aeiah on 2008-06-25
i know this isnt an awful lot of help, and something you've probabably tried, but cycling through the list of previous commands might lead you to some clues. perhaps he's got custom scripts in the server or client home directories, their usr/bin or usr/local/bin directories too.

to display the entire history, in a terminal or cli simply type 
```
history
```

you might want to pipe this to a file if its big:
```
history > history.list
```

not a massive help but then im not 100% clear on the set up and havent any particular experience with vlc over ssh. is the server with vlc sending video within the lan or offsite? what are the clients like? actual tv boxes or something?

---

### Post by yltv on 2008-06-25
> **aeiah said:**
> i know this isnt an awful lot of help, and something you've probabably tried, but cycling through the list of previous commands might lead you to some clues. perhaps he's got custom scripts in the server or client home directories, their usr/bin or usr/local/bin directories too.

to display the entire history, in a terminal or cli simply type 
```
history
```

you might want to pipe this to a file if its big:
```
history > history.list
```

not a massive help but then im not 100% clear on the set up and havent any particular experience with vlc over ssh. is the server with vlc sending video within the lan or offsite? what are the clients like? actual tv boxes or something?

Thanks for the quick reply.
The server is simply acting as a "player" that sends the video signal over a normal RCA video out.

Here is a snippet of his history. I'm seeing alot of telnet, which I assume means the player and scheduling is being controlled in telnet. 

I tried to open telnet and apparently the password he has set for it is different than the user account.

Is there anyway to reset the telnet password using sudo, and if so, can I do history within telnet?


  ```
33  telnet localhost 4140
   34  exit
   35  ls
   36  vi vlcSched
   37  vi vlcSched~
   38  pwd
   39  ls
   40  ls -l-
   41  ls -l
   42  sudo reboot
   43  telnet localhost 4140
   44  exit
   45  sudo reboot
   46  telnet localhost 4140
   47  exit
   48  telnet localhost 4140
   49  exit

```

---

### Post by aeiah on 2008-06-25
there should be yea. im not familiar with telnet apart from on routers but from what i can tell the username and password should be the server's user and password. have you made sure the telnet server is running? it often isnt because its pretty insecure, although if it didnt start on boot i guess you'd see it in the history file. hmm. maybe you can fish for a a telnet config file (i dunno where it is though but google will help, or perhaps:
```
find telnet
```

telnet localhost (which seems a little odd) is just looping back. perhaps vlc can be told what to do better in telnet than ssh so he was shh-ing into the server, then telnetting internally to control vlc?

the vlcSched is an obvious place to look for some clues but i guess you'll have looked there.

you should be able to view the telnet history once you get in, yea.

---

### Post by yltv on 2008-06-25
```
#!/bin/sh -e

vlc --vout=x11 --telnet-port 4140 &
xterm -e /home/dhowery/vlcTelnet.sh &

exit 0

```

That's in a file called vlcScript.sh


```

#!/usr/local/bin/expect
#set timeout 20
set PASSWORD admin
sleep 6

#Login to VLC Telnet
spawn telnet localhost 4140
expect "Password:"

#Send Password
send "$PASSWORD\r"
expect ">"

#Load Schedule file
send "load /home/dhowery/vlcSched\r"
expect ">"

#Start Auto Playing
#send "control Media play\r"
#expect ">"

#Exit VLC Telnet
send "exit\r"
expect eof

```

that's a file called vlcTelnet.sh

How do I find out when these scripts are launching and how do I use them? I hope these files are pretty big clues to how he was running it.

It is also important to note that VLC does have a Telnet interface, and has documentation on that interface, so I guess he was using ssh to log into the server then telnetting locally to control vlc...

---

### Post by jonty-comp on 2008-06-25
From what I can tell the first one starts VLC on the TV output, and the second one telnets into it's internal server and tells it to play.  Simply running the first .sh file in the same way he did in the history seems to be the way to do it.

---

### Post by yltv on 2008-06-25
> **jonty-comp said:**
> From what I can tell the first one starts VLC on the TV output, and the second one telnets into it's internal server and tells it to play.  Simply running the first .sh file in the same way he did in the history seems to be the way to do it.

I was thinking that too, but when I run it:

```
dhowery@vid-server003:~$ ./vlcScript.sh
VLC media player 0.8.6c Janus
dhowery@vid-server003:~$ [00000289] main interface: creating VLM
[00000289] telnet interface: using the VLM interface plugin...
[00000289] main interface error: cannot bind socket (Address already in use)
[00000289] main interface error: cannot bind socket (Address already in use)
[00000289] telnet interface error: cannot listen for telnet
[00000289] main interface error: no suitable interface module
[00000001] main private error: interface "telnet,none" initialization failed
xterm Xt error: Can't open display: :0
Error: Unable to initialize gtk, is DISPLAY set properly?
```

Which makes me think that the script has already been run on startup? 

I've posted on the VLC site forums but still haven't had a response. I appreciate any information that may help me put this together. I'm very new to Linux and how scripts work.

---

### Post by Technoviking on 2008-06-25
Have you rebooted the server? It should like a process maybe running and block the script from binding to that port.

Mike

---

### Post by yltv on 2008-06-25
> **Mike said:**
> Have you rebooted the server? It should like a process maybe running and block the script from binding to that port.

Mike

Oh yes, several times...

I think the biggest problem here is that I'm a linux noob... if I let a guru remote into the server they could probably look around and figure it out in no time.

Any takers?

If so call me at 601-415-3131. We will pay you for your trouble.

---

### Post by yltv on 2008-06-26
Ok, I finally figured out that telnet password.
When I logged into telnet I got:

```
Welcome, Master
>
> help
help
    Commands Syntax:
        new (name) vod|broadcast|schedule [properties]
        setup (name) (properties)
        show [(name)|media|schedule]
        del (name)|all|media|schedule
        control (name) [instance_name] (command)
        save (config_file)
        export
        load (config_file)
    Media Proprieties Syntax:
        input (input_name)
        inputdel (input_name)|all
        inputdeln input_number
        output (output_name)
        option (option_name)[=value]
        enabled|disabled
        loop|unloop (broadcast only)
        mux (mux_name)
    Schedule Proprieties Syntax:
        enabled|disabled
        append (command_until_rest_of_the_line)
        date (year)/(month)/(day)-(hour):(minutes):(seconds)|now
        period (years_aka_12_months)/(months_aka_30_days)/(days)-(hours):(minute                        s):(seconds)
        repeat (number_of_repetitions)
    Control Commands Syntax:
        play
        pause
        stop
        seek [+-](percentage) | [+-](seconds)s | [+-](milliseconds)ms

```

I guess I input my commands for VLC here and hopefully they write to an output file. I'll test it out tonight. Wish me luck.

---

### Post by yltv on 2008-06-26
Thanks so much for the help aeiah.

By looking at the history and doing some sleuthing, I was able to figure it all out.

---

### Post by aeiah on 2008-06-26
ah cool, i was wondering how this was going. glad it got sorted. sounds like a pretty interesting problem to solve with the investigating and such, even if you did have the stress of the company hemoragging loads of cash :cool: beats my daily grind of dealing with microsoft exchange server anyway

---

