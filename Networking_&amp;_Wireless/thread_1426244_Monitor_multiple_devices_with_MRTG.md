---
title: "Monitor multiple devices with MRTG"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by majestiknl on 2010-03-10
Hello,

At the moment I'm taking my first steps into Ubuntu since I work at a IT department.

They asked me if I could find out how to monitor multiple devices (routers and switches) with MRTG. The program is up and running on Ubuntu Server but the next job is to monitor more devices.

I searched google and many people came up with another <devicename>.cfg file. I tried this but it won't work.

[Here]("http://www.iceflatline.com/?s=mrtg") is a tutorial I used to get MRTG to work on my Ubuntu Server.

My question: could someone please tell me how to add another device to MRTG?

Thanks for the support!

Tristan

ps, sorry for bad English ;)

---

### Post by majestiknl on 2010-03-10
Additional information:

The first <device name>.cfg will start to monitor, the second cfg file I try to start wont work.

I use the command [PHP]sudo env LANG=C /usr/bin/mrtg /etc/<folder>/<dev name>.cfg[/PHP] to start the cfg files. I think it has to be something with the command.

I also get an error: I Quit, mrtg is already running.

However, sometimes it will run and saying: Daemonizing.

Thanks!

---

### Post by Grenage on 2010-03-10
If you're running as a daemon then it will always be running in the background.  I personally don't have that, I just have a load of config files and a crontab entry for the scheduling.  For example, in my *crontab -e*:

```
*/5 * * * * env LANG=C mrtg /var/lib/mrtg/router1.cfg
*/5 * * * * env LANG=C mrtg /var/lib/mrtg/router2.cfg
```

I don't know if this is the best way to go about it, but it's easy to manage.

---

### Post by majestiknl on 2010-03-10
Thnx Grenage for your reply.

Im going to ty your advice.

I tried your given command (crontab -e) and it says I don't have one yet. Is this normal?

**Edit:**
Created the crontab file... what name should I give it and in what folder should the file be?

---

### Post by Grenage on 2010-03-10
It's normal if you haven't used it before.  It might be worth stopping MRTG from running as a daemon when the machine boots up, otherwise you'll probably run into the same problem.

---

### Post by majestiknl on 2010-03-10
Thanks for your reply, ill keep you updated :)

---

### Post by Grenage on 2010-03-10
You shouldn't need to manually create it yourself!  By typing "crontab -e" (as the user who will be running the commands) it should create it for you:

```
grenage@ubqd:~$ crontab -e
no crontab for grenage - using an empty one

Select an editor.  To change later, run 'select-editor'.
  1. /bin/ed
  2. /bin/nano        <---- easiest
  3. /usr/bin/vim.basic
  4. /usr/bin/vim.tiny
```

---

### Post by majestiknl on 2010-03-10
Hey Grenage,

I did what you said and I get the same message as you. I choose nano and then i get the following screen:

[PHP]GNU nano 2.0.9      file: /tmp/crontab.uRqFMC/crontab

# m h  dom mon dow   command[/PHP]

Then I typ the same as you but with my path to the cfg files and ofcourse their filename.

Then I say Write out and it askes for a file name to write to. So I choose the same folder as suggested by nano and I reboot.

But it won't start MRTG :(.

I think it's a really small thing I'm doing wrong...

---

### Post by Grenage on 2010-03-10
I think the crontab files are kept in /var/spool/cron/crontabs/, so mine would be /var/spool/cron/crontabs/grenage.

I've never used Nano (I'm a vim man), but it should work just as well!  Does the command (env LANG=C mrtg /var/lib/mrtg/*xxxxx*.cfg) work in the command line, now that MRTG is not running as a daemon?

---

### Post by majestiknl on 2010-03-10
> Does the command (env LANG=C mrtg /var/lib/mrtg/xxxxx.cfg) work in the command line, now that MRTG is not running as a daemon?

My command looks like this:

[PHP]sudo env LANG=C /usr/bin/mrtg /etc/mrtg-dev-1/router1.cfg[/PHP]

And yes, it works for only one device.

I'm going to try to find that folder/file and see if my crontab is there.

---

### Post by Grenage on 2010-03-10
If the command needs to be run as root, then you'll want to modify the crontab of root:

```
sudo -s
crontab -e
exit
```

---

### Post by majestiknl on 2010-03-10
Right now my crontab is created. After a reboot (and login) it wont start. 

My crontab looks like this:

[PHP]*/5 * * * * env LANG=C /usr/bin/mrtg /etc/mrtg-dev-1/router1.cfg[/PHP]

After the edit it said that the crontab was written and it is in the correct dir.

Thanks in advance

Edit:

Going to try your suggested sudo ;) seems i dont have some permissions.

---

### Post by Grenage on 2010-03-10
so *crontab -e* (as root) displays correctly but does not run, and the command works from the command line correctly?

> Going to try your suggested sudo  seems i dont have some permissions.

Ok!

---

### Post by majestiknl on 2010-03-10
Grenage, your the best. It works for one device, now I'm going to generate the next device and see if I van get it to work.

[-o<

---

### Post by Grenage on 2010-03-10
Glad to hear it's working! :)

---

### Post by majestiknl on 2010-03-10
Consider this topic is solved!

I really appreciate your help Grenage ;) both graphs are updating and I will add more to see how it works.

Was easier then I was thinking :P

Again, thanks for your help! :D

---

