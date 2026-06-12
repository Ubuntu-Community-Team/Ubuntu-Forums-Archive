---
title: "Jack Control"
date: 2010-05-30
forum: Multimedia Software
---

### Post by Komputor on 2010-05-30
HELP!! lol
After installing Jack Control for some audio programs,  I tried to set it up -HA!  Well, maybe I'm still a little too new at this, but I am having one heck of a time setting this up so I can move on and start making some music!  
Readout from the message window is as follows:
 p, li { white-space: pre-wrap; }  [COLOR=#999999]01:07:01.642 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]01:07:01.643 Statistics reset.[/COLOR]
 [COLOR=#66CC99]01:07:01.736 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]01:07:01.932 ALSA connection change.[/COLOR]
 [COLOR=#999999]01:07:04.586 Startup script...[/COLOR]
 [COLOR=#990099]01:07:04.587 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]01:07:04.990 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]01:07:04.990 JACK is starting...[/COLOR]
 [COLOR=#990099]01:07:04.991 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]01:07:04.996 JACK was started with PID=2601.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 Your system has an audio group, but you are not a member of it.
 Please add yourself to the audio group by executing (as root):
   usermod -a -G audio (null)
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]01:07:05.020 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]01:07:05.021 Post-shutdown script...[/COLOR]
 [COLOR=#990099]01:07:05.021 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]01:07:05.432 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]01:07:07.145 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

When I tried to add myself to the audio group by executing the script above, I got this:
 p, li { white-space: pre-wrap; }  [COLOR=#999999][/COLOR]bash: syntax error near unexpected token `('



Just looking for someone to please shed a little light on this; thanks in advance to all who can
-Josh

---

### Post by luctor on 2010-05-30
just use Users and Groups app in System/Administration

---

### Post by cchhrriiss121212 on 2010-05-30
> JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
This is also a problem you need to solve. Either uncheck realtime in jack setup, or sudo gedit /etc/security/limits.conf and make sure these lines are present:
@audio - rtprio 99
@audio - memlock unlimited

---

### Post by Komputor on 2010-05-30
> **cchhrriiss121212 said:**
> This is also a problem you need to solve. Either uncheck realtime in jack setup, or sudo gedit /etc/security/limits.conf and make sure these lines are present:
@audio - rtprio 99
@audio - memlock unlimited
 
I am not sure about the second line, but I know I had to insert the rtprio 99 line.  I will confirm/insert the second one if needed, thanks!

---

### Post by Komputor on 2010-05-31
@luctor,
  Using the users/groups app, I was able to add myself to the audio group, BUT when I start JACK, I still get the output I originally posted :(  Back to square one.  I would like to get Ardour working, but I can't without having JACK up.

---

### Post by Komputor on 2010-06-01
Getting very annoyed and frustrated now!  I installed the Ubuntu Studio 10.4 with the real time kernel to see if it helped anything.  Took it a little while to install but not too long at all.  The only thing it seemed to do was install the real time kernel, and update and install a TON of apps.  Also seemed to change some configuration files to make everything work smoothly.  What it did NOT do was remove any of my user info, or the original version of Ubuntu Lucid I was using before (in fact, it ADDED another boot option to the Grub menu so now I have the option of booting either Lucid, Studio, or Vista, WITH the recovery mode for 3 versions of Ubuntu -Not sure what's up with that).

1- Good news, I got Jack started without the real time option, and had myself added to the audio group with no problem; Very bad news, EVERY time I change it to real time now, it wants to be a bad app and say that I need to change memlock option from unlimited, to 1052490 in /etc/security/limits.conf.  I had updated limits.conf to reflect the suggested correction and Jack still comes back with this problem EVERY time.
2- After reverting back to de-selecting real time option in Jack control, and wanting to run apps that require Jack to output any audio, NOTHING happens!!!
3- Tried to use DJPlay app and it will load my mp3 files just fine, but will not -absolutely will NOT- play any song file I throw at it regardless of file type(mp3, wav, etc).  WTF?!?!?!?!?
4-Ttried to open Patchage to set up programs and outputs, NOTHING happens
5-Ardour will not start without Jack control being set up correctly.

I thought Ubuntu Studio and all of these apps were supposed to come pretty much pre-configured so all that needs to happen is install and good to go.  This is keeping me from making music and I am very tired of setting things up so that I can!  Can someone with ANY knowledge of what is going on here PLEASE help me.

---

### Post by cchhrriiss121212 on 2010-06-01
I can help you with this, but you should probably give it a break for short while so you don't get too frustrated, which will only make things more difficult (and we've all been there).
> **Komputor said:**
> Getting very annoyed and frustrated now!  I installed the Ubuntu Studio 10.4 with the real time kernel to see if it helped anything.  Took it a little while to install but not too long at all.  The only thing it seemed to do was install the real time kernel, and update and install a TON of apps.  Also seemed to change some configuration files to make everything work smoothly.  What it did NOT do was remove any of my user info, or the original version of Ubuntu Lucid I was using before (in fact, it ADDED another boot option to the Grub menu so now I have the option of booting either Lucid, Studio, or Vista, WITH the recovery mode for 3 versions of Ubuntu -Not sure what's up with that).
It seems like you have installed studio side by side with the rest of your partitions, which is an option you get when installing. If you want just one Ubuntu on there, you can delete the first partition from a live cd environment using gparted. The installation of Ubuntu will only do what you tell it to do, so perhaps plan out what you are going to do first next time.


> 1- Good news, I got Jack started without the real time option, and had myself added to the audio group with no problem; Very bad news, EVERY time I change it to real time now, it wants to be a bad app and say that I need to change memlock option from unlimited, to 1052490 in /etc/security/limits.conf. I had updated limits.conf to reflect the suggested correction and Jack still comes back with this problem EVERY time.
That memlock warning is normal, and you can just ignore it as it won't stop jack from working normally.

Could you select the realtime option in setup, press start and then show what jack has in the message window? Like you did in the first post

> 3- Tried to use DJPlay app and it will load my mp3 files just fine, but will not -absolutely will NOT- play any song file I throw at it regardless of file type(mp3, wav, etc). WTF?!?!?!?!?
4-Ttried to open Patchage to set up programs and outputs, NOTHING happens
5-Ardour will not start without Jack control being set up correctly.
Install ubuntu-restricted-extras to enable mp3 playback and loads of other useful codecs. I would forget about running other music apps until you get jack working as it should do.

> I thought Ubuntu Studio and all of these apps were supposed to come pretty much pre-configured so all that needs to happen is install and good to go.
In a perfect world it would do just that, but due to users different setups it will rarely occur. Studio is just a group of packages with a new theme and a different kernel, so don't expect it to be any easier than regular Ubuntu.

---

### Post by Komputor on 2010-06-01
Message that appears now every time I start Jack:
 p, li { white-space: pre-wrap; }  [COLOR=#999999]18:49:10.279 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]18:49:10.283 Statistics reset.[/COLOR]
 [COLOR=#66CC99]18:49:10.477 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]18:49:10.690 ALSA connection change.[/COLOR]
 [COLOR=#999999]18:49:19.417 Startup script...[/COLOR]
 [COLOR=#990099]18:49:19.418 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]18:49:19.828 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]18:49:19.830 JACK is starting...[/COLOR]
 [COLOR=#990099]18:49:19.832 /usr/bin/jackd -dalsa -dhw:0,0 -r44100 -p1024 -n3[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1052490
 [COLOR=#999999]18:49:19.873 JACK was started with PID=5591.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0,0|hw:0,0|1024|3|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 [COLOR=#999999]18:49:20.625 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]18:49:20.626 Post-shutdown script...[/COLOR]
 [COLOR=#990099]18:49:20.627 killall jackd[/COLOR]
 [COLOR=#CC3366]18:49:20.627 JACK has crashed.[/COLOR]
 jackd: no process found
 [COLOR=#999999]18:49:21.039 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]18:49:21.889 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

Again, I have already modified the limits.conf file to reflect the memlock suggestion above, but it will not recognize that it changed.

I will try the ubuntu-restricted-extras option, will give feedback.

As for side-by-side installation, how would I remove the previous installations without a live cd?  I installed Ubuntu originally using a bootable usb stick, so would that be the same or can I just use gparted in Ubuntu Studio and modify my partitions there?

---

### Post by Komputor on 2010-06-01
Output of my limits.conf file:
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
#@audio          -       rtprio          99

#@audio          -       nice            -19
#@audio          -       memlock         1052490

# End of file

See where my frustration begins?  As Jack's message output suggests, memlock should be set to a number as I have set as indicated by the above output from the file itself. !@#$%^&  Not making very much sense to me at all.

---

### Post by cchhrriiss121212 on 2010-06-01
The problem here is that you have used # on each @audio line. # is used to denote a comment, which means that any line beginning with # will be ignored by the system. The other lines you see in your limits.conf file are examples.

Also, you need to be in a live environment to edit partitions, as the drive needs to be unmounted. So boot from the usb stick if thats your only option.

---

### Post by Komputor on 2010-06-01
Deleting the #'s from the file only seemed to make Jack WORSE!  I am not sure what is going on here, but after modifying the file(taking away the #'s for every @audio line), starting up Jack again, It almost took over my whole system!  First, Jack greyed out as if it was just not responding/crashed.  Next, I couldn't force close Jack, and I couldn't even open a terminal window to kill it!  After that, I started losing icons on my panel(esp. the important one that allows me to restart my system)!  Apps started crashing in my dock that I have set up in the lower center of my desktop, and I resolved to going through System>Shut Down and selecting restart -but it only logged me out!  I was able to restart again from the login screen but WOW!  What is going on???
Should I just revert the limits.conf file and enter each line separately with a reboot after each to identify the culprit, or do I have too many instances of Ubuntu on my system that may be interfering with each other?

---

### Post by Komputor on 2010-06-01
Oh and I rebooted after taking away the #'s.  Hope that helps!

---

### Post by Komputor on 2010-06-01
Success at last!!  I think the problem was in my code (always trust the code).  Instead of setting my "memlock" to a specified number, I just changed it to unlimited.  Instead of having "nice" set to -19, I set it to -10.
I am not sure what I did with having it the other way before, but now Jack message output is as follows:
 p, li { white-space: pre-wrap; }  [COLOR=#999999]21:39:41.291 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]21:39:41.315 Statistics reset.[/COLOR]
 [COLOR=#66CC99]21:39:41.467 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]21:39:41.620 ALSA connection change.[/COLOR]
 [COLOR=#999999]21:40:33.661 Startup script...[/COLOR]
 [COLOR=#990099]21:40:33.662 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]21:40:34.064 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]21:40:34.065 JACK is starting...[/COLOR]
 [COLOR=#990099]21:40:34.065 /usr/bin/jackd -dalsa -dhw:0,0 -r44100 -p1024 -n2[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1052490
 [COLOR=#999999]21:40:34.096 JACK was started with PID=4640.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0,0|hw:0,0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 [COLOR=#999933]21:40:36.191 Server configuration saved to "/home/komputor/.jackdrc".[/COLOR]
 [COLOR=#999999]21:40:36.193 Statistics reset.[/COLOR]
 [COLOR=#999999]21:40:36.705 Client activated.[/COLOR]
 [COLOR=#9999CC]21:40:36.707 JACK connection change.[/COLOR]
 [COLOR=#CC9966]21:40:36.713 JACK connection graph change.[/COLOR]
#end of msg

And now Jack is showing RT up and running!

---

### Post by Komputor on 2010-06-01
Now to see about configuring Ardour, and others to play along!

---

### Post by ken78724 on 2010-06-01
Komputer & cchhrriiss121212   Many, many thanks!!!!

Can someone post a sticky. you've done most valuable work UbuStudio users are crying for. But, not enough is said for me to reach the jack control solution you've achieved. I want to hear sound and get past what blocks me/all of us.

I pray someone will write a simple 1,2,3,,, it'd be welcomed.   :popcorn:  Please someone that can ,,, I'll pore the beer... Ken:guitar:

---

### Post by Komputor on 2010-06-02
Ken,
 Thank you very much, but every system is different as Chris said before.  With that said, I don't think I can be of much help with this thread anymore, so I am moving on with the next step in another thread.  Hope this helped you and any others having this issue.

---

### Post by cchhrriiss121212 on 2010-06-02
@Komputer - Glad you got things running. If you are recording live instruments with ardour then you may want to experiment with lowering the frame rate to get a lower latency. Anything <=10ms will be good but it depends on the quality of soundcard you have, so anything integrated will not handle much.

@Ken - There should definately be a sticky on jack somehwere here but for the time being you can look at the [community documentation.]("https://help.ubuntu.com/community/UbuntuStudioPreparation")
Try starting a new thread and post the error messages you are getting just like this thread.

---

### Post by rlameiro on 2010-06-02
I should remind, that as from Lucid, the configuration file isn't at /etc/security/limits.conf, but on /etc/security/limits.d/audio.conf

refer to the Ubuntu Studio preparation help 

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by cchhrriiss121212 on 2010-06-02
Good point, I'm not using lucid yet, but the StudioPrep document says this:
> Since **Ubuntu 10.10**, the version of Jackd write all needed informations in this file
So is that an error?

I'd also like to know why this has been changed if anyone knows

---

### Post by Komputor on 2010-06-02
rlameiro,
 I am not sure about that file location, just a heads up, I am running Ubuntu 10.04, Lucid and I do have the /etc/security/lmits.conf file that Jack uses.  Unless you are referring to a different app/topic altogether.

So I opened that file in limits.d/audio.conf and here's my output:
# generated by jackd's postinst.
#
# Do not edit this file by hand, use
#
#    dpkg-reconfigure -p high jackd
#
# instead.
@audio   -  rtprio     99
@audio   -  memlock    unlimited
#@audio   -  nice      -19

Is there anything wrong here?  Let me know, Thanks!

---

### Post by Komputor on 2010-06-02
WHY OH WHY???  Am I really that unfortunate?
 Just out of curiosity, I decided to run Jack again to make sure everything was still good.  Alas, all is not well.
Output from Jack's message:
 p, li { white-space: pre-wrap; }  [COLOR=#999999]19:27:10.707 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]19:27:10.729 Statistics reset.[/COLOR]
 [COLOR=#66CC99]19:27:10.839 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]19:27:11.003 ALSA connection change.[/COLOR]
 [COLOR=#999999]19:27:14.880 Startup script...[/COLOR]
 [COLOR=#990099]19:27:14.882 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]19:27:15.285 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]19:27:15.286 JACK is starting...[/COLOR]
 [COLOR=#990099]19:27:15.286 /usr/bin/jackd -t1000 -dalsa -dhw:0 -r44100 -p256 -n2[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1059984
 [COLOR=#999999]19:27:15.314 JACK was started with PID=2321.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 [COLOR=#FF0000]19:27:17.451 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 could not attach as JACK client (server has exited)
 [COLOR=#999999]19:27:17.587 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]19:27:17.588 Post-shutdown script...[/COLOR]
 [COLOR=#990099]19:27:17.592 killall jackd[/COLOR]
 [COLOR=#CC3366]19:27:17.593 JACK has crashed.[/COLOR]
 jackd: no process found
 [COLOR=#999999]19:27:18.018 Post-shutdown script terminated with exit status=256.[/COLOR]
AGAIN with the memlock suggestion.
And the output from the /etc/security/limits.conf file:
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
@audio          -       nice            -10
@audio          -       memlock         unlimited

# End of file
Would REALLY like to know what is happening!?!?!?!

---

### Post by Komputor on 2010-06-02
Oh and by the way, the problem that happened before where Jack almost took over my system happened AGAIN!!!

---

### Post by cchhrriiss121212 on 2010-06-03
Could be that there is another process running using sound, so when starting jack close everything like firefox beforehand.

---

