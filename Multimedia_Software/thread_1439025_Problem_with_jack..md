---
title: "Problem with jack."
date: 2010-03-25
forum: Multimedia Software
---

### Post by dub.son on 2010-03-25
This maybe should be in the absolute begginers forum... as I am one!!!

I have installed ubuntu studio 9.10 and would really like to use the sound production software...

But when i open jack i get this message 

 p, li { white-space: pre-wrap; }  Could not connect to JACK server as client.
 - Overall operation failed.
 - Unable to connect to server.
 Please check the messages window for more info.


in the message window...


  p, li { white-space: pre-wrap; }  [COLOR=#999999]21:37:10.534 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]21:37:10.610 Statistics reset.[/COLOR]
 [COLOR=#66cc99]21:37:10.656 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]21:37:11.513 ALSA connection change.[/COLOR]
 [COLOR=#999999]21:41:44.572 Startup script...[/COLOR]
 [COLOR=#990099]21:41:44.572 artsshell -q terminate[/COLOR]
 [COLOR=#999999]sh: artsshell: not found[/COLOR]
 [COLOR=#999999]21:41:44.980 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]21:41:44.981 JACK is starting...[/COLOR]
 [COLOR=#990099]21:41:44.981 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]21:41:45.002 JACK was started with PID=3869.[/COLOR]
 [COLOR=#999999]no message buffer overruns[/COLOR]
 [COLOR=#999999]jackd 0.116.1[/COLOR]
 [COLOR=#999999]Copyright 2001-2005 Paul Davis and others.[/COLOR]
 [COLOR=#999999]jackd comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#999999]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#999999]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#999999]JACK compiled with System V SHM support.[/COLOR]
 [COLOR=#999999]cannot use real-time scheduling (FIFO at priority 10) [for thread -1216919872, from thread -1216919872] (1: Operation not permitted)[/COLOR]
 [COLOR=#999999]cannot create engine[/COLOR]
 [COLOR=#999999]21:41:45.047 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]21:41:45.048 Post-shutdown script...[/COLOR]
 [COLOR=#990099]21:41:45.048 killall jackd[/COLOR]
 [COLOR=#999999]jackd: no process found[/COLOR]
 [COLOR=#999999]21:41:45.485 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]21:41:47.138 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


[COLOR=#ff0000][COLOR=Black]When I open Ardour, and click new I get this message...[/COLOR][/COLOR] Also sorry if it's a repost but i couldn't find anything to that'd help.


Ardour could not start JACK

There are several possible reasons:

1) You requested audio parameters that are not supported..
2) JACK is running as another user.

Please consider the possibilities, and perhaps try different parameters.


Any help would be greatly appreciated!!

;)

---

### Post by dub.son on 2010-03-26
can anyone help!!

---

### Post by cchhrriiss121212 on 2010-03-26
Jack does not work on any machine out of the box with US, but this is going to be fixed in Lucid apparently. Jack is great once you get it working and you can't use audio programs in US to their full potential without it.
Anyway it is a simple fix:
Open a terminal and paste this in
```
sudo gedit /etc/security/limits.conf
```
Then add these lines to the text file
```
@audio - rtprio 99
@audio - memlock unlimited
@audio - nice &#8722;10
```
Save and exit the file, then reboot and try starting jack again. You may get Xruns in the message window which means the sample rate is too high.

---

### Post by dub.son on 2010-03-26
now in the message window it says

 p, li { white-space: pre-wrap; }  [COLOR=#999999]12:59:40.213 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:59:40.302 Statistics reset.[/COLOR]
 [COLOR=#66CC99]12:59:40.419 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]12:59:40.638 ALSA connection change.[/COLOR]

[COLOR=Black]I copied that code at the end of the file, before it said End of file, is that right?
[/COLOR]

---

### Post by cchhrriiss121212 on 2010-03-26
Yes thats right. The output you posted doesn't seem to be a problem. Is jack running now? The clock should be running if it is and you can start using Ardour and other programs by connecting them in the connections window or by using patchage.

---

### Post by dub.son on 2010-03-26
I'v added ardour in the jack input but when i try open a file in ardour it still says

Ardour could not start JACK

There are several possible reasons:

1) You requested audio parameters that are not supported..
2) JACK is running as another user.

Please consider the possibilities, and perhaps try different parameters.

---

### Post by cchhrriiss121212 on 2010-03-26
Are you sure jack is running when you start Ardour? You can't open Ardour without it.
It will look similar to this: [http://www.jensgulden.de/img/screenshot_qjackctl.png]("http://http//www.jensgulden.de/img/screenshot_qjackctl.png")

---

### Post by dub.son on 2010-03-26
jack is open when i start ardour. heres what my screen looks like

[IMG]http://img521.imageshack.us/img521/6213/jackardour.png[/IMG]

---

### Post by dub.son on 2010-03-26
> **cchhrriiss121212 said:**
> Are you sure jack is running when you start Ardour? You can't open Ardour without it.
It will look similar to this: [http://www.jensgulden.de/img/screenshot_qjackctl.png]("http://http//www.jensgulden.de/img/screenshot_qjackctl.png")

that page wont load

---

### Post by cchhrriiss121212 on 2010-03-26
Sorry about that link. Jack is open but not running, you need to press the start button. It will say rolling instead of stopped and the display will start counting upwards..

---

### Post by dub.son on 2010-03-26
when i press start an error message comes up reading

 p, li { white-space: pre-wrap; }  Could not connect to JACK server as client.
 - Overall operation failed.
 - Unable to connect to server.
 Please check the messages window for more info.

---

### Post by dub.son on 2010-03-26
message 

 p, li { white-space: pre-wrap; }  [COLOR=#999999]14:15:36.535 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]14:15:36.659 Statistics reset.[/COLOR]
 [COLOR=#66CC99]14:15:36.701 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]14:15:36.962 ALSA connection change.[/COLOR]
 [COLOR=#999999]14:15:42.600 Startup script...[/COLOR]
 [COLOR=#990099]14:15:42.601 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]14:15:43.015 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]14:15:43.016 JACK is starting...[/COLOR]
 [COLOR=#990099]14:15:43.017 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]14:15:43.023 JACK was started with PID=4894.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1215572288, from thread -1215572288] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]14:15:43.091 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]14:15:43.092 Post-shutdown script...[/COLOR]
 [COLOR=#990099]14:15:43.093 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]14:15:43.521 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]14:15:45.086 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

---

### Post by cchhrriiss121212 on 2010-03-26
> cannot use real-time scheduling

This is why jack will not start, but it should have been fixed earlier when you edited the limits.conf file.
Could you open up /etc/security/limits.conf and post what it says here?

---

### Post by dub.son on 2010-03-26
# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

@audio          -       rtprio          99
@audio - rtprio 99
@audio - memlock unlimited
@audio - nice &#8722;10

# End of file

---

### Post by cchhrriiss121212 on 2010-03-26
Your screenshot earlier seems to be of a plain desktop install of 9.10 (and not the Studio version). So I take it you installed the studio metapackage with synaptic from a regular Ubuntu. Is that right?
If so you will need to boot into the realtime kernel (which you is included in the studio package) in order to use realtime with jack. Download startup manager from synaptic and use it to set the default kernel to the rt variant. Then try jack again.

---

### Post by dub.son on 2010-03-26
I updated the standard 9.10 to the studio version using the code on the ubuntu studio website. then changed the style to one that I prefer. It's still the full US.

i just downloaded the startup manager, but there isn't anything in it about kernels.

---

### Post by cchhrriiss121212 on 2010-03-26
One difference between upgrading from standard and installing studio from a dvd is that you will still be using a non-rt kernel.
Startup manager has a tab called Boot Options and under Default Operating system you can choose what kernel to use. You should have had a real time kernel installed when you did the upgrade. If you don't see one there then you can get one from synaptic.

---

### Post by dub.son on 2010-03-26
set the rt as the default. but still get the same message when i start jack

 p, li { white-space: pre-wrap; }  [COLOR=#999999]18:29:28.786 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]18:29:28.790 Statistics reset.[/COLOR]
 [COLOR=#66CC99]18:29:28.845 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]18:29:29.040 ALSA connection change.[/COLOR]
 [COLOR=#999999]18:29:30.851 Startup script...[/COLOR]
 [COLOR=#990099]18:29:30.852 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]18:29:31.255 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]18:29:31.256 JACK is starting...[/COLOR]
 [COLOR=#990099]18:29:31.257 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]18:29:31.262 JACK was started with PID=2822.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1215650112, from thread -1215650112] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]18:29:31.631 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]18:29:31.632 Post-shutdown script...[/COLOR]
 [COLOR=#990099]18:29:31.633 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]18:29:32.059 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]18:29:33.493 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

---

### Post by cchhrriiss121212 on 2010-03-26
You will need to reboot in order to load the kernel.

---

### Post by dub.son on 2010-03-26
Yeh I did that.

---

### Post by cchhrriiss121212 on 2010-03-26
Check that you are a member of the audio group. I think "Users and Groups" is under the system tab somewhere. If not then add yourself to it.

---

### Post by dub.son on 2010-03-26
I am a member of an audio group

is it not to do with the bit that says

sh: artsshell: not found

---

### Post by cchhrriiss121212 on 2010-03-27
Thats just what is displayed when jack will not start. I'm nearly out of ideas on this but to get things running quickly you could just uncheck the realtime option in setup. 
Alternatively start up a new thread in the Ubuntu Studio section and post all the things you have checked off. Also double check all the fixes if you haven't already, you also have an rtprio line listed twice in limits.conf which could be deleted.

---

