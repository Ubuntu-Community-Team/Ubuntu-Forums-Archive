---
title: "XMMS2: trouble connecting clients"
date: 2009-12-10
forum: Multimedia Software
---

### Post by DarkDigitalDream on 2009-12-10
Hello. I have been trying to configure xmms2 following a thread located here: [http://ubuntuforums.org/showthread.php?t=706736&page=2](http://ubuntuforums.org/showthread.php?t=706736&page=2)

I am trying to achieve two things: Getting both esperanza and conky to connect to the xmms2 server data.

I have this working, but not properly. This works:
```

$ XMMS_PATH="tcp://127.0.0.1:6600" esperanza list
"misc.cpp:50" [ connectXmms2 ] - trying to connect to: "tcp://127.0.0.1:6600" 

```and this does not:
```
$esperanza 
"misc.cpp:50" [ connectXmms2 ] - trying to connect to: "tcp://127.0.0.1:9667" 

```It is clear that esperanza tries to connect to port 9667 by default, but I can force it to connect properly to port 6600. Conky is a little less verbose, but running "conky -d &" gives me error messages and no xmms2 data, where as running "$ XMMS_PATH="tcp://127.0.0.1:6600" conky list" gives me the correct data.

I have been fighting with this installation for most of today, and this is as far as i've been able to get. How can I get xmms2 to default to port 6600, and have my other applications know this without being explicitly told?



~~~~~~~~~~~~~~~~~~

SOLVED:

Solved the problem! There is very little online help for XMMS2, so here's the trick that saved the day:

---

For esperanza, I simply had to re-run the 'first time' setup wizard. It asks for the server and port to connect to. If I knew where to search, there is probably a config file esperanza puts this data in. Running the setup wizard again could have been avoided if I could find that file.

---

For conky, the config file is a file called cli.conf in the xmms2 client configuration folder. In my xubuntu setup, this was ~/.config/xmms2/clients , but online tutorials I found suggested they can typically be found at ~/.xmms2/clients

in the cli.conf file, simply change the "ipcpath=" line to
"ipcpath=tcp://127.0.0.1:6600" (or wherever your xmms2 server is running) to allow conky to display data via the $xmms2_* variables.

Also, conky requires the $XMMS_PATH environment variable to be set. To set this permenantly, I added the line
export XMMS_PATH="tcp://127.0.0.1:6600"
to my ~/.bashrc file.

There might be a simpler way to get this done, and I am by no means an expert. I simply got this through trial and error. If you have any insight/questions, feel free to comment.

---

