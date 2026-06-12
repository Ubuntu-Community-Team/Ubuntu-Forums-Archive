---
title: "running remote X application"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by manthony121 on 2010-01-14
I have two computers running Ubuntu.  I want to run the copy of Firefox that is on the remote machine.  i connect to the remote in the usual way, "ssh -X fermi", which brings up a console on the remote machine, fermi.  When I type "firefox", however, it starts the copy of firefox that is on the local machine.  On the remote machine, "ps aux|grep firefox" confirms that firefox is not running there.  Is there a way to force execution of the remote copy?  Or, can I start a local copy of firefox using the remote bookmarks, preferences, etc?

---

### Post by Lars Noodén on 2010-01-15
The error sounds very strange.  

What about this running inside the ssh connection?

[url]
# show system name and info then run Firefox
uname -a && firefox 
[/url]

Or

```

# launch firefox directly
ssh -X fermi firefox

```

---

### Post by carcar1 on 2010-01-15
for this I would reccomend webmin which is a broswer based server/desktop manager that can be port forwarded to access it outside of where the ocmputer is.  And while doing this the nxclient and server have done a great job for me you connect to it via ssh yet you get a remote desktop feel [http://www.nomachine.com/]("http://www.nomachine.com/")  I was actually going to install this later today.  nomachine offers great guides to installing.

---

### Post by mazato on 2010-01-19
manthony121, you can  do this:

ssh -X [email]user@mybox.com[/email] firefox -no-remote

or:

once you have logged in this way:
ssh -X [email]user@mybox.com[/email]

then you find your Display environment by:
echo $DISPLAY
you will see something like this : "localhost:10.0"
once you write/memorize your DISPLAY, type the following in you terminal:

firefox -no-remote -display:=localhost:10.0

Hope this helps! :)

P.S. Once you know the command of the  GUI app you want to run from the remote machine, you just have to type it in your terminal. That's it!

---

