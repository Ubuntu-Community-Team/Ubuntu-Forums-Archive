---
title: "gui start applications as other user with video + audio support"
date: 2015-07-20
forum: Multimedia Software
---

### Post by asgard2 on 2015-07-20
Hi,

I like to start my gui applications as another user for security reasons.

For example firefox (web surfing) or other software which is closed source (ex. games). 

My secondary (non-root) user is already in the "video" and "audio" group, but audio does not work all right.

Most times audio is not working.


Someone now this problem, has a solution?


Thanks!

---

### Post by sudodus on 2015-07-20
Would it be OK to ***log out*** and ***log in*** as that other user, or to ***switch user***? This way the other user will grab the whole desktop environment, which makes things much easier than to have one window with the other user.

-o-

Otherwise it is possible to install ***openssh-server*** and log in via ssh with graphics to the other user. Run the following command in a terminal window

```
ssh -X otheruser@ssh -X other-user@192.168.0.2
```

(Change to your real other-user's ID and the real IP address of the computer)

and you can launch GUI application programs from the terminal window, for example you can test with ```
xlogo
```

It works to run ```
firefox
```

But I don't know how to make audio work that way (via ssh). Things will be straight-forward if you log out and log in as that other user.

---

### Post by asgard2 on 2015-07-20
Currently I use something like this:
```

function switchUser(){
        xhost +SI:localuser:user
        su user
        xhost -SI:localuser:user
        ps -ef | grep user
}

```

Switching the user is at xubuntu 14.04 not available anymore ... there is no option in the menu, only logout?

Just by using firefox as another user for an extended period, I could not log in and out any time.

Never tested the ssh -X connection to a local device, but I need a running ssh server. :/

With xhost the user has full access to the gui, is ssh more secure in this case?

---

### Post by sudodus on 2015-07-20
I don't know much about the security levels, except that running a server is a security risk in general.

Lubuntu has a ***switch user*** option in its logout window. I tested that it really works right now. So if this feature is important, you can switch to Lubuntu. It is probably also possible to switch only the logout tool, but I don't know the details how to do that. If you are lucky, someone who knows will chip in and tell you how to do that.

---

### Post by mc4man on 2015-07-20
This thread seems to be about switching user sessions in xubuntu 14.04+
[http://ubuntuforums.org/showthread.php?t=2218401](http://ubuntuforums.org/showthread.php?t=2218401)

---

### Post by asgard2 on 2015-07-21
Thanks, I could restore the option with this [post]("http://ubuntuforums.org/showthread.php?t=2218401&p=13002754#post13002754").

Anyway, if someone has another solution to fix the audio problem within the current session, please let me know. ;)

---

