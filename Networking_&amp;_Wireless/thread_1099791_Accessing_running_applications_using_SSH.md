---
title: "Accessing running applications using SSH"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by hipertrofia on 2009-03-18
Hi everyone!

I'd like to know how you can remotely access (using SSH) an application that is already running on the computer I'm logged in.

Namely:

I have Transmission running in graphic mode on my computer at home. Afterwards, I log in that computer using SSH from another computer on the same network. Now, I want to have access to this graphic enviroment of the already running Transmission application from the second computer, that is, I don't want to start a new Transmission process from the second computer but instead gain access to the existing process on the first computer.

Thanks in advance!

---

### Post by t0bias on 2009-03-18
Hi,

a connection via ssh is treated as a new login to your machine and there is no way I am aware of to get access to a process started from another login-session, namely your ordinary computer-login.

Toby

---

### Post by hipertrofia on 2009-03-18
Thanks for replying!

But it is the same session since I use the same user (#-o isn't it?). Wouldn't that be like opening two consoles in the same session?

Besides, trying to access Transmission from a console in the first computer yields the same message as done remotely: "Another copy of Transmission is already running" (sorry if this is not the original message in English but my OS is in Spanish).

Maybe my doubt could be restated as: how can I access an existing graphic process from a console whithin the same computer?

---

### Post by ktrnka on 2009-03-18
You will want to start vino the vnc server on the computer you want to access (computer 1). You can access it by going to Go to System -> Preferences -> Remote Desktop. and configure the Remote Desktop Preferences. once you have that properly set, you can ssh into your computer from any other box (computer 2) and tunnel the port through ssh.

From Computer 2:

```
ssh -L 5900:localhost:5900 username@remotecomputer.com
```

Then open up your vnc client on Computer 2 and in the address section, type localhost.

Good Luck!

---

### Post by ktrnka on 2009-03-18
Just a quick reference for you:

The default port for vnc is 5900, however, you can use any port above 1024 that you want, as long as it doesn't conflict with one currently in use. (Don't worry, when you ssh in, it will say failed to bind to port # if it is already in use)

Eaxmples

```
ssh -L 6000:localhost:5900 user@host.com
```

The -L says to bind to localhost. The 6000 is your local port number. The middle section between the : : basically says where to forward the traffic to on the remote side. i.e. you can specify any ip address on your lan if you are trying to view a remote desktop that is not the direct one you are ssh-ing to. The last section after the : signifies the remote port.

If you ran the command above, you would need to modify what you put in your vnc client slightly to look like ```
localhost:6000
``` to specify that you wish to connect to port 6000 on your current machine.

To connect to a windows box on your lan that is not your box which you are ssh-ing to, it would look a little like this:

```
ssh -L 3389:IPorDNSofWindowsbox:3389 user@host.com
```

and RDP client would need this in it's address section
```
localhost
```

or

```
ssh -L 3389:localhost:3389 user@host.com
```

and the RDP client would look like
```
IPaddressofWindowsBox
```

Just as with vnc, you can bind to a different port number. 
Example:
```
ssh -L 45000:IpaddrofWindowsbox:3389 user@host.com
```

Then the RDP client would look like:

```
localhost:45000
```

---

### Post by hipertrofia on 2009-03-19
Thank you very much for your help!

---

