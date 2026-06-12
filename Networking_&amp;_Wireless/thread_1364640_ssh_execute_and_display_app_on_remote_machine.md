---
title: "ssh: execute and display app on remote machine"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by lorsen on 2009-12-26
Hi, 

need some help, since I don't manage this.
I'm sitting in front of machineA and conncet via ssh to machineB.
```
machineA$: ssh -X lorsen@machineB
```after entering password I'm conncected to machine B.
Now I wont to start an app (e.g. xeyes) on the remote machine and it should be
displayed on that machine (machineB).
What I found is to do something like:
```
machineB$: DISPLAY=:0.0 xeyes
```but I get the error:
```
No protocol specified
Error: Can't open display: :0.0
```Using 
```
ssh lorsen@machineB
```I have no X11 forwarding, but get the error:
```
Error: Can't open display:
```Any suggestions? 
Thanks in Advance.

---

### Post by ELGL on 2009-12-26
I don't know if a kind of terminal server solution is what you're looking for, or just to run apps from anywhere on a pc at home. Anyway take a look at freeNX, it runs over SSH and it's a lot easier to set up than X forwarding over SSH. 

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Also nice is that there are linux and windows clients available.

---

### Post by Dennis N on 2009-12-26
[B]Running Remote Applications
[/B]
This might be helpful:

Here is an article on how to run remote applications with SSH:

[http://linuxplanet.com/linuxplanet/tutorials/6874/1/](http://linuxplanet.com/linuxplanet/tutorials/6874/1/)

see the section "Running Remote Applications" on the second page.

---

### Post by lorsen on 2009-12-27
Thanks for your answers, but maybe my problem wasn't stated clear enough.
I don't need to forward, I just don't want to forward ;-)
I sit in front of my PC at home (machineA). I need to start a program on my machine at work (machineB).
If I do:
```

machineA$: ssh -X lorsen@machineB
machineB$: xeyes

```
the x11 forwarding  makes the xeyes-window appear on my PC at home(machineA). That is a nice thing, but what I need is that the xeyes window appears on machineB.

(My problem is that I have to start a calculation at work (which lasts quite some time) that uses mathematica to generate some pics. Since there is some text in the pics mathematica needs to start its front end (a window) which is somehow needed for the text in the pictures but not otherwise. Since this happens a few thousand times it takes ages as compared when I run it on my machine at work directly. So I just want to make these windows appear on my machine at work, which should speed everything up enormously.)

Any ideas

---

### Post by lorsen on 2009-12-28
Noone around with an idea?  :(

---

### Post by Lars Noodén on 2009-12-28
Don't use X forwarding, if you intend the program to be displayed on the remote machine.  Once you are logged into machine B, set the DISPLAY environment variable so that the programs you run there known where to look for the X server.  


```

# connect
ssh -l lorsen machineB

# run xeyes
DISPLAY=:0.0 xeyes

# or set the environment variable for all programs
export DISPLAY=:0.0 
xeyes &
firefox &

```

---

### Post by lorsen on 2009-12-29
Hi Lars, 

thanks for your answer, but when I do it as you said :
> **Lars Noodén said:**
> 
```

# connect
ssh -l lorsen machineB

# run xeyes
DISPLAY=:0.0 xeyes

```

I get the error:
```

Error: Can't open display:

```What is the problem, what can I do?

---

### Post by dmizer on 2009-12-29
You should do research into the "screen" app. You should be able to start a secondary x-server in screen and switch in and out of it as needed.

More information here: [http://freshmeat.net/articles/the-antidesktop](http://freshmeat.net/articles/the-antidesktop)

Edit:
I thought I would share one thing about the above arrangement. Your app will not display on the remote machine's physical desktop. But, you can open a terminal attach to screen (just as you would from remote) and view the app locally that way.

Perhaps not ideal, but I believe it will be usable.

---

### Post by Lars Noodén on 2009-12-29
> **lorsen said:**
> 
thanks for your answer, but when I do it as you said :


What you pasted was different than what I wrote.  Did you try it with 'export' ?

---

### Post by lorsen on 2009-12-29
> **dmizer said:**
> You should do research into the "screen" app. You should be able to start a secondary x-server in screen and switch in and out of it as needed.

More information here: [http://freshmeat.net/articles/the-antidesktop](http://freshmeat.net/articles/the-antidesktop)

Edit:
I thought I would share one thing about the above arrangement. Your app will not display on the remote machine's physical desktop. But, you can open a terminal attach to screen (just as you would from remote) and view the app locally that way.

Perhaps not ideal, but I believe it will be usable.


Hi dmizer,

thanks. I will have a look at screen.

I don't need to be able to "really" few my app, it should just open the window "anywhere" on the remote machine and not on the local one (see lower part of post #4)

---

### Post by gradinaruvasile on 2009-12-29
Are you sure display is 0:0? It might be 0:1 or something.

---

### Post by lorsen on 2009-12-29
> **Lars Noodén said:**
> What you pasted was different than what I wrote.  Did you try it with 'export' ?

Hi Lars,

I only did not past the "# or set the environment variable for all programs"-part or was there also an error with the things above?

However it seems like I didn't copy one line (No protocol specified) of the error as I see now when I redo it again with both ways:
```

lorsen@machineB:~> DISPLAY=:0.0 xeyes
No protocol specified
Error: Can't open display: :0.0


lorsen@machineB:~> export DISPLAY=:0.0 
lorsen@machineB:~> xeyes &
[1] 5297
lorsen@machineB:~> firefox &No protocol specified
Error: Can't open display: :0.0

[2] 5298
[1]   Exit 1                  xeyes
lorsen@machineB:~> No protocol specified
No protocol specified
Error: cannot open display: :0.0

[2]+  Exit 1                  firefox

```**@[COLOR=Black][gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640")[/COLOR]:** same error when using DISPLAY 0.1
```
lorsen@machineB:~> DISPLAY=:0.1 xeyes
No protocol specified
Error: Can't open display: :0.1

```

---

### Post by lorsen on 2009-12-29
Hi, 

I thought some details are not important, but maybe this is not the case.
From my local PC (machineA) I have a VPN to machineL. I can ssh from machineA to machineL and from machineL to machineB. If I do it both time with -X (enable forwarding) I see the apps (e.g. xeys) on my local machine (machineA).
Because this 3-machine thing works I thought it is enough for my question to post just the 2-machine-setup. Maybe I was wrong?

However it is possible to see xeyes on my local machine (machineA) if it was started on machineB (using ssh -X). But I'm still not able to start it on the remote machineB (using ssh without -X (or using -x)) and let it appear on machineB.

Don't know if it gets more clear now :?

---

### Post by lorsen on 2009-12-29
Hi dmizer,

as far as I understood screen is for text-mode things only. This puzzles me somehow.
Nethertheless I tried something:
```

lorsen@machineA:~> ssh machineB
lorsen@machineB:~> screen

lorsen@machineB:~> konsole
<unknown program name>(6589)/: KUniqueApplication: Cannot find the D-Bus session server 

<unknown program name>(6588)/: KUniqueApplication: Pipe closed unexpectedly.


lorsen@machineB:~> terminal

(terminal:6591): Gtk-WARNING **: cannot open display: 

lorsen@machineB:~> xeyes
Error: Can't open display: 


```

I'm clueless ...      :-k_****_[]("http://dict.leo.org/ende?lp=ende&p=5tY9AA&search=clueless")

---

### Post by dmizer on 2009-12-29
Well, if you look closely at the site I linked, he's opening a screen session and typing "startx" to run a "ratpoison" desktop in screen.

Not too sure about the complexities of reattaching to the screen session once you've detached, but I think that screen is a big part of your puzzle.

---

### Post by Lars Noodén on 2009-12-29
> **lorsen said:**
> ...this is not the case.
From my local PC (machineA) I have a VPN to machineL. I can ssh from machineA to machineL and from machineL to machineB. If I do it both time with -X (enable forwarding) I see the apps (e.g. xeys) on my local machine (machineA)...

Try the whole circus without -X and make sure that you have DISPLAY set using **export** once you have reached machineB.  

BTW you can jump from A to B in one move using [netcat](http://linux.die.net/man/1/nc).  It can be done with keys or passwords or both.  

The following should allow ssh to machineB via machineL using only 'ssh machineB'

```

# in ~/.ssh/config
Host machineB
  HostName machineB.example.org
  User lars
  ProxyCommand ssh -l lorsen  machineL.example.org  nc %h %p

```

---

### Post by lorsen on 2009-12-31
Hi,

found it. I had to do a
```

machineB$: xhost +localhost

```on machineB directly (when I sit in front of it). Otherwise I'm not allowed to open a window on the xserver. That was my problem.
Now I just have to type
```

machineA$: ssh lorsen@machineB
machineB$: DISPLAY=:0.0 xeyes

```and it works fine \\:D/

**@Lars:**
Thanks for the tip with netcat. For some reason I had to write "netcat" instead of "nc" in your code example, but now it works fine :)
[B]
@dmizer:[/B]
Thanks for the tip with screen and ratpoison. This problem is solved  without it, but it really caught my attention. I installed ratcat on machineB but was not able to start it
(*startx /usr/bin/ratpoison -- :1*, as stated on [http://wiki.ubuntuusers.de/Ratpoison](http://wiki.ubuntuusers.de/Ratpoison) did not work; error: *no server "/usr/bin/Xgl" in PATH* and there is no */usr/bin/Xgl* (it is an opensuse 11.1)). However I will not try to much on that machine, but when I have my Karmic-Koala-Home-Machine ;-) up and running I will try again. 
In case needed you maybe allow me to ask you again ...
BTW Do you have it running?

**A Happy New Year for everyone!**

---

### Post by dmizer on 2009-12-31
> **lorsen said:**
> **@dmizer:**
Thanks for the tip with screen and ratpoison. This problem is solved  without it, but it really caught my attention. I installed ratcat on machineB but was not able to start it
(*startx /usr/bin/ratpoison -- :1*, as stated on [http://wiki.ubuntuusers.de/Ratpoison](http://wiki.ubuntuusers.de/Ratpoison) did not work; error: *no server "/usr/bin/Xgl" in PATH* and there is no */usr/bin/Xgl* (it is an opensuse 11.1)). However I will not try to much on that machine, but when I have my Karmic-Koala-Home-Machine ;-) up and running I will try again. 
In case needed you maybe allow me to ask you again ...
BTW Do you have it running?

**A Happy New Year for everyone!**

Happy new year indeed.

No I do not have it running, but the idea certainly intrigues me. I have some other projects ahead of this though, so it may be a while (if ever) before I get around to playing with it.

If you intend to pursue it, I'll do what I can to help but I'm not so fluent in X11. I'm mostly a networking freak. ;)

Edit:
Forgot to add -> Glad to see this marked solved! :)

---

