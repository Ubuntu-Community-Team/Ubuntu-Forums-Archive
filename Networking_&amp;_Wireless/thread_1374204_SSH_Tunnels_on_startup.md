---
title: "SSH Tunnels on startup"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by wbrady4927 on 2010-01-06
I have multiple ssh tunnels that I need to run on startup. Does anyone know a working way to do that? I have tried creating a script and putting it in all sorts of directories (/etc/init.d/, /etc/, /etc/network/if-up.d/). I have also tried appending the commands to /etc/rc.local but nothing works. The script is actually executed in all these places because I tried putting a simple mv command in there and that was executed but these ssh tunnels won't be constructed. My script looks something like this:

#! /bin/sh
xterm -e ssh ....... &
xterm -e ssh ....... &
xterm -e ssh ....... &

I also have another program that I would like to run along with the ssh tunnels. The program needs to be run as root, but that won't work either. Can anyone help with any of this?

---

### Post by puppywhacker on 2010-01-06
The xserver isn't started yet in the scripts you have tried. Besides you do not need to spawn a (graphical) terminal. Also you can setup multiple tunnels through the ssh-server. I assume you tested the ssh connection in a terminal? you don't need to sudo if the tunnel-port is higher than 1024. (the unprivileged range starts from 1024)

I like the use of /etc/rc.local The use of an script like /etc/rc2.d/S80mytunnels is fine too. I'm not sure if /etc/network/if-up.d/ is read in all circumstances. I don't think network manager reads it???

---

### Post by wbrady4927 on 2010-01-06
Thank you for your fast reply! What would you use to execute the commands without using the graphical terminal? I also don't know how to configure the ssh-server?

---

### Post by puppywhacker on 2010-01-06
Remove the xterm -e. Ssh will run just fine without it provided that it doesnt ask for a password and you use private&public with rsa or dse keys. google for authorized ssh keys

---

### Post by wbrady4927 on 2010-01-06
The 3 ssh commands I need to have running are:
ssh -b net1 -L net1:rt1:net2:rt2 user@net2
ssh -b net3 -L net3:rt3:net4:rt4 user@net4
ssh -D net1:rt2 user@net

What's the best way do you think to do that?

---

### Post by wbrady4927 on 2010-01-06
Just removing xterm -e did not work. Are you still supposed to leave the & at the end of each line? Or do you have any other thoughts? Any ideas are welcomed!

---

### Post by puppywhacker on 2010-01-07
removing the "xterm -e" is only a starting point, you still need to get autorized keys to work. This will allow ssh connections with trusted keys to be established, so that it doesn't ask for a password. Try these connecting on the commandline before trying it in a script. You can see where it fails on the commandline, but not in the script.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

If you get this to run on the commandline, you can think of putting the rules in the rc.local

I don't know what you try to achieve with the third ssh rule with -D, but I think you misunderstand it's function? Only TCP tunnels can be used easily.

As for the first rules, they could look like this
```

ssh -L 8000:localhost:8000 user@net2
ssh -L 8001:localhost:8000 user@net4
```

Where the localhost part is seen from the remote server, so the first rule will tunnel everything from net2:8000 to the client's local port 8000 and the second rule will forward net4:8000 to the local port 8001 (Since 8000 is already in use.) Now clients can use the ports 8000 and 8001 to initiate connections. The server in net2 and net4 can not initiate connections (since we did not set up a reverse tunnel with -R)

---

### Post by wbrady4927 on 2010-01-07
I already have the keys set up and when I run the script on its own after I have started the system everything works. But when the script is executed on startup it doesn't work. Is there a way to run those ssh commands in the background? I'm not sure if that would help or not. I cannot even get the startup script to run one other root command without these ssh commands. But it will run simple mv or cp commands.

---

### Post by wbrady4927 on 2010-01-07
If I just do :
ssh ...
ssh ...
ssh ...
I think it will do them nested. That is why I was trying to execute each in their own terminal.

---

### Post by Lars Noodén on 2010-01-07
> **wbrady4927 said:**
> If I just do :
ssh ...
ssh ...
ssh ...
I think it will do them nested. That is why I was trying to execute each in their own terminal.

If these tunnels are to be started automatically it will be easier to do so with help of [keys](http://ubuntuforums.org/showpost.php?p=8587498&postcount=7).  Here is one possible syntax for /etc/rc.local:

```

ssh -i /home/tunneluser/.ssh/key_net2 -L 8000:localhost:8000 tunneluser@net2
ssh -i /home/tunneluser/.ssh/key_net4 -L 8001:localhost:8000 tunneluser@net4

```

---

### Post by wbrady4927 on 2010-01-07
I mean I already have rsa keys setup in my /home/username/.ssh/id_rsa and I can successfully make the ssh connection without entering any password. Does specifying the file with the -i option change the behavior any more than it already is?

Also, is there any place to put the commands that will guarantee the network has already been loaded on startup? Does rc.local already guarantee that? I thought that my be an issue because the ssh commands won't work if there is no network setup already.

---

### Post by puppywhacker on 2010-01-07
Probably the -i works because when you boot up your system and rc.local will be executed, I think it will be done as root, and that is not where the keys are stored, so the "-i" Lars proposed do add some weight.

The ssh commands after each other will not be run nested, but in sequence. The "&" will spawn the process to the background so that you don't have to wait for it to return ... which it shouldn't since the tunnel should be up as long as your computer is up ... What you could do for troubleshooting purposes you can add temporarily add debug info to your ssh connections like

```
ssh -v -i keys -L 8000:net1:8001 user2@net2 > /tmp/normal.out 2> /tmp/error.out &

```
That should redirect all normal output (which is verbose thanks to the -v) to the file /tmp/normal.out and all errors to ... error.out :)

That should provide clues about ssh actually being started and what it is doing while you don't have any sight on it.

Happy regards

---

### Post by rhalff on 2010-06-14
Another good alternative is installing gstm (Gnome SSH Tunnel Manager) and add it to your startup programs.

The tunnel is more visually active this way (with a tray icon)

My only problem at the moment is gnome is asking me for the keyring password upon startup which prevents the network from starting before I enter it,
because of this the tunnel won't start either because there is no network available yet.

But I'm sure I'll have that fixed soon :-)

---

### Post by roy.nico on 2012-09-27
This is a very old thread, but since i was looking also for the answer and i found i somewhere else, than i copy it there. 
It seems (on my ubuntu 12.04) that rc.local is executed before the network is on. Just add a delay of a few seconds in the script ```
sleep 20
``` solved the problem for me.

---

### Post by jsmoriss on 2012-12-14
Why not use autossh? Here's a startup script for autossh that allows you to start/stop multiple tunnels: [http://surniaulula.com/2012/12/10/autossh-startup-script-for-multiple-tunnels/](http://surniaulula.com/2012/12/10/autossh-startup-script-for-multiple-tunnels/)

js.

---

