---
title: "Loading program up on remote system via SSH"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by Tobywuk on 2009-03-10
Hello

My server at home, running ubuntu, is turned on but i forgot to load up a program on the system, Transmission, so that I can access its remote web page while I am out of the house.

What I want to do is to SSH into my server and make the transmission application run on my server, not on my laptop where I am now. I have SSH'd into my server and run the command 'transmit' to load up the program on the remote system but i get '** Message: Cannot open display:'  (obviously because im using the server via command line). it seems to be trying to load it on my local laptop system from the server over ssh.

How can u get this software to run on the remote system and not to me through ssh?

thanks.

---

### Post by N04h on 2009-03-10
Have you set up the port forwarding necessary to access this from the outside world?

---

### Post by Tobywuk on 2009-03-11
Yes, Iv forwarded both ports for SSH (as i have succesfully connected as above) and the ports for the web interface.

All im after is some *nix trickery to run transmit on the remote server and stay there when I exit SSH, not through the tunnel on my local machine.  Im thinking the answer may be to use 'screen' or something along those lines.

---

### Post by mobilediesel on 2009-03-11
> **Tobywuk said:**
> Hello

My server at home, running ubuntu, is turned on but i forgot to load up a program on the system, Transmission, so that I can access its remote web page while I am out of the house.

What I want to do is to SSH into my server and make the transmission application run on my server, not on my laptop where I am now. I have SSH'd into my server and run the command 'transmit' to load up the program on the remote system but i get '** Message: Cannot open display:'  (obviously because im using the server via command line). it seems to be trying to load it on my local laptop system from the server over ssh.

How can u get this software to run on the remote system and not to me through ssh?

thanks.

Try this at the terminal:```
export DISPLAY=:0.0
```
Then when you run transmission, put a "&" at the end, like this:```
transmission&
```
So it forks a separate process from your ssh session.

---

### Post by skajoeska on 2009-03-16
i'm trying to do this almost exact thing. I don't have a headless server but rather I have a second laptop running Xubuntu.

This is what i've gotten through trial and error and some google searching.

I think your problem is X11 forwarding is not enabled. you can enable it by adding -X to your ssh command. You can also enable it by editing /etc/ssh/sshd_config on the server and /etc/ssh/ssh_config on your laptop i think. i'm not positive those are the right files so just google "X11 forwarding ssh ubuntu".

> ssh -X Tobywuk@server
insert the appropriate username and servername. It is a capital X. 

I would use screen. There are some tutorials on how to use it. For our purposes I found this solution.

1. Run your ssh session through screen with X11 forwarding.
> screen ssh -X Tobywuk@server
2. Enter your password
3. Run transmission as a background application
> transmission&
4. Detach the screen session by pressing Ctrl A D. meaning press and hold control then press 'A' then 'D' in sequence.
5. To reattach your screen session just run
> screen -r

I think that's what you want. It solves my problem. you can run multiple screen sessions and do some other cool stuff also.

---

