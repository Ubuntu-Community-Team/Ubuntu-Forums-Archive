---
title: "Writing a script"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by ve1drg on 2010-05-13
I want to write a simple script to set up a telnet function on ubuntu (10.04).
I am not used to the rc0.d etc.. files but rather creating these scripts through the /etc/services and inet files.  
Ubuntu does it different.  If someone could tell me (through and example) how to write one of these scripts I should be ok.  Also there is something you have to run to update the writen script into your system.

Any examples would be appreciated.  I used the telnet function as just something to use as an example.

---

### Post by sir_nasty on 2010-05-13
well I don't know if this is exactly what you need but here's an idea....

```


sudo gedit filenamethatyouwanttouse.sh


```

put in the commands you want like

```

mv /tmp/old /tmp/new
cp /tmp/new /home/user/desktop/new
echo it moved;

```

then
```

sudo chmod +x filenamethatyouwanttouse.sh
./filenamethatyouwanttouse.sh

```


does that help at all or was it way to basic for you?

---

### Post by ve1drg on 2010-05-13
Well first of all,   thanks for the input.
I am trying to write a script for some of ax25 utils that I am setting up. For example, setting up a telnet function.  I think that if I found a script similar to how a telnet script would be setup, that I could just copy it and leave it in the same directory.  But than that would only get the script started. I would than need to find a way to stop it.  So there are 'S' scripts and 'K' scripts.  This is all too complicated at the moment.  But I am sure there is a way to figure this out.
 
Thanks again for your input.

---

### Post by BoneKracker on 2010-05-13
This might help:

[http://ubuntuforums.org/showthread.php?t=1172846](http://ubuntuforums.org/showthread.php?t=1172846)

If you want to learn a bit about Ubuntu init system:

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)
[https://help.ubuntu.com/community/InitScriptList](https://help.ubuntu.com/community/InitScriptList)

---

