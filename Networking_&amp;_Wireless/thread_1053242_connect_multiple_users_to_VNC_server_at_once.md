---
title: "connect multiple users to VNC server at once"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by pytheas22 on 2009-01-28
I followed [this tutorial]("http://ubuntuforums.org/showpost.php?p=5229232&postcount=458") to set up a VNC server on Ubuntu 8.04 that allows logins directly to gdm.  It works fine, but only one user can connect at a time.  I need to allow multiple users under different accounts to be connected (from Windows) simultaneously.

Ideally, I would like to be able to tell users simply to launch a VNC client, connect to the Ubuntu machine's IP address without having to specify a screen (i.e. no :1 or :2 appended to the IP address), and the VNC server on the Ubuntu computer would automatically launch a session for the user on any available screen.  Is there a way to do this?

---

### Post by theDaveTheRave on 2009-06-11
Pytheas

did you find a solution for this??

I want to do a similar thing, I am wondering if changing the port for the connection will work for extra users, then the server can be started once for each port?

I'm going to try this out.... I'll report back

David

---

### Post by pytheas22 on 2009-06-11
Dave,

It's been a long time since I did this, but I did end up getting things working as desired, for the most part.  According to my notes, my first step was to set up everything according to [this tutorial]("http://ubuntuforums.org/showpost.php?p=5229232&postcount=458").

To get multiple VNC sessions working, I then edited the file /etc/xinetd.d/Xvnc.  By default (if you followed the instructions from that link), it will look like this:
```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}
```

To get the VNC server to listen on additional ports, you need to add an extra session for each new port, incrementing the 'port = XXXX' and '-inetd :X' lines as appropriate.  For example, if I wanted to make the server listen on ports 5901 and 5902, I would make /etc/xinetd.d/Xvnc look like this:
```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = **-inetd :1** -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        **port = 5901**
}

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = **-inetd :2** -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        **port = 5902**
}
```

This allows you to have one user logged in and connected to VNC screen 1 (i.e. port 5901) and another on screen 2 (port 5092) simultaneously.  Unfortunately, the users still need to specify the screen number when they log in--I couldn't figure out a way to tell the VNC server to just assign the next available port.

You need to restart xine ('sudo /etc/init.d/xine restart'), or possibly reboot, for changes to that file to take effect.

In principle, you can use this method to make your VNC server listen on as many ports as you like; just add a new section for each additional port.

However, I recall there being some issue where gdm by default allows only a certain number of gdm sessions to be running at once (I think it was 4 or 5), which effectively limits the number of users who can be logged into VNC using this method.  I think I got around this problem by editing /etc/gdm/gdm.conf; unfortunately, I seem to have neglected to write down exactly what I did.  I *think* I had to uncomment the line that reads '#FlexibleXServers=5' and change it to a higher number, but I'm not positive that this was all it took to make gdm allow more sessions.

Hope this helps.  Let me know if you have more questions.

---

### Post by theDaveTheRave on 2009-06-16
Pytheas.

Thanks that is going to help a lot, I'll get to it when I'm next at the office.

Are uou back in the land of esspresso coffee and croisants?

David

---

### Post by pytheas22 on 2009-06-16
> Are uou back in the land of esspresso coffee and croisants?

Yeah, I arrived this morning and spent the day dealing with French bureaucrats at the archives de la guerre, which combined with the jet lag made for a long day.  On the other hand, I got Internet access without having to use aircrack, so life isn't too bad.  I'm living in the 6th; if you're around, send a mail.

Let us know how you get on with the VNC stuff.  I'm interested to see whether things go smoothly for you--I was surprised how much hacking it took to get something working that seemed relatively straightforward.

---

### Post by theDaveTheRave on 2009-06-19
Hello again.

Whilst I mess about setting this idea up, and documenting it, no thanks to Pyhteas as he's "forgotten" how he set it up - typical, history proffesor can't remember what he did - oh the irony! ;)

Anyway I've stumbled across another interesting idea, thin clients.

for me using VNC is almost like getting all the benefits of a thin client system, and your own personal desktop all at the same time!

Check out this set of pages for the [LTSP]("http://www.ltsp.org/") project on linux systems.

David

---

### Post by pytheas22 on 2009-06-19
If people remembered everything all the time, there would be no need for historians to remind them what the past was like :)

I've never played with thin clients personally, but have read a bit about them.  Will be interested to hear about your experience if you go the thin-client route rather than VNC.

---

