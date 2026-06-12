---
title: "run a GUI program through ssh, but on server?"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by olof_ on 2010-12-22
hello out there!
after spending my day understanding the power of ssh I have been running into this issue.
how to achieve the following?

computer [COLOR="DarkRed"]A[/COLOR] connects to computer [COLOR="DarkGreen"]b[/COLOR].

computer A starts a grapical (GUI) program through the ssh connection *and it starts on computer [COLOR="DarkGreen"]b[/COLOR].*

I do have understanding about the -Y "flag", but while using it the program only starts on the computer [COLOR="DarkRed"]A[/COLOR] in the preceding example, and not on the computer [COLOR="DarkGreen"]b[/COLOR].

and yes, I have been searching about this problem, but I couldnt find it out.

---

### Post by gmargo on 2010-12-22
What program(s) are you talking about?  I actually saw this happen with firefox and it surprised me.  (When firefox was not already running on computer A, it acted as I expected - running on B and displaying on A.)

---

### Post by olof_ on 2010-12-23
about any program actually.
Vlc, firefox, notify-send, gedit etc.

---

### Post by gmargo on 2010-12-23
How about xterm?

---

### Post by olof_ on 2010-12-26
```

ssh username@192.168.1.17
[things not of interest]
username@hokatorp-serv:~$ xterm
xterm Xt error: Can't open display: 
xterm:  DISPLAY is not set
```

---

### Post by tgalati4 on 2010-12-26
You need to set the DISPLAY variable.

setenv

---

### Post by msandoy on 2010-12-26
I might be misunderstand you completely, but if you want to start a GUI program on Computer B, and see the GUI on Computer A, all you need to do is:
```

ssh -X username@ipadress

```
And then ofcourse start the desired app.

---

### Post by olof_ on 2010-12-27
> **tgalati4 said:**
> You need to set the DISPLAY variable.

setenv

thank you.
I did some search on setenv, and came up with this:
```

setenv DISPLAY localhost:0.0

```

but:
```
No command 'setenv' found, did you mean:
Command 'netenv' from package 'netenv' (universe)
setenv: command not found
```

I tried some different options, like:
```

setenv() DISPLAY localhost:0.0

setenv(DISPLAY localhost:0.0)

setenv DISPLAY=localhost:0.0

setenv DISPLAY localhost=0.0

setenv DISPLAY localhost:0

```

I also tried with the computers ip-address, but with the same result. and sudo, but then it did not work at all.

but none of the above commands work.

edit: also tried the following with no success:

```

sh -c ENV=$DISPLAY localhost:0.0

```

---

### Post by olof_ on 2010-12-27
> **msandoy said:**
> I might be misunderstand you completely, but if you want to start a GUI program on Computer B, and see the GUI on Computer A, all you need to do is:
```

ssh -X username@ipadress

```
And then ofcourse start the desired app.

I know about both -X and -Y, but that is not what I want to do. I want to start a GUI program on Computer B through ssh, and see the GUI on Computer B.

maybe I was a bit unclear about that. thank you for your reply anyways.

---

### Post by gmargo on 2010-12-27
To set the DISPLAY environment variable in bash syntax (setenv is for csh syntax):
```

export DISPLAY=:0

```

---

### Post by nerdy_kid on 2010-12-27
this is how I do it:

```
ssh -X user@host
```

then inside the ssh session:


```
w
```

find the screen you want, for me it is :0

then

```
export DISPLAY=:0
```

```
gui-app
```

---

### Post by nerdy_kid on 2010-12-27
<snip>

---

### Post by nerdy_kid on 2010-12-27
<snip>

---

### Post by nerdy_kid on 2010-12-27
UF is screwed up, sorry for the above.

---

### Post by olof_ on 2010-12-27
Thank you so much!!
I got it working now!

---

### Post by olof_ on 2010-12-27
oh, sorry to say this but now the original behavour of ssh -Y is gone.

```

olof@main:~$ ssh -Y username@192.168.1.17
usr/bin/xauth:  /home/username/.Xauthority not writable, changes will be ignored
[not interesting]
username@hokatorp-serv:~$ xclock
X11 connection rejected because of wrong authentication.
Error: Can't open display: localhost:10.0
```


probably it's remainings from my tinkering before I got it working...

is there a way to reset the ssh settings? a file to erase or similar.

just to mention - I have tried this too:
```

olof@main:~$ ssh -X username@192.168.1.17
[not interesting]
/usr/bin/xauth:  error in locking authority file /home/username/.Xauthority
username@hokatorp-serv:~$ w
 19:32:57 up  4:03,  3 users,  load average: 1.18, 0.65, 0.56
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
username tty7     :0               15:29    4:03m  2:26   0.06s /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
username pts/0    :0.0             15:32    3:58m 31.68s  0.78s bash
username pts/2    main.lan         19:31    0.00s  1.29s  0.02s w

sername@hokatorp-serv:~$export DISPLAY=main.lan

```
but it does not work.

---

### Post by olof_ on 2010-12-27
now I found /etc/ssh
and ~/.ssh/
will it help to remove the files within?

---

### Post by nerdy_kid on 2010-12-27
> **olof_ said:**
> now I found /etc/ssh
and ~/.ssh/
will it help to remove the files within?

rename it to something else and see if it fixes the issue.

---

### Post by tgalati4 on 2010-12-28
Sorry, my fault.  I meant:

env

setenv is for other systems.

And yes, export is the proper command to set an environment variable.  X allows up to 10 screens I believe.  You can use more, but you have to recompile the xorg server with larger settings.

Sorry that I caused so much grief.

I would normally say "google it", but that got me in trouble in another thread.

---

### Post by olof_ on 2010-12-30
I first renamed the textfiles inside the ssh folder, but it did not help.
secondly I tried to uninstall ssh and openssh-server on both of the machines, and I thik I dare to say that now are things exactly as I wanted it to be now

(I do not even know if I dare to ask this question), but should not 

```

username@hokatorp-serv:~$ w
 17:14:58 up  2:28,  3 users,  load average: 0.00, 0.09, 0.22
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
username tty7     :0               14:47    2:28m 44.40s  0.07s /bin/sh /etc/xdg/xfce4/xinitrc --
username pts/0    :0.0             15:00   16:31   1.51s  1.51s bash
username pts/1    main.lan         17:13    0.00s  1.27s  0.02s w

username@hokatorp-serv:~$ export DISPLAY=main.lan

```

turn things back to the default ssh -Y  behavior?

I know I can just disconnect and then reconnect, but it feels that there is a better way.

Happy New Year everyone!

---

### Post by gmargo on 2010-12-30
The proper syntax for the $DISPLAY variable, pointing back through the **ssh** link, is "localhost:10.0" (or 11.0 for the second connection, 12.0 for the third connection, etc).

So exit your ssh session and start a new one, then echo $DISPLAY to see what you should use.

---

### Post by olof_ on 2010-12-30
that did it!
thank you!

show it on the connecting computer:
```

export DISPLAY="localhost:10.0"

```

show it on the computer connected to:
```

export DISPLAY=:0

```

thank you all!!

---

### Post by olof_ on 2011-01-01
As a result of my new knowledge I made a guide, summarizing and explaining everything as good as I could [here]("http://ubuntuforums.org/showthread.php?t=1656263")

---

