---
title: "How Can I Control an Application Locally via Unix Socket? (shell-fm)"
date: 2012-11-30
forum: Networking &amp; Wireless
---

### Post by ohnonot on 2012-11-30
hello everybody,
i'm trying to access an application that runs as a daemon, send commands to it. locally, on the same machine.
i'm a total network noob and feel there's a huge gap in my knowledge which i'm hoping to fill with your help.

i'm playing around with shell-fm but my question is not necessarily about that particular app.

anyhow, in man shell-fm it says:
```
       bind = host
              This  specifies  the network interface you want shell-fm to bind
              to.  host should be the host name  or  an  IP  address  of  host
              shell-fm is running on.  shell-fm will open a port (see the port
              option below) on the specified interface which you  can  connect
              to  to  control  shell-fm  remotely  (or from local scripts, see
              key0x??  above). Check the NETWORK  INTERFACE  COMMANDS  section
              below for a list of known commands.  NOTE: The network interface
              has no user authentication, so anyone with access to  your  net&#8208;
              work/host  can  control shell-fm. Use it only if you really need
              to control shell-fm over  a  network.  Otherwise  use  the  UNIX
              socket interface (see below).

       unix = path
              If this is set to a proper path, on that path a UNIX socket will
              be created for local "remote"  control.  This  socket  interface
              takes the same commands as the TCP socket interface (see above).
(...)
NETWORK INTERFACE COMMANDS
       This section describes the commands shell-fm's network interface knows.
       To use the interface, you must provide a valid value to the bind option
       in your configuration or use the -i option on the  command  line.  Then
       you can connect the specified port (54311 by default) and send one com&#8208;
       mand at a time.  This is a list of the known commands.

       play lastfm://...
              Play the given stream.

       love   Love the currently played track.
(...)
```i tried the```
unix=path
```option first - it creates a socket but i can't communicate with it.
tried things like```
echo skip | /path/.shell-fm/socket
```but nada.
then i tried```
bind=127.0.1.1
```(which i beleve is sth called localhost?) and actually managed to access the application with ```
echo skip | nc 127.0.1.1 54311
```- but:
- i have to press ctrl-c everytime to get my command prompt back
- this doesn't work in shell scripts which can be called from a menu.

but basically i would rather use the socket if possible.

any help/suggestions/links appreciated. thanks.
and

---

### Post by ohnonot on 2012-12-01
bump...

---

### Post by ohnonot on 2012-12-03
bump...

---

