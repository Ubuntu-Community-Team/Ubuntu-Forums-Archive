---
title: "Need to execute commands on login?"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by rcb4t2 on 2012-01-07
Hey all - so I've just spent the better part of my day getting the wireless working on an old Inspiron 5100 a friend gave me. Using Ubuntu 11.4.

Anyway, I won't bore you with the gory details, but once I'm logged in, I need to go into the terminal and run:

sudo modprobe -r b44
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44

Once I do that, the wireless and wired connections work perfectly. It was suggested to me to add those commands to etc/rc.local. I tried them with and without the sudo with no luck.

I came to this solution from this thread: [http://ubuntuforums.org/archive/index.php/t-780719.html](http://ubuntuforums.org/archive/index.php/t-780719.html)

I tried the b43 fw cutter solution before the ndiswrapper one and couldn't get it working, if anyone's curious on the background. For now, though, I'm happy with the current solution if I could get it to automatically run those commands at login.

Any thoughts? Thanks y'all!

---

### Post by Dangertux on 2012-01-07
> **rcb4t2 said:**
> Hey all - so I've just spent the better part of my day getting the wireless working on an old Inspiron 5100 a friend gave me. Using Ubuntu 11.4.

Anyway, I won't bore you with the gory details, but once I'm logged in, I need to go into the terminal and run:

sudo modprobe -r b44
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44

Once I do that, the wireless and wired connections work perfectly. It was suggested to me to add those commands to etc/rc.local. I tried them with and without the sudo with no luck.

I came to this solution from this thread: [http://ubuntuforums.org/archive/index.php/t-780719.html](http://ubuntuforums.org/archive/index.php/t-780719.html)

I tried the b43 fw cutter solution before the ndiswrapper one and couldn't get it working, if anyone's curious on the background. For now, though, I'm happy with the current solution if I could get it to automatically run those commands at login.

Any thoughts? Thanks y'all!

Add the commands to your ~/.bash_profile or .profile files and they will execute once your shell is spawned (logging in).

Hope this helps.

---

### Post by rcb4t2 on 2012-01-07
Thank you for the reply - when entering the commands manually in the terminal, most of them don't work without the sudo before the command. If I enter them in ~/.bash_profile or .profile as you suggest should I include the sudo? Will it be able to execute the commands as root that way?

Thanks!

(fwiw, I've realized since booting up and manually entering the commands once, they hold up even after log-out and log-in.)

---

### Post by Dangertux on 2012-01-07
> **rcb4t2 said:**
> Thank you for the reply - when entering the commands manually in the terminal, most of them don't work without the sudo before the command. If I enter them in ~/.bash_profile or .profile as you suggest should I include the sudo? Will it be able to execute the commands as root that way?

Thanks!

(fwiw, I've realized since booting up and manually entering the commands once, they hold up even after log-out and log-in.)

 For those to work you would have had to append the sudo, which obviously would prompt you for a password. Sorry I kinda skimmed and didn't realize you were messing with modprobe that way. In any case yes that is a persistent command so you shouldn't have to do it every time you logout/in. Reboot on the other hand you will have to do.

When you placed them in rc.local did you put them before the

```

exit 0

```

If you didn't it will exit out before they run.

Hope this helps.

---

### Post by rcb4t2 on 2012-01-07
Thanks - I did put them before the exit. It's not so bad to enter them manually but if I could automate it that'd be great....

Or, really, if there's a better solution to the underlying problem that would, of course, be ideal. I think ssb is the underlying problem...

It's kinda silly - b44 is using ssb, and ssb interferes with ndiswrapper. So, to turn off ssb you must first turn off b44, at which point you can turn on ndiswrapper and b44 again. I honestly don't really understand what each thing does - I got all this from experimentation and the method from the thread linked in my first post. 

I think if I could disable ssb altogether I could set ndiswrapper to load itself (there was a method for that listed in another thread) and not have to execute any commands, manually or automatically.

---

### Post by Dangertux on 2012-01-07
Well you could add ssb and b43 to your /etc/modprobe.d/blacklist.conf file

```

sudo echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
sudo echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf

```then you can create a script in /etc/rc.5 name it whatever you want it will be run at startup

have it look something like this

```

modprobe -r b44
modprobe ndiswrapper
modprobe b44
exit 0

```
*make sure you chmod 755 the script you create

That might maintain through a reboot and you wouldn't have to type anything extra.

Hope that helps.

---

### Post by Kyslosh on 2012-01-07
Hello there I suggest you try google first ( I know after half day spending...)
try entries 
linux modprobe on start
linux modprobe on boot

as I googled a little some another person had same issues (ofc different driver)

I guess legit reply to this thread should be:
(following quote is from another forum)
> I think that by simply adding the command in this file ```
 /etc/rc.d/ init.d/ 
```
it'll do what you want...


and ofc put your firs four commands 
I mean all```

modprobe -r 

```
in blacklist




//I am on the iPhone it takes longer to write :D

---

### Post by rcb4t2 on 2012-01-07
Thanks guys - I already had the following added to the end of my blacklist.conf file long before the current solution:

blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb

Any idea why ssb loads anyway?

---

