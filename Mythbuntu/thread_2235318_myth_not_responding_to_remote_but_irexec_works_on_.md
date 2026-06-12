---
title: "myth not responding to remote but irexec works on mythbuntu 14.04"
date: 2014-07-20
forum: Mythbuntu
---

### Post by Marc_Aronson on 2014-07-20
I upgraded from mythbuntu 12.04 to 14.04 by doing a clean install of 14.04, restoring my database and letting mythtv-setup upgrade the database.

I also upgraded to new hardware (From Core 2 DUO to intel NUC).

mythtv isn't responding to the remote. IREXEC does respond as expected to the remote.

The output from "irw" and "ircat mythtv" suggest that things are configured properly, but the mythfrontend is clearly not responding.

Below is some additional diagnostic information -- any help on this would be greatly appreciated!

Marc

Output from IRW
```
aronson@MB2-Cup:~/.lirc$ irw000000037ff07be0 00 KEY_DOWN mceusb
000000037ff07be0 00 KEY_DOWN mceusb
000000037ff07be1 00 KEY_UP mceusb
000000037ff07be1 00 KEY_UP mceusb
000000037ff07bde 00 KEY_RIGHT mceusb
000000037ff07bde 01 KEY_RIGHT mceusb
000000037ff07bdf 00 KEY_LEFT mceusb
000000037ff07bde 00 KEY_RIGHT mceusb
000000037ff07bde 01 KEY_RIGHT mceusb
000000037ff07bdd 00 KEY_OK mceusb
000000037ff07bdd 01 KEY_OK mceusb

```
Output from "ircat mythtv"
```
aronson@MB2-Cup:/run/lirc$ ircat mythtv
Down
Down
Up
Up
Right
Left
Right
Return

```
Output from 3 separate "ps auxw | grep <target>", with <target> set to lircd, irw and myth
```
aronson@MB2-Cup:~/.lirc$ ps auxw | grep lircd
root     14139  0.0  0.0  33108   692 ?        Ss   07:54   0:00 /usr/sbin/lircd --output=/run/lirc/lircd --device=/dev/lirc0
aronson  14203  0.0  0.0  10464   916 pts/3    S+   08:05   0:00 grep --color=auto lircd
aronson@MB2-Cup:~/.lirc$ ps auxw | grep irw
aronson  14147  0.0  0.0   4192   356 pts/2    S+   07:54   0:00 irw
aronson  14205  0.0  0.0  10464   916 pts/3    S+   08:05   0:00 grep --color=auto irw
aronson@MB2-Cup:~/.lirc$ ps auxw | grep myth
mythtv    2266 12.3  0.8 4813240 67036 ?       Ssl  Jul19  67:06 /usr/bin/mythbackend --syslog local7 --user mythtv --daemon
aronson  13887  0.0  0.0  10616   320 ?        Ss   07:54   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
aronson  13890  0.0  0.0  24440   580 ?        S    07:54   0:00 /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
aronson  13935  0.0  0.0   4444   716 ?        S    07:54   0:00 /bin/sh /usr/bin/mythfrontend --service
aronson  13968  3.2  1.4 5897796 116548 ?      Sl   07:54   0:20 /usr/bin/mythfrontend.real --syslog local7
aronson  14148  0.0  0.0   6404   720 pts/0    S+   07:54   0:00 ircat mythtv
aronson  14207  0.0  0.0  10468   912 pts/3    S+   08:05   0:00 grep --color=auto myth



```

---

### Post by khPWXxF on 2014-07-20
Do you have a file ~/.mythtv/lircrc – possibly it's a link to ~/.lirc/mythtv
   Does it contain lines like this?
   > begin[INDENT]remote = mceusb
       prog = mythtv
       button = KEY_OK
       config = Return
       repeat = 0
       delay = 0
[/INDENT]
 end
   Does it have read permissions? 
   
  Phil

---

### Post by Marc_Aronson on 2014-07-20
thank you for replying. 

yes,  those files exist and are rradable.  that is why the ircat is exhibiting appropriate behavior. 

it seems like the myth backend doesn't get the messages.

---

### Post by khPWXxF on 2014-07-20
> 

it seems like the myth backend doesn't get the messages.
Do you mean frontend?
Phil

---

### Post by Marc_Aronson on 2014-07-20
yes,  meant frontend,  not backend.  my bad.

---

### Post by DaveQB on 2014-07-20
Just a thought, have you tried an strace on the lircd process?

---

### Post by Marc_Aronson on 2014-07-21
Found the problem!

I had a scenario where I was starting the mythfrontend first, following by LIRC. In 14.04 it appears that LIRC needs to be started first. When I start LIRC first, following by mythfrontend, everything works properly.

Phil, thanks for taking the time to reply and contribute your ideas -- very much appreciated!

Marc

---

### Post by joe145 on 2014-11-04
> **Marc_Aronson said:**
> Found the problem!

I had a scenario where I was starting the mythfrontend first, following by LIRC. In 14.04 it appears that LIRC needs to be started first. When I start LIRC first, following by mythfrontend, everything works properly.

Phil, thanks for taking the time to reply and contribute your ideas -- very much appreciated!

Marc

What do you need to do to find out what your load order is? I have the same problem and would like to see if this solves it.

Thanks!

---

### Post by Marc_Aronson on 2014-12-28
> **joe145 said:**
> What do you need to do to find out what your load order is? I have the same problem and would like to see if this solves it.

Thanks!

Sorry for the delayed response.

I have a script that I run that simply starts LIRC first, and then starts the myth frontend. Here is a snipet from that script:

```
      echo "Starting lirc..."
      sudo service lirc start
      sleep 3
      echo "Starting lightdm..."
      sudo service lightdm start
      sleep 3

```

Hope this helps!

Marc

---

