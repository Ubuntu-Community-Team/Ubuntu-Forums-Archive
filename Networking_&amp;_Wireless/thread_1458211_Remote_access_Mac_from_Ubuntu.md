---
title: "Remote access Mac from Ubuntu"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by BaroqueBloke on 2010-04-19
I am sorry if there are already numerous threads on this subject but I am complete $#!@ at forum searches.  

Recently came into a new netbook and decided to hackintosh it so as to utilize apples seamless remote access capabilities (in my experience).  Needless to say I ran into numerous problems including wifi, sound, graphics, etc.  The usual issues.  

So i installed 9.10 and made a live usb of UNR to try out (juries still out on that).  Ubuntu seems to run better on this little netbook than it did on my mac!  

Which brings me to my question:

     How do I remote access mac files via the mac file share ip?


under the share tab in mac prefs it lists the web ip to link to for file sharing, "afp://ip-blah-blah.blah.blah"   
This doesn't work when I enter it in Ubuntu web browser.  

What must I do to get this to work????


Thanks all!

---

### Post by Felix-the-Cat on 2010-04-20
The best way is to enable a ssh server on your mac (I would turn this off when not on a private network i.e. home). I think Apple calls it remote management or something vague and non-descript (don't confuse the user with options). After this you can go to Places>connect to server and then in the drop down at the top select "SSH Server" enter you mac's IP and then click connect. Also note that on the MAc the firewall (if its enabled at all - it isn't from factory) needs to allow incoming connections on port 22. It should do that automatically but the word "should" has gotten me into trouble before.

---

### Post by BaroqueBloke on 2010-04-20
Thanks for the reply.  I wasn't expecting one so soon.  Some how I knew I wasn't going to get it set up so easily.  Using Remote Desktop Viewer and entering my macs ip for remote management always turns up this response:     

     (with SSH ticked)
     connection to host ip********* was closed

     (with VNC ticked)
     Authentication method to host ip******* is unsupported (30)

Edit*  well I managed to get to a password promt (my typing on the netbook is still not up to par....)  
I assumed it wanted the password for the computer im connecting to.  no luck.  So I tried the computer im connecting from.  no luck.  After three tries it denies access from too many attempts.

Is it possible the connection requires root level password(s)?



Thanks again!

---

### Post by Felix-the-Cat on 2010-04-21
> (with SSH ticked)
connection to host ip********* was closed
That is because you don't have a SSH server enabled on the MAC. You would have to go to System Preferences > Sharing and then enable a SSH server as per my previous post.

> 
(with VNC ticked)
Authentication method to host ip******* is unsupported (30)
Edit* well I managed to get to a password promt (my typing on the netbook is still not up to par....)
Sounds like you do have desktop sharing turned on the MAC machine but you need to redo it since you don't know the password (this is a separate password from the one used to login to the machine). Again to set this up go to System Preferences > Sharing on the MAC machine and then I think apple calls it "Apple Remote Desktop" (I laugh at this because it isn't even a Apple developed protocol - its VNC. In fact its not even the best around (MS RDP beats the pants off VNC anyday) yet they try to make it sound special.)

> Is it possible the connection requires root level password(s)?
Never, ever ever should you log in as root remotely or should such ever be allowed. By default on Ubuntu machines it isn't and I would hope to God it is the same on Apple(i.e. BSD) machines.

---

### Post by BaroqueBloke on 2010-04-26
Thank your much for your help!  I finally got it working.  It turns out terminal things typed in terminal are case sensitive.  Guess I should have read the Ubuntu pocket guide.  

Thanks again!

---

### Post by Felix-the-Cat on 2010-04-26
Great! It would be great if you could mark this thread as Solved when you get a chance.

---

