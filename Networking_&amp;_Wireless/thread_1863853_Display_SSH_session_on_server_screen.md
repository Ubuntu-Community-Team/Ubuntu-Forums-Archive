---
title: "Display SSH session on server screen"
date: 2011-10-18
forum: Networking &amp; Wireless
---

### Post by rkem on 2011-10-18
Hello everyone!

In an effort to make the internet more distributed (eventually setting up a diaspora node etc.), I have begun to delve into Ubuntu server configuration and usage over SSH.

I currently have the following issue:

I have a laptop which connects to my server over SSH console. The server is attached to a physical screen output. I would now like to either display my SSH session (which I see on my laptop) on the physical server screen and/or know the proper commands to control the display remotely. Since I am just configuring the server and basically sitting in front of the server screen, I would like it to display my SSH session or specific sysadmin-monitoring tools so they don't use up the space on my laptop screen. I don't need X11 etc. The important point is of course that I don't need to attach any keyboard to the server in order to have its screen turn on and display. (It is powered on at startup but then suspends as there is no activity to be displayed)

Any help would be greatly appreciated.
Thanks!

---

### Post by nothingspecial on 2011-10-18
One solution would be to use screen.

Run screen on the server and give the session a name. Like so

```
screen -S banana
```

Log in via ssh from the remote machine and use the -x flag to attach to that sewssion

```
screen -x banana
```

Change banana for a more sensible name if you like.

---

### Post by rkem on 2011-10-18
Thank you for your reply.

Since there is only a single user account on the server, I log in via SSH, start screen, but upon attaching the screen it says "Attaching from inside of screen?". If I use two different log-ins (one for starting screen, the other for attaching), it appears to work. 
However, that doesn't show me anything on the server display. I would like to actually see my session on that display attached to the server.

Thanks for any further hints.

---

### Post by redmk2 on 2011-10-18
> **rkem said:**
> Thank you for your reply.

Since there is only a single user account on the server, I log in via SSH, start screen, but upon attaching the screen it says "Attaching from inside of screen?". If I use two different log-ins (one for starting screen, the other for attaching), it appears to work. 
However, that doesn't show me anything on the server display. I would like to actually see my session on that display attached to the server.

Thanks for any further hints.

I'm not quite sure I follow what you are doing.  One thing I can tell you is the ssh session from the laptop is really the **laptop user** remotely connecting to the server.  The laptop user could have the same user name, but it is still a separate user from any user that is created on the server.

As the laptop user is *not a server local user* to the Server you would not expect to see his session on the server at all.

As an example; from the ssh session you can check to see your identity by issuing this command ```
who
```

It will return something like this```

[COLOR="Blue"]redmk2[/COLOR]@[COLOR="Green"]triumph[/COLOR]:/smb/backup/manila>who
redmk2    pts/0        2011-10-18 10:45 ([COLOR="Red"]jaguar[/COLOR])

```

As you can see, I am on the host [COLOR="Green"]triumph[/COLOR].  The line shows that I ssh'd from the host [COLOR="Red"]jaguar[/COLOR]

---

### Post by rkem on 2011-10-18
> **redmk2 said:**
> I'm not quite sure I follow what you are doing.  One thing I can tell you is the ssh session from the laptop is really the **laptop user** remotely connecting to the server.  The laptop user could have the same user name, but it is still a separate user from any user that is created on the server.

As the laptop user is *not a server local user* to the Server you would not expect to see his session on the server at all.

As an example; from the ssh session you can check to see your identity by issuing this command ```
who
```It will return something like this```

[COLOR=Blue]redmk2[/COLOR]@[COLOR=Green]triumph[/COLOR]:/smb/backup/manila>who
redmk2    pts/0        2011-10-18 10:45 ([COLOR=Red]jaguar[/COLOR])

```As you can see, I am on the host [COLOR=Green]triumph[/COLOR].  The line shows that I ssh'd from the host [COLOR=Red]jaguar[/COLOR]

Of course you are correct, they are separate users (same name in my scenario). I would like the server to display the SSH session on its physical display output. Basically, I want it to display the same stuff that I see in my console SSH window on the laptop. Overall, I want to remotely control the server display and its output (showing my SSH session or some console tools). I hope my intention is clear now ;-).

Thanks!

---

### Post by redmk2 on 2011-10-18
> **rkem said:**
> Of course you are correct, they are separate users (same name in my scenario). I would like the server to display the SSH session on its physical display output. Basically, I want it to display the same stuff that I see in my console SSH window on the laptop. Overall, I want to remotely control the server display and its output (showing my SSH session or some console tools). I hope my intention is clear now ;-).

Thanks!

That would be a security breach of the highest magnitude.  As the user ssh'ing to the server you expect that you are the only one seeing your tty session.  After all ssh stands for **[COLOR="Red"]S[/COLOR]**ecure **[COLOR="Red"]Sh[/COLOR]**ell.  The ssh user is in control here and although I believe that the session can be redirected back (ssh in an ssh tunnel), I'm not so sure that the output (STDOUT) can be split into two streams.  

This is a lot of overhead for convenience.  Your server being GUI-less is a TTY and the only thing the appears on it is from its own sessions STDOUT.  The ssh session is a pseudo TTY (terminal in a GUI) it receives its output from its own separate STDOUT via the ssh connection.  Google the term STDOUT for more information.

You might try running 2 ssh sessions if you need to split up the data on to 2 terminals.  I do that all day.  I believe this is what *screen* does.  Maybe some more bells and whistles in one package.  

In addition, if your laptop is running Gnome on Linux you have multiple desktops. You could put a terminal session on each desktop.  I believe other Desktops (KDE, etc.) will do this too.

Hope this helps.

---

### Post by rkem on 2011-10-19
Thanks for the hints, I will try to learn about STDOUT. In my setup, it wouldn't be a security breach since I am the admin and just want to control the screen in front of me ;-) - but I understand your point.
Screen and multiple desktops etc. (I use Guake terminal e.g.) are handy, but I want to use the spare screen connected to the server.

---

### Post by redmk2 on 2011-10-19
> **rkem said:**
> Thanks for the hints, I will try to learn about STDOUT. In my setup, it wouldn't be a security breach since I am the admin and just want to control the screen in front of me ;-) - but I understand your point.
Think a little bit broader than just your setup.  If SSH  had the that capability it would be a vector for hackers.  This will never happen.> 

Screen and multiple desktops etc. (I use Guake terminal e.g.) are handy, but I want to use the spare screen connected to the server.
I don't think there is anything out there, but if there is, it won't involve SSH that's for sure.

---

