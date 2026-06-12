---
title: "X11 forwarding with Xvfb"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by MWkemo on 2009-09-13
Hello,

I'm trying to forward X11 aplications to my local computer without X server, so I'm using Xvfb on my server. I configured sshd to forward X11 and on my client I configured putty with X11 forwarding localhost:0. The problem is that nothing hapens if I start for ex. xclock. It just stays runing and nothing popups.
I also tryed with x11vnc combination and after conecting with VNCViewer to server everything works just fine. But i wont to use X apllication without VNCViewer. 

```
Xvfb :1 -screen 0 1280x1024x24 &
```

This is my xvfb start command.

After i connect with putty to server I have to export DISPLAY to :1 with:

```
export DISPLAY=:1
```

now the application starts but no window is poping out. 

Any ideas?

Thanks

---

### Post by krunge on 2009-09-13
> **MWkemo said:**
> I'm trying to forward X11 aplications to my local computer without X server, so I'm using Xvfb on my server. I configured sshd to forward X11 and on my client I configured putty with X11 forwarding localhost:0. The problem is that nothing hapens if I start for ex. xclock. It just stays runing and nothing popups.
I also tryed with x11vnc combination and after conecting with VNCViewer to server everything works just fine. But i wont to use X apllication without VNCViewer. 

I don't think what you are trying to do will work.  Xvfb is a virtual framebuffer (exists in RAM only.)  It acts like graphics hardware that no one can ever see.  So xclock is showing up on it, but you can't see it. However, as a believe you have found you can view the contents of the Xvfb screen by exporting it by VNC via x11vnc (so that way the apps can be seen; xwd(1) is another.) 

I don't think there is a way to instruct Xvfb "tell all of the apps connected to you to now go through this putty tunnel to (an X server on) that Windows box".

You may want to look into xmove and xpra, or perhaps any similar tools.  I've only used xmove and that was a long time ago.

---

### Post by MWkemo on 2009-09-13
Ah, to bad. It's logical that there is no application popping out with Xvfb. I thought that i was able to run applications in past with Xvfb but obviously i was wrong. If I think harder there is a possibility that I was running real X server at that time.

Xpra looks interesting and it does what i want. I will give it a try.

Thanks for suggestion!

---

### Post by Endolith on 2009-10-11
> **MWkemo said:**
> I'm trying to forward X11 aplications to my local computer without X server

What does this mean, exactly?

> The problem is that nothing hapens if I start for ex. xclock. It just stays runing and nothing popups.

Isn't that what's supposed to happen with Xvfb?  I can't figure out how to get that working.  :)  What did you do?

---

### Post by smokes2345 on 2011-01-24
While i realize this thread is rather old, i believe what you are trying to accomplish can be done without using any kind of video device (virtual or otherwise) on your ubuntu box.  What you need is an Xserver running on your windows box, I use xming.  Once you get xming installed and running, just enable X11 forwarding in your putty client and the rest should take care of itself.

---

### Post by Endolith on 2011-01-24
> **smokes2345 said:**
> Once you get xming installed and running

That part seems difficult.  :)

---

### Post by smokes2345 on 2011-01-25
Not at all.  Just download the public domain release (You have to purchase the website releases) from their website (google it, it's the first result) and run it.  All the defaults should work fine, but you may wish to uncheck the putty option when it asks what you want to install since you already have it.  Once you get xming installed, in your putty options go to Connection->SSH->X11 and check the box labeled "Enable X11 Forwarding" then connect.  If you have xming running you should be able to run any GUI program from your prompt and it will display on your windows box.  

Once you connect, don't try to setup an X server or framebuffer or anything, the ssh server should handle all of that for you.  It should also set your DISPLAY variable to the proper value.

---

### Post by N00bED^ on 2011-08-12
I am trying to get Xvfb to run, and it says "Multiple display managers can rum simultaneously if they are configured to manage different servers, configure the display managers accordingly, edit each of their init scripts in /etc/init.d, then disable 'check for a default display manager'. I just installed Ubuntu 11.04, Natty Narwhal, and am having trouble finding these init scripts so that I may initialize the X server, to then continue with trying to run Xvfb, HELP. Lol, any and all help is greatly appreciated, thanks for looking! - Kevin

---

