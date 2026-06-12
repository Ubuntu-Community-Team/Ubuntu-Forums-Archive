---
title: "how do you control vlc running video from another computer?"
date: 2010-03-21
forum: Multimedia Software
---

### Post by senor_smile on 2010-03-21
Here is my setup: 
I have one laptop connected to my tv.  It has all the videos on it.  I have another laptop(actually a netbook) that I have set up to do light browsing on.  Both are running ubuntu 9.10.  I would to be able to remotely control vlc running on the laptop connected to the tv from the netbook.  

I have been searching for a while and have found hints that this is possible, but everything either refers to streaming from one machine to another or doesn't give enough examples to figure it out.  I have tried enabling the http interface, but I can't access this from another computer.  Anyone know of any good howto's for this?

---

### Post by Revolutionary101 on 2010-03-21
You would need to setup a SSH connection between the two computers. SSH will let you transfer files between the computers and also send commands via terminal. To do this follow this tutorial.

[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

After you have done that reply to the thread so I can talk to you about the next step.

Also ask any questions that you may have with setting up the SSH

---

### Post by senor_smile on 2010-03-21
I am very familiar with ssh server/client operations.  I have access to the machine that I need to connect to over ssh.

---

### Post by jms1989 on 2010-03-21
I have been experimenting with this on my machines with the one connected to the tv running ubuntu 9.04 and the netbook as the controls running windows xp. 

My solution consists of ssh into the media pc and control vlc from on the command line. You'd have to tell it to output to the first display and play it in fullscreen. I am unfamiliar with the http interface of vlc so I have no idea what it does.

Examine the output from 'vlc --help' to find a command that works for you. Its all about trial and error to find with works for you. I hear its even possible to control it over the web but I wouldn't want to do that personally.

---

### Post by Revolutionary101 on 2010-03-21
Okay log into your laptop that you want to play videos with via SSH in your terminal. Then type this:

```
vlc --help
```

That should list a bunch of commands that you may want to use. To play a file use the command "cd" to go to the directory that the file is in. Then type this to play that file.

```
vlc file:///filename.mp4
```

That should play the file for you.

---

### Post by senor_smile on 2010-03-21
> **jms1989 said:**
> I have been experimenting with this on my machines with the one connected to the tv running ubuntu 9.04 and the netbook as the controls running windows xp. 

My solution consists of ssh into the media pc and control vlc from on the command line. You'd have to tell it to output to the first display and play it in fullscreen. I am unfamiliar with the http interface of vlc so I have no idea what it does.

Examine the output from 'vlc --help' to find a command that works for you. Its all about trial and error to find with works for you. I hear its even possible to control it over the web but I wouldn't want to do that personally.

I have played a little with the command line interface of vlc, but I can't get it to play to "screen 0", it always tries to play locally.  I don't see an option to get it to control like that.

---

### Post by jms1989 on 2010-03-21
You can try some thing like this; DISPLAY=:0.0 vlc --play-and-stop -f dir/file.ext

Just include the DISPLAY variable at the beginning of the command to cause it to play on the remote machine. However, I find vlc to be a bit slow and keeps dropping frames so I tried smplayer and it seemed to do better. 

DISPLAY=:0.0 smplayer -fullscreen dir/file.ext

---

### Post by senor_smile on 2010-03-21
> **jms1989 said:**
> You can try some thing like this; DISPLAY=:0.0 vlc --play-and-stop -f dir/file.ext

Just include the DISPLAY variable at the beginning of the command to cause it to play on the remote machine. However, I find vlc to be a bit slow and keeps dropping frames so I tried smplayer and it seemed to do better. 

DISPLAY=:0.0 smplayer -fullscreen dir/file.ext
thanks!  exactly what I was looking for.

---

### Post by senor_smile on 2010-03-21
Do you know of any ways to control other video/audio playing programs on the command line? e.g. Firefox connecting to hulu.

---

### Post by jms1989 on 2010-03-22
Controlling a flash based app on the commandline? I don't believe its possible. It'd have to be a app callable via the command line. Sure you can run 'firefox [http://www.hulu.com](http://www.hulu.com)' and firefox will open and go straight to hulu but controlling the video player would need to be done with a mouse.

There is 'mp3blaster', a command line based music player that will play music on the host machine. IE, if you run it on your media pc, it will play music through your audio device. Be it a stereo receiver, tv speakers, etc.

---

