---
title: "Why is this custom key command not working in Mythbuntu?"
date: 2012-07-16
forum: Mythbuntu
---

### Post by Dave M G on 2012-07-16
I want to set up my MythTV interface so that when I press f12, it executes a script called "powerbutton.sh" which toggles the monitor on and off.

I followed the instructions [here]("https://code.google.com/p/mythmote/issues/detail?id=56#c2") for connecting the key to my script. However, despite following the instructions to the letter, when I press f12, my script is not executed, and I can't understand why. I am confident the script itself is fine because I have been using it for years, and when I run it from the command line, it works.

I tried running mythfrontend from the command line, but there was nothing at the command prompt output related to pressing f12 that I could see.

What else do I need to do so that my script will execute when I press f12?

Here are the settings in my Mythbuntu interface:

[IMG]http://i.stack.imgur.com/w0klz.jpg[/IMG]

[IMG]http://i.stack.imgur.com/PZ2ln.jpg[/IMG]

---

### Post by nickrout on 2012-07-16
> **Dave M G said:**
> I want to set up my MythTV interface so that when I press f12, it executes a script called "powerbutton.sh" which toggles the monitor on and off.

I followed the instructions [here]("https://code.google.com/p/mythmote/issues/detail?id=56#c2") for connecting the key to my script. However, despite following the instructions to the letter, when I press f12, my script is not executed, and I can't understand why. I am confident the script itself is fine because I have been using it for years, and when I run it from the command line, it works.

I tried running mythfrontend from the command line, but there was nothing at the command prompt output related to pressing f12 that I could see.

What else do I need to do so that my script will execute when I press f12?

Here are the settings in my Mythbuntu interface:



shouldn't the entry start /bin/sh not sh?

---

### Post by azmyth on 2012-07-16
Who owns the powerbutton.sh file and who is running your mythtv

ls -al /path/to/powerbutton.sh

and 

ps -aux | grep myth

sounds like a permission issue

---

### Post by Dave M G on 2012-07-17
Thank you for the replies.

> shouldn't the entry start /bin/sh not sh?

I tried /bin/sh but it does not seem to change anything.

As for permissions and ownership, it looks like powerbutton.sh is owned by the user "mythbuntu" and has fully open permissions (777), and is executable:

```
-rwxrwxrwx  1 mythbuntu mythbuntu   180 Nov 22  2011 powerbutton.sh
```

If I'm reading the output correctly, the MythTV back end seems to be run by a user called "mythtv", and the front end by a user with the number 1000(?):

```
$ ps -aux | grep myth
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
avahi     1126  0.0  0.0   3568  1536 ?        S    Jul08   0:02 avahi-daemon: running [mythbuntu.local]
mythtv    1863  0.0  0.8 323960 36096 ?        Sl   Jul08   3:38 /usr/bin/mythbackend --syslog local7 --user mythtv
1000      2278  0.0  0.0   4060   204 ?        Ss   Jul08   0:01 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
1000      2281  0.0  0.0   3920   740 ?        S    Jul08   0:00 /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
1000      2336  0.0  0.0   2216   592 ?        S    Jul08   0:00 /bin/sh /usr/bin/mythfrontend --service
root      8365  0.0  0.0  10104  3420 ?        Ss   17:40   0:00 sshd: mythbuntu [priv]
1000      8548  0.1  0.0  10252  1772 ?        S    17:40   0:00 sshd: mythbuntu@notty
1000      8624  0.0  0.0   4132   836 pts/3    S+   17:41   0:00 grep --color=auto myth
1000     12749  1.7  6.9 618604 288348 ?       Sl   Jul11 148:53 /usr/bin/mythfrontend.real --syslog local7
root     19353  0.0  0.0  10104  3420 ?        Ss   Jul14   0:00 sshd: mythbuntu [priv]
1000     19491  0.0  0.0  11888  3376 ?        S    Jul14   0:07 sshd: mythbuntu@notty
root     19493  0.0  0.0  10104  3420 ?        Ss   Jul14   0:00 sshd: mythbuntu [priv]
1000     19631  0.0  0.0  11216  2780 ?        S    Jul14   1:33 sshd: mythbuntu@notty
1000     19786  0.0  0.0   6288  2200 ?        S    Jul14   0:00 
root     22117  0.0  0.0  10104  3496 ?        Ss   Jul16   0:00 sshd: mythbuntu [priv]
1000     22255  0.0  0.0  10104  1864 ?        S    Jul16   0:00 sshd: mythbuntu@pts/2
```

Does any of that shed light on why the command might not be running?

---

### Post by nickrout on 2012-07-17
mythfrontend should run as the user you set up during install. Looks like you have somehow not given that user a proper name, or tried to delete it?

```
grep 1000 /etc/passwd
```

---

### Post by Dave M G on 2012-07-18
Turns out, user 1000 = user mythbuntu. Explanation [here]("http://askubuntu.com/a/165028/17041").

So I guess I'm still looking for a reason why this command is not executing.

---

### Post by azmyth on 2012-07-18
When I setup my system, I added my username to the mythtv group as this avoid permission issues I was seeing.

---

### Post by Dave M G on 2012-07-18
My user is already added to the mythtv group as far as I can tell.

```
$ groups mythbuntu
mythbuntu : mythbuntu adm dialout cdrom video plugdev fuse admin mythtv sambashare lpadmin
```

---

### Post by azmyth on 2012-07-18
I would try two things. First of all, I'd try a simple command instead of the script. Something like

touch /path/to/file

with and without the quotes.

I'd also use phpmyadmin and make sure it's actually assigning the f12 key to the script.

---

### Post by Dave M G on 2012-07-19
The keybinding seems to be in my database:

```
context	action		description			keylist		hostname
Global	SYSEVENT01	Trigger System Key Event #1	F12		mythbuntu
```

I tried the touch command. I verified it worked directly from the command line, but it does not work from within MythTV with the keybinding.

So it would seem the problem is that the keybinding is not executing the command.

---

### Post by nickrout on 2012-07-19
> **Dave M G said:**
> The keybinding seems to be in my database:

```
context	action		description			keylist		hostname
Global	SYSEVENT01	Trigger System Key Event #1	F12		mythbuntu
```

I tried the touch command. I verified it worked directly from the command line, but it does not work from within MythTV with the keybinding.

So it would seem the problem is that the keybinding is not executing the command.

Again I suspect you need to give the full path to the touch command, ie /usr/bin/touch.

If that works then try adding a PATH= line to the start of your power script, or give the full path to all commands in it.

Also. what happens when you hit f12 on the keyboard?

---

### Post by Dave M G on 2012-07-19
Unfortunately, using the full path, /usr/bin/touch, did not change anything.

I have been testing all along by hitting f12 on the keyboard. Nothing happens.

---

### Post by nickrout on 2012-07-19
> **Dave M G said:**
> Unfortunately, using the full path, /usr/bin/touch, did not change anything.

I have been testing all along by hitting f12 on the keyboard. Nothing happens.

OK its probably not an environment thing then.

F12 has alot of bindings, where are you in mythtv when you try it? I think specific contexts trump global settings.

Having said that I just tried to emulate what you have done and F12 touches the correct file. *puzzled*

---

### Post by Dave M G on 2012-07-19
I found an error in my mythbackend.log. (There's a lot in there and I missed it before).

```
Jul 19 15:55:47 mythbuntu mythbackend[1863]: W SystemEvent mythsystemevent.cpp:55 (run) MythSystemEventHandler: Command '/bin/sh /home/mythbuntu/Buttons/powerbutton.sh' returned 127
```

I looked up what 127 means, and it means "command not found".

But, /bin is on my path:

```
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/mythbuntu/Buttons:/home/mythbuntu
```

So why is it not finding the command?

---

### Post by nickrout on 2012-07-19
> **Dave M G said:**
> I found an error in my mythbackend.log. (There's a lot in there and I missed it before).

```
Jul 19 15:55:47 mythbuntu mythbackend[1863]: W SystemEvent mythsystemevent.cpp:55 (run) MythSystemEventHandler: Command '/bin/sh /home/mythbuntu/Buttons/powerbutton.sh' returned 127
```

I looked up what 127 means, and it means "command not found".

But, /bin is on my path:

```
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/mythbuntu/Buttons:/home/mythbuntu
```

So why is it not finding the command?

? Something inside the script not found? (Can you post the script contents please)

? mythbackend runs as user mythtv so does not necessarily have the same environment (including PATH) as you do. However /bin should be in its PATH.

---

### Post by nickrout on 2012-07-19
Can user mythtv access /home/mythbuntu/Buttons/powerbutton.sh ?

```
sudo su - mythtv
sh /home/mythbuntu/Buttons/powerbutton.sh
```

Why not put powerbutton.sh in /usr/bin and leave /bin/sh out of it? Assuming powerbutton.sh has the proper shebang on the first line, ie:```
#!/bin/sh
``` 

you can 

```
sudo mv /home/mythbuntu/Buttons/powerbutton.sh /usr/bin
sudo chmod +x /usr/bin/powerbutton.sh
```

Then simply make the script to execute powerbutton.sh

---

