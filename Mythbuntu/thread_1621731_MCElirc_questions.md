---
title: "MCE/lirc questions"
date: 2010-11-14
forum: Mythbuntu
---

### Post by wilma92010 on 2010-11-14
Hi There!

I am using MythTV 9.10 with a Haup. HVR-1600 and have had great success.  The remote for the HVR worked intermittently so I tossed it and bought an SIIG MCE remote.

The MCE remote works better.  Actually, it works all the time except when watching videos, when seeking forward sort of "craps out" after a few clicks, meaning it stops responding.  This makes it difficult to get to "the good parts" if you know what I mean.

BTW, using a keyboard does not show that problem at all.  I can jump forward at will and the performance is immediate.

I have read a lot of threads and looked at irw which just shows the stated behavior, it prints out a code from mceusb until it decides to stop responding, coinciding with the player not responding.   

I have also found .lirc configuration for mplayer, elisa, vlc, mythtv etc.   My configuration is for the "internal player."  

So, here are some questions:

1) what is the mythtv "internal player?"    I tried changing it to mplayer, thinking the player had some problem seeking forward, but now I know that is not the problem.  But I would like to make sure the configuration is correct and would like to play with it to perhaps find a solution.

2) where can i find documentation for the .lirc configuration files.  I think this is the most likely path to a solution.  (i realize this may be a dumb question, but i really don't know where to look for this)

3)  will upgrading to 10.x help?   Are the drivers for this product under the purview of mythtv or ubuntu or somewhere else?   Is there a driver update that would solve this problem?

4) i am willing to buy a new remote device compatible with MCE if that would solve the problem, but it doesn't seem likely.   Anyone have any suggestions?

Thanks for any help.

Wilma

---

### Post by winewood on 2010-11-14
Wilma,

It sounds like this issue isn't a remote control problem.  It sounds like the player is jumping ahead, and either due to too many commands too quickly, or the cpu/memory can't handle the requests.  

If it were a remote control problem, the issue would be not getting a signal to the box at all.  The buttons are responding.  The only way it could be a remote issue, is if the remote is sending too many commands at one time.  This could be config, or a stuck button.  

I am going of memory, but the command is "irw" from the command line.  Type this in a new window and send the box your commands.  Each single command is a few short characters.  Now try pressing fast forward multiple times.  Take note of the output and hopefully you will see if multiple commands are going to the box unintentionally.

-Hope this helps.

---

### Post by wilma92010 on 2010-11-14
Hi,

I started a video and then ran irw which reports as follows.

000000037ff07bde 00 Right mceusb
000000037ff07bde 01 Right mceusb
000000037ff07bde 00 Right mceusb
000000037ff07bde 01 Right mceusb
000000037ff07bde 02 Right mceusb
000000037ff07bde 00 Right mceusb
000000037ff07bde 01 Right mceusb
000000037ff07bde 02 Right mceusb
000000037ff07bdf 00 Left mceusb
000000037ff07bdf 01 Left mceusb
000000037ff07bdf 00 Left mceusb
000000037ff07bdf 01 Left mceusb
000000037ff07bdf 02 Left mceusb
000000037ff07bdf 00 Left mceusb
000000037ff07bdf 01 Left mceusb
000000037ff07bdf 02 Left mceusb

In this sequence I fwd 3 times and back 3 times.  So it looks like it is sending multiple codes every time I press a button. 

I kind of doubt that the buttons are sticking, but somehow the codes are getting repeated.  

Any thoughts on how that might happen?

Thanks,

Wilma

---

### Post by winewood on 2010-11-15
I too have that exact remote, which is just a standard MCE remote. The codes that end in 00 are the initial code. The 01, and 02 are repeats. Therefore this is due to the button being held down, or the repeat value being set (im gussing) and repeating your press multiple times.
 
I will offer some samples from my /home/username/.lirc/mythtv config if you want to compare it. See if your repeat values are at 0.
 
```
begin
    remote = mceusb
    prog = mythtv
    button = Two
    config = 2
    repeat = 0
    delay = 0
end
begin
    remote = mceusb
    prog = mythtv
    button = One
    config = 1
    repeat = 0
    delay = 0
end
begin
    remote = mceusb
    prog = mythtv
    button = Zero
    config = 0
    repeat = 0
    delay = 0
end
# Start MythTV with MCE Start button:
begin
        prog = irexec
        button = Power
        repeat = 0
        config = /usr/local/bin/mythtv_startup
end

```
 
oh.. shameless plug
I was able to get my power button to start/stop the frontend with that last command. To get it working, in the /user/local/bin , create a file the same name as the config="filename" and put this into it.
 
```
#!/bin/sh
echo "start" >> counterfile
if [ ! "$(pgrep mythfrontend)" ]
then
        exec /usr/bin/mythfrontend.real --logfile /var/log/mythtv/mythfrontend.log &
else
        kill -9 `pgrep mythfrontend`
        sleep 1
        exec /usr/bin/mythfrontend.real --logfile /var/log/mythtv/mythfrontend.log &
fi

```
 
I hope your problem is the repeat but I am guessing. Go ahead and search in the Mythtv forum for irw and repeat or duplicate and I am pretty sure you can find a wealth of info on this same topic in case that wasn't it.

---

### Post by wilma92010 on 2010-11-19
Thanks for your post.

I have experimented with the repeat and see how it does effect the input.  I do get repeats when set to 0, so maybe my hamfisted button pressing is at fault.  Or something about the keys.   

Also the documentation for the file is at:

[http://www.lirc.org/html/configure.html](http://www.lirc.org/html/configure.html)

which I am sure you know.

Anyway, it is cool how you set up the front-end on/off, I have wondered how you would use the key and that is a nice idea, thanks.

I think I will try to program another remote to see if it the remote itself -- always blame hardware when possible!

Wilma

---

### Post by LowSky on 2010-11-19
LIRC the program that handles remote input has had some revisions and maybe a newer version of Mythbuntu will work better for you.

---

