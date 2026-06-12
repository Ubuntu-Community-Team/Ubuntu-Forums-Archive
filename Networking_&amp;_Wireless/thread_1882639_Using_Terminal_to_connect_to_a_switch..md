---
title: "Using Terminal to connect to a switch."
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by Aydos on 2011-11-17
I am a Network Admin at a school and I currently use Windows 7 on my main laptop and use Putty to ssh and telnet to connect to switches and waps, a cisco program to monitor cdp, etc.

I have been setting up a Linux laptop to be more portable and learned how to use the terminal to monitor cdp on a port. It was actually quicker than the program I use.

I am trying to see if I can get away from using this program for this function and this program for that and just do it all in one.

Is there away to telnet and/or ssh into a switch or anything else using just the gnome terminal that comes with Linux?

If so do I need to install anything, what is it, and what commands do I use to do this.

Thank you in advance.

---

### Post by jonobr on 2011-11-17
Hi there


Id recommend dropping telnet all together as it seems a bit odd to be running both.
One is insecure and the other is secure and replaces telnet.


However, I understand some equipment you have may only support telnet, if so shame.......

The terminal located in applications-> accessories will will let you telnet and ssh to your devices.

In putty you have the option to check a radial button to indicate telnet ssh serial, but again in the terminal you just enter the commend

telnet myhost.com

ssh myserver.com

I do however, get the feeling i am not understanding the question

---

### Post by Aydos on 2011-11-17
You understood it perfectly and answered exactly what I needed. Thank you.

I figured it was built in and I wanted to check.

I agree with you on the ssh. We have it on every device that can and telnet on the few that cannot.

Thank you again.

---

### Post by jonobr on 2011-11-17
Sweet

---

### Post by Aydos on 2011-11-17
Hmmm.

Spoke to soon. I tried to telnet into the ip and it said 

telnet: Unable to connect to remote hose: Connection refused.

Any ideas why?

Putty connects right away. I can use it if need be but I am trying to lower my tools to one place.

---

### Post by Aydos on 2011-11-17
I wonder if there is any libraries I need to install or anything I need to turn on.

---

### Post by jonobr on 2011-11-17
What settings are you using to connect with putty...

Telnet client is on there by default.
If it is saying connection refused, your ubuntu machine is trying to telnet,
but the other end or device is saying no.
Either it doesn't have telnet enabled or your being blocked/restricted at some point

If you want to double check telnet is working on your machine and you have internet access

then  in terminal type

telnet towel.blinkenlights.nl

and enjoy the show

(PS- The above is star wars in telnet showing that telnet does work on your machine)

---

### Post by Aydos on 2011-11-17
Hmm

When I type that my terminal just puts the cursor down on the next line solid and sits there.

Obviously I am missing something on here lol.

As far as how do I connect with putty at work I just click the telnet bubble and type the IP in to the address bar and putty pulls up the console window and I just type my username and password and voila.

---

### Post by Aydos on 2011-11-17
Well I tried it a second time with sudo and I got a window welcoming me somewhere so I guessed that worked.

Now I gotta figure out why I cannot get to my stuff.

Btw I let it keep going. The star wars stuff was awesome.

---

### Post by jonobr on 2011-11-17
Something sounds messed up in your path

Normally the telnet client is in 
/usr/bin
You should be able to run telnet as a regular user.

this is normally in your user path so when you type in telnet it looks in the local directory your in and then in your path.

Because it works with sudo and not as a regular user (which it should) it makes me think your path is incorrect.



Here is how you can test
in the terminal type

```
which telnet
```
it should come back and say 

/usr/bin/telnet or something similar

then type
```
echo $PATH
```
if /usr/bin is not in your path then thats why its not running as 
a regular user.

If it is in your path and its still not working then someone was monkeying around with permissions

In that case, take a look at the permissions of telnet
```
ls -l /usr/bin/telnet
```
it should show the permissions like this

> lrwxrwxrwx 1 root root 24 2011-09-23 10:30 telnet->/etc/alternatives/telnet
or similar

---

### Post by Aydos on 2011-11-17
> **jonobr said:**
> Something sounds messed up in your path

Normally the telnet client is in 
/usr/bin
You should be able to run telnet as a regular user.

this is normally in your user path so when you type in telnet it looks in the local directory your in and then in your path.

Because it works with sudo and not as a regular user (which it should) it makes me think your path is incorrect.



Here is how you can test
in the terminal type

```
which telnet
```
it should come back and say 

/usr/bin/telnet or something similar

then type
```
echo $PATH
```
if /usr/bin is not in your path then thats why its not running as 
a regular user.

If it is in your path and its still not working then someone was monkeying around with permissions

In that case, take a look at the permissions of telnet
```
ls -l /usr/bin/telnet
```
it should show the permissions like this


or similar

My which telnet came back correct, but my echo $PATH says /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games.

On a second note I installed Putty and tried to connect the same way I do with windows version of putty and it timed out. However, I can do it on a windows machine right now the same way. 

I am confused.

---

### Post by Aydos on 2011-11-17
I think it is something on my network. I will dig around and post later. Thanks for all the help.

---

### Post by jonobr on 2011-11-17
Hey there


Try posting the results of 
ls -l /usr/bin/telnet

Im wondering if your permissions are wrong

Im guessing also if you sudo telnet <ip address> to the machine you want that this works?

Cheers

---

### Post by Aydos on 2011-11-17
Nope that does not either. 

Also, I do not have to sudo to the star wars telnet. I am thinking I mistyped it the first time or something.

My problems seem to be on my network.

I am on the wrong vlan I believe. I never try to do it wired and I cannot make the new version of Ubuntu work with this wireless cards.

I am about to swap to my other machine though and I should be fine.

I'll post later.

---

### Post by jonobr on 2011-11-17
Ok, I misunderstood you
I thought you said it worked when you went sudo.

If you do a telnet to anything that doesnt exist 
eg 50.50.50.50

does it at least say trying?

Can you ping the remote server your trying to connect to?

I also though you mentioned ssh was ok?

Is that still the case?

---

