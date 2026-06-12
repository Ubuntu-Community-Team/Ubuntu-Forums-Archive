---
title: "X Forwarding"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by kranny on 2009-11-26
This isnt exactly X forwarding but i want to run my eclipse instance which is installed on my desktop on a remote machine...

Any ideas?

---

### Post by Grenage on 2009-11-26
X over SSH is probably what you want, and it can/does sort or work.  Take a look here:

[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

---

### Post by kranny on 2009-11-26
Its displays the following error 

(eclipse:19687): Gtk-WARNING **: cannot open display:

Do i need to install GTK+

---

### Post by Lars Noodén on 2009-11-26
How are you getting the error?  The server should also allow at least that particular user the option for X11Forwarding in /etc/ssh/sshd_config.

```

X11Forwarding **yes**
X11DisplayOffset 10

```

Try a simple connection from the remote machine first:

```

ssh -**X** -l kranny krannysdesktop.example.com

```

Note, that the ssh option is a capital X, not a small x.

---

### Post by xifer on 2009-11-26
My config has this on the client machine. :

/etc/ssh_config

ForwardX11 yes
ForwardAgent yes

at the command line I type

ssh hostname_or_ipaddress -l username

Once logged in I can run an xsession or any app as required

xfce-session &

or
gnome-session &

or 

startkde &

or xterm &


Without the ssh_config it is possible simply to set this once logged in from the client to the server:

DISPLAY=clientipaddress:0.0
export DISPLAY
then as above.


HTH

---

