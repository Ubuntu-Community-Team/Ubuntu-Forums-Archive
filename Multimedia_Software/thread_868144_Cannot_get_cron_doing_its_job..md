---
title: "Cannot get cron doing its job."
date: 2008-07-23
forum: Multimedia Software
---

### Post by nyborjare on 2008-07-23
Folks, I need your help.

I have two scripts

#!/bin/sh
NOW=$(date +"%b-%d-%y")
mplayer mms://wm-live.sr.se/sr-p1-high -ao pcm:file=/tmp/mystream.wav -vc dummy -vo null ;
lame -m s /tmp/mystream.wav -o /home/michael/Music/sommar/sommar-$NOW.mp3 ;
rm /tmp/mystream.wav ;

#!/bin/sh
pkill mplayer

When running these in Terminal all seems to work just fine
When running them in Kcron by "Start now" all seems to work fine
But Kcron does not start the job automatically on set time.

I have then looked at numerous threads and read all I can find about cron and have tried to make an automatic execution but no luck at all.

My crontab looks like this.

16 14 * * * export DISPLAY=:0 && /scripts/streamrecord

no action is started by this.

What am I doing wrong
Please help me, I have been working on this now for days and days.
I am new to all this 

Regars

---

### Post by KIAaze on 2008-07-23
Check your mail for error messages.
Just run the command "mail".
Type the number of the message you want to read to read it.

cronjobs results always get logged there. ;)

Also be careful with the environment: [http://www.adminschoice.com/docs/crontab.htm#Environment](http://www.adminschoice.com/docs/crontab.htm#Environment)
.bashrc and .bash_profile aren't used.

The export command should work however. I just did a quick test and it works.
Of course, you could always try defining the DISPLAY variable in the script.
Why do you need it for stream recording anyway?

---

### Post by nyborjare on 2008-07-24
KIAaze

Thank you for your reply.

Well first I have not the  
* mailx
* mailutils
installed but will do so.

Beeing totally new to this most of your reply is  ??? to me, sorry.

But why I need the cron for streaming.
Well I have thought that cron is an utility to schedule actions. I want a specific radio program to start at a set time and date and record for later use.

Appreciate further support in this matter.

Regards

---

### Post by KIAaze on 2008-07-24
> **nyborjare said:**
> KIAaze
But why I need the cron for streaming.
Well I have thought that cron is an utility to schedule actions. I want a specific radio program to start at a set time and date and record for later use.


No, I meant why do you need the "export DISPLAY=:0" command?
My guess is that you shouldn't need it since you only use non-graphical utilities.
Here's what the DISPLAY variable is used for:
[http://www.phys.ufl.edu/docs/emacs/emacs_488.html](http://www.phys.ufl.edu/docs/emacs/emacs_488.html)

Also, when do you run the second script "pkill mplayer"?
Is it to stop the recording?

I'll try running the whole script as cronjob myself to see if it works for me.

---

### Post by nyborjare on 2008-07-24
KIAaze
The Display - thing well I just put it there as I have seen it all the time in the posts about cron??
So you see what alevel of knowlage I have in this.

Yes the second sript is set in a second crontab to stop the recording at given time.

I have studies your link in your firs reply. 
"You can execute crontab if your name appears in the file /usr/lib/cron/cron.allow. If that file does not exist, you can use
crontab if your name does not appear in the file /usr/lib/cron/cron.deny.
If only cron.deny exists and is empty, all users can use crontab. If neither file exists, only the root user can use crontab"

I do not find those files mentioned here. So I understand I can only run a crontab as sudo su ??

I have tested this but no luck.

Another thing I have been thinking of. When i boot I see a lot of processes getting OK but Setting the system clock gets no OK
Could this be a reason why my cron jobs not work ??

Once again thank you for trying to help me.
Regards

---

### Post by nyborjare on 2008-07-24
KIAaze

:):):):):):):)

You have managed to get me to the point where my cron jobs work.

I have just tried them and what I did was take away the DISPLAY thing and not least. In terminal I logged in as su and set up my job.

I can tell you I have been on this for hours and days and weeks without luck.
Right now I am happy as a child on its birthday.

Millions of thanks to you and wish you all the best

Michael

---

### Post by KIAaze on 2008-07-24
Glad to have been helpful.

But you shouldn't need to have used su or sudo.
Putting the scripts in the normal user crontab should have worked too since they don't require root permissions (/tmp is writable without sudo).

If you put the scripts in the root crontab (by using su or sudo), it will create the "/home/michael/Music/sommar/sommar-$NOW.mp3" file so that it belongs to root and only root can modify/move/delete it, which may not be very practical for you.

> "You can execute crontab if your name appears in the file /usr/lib/cron/cron.allow. If that file does not exist, you can use
crontab if your name does not appear in the file /usr/lib/cron/cron.deny.
If only cron.deny exists and is empty, all users can use crontab. If neither file exists, only the root user can use crontab"

That's strange because I also don't have cron.allow and cron.deny, but I can use crontab as a normal user...

The official crontab manual (man crontab) is more correct here:
>  If the /etc/cron.allow file exists, then you must be  listed  therein  in  order  to  be  allowed  to  use  this  command.   If  the /etc/cron.allow  file  does not exist but the /etc/cron.deny file does exist, then you must not be listed in the /etc/cron.deny file in order to use this command.  **If neither of these files exists, then depending on site-dependent configuration parameters, only the super  user  will  be  allowed  to use this command, or all users will be able to use this command. For standard Debian systems, all users may use this command.**

So that explains why I can use crontab as a normal user and you should too. ;)


> Another thing I have been thinking of. When i boot I see a lot of processes getting OK but Setting the system clock gets no OK
Could this be a reason why my cron jobs not work ??

I don't know.

---

### Post by KIAaze on 2008-07-24
Finally tested it and it works well as a user. :)

Your scripts worked (just changed username and save location), but I think it's more logical this way:

start_recording.sh:
```
#!/bin/sh
mplayer mms://wm-live.sr.se/sr-p1-high -ao pcm:file=/tmp/mystream.wav -vc dummy -vo null ;

```

stop_recording.sh:
```
#!/bin/sh
pkill mplayer
NOW=$(date +"%b-%d-%y")
lame -m s /tmp/mystream.wav -o ~/Music/sommar-$NOW.mp3 ;
rm /tmp/mystream.wav ;

```

I don't listen to any radio online yet, but I can imagine a lot of people may find this useful.

---

### Post by nyborjare on 2008-07-24
KIAaze

Thanks again.
I will make some more tests tomorrow to se if I can get it running the "normal" way

Regards
michael

---

### Post by nyborjare on 2008-07-24
OK will test these aswell
Regards
michael

---

### Post by nyborjare on 2008-07-26
Sorry.
Moved my q here :
[http://ubuntuforums.org/showthread.php?p=5466793#post5466793](http://ubuntuforums.org/showthread.php?p=5466793#post5466793)

---

