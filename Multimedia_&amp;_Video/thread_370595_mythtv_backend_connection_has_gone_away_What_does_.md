---
title: "mythtv backend connection has gone away? What does this mean?"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by Tdonohue on 2007-02-25
I've installed mythtv and mysql and everything appears to okay, but when I start the backend, and then the frontend.  It tells me the "connection has gone away...".  What does this mean?  I've installed Mythtv and had it working okay on a laptop with no tv tuners (as a test run before I built this PC) and never got this message.  I have an analog kworld tuner and a dual analog/digital kworld tuner.  An excerpt from the log shows....

2007-02-25 23:02:04.389 New DB connection, total: 2
2007-02-25 23:02:04.448 Connected to database 'mythconverg' at host: localhost
2007-02-25 23:02:04.554 EITHelper: localtime offset -5:00:00 
2007-02-25 23:02:04.631 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2007-02-25 23:02:04.773 ChannelBase(1) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2007-02-25 23:02:04.891 EITHelper: localtime offset -5:00:00 

I really don't know if the cards are setup correctly, or if that is what is contributing to my problem.

Can anyone help?  Thanks

---

### Post by tgm4883 on 2007-02-25
did you configure the card AND the video source?

---

### Post by Tdonohue on 2007-02-25
> **tgm4883 said:**
> did you configure the card AND the video source?

I don't know.  My guess is that the cards are not configured correctly.  I've not done anything to them since I've installed ubuntu.  I was hoping to find a way to test if the cards were setup right, but I don't  know how (I opened another thread about the cards). 

As for the source, I don't know.  I believe I did that during the install.  Is there a way I can check?

---

### Post by Erlander on 2007-02-26
You need to follow a guide to setup Mythtv.  The Ubuntu documentation is as good as any:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

and the Mythtv Setup section:

[https://help.ubuntu.com/community/MythTV_mythtvsetup](https://help.ubuntu.com/community/MythTV_mythtvsetup)

Capture Cards, Video Sources and Input Connections are important.

Rob

---

### Post by Tdonohue on 2007-02-26
> **Erlander said:**
> You need to follow a guide to setup Mythtv.  The Ubuntu documentation is as good as any:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

and the Mythtv Setup section:

[https://help.ubuntu.com/community/MythTV_mythtvsetup](https://help.ubuntu.com/community/MythTV_mythtvsetup)

Capture Cards, Video Sources and Input Connections are important.

Rob

Rob, I thank you for your response.  I was following the guide in the community documentation for "combined frontend, backend and regular desktop".  

I believe I have solved the issue with the "...backend connection has gone away...".  It appears that I never set a password for the mythtv user (and hence was unable to log in as mythtv user).  I ran  mythtv-setup  as a user in the mythtv group when I set it up first.  So, I set a password for the mythtv user, logged in as that user, ran the mythtv-setup again, and was finally able to run the frontend without error under all users in the mythtv group.

However, the issues with the tv tuners I've not solved.  The guides for installing mythtv, seem to go over the tv tuner configuration briefly, which leads me to believe it is a simple procedure and user error is entirely to blame for my problem here.  

When I get home from work I will work on the tuners.  If anyone as any suggestions as to how I can confirm that the cards work and are detected by ubuntu correctly, I would appreciate it.

---

### Post by tgm4883 on 2007-02-26
install tvtime.  It allows you to watch tv, but doesn't have pvr functionality.  It should work to check if your cards are working correctly.  You could also lspci to see if anything is coming up unknown (and lsusb, dmesg, etc)

---

### Post by Tdonohue on 2007-02-26
> **tgm4883 said:**
> install tvtime.  It allows you to watch tv, but doesn't have pvr functionality.  It should work to check if your cards are working correctly.  You could also lspci to see if anything is coming up unknown (and lsusb, dmesg, etc)

Thanks for the response.  I did try lspci and it did show the tuners coming up as unknown.  I posted the output and my response in my other thread.  This thread evolved into the same topic as the other one and it wouldn't be right to carry on two threads of the same problem at the same time.

[http://ubuntuforums.org/showthread.php?t=370615]("http://ubuntuforums.org/showthread.php?t=370615")

If you would be so kind as to carry on with this in the other thread, I would very much appreciate it.

Thanks, Tm

---

