---
title: "Copying from computer A to B using C"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by Ballzac on 2011-07-08
First of all, my apologies. It seems like something that would be pretty common for people to want to do, but I can't find a thread about it. The problem is that typing in relevant search strings returns a heap of threads about related, but different, topics.

I have 3 computers on a network. Computer A is ubuntu server, computer B is XBMC live. Computer C is ubuntu natty.

I wan't to copy files from A to B using C, and THEN be able to shutdown C without terminating the file transfer.

An example of why I might want to do this is that I copy over a folder of movies from the server to XBMC, but it takes hours because the XBMC machine is on wireless. During this time I may want to log out of my own computer (C) so that I can log into windows and use software that I have installed there.

The way I perform tasks on both A and B is by using ssh on C. Specifically, I type

[HTML]ssh -l username 192.168.1._
[/HTML]

where "username" is the relevant login for each computer, and "_" is the last number of the local ip for that computer. I then type my password when prompted.

I have samba set up on all computers, and it is a simple task to open network shares in nautilus on computer C to copy stuff from A to B, but if I shutdown computer C, it interrupts the file transfer.

I considered mounting a drive from computer B on computer A and logging in to computer A on computer C via ssh, then cp from A to the network drive of B mounted on A. But, if I understand correctly, I still need to be logged in via ssh for the tasks I'm performing to continue, so this will be no better than using nautilus. Am I correct in saying this?

How would I go about doing what I need to get done?

Thanks in advance for your help.

---

### Post by capscrew on 2011-07-08
> **Ballzac said:**
> First of all, my apologies. It seems like something that would be pretty common for people to want to do, but I can't find a thread about it. The problem is that typing in relevant search strings returns a heap of threads about related, but different, topics.

I have 3 computers on a network. Computer A is ubuntu server, computer B is XBMC live. Computer C is ubuntu natty.

I wan't to copy files from A to B using C, and THEN be able to shutdown C without terminating the file transfer.

An example of why I might want to do this is that I copy over a folder of movies from the server to XBMC, but it takes hours because the XBMC machine is on wireless. During this time I may want to log out of my own computer (C) so that I can log into windows and use software that I have installed there.

The way I perform tasks on both A and B is by using ssh on C. Specifically, I type

[HTML]ssh -l username 192.168.1._
[/HTML]

where "username" is the relevant login for each computer, and "_" is the last number of the local ip for that computer. I then type my password when prompted.

I have samba set up on all computers, and it is a simple task to open network shares in nautilus on computer C to copy stuff from A to B, but if I shutdown computer C, it interrupts the file transfer.

I considered mounting a drive from computer B on computer A and logging in to computer A on computer C via ssh, then cp from A to the network drive of B mounted on A. But, if I understand correctly, I still need to be logged in via ssh for the tasks I'm performing to continue, so this will be no better than using nautilus. Am I correct in saying this?

How would I go about doing what I need to get done?

Thanks in advance for your help.

Run the command detached from the terminal (e.g. in the background).  You can do that with this command ```
<the_command_you use_ to copy>**[COLOR="Red"] &[/COLOR]**
```

You can test this on your Ubuntu desktop machine by opening the terminal and running this```
gedit &
```

Now close the terminal and you will should still have gedit running.

---

### Post by Ballzac on 2011-07-08
Hey, thanks for the help. It actually doesn't quite work. I get the command prompt back straight away, but if I close the terminal, gedit closes too. But, using this as a starting point, I discovered the nohup command after a little bit of googling, and that seems to work on my local machine, so I'll test it out on the network after I've mounted the drive.

Cheers. :)

EDIT: After a little more googling about nohup, I found this [http://www.cyberciti.biz/tips/nohup-execute-commands-after-you-exit-from-a-shell-prompt.html](http://www.cyberciti.biz/tips/nohup-execute-commands-after-you-exit-from-a-shell-prompt.html), so I'll mark this thread as solved even though I haven't actually tried it for my task yet.

---

### Post by Ballzac on 2011-07-08
It turns out that the mv command produces a "preserving permissions" warning when copying to a samba share (even though the share is mounted locally). The actual move occurs, and the permissions are indeed different to what they were originally. This would be okay, but I get 

> nohup: ignoring input and appending output to `nohup.out'


which just sits there until I ctrl+C. I've searched, and it seems there is no solution. Is there another way to do what I'm trying to do?

---

### Post by Bachstelze on 2011-07-08
Look into tmux or screen. ;)

---

### Post by Ballzac on 2011-07-09
Sounds great. I'll give screen a go as soon as I get my server back up and running. Unfortunately, in following advice I found to try to circumvent the "preserving permissions" error, I was chmodding the files and then moving them. To 'simplify' this I decided to write a script (which I've never done before) rather than have to type the commands every time I changed a setting on the other computer. This somehow screwed up my bash, and I can no longer log in. I have posted about it here: [http://ubuntuforums.org/showthread.php?t=1800468](http://ubuntuforums.org/showthread.php?t=1800468)

---

### Post by Ballzac on 2011-07-09
Yep, it works perfectly. Thanks for that :)

EDIT: Thought I'd give a quick description here for anyone reading this thread who wants to do the same thing.

Login to your server via ssh. Then, assuming screen is installed on the server (it was already installed on my ubuntu server), type

```
screen -S *name*
```

where *name* is the name you want to give the terminal screen you are opening. This will start a new screen. It will look the same as a normal terminal. Type your command, in my case

```
sudo mv /home/ballzac/*path1* /home/ballzac/*path2* 
```

then hit ctrl+a. The cursor will stop flashing as screen waits for input. Hit d to detach the terminal. This just means that it will run in the background on the server itself. You can then type 

```
exit
```

to exit screen, and again to exit the terminal. If you logoff on your computer at this stage, the commands will continue running on the server. To reattach the terminal, log back in via ssh, and type 

```
screen -r *name*
```

where *name* is the name you defined earlier. This should take you back to where you were before and you can see if your commands have finished executing or whatever. If you have issues getting back in, you can type

```
screen -ls
```

to see what screens are active. You will see something like
```
14234.*name* [detached]
```
The number is a unique identifier, and if you can't get in with

```
screen -r *name*
```

you can use (for the example given above)

```
screen -r 14234
```

If you see

```
14234.*name* [attached]
```

then the screen isn't detached for whatever reason, and you type

```
screen -x 14234
```

to view it.

---

