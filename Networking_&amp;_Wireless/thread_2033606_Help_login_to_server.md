---
title: "Help login to server"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by neopiper on 2012-07-26
Hello,

I'm a newbie for this network things and don't know how to do the following:

My office has an OpenSuse server and I do have an account there.

I need to run, in this case Matlab, which is installed in the server.

How can I do it from my computer which has Ubuntu 12.04?  I want to be able to see the GUI though.

Any help is appreciated.

Thanks.

---

### Post by spjackson on 2012-07-27
From your Ubuntu machine, open a terminal window and do
```

ssh -X username@NameOfOpenSuseServer

```
The -X enables GUI programs to be displayed over ssh.

Then when you have logged into your OpenSuse server, run the command for Matlab. I don't have Matlab and have never used it, so I don't know what that command is.

---

### Post by neopiper on 2012-07-27
Thanks for your reply...I still haven't been able to get this working...ssh should work but maybe I'm in the wrong domain..how can I set this up?

---

### Post by neopiper on 2012-07-27
OK I was finally able to login to the server...however, any command I run I obtain a message like

-bash: COMMAND: command not found

any clues? ideas?

---

### Post by steeldriver on 2012-07-27
your login shell under ssh is not setting its PATH environment variable correctly maybe? can you run things if you give the full path? what does ```
echo $PATH
``` show?

---

### Post by neopiper on 2012-07-27
yes it does work if I give the full path. how can I set the Path environment variables as it should? in other words..how do I add matlab to the environment variables?

---

### Post by steeldriver on 2012-07-27
You would do something like 

```
export PATH=/path/to/matlab:$PATH
```

You could put that in the appropriate startup script - exactly where depends on your current configuration (.profile / .bash_profile / .bashrc etc.) - you likely want it so that you get the same environment for both ssh logins and xterms - I would check with your friendly sysadmin

FWIW I run matlab sessions on a remote Fedora box for my work - although I use a VNC session tunneled over ssh rather than 'ssh - X' (this way I can leave the session running and just reconnect whenever)

---

### Post by HoCo xXSamXx on 2012-07-27
From the desktop I would do this:
File>Connect to server> then enter all the information

---

